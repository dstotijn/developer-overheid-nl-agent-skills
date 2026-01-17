# eIDAS

**eIDAS** staat voor _electronic IDentification, Authentication and trust
Services_. Het is een Europese verordening (nr. 910/2014) die zorgt voor een
juridisch kader rond digitale identiteit, elektronische handtekeningen en
vertrouwensdiensten in de EU.

Kort gezegd: eIDAS maakt het mogelijk om veilig en grensoverschrijdend online
zaken te doen binnen Europa — zowel voor burgers als bedrijven.

## Wat regelt eIDAS?

eIDAS zorgt voor:

- **Erkenning van elektronische identiteiten** tussen EU-landen.
- **Juridische status** voor digitale handtekeningen en zegels.
- **Regels voor vertrouwensdiensten**, zoals tijdstempels, certificaten en
  archiveringsdiensten.

### Belangrijke begrippen

- **Gekwalificeerde elektronische handtekening**: Heeft dezelfde
  rechtsgeldigheid als een handgeschreven handtekening.
- **Gekwalificeerde vertrouwensdienstverlener (TSP)**: Moet voldoen aan strikte
  eisen en is opgenomen in de EU Trusted List.
- **Interoperabiliteit**: Een eID uit land A moet bruikbaar zijn bij een
  overheidsdienst in land B.

## Wat betekent eIDAS voor developers?

Als je werkt aan toepassingen die:

- internationale digitale handtekeningen gebruiken,
- identiteiten van EU-burgers moeten verifiëren,
- of gekwalificeerde vertrouwensdiensten inzetten,

...dan moet je voldoen aan de eIDAS-richtlijnen.

### Voorbeelden van integraties

- Inloggen met een buitenlands eID bij een Nederlandse overheidsdienst.
- Ondertekenen van een contract met een **gekwalificeerde elektronische
  handtekening (QES)**.
- Verifiëren van een certificaat dat onder een **Trusted List** valt.

In Nederland worden systemen als **DigiD** en **eHerkenning** aangesloten op
eIDAS via de zogenaamde **eIDAS-node**.

## eIDAS 2.0: de Europese Digitale Identiteit

Met de komst van eIDAS 2.0 verandert er veel. Er komt o.a. een EU Digital
Identity Wallet, en in dat kader wordt er nagedacht over modernere standaarden
zoals OAuth 2.0 en OpenID Connect (OIDC). De nieuwe verordening **eIDAS 2.0**
(in ontwikkeling) introduceert:

- **Europese Digitale Identiteit Wallets**: apps waarmee burgers hun ID,
  diploma’s, rijbewijs en andere gegevens digitaal kunnen beheren.
- Meer macht aan gebruikers om zelf te bepalen wie welke gegevens mag zien.
- Strengere eisen aan beveiliging en privacy-by-design.

Dit betekent nieuwe kansen én verplichtingen voor developers die digitale
identiteiten verwerken.

Hoewel OAuth/OIDC (nog) geen officieel deel is van de bestaande eIDAS
specificatie, is het waarschijnlijk dat deze standaarden in eIDAS 2.0 gebruikt
gaan worden voor:

- toestemming geven op attribuut niveau (consent),
- mobiele authenticatie via apps (wallets),
- en bredere integratie met moderne web-API’s.

## Meer informatie

- [Technische Specificatie](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32015R0806)
- [eIDAS Building blocs](https://ec.europa.eu/digital-building-blocks/sites/display/DIGITAL/Documentation+eID)
- [Irish eIDAS node provides OAuth 2.0 API that can be used for authentication](https://demo.eidasnode.gov.ie/doc/usage.html)
- EU-info:
  [eIDAS Regulation – Europese Commissie](https://digital-strategy.ec.europa.eu/en/policies/eidas-regulation)
- Nederlandse uitleg (Logius):
  [Logius.nl - Vertrouwensdiensten](https://www.logius.nl/domeinen/toegang/vertrouwensdiensten)