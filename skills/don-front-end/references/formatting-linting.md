# Formatting & Linting

Bij het ontwikkelen van front-end code is het belangrijk om consistente
code-stijl en kwaliteit te waarborgen. Het feit dat front-end code nagenoeg
altijd in JavaScript is geschreven geeft hier nog meer reden toe. JavaScript
geeft je namelijk heel veel vrijheid om problemen op verschillende manieren op
te lossen. Linting geeft je juist een mogelijkheid om hierin wat striktere
afspraken te maken.

:::success[**TL;DR - Formatting is een goed idee, gebruik bijvoorbeeld Biome**]

Om te voorkomen dat er discussie binnen je team ontstaat over bepaalde
stijlkeuzes is het slim om je code te linten en te formatten. Dit voorkomt
**inconsistenties** en **bugs** in de codebase en maakt hem beter leesbaar. Een
snelle en moderne tool die dit voor je doet is [**Biome**](#biome-1).

:::

Voordelen van formatting en linting zijn:

- **✔️ Consistentie in de codebase**: je code ziet er overal hetzelfde uit,
  ongeacht wie het geschreven heeft.

- **✔️ Fouten vroegtijdig opsporen**: linters vangen veelgemaakte fouten op.
  Denk aan: ongebruikte variabelen, ontbrekende return statements, verkeerde
  vergelijkingen (`==` versus `===`).

- **✔️ Betere code kwaliteit**: linters dwingen je om best practices te volgen.
  Ze waarschuwen voor potentieel problematische patronen.

- **✔️ Makkelijkere onboarding nieuwe teamleden**: nieuwe developers leren
  meteen de juiste patronen en stijl.

## Wat is formatting?

Formatting verwijst naar de stijl van je code: hoe deze eruitziet qua
inspringing, spaties, regels en leestekens. Een formatter zorgt ervoor dat alle
code in een project er uniform uitziet, ongeacht wie de code heeft geschreven.

### Typische formatting-regels

- Gebruik van spaties of tabs voor inspringing en hoeveel (2, 4, etc.)
- Maximale regellengte (hoeveel karakters)
- Gebruik van enkele of dubbele aanhalingstekens ('' vs "")
- Komma's aan het einde van objecten of arrays (trailing commas)

## Wat is linting?

Linting controleert de logica en kwaliteit van je code. Een linter analyseert je
code op fouten, onlogische patronen, onveilige constructies en slechte
praktijken. Waar formatting zich richt op stijl, richt linting zich op
correctheid en consistentie.

### Typische linting-controles

- Ongebruikte variabelen of imports
- Vergelijkingen met `==` in plaats van `===`
- Niet-gedefinieerde variabelen
- Console-statements in productiecode

## Populaire Tools

### Prettier

Prettier is een "opinionated formatter" - het legt één vaste stijl op, zodat je
geen eindeloze discussies voert over spaties en puntkomma’s. Het ondersteunt
veel programmeertalen en kan worden geïntegreerd in verschillende editors en
build-tools.

### ESLint

[ESLint] is een veelgebruikte **linter** voor JavaScript en TypeScript. Het
biedt uitgebreide mogelijkheden om je code te analyseren en te controleren op
fouten en inconsistenties. Je kunt ESLint uitbreiden met plug-ins voor
frameworks zoals React, Vue of Next.js.

### Stylelint

[Stylelint] is een **linter** voor CSS en aanverwante talen zoals SCSS en Less.
Het helpt bij het handhaven van consistente stijlen en het voorkomen van fouten
in je stylesheets. Voorbeelden van regels die Stylelint kan afdwingen zijn het
gebruik van onnodige units, zoals `0px`, de volgorde van properties en het
vermijden van dubbele definities.

### Biome

[Biome] is de moderne opvolger van de traditionele ESLint + Prettier combinatie.
Het is geschreven in Rust, waardoor het razendsnel is, en het combineert
**formatting, linting en code-analyse** in één tool. Biome ondersteunt
JavaScript, TypeScript, JSON, CSS, HTML, Markdown en meer. Biome is zeer
configureerbaar, je kan kiezen voor de gekozen _default_ instellingen of deze
aanpassen naar je eigen regels. Configuratiebestanden kunnen per map worden
overgeschreven en overerven.

## Integratie in je workflow

Deze tools kunnen worden geïntegreerd in je ontwikkelworkflow op verschillende
manieren:

- **Editor-integratie**: De meeste moderne code-editors zoals VSCode en Webstorm
  ondersteunen plugins voor Prettier, ESLint, Stylelint en andere tools.
  Hierdoor worden fouten en formatteerproblemen direct tijdens het typen
  gemarkeerd.
- **Pre-commit hooks**: Tools zoals Husky kunnen worden gebruikt om linting en
  formatting uit te voeren voordat code wordt gecommit naar een
  versiebeheersysteem zoals Git. Dit zorgt ervoor dat alleen goedgekeurde code
  wordt toegevoegd aan de codebase.
- **Continuous Integration (CI)**: Linting en formatting kunnen worden opgenomen
  in je CI/CD-pijplijn om ervoor te zorgen dat alle code die wordt samengevoegd
  aan de kwaliteitsnormen voldoet.

## Voorbeelden

### Prettier

Installatie (met npm):

```bash
npm install --save-dev --save-exact prettier
```

Voorbeeld configuratiebestand (`.prettierrc.json`)

```json
{
  "semi": true,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}
```

Voeg ook een [`.prettierignore`](https://prettier.io/docs/ignore) toe om
bestanden of mappen uit te sluiten van formatting.

Commando: (_Let op:_ dit commando kan alle bestanden wijzigen)

```bash
npx prettier . --write
```

Meer documentatie: [Prettier Docs](https://prettier.io/docs/)

### ESLint

Installatie en configuratie (met npm):

```bash
npm init @eslint/config@latest
```

Voorbeeld configuratiebestand (eslint.config.js)

```js

  { files: ["**/*.js"], plugins: { js }, extends: ["js/recommended"] },
  {
    rules: {
      "no-unused-vars": "warn",
      "no-undef": "warn",
    },
  },
]);
```

Commando: (_Let op:_ `--fix` verbetert bestanden waar mogelijk)

```bash
npx eslint . --fix
```

Meer documentatie: [ESLint Docs](https://eslint.org/docs/latest/)

### Biome

Installatie (met npm):

```bash
npm i -D -E @biomejs/biome
```

Voorbeeld configuratiebestand (`biome.json`), makkelijk te genereren met:

```bash
npx @biomejs/biome init
```

```json
{
  "$schema": "https://biomejs.dev/schemas/2.0.5/schema.json",
  "formatter": {
    "enabled": false
  },
  "linter": {
    "enabled": false
  },
  "assist": {
    "enabled": false
  },
  "overrides": [
    {
      "includes": ["**/*.astro"],
      "linter": {
        "rules": {
          "style": {
            "useConst": "off",
            "useImportType": "off"
          },
          "correctness": {
            "noUnusedVariables": "off",
            "noUnusedImports": "off"
          }
        }
      }
    }
  ]
}
```

Commando:

```bash
npx biome check --write
```

Linting en formatting kunnen ook apart worden uitgevoerd met `biome lint` en
`biome format`.

Meer documentatie: [Biome Docs](https://biomejs.dev/docs/).

### Integratie in de workflow

#### Automatisch bij opslaan

De meeste IDE’s, zoals VS Code, kunnen automatisch [Prettier] en [ESLint] of
[Biome] draaien bij het opslaan van bestanden.

- Prettier:
  [VSCode Extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode),
  [WebStorm Integration](https://www.jetbrains.com/help/webstorm/prettier.html),
  [Sublime Text Integration](https://packagecontrol.io/packages/JsPrettier)
- ESLint:
  [ESLint VSCode Extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint),
  [WebStorm Integration](https://www.jetbrains.com/help/webstorm/eslint.html),
  [Sublime Text Integration](https://packagecontrol.io/packages/ESLint)
- Biome:
  [Biome VSCode Extension](https://marketplace.visualstudio.com/items?itemName=biomejs.biome),
  [WebStorm Integration](https://plugins.jetbrains.com/plugin/22761-biome),
  [Sublime Text Integration](https://github.com/sublimelsp/LSP-biome)

#### Pre-commit hooks

Met [Husky](https://typicode.github.io/husky/) en
[lint-staged](https://github.com/lint-staged/lint-staged) of
[Lefthook](https://github.com/evilmartians/lefthook) kun je pre-commit hooks
instellen om formatting en linting uit te voeren voordat code wordt gecommit.

Voorbeeld met [Biome] in een Shell script

```bash
#!/bin/sh
set -eu

npx @biomejs/biome check --staged --files-ignore-unknown=true --no-errors-on-unmatched
```

#### Continuous Integration (CI)

Je kunt linting en formatting opnemen in je CI/CD-pijplijn met tools zoals
GitHub Actions, GitLab CI of Jenkins om ervoor te zorgen dat alle code die wordt
samengevoegd aan de kwaliteitsnormen voldoet.

De [Prettier] GitHub Action werkt met de
[`autofix.ci`-app](https://github.com/apps/autofix-ci). Zie de
[Prettier CI-documentatie](https://prettier.io/docs/ci). Voor [Biome] is een
first party [GitHub Action](https://github.com/marketplace/actions/setup-biome)
beschikbaar, zie de
[Biome CI-documentatie](https://biomejs.dev/recipes/continuous-integration/).

## Conclusie

Wanneer elke ontwikkelaar werkt volgens dezelfde richtlijnen, verdwijnt veel van
de frictie die normaal gesproken tijdens samenwerking of code reviews ontstaat.
Teams hoeven minder tijd te besteden aan het bespreken van stijlverschillen en
kunnen zich richten op inhoudelijke verbeteringen en architecturale
beslissingen. Het resultaat is een stabielere codebase en een meer voorspelbare
ontwikkelervaring. Door deze tools te integreren in je workflow, kun je de
kwaliteit en consistentie van je code aanzienlijk verbeteren.

### Biome: een eenvoudige setup en een tool met snelle performance

Een tool zoals [Biome] die zowel formatting als linting combineert, kan de setup
en het onderhoud van deze tools vereenvoudigen, waardoor teams sneller aan de
slag kunnen met het handhaven van codekwaliteit.

:::info[Tip]

Ga je linting en formatting tools gebruiken in een bestaand project?
Waarschijnlijk zullen veel bestanden aangepast worden door de tools. Het is aan
te raden om deze wijzigingen in een aparte commit te plaatsen, en deze te mergen
op een moment dat er weinig actieve ontwikkeling plaatsvindt. Zo voorkom je dat
er veel merge-conflicten ontstaan met andere lopende werkzaamheden.

:::

[Prettier]: https://prettier.io/
[ESLint]: https://eslint.org/
[Stylelint]: https://stylelint.io/
[Biome]: https://biomejs.dev/
[Oxc]: https://oxc.rs/