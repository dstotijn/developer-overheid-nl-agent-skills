# FSC (Federated Service Connectivity)

:::info[TL;DR]

De [FSC-standaard](https://fsc-standaard.nl) beschrijft hoe koppelingen voor
gegevensuitwisseling veilig, transparant en beheersbaar kunnen worden opgezet.
De standaard is opgenomen als verplicht onderdeel van het
[Digikoppeling REST API profiel](https://gitdocumentatie.logius.nl/publicatie/dk/restapi/).
Wil je direct met FSC aan de slag dan kan je de referentie implementatie
[OpenFSC](https://docs.open-fsc.nl/) gebruiken.

:::

## Standaardisatie in gegevensuitwisseling

Volgens het principe
[Data bij de Bron](https://www.digitaleoverheid.nl/data-bij-de-bron) moeten
organisaties die verantwoordelijk zijn voor data deze op een bruikbare manier
beschikbaar stellen. Dit principe gaat er voor zorgen dat er veel koppelingen
zullen ontstaan tussen afnemers en bronnen. Om te voorkomen dat er een
onbeheersbaar data-landschap ontstaat van verschillenden manieren van koppelen
is de standaard FSC geschreven. FSC beschrijft hoe koppelingen gemaakt en
beheerd kunnen worden.

De FSC standaard helpt je op het gebied van de volgende thema's:

- **Security**: de FSC standaard beschrijft hoe een aanbieder en afnemer veilig
  kunnen communiceren.
- **Autorisatie**: Toestemming om met een API te verbinden word vastgelegd met
  een digitaal Contract.
- **Beheerbaarheid**: de beheeromgeving geeft je een overzicht van alle
  koppelingen van en naar jouw organisatie. Deze koppelingen kunnen eenvoudig
  worden aangemaakt of ingetrokken.
- **Discovery**: de Directory geeft inzicht in welke API's er worden aangeboden.
- **Logging**: door middel van transactielogging heb je op een
  gestandaardiseerde manier inzicht in welke gegevens er zijn ingezien.
- **Delegatie**: Geef op een transparante wijze een organisatie toestemming om
  names jou een API aan te bieden of te consumeren.

<br/>

[![Image](./img/fsc_graph.png)](./img/fsc_graph.png)

## Aan de slag

Wil je experimenteren met OpenFSC? Dan kan dat op meerdere manieren. Je kan
eenvoudig lokaal met Docker Compose OpenFSC draaien. Of je kan OpenFSC draaien
op een Kubernetes cluster via de Helm charts.

### Met Docker Compose

In deze tutorial leer je hoe je een lokale testomgeving opzet, met als doel een
API aanbieden op de demo omgeving van FSC. Vervolgens kan je de Controller
web-interface gebruiken om je FSC componenten te beheren.

- [Naar de tutorial voor Docker Compose](https://docs.open-fsc.nl/try-fsc/docker/introduction)

### Met Helm

In deze tutorial gebruik je Helm om OpenFSC op een Kubernetes omgeving te
installeren. In deze tutorial leer je hoe je een API kan aanbieden en
consumeren.

- [Naar de tutorial voor Helm](https://docs.open-fsc.nl/try-fsc/helm/introduction)

## Screenshots

[![Image](./img/fsc_directory.png)](./img/fsc_directory.png) Beheeromgeving:
directory view

[![Image](./img/fsc_peers.png)](./img/fsc_peers.png) Beheeromgeving: peers view

[![Image](./img/fsc_services.png)](./img/fsc_services.png) Beheeromgeving:
services view

[![Image](./img/fsc_services_detail.png)](./img/fsc_services_detail.png)
Beheeromgeving: services detail page

[![Image](./img/fsc_inways.png)](./img/fsc_inways.png) Beheeromgeving: inways
view

[![Image](./img/fsc_verbindingen.png)](./img/fsc_verbindingen.png)
Beheeromgeving: verbindingen view

[![Image](./img/fsc_logs.png)](./img/fsc_logs.png) Beheeromgeving: logs view

[![Image](./img/fsc_contracten.png)](./img/fsc_contracten.png) Beheeromgeving:
contracten view

## Externe links

- [Website FSC](https://fsc-standaard.nl/)
- [Technische docs OpenFSC](https://docs.open-fsc.nl)