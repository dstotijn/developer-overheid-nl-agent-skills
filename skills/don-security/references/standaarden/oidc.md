# OpenID Connect (OIDC)

**OpenID Connect (OIDC)** is een authenticatielaag bovenop **OAuth 2.0**. Waar
OAuth toegang regelt tot API’s (autorisatie), voegt OIDC daar **authenticatie**
aan toe — oftewel: wie is de gebruiker?

Met OIDC kan een applicatie (Relying Party) betrouwbaar de identiteit van een
gebruiker vaststellen op basis van een login bij een Identity Provider (IdP),
zoals een overheidssysteem of commerciële aanbieder.

## Hoe werkt OIDC?

De flow van OIDC lijkt sterk op OAuth, maar voegt o.a. deze elementen toe:

- **ID Token**: een JWT (JSON Web Token) met gebruikersinfo
- **UserInfo endpoint**: een optionele API om aanvullende gegevens op te halen
- **Standard scopes**: zoals `openid`, `profile`, `email`

Een typische OIDC flow verloopt als volgt:

1. Gebruiker wordt doorgestuurd naar de IdP.
2. Gebruiker logt in en geeft toestemming.
3. De app ontvangt een `code`, wisselt deze in voor een **access token** én een
   **ID token**.
4. De app valideert het ID token en weet wie de gebruiker is.

## OIDC in Nederland: NL GOV OIDC-profiel

Binnen de Nederlandse overheid is er een specifiek profiel ontwikkeld: het **NL
GOV OpenID Connect profiel**. Dit profiel specificeert hoe OIDC veilig en
interoperabel gebruikt kan worden voor publieke dienstverlening.

Belangrijke kenmerken:

- Verplichte ondersteuning voor `authorization_code` flow met PKCE
- Gebruik van `id_token_hint` en `login_hint` voor login-context
- Verplichte `sub` en `acr` claims in ID Token
- Beveiligingsmaatregelen zoals signed requests en TLS

🔗
[NL GOV OIDC profiel (GitHub)](https://github.com/Logius-standaarden/OIDC-NLGOV/)

## Officiële standaarden

- [OpenID Connect Core 1.0](https://openid.net/specs/openid-connect-core-1_0.html)
- [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html)
- [OpenID Connect Dynamic Client Registration](https://openid.net/specs/openid-connect-registration-1_0.html)
- [OAuth 2.0 (RFC 6749)](https://datatracker.ietf.org/doc/html/rfc6749)

## Wanneer gebruik je OIDC?

OIDC is ideaal voor:

- Single Sign-On (SSO) tussen meerdere diensten
- Federatieve login (bijv. met DigiD of eHerkenning)
- Veilige identificatie van gebruikers op basis van standaarden
- Integraties in moderne web- en mobiele applicaties

Niet geschikt voor:

- Pure autorisatie zonder gebruikersidentiteit → gebruik dan alleen OAuth 2.0

## Meer informatie

- [NL GOV OIDC profiel](https://gitdocumentatie.logius.nl/publicatie/api/oidc/)
- [OpenID Connect officiële site](https://openid.net/connect/)
- [OIDC + OAuth uitleg (oauth.net)](https://oauth.net/2/)