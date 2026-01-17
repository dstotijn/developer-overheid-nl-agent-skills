# Richtlijn: Beveilig systemen en data

In een wereld die snel verandert en waar geopolitieke verschuivingen
plaatsvinden, wordt security een steeds crucialer thema. Het is daarom
belangrijker dan ooit om proactief kwetsbaarheden te monitoren en ervoor te
zorgen dat software altijd up-to-date is.

## Rationale: Waarom systemen en data beveiligen?

Overheden verwerken enorme hoeveelheden vertrouwelijke informatie van burgers,
bedrijven en over nationale veiligheid. Een datalek kan desastreuze gevolgen
hebben voor individuele burgers (identiteitsfraude, financiële schade) en voor
de nationale veiligheid.

Overheidsdiensten zijn essentieel voor het functioneren van de samenleving.
Uitval door cyberaanvallen kan leiden tot verstoring van cruciale diensten zoals
zorg, sociale zekerheid, belastingdienst en noodhulpdiensten.

Geopolitieke spanningen leiden tot meer gerichte aanvallen op
overheidsinstanties door andere landen, criminele organisaties en hacktivisten.
De dreigingen nemen toe in frequentie en geavanceerdheid.

Overheden moeten voldoen aan strikte wetgeving zoals de AVG/GDPR, de Baseline
Informatiebeveiliging Overheid (BIO) en sectorspecifieke regelgeving.
Niet-naleving kan leiden tot boetes, aansprakelijkheid en reputatieschade.

## Doelgroep: Wie zijn er betrokken bij beveiliging?

De volgende doelgroepen kunnen met beveiliging aan de slag: security officers,
developers, DevSecOps engineers, architecten, pentesten en compliance officers.

Security officers stellen het beveiligingsbeleid op en bewaken de naleving.
Developers implementeren secure coding practices en gebruiken security tools.
DevSecOps engineers integreren security in de CI/CD pipeline. Architecten
ontwerpen beveiligde architecturen. Pentesters voeren penetratietesten uit om
kwetsbaarheden te vinden. Compliance officers zorgen dat wordt voldaan aan wet-
en regelgeving.

## Implementatie: Hoe beveilig je systemen en data?

### Methoden en technieken

#### Security by Design toepassen

Security by Design betekent dat je beveiliging vanaf het begin meeneemt in het
ontwerp van je systeem. Dit voorkomt dat beveiliging een afterthought is en
maakt het goedkoper en effectiever om systemen te beveiligen.

#### Threat modeling uitvoeren

Door threat modeling uit te voeren identificeer je potentiële dreigingen en
kwetsbaarheden in je systeem. Dit helpt je prioriteren welke
beveiligingsmaatregelen het belangrijkst zijn.

#### Security scanning in CI/CD

Integreer security tools (SAST, DAST, SCA) in je CI/CD pipeline zodat
kwetsbaarheden automatisch worden gedetecteerd voordat code in productie komt.

### Tools

#### Applicatie security tools

Voor het scannen van code en dependencies gebruik je tools zoals SonarQube
(SAST), OWASP ZAP (DAST) en Trivy of OWASP Dependency-Check (SCA).

#### Security monitoring tools

Voor het monitoren van de beveiligingsstatus gebruik je tools zoals OpenKAT,
SIEM-oplossingen en vulnerability scanners.

#### PKIoverheid-certificaten

Voor bepaalde koppelingen is gebruik van PKIoverheid-certificaten verplicht of
wenselijk voor extra zekerheid over identiteit.

### Gerelateerde richtlijnen

- [Richtlijn gebruik PKIoverheid-certificaten](richtlijn-pkioverheid.md)
- [Richtlijn applicatie security tools](richtlijn-applicatie-security-tools.md)

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je hebt security tools geïntegreerd in je CI/CD pipeline.
- Je voert regelmatig security assessments en pentesten uit.
- Je past Security by Design principes toe.
- Je monitort actief op security incidenten en kwetsbaarheden.

Wanneer ben je echt goed bezig?

- Je hebt een Security Operations Center (SOC) of SIEM ingericht.
- Je voert regelmatig threat modeling sessies uit.
- Je hebt een incident response plan en test dit regelmatig.
- Je deelt security knowledge en leermomenten met andere overheidsorganisaties.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is altijd van toepassing. Security moet vanaf het begin onderdeel
zijn van elk softwareontwikkelingsproject en blijft relevant gedurende de hele
levenscyclus van de software.

## Bronnen

### Wet- en regelgeving

- Baseline Informatiebeveiliging Overheid (BIO)
- Algemene Verordening Gegevensbescherming (AVG/GDPR)

### Beleid

Geen bekend.

### Standaarden

- OWASP Top 10
- OWASP Application Security Verification Standard (ASVS)
- ISO/IEC 27001

### Communities

- [Nationaal Cyber Security Centrum (NCSC)](https://www.ncsc.nl/)
- [Centrum Informatiebeveiliging en Privacybescherming (CIP)](https://www.cip-overheid.nl/)

### Literatuur

- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)

### Bronnen op developer.overheid.nl

- [OpenKAT](/kennisbank/security/tools/openkat)
- [Security hoofdstuk](/kennisbank/security)
- [Rijksinspectie Digitale Infrastructuur (RDI)](https://rdi.nl)
- [Nationaal innovatie centrum privacy-enhancing technologies (nicpet)](https://nicpet.nl)