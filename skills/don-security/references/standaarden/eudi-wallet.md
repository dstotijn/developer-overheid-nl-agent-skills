# EUDI Wallet

De herziene [**eIDAS-verordening**](./eidas.md) (mei 2024) legt de basis voor
een Europese Digitale Identiteit (EUDI). Deze verordening stelt hogere eisen aan
veiligheid, betrouwbaarheid en gebruiksgemak. Daarmee krijgen burgers en
bedrijven een nieuwe manier om hun identiteit online te bewijzen en gegevens te
delen. Elke lidstaat moet volgens de verordening eind 2026 minstens één
gecertificeerde EDI-wallet beschikbaar stellen.

## Wat is een EUDI wallet?

Een **EUDI wallet** (in Nederland ook wel de EDI-wallet of NL-Wallet genoemd) is
een mobiele applicatie waarmee burgers in alle EU-lidstaten, ongeacht het land
van verblijf/herkomst, op een veilige manier:

- zichzelf online kunnen identificeren
- persoonlijke gegevens kunnen uitwisselen (bijvoorbeeld naam, geboortedatum,
  diploma’s, rijbewijs)
- documenten digitaal kunen ondertekenen

Het unieke van een wallet applicatie (in het algemeen) is dat je als gebruiker
zelf bepaalt welke gegevens je deelt en met wie. Daarmee krijg je regie over je
eigen data. Gebruik van de EUDI wallet is vrijwillig. Huidige kanalen en
inlogmiddelen blijven beschikbaar.

