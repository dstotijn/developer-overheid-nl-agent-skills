# API Architectuur

<!-- prettier-ignore -->
> **Dit is een samenvatting van de Architectuur van de NL API Strategie van het Kennisplatform API's**
Het volledige
[Architectuurdocument](https://geonovum.github.io/KP-APIs/API-strategie-algemeen/Architectuur/)
is vastgesteld en online gepubliceerd als onderdeel van het
[Kennisplatform API's](https://developer.overheid.nl/communities/kennisplatform-apis/).

## Introductie

Dit architectuurdocument is onderdeel van de **NL API Strategie** en biedt een
verdieping op
[de algemene inleiding](https://docs.geostandaarden.nl/api/API-Strategie/). De
versie is opgesteld in december 2023 en is los gepositioneerd ten opzichte van
de eerdere geïntegreerde versie.

De NL API Strategie is opgebouwd uit drie hoofdcomponenten

- **Algemene documenten** (Inleiding, Architectuur, Gebruikerswensen)
- **Normatieve standaarden** (zoals API Design Rules, OAS, NL GOV OAuth‑profiel,
  Digikoppeling REST API)
- **Functionele/technische modules** (bijvoorbeeld Geospatial, Transport
  Security, Access Control, Hypermedia)

Het hoofdstuk Architectuur beschrijft de rol van deze componenten binnen het
bredere strategisch kader en de belangrijkste delen zijn hier samengevat

## Typologie van API’s

Binnen de NL API Strategie wordt een onderscheid gemaakt in verschillende
soorten API’s, afhankelijk van hun rol binnen een informatieketen of
applicatielandschap:

| Type API           | Beschrijving                                                                     |
| ------------------ | -------------------------------------------------------------------------------- |
| **System API**     | Directe toegang tot een specifieke databron of systeem. Beperkt in logica.       |
| **Process API**    | Combineert meerdere System API’s en bevat domeinlogica (ook wel: orchestration). |
| **Experience API** | Op maat gemaakte API voor specifieke afnemers of kanalen.                        |
| **Public API**     | API’s die publiek beschikbaar zijn voor derden, vaak met toegangsbeheer.         |
| **Private API**    | Alleen intern gebruikt, niet bedoeld voor externe partijen.                      |

Deze typologie helpt bij het structureren van API-landschappen en het toewijzen
van verantwoordelijkheden in grotere overheidsorganisaties. Een veelgebruikt
voorbeeld is de Common Ground-architectuur waarbij System API’s toegang geven
tot bronnen als BAG of BRK, en Process API’s dienstlogica bevatten voor
bijvoorbeeld Zaakgericht Werken (ZGW API's).

> [Verder lezen](https://geonovum.github.io/KP-APIs/API-strategie-algemeen/Architectuur/#typologie-van-api-s)

## API Capability Model

Het API Capability Model beschrijft modulair de functionaliteiten die
samenhangen met de inzet van API's. De opbouw helpt organisaties bij het
prioriteren van ontwikkelinspanningen en bij het toetsen van bestaande API’s.
Het model bestaat uit de volgende onderdelen:

- **Registratie & Gebruik**
  - Aanmelden & Registratie: Zelf-service onboarding van ontwikkelaars en hun
    applicaties inclusief registratie, credential issuance, client registration
    en beheer. ￼
  - Ontdekken: Zorgt voor vindbaarheid via portals, catalogi en API directories
    (zoals het
    [Developer Overheid API Register](https://apis.developer.overheid.nl/apis)
    ).
- **Realisatie & Beheer**
  - Realisatie: Behelst ontwerp, ontwikkeling, testen en het technisch
    beschikbaar maken van APIs.
  - API Governance: Beleidsregels, standaarden, naming conventions en
    richtlijnen om uniformiteit te garanderen.
  - API Lifecycle beheer: Proces van aanbieden, versiebeheer, deprecatie,
    sunset-fases en communicatie richting gebruikers.
  - Platform beheer: Operationeel beheer van de API Gateway, sleutelmanagement,
    toegangsmatrix en beheer van tooling. ￼ ￼
- **Verkeersstroom beheer**
  - Mediatie & Orkestratie: Routing, validatie, datatransformaties en
    foutafhandeling tussen client en backend systemen.
  - Telemetrie & Inzicht: Logging, monitoring, dashboards en analytics voor
    gebruiksinzicht en platformgezondheid.
  - Service level beheer: SLA’s, throttling, rate limits, doorbelasting en
    capaciteitsbeheer.
  - Beveiliging: Identificatie (authenticatie), autorisatie, sleutelbeheer,
    policy enforcement, audit logging en anomalie detectie. ￼

![API Capability model](./img/API-Capability.png)

> [Verder lezen](https://geonovum.github.io/KP-APIs/API-strategie-algemeen/Architectuur/#api-capability-model)

## API management functionaliteit

In een volwassen API-architectuur is **API-management** onmisbaar voor het goed
kunnen beheren, beveiligen en monitoren van API’s. Het hoofdstuk
API-management-functionaliteit uit de architectuurdocumentatie van de **NL API
Strategie** beschrijft de belangrijkste functies en hun positionering.

### Belangrijkste API-managementfuncties

| Functionaliteit             | Beschrijving                                                                                                                             |
| --------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **API Gateway**             | Centrale toegangspoort voor inkomend verkeer. Zorgt voor policy enforcement, routing, throttling, caching, request logging en validatie. |
| **Developer Portal**        | Publicatiepunt voor discovery, documentatie en registratie van API-gebruikers. Biedt self-service toegang voor developers.               |
| **Beveiligingsservices**    | Ondersteuning van authenticatie (zoals OAuth2, mTLS), autorisatie (rollen/scopes) en beveiligingsbeleid.                                 |
| **Monitoring en Analytics** | Dashboarding en alerts voor gebruik, beschikbaarheid, fouten en performance. Helpt bij SLA-bewaking en verbeteringen.                    |
| **Rate limiting & Quotas**  | Beschermen van achterliggende systemen tegen overbelasting door limieten op te leggen aan gebruik per client.                            |
| **Lifecycle management**    | Versiebeheer, deprecatiebeleid en ondersteuning voor staging (dev, test, prod) om API-evolutie beheerst uit te voeren.                   |

### Architectonische inbedding

De functionaliteiten kunnen beperkt gecentraliseerd worden aangeboden
(bijvoorbeeld via een generiek API-platform binnen een overheidsorganisatie)
maar zullen hoofdzakelijk decentraal per API-team worden ingericht conform het
Federatief Data Stelsel (FDS). Afstemming over design, logging, beveiliging en
lifecycle management blijft essentieel bij decentrale implementaties.

De API-architectuur benadrukt dat API-management niet alleen een technische
aangelegenheid is, maar ook organisatorische en governance vraagstukken omvat.
Denk aan:

- Wie bepaalt welke API’s beschikbaar worden gesteld?
- Hoe wordt versiebeheer uitgevoerd?
- Wat zijn de voorwaarden voor toegang en gebruik?
- Voldoen de API's aan de wetten, regels en standaarden die we hebben
  afgesproken?

## Tot slot

Het gebruik van open source API-management tooling (zoals APISIX, WSO2, KONG,
TYK of andere open source alternatieven) wordt aanbevolen mits deze passen
binnen de Nederlandse open-standaardenstrategie.

Door het toepassen van een **duidelijke typologie** en het **Capability Model**
wordt het eenvoudiger om API’s in te richten binnen de bredere API-strategie van
de overheid. Dit sluit aan bij het streven naar een API-first benadering en
modulaire overheidsinfrastructuur.

## Meer informatie

- [API Strategie – Geonovum](https://geonovum.nl/geo-standaarden/api-strategie)
- [KP-APIs GitHub](https://github.com/Geonovum/KP-APIs)
- [API Design Rules (ADR)](https://gitdocumentatie.logius.nl/publicatie/api/adr/)
- [NL API Strategie – Architectuur](https://geonovum.github.io/KP-APIs/API-strategie-algemeen/Architectuur/)
- [API Management en Beveiliging – Developer Overheid](https://developer.overheid.nl/apis/beveiliging/)

```mdx-code-block

```