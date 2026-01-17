# Richtlijn: Werk open source

Als overheid werken we zo veel mogelijk open source. We ontwikkelen software die
iedereen kan inzien, gebruiken en verbeteren. Dit bevordert transparantie,
stimuleert hergebruik en verhoogt de kwaliteit van overheidssoftware.

## Rationale: Waarom open source werken?

**Transparantie:** Door open source te werken, kunnen burgers en andere partijen
zien welke software de overheid gebruikt en hoe deze werkt. Dit vergroot het
vertrouwen in de overheid en maakt het mogelijk om de werking van
overheidssoftware te controleren.

**Hergebruik:** Open source software kan door andere overheidsorganisaties
hergebruikt worden. Dit voorkomt dubbel werk en bespaart kosten. Als meerdere
organisaties aan dezelfde software werken, wordt de kwaliteit hoger en kunnen
kosten gedeeld worden.

**Beveiliging:** Wanneer broncode openbaar is, kunnen meer ogen naar de code
kijken. Beveiligingsproblemen worden sneller ontdekt en opgelost. Dit principe
heet "many eyes make all bugs shallow".

**Innovatie:** Open source bevordert innovatie. Anderen kunnen de software
verbeteren, nieuwe features toevoegen of de software aanpassen voor hun eigen
gebruik. Dit leidt tot snellere ontwikkeling en betere software.

**Leveranciersonafhankelijkheid:** Met open source software ben je minder
afhankelijk van één leverancier. Je kunt altijd de code zelf aanpassen of een
andere partij inschakelen voor onderhoud.

## Doelgroep: Wie zijn er betrokken bij open source?

De volgende doelgroepen kunnen met open source aan de slag: developers,
architecten, product owners, inkoop en management.

Developers schrijven en publiceren open source code. Architecten bepalen welke
open source componenten gebruikt worden. Product owners bepalen het open source
beleid voor hun product. Inkoop zorgt dat leveranciers open source leveren waar
mogelijk. Management stelt organisatiebreed open source beleid vast.

## Implementatie: Hoe werk je open source?

### Methoden en technieken

#### "Open, tenzij" principe hanteren

De overheid hanteert het principe "open, tenzij". Dit betekent dat software
standaard open source ontwikkeld en gepubliceerd wordt, tenzij daar zwaarwegende
redenen tegen zijn (zoals nationale veiligheid of privacy).

#### Open source repositories gebruiken

Publiceer je code op een publiek toegankelijk platform zoals Codeberg, GitHub,
GitLab of Gitea. Zorg dat de repository goed gedocumenteerd is met een README,
licentie en contributing guidelines.

#### Open source licenties toepassen

Gebruik een geaccepteerde open source licentie zoals EUPL (European Union Public
License), MIT, Apache 2.0 of GPL. De EUPL is specifiek ontwikkeld voor overheden
in de EU en wordt aanbevolen.

#### Inner source toepassen

Als je nog niet klaar bent om volledig open source te werken, begin dan met
inner source: open source principes toepassen binnen je organisatie. Dit helpt
de cultuurverandering en leert teams open source werken.

### Tools

#### Git-platform voor code hosting

Gebruik Codeberg, GitHub, GitLab of een andere Git-based platform voor het
hosten van je open source code. Deze platforms bieden functionaliteit voor
versiebeheer, issue tracking en pull requests.

#### Publiccode.yml voor metadata

Gebruik een `publiccode.yml` bestand om metadata over je software te publiceren.
Dit maakt het voor anderen makkelijker om je software te vinden en te
hergebruiken.

#### Open source vulnerability scanners

Gebruik tools zoals Dependabot, Renovate of Snyk om kwetsbaarheden in je open
source dependencies te detecteren.

### Gerelateerde richtlijnen

- [Richtlijn repository opzetten](./richtlijn-repository-policy.md)

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je publiceert je code onder een open source licentie.
- Je hebt een publieke repository met documentatie.
- Je accepteert contributions van buiten je organisatie.
- Je gebruikt open source dependencies waar mogelijk.

Wanneer ben je echt goed bezig?

- Je hebt een actieve community van contributors.
- Je publiceert alle nieuwe software standaard open source.
- Je draagt actief bij aan andere open source projecten.
- Je gebruikt tools om open source kwaliteit te borgen (zoals CII Best Practices
  Badge).

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is van toepassing op alle nieuwe softwareontwikkeling door of
voor de overheid, tenzij er zwaarwegende redenen zijn om dit niet te doen (zoals
nationale veiligheid, privacy of intellectueel eigendom van derden).

## Bronnen

### Wet- en regelgeving

Geen bekend.

### Beleid

- [Programma Open Overheid](https://www.rijksoverheid.nl/onderwerpen/digitale-overheid/open-overheid)

### Standaarden

- [Publiccode.yml](/kennisbank/open-source/standaarden/publiccode-yml)

### Communities

- [Code for NL](/communities/code-for-nl)
- [Common Ground](/communities/common-ground)

### Literatuur

- [GitHub: Building communities](https://docs.github.com/en/communities)
- [Standaard voor Publieke Code](https://standaardvoorpubliekecode.nl/)
- [GitHub's opensource.guide](https://opensource.guide/)

### Bronnen op developer.overheid.nl

- [Open source hoofdstuk](/kennisbank/open-source)
- [Publiccode.yml](/kennisbank/open-source/standaarden/publiccode-yml)