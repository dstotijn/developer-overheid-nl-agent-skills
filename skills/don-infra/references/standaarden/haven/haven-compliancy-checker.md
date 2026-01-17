# Haven compliancy checker (CLI)

In deze sectie laten we zien hoe je met de Haven Compliancy Checker een bestaand
cluster kan controleren op Haven Compliancy.

## Voorbereiding

Zorg dat je [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
hebt geïnstalleerd op je lokale computer. Daarnaast heb je cluster admin rechten
nodig om het cluster te valideren op compliancy.

## Installeren

De Compliancy Checker is onderdeel van de Haven CLI. We bieden de Haven CLI aan
voor meerdere besturingssystemen, waaronder macOS, Linux en Windows.

1. Download de
   [gewenste versie van de Haven CLI](https://gitlab.com/commonground/haven/haven/-/packages)
1. Pak de download uit (`unzip haven-v9.0.0-darwin-amd64.zip`)
1. Verplaats de binary in de uitgepakte map naar het gewenste pad
   (`mv darwin-amd64/haven /usr/local/bin/haven`)

## Checks uitvoeren

Start de Haven Compliancy Checker als volgt:

```bash
$ haven check
```

Binnen enkele ogenblikken toont het systeem de resultaten:

![Schermafbeelding van de Compliancy Checker](./img/schermafbeelding-compliancy-checker.png)

Een cluster is Haven-compliant indien alle checks slagen, inclusief de CNCF
checks. Zie ook `haven check --help`.

## Kubernetes conformance tests

Het is ook mogelijk om de Kubernetes conformance tests uit te voeren. Installeer
eerst [Sonobuoy](https://sonobuoy.io/docs/). Voer daarna de checks uit zoals
hierboven vermeld staat. Voeg daarbij de flag `--cncf=true` toe.

## De basis

Een Haven Compliant cluster is de basis waarop verder gebouwd kan worden.
Zorgvuldig beheer is doorlopend van belang voor de operatie en veiligheid, denk
hierbij aan:

1. Het up-to-date houden van het cluster.
2. Het up-to-date houden van de deployments op het cluster.
3. Goed beheer voeren op de toegangsrechten tot het cluster.

Ontwikkelaars zullen voorts het cluster in gebruik gaan nemen, voor hen hebben
we ter illustratie ook de
[Ontwikkelen op Haven](https://haven.commonground.nl/techniek/voorbereiding)
documentatie pagina's.

## Links

- [Readme Haven CLI](https://gitlab.com/commonground/haven/haven/-/tree/main/haven/cli?ref_type=heads)

<!-- This license was moved to the bottom of the page since it breaks previews in the search mode when its located at the top -->
<!---
Copyright © VNG Realisatie 2019-2023
Licensed under EUPL v1.2
-->