De EUDI wallet wordt in alle EU-lidstaten erkend. Publieke organisaties moeten
wallets accepteren zodra ze beschikbaar zijn, private partijen een jaar later.
In Nederland wordt de **EDI-wallet** ontwikkeld die gratis beschikbaar komt en
voldoet aan de eisen van inclusiviteit, toegankelijkheid en veiligheid. De
broncode van deze applicatie is als
[open source project](https://oss.developer.overheid.nl/repositories/minbzk-nl-wallet-9632)
gepubliceerd. Naast de publieke wallet kunnen in de toekomst ook private
aanbieders toetreden, mits zij voldoen aan de eIDAS-eisen.

Meer info:
[EUDI Architecture and Reference Framework](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main/)

## Voordelen voor burgers en bedrijven

- **Regie over gegevens**: zelf bepalen welke gegevens je deelt, met wie en voor
  welk doel
- **Dataminimalisatie** alleen delen wat nodig is (bijv. leeftijd >18 i.p.v.
  volledige geboortedatum)
- **Gebruiksgemak**: processen die nu vaak papier vereisen (contracten tekenen,
  auto huren) kunnen digitaal
- **Betrouwbaarheid**: verifieerbaar dat de gegevens door officiële bronnen zijn
  uitgegeven

## Belangrijke begrippen en afkortingen

| Begrip/afkorting                                                                | Toelichting                                                                                                                                                                                  |
| ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Issuer**                                                                      | De partij die een VC uitgeeft, bijvoorbeeld een universiteit die een diploma uitgeeft. Voor QEAA's is dat altijd een QTSP.                                                                   |
| **Holder**                                                                      | Degene die de wallet beheert en de credentials bezit, ofwel de burger.                                                                                                                       |
| **Relying Party (RP) / Verifier**                                               | De organisatie die om bewijs vraagt en jouw VC's controleert (bijvoorbeeld een bank, werkgever of ziekenhuis).                                                                               |
| **Wallet Provider**                                                             | De partij die de digitale wallet applicatie beschikbaar stelt.                                                                                                                               |
| **VC (Verifiable Credential)**                                                  | Een digitaal bewijsstuk dat cryptografisch is beveiligd zodat iedereen kan controleren dat het echt is.                                                                                      |
| **VP (Verifiable Presentation)**                                                | Een bundel bewijzen (samengesteld uit VC's) waarin alleen de gegevens staan die men expliciet wilt delen.                                                                                    |
| **PID (Person Identification Data)**                                            | De basisidentiteitscredential met je kerngegevens (naam, geboortedatum, nationaliteit, ID-nummer). Wordt door de overheid uitgegeven en is de digitale tegenhanger van je paspoort/ID-kaart. |
| **TSP (Trust Service Provider)**                                                | Organisatie die vertrouwensdiensten aanbiedt (bv. digitale certificaten of elektronische handtekeningen).                                                                                    |
| **QTSP (Qualified Trust Service Provider)**                                     | Een officieel gecertificeerde TSP die op de EU-lijst staat. Alleen een QTSP mag QEAA's uitgeven.                                                                                             |
| **EAA (Electronic Attestation of Attributes)**                                  | Een digitaal bewijs van een bepaald kenmerk (attribuut), zoals "ouder dan 18" of "BIG-geregistreerd arts".                                                                                   |
| **QEAA (Qualified Electronic Attestation of Attributes)**                       | Een EAA uitgegeven door een QTSP en daardoor in de hele EU rechtsgeldig.                                                                                                                     |
| **Pub-EEA (Public Body Authentic Source Electronic Attestation of Attributes)** | Een EAA uitgegeven door of namens een overheidsinstantie die fungeert als authentieke bron.                                                                                                  |

## API’s en protocollen binnen de EUDI-architectuur

De EUDI wallet gebruikt open (API-)standaarden om interoperabiliteit en
veiligheid te garanderen. Hieronder een overzicht met directe verwijzingen naar
de officiële specificaties:

| API / standaard                 | Toepassing                                                                             | Officiële standaard / documentatie                                                                                                                                                      |
| ------------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Verifiable Credentials (VC)** | Standaard voor digitale bewijsstukken (credentials).                                   | [W3C Verifiable Credentials](https://www.w3.org/TR/vc-overview/)                                                                                                                        |
| **OpenID4VCI**                  | Standaard voor het uitgeven van VC's. Zo haalt de wallet app een VC op bij een issuer. | [OpenID4VCI](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html)                                                                                                 |
| **OpenID4VP**                   | Standaard voor het presenteren van verifiable credentials aan een relying party.       | [OpenID4VP](https://openid.net/specs/openid-4-verifiable-presentations-1_0.html)                                                                                                        |
| **SD-JWT VC**                   | Bestandsformaat voor het uitwisselen van VC's.                                         | [IETF SD-JWT VC Draft](https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/)                                                                                                    |
| **WebAuthn / Passkeys**         | Ondersteuning voor pseudoniemen en sterke authenticatie.                               | [W3C WebAuthn](https://www.w3.org/TR/webauthn-2/)                                                                                                                                       |
| **Proximity flows (NFC, QR)**   | Voor fysiek nabije presentaties van data.                                              | [ISO/IEC 18013-5 NFC & QR Specificaties](https://www.iso.org/standard/69084.html)                                                                                                       |
| **Remote presentation flows**   | Voor uitwisseling op afstand tussen wallet en dienstverlener.                          | [EUDI Architecture & Reference Framework](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main/) |

Zie hoofdstukken 4 en 5 van het
[EUDI-Architecture Framework](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main/#4-high-level-architecture)

De W3C VC, ISO/IEC 18013-5, WebAuthn, Proximity flows zijn verplicht en
vastgesteld, de overige standaarden (OpenID4VP, SD-JWT VC, Remote flows) zijn
nog in ontwikkeling, maar gaan richting verplicht.

Onderstaand model geeft een overzicht van de architectuur van het EUDI wallet
ecosysteem:

![het EUDI wallet ecosysteem](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/media/Figure_2_High-Level_Architecture.jpg)

---

## Meer weten?

- [edi.pleio.nl](https://edi.pleio.nl) – informatie over de Nederlandse
  EDI-wallet.
- [blsp.pleio.nl](https://blsp.pleio.nl) – Large Scale Pilots in Europa.
- [OSS repository NL-wallet](https://oss.developer.overheid.nl/repositories/minbzk-nl-wallet-9632)
  – open source ontwikkeling van de Nederlandse wallet.
- [EUDI Architecture and Reference Framework](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/architecture-and-reference-framework-main/) -
  het Europese referentie en architectuur raamwerk.