# Richtlijn: Ontwikkel duurzame software door te investeren in geautomatiseerde tests

Bij **handmatige** tests bedient een mens de applicatie en vergelijkt het
werkelijke gedrag van een applicatie met het verwachte gedrag. Bij
**geautomatiseerde** tests voert een ander stuk software deze activiteiten uit.
Deze software bestaat vaak uit een 'test runner' en 'testscripts'. De
testscripts bedienen de applicatie (of stukjes daarvan) en vergelijken het
werkelijke gedrag met het verwachte gedrag van de applicatie. De test runner
voert de testscripts uit.

We onderscheiden testscripts die een hele applicatie bedienen en controleren en
testscripts die een stukje van de applicatie testen. Die eersten heten vaak
end-to-end tests of systeemtests, de laatsten worden unittests genoemd.

Bij het draaien van een testscript wordt over het algemeen slechts een deel van
applicatiecode uitgevoerd. Door een coveragetool te laten bijhouden welke
coderegels en codepaden wel of niet worden uitgevoerd kan na het draaien van de
testscripts een overzicht worden gemaakt van de testdekking. Zo'n overzicht laat
zien welke regels code wel, en welke niet zijn uitgevoerd ('geraakt') tijdens
het testen. Ook laat het zien welke codepaden wel en niet zijn uitgevoerd.

Coderegels en -paden die niet zijn geraakt tijdens het draaien van de
testscripts vertegenwoordigen feitelijk ongeteste functionaliteit. Met je team
maak je afspraken over hoeveel ongeteste code acceptabel is voor je applicatie.
Meestal meestal gebeurt dat door af te spreken dat bijvoorbeeld maximaal 5%
ongeteste code acceptabel is. Oftewel, dat de gewenste testdekking 95% is.

## Rationale: Waarom geautomatiseerde tests?

Geautomatiseerde tests bieden een aantal voordelen. Ten eerste zijn ze veel
goedkoper om uit te voeren dan handmatige tests. Als je een test eenmaal hebt
geautomatiseerd is het opnieuw uitvoeren van de test praktisch gratis. Daardoor
kun je na een wijziging snel vaststellen of bestaande functionaliteit nog steeds
werkt. Oftewel, of er geen regressies zijn opgetreden. En dat draagt bij aan het
tweede voordeel: het wordt goedkoper en minder risicovol om wijzigingen uit te
voeren. Wat weer bijdraagt aan de duurzaamheid van de software.

Je meet de testdekking om te bepalen of alle functionaliteit getest wordt door
je testscripts. Door er bovendien een norm op te zetten dwing je jezelf de
testdekking te verhogen als deze te laag is.

## Doelgroep: Wie zijn er betrokken bij geautomatiseerde tests?

De volgende doelgroepen kunnen met geautomatiseerde tests aan de slag:
developers en testers.

Developers ontwikkelen unittests om te controleren of de code die ze schrijven
doet wat ze verwachten. Daarnaast meten ze de testdekking van de unittests en
verhogen de testdekking indien nodig door unittests toe te voegen.

Testers ontwikkelen end-to-end tests en systeemtests die controleren of de
applicatie werkt zoals verwacht, meten de testdekking ervan en verhogen de
testdekking indien nodig door tests toe te voegen.

## Implementatie: Hoe implementeer je geautomatiseerde tests?

### Methoden en technieken

#### Test-driven development

Test-driven development (TDD) is strikt genomen geen methode om tests te
ontwikkelen, maar een aanpak om code te ontwikkelen. Het idee is dat je in een
kortcyclisch proces (denk minuten, niet uren):

1. één test toevoegt aan je testset en de tests draait om te controleren dat de
   nieuwe test faalt,
2. de eenvoudigste code toevoegt die de nieuwe en alle oude tests doet slagen,
   en
3. de code netjes maakt die je in stap 2 hebt toegevoegd.

Op deze manier ontstaat goed testbare code met een hoge testdekking. Test-driven
development zoals door Kent Beck beschreven in (1) richt zich vooral op
unittests.

#### Behaviour-driven development

