# Registratie verhuizing – Opvragen meerdere BSN's

Deze case beschrijft de samenstelling van een huishouding op een bepaald adres.
De beschrijving is functioneel zo eenvoudig mogelijk, een burger komt aan de
balie en er is geen sprake van wijzigingen in de huishouding.

## Uitgangspunten

- Het beschreven proces is een voorbeeld, het werkelijke proces kan anders
  verlopen.
- Het proces is een 'happy flow', dit betekent dat validaties en eventuele
  foutsituaties in dit voorbeeld niet in ogenschouw worden genomen.
- Autorisatieprocessen zijn in dit voorbeeld niet meegenomen.
- Een Loggingsregel wordt toegevoegd aan het logboek per **geheel** afgeronde
  transactie. Er wordt dus **geen** aparte logregel aangemaakt per ontvangen of
  verstuurd bericht.
- Het is optioneel om het BSN (`dpl.core.data_subject_id`) te versleutelen ten
  behoeve van extra databeveiliging. In dit voorbeeld wordt versleuteling van
  data toegepast.

## Globaal proces

Schematisch ziet dit proces er als volgt uit:

1. De Baliemedewerker voert adres van de burger in.
2. De Browser vraagt om persoonsdata bij de gemeentelijke Balieapplicatie.
3. De gemeentelijke Balieapplicatie vraag persoonsdata bij het BRP-systeem.
4. Het BRP systeem stuurt gevraagde data naar de gemeentelijke Balieapplicatie
   en logt de aanvraag.
5. De gemeentelijke Balieapplicatie stuurt de data naar de Browser en worden
   getoond aan de Baliemedewerker. De aanvraag wordt gelogd door de
   Balieapplicatie.

Schematisch ziet dit proces er als volgt uit:

```mermaid
sequenceDiagram
    box ivory Baliemedewerker
      participant B as Browser
    end

    box ivory Gemeente
      participant BA as Balieapplicatie
      participant L1 as Log Gemeente
    end

    box ivory BRP Registratie
      participant BR as BRP
      participant L2 as Log BRP
    end

    rect lavender
    B->>+BA: tonenNAWGegevensVraag
    BA->>BR: opvragenPersoonsgegevensVraag
    BR-->>BA: opvragenPersoonsgegevensAntwoord
    BR->>L2: Log gegevensverwerking (opvragenPersoonsgegevens)
    BA-->>B: tonenNAWGegevensAntwoord
    BA->>L1: Log gegevensverwerking (tonenNAWGegegevens)
    end
```

## Logging van data

De volgende data worden gelogd in de diverse logmomenten:

- **Log opvragenPersoonsgegevens (log BRP) persoon 1**

  | Attribuut                   | Waarde                                |
  | --------------------------- | ------------------------------------- |
  | `span_id`                   | 7a22eb38-bca6-463f-9955-54ab040287cb  |
  | `name`                      | opvragenPersoonsgegevens              |
  | `parent_span_id`            | `<leeg>`                              |
  | `trace_id`                  | c6adf4df949d03c662b53e95debdc411      |
  | `start_time`                | 2024-07-29 08:16:49.000               |
  | `end_time`                  | 2024-07-29 08:16:49.000               |
  | `status_code`               | OK                                    |
  | resource.name               | BRP                                   |
  | resource.version            | 2.0                                   |
  | attributeKey                | `dpl.core.processing_activity_id`     |
  | attributeValue              | 12f2ec2a-0cc4-3541-9ae6-219a178fcfe4  |
  | `foreign_operation.span_id` | b2e339a595246e01                      |
  | <u>BSN 1</u>                | `<leeg>`                              |
  | attributeKey                | `dpl.core.data_subject_id`            |
  | attributeValue              | ddj2ey299-0cf4-3541-9ar6-21ia178fcfrr |
  | `span_id`                   | r2e3229059BG246e01                    |
  | `parent_span_id`            | 7a22eb38-bca6-463f-9955-54ab040287cb  |

