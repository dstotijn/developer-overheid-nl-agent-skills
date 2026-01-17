# Richtlijn: verwerken van het burgerservicenummer

De overheid gebruikt het burgerservicenummer (bsn) in bepaalde processen.
Hieronder volgen handvatten hoe je als developer hiermee om kunt gaan.

## Rationale: waarom wordt het burgerservicenummer gebruikt?

Het burgerservicenummer is een uniek persoonsnummer dat gebruikt wordt voor
iedereen die een relatie heeft met de Nederlandse overheid. Gebruik van het
burgerservicenummer is alleen mogelijk als de organisatie een wettelijk
gereguleerde taak heeft die gebruik van het bsn toestaat of verplicht. Naast de
overheid zijn er ook bepaalde andere sectoren waar het bsn gebruikt mag of moet
worden, zoals in de gezondheidszorg en in de pensioensector.

Door het bsn wordt het makkelijker om identity matching uit te voeren en met
hoge zekerheid vast te stellen dat meerdere sets van persoonsgegevens inderdaad
over dezelfde persoon gaan. Door deze eigenschap wordt het bsn vaak als gevoelig
beschouwd en is het gebruik ervan stricter gereguleerd dan van persoonsgegevens
in het algemeen.

Het moeten of mogen gebruiken van het bsn is een noodzakelijke voorwaarde om
DigiD en bepaalde registraties (zoals de Basisregistratie Personen) te
gebruiken.

## Doelgroep: Wie zijn betrokken?

| Rol              | Typische activiteiten                                                                                         |
| ---------------- | ------------------------------------------------------------------------------------------------------------- |
| developer        | Is zich bewust van de gevoeligheid van het bsn en handelt daarnaar                                            |
| privacy officer  | Beoordeelt de verwerking en (geplande) maatregelen van het bsn in de Data Protection Impact Assessment (DPIA) |
| security officer | Beoordeelt de informatiebeveiligingsmaatregelen en ziet toe op de implementatie ervan                         |

## Implementatie: Hoe gebruik je het burgerservicenummer?

Aandachtpunten bij gebruik van het bsn zijn:

1. Controleer bij de privacy officer dat het gebruik van het bsn inderdaad is
   toegestaan, en voor welke doelen.
1. Bepaal samen andere rollen zoals privacy officer en architect of en zo ja hoe
   lang het bsn ook daadwerkelijk bewaard moet worden. Bepaal samen met rollen
   als architect, beheerder, en security officer hoe gegevens verwijderd gaan
   worden na verstrijken van de bewaartermijn (bijvoorbeeld door de applicatie,
   of door processen buiten de applicatie om).
1. Bedenk of iedereen in de doelgroep die je met de applicatie moet bedienen wel
   (tijdig) over een bsn beschikt.
1. Voorkom dat het bsn (en andere persoonsgegevens) in logs terechtkomen. Dit
   geldt ook voor loglevels die in productie waarschijnlijk bijna niet gebruikt
   worden zoals DEBUG en TRACE. Als het wel nodig is om data te loggen waar het
   bsn in kan zitten maskeer het bsn dan zodat geen of hoogstens alleen twee
   cijfers zichtbaar zijn (`*******27`).
1. Gebruik voor testen de test-bsns die
   [Rijksdienst voor Identiteitsgegevens gepubliceerd heeft](https://www.rvig.nl/test-bsn-a-nummers-omnummertabel).
   Deze worden gegarandeerd nooit uitgegeven aan personen. Er zijn ook
   [testsets van fictieve persoonsgegevens inclusief test-bsn](https://www.rvig.nl/testdataset-persoonslijsten-proefomgevingen-bvbsn)
   die je kunt gebruiken voor (keten)testen.
1. Pas de overige richtlijnen op het gebied van privacy en security toe.

### Methoden en technieken

&ndash;

### Tools

&ndash;

### Gerelateerde richtlijnen

- [Privacy-richtlijnen](index.md)
- [Security-richtlijnen](../security/index.mdx)

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- De omgang van het bsn in de applicatie is in lijn met wat in de DPIA is
  beoordeeld en gedocumenteerd.
- Bij iedere wijziging aan de software overdenk je bewust eventuele
  privacy-implicaties en als die er (kunnen) zijn bespreek je die met de privacy
  officer.

Wanneer ben je echt goed bezig?

- Samen met andere rollen zoals architect, privacy officer en security officer
  overweeg je gebruik van Privacy Enhancing Technology. Gebruik bijvoorbeeld
  [deze verdiepingshandleiding van het CIP](https://www.cip-overheid.nl/media/o3vfhs0c/aan-de-slag-met-privacy-by-design-pbd-en-privacy-enhancing-technologies-pets-versie-10.pdf?csf=1&web=1&e=iOEjfq).

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is alleen van toepassing als je het bsn ook mag verwerken.
Sommige concepten kun je wel gebruiken voor overige uniek identificerende
persoonskenmerken.

## Bronnen

### Wetten

- [Wet algemene bepalingen burgerservicenummer](https://wetten.overheid.nl/BWBR0022428/2018-07-28/0)
- Er zijn specifieke wetten die gebruik van het bsn bij de overheid en in
  bepaalde sectoren reguleren.

### Beleid

### Standaarden

- Bsn's voldoen aan een variant van de
  [elfproef](https://nl.wikipedia.org/wiki/Elfproef). Dit is met name relevant
  in situaties waarin een bsn handmatig wordt ingevoerd.

### Communities

&ndash;

### Literatuur

&ndash;

### Bronnen op developer.overheid.nl

&ndash;