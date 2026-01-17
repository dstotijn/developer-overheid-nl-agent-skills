# Quality-time

"@rijkshuisstijl-community/components-react"; import Author from
'@theme/Blog/Components/Author';

**tl;dr:** Quality-time is een open source tool die je kan helpen de kwaliteit
van je maatwerksoftware te bewaken en technical debt te managen.

Mijn werkgever, ICTU, doet projecten met/voor andere overheden om de digitale
dienstverlening door de overheid te verbeteren. Vaak ontwikkelen we daarbij
maatwerksoftware. Voorbeelden die je misschien kent zijn het
[Landelijk Register Kinderopvang](https://www.landelijkregisterkinderopvang.nl)
of het [Leeroverzicht](https://www.leeroverzicht.nl).

### Tool voor kwaliteitsmanagers

Om de kwaliteit van de software die we ontwikkelen en/of onderhouden te bewaken
hebben we in elk project een kwaliteitsmanager. En om die kwaliteitsmanagers,
het softwareontwikkelteam, en andere belanghebbenden, inzicht te geven in de
kwaliteit van de software en de ontwikkelprocessen, gebruiken we
[Quality-time](https://github.com/ICTU/quality-time).

### Metrics uit allerlei bronnen

Quality-time verzamelt informatie uit
[andere tools](https://quality-time.readthedocs.io/en/latest/reference.html#sources)
die je toch al gebruikt in je softwareproject, zoals SonarQube, GitLab,
Dependency-Track, Jira, Robot Framework, OWASP ZAP, etc., en vergelijkt de
meetwaardes met instelbare normen. Op die manier kan Quality-time je waarschuwen
als meetwaardes afwijken en welke
[metrieken](https://quality-time.readthedocs.io/en/latest/reference.html#metrics)
dus aandacht nodig hebben. Denk aan gefaalde testen, nieuwe CVE's, violations
uit linters, te veel open bugs, accessibility violations, doorlooptijd van
builds, outdated dependencies, etc. etc.

### Technical debt managen

Omdat technical debt onvermijdelijk is, kun je dit in Quality-time expliciet
managen. Als een meting niet aan de norm voldoet en je kunt dit niet op korte
termijn fixen, accepteer je de meting als technical debt. Vervolgens kun je er
een geplande einddatum aan geven en/of een Jira-issue aan koppelen zodat
Quality-time je weer kan waarschuwen als je de technical debt niet volgens plan
oplost.

Quality-time is open source en beschikbaar via
[GitHub](https://github.com/ICTU/quality-time/). De documentatie staat op
[Read the Docs](https://quality-time.readthedocs.io/en/latest/). Je draait
Quality-time via Docker of Kubernetes.

Wij hebben al jaren veel plezier van Quality-time in onze projecten. Het zou
mooi zijn als het ook voor jouw project/organisatie nuttig kan zijn?!

## Externe links

- [Naar de github van Quality-time](https://github.com/ICTU/quality-time)