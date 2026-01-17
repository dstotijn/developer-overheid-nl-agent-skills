# NL GOV Profile for CloudEvents

## Van intake tot verplichte standaard

CloudEvents is een internationale standaard voor het uniform beschrijven van
events in [eventgedreven architecturen](./eda.md). Dankzij deze standaard kunnen
applicaties eenvoudiger informatie uitwisselen over gebeurtenissen (bijvoorbeeld
een adreswijziging of een vergunningaanvraag). In Nederland wordt CloudEvents nu
voorzien van een nationaal profiel: het
[**NL GOV profile for CloudEvents**](https://gitdocumentatie.logius.nl/publicatie/notificatieservices/CloudEvents-NL/).

---

![CloudEvents logo](https://github.com/cncf/artwork/blob/main/projects/cloudevents/horizontal/color/cloudevents-horizontal-color.png?raw=true)

---

### Besluitvorming Forum Standaardisatie

- **4 december 2024 – Intakefase**  
  Het Forum Standaardisatie stemde in met het intakeadvies om het _"NL GOV
  profile for CloudEvents"_ in procedure te nemen voor plaatsing op de lijst met
  verplichte standaarden (“Pas toe of leg uit”).  
  Bron: [intakeadvies NL GOV profile for CloudEvents (PDF)](https://www.forumstandaardisatie.nl/sites/default/files/BFS/3-lijsten/standaarden/cloudevents/20241204-intakeadvies-NL-GOV-profile-for-CloudEvents.pdf).

- **19 juni 2025 – Expertadvies**  
  De expertgroep adviseerde positief over opname van de standaard. Het profiel
  sluit nauw aan op internationale CloudEvents-specificaties, maar maakt ze
  concreet toepasbaar binnen de Nederlandse overheid.  
  Bron: [expertadvies NL GOV profile for CloudEvents (PDF)](https://www.forumstandaardisatie.nl/sites/default/files/BFS/3-lijsten/standaarden/cloudevents/20250619-Expertadvies-NL-GOV-profile-for-CloudEvents.pdf).

- **25 september 2025 – Forumadvies**  
  Het Forum Standaardisatie heeft ingestemd met het advies aan het
  [OBDO](https://pgdi.nl/) om het _"NL GOV profile for CloudEvents"_ verplicht
  te stellen (“Pas toe of leg uit”). Daarnaast is Logius het predicaat
  **‘Uitstekend beheer’** toegekend voor deze standaard.

## Wat is het NL GOV profile for CloudEvents?

Het Nederlandse profiel geeft richtlijnen voor hoe overheidsorganisaties
CloudEvents moeten gebruiken, zodat er interoperabiliteit ontstaat tussen
systemen en sectoren. Het NL GOV profiel specificeert onder meer:

- Uniforme naamgeving en metadata.
- Afspraken over payload en headers.
- Toepassing in notificatieservices van de overheid.

**Een voorbeeld van een CloudEvent dat is opgenomen in de standaard:**

```JSON
{
  "specversion": "1.0",
  "type": "nl.overheid.zaken.zaakstatus-gewijzigd",
  "source": "urn:nld:oin:00000001823288444000:systeem:BRP-component",
  "subject": "999990342",
  "id": "f3dce042-cd6e-4977-844d-05be8dce7cea",
  "time": "2021-12-10T17:31:00Z",
  "nlbrpnationaliteit": "0083",
  "geheimnummer": null,
  "dataref": "https://gemeenteX/api/persoon/999990342",
  "sequence": "1234",
  "sequencetype": "integer",
  "datacontenttype": "application/json",
  "data": {
    "bsn": "999990342",
    "naam": "Jan Jansen",
    "gecontroleerd": "ja"
  }
}
```

De technische specificatie is beschikbaar via Logius: -
[CloudEvents NL – technische documentatie](https://gitdocumentatie.logius.nl/publicatie/notificatieservices/CloudEvents-NL/).  
Het
voorbeeld en de toelichting daarop zijn beschikbaar op
[gitdocumentatie.logius.nl/publicatie/notificatieservices/CloudEvents-NL/#example](https://gitdocumentatie.logius.nl/publicatie/notificatieservices/CloudEvents-NL/#example).

Naast het Nederlandse profiel zijn ook een drietal handreikingen gemaakt die
toelichten hoe het NL GOV profiel is toe te passen bij gebruik van het:

- [JSON gegevensformaat](https://github.com/Logius-standaarden/CloudEvents-NL-Guidelines/blob/develop//NL-GOV-Guideline-for-CloudEvents-JSON.md)
- [HTTP transportprotocol](https://github.com/Logius-standaarden/CloudEvents-NL-Guidelines/blob/develop/NL-GOV-Guideline-for-CloudEvents-HTTP.md)
- [Webhook interactiepatroon](https://github.com/Logius-standaarden/CloudEvents-NL-Guidelines/blob/develop//NL-GOV-Guideline-for-CloudEvents-Webhook.md).

> Deze handreikingen verwijzen naar door de Serverless Working Group ontwikkelde
> specificaties. Doel daarvan is om verdergaande standaardisatie te
> bewerkstelligen en interoperabiliteit te vergroten.

## Waarom belangrijk?

Het gebruik van CloudEvents en het NL GOV profiel helpt de overheid om:

- **Real-time** en **event-driven** te werken in ketens en ecosystemen.
- **Losse koppelingen** te realiseren tussen systemen, waardoor onderhoud en
  innovatie eenvoudiger worden.
- **Interoperabiliteit** te garanderen, zodat alle overheidsorganisaties
  dezelfde taal spreken in event-uitwisseling.

## Meer informatie

- [NL GOV profile for CloudEvents – Forum Standaardisatie](https://www.forumstandaardisatie.nl/open-standaarden/nl-gov-profile-cloudevents)
- [CloudEvents NL – Logius documentatie](https://gitdocumentatie.logius.nl/publicatie/notificatieservices/CloudEvents-NL/)
- [CloudEvents NL - Guidelines for HTTP, JSON & Webhooks](https://gitdocumentatie.logius.nl/publicatie/notificatieservices/guidelines/)
- [De internationale specificatie en documentatie van Cloudevents](https://cloudevents.io/)