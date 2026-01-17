# Bouw een API

Hier leggen we uit welke stappen je kunt doorlopen om snel en efficiënt een
nieuwe REST API te ontwikkelen. We gaan hierbij uit van een _design first_
aanpak, dus we starten met het API design.

## Een API bouwen volgens de "Design First" methode

### 1. Genereer een OpenAPI Specification (OAS)

Elk REST API Design dient beschreven te worden middels OAS. Je kunt de
[OpenAPI Specification Generator](../openapi-specification/openapi-specification-generator.md)
gebruiken om automatisch een start template te genereren die reeds aan de
[REST API Design Rules](../api-design-rules) voldoet.

### 2. Pas de OAS aan naar jouw specifieke usecase

De template die zojuit gegenereerd is, is nog niet compleet. Specifieke
responses en requests ontbreken nog, dus het is noodzakelijk om de OAS verder af
te maken. Om te zorgen dat het design niet afwijkt van de REST API Design Rules,
kun je de [ADR Linter](../api-design-rules/api-design-rules-linter) gebruiken.

### 3. Feedback verzamelen en verwerken

Nu de eerste versie van de OAS klaar is, kan deze gedeeld worden met andere
personen, zoals potentiële gebruikers van de API. Deze kunnen dan een blik
werpen op het design en feedback geven.

### 4. Optioneel: mock de API

Indien je over een API gateway beschikt die _mocking_ ondersteunt, kan deze op
basis van de OAS een _mock API_ publiceren. Hierdoor kunnen er echte requests
gedaan worden naar de endpoints, welke vervolgens voorbeelddata teruggeven. Zo
kunnen clients alvast starten met de implementatie van de API, zonder dat de
achterliggende business logic van de API daadwerkelijk gerealiseerd is.

### 5. Ontwikkel de API

Zodra het API Design final is, kan de ontwikkeling van de API beginnen.
Afhankelijk van de mogelijkheden kan het interessant zijn om deze in twee fases
te publiceren:

#### 5.1 Publiceer de endpoints

Een stapje verder dan een mocking service is het daadwerkelijk publiceren van de
endpoints. Hoewel misschien nog geen business logic aanwezig is, kan hiermee de
verbinding en eventuele authenticatie getest worden. Met de
[ADR Validator](../api-design-rules/api-design-rules-validator.md) kan zo ook al
gevalideerd worden of er issues zijn met bepaalde API Design Rules en security.

#### 5.2 Publiceer de business logic

Na de endpoints kan de business logic geïmplementeerd worden, waardoor de eerste
versie van de API (v1) klaar is.

### 6. Voeg de API toe aan developer.overheid.nl

Zodra de API productie-waardig is, kan deze opgenomen worden in het API register
van developer.overheid.nl. Hierdoor is de API meteen vindbaar, wordt het
voorzien van documentatie en van een eigen topic in de community. Bovendien
wordt elke dag automatisch gevalideerd of de API nog aan de API Design Rules
voldoet.