- **Log opvragenPersoonsgegevens (log BRP) persoon 2**

  | Attribuut                   | Waarde                                  |
  | --------------------------- | --------------------------------------- |
  | `span_id`                   | 7a22eb38-bca6-463f-9955-54ab040287cb    |
  | `name`                      | opvragenPersoonsgegevens                |
  | `parent_span_id`            | `<leeg>`                                |
  | `trace_id`                  | c6adf4df949d03c662b53e95debdc411        |
  | `start_time`                | 2024-07-29 08:16:49.000                 |
  | `end_time`                  | 2024-07-29 08:16:49.000                 |
  | `status_code`               | OK                                      |
  | resource.name               | BRP                                     |
  | resource.version            | 2.0                                     |
  | attributeKey                | `dpl.core.processing_activity_id`       |
  | attributeValue              | 12f2ec2a-0cc4-3541-9ae6-219a178fcfe4    |
  | `foreign_operation.span_id` | b2e339a595246e01                        |
  | <u>BSN 2</u>                | `<leeg>`                                |
  | attributeKey                | `dpl.core.data_subject_id`              |
  | attributeValue              | f4j2ey299-3er4-3aa41-9ar6-21ia178fc3tyy |
  | `span_id`                   | 9as5y3t-3ca7-463f-wwt9a5-54ab0402rft    |
  | `parent_span_id`            | 7a22eb38-bca6-463f-9955-54ab040287cb    |

- **Log tonenNAWGegevens (log gemeente) persoon 1**

  | Attribuut        | Waarde                               |
  | ---------------- | ------------------------------------ |
  | `span_id`        | b2e339a595246e01                     |
  | `name`           | tonenNAWGegevens                     |
  | `parent_span_id` | `<leeg>`                             |
  | `trace_id`       | c6adf4df949d03c662b53e95debdc411     |
  | `start_time`     | 2024-07-29 10:16:49.690              |
  | `end_time`       | 2024-07-29 10:16:49.723              |
  | `status_code`    | OK                                   |
  | resource.name    | Balieapp                             |
  | resource.version | 1.0.5                                |
  | attributeKey     | `dpl.core.processing_activity_id`    |
  | attributeValue   | 11x2ec2a-0774-3541-9b16-21ba179fcf15 |
  | <u>BSN 1</u>     | `<leeg>`                             |
  | attributeKey     | `dpl.core.data_subject_id`           |
  | attributeValue   | 13j2ec27-0cc4-3541-9av6-219a178fcfe5 |
  | `span_id`        | 42f33gfa595246ert                    |
  | `parent_span_id` | b2e339a595246e01                     |

- **Log tonenNAWGegevens (log gemeente) persoon 2**

  | Attribuut        | Waarde                               |
  | ---------------- | ------------------------------------ |
  | `span_id`        | b2e339a595246e01                     |
  | `name`           | tonenNAWGegevens                     |
  | `parent_span_id` | `<leeg>`                             |
  | `trace_id`       | c6adf4df949d03c662b53e95debdc411     |
  | `start_time`     | 2024-07-29 10:16:49.690              |
  | `end_time`       | 2024-07-29 10:16:49.723              |
  | `status_code`    | OK                                   |
  | resource.name    | Balieapp                             |
  | resource.version | 1.0.5                                |
  | attributeKey     | `dpl.core.processing_activity_id`    |
  | attributeValue   | 11x2ec2a-0774-3541-9b16-21ba179fcf15 |
  | <u>BSN 2</u>     | `<leeg>`                             |
  | attributeKey     | `dpl.core.data_subject_id`           |
  | attributeValue   | 342ec27-aa41-dav6-219a178f5ty6       |
  | `span_id`        | aef53rfa59e240ert                    |
  | `parent_span_id` | b2e339a595246e01                     |

## Relatie tussen data

Om uiteindelijk alle data te kunnen rapporteren, is het van belang dat data op
een bepaalde manier aan elkaar gekoppeld zijn. In dit voorbeeld zijn de data op
de volgende manier gekoppeld:

![Relatie tussen gegevens registratie verhuizing](/img/logboek-dataverwerkingen/relatie-tussen-gegevens-registratie-verhuizing.png)

