# Axe accessibility checker

[Axe](https://www.deque.com/axe/) is een veelgebruikte accessibility-checker die
WCAG‑problemen (grotendeels) automatisch kan opsporen. Binnen DON draait Axe
dagelijks via een geplande GitHub Actions workflow die ons CLI-script aanroept.
Desgewenst kun je dezelfde tooling lokaal draaien om resultaten te reproduceren.

## Browser: Axe DevTools

Axe DevTools is een browserplugin voor Chrome en Firefox waarmee je snel een
enkele pagina kunt toetsen. We gebruiken deze plugin niet in de
standaardpipeline, maar hij is handig voor:

- tussentijds controleren tijdens ontwikkeling
- de exacte DOM‑locaties van overtredingen inspecteren
- regressies reproduceren die je in de geautomatiseerde rapportage ziet

Meer informatie en installatie-instructies:
[Axe DevTools](https://www.deque.com/axe/devtools).

## Command line & lokaal debuggen

We gebruiken `@axe-core/cli` in combinatie met `scripts/wcag-sitemap-check.js`.
Dat script leest de `sitemap.xml` van een lokaal draaiende site en draait Axe
headless voor elke URL.

### Waarom een apart script?

- Docusaurus genereert automatisch een `sitemap.xml` met alle gepubliceerde
  pagina's. Door die lijst te gebruiken hoeven we geen URL-lijst bij te houden.
- Nieuwe pagina's komen vanzelf mee in de check zodra ze in de sitemap
  terechtkomen (bijvoorbeeld na een nieuwe doc of blogpost).
- Axe CLI kent geen ingebouwde "crawl" functie; met het script houden we de
  logic klein maar krijgen we toch volledige dekking.
- Het script kan eenvoudig worden uitgebreid, bijvoorbeeld met filters voor
  bepaalde paden of een alternatief sitemap-endpoint (testomgeving, staging,
  enzovoort).

### Voorbereiding

- Node.js 18+, pnpm en Google Chrome zijn geïnstalleerd.
- Het Docusaurus‑project draait lokaal op `http://localhost:3000`. Start
  bijvoorbeeld:
  ```bash
  pnpm run start:docusaurus
  ```
  of bouw en serveer statische bestanden:
  ```bash
  pnpm run build
  pnpm dlx http-server build --port 3000
  ```
- Zorg dat `node_modules` up-to-date zijn (`pnpm install`). De `pnpm` override
  in `package.json` zorgt dat de juiste ChromeDriver voor Chrome 140 wordt
  opgehaald.

### Draai de Axe-check

```bash
node scripts/wcag-sitemap-check.js
```

Wat er gebeurt:

- Het script haalt de sitemap op en loopt alle `loc`-links af.
- Voor elke pagina wordt `npx axe <url> --exit` aangeroepen.
- Bij fouten wordt `wcag-report.txt` geschreven en het proces stopt met exitcode
  `1`. Zonder issues krijg je dezelfde file met een succesbericht en exitcode
  `0`.

Voorbeeld van een foutblok:

```text
========================================
WCAG issues found on: https://developer.overheid.nl/blog/archive
  Violation of "heading-order" with 1 occurrences!
    Ensure the order of headings is semantically correct. Correct invalid elements at:
     - #\32 025
  Violation of "landmark-no-duplicate-banner" with 1 occurrences!
    Ensure the document has at most one banner landmark. Correct invalid elements at:
     - .ro-header
  Violation of "landmark-unique" with 1 occurrences!
    Ensure landmarks are unique. Correct invalid elements at:
     - .ro-header
3 Accessibility issues detected.
========================================
```

De selectors onder `Correct invalid elements at:` helpen je het element in de
DOM terug te vinden. Open de pagina in je browser, start Axe DevTools en check
dezelfde regel voor extra context.

## Automatisering met GitHub Actions

De workflow `.github/workflows/check-wcag.yml` draait wekelijks (zondag 02:00
UTC) en is daarnaast handmatig te starten vanuit de default branch via
`workflow_dispatch`. Globaal doet de job het volgende:

1. Checkout van de repository.
2. pnpm installeren + dependencies binnenhalen.
3. Docusaurus build uitvoeren.
4. Statische bestanden serveren op poort 3000.
5. `node scripts/wcag-sitemap-check.js` draaien.
6. Het rapport (`wcag-report.txt`) uploaden naar Slack.

Handmatig triggeren:

- Web UI: ga naar **Actions → Check WCAG compliance → Run workflow** en kies de
  branch (alleen zichtbaar op de default branch).
- GitHub CLI:
  ```bash
  gh workflow run check-wcag.yml --ref <branch>
  ```

Het Slack‑gedeelte gebruikt `SLACK_BOT_TOKEN` en `SLACK_CHANNEL_ID` uit de
repository secrets. Zonder deze secrets slaat de workflow het uploaden over of
faalt de stap.

## Aanpassen en uitbreiden

- Wil je een andere omgeving toetsen (bijvoorbeeld acceptatie)? Pas
  `SITEMAP_URL` in `scripts/wcag-sitemap-check.js` aan of maak een kopie van het
  script.
- Voeg filters toe met Axe flags (bijv. `--tags wcag21aa`) door de command
  string in het script uit te breiden.
- Overweeg om een npm-script toe te voegen, bijvoorbeeld:
  ```json
  "scripts": {
    "wcag:check": "node scripts/wcag-sitemap-check.js"
  }
  ```
  zodat je `pnpm run wcag:check` kunt draaien.