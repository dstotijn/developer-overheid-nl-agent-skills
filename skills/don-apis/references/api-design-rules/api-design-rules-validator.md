# ADR Validator

De API Design Rules (ADR) Validator is een CLI-tool om te valideren of een API
zich gedraagt conform deze delen van de
[NL API Strategie](https://geonovum.github.io/KP-APIs/API-strategie-algemeen/Inleiding/):

- Alle rules uit de
  [API Design Rules Module](https://gitdocumentatie.logius.nl/publicatie/api/adr/)
  die testbaar zijn en we dus kunnen valideren door het aanroepen van de API.
- De Transport Layer Security (TLS) rules van de
  [Transport Security Module](https://docs.geostandaarden.nl/api/API-Strategie-mod-transport-security/#transport-security).

## Hoe kan ik mijn API valideren?

In de readme van de
[ADR Validator repository](https://gitlab.com/commonground/don/adr-validator)
vind je hoe je deze tool lokaal kan installeren en gebruiken. In de repository
kan je ook de code van vinden.

## Continuous Integration (CI): Hoe kan ik mijn API’s automatisch blijven valideren?

Het is mogelijk om de ADR validator toe te voegen aan je Continuous Integration
(CI) pipeline om je API automatisch elke keer te valideren als deze wordt
uitgerold. Hiervoor dien je op twee plekken de build-step toe te voegen.
Voorbeelden vind je hier:

- [DockerFile](https://gitlab.com/commonground/don/developer.overheid.nl/-/blob/main/Dockerfile?ref_type=heads)
- [.gitlab-ci.yml](https://gitlab.com/commonground/don/developer.overheid.nl/-/blob/main/.gitlab-ci.yml?ref_type=heads)