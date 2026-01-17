# eHerkenning

**eHerkenning** is het zakelijke inlogmiddel waarmee organisaties veilig en
betrouwbaar kunnen inloggen bij digitale publieke en private dienstverleners.
Voor het gemak wordt wel eens gezegd dat eHerkenning is de zakelijke tegenhanger
van DigiD is. Maar dat klopt niet helemaal omdat je het ook buiten de overheid
kan gebruiken en omdat er een machtigingenvoorziening deel uit maakt van de
oplossing. Je kan dan namens een organisatie inloggen en handelen bij andere
organisaties.

Met eHerkenning toon je aan dat je als natuurlijk persoon namens een bedrijf mag
handelen. Dit is belangrijk voor zaken als belastingaangifte, subsidies
aanvragen of het doorgeven van personeelsgegevens.

## Hoe werkt het?

eHerkenning is gebaseerd op een systeem van erkende **leveranciers** die
authenticatiemiddelen uitgeven en machtigingen registreren. Deze middelen zijn
gekoppeld aan een **betrouwbaarheidsniveau** (EH2+ t/m EH4), afhankelijk van de
gevoeligheid van de dienst waarmee wordt ingelogd. Deze betrouwbaarheidsniveaus
zijn vergelijkbaar met eIDAS laag, substiantieel en hoog. Dat geldt ook voor de
machtiging: die moeten ook voldoen aan een vooraf bepaalde
betrouwbaarheidsniveau. Op die manier geef je bij de dienstverlener aan; ik ben
ik én ik ben gemachtigd.

De techniek achter eHerkenning is gebaseerd op **SAML 2.0**, net als DigiD.
Daardoor is het goed integreerbaar in bestaande SSO- en federatieve
login-oplossingen.

## Waarvoor wordt eHerkenning gebruikt?

Met eHerkenning log je in bij meer dan 600 publiek en private dienstverleners,
waaronder:

- **Kamer van Koophandel (KvK)**
- **Belastingdienst**
- **UWV**
- **RVO**
- **Justis**
- **Pensioenfondsen**

Daarnaast kan eHerkenning ook worden gebruikt om in te loggen bij Europese
dienstverleners omdat deze oplossing is genotificeerd.

Als developer bouw je bijvoorbeeld integraties waarin een gebruiker namens een
organisatie inlogt om gegevens aan te leveren of aanvragen te doen.

## Belangrijk voor developers

Bij implementatie van eHerkenning in jouw applicatie of dienst:

- Koppel je aan via een **herkenningsmakelaar** of **dienstverlener** die
  eHerkenning ondersteunt.
- Moet je jouw dienst registreren in het **dienstencatalogus**.
- Werk je met **SAML-authenticatie** (en dus metadata, EntityID’s,
  AssertionConsumerServices, enz.).

Het aansluiten hoef je niet allemaal zelf te doen; de herkenningsmakelaar die de
aansluiting aanbiedt ondersteunt hierbij.

Organisaties krijgen alleen attributen aangeleverd die binnen het
afsprakenstelsel zijn afgesproken en die in de
[attributencatalogus](https://afsprakenstelsel.etoegang.nl/Startpagina/as/attribuutverstrekking).
Denk aan KvK-nummer en bedrijfsnaam.

## Betrouwbaarheidsniveaus

eHerkenning werkt met drie hoofd-niveaus (EH2+ t/m EH4):

- **EH2+**: laag niveau (bv. aanvragen van milieu pas)
- **EH3**: standaard niveau (bv. loonaangifte via Belastingdienst)
- **EH4**: hoog niveau (juridisch bindende handelingen)

De dienstverlener bepaalt het betrouwbaarheidsniveau voor de dienst.

## Meer informatie

- Algemene info en registratie: [eHerkenning.nl](https://www.eherkenning.nl/) of
  stuur een bericht naar info@eherkenning.nl
- Specificaties:
  [Afsprakenstelsel eHerkenning](https://afsprakenstelsel.etoegang.nl/?l=nl)