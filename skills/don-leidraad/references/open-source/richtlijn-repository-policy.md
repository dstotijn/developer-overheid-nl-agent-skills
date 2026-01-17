# Richtlijn: Repository policy

Een repository policy beschrijft de regels waaraan de code repositories van een organisatie moeten voldoen. Denk aan toegestane licenties, de code of conduct, security contacts, de minimaal te hanteren security tools, branch protection, versionering, etc. Een repository policy is typisch van toepassing op alle publieke code repositories van een organisatie.

Een voorbeeld van een repository policy is https://github.com/ICTU/github-policy.

## Rationale: Waarom een repository policy?

Overheden die software publiceren op bijvoorbeeld GitHub, GitLab of Codeberg, hebben al snel tientallen of zelfs honderden repositories. Om te zorgen dat de repositories voldoen aan de minimale vereisten van transparantie en om hergebruik te vergemakkelijken maak je een repository policy die beschrijft aan welke richtlijnen de inrichting en het gebruik van repositories moet voldoen.

## Doelgroep: Wie zijn er betrokken bij een repository policy?

De volgende doelgroepen kunnen met de repository policy:
security officers,
kwaliteitsmanagers en
developers.

Security officers en kwaliteitsmanagers stellen de repository policy op en controleren van tijd tot tijd of de repositories (nog) voldoen aan de policy.

Developers passen de repository policy toe als ze een nieuwe repository aanmaken en controleren van tijd tot tijd of hun repositories (nog) voldoen aan de policy.

## Implementatie: Hoe implementeer je een repository policy?

Maak een losse repository en neem in het `README.md`-bestand de spelregels op.

Voeg bestanden toe die andere repositories moeten of kunnen gebruiken. Denk aan licenties, code of conduct en een voorbeeld `publiccode.yml`.

Communiceer de policy met je collega developers.

Organiseer het periodiek controleren van de repositories tegen de policy.

### Methoden en technieken

Geen bekend.

### Tools

#### Repository initialisatie

Er zijn verschillende tools beschikbaar om repositories te initialiseren aan de hand van templates. Voorbeelden zijn Cookiecutter, Copier en Yeoman (vooral gericht op webapplicaties).

#### Publiccode.yml

Voor het maken en lezen van `publiccode.yml` bestanden zijn tools beschikbaar:
- [Publicode.yml editor](https://developer.overheid.nl/kennisbank/open-source/tools/publiccode-yml-editor)
- [Publicode.yml parser](https://developer.overheid.nl/kennisbank/open-source/tools/publiccode-yml-parser)

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je policy zorgt dat het eigenaarschap van de repository duidelijk is
- Je policy zorgt dat het duidelijk is hoe security incidenten gemeld kunnen worden.
- Je policy schrijft voor dat repositories een [`publiccode.yml`](https://github.com/publiccodeyml/publiccode.yml) bestand bevatten waarmee repositories 'discoverable' worden.
- Je policy schrijft een licentie voor of maakt duidelijk welke licenties acceptabel zijn voor je organisatie.
- Je policy schrijft een code of conduct voor.
- Je controleert regelmatig of de repositories van je organisatie voldoen aan de policy.

Wanneer ben je echt goed bezig?

- Je automatiseert het controleren of repositories aan de policy voldoen.

## Wanneer is deze richtlijn van toepassing?

Deze richtlijn is van toepassing op publieke repositories. Uiteraard kan het geen kwaad je policy ook voor private repositories te gebruiken.

## Bronnen

### Wetten

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

- The publiccode.yml Standard, https://github.com/publiccodeyml/publiccode.yml
- Keep a changelog, https://keepachangelog.com/en/1.1.0/
- Semantic versioning, https://semver.org/spec/v2.0.0.html

### Communities

- Geen bekend

### Literatuur

- Geen bekend.

### Bronnen op developer.overheid.nl

- [README.md](https://developer.overheid.nl/kennisbank/open-source/standaarden/readme-md)
- [CODE_OF_CONDUCT.md](https://developer.overheid.nl/kennisbank/open-source/standaarden/code-of-conduct-md)
- [CONTRIBUTING.md](https://developer.overheid.nl/kennisbank/open-source/standaarden/contributing-md)
- [PROJECT_GOVERANCE.md](https://developer.overheid.nl/kennisbank/open-source/standaarden/project-governance-md)
- [Publiccode.yml](https://developer.overheid.nl/kennisbank/open-source/standaarden/publiccode-yml)
- [Een licentie kiezen](https://developer.overheid.nl/kennisbank/open-source/tutorials/open-source-software-licenties)