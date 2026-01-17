# Webhooks

Steeds meer overheidsorganisaties bouwen API’s om data en processen beschikbaar
te stellen. Vaak wordt gewerkt met het bekende request-response patroon van
REST. Toch is er een groeiende behoefte aan real-time notificaties: denk aan een
melding zodra er een nieuw document beschikbaar is, of wanneer een status van
een aanvraag verandert.

Een **webhook** is een beproefde manier om dit te realiseren. Met webhooks kan
een systeem zelf een bericht (event) sturen naar een ander systeem zodra er iets
verandert, in plaats van dat de afnemer steeds moet "poll-en" of er nieuwe data
is.

## Wat zijn webhooks?

Webhooks zijn een eenvoudige manier om systemen real-time te koppelen.

Een webhook is in feite een **HTTP-callback**. Dat betekent dat een producer
(bijvoorbeeld een registratiesysteem) een POST-request verstuurt naar een vooraf
opgegeven URL van een consumer. Die URL fungeert als “luisterend eindpunt” en
ontvangt de melding zodra er iets gebeurt.

**Kenmerken van webhooks:**

- **Event-driven**: berichten worden verstuurd zodra er iets gebeurt.
- **Push-mechanisme**: de producer “duwt” de melding naar de consumer.
- **Lichtgewicht**: meestal in de vorm van een kleine JSON-payload.
- **Eenvoudig te implementeren**: werkt via standaard HTTP.

## Voorbeeld

Stel: een gemeente gebruikt een zaaksysteem waarin de status van een
vergunningaanvraag kan wijzigen. Een andere applicatie (bijvoorbeeld een
publieksportaal) wil altijd direct up-to-date zijn.

1. Het portaal registreert een webhook-URL bij het zaaksysteem.
2. Zodra de status verandert naar bijvoorbeeld _“vergunning verleend”_,
   verstuurt het zaaksysteem een POST naar die URL.
3. Het portaal ontvangt het bericht en kan direct de nieuwe status tonen aan de
   burger.

Een voorbeeld van een payload (`data` attribuut in CloudEvents) kan er zo
uitzien:

```json
{
  "event": "vergunning.status.veranderd",
  "zaakId": "12345",
  "oudeStatus": "in_behandeling",
  "nieuweStatus": "vergunning_verleend",
  "timestamp": "2025-09-23T13:45:00Z"
}
```

## Beveiliging

Omdat webhooks vaak publieke endpoints aanspreken, is beveiliging essentieel.
Veelgebruikte methoden zijn:

- **JWT tokens**: meegeven van gesigned token in de header, zodat de ontvanger
  de payload kan verifiëren.
- **Opaque tokens**: meegeven van een geheim in de header, zodat de ontvanger de
  afzender kan verifiëren.
- **Digitale handtekeningen**: de payload wordt ondertekend, waardoor
  integriteit en authenticiteit kunnen worden gecontroleerd.
- **HTTPS**: altijd gebruiken om transportbeveiliging te garanderen.

Meer informatie hierover vind je ook in de richtlijnen van de
[NL API Strategie](https://developer.overheid.nl/communities/kennisplatform-apis/).

## Webhooks en de API-strategie

Binnen de Nederlandse API-strategie worden webhooks gezien als het belangrijkste
**event-driven patroon**. Voor lichte notificaties zijn webhooks ook de snelste
en goedkoopste oplossing. Voor complexere scenario’s, zoals veel events of hoge
betrouwbaarheidseisen, kan worden gekeken naar alternatieven als:

- **Server-Sent Events (SSE)** - broadcasting van actuele informatie
- **WebSockets** - een open kanaal voor streams van data Voor interoperabiliteit
  van berichten is er CloudEvents, een gestandaardiseerd eventformaat dat ook
  met webhooks gecombineerd kan worden.
- **CloudEvents** - gestructureerde berichtafhandeling

Webhooks zijn ook eenvoudig op te nemen in het API-ontwerp door ze te
specificeren in de Open API Specification (OAS).

```YAML
openapi: 3.1.0
info:
  title: Payment Webhook API
  version: "1.0.0"
  description: |
    Voorbeeld van een webhook definitie in OAS 3.1.
    Deze webhook wordt aangeroepen wanneer een betaling is geslaagd.
webhooks:
  paymentSucceeded:
    post:
      summary: "Webhook ontvangen bij succesvolle betaling"
      description: |
        Deze webhook wordt door de betalingsprovider aangeroepen
        en bevat event metadata in CloudEvents headers (binary mode).
      requestBody:
        required: true
        content:
          application/cloudevents+json:
            schema:
              type: object
              properties:
                amount:
                  type: number
                  description: Salaris
                  example: 12345.67
                currency:
                  type: string
                  description: Valuta
                  example: EUR
      parameters:
```

## Voordelen en aandachtspunten

### Voordelen

- Directe notificaties → systemen blijven actueel.
- Minder belasting → geen continue polling nodig.
- Eenvoudig → standaard webtechnieken (HTTP/JSON).

### Aandachtspunten

- **Betrouwbaarheid**: wat gebeurt er als een webhook-call faalt? Retries zijn
  vaak nodig.
- **Beveiliging**: endpoints moeten goed beschermd zijn.
- **Beheer**: documenteer welke events er bestaan en hoe ze eruit zien.

## Tot slot

Webhooks bieden een laagdrempelige manier om systemen real-time te koppelen.
Zeker in overheidscontext, waar informatie actueel en betrouwbaar beschikbaar
moet zijn voor burgers en ketenpartners, zijn webhooks een waardevolle
aanvulling op REST-API’s.

Voor meer informatie:

- [NL API Strategie – Eventgedreven werken](https://developer.overheid.nl/communities/kennisplatform-apis/)
- [CloudEvents standaard bij Geonovum](https://www.gemmaonline.nl/wiki/De_CloudEvents_standaard)
- [Server-sent events wiki](https://en.wikipedia.org/wiki/Server-sent_events)
- [WebSocket wiki](https://en.wikipedia.org/wiki/WebSocket)