Behaviour-driven development (BDD) is een variant van Test-driven development
waarbij de tests geen unittests zijn maar gewenst gedrag (behaviour) van de
applicatie beschrijven. In
[Introducing BDD](https://dannorth.net/blog/introducing-bdd/) (2) beschrijft
Daniel Terhorst-North hoe BDD ontstond en waarom hij koos voor de term
"behaviour" in plaats van "test".

Testers beschrijven het gewenste gedrag van de applicatie in een
domein-specifieke taal (domain specific language) zoals Gherkin. Deze
specificaties worden door de testrunner omgezet in geautomatiseerde acties en
uitgevoerd in het te testen systeem. Hiervoor is veelal "glue" code nodig om de
specificaties om te zetten in acties die de testrunner kan uitvoeren. Developers
of testers met programmeerkennis schrijven deze glue code.

Een voorbeeld van gewenst gedrag geschreven in de domein-specifieke taal
Gherkin:

```
Feature: report
  Creating, editing, and removing reports

  Background: the user is logged in
    Given a logged-in user

  Scenario: add report
    When the user creates a report
    Then the report title is "New report"

  Scenario: delete report
    Given an existing report
    When the user deletes the report
    Then the report does not exist

  Scenario: copy report
    Given an existing report
    When the user copies the report
    Then the report overview contains 2 reports
```

#### Mutation testing

Mutation test tools draaien je tests herhaald, waarbij ze voor iedere run een
kleine wijziging aanbrengen in je code (een "mutant") om te zien of je tests die
verandering waarnemen. Hoe meer mutanten niet worden ontdekt, hoe lager de
kwaliteit van je testset. En ook, hoe meer tests falen bij één kleine wijziging,
hoe fragieler je testset.

### Tools

#### Test runners

Om tests te draaien gebruik je een testrunner. Hiervoor zijn teveel opties om op
te noemen, maar denk aan JUnit voor Java unittests of pytest voor Python
unittests. Voor systeemtesten kun je denken aan JBehave en Robot Framework.

Om inspiratie op te doen in andere projecten kan je onze
[Open Source Catalogus](https://oss.developer.overheid.nl/) gebruiken.

#### Testcoveragetool

Om testdekking te meten gebruik je een testcoveragetool. Hiervoor zijn teveel
opties om op te noemen, maar denk aan JaCoCo voor Java code, coverage.py voor
Python code, en Jest voor Javascript code.

#### Mutation testing tools

Voorbeelden van mutation testing tools zijn PIT voor Java en de Java Virtual
Machine (JVM), Stryker voor Javascript, C# en Scala en mutmut voor Python.

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je tests raken een significant deel van de code van je applicatie.
- Je meet de testdekking van alle productiecode.
- Je hebt een minimale norm voor testdekking van regels code en code paden.
- Je tests doen zinvolle controles (asserts) en roepen niet alleen maar
  functionaliteit aan om zo een hoge dekking te krijgen.
- Kleine wijzigingen aan je applicatie laten een klein deel van de tests falen.
  Je wilt niet dat het veranderen van bijvoorbeeld het formaat van een attribuut
  van één entiteit leidt tot het falen van honderden tests.
- Je unittests zijn échte unittests en doen geen I/O, zodat ze snel zijn. Ook
  hier is het weer lastig om generiek te definiëren wat significant is, maar
  denk aan minder dan een minuut. Hoe langer de doorlooptijd van je unittests,
  hoe minder bruikbaar ze zijn als directe feedback bij het aanpassen van de
  software.

Wanneer ben je echt goed bezig?

- Je zet de norm voor testdekking van regels code en code paden op 100% en je
  configureert je testcoveragetool zodanig dat echt lastig te raken regels code
  niet worden meegeteld.
- Je meet ook de testdekking van de tests zelf om dode code in tests te
  ontdekken.
- Je gebruikt mutation testing om de kwaliteit van je tests te meten.
- Je combineert de coverage metingen van verschillende testsoorten in één
  coveragerapportage zodat je kunt zien of code die niet door de systeemtest
  wordt geraakt in ieder geval wel door de unittests wordt geraakt, en
  omgekeerd.

## Wanneer is deze richtlijn van toepassing?

Bijna altijd. Er zijn maar weinig uitzonderingen. Een uitzondering zou het
ontwikkelen van een prototype kunnen zijn, waarbij de investering in
geautomatiseerde tests zich niet terugverdient.

## Bronnen

### Wetten

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

- ISO/IEC/IEEE 29119 Software and systems engineering — Software testing series

### Communities

- [Test automation days](https://www.testautomationdays.com)

### Literatuur

- (1) Test Driven Development: By Example, Kent Beck, 2002.
- (2) [Introducing BDD](https://dannorth.net/blog/introducing-bdd/), Daniel
  Terhorst-North, 2006.

### Bronnen op developer.overheid.nl

- [Deze goede redenen heeft de Kiesraad om Rust te gebruiken (Over Cargo test-framework voor Rust)](https://developer.overheid.nl/blog/2025/03/26/interview-kiesraad-rust#cargo-test-framework)