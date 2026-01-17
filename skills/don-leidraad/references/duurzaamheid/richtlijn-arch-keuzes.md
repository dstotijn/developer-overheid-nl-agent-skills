# Richtlijn: Leg organisatiebrede architectuurkeuzes vast en draag deze uit

Overheidsorganisaties hebben te maken met een veelheid aan applicaties om
externe gebruikers en medewerkers te ondersteunen. Bij de beheersing van
complexiteit van dit applicatielandschap helpt het als er keuzes gemaakt zijn
over architectuur(patronen) en technologie.

## Rationale: Waarom architectuur- en technologiekeuzes maken?

Meestal zijn er meerdere manieren om een oplossing te ontwerpen en
implementeren. Als elk project eigen keuzes maakt loop je de kans op wildgroei
in het applicatielandschap. Een bepaalde mate van harmonisering vergroot de kans
op succesvolle implementatietrajecten, beperkt de beheerlast, verhoogt
mogelijkheden tot hergebruik binnen de organisatie, en geeft focus aan de
(specialistische) kennis en ervaring van personeel.

## Doelgroep: Wie zijn er betrokken ?

Developers, architecten en beheerders leveren gezamenlijk input voor de keuzes
die gemaakt worden. Veel organisaties gebruiken een forum zoals een Architecture
Board om keuzes te bekrachtigen.

## Implementatie: Hoe kom je tot de keuzes?

Bij het komen tot keuzes spelen _inhoud_ (op welke gebieden maak je keuzes?) en
_proces_ (hoe stel je een keuze vast en draag je hem uit?) een rol.

### Inhoudelijke aspecten

Voorbeelden van aspecten waarop je als organisatie een keuze kunt maken:

- Software referentie architectuur (b.v. microservices architectuur, event
  driven architectuur)
- "Design patterns" (b.v. gebruik van een track-and-trace ID om events te kunnen
  correleren)
- Programmeertalen
- Frameworks
- Infrastructuurcomponenten (b.v. gebruik van een bepaalde identity provider,
  API gateway, ...)
- Open source licenties (b.v. open source componenten met welke licenties kunnen
  zonder meer gebruikt worden, bij welke is even ruggenspraak nodig, ...)
- Voorkeur voor bepaalde technische standaarden

### Proces

Houdt bij het proces rekening met het volgende:

- Is er een mogelijkheid om af te wijken wanneer nodig ("pas toe of leg uit")?
- Is er voldoende mogelijkheid voor nieuwe ontwikkelingen?
- Is er voldoende afweging vanuit verschillende perspectieven, zoals
  toekomstvastheid, beschikbare kennis, beschikbare tooling?
- Hoe zorg je dat een keuze ook gebruikt wordt (review op bepaalde momenten,
  expert (tijdelijk) laten meedraaien in een team tijdens de opstartfase?
- Wie bekrachtigt welk soort keuzes (architecture board, een rolspecifiek
  chapter)?

Om een keuze te beproeven kun je gebruik maken van een lichtgewicht proces zoals
beschreven in
[deze blog over do-describe-check-act](https://developer.overheid.nl/blog/2025/12/04/do-describe-check-act).

### Methoden en technieken

&dash;

### Tools

Gemaakte keuzes kun je vastleggen in een Wiki.

### Gerelateerde richtlijnen

- Gebruik van
  [cloud(diensten)](https://developer.overheid.nl/kennisbank/leidraad/cloud)
- Gebruik van
  [open source](https://developer.overheid.nl/kennisbank/leidraad/open-source)
- [Richtlijn onboarding](https://developer.overheid.nl/don-site/leidraad/hergebruik/richtlijn-onboarding)
  helpt ervoor te zorgen dat nieuwe developers bekend raken met de keuzes die je
  als organisatie hebt gemaakt.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je hebt keuzes gedocumenteerd zodat ze voor alle betrokkenen makkelijk
  vindbaar en raadpleegbaar zijn.
- Je hebt de relevante (links naar) informatie opgenomen in de
  [onboarding](https://developer.overheid.nl/don-site/leidraad/hergebruik/richtlijn-onboarding).
- Je hebt belegd hoe keuzes bekrachtigd worden.
- Je hebt belegd hoe keuzes bewaakt worden.

Wanneer ben je echt goed bezig?

- Je hebt kant-en-klare instrumenten ontwikkeld waarmee een team meteen mee aan
  de slag kan. Denk bijvoorbeeld aan een archetype van een applicatie of een
  service.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is met name relevant voor organisaties met een omvangrijk
applicatielandschap, met veel processen en diensten die voor een aanzienlijk
deel met maatwerksoftware worden ondersteund.

## Bronnen

### Wetten

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

&ndash;

### Communities

&ndash;

### Literatuur

&ndash;

### Bronnen op developer.overheid.nl

- [Deze blogpost](https://developer.overheid.nl/blog/2025/12/04/do-describe-check-act)
  beschrijft een licht Do-Describe-Check-Act proces waarmee je een nieuwe keuze
  kunt beproeven voordat je hem bekrachtigt.