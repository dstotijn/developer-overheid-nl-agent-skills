# /core/uri-version

Deze regel schrijft voor dat de major versie, voorafgegaan door de letter `v`,
opgenomen moet zijn in de URI van het endpoint. In OAS mag deze niet
gespecificeerd worden op `path` niveau; dit zou impliceren dat er binnen
hetzelfde endpoint meerdere (major versies van) API's beschikbaar zijn, terwijl
elke API vergezeld moet worden van een eigen `/openapi.json`.

- Regel:
  https://gitdocumentatie.logius.nl/publicatie/api/adr/2.0.2/#/core/uri-version
- Linter test:
  https://logius-standaarden.github.io/API-Design-Rules/#:~:text=%23%2Fcore%2Furi%2Dversion

## Uitdrukken in OAS

  
</Tabs>