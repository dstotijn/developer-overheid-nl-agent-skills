# CONTRIBUTING.md

Een goede CONTRIBUTING.md helpt potentiële bijdragers om efficiënt en effectief
bij te dragen aan een project.

````markdown showLineNumbers title="./CONTRIBUTING.md"
# Bijdragen aan {{ name }}

Allereerst bedankt dat je wilt bijdragen aan dit project! Zonder jouw input
wordt dit nooit een beter open source project.

## Code of Conduct

Dit project hanteert een [Code of Conduct](CODE_OF_CONDUCT.md). Door bij te
dragen aan dit project ga je akkoord met de voorwaarden hiervan.

## Hoe kan je bijdragen?

Er zijn verschillende manieren om bij te dragen aan dit project:

### Meld een bug

Heb je een bug gevonden? Maak dan een [issue]({{ issueLink }}) aan met:

- Een duidelijke en beschrijvende titel
- Stappen om de bug te reproduceren
- Verwacht gedrag vs. daadwerkelijk gedrag
- Screenshots of foutmeldingen (indien van toepassing)
- Je omgeving (OS, browserversie, etc.)

### Features voorstellen

Heb je een idee voor een nieuwe feature? Open een issue met:

- Een duidelijke beschrijving van de feature
- Waarom deze feature waardevol zou zijn
- Eventuele voorbeelden of mockups

### Documentatie verbeteren

Documentatie kan altijd beter! Pull requests voor verbeteringen aan de
documentatie zijn zeer welkom.

### Code bijdragen

Wil je code bijdragen? Volg dan onderstaand proces.

## Ontwikkelproces

### 1. Fork en clone de repository

```bash
git clone {{ url }}
cd directory-name
```

### 2. Maak een nieuwe branch

```bash
git checkout -b feature/mijn-nieuwe-feature
```

Of voor bugfixes:

```bash
git checkout -b fix/issue-nummer-korte-beschrijving
```

### 3. Installeer dependencies

```bash
# PROJECTSPECIFIEK: pas dit aan voor jouw project
npm install
# of
pip install -r requirements.txt
# of
composer install
```

### 4. Maak je wijzigingen

- Schrijf duidelijke, leesbare code
- Voeg tests toe voor nieuwe functionaliteit
- Update documentatie waar nodig

### 5. Test je wijzigingen

```bash
# PROJECTSPECIFIEK: pas dit aan voor jouw project
npm test
# of
pytest
# of
./vendor/bin/phpunit
```

### 6. Commit je wijzigingen

