# Richtlijn: Denk na over duurzaamheid

Duurzaam beheer betekent dat je ervoor zorgt dat je web-applicatie veilig,
efficiënt en schaalbaar blijft over de gehele levenscyclus.

## Rationale: Waarom nadenken over duurzaamheid?

Overheidssoftware moet vaak tientallen jaren blijven functioneren. Duurzaam
beheer zorgt ervoor dat de applicatie gedurende de gehele levenscyclus veilig,
efficiënt en schaalbaar blijft. Dit voorkomt dat software snel veroudert en
garandeert dat de oplossing ook in de toekomst blijft voldoen aan de steeds
veranderende eisen van gebruikers, technologie en wetgeving.

Door duurzame softwarepraktijken toe te passen, zoals regelmatige updates en
goed beheer, kunnen onverwachte kosten voor het oplossen van
beveiligingsproblemen of het herschrijven van verouderde systemen worden
voorkomen. Dit maakt het voor de overheid financieel haalbaarder om software op
de lange termijn te onderhouden.

De overheid behandelt vaak gevoelige informatie, zoals persoonlijke gegevens van
burgers. Duurzaam beheer waarborgt dat de software voortdurend
beveiligingsupdates ontvangt en kwetsbaarheden tijdig worden opgelost, zodat de
privacy en veiligheid van data gewaarborgd blijven.

De wetgeving verandert regelmatig, en dit geldt ook voor wetgeving rondom
privacy, gegevensbeveiliging en digitale toegankelijkheid. Duurzaam beheer houdt
in dat de software kan worden aangepast aan nieuwe wettelijke vereisten zonder
grote herzieningen, waardoor de overheid compliant blijft met wet- en
regelgeving.

## Doelgroep: Wie zijn er betrokken bij duurzaamheid?

De volgende doelgroepen kunnen met duurzaamheid aan de slag: developers,
testers, beheerders, security officers en kwaliteitsmanagers.

Developers investeren in geautomatiseerde tests en schrijven onderhoudbare code.
Testers ontwikkelen en onderhouden de testautomatisering. Beheerders richten
monitoring en logging in. Security officers zorgen dat beveiligingsupdates
tijdig worden doorgevoerd. Kwaliteitsmanagers bewaken de kwaliteit van de
software met tools zoals Quality-time.

## Implementatie: Hoe implementeer je duurzaamheid?

### Methoden en technieken

#### Geautomatiseerd testen

Door te investeren in geautomatiseerde testen kun je de applicaties met minder
risico aanpassen en gaan ze langer mee. Geautomatiseerde tests vangen regressies
op en geven ontwikkelaars vertrouwen bij het doorvoeren van wijzigingen.

#### Maak organisatiebrede architectuurkeuzes en draag deze uit

Door binnen je organisatie een bepaalde mate van standaardisering toe te passen  
maak je effectiever gebruik van beschikbare middelen en kennis, en vergroot je de 
beheerbaarheid.

#### Continuous monitoring

Door monitoring in te richten voor applicaties die je in beheer hebt krijg je
inzicht in technical debt en andere factoren waar je rekening mee dient te
houden als organisatie. Monitor performance, beschikbaarheid en fouten.

#### Structured logging

Voor het beheer van applicaties is het van groot belang dat de logging op orde
is om te kunnen debuggen. Zorg ervoor dat logging op een toegankelijke manier is
georganiseerd en dat logs voldoende context bevatten.

### Tools

#### Test automation frameworks

Voor geautomatiseerd testen gebruik je frameworks zoals JUnit, pytest, Jest of
Selenium, afhankelijk van je technologie stack.

#### Monitoring tools

Voor monitoring gebruik je tools zoals Prometheus, Grafana, ELK stack
(Elasticsearch, Logstash, Kibana) of cloud-native monitoring oplossingen.

#### Quality management tools

Quality-time is een open source tool die je kan helpen de kwaliteit van je
maatwerksoftware te bewaken en technical debt te managen.

### Gerelateerde richtlijnen

- [Richtlijn geautomatiseerd testen](richtlijn-geautomatiseerd-testen.md)
- [Richtlijn maak (architectuur)keuzes en draag deze uit](richtlijn-arch-keuzes.md).

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je hebt geautomatiseerde tests die regelmatig draaien.
- Je monitort de performance en beschikbaarheid van je applicaties.
- Je hebt structured logging geïmplementeerd.

Wanneer ben je echt goed bezig?

- Je meet en bewaakt technical debt structureel met tools zoals Quality-time.
- Je hebt alerts ingesteld die automatisch waarschuwen bij problemen.
- Je voert regelmatig dependency updates uit om kwetsbaarheden te voorkomen.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is van toepassing op alle software die in beheer is en langere
tijd in gebruik zal blijven, wat voor vrijwel alle overheidssoftware geldt.

## Bronnen

### Wet- en regelgeving

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

Geen bekend.

### Communities

Geen bekend.

### Literatuur

Geen bekend.

### Bronnen op developer.overheid.nl

- [Quality-time](https://quality-time.readthedocs.io/en/latest/)
- [Quality-time op developer.overheid.nl](/kennisbank/infra/tools/quality-time)