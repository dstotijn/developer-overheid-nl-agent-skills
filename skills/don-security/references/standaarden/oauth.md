# OAuth 2.0

**OAuth 2.0** is een open standaard voor **autorisatie**, waarmee applicaties
namens een gebruiker toegang kunnen krijgen tot gegevens of functionaliteiten,
zonder dat het wachtwoord gedeeld hoeft te worden. Het is vooral populair in
mobiele apps, API's en microservices architecturen.

OAuth is **geen authenticatieprotocol**, maar wordt vaak samen gebruikt met
OpenID Connect (OIDC) om ook de identiteit van een gebruiker vast te stellen.

## Hoe werkt OAuth?

Een typische OAuth flow verloopt als volgt:

1. Een gebruiker probeert toegang te krijgen tot een resource.
2. De applicatie vraagt toestemming via een **authorization server**.
3. De gebruiker logt in en geeft toestemming.
4. De app ontvangt een **access token** en gebruikt dit om API's aan te roepen.

> Zie ook de uitgebreide use case beschrijvingen van de
> [client credentials flow](https://gitdocumentatie.logius.nl/publicatie/api/oauth/#use-case-client-credentials-flow)
> en de
> [authorization code flow](https://gitdocumentatie.logius.nl/publicatie/api/oauth/#use-case-authorization-code-flow)

Belangrijke componenten:

- **Resource Owner**: de gebruiker
- **Client**: de app die toegang vraagt >
  [link](https://gitdocumentatie.logius.nl/publicatie/api/oauth/#client)
- **Authorization Server**: geeft tokens uit >
  [link](https://gitdocumentatie.logius.nl/publicatie/api/oauth/#authorization-server)
- **Resource Server**: API die toegang beschermt >
  [link](https://gitdocumentatie.logius.nl/publicatie/api/oauth/#resource-server)

## OAuth in Nederland: NL GOV OAuth-profiel

Voor toepassingen binnen de Nederlandse overheid is er het **NL GOV OAuth 2.0
profiel**. Dit is een set afspraken en richtlijnen die ervoor zorgt dat OAuth op
een **interoperabele, veilige en betrouwbare** manier wordt ingezet binnen het
publieke domein.

Enkele kenmerken van het profiel:

- Gebaseerd op de OAuth 2.0 standaard (RFC 6749)
- Sluit aan bij
  [Security Best Current Practices (BCP)](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-security-topics)
- Strikt gebruik van PKCE en geen client secrets op publieke clients
- Gebruik van signed requests en mutual TLS waar nodig

Het profiel wordt beheerd via een GitHub repository:

- [NL GOV OAuth 2.0 profiel (GitHub)](https://github.com/Logius-standaarden/OAuth-NL-profiel)

## Officiële standaarden

- [RFC 6749 - OAuth 2.0 Authorization Framework](https://datatracker.ietf.org/doc/html/rfc6749)
- [RFC 6750 - Bearer Token Usage](https://datatracker.ietf.org/doc/html/rfc6750)
- [OAuth 2.1 (in ontwikkeling)](https://oauth.net/2.1/)
- [OAuth Security Best Practices (BCP)](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-security-topics)

## Wanneer gebruik je OAuth?

OAuth is ideaal voor:

- Toegang tot REST API's (bv. gegevens ophalen uit een register)
- Delegatie van rechten (bv. iemand machtigt een app om namens hem gegevens op
  te vragen)
- Veiligere alternatieven voor API keys of basis authenticatie

Niet geschikt voor:

- Alleen identificatie zonder toestemming → gebruik dan OpenID Connect
- Authenticatie in browser-only context zonder backend → kwetsbaar voor token
  diefstal

## Meer bronnen

- [OAuth 2.0 overzicht - oauth.net](https://oauth.net/2/)
- [NL GOV OAuth profiel](https://gitdocumentatie.logius.nl/publicatie/api/oauth/)
- [OpenID Connect profiel](https://gitdocumentatie.logius.nl/publicatie/api/oidc/)
- [eIDAS en OAuth in de toekomst](https://digital-strategy.ec.europa.eu/en/policies/eidas-regulation)