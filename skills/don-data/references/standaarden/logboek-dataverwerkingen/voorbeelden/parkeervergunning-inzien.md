# Parkeervergunning - inzien

Een persoon heeft bij een gemeente een parkeervergunning in gebruik en wil de
data van deze vergunning bekijken.

## Uitgangspunten

- Het beschreven proces is een voorbeeld, het werkelijke proces kan anders
  verlopen.
- Het proces is een 'happy flow', dit betekent dat validaties en eventuele
  foutsituaties in dit voorbeeld niet in ogenschouw worden genomen.
- Autorisatieprocessen zijn in dit voorbeeld niet meegenomen.
- Een Loggingsregel wordt toegevoegd aan het logboek per **geheel** afgeronde
  transactie. Er wordt dus **geen** aparte logregel aangemaakt per ontvangen of
  verstuurd bericht.

## Globaal proces

1. Een persoon vraagt in zijn 'MijnOmgeving' van de gemeente om de bestaande
   parkeervergunningdata.
2. De 'MijnOmgeving' van de gemeente verzoekt de parkeervergunningapplicatie om
   de actuele parkeervergunningdata van de persoon.
3. Het parkeervergunningsysteem voert dit verzoek uit. Daarna verzendt de
   parkeervergunningapplicatie de gevraagde data naar de gemeente. Het
   parkeervergunningensysteem logt dat er data verzonden is naar de gemeente.
4. De gemeente toont de data aan de persoon en logt dat deze data is getoond aan
   de persoon.

Schematisch ziet dit proces er als volgt uit:

```mermaid
sequenceDiagram
    box ivory Burger
      participant B as Browser
    end

    box ivory Gemeente
      participant MO as MijnOmgeving
      participant L1 as Log Gemeente
    end

    box ivory Vergunningsoftware BV
      participant V as Parkeeradmin
      participant L2 as Log Vergunning
    end

    rect lavender
    B->>+MO: tonenVergunningenVraag
    MO->>V: opvragenVergunningenVraag
    V-->>MO: opvragenVergunningenAntwoord
    V->>L2: Log gegevensverwerking (opvragenVergunningen)
    MO-->>B: tonenVergunningenAntwoord
    MO->>L1: Log gegevensverwerking (tonenVergunningen)
    end
```

## Logging van data

De volgende data worden gelogd in de diverse logmomenten:

- **Log opvragenVergunningen (log vergunningenapplicatie)**

  | Attribuut                   | Waarde                                   |
  | --------------------------- | ---------------------------------------- |
  | `span_id`                   | 8451dcd9ede037cb                         |
  | `name`                      | opvragenVergunningen                     |
  | `parent_span_id`            | `<leeg>`                                 |
  | `trace_id`                  | ccf5064a324163ed939bfa09c2bcb210         |
  | `start_time`                | 2024-05-30 08:40:37.000                  |
  | `end_time`                  | 2024-05-30 08:40:37.000                  |
  | `status_code`               | OK                                       |
  | resource.name               | Parkeeradmin                             |
  | resource.version            | 2.1.6                                    |
  | attributeKey                | `dpl.core.processing_activity_id`        |
  | attributeValue              | rva:12f2ec2a-0cc4-3541-9ae6-219a178fcfe4 |
  | attributeKey                | `<leeg>`                                 |
  | attributeValue              | `<leeg>`                                 |
  | `foreign_operation.span_id` | 9f8971bfd093637d                         |

- **Log opvragenVergunningen (log gemeente)**

  | Attribuut        | Waarde                                   |
  | ---------------- | ---------------------------------------- |
  | `span_id`        | ccf5064a324163ed939bfa09c2bcb210         |
  | `name`           | tonenVergunningen                        |
  | `parent_span_id` | `<leeg>`                                 |
  | `trace_id`       | c7a26dcd0bee0c8900e2174c43c3393c         |
  | `start_time`     | 2024-05-30 10:40:37.821                  |
  | `end_time`       | 2024-05-30 10:40:37.845                  |
  | `status_code`    | OK                                       |
  | resource.name    | MijnOmgeving                             |
  | resource.version | 1.0.5                                    |
  | attributeKey     | `dpl.core.processing_activity_id`        |
  | attributeValue   | rva:11x2ec2a-0774-3541-9b16-21ba179fcf15 |
  | attributeKey     | `dpl.core.data_subject_id`               |
  | attributeValue   | rva:13j2ec27-0cc4-3541-9av6-219a178fcfe5 |

