# Haven (Kubernetes)

Haven is een standaard voor platform-onafhankelijke cloud hosting. Het is een
project dat is ontstaan vanuit de wens van Nederlandse gemeenten om op een
uniforme manier hun Kubernetes cloud hosting te organiseren. Het project is
onderdeel van de Common Ground architectuurvisie. Common Ground is een
initiatief van de Vereniging van Nederlandse Gemeenten (VNG) waarin samengewerkt
wordt aan principes voor een toekomstbestendige digitale architectuur.

![Haven](./img/haven_overview.svg)

## Voordelen

### ✅ Stimuleert hergebruik

Haven maakt het eenvoudiger om open source applicaties tussen organisaties te
hergebruiken. Doordat Haven een specificatie biedt voor hoe die applicaties
precies opgezet moeten zijn ontstaat er een gezamenlijk referentiekader.

Voorbeelden van applicaties die geschikt zijn voor Haven:

- [Signalen](https://github.com/signalen)
- [Generiek Zaakafhandelcomponent](https://github.com/generiekzaakafhandelcomponent)
- [Keycloak](https://github.com/keycloak/keycloak)

### ✅ Correct gebruik van Kubernetes

De learning curve van Kubernetes is behoorlijk steil. De Haven-standaard
waarborgt dat belangrijke principes worden gevolgd. Voorbeelden hiervan zijn het
verzamelen van metrics maar ook dat je een recente versie van Kubernetes draait.

### ✅ Duidelijkheid voor inkopers en leveranciers

Bij aanbestedingen is duidelijkheid cruciaal. Wanneer een gemeentelijke inkoper
om een "Haven Compliant" applicatie of cluster vraagt, weet de leverancier
precies wat er opgeleverd moet worden, wat leidt tot efficiëntere offertes en
betere afstemming.

### ✅ Security

De checks waaruit de Haven-standaard bestaat, bestaan voor een deel uit
security-checks.

### ✅ Voorkomen van vendor lock-in

Omdat de Haven-standaard open source is en er een
[compliancy-checker](./haven-compliancy-checker.md) voor handen is, kan elke
leverancier die daar oren naar heeft een Haven-compliant Kubernetes Cluster
opleveren.

### ✅ Haven is een levende standaard

Haven is een standaard die door verschillende gemeentes en leveranciers van
gemeentes in de praktijk wordt gebruikt. Veel leveranciers geven aan dat ze blij
zijn met de Haven-standaard omdat het ze duidelijkheid geeft bij de communicatie
met gemeenten.

## Haven-compliant != direct compleet soeverein

Als organisatie is het goed om na te denken over digitale soevereiniteit. Hoe
meer gebruik je maakt van componenten waar je geen controle over hebt, hoe
minder wendbaar je bent. Door je Kubernetes clusters op basis van de
Haven-standaard in te richten zet je een stap in de goede richting. Echter is
het **geen keurmerk voor totale soevereiniteit**.

De volgende casus illustreert een situatie waarin je Haven-compliant bent, maar
toch afhankelijk bent van platform-specifieke functionaliteit:

- Op je cluster wil je een container hebben waar je bestanden kan wegschrijven.
  Binnen Kubernetes is het dan raadzaam om te werken met een `StorageClass`.
- Die StorageClass mag volgens de Haven-standaard prima geïmplementeerd zijn met
  een Azure driver voor Azure Blob Storage of een AWS S3 Bucket.
- Op dat moment maak je zelf de keuze om een vendor-specifiek product te
  gebruiken, de Haven-standaard dwingt niet af dat je dit niet doet.

:::info[Met Haven niet direct compleet soeverein]

Als je Haven-compliant bent, betekent dit niet direct dat je volledig
platform-agnostisch bezig bent. De standaard staat het namelijk nog steeds toe
om bijvoorbeeld platform specifieke functionaliteiten te gebruiken zoals
`Azure Blob Storage` of `AWS S3 Buckets` voor file storage.

:::

### [Haven+](./haven-plus): meer soevereiniteit door componenten als vervanging voor Azure/ AWS services

Gelukkig biedt het Haventeam een oplossing voor het bovenstaande probleem: een
suite van componenten die functionaliteiten zoals `monitoring`, `authenticatie`,
`databases`, `certificaatbeheer` en `secret management` voor je regelen.
Hierdoor hoef je geen AWS- of Azure-specifieke functionaliteit te gebruiken.

## Hoe maak ik mijn applicatie geschikt voor een Haven Cluster?

De voorwaarden voor een project om op een Haven Cluster te kunnen draaien zijn:

- De opzet moet containerized zijn (bijvoorbeeld met Docker)
- Het project moet Kubernetes manifests bevatten (bijvoorbeeld op basis van
  Helm)
- Er moet een endpoint beschikbaar zijn voor metrics
- De applicaties moeten kunnen schalen naar meerdere replica's

Op dit moment is er nog geen tooling of validator die checkt of je applicatie
voldoet aan de voorwaarden om te draaien op een Haven Cluster.

## Haven Compliancy Checker

Deze CLI Tool stelt je in staat om pro-actief je Kubernetes cluster
Haven-compliant te houden.

- [Meer info over Haven Compliancy Checker](./haven-compliancy-checker)

![Screenshot FSC Policy Builder](./img/schermafbeelding-compliancy-checker.png)

## Haven+

Haven+ is een set aan componenten die gezamenlijk de volgende dingen voor je
doet: monitoring (metrics, logging en tracing), authenticatie, databases,
certificaatbeheer, secret management.

[Naar ons artikel over Haven+](./haven-plus.md)

## Welke organisaties werken met Haven?

- [Gemeente Utrecht](https://utrecht.nl)
- [Wigo4it](https://www.wigo4it.nl/nieuws/haven-compliancy-bij-wigo4it/)
- [SURF](https://www.surf.nl/files/2024-10/surf-cloud-sourcing-strategie.pdf)

## Links

- [Gitlab Haven](https://gitlab.com/commonground/haven/haven)
- [Website Haven](https://haven.commonground.nl/)