We gebruiken [Conventional Commits](https://www.conventionalcommits.org/) voor
onze commit messages:

```
<type>(<scope>): <beschrijving>

[optionele body]

[optionele footer]
```

Types:

- `feat`: Een nieuwe feature
- `fix`: Een bug fix
- `docs`: Documentatie wijzigingen
- `style`: Code style wijzigingen (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Toevoegen of wijzigen van tests
- `chore`: Onderhoud (dependencies, etc.)

Voorbeeld:

```
feat(auth): voeg two-factor authenticatie toe

Implementeert TOTP-based 2FA voor gebruikers.

Closes #123
```

### 7. Push naar je fork

```bash
git push origin feature/mijn-nieuwe-feature
```

### 8. Open een Pull Request

- Geef je PR een duidelijke titel en beschrijving
- Link gerelateerde issues
- Zorg dat alle tests slagen
- Wacht op review van een maintainer

## Ontwikkelomgeving

**PROJECTSPECIFIEK**: Voeg specifieke setup instructies toe voor jouw project

### Vereisten

- Node.js >= 18.x / Python >= 3.9 / PHP >= 8.1
- Git >= 2.30
- [Andere specifieke dependencies]

### Lokaal draaien

```bash
# Development server starten
npm run dev
# of
python manage.py runserver
# of
php artisan serve

# Build maken
npm run build
```

### Development tools

- [Link naar lokale development documentatie]
- [Link naar database setup instructies]
- [Link naar API documentatie]

## Testing

**PROJECTSPECIFIEK**: Voeg test-instructies toe

```bash
# Alle tests draaien
npm test

# Met coverage
npm run test:coverage

# Specifieke test
npm test -- auth.test.js

# Linting
npm run lint

# Formatting
npm run format
```

### Test requirements

- Nieuwe features moeten minimaal 80% code coverage hebben
- Alle tests moeten slagen voordat een PR gemerged wordt
- Voeg zowel unit als integration tests toe waar relevant

## Toegankelijkheid (Accessibility)

Voor Nederlandse overheidsprojecten is toegankelijkheid wettelijk verplicht:

- Volg [WCAG 2.1](https://www.w3.org/WAI/WCAG21/quickref/) niveau AA
- Test met screenreaders (NVDA/JAWS)
- Zorg voor keyboard navigatie
- Gebruik semantische HTML
- Test kleurcontrast (minimaal 4.5:1)

## Beveiliging (Security)

- Meld beveiligingsproblemen **NIET** via publieke issues
- Gebruik het proces beschreven in SECURITY.md
- Volg [OWASP Top 10](https://owasp.org/www-project-top-ten/) best practices
- Voor overheidsprojecten: houd rekening met
  [BIO](https://www.digitaleoverheid.nl/overzicht-van-alle-onderwerpen/cybersecurity/kaders-voor-cybersecurity/baseline-informatiebeveiliging-overheid/)
  normen

## Community

**PROJECTSPECIFIEK**: Voeg relevante community informatie toe

- Community calls: zijn er vaste community calls?
- Chat: link naar bijvoorbeeld het Slack-kanaal.
- Mailinglist: link naar de nieuwsbrief.
- Roadmap: link naar de roadmap.

## Licentie

Door bij te dragen aan dit project ga je ermee akkoord dat je bijdragen worden
gelicenseerd onder de **LICENTIE** licentie. Dit betekent dat:

- Je het auteursrecht behoudt op je bijdragen
- Je bijdragen beschikbaar komen onder dezelfde open source licentie
- De code gebruikt mag worden door andere overheidsorganisaties

## Erkenning

Bijdragers worden vermeld in:

- CHANGELOG.md bij elke release
- De AUTHORS.md file (optioneel)

---

Bedankt voor je bijdrage!

_Dit project wordt onderhouden door ORGANISATIE en de open source community._
````

## Wat neem je erin op?

### 1. Introductie

Een korte uitleg over het project en waarom bijdragen belangrijk zijn. Eventueel
een verwijzing naar de doelstellingen of missie van het project.

### 2. Hoe je kunt bijdragen

- Bijdragen aan de code (bugfixes, nieuwe features, refactoring).
- Aandragen van issues (feature requests).
- Deelnemen aan discussies (op Mattermost, Github, Slack of een ander platform).
- Documentatie verbeteringen.
- Testen en bug reports indienen.
- Design, UX of accessibility verbeteringen.

### 3. Voordat je begint

Waar moet je rekening mee houden als je een bijdrage wilt doen? Verwijs naar de
lijst met bestaande issues en leg uit hoe je een nieuwe issue opent. Geef aan of
je eerst met de maintainers dient te overleggen voordat je een grote feature
aandraagt.

### 4. Technische richtlijnen

- Code style: verwijzing naar linters, formattering, en naming conventions.
- Commit messages: bijvoorbeeld conventies zoals
  [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).
- Pull requests: hoe je een PR indient.
- Reviewproces: hoe de feedbackloop werkt en wie reviews uitvoert.

### 5. Opzetten van de ontwikkelomgeving

- Hoe je het project lokaal installeert en draait.
- Vereisten zoals dependencies, SDK's, en buildtools.
- Eventuele scripts om het project snel op te zetten.
- Heb je documentatie voor het lokaal opzetten van het project in de
  `README.md`? Link hier dan vooral naartoe.

### 6. Tests en kwaliteitscontrole

- Hoe je tests draait en toevoegt.
- Code coverage en teststrategie (unit, integration, e2e).
- Continuous Integration: welke checks en pipelines draaien er?
- Zorg ervoor dat bijdragers zelf alle tests lokaal kunnen vinden en draaien.

### 7. Gedragscode

- Verwijzing naar een `CODE_OF_CONDUCT.md` (indien van toepassing).
- Noem de basisprincipes voor een inclusieve en respectvolle samenwerking.
- Geef aan met wie een deelnemer contact kan opnemen in het geval dat de
  gedragscode wordt geschonden.

### 8. Licentie en juridische zaken

- Vertel onder welke licentie bijdragen vallen.
- Welke implicaties heeft de licentie voor de developer?
- Of bijdragers een Contributor License Agreement (CLA) moeten tekenen.

### 9. Bestuur

Wie bepaalt welke bijdragen uiteindelijk wel en niet worden geaccepteerd?
Verwijs eventueel naar de `GOVERNANCE.md`. Vermeld onder dit kopje ook wie er
betaalt voor het beoordelen en verwerken van de bijdragen. Als meerdere
organisaties bij het project betrokken zijn, neem ze dan op in een lijst en
benoem hun rollen.

### 10. Contact en ondersteuning

- Hoe en waar je vragen stelt (bijv. Discord, Slack, GitHub Discussions).
- Wie je kunt benaderen voor hulp.
- Vermeld hier ook contactgegevens (bijv. e-mailadressen)
- Voeg hier ook links toe naar communicatiekanalen (Slack, Mattermost,
  Mastodon).

## Voorbeelden

- Zie de
  [contributing guidelines](https://docs.openkat.nl/developer-documentation/contributor/index.html)
  van OpenKAT.

## Externe links

- [Standaard voor Publieke Code / Criterium 4: verwelkom bijdragers](https://codefor.nl/community-translations-standard/nl/criteria/welcome-contributors.html)