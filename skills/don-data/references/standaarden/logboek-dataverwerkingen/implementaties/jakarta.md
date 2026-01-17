# Jakarta service method interceptor

Met Jakarta kunnen Java applicaties HTTP requests afhandelen.
Hierbij is het mogelijk om een `@Interceptor` te definiëren die method van een `@Service` kan wrappen met code voor het starten van een span.
Deze interceptor kan ook geïntegreerd worden met een W3C Trace propagator die de relevante informatie uit de HTTP header kan halen (als die header er is).

Voorbeeldcode van het gebruik:

```java
public class Service {
    @Inject
    ProcessingHandler handler;

    @Inject
    LogboekContext logboekContext;

    @Path("/api-endpoint")
    // Hier is de `processingActivityId` de index van het register
    // waar de verwerkingsactiviteit is beschreven.
    @Logboek(name = "Vraag gegevens op voor burger", processingActivityId = "23")
    public Response test() {
        // Er kan automatisch een span worden aangemaakt binnen de huidige
        // actie, waardoor deze gelinkt worden aan de correcte context.
        var innerSpan = handler.startSpan("geneste-actie", null);
        
        // Voeg alle relevante context toe. Dit hoeft niet per se in deze
        // methode, maar kan ook elders in de applicatie gebeuren. Het
        // is wel belangrijk om de `ProcessingHandler` te injecten zodat
        // alle contexten correct gelinkt worden aan elkaar.
        LogboekContext innerContext = new LogboekContext();
        innerContext.setStatus(StatusCode.Ok);
        innerContext.setDataSubjectId("123456789");
        innerContext.setDataSubjectType("BSN");
        innerContext.setProcessingActivityId("25");
        innerContext.addLogboekContextToSpan(innerSpan);
        innerSpan.end();

        // Dit is de context voor de hoofdactie, waar andere spans aan gelinkt
        // kunnen worden. Deze wordt geupdate door de geinjecteerde `LogboekContext`
        // te updaten die dan door de `@Interceptor` wordt uitgelezen.
        logboekContext.setDataSubjectId("Bedrijf XYZ");
        logboekContext.setDataSubjectType("KVK");
        logboekContext.setStatus(StatusCode.OK);

        return Response.ok("We hebben succesvol gegevens opgevraagd").build();
    }
}
```

## Interceptor definitie

Deze definitie maakt gebruik van de classes die hier beneden staan.
Alle logica zit in de interceptor, de rest zijn data holders of doen wat initialisatie werk.

```java
package nl.gov.logboekdataverwerking;





@Logboek
@Interceptor
public class LogboekInterceptor {

    @Inject
    LogboekContext logboekContext;

    @Context
    HttpHeaders headers;

    @Inject
    ProcessingHandler handler;

    @AroundInvoke
    public Object log(InvocationContext invocationContext) throws Exception {
        // Propagater om trace informatie uit HTTP headers op te halen
        var propagatorInstance = W3CTraceContextPropagator.getInstance();
        // Voer de propagater uit op de headers. Als er geen informatie uit
        // de headers te behalen is, dan wordt er automatisch een nieuwe
        // trace context aangemaakt. Anders wordt dat gedaan op basis van
        // de headers met de implementatie van `HttpHeadersGetter`.
        var traceContext = propagatorInstance.extract(
                io.opentelemetry.context.Context.current(), 
                headers, 
                new HttpHeadersGetter()
        );

        // Deze annotation moet op de service method
        Logboek annotation = invocationContext.getMethod().getAnnotation(Logboek.class);
        if (annotation == null) {
            throw new IllegalArgumentException("Logboek annotation ontbreekt op service method");
        }

        // Start een span binnen deze trace. Dit zorgt er onder andere voor dat de `start_time`
        // goed staat. De andere attributen worden toegevoegd nadat de service method
        // is uitgevoerd, omdat in de service method de `LogboekContext` verder wordt gevuld
        var span = handler.startSpan(annotation.name(), traceContext);

        // Voer alle acties uit als onderdeel van deze span. Omdat de span `AutoCloseable`
        // is, zal automatisch de context weer terug worden gezet naar de originele trace
        // context wanneer deze interceptor klaar is.
        try (var scoped = span.makeCurrent()) {
            // Voer de business logica van de service method uit.
            return invocationContext.proceed();
        } catch (Exception e){
            // Overwrite de status van de service method en zet deze altijd op `Error`.
            span.setStatus(StatusCode.ERROR);
            // Zet alle attributen als onderdeel van de foutafhandeling.
            span.setAttribute("exception.message", e.getMessage());
            span.setAttribute("exception.type", String.valueOf(e.getClass()));
            // Rethrow de exceptie zodat die correct wordt terug gegeven door de service.
            throw e;
        } finally {
            // Elke span is altijd ook readable. Dit is nodig om er ook nog weer informatie
            // uit te halen, zodat we ook dingen kunnen toevoegen aan de span.
            var spanData = ((ReadableSpan) span).toSpanData();

            // Check of we extern zijn aangeroepen en alleen dan moeten we de attributen zetten
            if (headers.getHeaderString("traceparent") != null) {
                span.setAttribute("dpl.core.foreign_operation.span_id", spanData.getParentSpanId());

                // TODO: Haal de URL van de externe applicatie op. Dit hangt af van het applicatielandschap.
                // Dit kan bijvoorbeeld worden gehaald uit een FSC contract, op basis van bestaande
                // Digikoppeling informatie of moet worden bepaald op basis van API keys.
                span.setAttribute("dpl.core.foreign_operation.processor", headers.getHeaderString("traceparent-processor"));
            }

            // Zet de `processing_activity_id` op basis van de annotation. Deze is statisch
            // en hoort niet te veranderen tussen verschillende calls.
            logboekContext.setProcessingActivityId(annotation.processingActivityId());
            // Zet overige attributen op de context.
            logboekContext.addLogboekContextToSpan(span);
            // Sluit deze span af en populate daarmee de `end_time`.
            span.end();
        }
    }

    private static class HttpHeadersGetter implements TextMapGetter<HttpHeaders> {
        @Override
        public Iterable<String> keys(HttpHeaders httpHeaders) {
            return httpHeaders.getRequestHeaders().keySet();
        }

        @Override
        public String get(HttpHeaders httpHeaders, String key) {
            return httpHeaders.getHeaderString(key);
        }
    }
}
```

