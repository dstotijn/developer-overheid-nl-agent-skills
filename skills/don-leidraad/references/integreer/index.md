# Richtlijn: Integreer technologie in bestaande systemen

Technologie moet compatibel zijn met bestaande systemen, processen en
infrastructuur binnen de organisatie en flexibel genoeg om aan toekomstige eisen
te voldoen.

## Rationale: Waarom technologie integreren in bestaande systemen?

Overheden hebben vaak al geïnvesteerd in bestaande systemen en infrastructuur.
Integratie voorkomt dat deze investeringen verloren gaan en zorgt voor
kostenefficiëntie.

Als een nieuwe software-applicatie niet wordt geïntegreerd met bestaande
systemen, kan de adoptie door medewerkers achterblijven. Medewerkers moeten dan
werken met losse systemen die niet met elkaar communiceren, wat leidt tot
inefficiëntie en frustratie.

Integratie zorgt ervoor dat bestaande werkprocessen niet onnodig verstoord
worden. Medewerkers kunnen doorgaan met hun dagelijkse taken zonder grote
veranderingen of leercurves.

## Doelgroep: Wie zijn er betrokken bij integratie?

De volgende doelgroepen kunnen met integratie aan de slag: architecten,
developers, API-specialisten, beheerders en functioneel beheerders.

Architecten ontwerpen de integratiearchitectuur en bepalen welke
integratiepatronen toegepast worden. Developers implementeren de API's en
koppelingen. API-specialisten zorgen voor goede API-documentatie en governance.
Beheerders zorgen dat de technische infrastructuur de integratie ondersteunt.
Functioneel beheerders testen of de geïntegreerde systemen correct samenwerken.

## Implementatie: Hoe integreer je technologie in bestaande systemen?

### Methoden en technieken

#### API-first ontwikkeling

Bij API-first ontwikkeling ontwerp je eerst de API voordat je de implementatie
bouwt. Dit zorgt voor goed doordachte interfaces die makkelijk te integreren
zijn. Door data toegankelijk te maken via API's vanaf de afdelingen die ervoor
verantwoordelijk zijn, blijft de data bij de bron terwijl de hele organisatie
profiteert.

#### Microservices architectuur

Een microservices architectuur waarbij functionaliteit is opgedeeld in kleine,
onafhankelijke services maakt integratie flexibeler. Services kunnen via API's
met elkaar communiceren en onafhankelijk van elkaar worden aangepast.

### Tools

#### API management platforms

Voor het beheren, publiceren en monitoren van API's gebruik je API management
platforms zoals Kong, Tyk of AWS API Gateway.

#### API documentatie tools

Voor het documenteren van API's gebruik je tools zoals Swagger/OpenAPI, Redoc of
Stoplight. Goede documentatie is essentieel voor succesvolle integratie.

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je nieuwe systemen bieden API's aan voor integratie met andere systemen.
- Je documenteert de API's helder en compleet.
- Je test de integraties grondig voordat je live gaat.

Wanneer ben je echt goed bezig?

- Je hebt een API-strategie en governance proces ingericht.
- Je monitort het gebruik en de performance van je API's.
- Je versioned je API's zodat bestaande integraties blijven werken bij
  aanpassingen.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is van toepassing wanneer je nieuwe software ontwikkelt of
inkoopt die moet samenwerken met bestaande systemen, of wanneer je bestaande
systemen toegankelijk wilt maken voor andere applicaties.

## Bronnen

### Wet- en regelgeving

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

Geen bekend.

### Communities

- [Kennisplatform API's](/communities/kennisplatform-apis/)

### Literatuur

Geen bekend.

### Bronnen op developer.overheid.nl

- [Hoofdstuk over API's](/kennisbank/apis)