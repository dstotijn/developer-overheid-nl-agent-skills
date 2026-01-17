# PKIoverheid

PKIoverheid is het Nederlandse stelsel van digitale certificaten voor veilige
communicatie met en binnen de overheid. Het wordt beheerd door **Logius**, de
digitale dienstverlener van de overheid. Met PKIoverheid kunnen organisaties en
burgers erop vertrouwen dat hun gegevens veilig worden uitgewisseld en dat ze
met de juiste partij communiceren.

## Wat doet PKIoverheid?

PKIoverheid zorgt voor:

- **Authenticatie**: Vaststellen met wie je te maken hebt.
- **Vertrouwelijkheid**: Versleutelde communicatie.
- **Integriteit**: De zekerheid dat gegevens niet zijn aangepast.
- **Onweerlegbaarheid**: Bewijs dat een handeling écht is uitgevoerd door een
  bepaalde partij.

Dit is bijvoorbeeld belangrijk bij:

- Inloggen met DigiD of eHerkenning.
- Het versturen van beveiligde e-mails.
- Digitale handtekeningen onder documenten.
- Het beveiligen van websites via TLS/SSL.

## Hoe werkt het?

PKIoverheid gebruikt een hiërarchisch systeem van certificaten:

- Bovenaan staat de **Root CA** (certificeringsinstantie).
- Daaronder hangen **intermediaire certificaten**.
- Deze geven weer certificaten uit aan eindgebruikers of organisaties (zoals
  SSL-certificaten voor websites of certificaten voor e-mailversleuteling).

Het hele stelsel voldoet aan strenge eisen en wordt onafhankelijk gecontroleerd.
Alleen partijen die aan alle voorwaarden voldoen mogen certificaten uitgeven
namens PKIoverheid.

## Waarom is dit relevant voor developers?

Als je werkt aan toepassingen voor of met de overheid, krijg je vrijwel altijd
met PKIoverheid te maken. Denk aan:

- Het configureren van HTTPS met PKIoverheid-certificaten.
- Het valideren van digitale handtekeningen.
- Werken met services die authenticatie eisen via PKIoverheid-certificaten.

Zorg dat je op de hoogte bent van hoe je certificaten installeert, beheert en
valideert binnen je stack.

## Meer informatie

Wil je verder lezen of certificaten downloaden? Check dan deze bronnen:

- Uitleg van de dienst:
  [Logius - PKIoverheid](https://www.logius.nl/onze-dienstverlening/toegang/pkioverheid)
- Wat is PKIoverheid precies:
  [Wat is PKIoverheid?](https://www.logius.nl/domeinen/toegang/pkioverheid/wat-pkioverheid)
- Certificaten downloaden of controleren:
  [cert.pkioverheid.nl](https://cert.pkioverheid.nl/)