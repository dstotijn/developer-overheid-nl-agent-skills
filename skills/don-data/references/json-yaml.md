# JSON / YAML

JSON (JavaScript Object Notation) en YAML (YAML Ain't Markup Language) zijn twee
veelgebruikte dataformaten voor het uitwisselen en opslaan van gestructureerde
gegevens. JSON is compact, eenvoudig te parsen en ideaal voor machine-to-machine
communicatie, zoals API's. YAML daarentegen is mensvriendelijker door zijn
leesbare syntaxis en wordt vaak gebruikt in configuratiebestanden, zoals in
DevOps-tools en CI/CD-pipelines. Beide formaten ondersteunen complexe
datastructuren zoals lijsten en geneste objecten, maar verschillen in syntaxis
en gebruiksscenario's.

## JSON

JSON is een lichtgewicht dataformaat dat wordt gebruikt voor het uitwisselen van
gegevens tussen systemen. Het is eenvoudig te lezen en te schrijven voor mensen,
en gemakkelijk te parsen en genereren door machines. JSON is gebaseerd op een
subset van de JavaScript-taal, maar wordt ondersteund door vrijwel alle
programmeertalen.

JSON wordt vaak gebruikt in webtoepassingen om gegevens uit te wisselen tussen
een client (zoals een browser) en een server, bijvoorbeeld via API's. JSON is
populair vanwege zijn eenvoud en brede ondersteuning, waardoor het een
standaardkeuze is voor het werken met gestructureerde gegevens in moderne
applicaties.

### Voorbeeld van JSON

Hier is een voorbeeld van een JSON-object dat informatie over een persoon bevat:

```json
{
  "name": "Jan Jansen",
  "age": 30,
  "email": "jan.jansen@example.com",
  "skills": ["JavaScript", "Python", "HTML"],
  "isEmployed": true
}
```

## YAML

YAML is een mensvriendelijk dataformaat dat wordt gebruikt voor het schrijven
van configuratiebestanden en het uitwisselen van gegevens. Het is ontworpen om
eenvoudig te lezen en te schrijven te zijn, met een focus op minimale syntaxis.
YAML ondersteunt complexe datastructuren zoals lijsten, mappen en geneste
objecten, en wordt vaak gebruikt in DevOps-tools, configuratiebestanden en
data-uitwisseling.

### Voorbeeld van YAML

Hier is hetzelfde voorbeeld als het JSON-object, maar nu in YAML:

```yaml
name: Jan Jansen
age: 30
email: jan.jansen@example.com
skills:
  - JavaScript
  - Python
  - HTML
isEmployed: true
```

## Verschillen tussen JSON en YAML

1. Leesbaarheid:
   - YAML is mensvriendelijker door het gebruik van inspringingen en het
     weglaten van haakjes en aanhalingstekens (tenzij nodig).
   - JSON is compacter, maar kan minder intuïtief zijn voor mensen.
1. Syntaxis:
   - YAML gebruikt inspringingen om hiërarchieën aan te geven, terwijl JSON
     haakjes ({} en []) gebruikt.
   - YAML vereist geen aanhalingstekens rond sleutels, tenzij er speciale tekens
     in voorkomen.
1. Gebruik:
   - JSON wordt vaak gebruikt in API's en data-uitwisseling tussen systemen.
   - YAML wordt vaak gebruikt in configuratiebestanden (bijvoorbeeld voor
     CI/CD-tools zoals GitHub Actions of Kubernetes).
1. Complexiteit:
   - YAML ondersteunt meer geavanceerde functies zoals ankers en referenties,
     wat JSON niet heeft.

Kortom, JSON is ideaal voor machine-to-machine communicatie, terwijl YAML beter
geschikt is voor configuratiebestanden die door mensen worden beheerd.

## Tools

- [JSON/YAML converter](https://openreplay.com/tools/json-yaml/): handige tool
  om snel JSON naar YAML en YAML naar JSON om te zetten.