## Relatie tussen data

Om uiteindelijk alle data te kunnen rapporteren, is het van belang dat data op
een bepaalde manier aan elkaar gekoppeld is. In dit voorbeeld is de data op de
volgende manier gekoppeld:

![Relatie tussen gegevens parkeervergunning inzien](/img/logboek-dataverwerkingen/relatie-tussen-gegevens-parkeervergunning-inzien.png)

## Relatie met de standaard Logboek dataverwerkingen

De relatie met de doelstellingen die gesteld zijn in de standaard Logboek
dataverwerkingen worden, op basis van dit voorbeeld, als volgt concreet
gerealiseerd:

- **het wegschrijven van logs van dataverwerkingen:** In dit voorbeeld is het de
  betrokkene zelf die via een portaal zijn eigen data kan bekijken. Deze actie
  is een dataverwerking en wordt gelogd bij zowel de gemeenteapplicatie (data
  wordt getoond aan de betrokkene) als bij de vergunningenapplicatie
  (verstrekking specifieke informatie aan de gemeenteapplicatie).
- **het aan elkaar relateren van logs van dataverwerkingen:** Er zijn in dit
  voorbeeld twee applicaties nodig om het totaal aan gevraagde informatie te
  kunnen tonen aan de betrokkene. Beide applicaties hebben een logboek voor
  verwerkte data. Om een totaalbeeld van de gelogde data te kunnen construeren,
  is een relatie tussen de logs nodig. In dit voorbeeld wordt de koppeling
  gelegd door het `span_id` en `trace_id` uit het gemeentelogboek te linken aan
  het `foreign_operation.span_id` en `trace_id` uit het vergunningenlogboek.
- **het aan elkaar relateren van dataverwerkingen over de grenzen van
  systemen:** Naast het koppelen van logs van diverse applicaties, wordt ook een
  koppeling gelegd met het Register van verwerkingsactiviteiten. Dit gebeurt per
  applicatie op basis van het `processing_activity_id` (register) te koppelen
  aan `dpl.core.processing_activity_id` (logboek). De diverse registers hebben
  **geen** directe koppeling met elkaar.

Standaard Logverwerkingen: **paragraaf 3.3.1 Gedrag**

1. _De applicatie MOET een Trace starten voor iedere Dataverwerking waarvan nog
   geen Trace bekend is._ Bij elke start van een verwerking wordt een `trace_id`
   aangemaakt. Bijvoorbeeld: in het voorbeeld komt er een bericht binnen bij de
   'MijnOmgeving' van de gemeente (opvragenVergunningenVraag). Er wordt direct
   een `trace_id` aangemaakt.
2. _De applicatie MOET voor iedere Dataverwerking een logregel wegschrijven in
   een Logboek. Log Sampling is niet toegestaan._ Een dataverwerking wordt
   opgeslagen als deze volledig is afgerond. In het voorbeeld is te zien dat een
   logregel wordt geschreven op het moment dat de vraag- en het antwoordbericht
   zijn afgerond.
3. _De applicatie MOET bijhouden of een Dataverwerking geslaagd of mislukt is en
   dit per Dataverwerking als status meegeven aan het Logboek._ Bij elke
   logregel in het voorbeeld staat de `status_code` vermeld ('OK').
4. _Als een Dataverwerking meerdere Betrokkenen heeft dan MOET de applicatie
   voor iedere betrokkene een aparte logregel wegschrijven. Een logregel kan
   naar 0 of 1 betrokkenen verwijzen._ In het voorbeeld gaat het om één
   betrokkene (`dpl.core.data_subject_id`), er wordt steeds één logregel
   aangemaakt.
5. _Als een applicatie aangeroepen kan worden vanuit een andere applicatie MOET
   de applicatie Trace Context metadata accepteren bij een dergelijke aanroepen
   deze metadata kunnen omzetten naar een foreign_operation bericht._ Bij een
   externe verwerking (bijvoorbeeld opvragenVergunningen) geeft de
   'MijnOmgeving' de `trace_id` en `span_id` mee aan de Vergunningenapplicatie.
   De vergunningenapplicatie registreert de `trace_id`, en `span_id` als
   `foreign_operation.span_id`.