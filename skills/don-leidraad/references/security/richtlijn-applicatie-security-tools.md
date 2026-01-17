# Richtlijn: Integreer applicatie security tools in de pijplijn

Applicatie security tools helpen je geautomatiseerd beveiligingskwetsbaarheden
te ontdekken in je eigen code of in code waar je afhankelijk van bent, zoals
bibliotheken of container images (dependencies).

We onderscheiden verschillende soorten security tools:

- Statische applicatie security tools (SAST): scannen de broncode op mogelijk
  kwetsbare contructies zonder de code uit te voeren. Deze analyse draait na
  elke wijziging van de code, bijvoorbeeld als onderdeel van elke pull request.
- Dynamische applicatie security tools (DAST): controleren de applicatie op
  kwetsbaarheden door de applicatie te draaien en geautomatiseerd te
  onderzoeken. Deze analyse draait na elke succesvolle deployment van de
  applicatie naar een testomgeving.
- Software compositie analyse (SCA) tools: controleren dependencies op bekende
  kwetsbaarheden en licentie compliance risico's en waarschuwen voor
  achterlopende versies. Deze analyse draait bij elke wijziging van de code én
  periodiek.

## Rationale: Waarom security tools integreren in de pijplijn?

Door applicatie security tools te integreren in de pijplijn kun je
kwetsbaarheden vroegtijdig ontdekken en repareren voordat deze in productie
terecht komen.

Door de software compositie analyse tools ook periodiek te draaien, kunnen deze
je waarschuwen voor nieuw ontdekte kwetsbaarheden in de dependencies van je
applicatie.

## Doelgroep: Wie zijn er betrokken bij security tools?

De volgende doelgroepen kunnen met security tools aan de slag:

**Developers** richten de tools in en repareren de kwetsbaarheden.

**Security engineers** beoordelen de risico's.

De **Chief Information Security Officer** (CISO) of andere verantwoordelijke
bestuurder houdt de statistieken over de openstaande risico's in de gaten.

## Implementatie: Hoe implementeer je security tools?

### Methoden en technieken

Geen bekend.

### Tools

#### Statische applicatie security tools

Er bestaan veel tools in deze categorie. Enkele bekende voorbeelden zijn
SonarQube en Checkmarx.

#### Dynamische applicatie security tools

Er bestaan veel tools in deze categorie. Enkele bekende voorbeelden zijn
Burpsuite en ZAP.

#### Software compositie analyse tools

Er bestaan veel tools in deze categorie. Enkele bekende voorbeelden zijn Trivy,
OWASP Dependency-Check en OWASP Dependency-Track. Package management tools
hebben soms functionaliteit om bekende kwetsbaarheden te tonen, bijvoorbeeld
`npm audit`.

### Gerelateerde richtlijnen

Geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je hebt voor elk van de genoemde types applicatie security tools minimaal één
  tool in de pijplijn geïntegreerd.
- Je analyseert de uitkomsten en prioriteert de kwetsbaarheden op basis van
  risico.
- Je update regelmatig dependencies.
- Je bewaakt dat de software compositie analyse regelmatig draait.

Wanneer ben je echt goed bezig?

- Je monitort de verschillende tools met behulp van een overkoepelend
  kwaliteitsdashboard zoals Quality-time.

## Wanneer is deze richtlijn van toepassing?

Bijna altijd. Er zijn maar weinig uitzonderingen. Een uitzondering zou het
ontwikkelen van een prototype kunnen zijn, waarvan 100% zeker is dat het niet in
gebruik wordt genomen.

## Bronnen

### Wetten

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

- [OWASP Application Security Verification Standard (ASVS)](https://github.com/OWASP/ASVS),
  versie 5.0, paragraaf 15.2, "Security Architecture and Dependencies".
- [OWASP Software Assurance Maturity Model (SAMM)](https://owaspsamm.org),
  versie 2, the Secure Build practice.

### Communities

- [Centrum Informatiebeveiliging en Privacybescherming (CIP)](https://www.cip-overheid.nl/).
  CIP is een publiek-private netwerkorganisatie die bestaat uit
  overheidsbedrijven en kennispartners.

### Literatuur

Todo

### Bronnen op developer.overheid.nl

- Lees meer over
  [security in de kennisbank](https://developer.overheid.nl/kennisbank/security/).