# ADR Cheat Sheet

Het actuele en uitgebreide overzicht van de REST API Design Rules vind je hier:
[API Design Rules](https://logius-standaarden.github.io/API-Design-Rules/#normative-design-rules).
Hieronder vind je echter een extract met de belangrijkste technische regels en
best practices om te gebruiken tijdens het ontwerpen van een API.

## Gebruik OpenAPI Specification

> **Verplichte standaard**
Naast dat deze regels onderdeel zijn van de API Design Rules, is het gebruik van
de OpenAPI Specification ook een eigen verplichte standaard op de
pas-toe-leg-uit-lijst bij Forum Standaardisatie:
[https://www.forumstandaardisatie.nl/open-standaarden/openapi-specification](https://www.forumstandaardisatie.nl/open-standaarden/openapi-specification)

- Bied een OpenAPI Specification aan waarin de API is gespecificeerd.
- Het document dient in `JSON` formaat beschikbaar te zijn.
- Het document dient op de standaardlocatie `openapi.json` achter de baseUrl van
  het endpoint te staan.
- Het document dient resolvable te zijn vanaf elk domein, dus zonder
  authenticatie en met de juiste CORS policy:
  - ✅**Goed**: `Access-Control-Allow-Origin: *`
  - ⛔️**Fout**: `Access-Control-Allow-Origin: https://developer.overheid.nl`

## Gebruik Nederlands

Voor zowel de documentatie als de interface zelf geldt dat de Nederlandse taal
leidend is, tenzij er al Engelse documentatie voorhanden is.

## Contactinformatie

Het OpenAPI document moet een geldig `contact` object bevatten:

- `name`: naam van het verantwoordelijke team/afdeling.
- `url`: nuttige URL om contact op te kunnen nemen, dus bijvoorbeeld een
  issuetracker in plaats van `www.ministerie.nl`.
- `email`: nuttig e-mailadres om contact op te kunnen nemen, dus bijvoorbeeld
  een team in plaats van `info@ministerie.nl`.

Voorbeeld van een geldig `info.contact` object:

```json
{
  "contact": {
    "name": "Gebouwen API beheerder",
    "url": "https://www.github.com/ministerie/gebouwen/issues",
    "email": "teamgebouwen@ministerie.nl"
  }
}
```

## Versioning

- Gebruik semantic versioning (`major.minor.patch`) voor de volledige API
  versie, bijv. `2.1.4`
- Geef bij elke response een `API-Version` header terug met daarin de volledige
  API versie, bijv. `API-Version: 2.1.4`
- De major version moet onderdeel zijn van het endpoint, prefixed met een `v`,
  bijv. `https://api.developer.overheid.nl/v1`. Dit dient ook in het `servers`
  object van de OpenAPI Specificatie zo opgenomen te zijn.

Voorbeeld van een geldig `info.servers` object:

```json
{
  "servers": [
    {
      "url": "https://api.example.com/v1",
      "description": "Productie omgeving"
    },
    {
      "url": "https://sandbox-api.example.com:8443/v1",
      "description": "Sandbox omgeving"
    }
  ]
}
```

## Response bodies

- Gebruik `application/json` voor response bodies.
- Gebruik `lowerCamelCase` voor properties, bijvoorbeeld `organisatieNaam`.
- Gebruik [Problem Details](../gedrag-en-implementatie/problem-details) voor
  foutmeldingen.

## HTTP methods

| Method | Wanneer te gebruiken              | Voorbeeld                    | Omschrijving                               |
| ------ | --------------------------------- | ---------------------------- | ------------------------------------------ |
| GET    | Collectie ophalen                 | `GET /rijksmonumenten`       | Lijst van rijksmonumenten ophalen          |
| GET    | Resource ophalen                  | `GET /rijksmonumenten/12`    | Rijksmonument #12 ophalen                  |
| POST   | Nieuwe resource maken             | `POST /rijksmonumenten`      | Nieuw rijksmonument maken                  |
| PUT    | Resource in zijn geheel vervangen | `PUT /rijksmonumenten/12`    | Rijksmonument #12 in zijn geheel vervangen |
| PATCH  | Resource gedeeltelijk vervangen   | `PATCH /rijksmonumenten/12`  | Rijksmonument #12 gedeeltelijk vervangen   |
| DELETE | Resource verwijderen              | `DELETE /rijksmonumenten/12` | Rijksmonument #12 verwijderen              |

## Status codes

| Status code | Omschrijving | Wanneer te gebruiken                                                                                  |
| ----------- | ------------ | ----------------------------------------------------------------------------------------------------- |
| 200         | Ok           | GET, PUT, PATCH, DELETE, als de request succesvol is uitgevoerd                                       |
| 201         | Created      | POST, als nieuwe resource direct wordt teruggegeven                                                   |
| 202         | Accepted     | Als de request een asynchrone response triggert, bijvoorbeeld een POST die niet direct verwerkt wordt |
| 400         | Bad request  | Als de request invalid is, meestal bij een POST, PUT of PATCH met een invalid body                    |
| 404         | Not found    | Als de request URI niet gevonden wordt of een resource niet bestaat                                   |

## URI's

- Collecties in (Nederlands) meervoud. Best practice voor koppelwoorden in de
  URI is `kebab-case`:
  - ✅**Goed**: `https://api/v1/open-source-projecten`
- Child genest onder resource in (Nederlands) meervoud. Voorkeur voor
  koppelwoorden in de URI is `kebab-case`:
  - ✅**Goed**: `https://api/v1/organisaties/372/open-source-projecten`
- URI's mogen niet op een slash eindigen.
  - ✅**Goed**: `https://api/v1/open-source-projecten`
  - ⛔️**Fout**: `https://api/v1/open-source-projecten/`
- URI's mogen geen gevoelige informatie bevatten omdat dit bijv. in logs terecht
  kan komen.
  - ⛔️**Fout**: `https://api/v1/personen?bsn=123234345456`

## Tools

- [API Design Rules Linter](./api-design-rules-linter)
- [API Design Rules Validator](./api-design-rules-validator)
- [OpenAPI Spec generator](../openapi-specification/openapi-specification-generator)