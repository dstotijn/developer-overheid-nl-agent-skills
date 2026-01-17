# Richtlijnsjabloon

*Dit is het sjabloon voor het opstellen van richtlijnen. Het sjabloon gebruikt 
een van de bestaande richtlijnen als voorbeeld. Die tekst ga je vervangen door 
de tekst van de nieuwe richtlijn die je wilt maken. De blokken met schuingedrukte 
tekst verwijder je als je klaar bent met de nieuwe richtlijn.*

*Gebruik informele taal. Je kan de lezer aanspreken met "je". Afkortingen schrijf 
je de eerste keer uit met de afkorting tussen haakjes erachter.*

*De titel van de richtlijn is bij voorkeur in de gebiedende wijs:*

# Richtlijn: Ontwikkel duurzame software door te investeren in geautomatiseerde tests

*Direct onder de titel beschrijf je de richtlijn en de belangrijkste begrippen daarin. 
Leg hier nog niet uit waarom de richtlijn een goed idee is, dat komt bij het volgende 
kopje.*

Bij **handmatige** tests bedient een mens de applicatie en vergelijkt het
werkelijke gedrag van een applicatie met het verwachte gedrag. Bij
**geautomatiseerde** tests voert een ander stuk software deze activiteiten uit.
Deze software bestaat vaak uit een 'test runner' en 'testscripts'. De
testscripts bedienen de applicatie (of stukjes daarvan) en vergelijken het
werkelijke gedrag met het verwachte gedrag van de applicatie. De test runner
voert de testscripts uit.

*Bij een beschrijving van 'common knowledge' kun je "we" gebruiken:*

We onderscheiden testscripts die een hele applicatie bedienen en controleren en
testscripts die een stukje van de applicatie testen. Die eersten heten vaak
end-to-end tests of systeemtests, de laatsten worden unittests genoemd.

*Het gebruik van de passieve vorm ("worden") is, mits spaarzaam toegepast, prima
bij het beschrijven van de richtlijn:*

Bij het draaien van een testscript wordt over het algemeen slechts een deel van
applicatiecode uitgevoerd. Door een coveragetool te laten bijhouden welke
coderegels en codepaden wel of niet worden uitgevoerd kan na het draaien van de
testscripts een overzicht worden gemaakt van de testdekking. Zo'n overzicht laat
zien welke regels code wel, en welke niet zijn uitgevoerd ('geraakt') tijdens
het testen. Ook laat het zien welke codepaden wel en niet zijn uitgevoerd.

*Bij activiteiten die developers als onderdeel van de richtlijn zouden moeten
uitvoeren is het prima om de gebiedende wijs te gebruiken:*

Coderegels en -paden die niet zijn geraakt tijdens het draaien van de
testscripts vertegenwoordigen feitelijk ongeteste functionaliteit. Met je team
maak je afspraken over hoeveel ongeteste code acceptabel is voor je applicatie.
Meestal meestal gebeurt dat door af te spreken dat bijvoorbeeld maximaal 5%
ongeteste code acceptabel is. Oftewel, dat de gewenste testdekking 95% is.

*Het kopje Rationale is van de vorm "Rationale: Waarom 'richtlijn'?":*

## Rationale: Waarom geautomatiseerde tests?

*Beschrijf waarom het een goed idee is om de richtlijn toe te passen. Motiveer 
waarom de richtlijn bijdraagt aan het realiseren van het principe waar deze onder 
valt. Noem ook risico's die optreden als de richtlijn niet wordt toegepast.*

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

*Het kopje Doelgroep is van de vorm "Doelgroep: Wie zijn er betrokken bij 'richtlijn'?":*

## Doelgroep: Wie zijn er betrokken bij geautomatiseerde tests?

*Noem eerst de doelgroepen als een lijstje:*

De volgende doelgroepen kunnen met geautomatiseerde tests aan de slag:
developers en testers.

*Beschrijf vervolgens per doelgroep met welke activiteit de doelgroep aan de slag 
kan:*

Developers ontwikkelen unittests om te controleren of de code die ze schrijven
doet wat ze verwachten. Daarnaast meten ze de testdekking van de unittests en
verhogen de testdekking indien nodig door unittests toe te voegen.

Testers ontwikkelen end-to-end tests en systeemtests die controleren of de
applicatie werkt zoals verwacht, meten de testdekking ervan en verhogen de
testdekking indien nodig door tests toe te voegen.

*Het kopje Implementatie is van de vorm "Implementatie: Hoe implementeer je 'richtlijn'?":*

## Implementatie: Hoe implementeer je geautomatiseerde tests?

### Methoden en technieken

*Onder het kopje methoden en technieken beschrijf je methoden en technieken die 
helpen bij het implementeren of uitvoeren van de richtlijn. Maak een subkopje voor elke 
methode en/of techniek.*

*Een methode of techniek is een beschreven werkwijze met een duidelijk herkenbare naam en 
een afgebakende scope. "CI/CD pijplijn opzetten" is dus geen methode of techniek, 
"GitOps" wel. "Unittesten" is geen methode of techniek, "Test-driven development" wel.*

#### Test-driven development

*Houd de beschrijving van de methode of techniek beknopt. De beschrijving hoeft
niet uitputtend te zijn. Verwijs naar een boek of website voor meer informatie. 
Houd ook het aantal verwijzingen beperkt. Verwijs het liefst naar één canonieke bron.*

