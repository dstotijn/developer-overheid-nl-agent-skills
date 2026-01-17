# Richtlijn: Maak correct gebruik van data

Gebruik data effectiever door je technologie, infrastructuur en processen te
verbeteren.

## Rationale: Waarom correct gebruik van data?

Betrouwbare en actuele data stelt overheden in staat om gefundeerde beslissingen
te nemen, beleidsmaatregelen te verbeteren en de effectiviteit van beleid te
meten. Zonder goede data is het onmogelijk om goed te sturen.

Door data effectief te gebruiken, kunnen overheidsprocessen geautomatiseerd en
geoptimaliseerd worden, wat tijd, middelen en kosten bespaart, en de
dienstverlening aan burgers versnelt.

Het data bij de bron principe betekent dat overheidsdata op de plek van
oorsprong wordt beheerd en geraadpleegd. Dit zorgt ervoor dat data actueel en
betrouwbaar blijft, duplicatie wordt vermeden en de bronorganisatie de controle
behoudt over beveiliging en privacy. Applicaties kunnen via gestandaardiseerde
API's direct de originele gegevens raadplegen, wat bijdraagt aan een
transparante en efficiënte datagedreven dienstverlening.

## Doelgroep: Wie zijn er betrokken bij correct gebruik van data?

De volgende doelgroepen kunnen met correct gebruik van data aan de slag: data
engineers, developers, data stewards, architecten en informatie-analisten.

Data engineers bouwen en onderhouden data pipelines en zorgen dat data van de
bron naar de juiste systemen stroomt. Developers gebruiken API's om data bij de
bron op te halen. Data stewards zijn verantwoordelijk voor de kwaliteit en
governance van data. Architecten ontwerpen de data-architectuur volgens
principes als data bij de bron. Informatie-analisten analyseren en interpreteren
data voor beleid en besluitvorming.

## Implementatie: Hoe implementeer je correct gebruik van data?

### Methoden en technieken

#### Data bij de bron principe toepassen

Implementeer het principe dat data wordt beheerd en geraadpleegd op de plek van
oorsprong. Applicaties raadplegen via gestandaardiseerde API's direct de
originele gegevens in plaats van kopieën te maken.

#### DCAT gebruiken voor metadata

De DCAT (Data Catalog Vocabulary) standaard biedt een uniforme manier om
metadata over datasets te beschrijven. Hierdoor worden datasets beter vindbaar,
zowel voor machines als voor gebruikers:

- **Gestandaardiseerde metadata:** DCAT zorgt voor een uniforme manier om
  metadata over datasets te beschrijven. Hierdoor kun je data consistent en
  gestructureerd publiceren.
- **Verbeterde interoperabiliteit:** Door te werken met een gemeenschappelijke
  vocabulaire wordt het eenvoudiger om data uit verschillende bronnen te
  integreren en met elkaar te laten samenwerken.
- **Betere vindbaarheid en toegankelijkheid:** DCAT maakt datasets beter
  vindbaar, zowel voor machines als voor gebruikers, wat essentieel is voor open
  data initiatieven.
- **Voldoen aan Europese standaarden:** Met profielen zoals DCAT-AP sluit je aan
  bij de Europese open data standaarden, wat de uitwisseling van data tussen
  overheidsorganisaties vergemakkelijkt.
- **Efficiëntie in ontwikkeling:** Door gebruik te maken van een standaard
  metadata schema hoef je niet telkens nieuwe beschrijvingen te maken, wat je
  ontwikkelingsproces versnelt en vereenvoudigt.

#### Linked data principes toepassen

Met [linkeddata.overheid.nl](https://linkeddata.overheid.nl) krijg je als
developer toegang tot gestructureerde, semantisch verrijkte overheidsdata. Dit
geeft diverse mogelijkheden:

- **Rijke, gestructureerde data:**  
  Werk met gegevens die in RDF-formaat zijn aangeboden, zodat je op een uniforme
  manier overheidsinformatie kunt verwerken.

- **SPARQL-endpoints:**  
  Raadpleeg de data direct via SPARQL-query's. Dit stelt je in staat om complexe
  vragen te stellen en de data op maat te extraheren voor jouw toepassingen.

- **Interoperabiliteit:**  
  Integreer data van verschillende overheidsbronnen dankzij de linked data
  principes, waardoor jouw applicaties beter kunnen samenwerken met andere
  systemen.

- **Innovatie en hergebruik:**  
  Bouw innovatieve toepassingen en dashboards die inzichten bieden in
  overheidsprocessen, door gebruik te maken van open en gestandaardiseerde data.

- **Uitgebreide documentatie en community:**  
  Maak gebruik van de beschikbare documentatie en voorbeelden om snel aan de
  slag te gaan. Daarnaast kun je ervaringen delen en vragen stellen binnen de
  developer community.

### Tools

Geen bekend.

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je past het data bij de bron principe toe waar mogelijk.
- Je gebruikt gestandaardiseerde API's voor datatoegang.
- Je documenteert je datasets met metadata.

Wanneer ben je echt goed bezig?

- Je gebruikt DCAT voor het beschrijven van dataset metadata.
- Je publiceert linked data op linkeddata.overheid.nl.
- Je hebt data governance processen ingericht om datakwaliteit te waarborgen.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is van toepassing zodra je applicatie data gebruikt of
produceert, wat vrijwel altijd het geval is.

## Bronnen

### Wet- en regelgeving

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

- [DCAT (Data Catalog Vocabulary)](https://www.w3.org/TR/vocab-dcat/)
- [Standaarden.overheid.nl](https://standaarden.overheid.nl/)

### Communities

- [Linkeddata.overheid.nl](https://linkeddata.overheid.nl)
- [Federatief Datastelsel](/communities/federatief-datastelsel)

### Literatuur

Geen bekend.

### Bronnen op developer.overheid.nl

Geen bekend.