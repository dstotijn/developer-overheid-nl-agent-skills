# Richtlijn: Gebruik PKIoverheid-certificaten

Om de vertrouwelijkheid, integriteit en authenticiteit van gegevens te
waarborgen worden gegevens vaak versleuteld en/of digitaal ondertekend op basis
van public key cryptografie. Om het eigenaarschap van public keys te kunnen
waarborgen worden certificaten gebruikt die in een Public Key Infrastructure
(PKI) worden uitgegeven.

PKIoverheid is de Public Key Infrastructure van X.509 certificaten die onder
toezicht staat van de Nederlandse overheid. Logius is de organisatie die het
PKIoverheid-stelsel beheert. De certificaten zelf worden geleverd door een
aantal door PKIoverheid erkende partijen. Meer informatie kun je vinden bij
[Logius](https://www.logius.nl/onze-dienstverlening/toegang/pkioverheid).

Gebruik van PKIoverheid-certificaten is onderdeel van andere standaarden, zoals
[Digikoppeling](https://www.logius.nl/onze-dienstverlening/gegevensuitwisseling/digikoppeling).

PKIoverheid-certificaten kunnen gebruikt worden voor:

1. versleuteling van verbinding (mTLS) of bericht of document, of
1. verzegeling/ondertekening van bericht of document.

PKIoverheid-certificaten worden sinds 2022 niet meer gebruikt voor publiek
toegankelijke websites.

## Rationale: Waarom PKIoverheid-certificaten gebruiken?

PKIoverheid is bedoeld voor situaties waarin meer zekerheid over de identiteit
van de organisatie waarmee gegevens worden uitgewisseld noodzakelijk of
wenselijk is. Bij de uitgifte van certificaten vinden specifieke controles
plaats om zeker te zijn dat het certificaat inderdaad wordt aangevraagd door
iemand die namens die organisatie mag handelen. De normen hiervoor zijn
vastgelegd in het PKIoverheid-afsprakenstelsel.

## Doelgroep: Wie zijn betrokken?

Deze richtlijn is relevant voor:

| Rol               | Typische activiteiten                                                                                                           |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Developers        | Implementeren van specifieke controles (bijvoorbeeld op OIN) en afstemming met overige rollen van de implementatie              |
| Beheerders        | Installeren en configureren van PKIoverheid-certificaten                                                                        |
| Security officers | Aanvragen van PKIoverheid-certificaten, en betrokkenheid bij of intern toezicht op het bijkomende certificaat- en sleutelbeheer |
| Architecten       | Borgen van het gebruik van passende (overheids)richtlijnen                                                                      |

## Implementatie: Hoe gebruik je PKIoverheid-certificaten?

PKIoverheid-certificaten zijn normale X.509-certificaten die onder een eigen
root Certificate Authority (CA) vallen. Het certificaat van deze root CA is
standaard geen onderdeel van de trust stores van operating systems en browsers.
Daardoor zullen PKIoverheid-certificaten niet zonder aanvullende acties
geaccepteerd worden.

1. Het certificaat van de root CA van PKIoverheid (en afhankelijk van de
   implementatie ook de certificaten van de intermediate CA's) moet in de trust
   store geïmporteerd worden. Deze certificaten kun je downloaden van de
   [site van PKIoverheid](https://cert.pkioverheid.nl/).

1. Van PKIoverheid moet bij gebruik ook gecontroleerd worden of certificaten
   niet zijn ingetrokken. De Certificate Revocation Lists (CRLs) van de
   uitgevende CA's moet dus vanuit de productieomgeving gedownload kunnen
   worden.

1. In veel toepassingen, zoals Digikoppeling, moet het
   [Organisatie Identificatie Nummer (OIN)](https://www.logius.nl/onze-dienstverlening/toegang/organisatie-identificatienummer)
   van de organisatie of het organisatieonderdeel in het `Subject.serialNumber`
   veld van het PKIoverheid-certificaat zijn opgenomen. Hiermee moet je rekening
   houden bij het maken van het Certificate Signing Request (CSR) dat je
   opstuurt naar je PKIoverheid-certificaatleverancier (CA).

1. Voor testen is het mogelijk om TRIAL PKIoverheid certificaten te gebruiken.
   Zie
   [https://github.com/pkioverheid/g4-trial](https://github.com/pkioverheid/g4-trial).

### Methoden en technieken

PKIoverheid-certificaten zijn technisch hetzelfde als "gangbare"
X.509-certificaten, ze maken alleen onderdeel uit van een afzonderlijke
certificaathiërarchie. Hierdoor zijn de bovenstaande acties meestal voldoende
voor implementatie.

### Tools

Gangbare tools voor certificaatbeheer zijn openssl op Linux en keytool in Java.

Vraag ook na bij de beheerder of security officer of de organisatie een meer
geavanceerde certificaat- en keymanagement tool gebruikt.

### Gerelateerde richtlijnen

&ndash;

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- De koppelingen met externe systemen gebruiken PKIoverheid-certificaten waar
  nodig

- Je voert de relevante controles uit op de certificaten van je
  communicatiepartner(s), zoals op OIN en revocatiestatus.

Wanneer ben je echt goed bezig?

- Je organisatie werkt volgens richtlijnen en processen in de omgang met
  certificaten.

## Wanneer is deze richtlijn van toepassing?

Gebruik van PKIoverheid-certificaten wordt meestal afgedwongen als onderdeel van
andere standaarden, of door de beheerder van een voorziening waar je gebruik van
maakt. Verder is het gebruik van PKIoverheid raadzaam als een hogere mate van
zekerheid nodig is over de organisatie met wie je gegevens uitwisselt.

## Bronnen

### Wetten

&ndash;

### Beleid

Gebruik van PKIoverheid is vaak verplicht bij het aansluiten op voorzieningen
als DigiD en de Basisregistratie Personen (BRP). De beheerders van dergelijke
voorzieningen kunnen aanvullende voorwaarden stellen aan informatie in het
certificaat. Controleer dit vóór het aanvragen van certificaten.

### Standaarden

- Gebruik van PKIoverheid is verplicht binnen
  [Digikoppeling](https://www.logius.nl/onze-dienstverlening/gegevensuitwisseling/digikoppeling)
- [X.509 ITU](https://www.itu.int/rec/T-REC-X.509)

### Communities

&ndash;

### Literatuur

- Algemene informatie over X.509-certificaten is makkelijk vindbaar op het
  internet, bijvoorbeeld op [Wikipedia](https://en.wikipedia.org/wiki/X.509).
- Het NCSC heeft een gearchiveerde
  [publicatie uit 2021](https://www.ncsc.nl/documenten/factsheets/2021/september/29/factsheet-pkioverheid-stopt-met-webcertificaten)
  die nog steeds veel bruikbare informatie bevat.

### Bronnen op developer.overheid.nl

&ndash;