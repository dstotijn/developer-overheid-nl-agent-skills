# Richtlijn: Cloud-native softwareontwikkeling

Binnen de overheid wordt steeds vaker gesproken over digitale soevereiniteit,
wat verwijst naar de controle over digitale infrastructuren en data. Wanneer
applicaties en de onderliggende infrastructuur goed zijn opgezet, wordt het
eenvoudiger om services te verplaatsen of nieuwe diensten toe te voegen.

## Rationale: Waarom cloud-native softwareontwikkeling?

- **Schaalbaarheid** - Overheidssoftware moet vaak kunnen omgaan met fluctuaties
  in gebruik, zoals pieken in het aantal gebruikers tijdens belastingaangiftes
  of verkiezingen. Duurzaam beheer zorgt ervoor dat de software flexibel kan
  worden opgeschaald zonder verlies van prestaties, wat cruciaal is voor de
  beschikbaarheid van diensten.

- **Onafhankelijkheid** - Geen vendor lock-in. Services kunnen gemakkelijk
  worden geïsoleerd en beheerd. Het is eenvoudiger om nieuwe diensten toe te
  voegen of bestaande te vervangen

- **Kostenefficiëntie** - Dynamische resource-allocatie zorgt voor
  kostenbesparing door te betalen naar werkelijk gebruik, wat leidt tot lagere
  onderhoudskosten voor infrastructuur en vereenvoudigde continue integratie en
  delivery processen.

- **Betrouwbaarheid** - Betere beschikbaarheid van services. Gecontroleerde en
  gestandaardiseerde deploymentprocessen.

## Doelgroep: Wie zijn er betrokken bij cloud-native softwareontwikkeling?

De volgende doelgroepen kunnen met cloud-native aan de slag: developers, DevOps
engineers, platform engineers, architecten en security officers.

Developers bouwen applicaties volgens cloud-native principes zoals twelve-factor
app. DevOps engineers richten CI/CD pipelines in en automatiseren deployment.
Platform engineers bouwen en beheren het onderliggende platform (zoals
Kubernetes). Architecten ontwerpen de cloud-native architectuur. Security
officers zorgen dat beveiligingsmaatregelen zijn geïntegreerd in de cloud-native
omgeving.

## Implementatie: Hoe implementeer je cloud-native softwareontwikkeling?

### Methoden en technieken

#### Containerisatie

Verpak je applicaties in containers (bijvoorbeeld Docker) zodat ze consistent
draaien op verschillende omgevingen. Containers zorgen voor betere isolatie en
resource-efficiëntie.

#### Infrastructure as Code

Beheer je infrastructuur met code (bijvoorbeeld Terraform, Ansible) zodat deze
reproduceerbaar en versioneerbaar is.

### Tools

#### Container orchestratie

Voor het beheren van containers in productie gebruik je orchestratie platforms
zoals Kubernetes, Docker Swarm of cloud-native oplossingen.

#### CI/CD platforms

Voor continue integratie en deployment gebruik je platforms zoals GitLab CI,
GitHub Actions, Jenkins of Azure DevOps.

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je applicaties zijn gecontaineriseerd en draaien op een container orchestratie
  platform.
- Je hebt geautomatiseerde CI/CD pipelines.

Wanneer ben je echt goed bezig?

- Je gebruikt Infrastructure as Code voor het beheren van je infrastructuur.
- Je hebt monitoring en observability geïmplementeerd voor je cloud-native
  applicaties.
- Je past chaos engineering toe om de veerkracht van je systeem te testen.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is met name van toepassing bij nieuwe applicaties of bij
modernisering van bestaande applicaties. Het is vooral relevant wanneer
schaalbaarheid, flexibiliteit en onafhankelijkheid belangrijke eisen zijn.

## Bronnen

### Wet- en regelgeving

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

Geen bekend.

### Communities

- [Common Ground](/communities/common-ground)
- [Haven](https://haven.commonground.nl/)

### Literatuur

Geen bekend.

### Bronnen op developer.overheid.nl

Geen bekend.