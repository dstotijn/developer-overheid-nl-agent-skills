# /core/publish-openapi

Deze regel schrijft voor dat elke api een `/openapi.json` file moet publiceren
zodat tooling hier gebruik van kan maken. Hiermee kunnen tools zoals
[Swagger UI](https://swagger.io/tools/swagger-ui/) automatisch documentatie
websites bouwen en kunnen er [TypeScript types](https://openapi-ts.dev/) worden
gegenereerd. Dit alles zorgt ervoor dat een API inzichtelijk is, maar ook
makkelijk te gebruiken voor eindgebruikers

- Regel:
  https://gitdocumentatie.logius.nl/publicatie/api/adr/2.0.2/#/core/publish-openapi

## Waarom moet dit bestandje publiekelijk beschikbaar zijn?

API's zijn niet per definitie open, vanwege gevoelige data die zij exposen of
vanwege het enforceren van rate limits. Hierdoor zijn API's niet altijd
bereikbaar voor eenieder. Toch stelt deze regel dat het `/openapi.json` bestand
wel altijd bereikbaar moet zijn, zonder authenticatie en autorisatie.

De bovengenoemde tooling is de grootste reden hiervoor: als de specificatie
altijd beschikbaar is, kunnen afnemers hier gebruik van maken. Denk bijvoorbeeld
aan CI systemen die geen productie toegang moeten hebben tot een API, maar wel
de TypeScript types willen genereren. Of dat developers eerst de documentatie
willen doorlezen, voordat ze beslissen of ze een API key willen aanvragen.

Het beschikbaar maken van de `/openapi.json` voor iedereen en op een standaard
locatie zorgt ervoor dat afnemers hier tooling omheen kunnen bouwen, zonder dit
voor elke API anders af te handelen. Vanwege deze vraag naar uniformiteit is dit
dus gestandaardiseerd.

## Implementeren in code

Afhankelijk van het framework van de server die de API host zijn er meerdere
oplossingen.

  
</Tabs>