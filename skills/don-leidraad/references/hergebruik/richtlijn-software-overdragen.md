# Richtlijn: Software beheerst overdragen

Als je software ontwikkelt die op enig moment door een andere developer, een
ander team of een andere organisatie verder ontwikkeld en/of onderhouden zal
worden, zorg je voor een beheerste overdracht. Je zorgt dat documentatie,
broncode en testmiddelen van een dusdanige kwaliteit en compleetheid zijn dat de
andere partij de software efficiënt en effectief kan onderhouden en/of
doorontwikkelen.

Als je software ontvangt van een andere partij om verder te onderhouden en/of
door te ontwikkelen, review je de documentatie, broncode en testmiddelen op
kwaliteit en compleetheid. Zodat je met vertrouwen de software kan onderhouden
en/of doorontwikkelen.

De developers, het team of de organisatie die de software overdraagt noemen we
de latende partij. De developers, het team of de organisatie die de software
ontvangt is de ontvangende partij.

Beide partijen maken samen met de eigenaar van de software afspraken over de
voorbereiding van de overdracht, de kennisoverdracht, de overdracht van de
software zelf en eventuele nazorg.

## Rationale: Waarom software beheerst overdragen?

Om te zorgen dat de software ook na overdracht van de ene naar de andere partij
efficiënt en effectief kan worden onderhouden en doorontwikkeld is het
belangrijk dat de kwaliteit van de broncode, documentatie en testmiddelen goed
is. Daarnaast is het belangrijk dat er voldoende tijd is voor het overdragen van
kennis omdat het vaak moeilijk is alle relevante kennis van software in
documentatie te vangen.

## Doelgroep: Wie zijn er betrokken bij het overdragen van software?

De volgende doelgroepen kunnen met het beheerst overdragen van software aan de
slag: de eigenaar van de software, developers en testers van de latende partij
en developers en testers van de ontvangende partij.

## Implementatie: Hoe draag je software beheerst over?

### Methoden en technieken

#### Fade-in/fade-out

Om te zorgen voor een goede kennisoverdracht draaien één of meer developers van
de ontvangende partij een tijdje mee bij de latende partij. Denk hierbij aan een
aantal sprints als er volgens Scrum wordt gewerkt. Na de overdracht werken één
of meer developers van de latende partij nog een tijdje mee bij de ontvangende
partij. Tenslote zijn één of meer developers van de latende partij tijdens de
nazorgperiode beschikbaar als vraagbaak.

#### NEN NPR 5325

De NEN Nederlandse Praktijkrichtlijn 5325 biedt een checklist van criteria
waaraan software, inclusief broncode, documentatie en testset, moet voldoen.
Deze criteria staan hieronder opgesomd. De paragraafnummers tussen haakjes
verwijzen naar de betreffende paragraaf in de NPR 5325.

1. De documentatie beschrijft de ontwikkel- en testomgeving die is toegepast
   (5.1),
1. De functionele documentatie beschrijft gegevensmodellen, functionele
   indeling, koppelingen, berichtdefinities en workflows/processen (5.2),
1. Als operationeel beheer onderdeel was van de dienstverlening: de operationele
   bedieningsinstructies beschrijven minimaal back-up/recovery, procedures bij
   calamiteiten, regelmatig terugkerende beheeractiviteiten en opstart- en
   afsluitprocedures (5.3),
1. De product backlog bevat de bekende bugs en wensen (5.4),
1. De broncode kent een gezonde balans tussen isolatie, cohesie en koppeling
   (6.1),
1. De broncode heeft een beperkte mate van duplicatie (6.2),
1. De broncode heeft een beperkte mate van complexiteit (6.3),
1. De broncode bevat geen of een beperkt aantal niet-afgeronde werkzaamheden
   ("todo's") (6.4).
1. De tests raken een voldoende groot deel van de broncode (code dekking) (7.1),
1. De tests raken een voldoende groot deel van de functionaliteit (functionele
   dekking) (7.2),
1. De onderkende productrisico's zijn gedekt (7.3),
1. Er is een regressietest beschikbaar (7.4),
1. Er is traceerbaarheid van eisen naar testgevallen (7.5), en
1. De testset is goed opgebouwd (7.6).

Merk op dat de criteria van de NPR 5325 niet altijd 100% meetbaar zijn. Waar
nodig scherpen de latende en ontvangende partij de criteria aan. Dit doe je
uiteraard ruim voor de overdracht.

### Tools

Voor het meten van de kwaliteit van de broncode kun je tools zoals SonarQube,
Sigrid of CAST gebruiken.

Voor het meten van de testdekking kun je testcoverage tools gebruiken. Zie de
[richtlijn geautomatiseerd testen](../duurzaamheid/richtlijn-geautomatiseerd-testen.md).

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Als je software overdraagt voldoet deze aan de criteria uit de NEN NPR 5325.
- Als je software krijgt overgedragen voldoet deze aan de criteria uit de NEN
  NPR 5325.
- Ontvangende en latende partij hebben afspraken gemaakt over de voorbereiding
  van de overdracht, de kennisoverdracht, de overdracht van de software zelf en
  de nazorg.

Wanneer ben je echt goed bezig?

- Je zorgt voor een warme overdracht door een of meer developers van de
  ontvangende partij voor de daadwerkelijke overdracht een tijdje te laten
  meedraaien bij de latende partij en door developers van de latende partij na
  de overdracht een tijdje te laten meewerken bij de ontvangende partij.
- Je toetst periodiek of je software voldoet aan de richtlijnen uit de NEN NPR
  5325, zelfs als er op korte termijn geen overdracht is voorzien.

## Wanneer is deze richtlijn van toepassing?

Als je software overdraagt aan een andere developer, een ander team, of een
andere organisatie die de ontvangende partij moet gaan onderhouden en/of
doorontwikkelen. Of als je software overgedragen krijgt van een andere partij
die je zelf gaat onderhouden en/of doorontwikkelen.

## Bronnen

### Wetten

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

- [NEN NPR 5325:2017 - Praktijkrichtlijn voor het overdragen van software](https://www.nen.nl/npr-5325-2017-nl-238298).

### Communities

Geen bekend.

### Literatuur

Geen bekend.

### Bronnen op developer.overheid.nl

Geen bekend.