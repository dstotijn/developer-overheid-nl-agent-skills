# Referentie implementatie in Go

Er is een referentie implementatie beschikbaar die de samenwerking van verscheidene prototype overheidsapplicaties laat zien.
De code is beschikbaar [bij Digilab op GitLab](https://gitlab.com/digilab.overheid.nl/ecosystem/logboek-dataverwerkingen/ldv-referentie-implementatie).
Er zijn instructies toegevoegd hoe de applicatie lokaal te draaien is, alsmede een test omgeving die draait op de Digilab infrastructuur.
Tevens is de code zelf veelvuldig beschreven met code comments en extra informatie + verwijzingen naar de standaard.

## Voorbeeldsnippets

Om een indruk te geven hoe een implementatie in Go eruit ziet, zie onderstaand voorbeeld van het ophalen van informatie van een burger ([source code](https://gitlab.com/digilab.overheid.nl/ecosystem/logboek-dataverwerkingen/ldv-referentie-implementatie/-/blob/3a4b2b8bae9272d02731a716a2e8d6cb8b9f2a54/apps/orgb/backend/application/citizen.go#L45-74)).

```go
// Get all data from a citizen
func (app *Application) CitizenGet(ctx context.Context, bsn string) (model.Citizen, error) {
	_, span := tracer.DataProcessingStart(ctx,
		app.tracer,
		"uri://brp.example/activities/citizen-get",
		tracer.SetAttributeActivityID(app.rvaIDs["citizen-get"].String()),
		tracer.SetAttributeBSN(bsn),
	)
	defer span.End()

	citizen, err := citizenGet(bsn)
	if err != nil {
		err := fmt.Errorf("citizen get: %w", err)
		span.SetStatus(codes.Error, err.Error())
		return model.Citizen{}, err
	}

	children, err := app.ChildrenGet(ctx, bsn)
	if err != nil {
		err := fmt.Errorf("children get: %w", err)
		span.SetStatus(codes.Error, err.Error())
		return model.Citizen{}, err
	}

	citizen.Children = children

	span.SetStatus(codes.Ok, "")

	return citizen, nil
}
```

Deze functie maakt gebruik van een abstractie om de overige attributen correct te zetten ([source code](https://gitlab.com/digilab.overheid.nl/ecosystem/logboek-dataverwerkingen/ldv-referentie-implementatie/-/blob/3a4b2b8bae9272d02731a716a2e8d6cb8b9f2a54/apps/orgb/backend/trace/operation.go#L112-L140)).

```go
func DataProcessingStart(ctx context.Context, tracer trace.Tracer, name string, opts ...trace.SpanStartOption) (context.Context, trace.Span) {
	return Action(ctx, tracer, name, append(opts, trace.WithNewRoot())...)
}

func Action(ctx context.Context, tracer trace.Tracer, name string, opts ...trace.SpanStartOption) (context.Context, trace.Span) {
	var parent ProcessingContext
	if p := ProcessingOperationFromContext(ctx); p.IsValid() {
		parent = *p
	}

	if opts == nil {
		opts = make([]trace.SpanStartOption, 0, 1)
	}

	opts = append(opts,
		trace.WithTimestamp(time.Now()),
	)

	if parent.IsValid() && parent.Foreign() {
		opts = append(opts, trace.WithAttributes(
			attribute.String("dpl.core.foreign_operation.trace_id", parent.TraceID().String()),
			attribute.String("dpl.core.foreign_operation.span_id", parent.SpanID().String()),
		))
	}

	ctx, span := tracer.Start(ctx, name, opts...)

	return ctx, span
}
```