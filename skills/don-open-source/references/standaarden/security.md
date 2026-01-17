# SECURITY.md

Een SECURITY.md geeft mensen die een kwetsbaarheid in je project hebben gevonden
handvatten om deze op een verantwoorde manier aan je terug te koppelen.

## Waarom is dit belangrijk?

Een SECURITY.md voorkomt dat kwetsbaarheden direct publiek worden gemaakt en
toont aan dat je beveiliging serieus neemt. Het geeft securityonderzoekers
duidelijke instructies voor het melden van problemen, zodat deze kunnen worden
opgelost voordat ze schade aanrichten.

```markdown showLineNumbers title="./SECURITY.md"
# Securitybeleid

## Ondersteunde versies

In deze tabel staat beschreven welke versies van onze codebase worden ge-update
door middel van securitypatches.

| Versie | Ondersteund |
| ------ | ----------- |
| 1.x.x  | ✅          |
| < 1.0  | ❌          |

## Een kwetsbaarheid melden

We nemen de beveiliging van onze software serieus. Als je denkt dat je een
beveiligingskwetsbaarheid hebt gevonden, meld deze dan zoals hieronder
beschreven.

> **Meld beveiligingskwetsbaarheden nooit via openbare GitHub issues.**

### Hoe te melden

Stuur een e-mail naar: [security@organisatie.nl](mailto:security@organisatie.nl)

Vermeld indien mogelijk de volgende informatie:

- Type kwetsbaarheid (bijv. buffer overflow, SQL injection, cross-site
  scripting, etc.)
- Volledige paden van bronbestanden die verband houden met de kwetsbaarheid.
- De locatie van de getroffen broncode (tag/branch/commit of directe URL).
- Speciale configuratie die nodig is om de kwetsbaarheid te reproduceren.
- Stap-voor-stap instructies om de kwetsbaarheid te reproduceren.
- Proof-of-concept of exploit code (indien mogelijk).
- Impact van de kwetsbaarheid, inclusief hoe een aanvaller deze zou kunnen
  misbruiken.

### Wat kun je verwachten

Dit project volgt de CVD-leidraad (Coordinated Vulnerability Disclosure) van het
NCSC. Dit betekent dat we een gestructureerd proces hanteren voor het melden en
afhandelen van beveiligingslekken.

- Je ontvangt binnen 3 werkdagen een bevestiging van je melding.
- We houden je op de hoogte van de voortgang van de oplossing.
- We streven ernaar kritieke kwetsbaarheden binnen 5 werkdagen op te lossen.
- We vermelden je in onze release notes (tenzij je liever anoniem blijft).

## CHANGELOG.md

Beveiligingsupdates worden uitgebracht als patch-versies en gedocumenteerd in
onze [CHANGELOG.md](CHANGELOG.md).

## Contact

Voor vragen over dit beleid, neem contact op via:
[security@organisatie.nl](mailto:security@organisatie.nl).
```