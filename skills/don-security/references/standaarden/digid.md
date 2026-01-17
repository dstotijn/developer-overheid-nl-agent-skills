# DigiD

**DigiD** staat voor _Digitale Identiteit_ en is het officiële inlogsysteem van
de Nederlandse overheid. Burgers gebruiken DigiD om veilig en betrouwbaar in te
loggen bij overheidsinstanties, zorginstellingen en onderwijsorganisaties.

Met DigiD kunnen gebruikers hun identiteit digitaal bewijzen. Denk aan het
aanvragen van toeslagen, het raadplegen van medische gegevens of het verlengen
van een rijbewijs. DigiD is een cruciale schakel in de digitale dienstverlening
van de overheid.

## Hoe werkt DigiD?

DigiD biedt meerdere manieren van inloggen:

- **Gebruikersnaam + wachtwoord**
- **Sms-controle**
- **DigiD app (met face ID of vingerafdruk)**
- **Inloggen met identiteitsbewijs via NFC**

DigiD maakt gebruik van de Nederlandse publieke infrastructuur en gebruikt
standaarden zoals SAML2.0 voor authenticatie. Dit maakt het ook goed
integreerbaar in applicaties die met overheidsgegevens werken.

## Wat betekent dit voor developers?

Als je werkt aan een applicatie waarin gebruikers moeten inloggen namens of voor
de overheid, moet je vaak DigiD integreren. Hiervoor zijn specifieke
koppelvlakken beschikbaar via Logius.

Belangrijke punten:

- Je moet aangesloten zijn via **Machtigingenregister** of een andere erkende
  route.
- DigiD werkt via een **SAML-koppeling**, en vereist een betrouwbaarheidsniveau
  (bv. Substantieel of Hoog).
- Er gelden strikte eisen voor logging, beveiliging en gebruik van
  persoonsgegevens.

## DigiD Machtigen

Met **DigiD Machtigen** kunnen burgers iemand anders (tijdelijk) toestemming
geven om namens hen digitale overheidszaken te regelen. Bijvoorbeeld: een ouder
mag belastingzaken regelen voor een kind.

Als developer is dit relevant als jouw applicatie toegang moet geven aan
gemachtigden. Er is ondersteuning voor:

- Machtiging aanvragen en beheren via een portaal
- Controle van machtiging via de DigiD machtigingenservice

Meer info:
[Logius.nl/digid-machtigen](https://www.logius.nl/domeinen/toegang/digid-machtigen)

## BSNk en persoonsgegevenbescherming

Bij DigiD speelt ook de **Basisinfrastructuur voor Persoonsgegevens (BSNk)** een
rol. BSNk zorgt voor veilige en gestandaardiseerde verwerking van
identiteitsgegevens bij authenticatie en machtigen. Onderdeel hiervan is de
**Pseudoniemenvoorziening (PP)**, waarmee gevoelige gegevens worden omgezet in
pseudoniemen. Dit verhoogt de privacy.

Technisch gezien krijg je als afnemer dan geen BSN te zien, maar een pseudoniem
dat uniek is per dienst.

Meer info over BSNk en PP:
[Logius.nl/bsnk-pp](https://www.logius.nl/domeinen/toegang/bsnk-pp)

## Samengevat

DigiD is essentieel voor veilige toegang tot digitale overheidsdiensten. Voor
developers betekent dit:

- Werken met SAML-authenticatie
- Rekening houden met verschillende inlogniveaus
- Eventuele ondersteuning van machtigen
- Privacymaatregelen zoals pseudonimisering via BSNk
- Token exchange om SAML tokens in te wisselen voor een OAuth/OIDC JWT

## Meer informatie

- Over DigiD algemeen:
  [Logius - DigiD](https://www.logius.nl/domeinen/toegang/digid)
- DigiD Machtigen:
  [Logius.nl/digid-machtigen](https://www.logius.nl/domeinen/toegang/digid-machtigen)
- BSNk & pseudoniemenvoorziening:
  [Logius.nl/bsnk-pp](https://www.logius.nl/domeinen/toegang/bsnk-pp)