## Relatie met de standaard Logboek dataverwerkingen

De relatie met de doelstellingen die gesteld zijn in de standaard Logboek
dataverwerkingen worden, op basis van dit voorbeeld, als volgt concreet
gerealiseerd:

- **het wegschrijven van logs van dataverwerkingen:** In dit voorbeeld is het de
  Baliemedewerker die via een Balieapplicatie de data van een Betrokkene kan
  bekijken. Deze acties zijn dataverwerkingen en worden gelogd bij zowel de
  Balieapplicatie als bij het BRP-systeem.

- **het aan elkaar relateren van logs van dataverwerkingen:** Er zijn in dit
  voorbeeld twee applicaties nodig om het totaal aan gevraagde informatie te
  kunnen tonen aan de betrokkene. Beide applicaties hebben een logboek voor
  verwerkte data. Om een totaalbeeld van de gelogde data te kunnen construeren,
  is een relatie tussen de logs nodig. In dit voorbeeld wordt de koppeling
  gelegd door het `span_id` en `trace_id` (gemeentelogboek) te linken aan het
  `foreign_operation.span_id` en `foreign_operation.trace_id` (BRP-logboek). De
  aanroep van de gemeente-applicatie naar het BRP betreft één opvraag op basis
  van één adres, één `span_id` en één `trace_id`. Het resultaat is meervoudig en
  moeten naar dezelfde `span_id` en `trace_id` leiden van de
  gemeente-applicatie. Het onderscheid zit in de verschillende BSN's van de
  personen die via een `parent_span_id` gekoppeld zijn.

- **het aan elkaar relateren van dataverwerkingen over de grenzen van
  systemen:** Naast het koppelen van logs van diverse applicaties, wordt ook een
  koppeling gelegd met het Register van verwerkingsactiviteiten. Dit gebeurt per
  applicatie op basis van het `processing_activity_id` (register) te koppelen
  aan `dpl.core.processing_activity_id` (logboek). De diverse registers hebben
  **geen** directe koppeling met elkaar.

### Paragraaf 3.3.1 Gedrag

1. _De applicatie MOET een Trace starten voor iedere Dataverwerking waarvan nog
   geen Trace bekend is._ Bij elke start van een verwerking wordt een `trace_id`
   aangemaakt. Bijvoorbeeld: in het voorbeeld komt er een bericht binnen bij de
   Balieapplicatie van de gemeente (tonenNAWGegevens). Er wordt direct een
   `trace_id` aangemaakt.
2. _De applicatie MOET voor iedere Dataverwerking een logregel wegschrijven in
   een Logboek. Log Sampling is niet toegestaan._ Een dataverwerking wordt
   opgeslagen als deze volledig is afgerond. In het voorbeeld is te zien dat
   logregels worden geschreven op het moment dat de vraag- en het
   antwoordbericht zijn afgerond.
3. _De applicatie MOET bijhouden of een Dataverwerking geslaagd of mislukt is en
   dit per Dataverwerking als status meegeven aan het Logboek._ Bij elke
   logregel in het voorbeeld staat de `status_code` vermeld ('OK').
4. _Als een Dataverwerking meerdere Betrokkenen heeft dan MOET de applicatie
   voor iedere betrokkene een aparte logregel wegschrijven. Een logregel kan
   naar 0 of 1 betrokkenen verwijzen._ In het voorbeeld gaat het om twee
   betrokkenen (`dpl.core.data_subject_id`), er wordt één logregel aangemaakt
   per BSN.
5. _Als een applicatie aangeroepen kan worden vanuit een andere applicatie MOET
   de applicatie Trace Context metadata accepteren bij een dergelijke aanroepen
   deze metadata kunnen omzetten naar een foreign_operation bericht._ Bij een
   externe verwerking (bijvoorbeeld opvragenPersoonsgegevens) geeft de
   Balieapplicatie de `trace_id` en `span_id` mee aan het BRP-systeem. Het
   BRP-systeem registreert de `trace_id`, en `span_id` als
   `foreign_operation.span_id`.