## Annotation voor service method

`Logboek.java` met een annotation die op een service method kan worden gezet.
Hiermee definieer je de [naam](https://logius-standaarden.github.io/logboek-dataverwerkingen/#name) van de dataverwerking en de [`dpl.core.processing_activity_id`](https://logius-standaarden.github.io/logboek-dataverwerkingen/#attributes).

```java
package nl.gov.logboekdataverwerking;







@InterceptorBinding
@Target({TYPE, METHOD})
@Retention(RUNTIME)
public @interface Logboek {

    @Nonbinding
    String name() default "";
    
    @Nonbinding
    String processingActivityId() default "";

}
```

## Context voor het updaten van relevante attributen

Daarnaast is er een `LogboekContext.java` die de overige dynamische attributen kan zetten.
Waar de verwerkingsactiviteit altijd statisch is, zijn de andere dynamisch en moeten die dus door de business logica worden gezet.

```java
package nl.gov.logboekdataverwerking;



@RequestScoped
public class LogboekContext {

    private String processingActivityId;
    private String dataSubjectId;
    private String dataSubjectType;
    private StatusCode status;

    public String getProcessingActivityId() {
        return this.processingActivityId;
    }

    public void setProcessingActivityId(String processingActivityId) {
        this.processingActivityId = processingActivityId;
    }

    public String getDataSubjectId() {
        return this.dataSubjectId;
    }

    public void setDataSubjectId(String dataSubjectId) {
        this.dataSubjectId = dataSubjectId;
    }

    public String getDataSubjectType() {
        return this.dataSubjectType;
    }

    public void setDataSubjectType(String dataSubjectType) {
        this.dataSubjectType = dataSubjectType;
    }

    public StatusCode getStatus() {
        return this.status;
    }

    public void setStatus(StatusCode status) {
        this.status = status;
    }

    public void addLogboekContextToSpan(Span span) {
        span.setAttribute("dpl.core.processing_activity_id", this.getProcessingActivityId());
        span.setAttribute("dpl.core.data_subject_id", this.getDataSubjectId());
        span.setAttribute("dpl.core.data_subject_id_type", this.getDataSubjectType());
        span.setStatus(this.getStatus());
    }
}
```

## Handler voor starten van traces

Om traces vast te kunnen leggen moet er ook een `Tracer` worden aangemaakt.
Dit gebeurt in de `ProcessingHandler.java`.

```java
package nl.gov.logboekdataverwerking;



@ApplicationScoped
public class ProcessingHandler {

    private final Tracer tracer;

    public ProcessingHandler() {
        try {
            // Configureer de service met een naam, waarbij `logboekdataverwerking.service-name`
            // in een `application.properties` staat.
            String serviceName = ConfigurationLoader.getString("logboekdataverwerking.service-name");

            // Start OpenTelemetry als een service en maak een `Tracer` aan waaraan spans kunnen
            // worden toegevoegd.
            this.tracer = TelemetryConfig.initOpenTelemetry(serviceName).getTracer(serviceName);
        } catch (ConfigurationException e) {
            throw new RuntimeException("Failed to initialize ProcessingHandler", e);
        }
    }

    public Span startSpan(String name, Context context) {
        // Als er een context is (zowel van een externe applicatie als binnen de huidge applicatie),
        // dan moet de `parent` worden gezet. Als de context er niet is, dan moeten we niet de parent
        // overwriten, omdat dan de context verloren gaat.
        if (context != null) {
            return tracer.spanBuilder(name)
                    .setParent(context)
                    .startSpan();
        }

        return tracer.spanBuilder(name)
                .startSpan();
    }
}
```