Test-driven development (TDD) is strikt genomen geen methode om tests te
ontwikkelen, maar een aanpak om code te ontwikkelen. Het idee is dat je in een
kortcyclisch proces (denk minuten, niet uren):

1. één test toevoegt aan je testset en de tests draait om te controleren dat de
   nieuwe test faalt,
2. de eenvoudigste code toevoegt die de nieuwe en alle oude tests doet slagen,
   en
3. de code netjes maakt die je in stap 2 hebt toegevoegd.

*Merk op dat in de volgende alinea een boek wordt gerefereerd met (1). Dit boek 
staat verderop genoemd in het hoofdstuk Bronnen.*

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

### Tools

*Onder het kopje Tools beschrijf je tools die je kunt gebruiken bij het toepassen
van de richtlijn. Bij voorkeur zijn dit open source tools, maar als de meestgebruikte 
tools commercieel zijn noem je die ook. Neem geen links op. Het is niet nodig 
uitputtend te zijn, een aantal voorbeelden is voldoende. Als er  meerdere soorten 
tools zijn, zoals in dit voorbeeld, maak dan subkopjes per soort tool.*

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

### Gerelateerde richtlijnen

*Onder het kopje gerelateerde richtlijnen neem je links naar andere richtlijnen 
uit de NeRDS Leidraad Softwareontwikkeling op indien relevant. Let op, voeg hier
geen andere standaarden toe, daar is verderop een kopje voor.*

- [Richtlijn software beheerst overdragen](hergebruik/richtlijn-software-overdragen.md)

### Succescriteria

*Onder het kopje successcriteria richtlijnen neem je criteria op voor het succesvol
toepassen van de richtlijn. Verdeel de criteria in twee groepen: wat is nodig om
te voldoen en wanneer ben je echt goed bezig. Deze succescriteria moeten ook worden
toegevoegd aan de [self-assessment checklist](self-assessment-checklist.ods).*

Wanneer voldoe je aan deze richtlijn?

- Je tests raken een significant deel van de code van je applicatie.
- Je meet de testdekking van alle productiecode.
- Je hebt ...

Wanneer ben je echt goed bezig?

- Je zet de norm voor testdekking van regels code en code paden op 100% en je
  configureert je testcoveragetool zodanig dat echt lastig te raken regels code
  niet worden meegeteld.
- Je meet ook de testdekking van de tests zelf om dode code in tests te
  ontdekken.
- Je past ...

## Wanneer is deze richtlijn van toepassing?

*Beschrijf de situaties waarin de richtlijn al dan niet van toepassing is.*

Bijna altijd. Er zijn maar weinig uitzonderingen. Een uitzondering zou het
ontwikkelen van een prototype kunnen zijn, waarbij de investering in
geautomatiseerde tests zich niet terugverdient.

## Bronnen

*Noem hieronder bronnen onder de juiste subkopjes. Voeg bij wetten, beleid en standaarden geen links toe. Deze zouden eenvoudig vindbaar moeten zijn op basis van organisatie, naam en jaartal.*

### Wetten

*Voeg namen toe van wetten, inclusief jaartal, indien relevant. Denk aan de 
European Accessibility Act die accessibility requirements voorschrijft. Gebruik 
"Geen bekend" als er geen relevante wet- en regelgeving bekend is.*

Geen bekend.

### Beleid

*Voeg namen toe van overheidsbeleid, inclusief jaartal, indien relevant.*

Geen bekend.

### Standaarden

*Voeg namen van standaarden toe, inclusief jaartal en uitgevende organisatie, indien relevant.
Noem hier standaarden die door deze richtlijn worden gebruikt of welke met behulp van deze 
richtlijn deels of geheel worden geïmplementeerd. Denk aan ISO-standaarden en de  'Pas toe of 
leg uit'-standaarden van Forum Standaardisatie. Gebruik "Geen bekend" als er geen 
relevante standaarden bekend zijn.*

- ISO/IEC/IEEE 29119 Software and systems engineering — Software testing series

### Communities

*Voeg websites van relevante communities toe. Noem hier communities die actief zijn in het 
werkveld van deze richtlijn. Denk aan een community van testers bij een test-richtlijn. Gebruik 
"Geen bekend" als er geen relevante communities bekend zijn.*

- [Test automation days](https://www.testautomationdays.com)

### Literatuur

*Voeg artikelen of boeken toe die hierboven gebruikt zijn in de beschrijving. 
Gebruik getallen voor de referenties. Link naar de literatuur als deze openbaar is.
Gebruik "Geen bekend" als er geen relevante literatuur bekend is.* 

- (1) Test Driven Development: By Example, Kent Beck, 2002.
- (2) [Introducing BDD](https://dannorth.net/blog/introducing-bdd/), Daniel
  Terhorst-North, 2006.

### Bronnen op developer.overheid.nl

*Noem andere bronnen op developer.overheid.nl, zoals blogpost en artikelen. 
Noem hier geen andere richtlijnen, daarvoor is het kopje "Gerelateerde richtlijnen".
Gebruik "Geen bekend" als er geen relevante bronnen op developer.overheid.nl bekend zijn.*

- [Deze goede redenen heeft de Kiesraad om Rust te gebruiken (Over Cargo test-framework voor Rust)](https://developer.overheid.nl/blog/2025/03/26/interview-kiesraad-rust#cargo-test-framework)

## Colofon

*Noem hier het gebruikte sjabloon inclusief link:*

Gebruikt sjabloon: [Richtlijnsjabloon, versie 1](./richtlijnsjabloon-v1.md)."