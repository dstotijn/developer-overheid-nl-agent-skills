# Richtlijn: Neem privacy als uitgangspunt

Het waarborgen van de privacy van de gebruiker zou in elke stap van het proces
een prioriteit moeten zijn.

## Rationale: Waarom privacy als uitgangspunt?

Overheidsinstanties moeten voldoen aan strikte privacywetgeving, zoals de AVG
(Algemene Verordening Gegevensbescherming). Dit betekent dat gegevens alleen
mogen worden verwerkt als daar een legitieme grondslag voor is, en dat burgers
controle moeten hebben over hun eigen gegevens.

Een datalek of privacyschending kan enorme gevolgen hebben, zoals
identiteitsfraude, discriminatie of andere vormen van misbruik. Door privacy
vanaf het begin in te bouwen (Privacy by Design) worden deze risico's
geminimaliseerd.

Het niet naleven van privacyregels kan leiden tot boetes van toezichthouders
zoals de Autoriteit Persoonsgegevens. Daarnaast kunnen schadeclaims van burgers
financiële en reputatieschade opleveren.

Het nemen van privacy als uitgangspunt dwingt ontwikkelaars tot het toepassen
van dataminimalisatie: alleen noodzakelijke gegevens worden verwerkt en bewaard.
Dit leidt tot betere beveiliging, efficiëntere systemen en lagere kosten op de
lange termijn.

## Doelgroep: Wie zijn er betrokken bij privacy?

De volgende doelgroepen kunnen met privacy aan de slag: privacy officers,
developers, security officers, architecten en legal advisors.

Privacy officers beoordelen de verwerking en maatregelen in de Data Protection
Impact Assessment (DPIA) en adviseren over privacyvraagstukken. Developers
implementeren privacy by design principes in de code. Security officers zorgen
voor de technische beveiligingsmaatregelen. Architecten ontwerpen systemen die
privacy-vriendelijk zijn. Legal advisors zorgen dat de verwerking voldoet aan de
wettelijke vereisten.

## Implementatie: Hoe implementeer je privacy als uitgangspunt?

### Methoden en technieken

#### Privacy by Design toepassen

Privacy by Design betekent dat je privacy vanaf het begin meeneemt in het
ontwerp van je systeem. De acht privacyontwerpstrategieën uit het Blauwe Boekje
helpen je concreet invulling te geven aan Privacy by Design.

#### Data Protection Impact Assessment (DPIA) uitvoeren

Bij verwerkingen met hoog privacy-risico ben je wettelijk verplicht een DPIA uit
te voeren. Hierin analyseer je de risico's en beschrijf je de maatregelen om
deze te beperken.

#### Dataminimalisatie toepassen

Verwerk alleen de strikt noodzakelijke persoonsgegevens voor het doel waarvoor
je ze verzamelt. Bewaar gegevens niet langer dan nodig.

### Tools

#### DPIA tools

Voor het uitvoeren van een DPIA kun je tools gebruiken die je helpen de risico's
systematisch in kaart te brengen.

#### Encryptie en hashing tools

Gebruik encryptie voor opslag en transport van persoonsgegevens en hashing voor
het pseudonimiseren van identificerende gegevens.

### Gerelateerde richtlijnen

- [Verwerken van het burgerservicenummer](bsn.md)

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je hebt een DPIA uitgevoerd voor verwerkingen met hoog risico.
- Je past dataminimalisatie toe en bewaart gegevens niet langer dan nodig.
- Je hebt passende beveiligingsmaatregelen getroffen zoals encryptie.

Wanneer ben je echt goed bezig?

- Je gebruikt Privacy Enhancing Technologies (PETs) waar mogelijk.
- Je hebt verwerkingsovereenkomsten gesloten met alle verwerkers.
- Je faciliteert de uitoefening van privacy-rechten van betrokkenen (inzage,
  correctie, verwijdering).

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is van toepassing zodra je persoonsgegevens verwerkt in je
software. Dit is vrijwel altijd het geval bij overheidssoftware.

## Bronnen

### Wet- en regelgeving

- [Algemene Verordening Gegevensbescherming (AVG/GDPR)](https://autoriteitpersoonsgegevens.nl)

### Beleid

Geen bekend.

### Standaarden

Geen bekend.

### Communities

- [Centrum Informatiebeveiliging en Privacybescherming (CIP)](https://www.cip-overheid.nl)

### Literatuur

- [Het Blauwe Boekje](https://www.cs.ru.nl/~jhh/blauwe-boekje.html)
- [Handleiding "Privacy by Design" van het CIP](https://www.cip-overheid.nl/producten-en-diensten/handleiding-privacy-by-design)

### Bronnen op developer.overheid.nl