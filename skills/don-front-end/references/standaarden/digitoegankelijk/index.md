# DigiToegankelijk

:::info[Verplichte standaard]

Deze standaard is
[verplicht voor alle websites](https://www.digitoegankelijk.nl/wetgeving) van de
overheid.

:::

Dit artikel heeft als doel om developers ondersteuning te bieden bij het
implementeren van de standaard
[DigiToegankelijk](https://www.forumstandaardisatie.nl/open-standaarden/digitoegankelijk-en-301-549-met-wcag-21)
zoals vastgesteld door het Forum Standaardisatie.

Sinds 1 juli 2018 zijn overheidsorganisaties verplicht
[zich te houden](https://www.forumstandaardisatie.nl/open-standaarden/digitoegankelijk-en-301-549-met-wcag-21)
aan de [WCAG 2.1](https://www.w3.org/TR/WCAG21/) richtlijnen. Dit om te zorgen
dat zoveel mogelijk Nederlandse burgers, ook mensen met een beperking gebruik
kunnen maken van overheidsdiensten.

## Toegankelijkheid voor iedereen

Toegankelijkheid gaat over het geschikt maken van websites, apps en documenten voor gebruikers met een functiebeperking. 

Sommige burgers hebben **permanente
functiebeperkingen**:

- slechthorendheid en doofheid
- lichtgevoeligheid, slechtziendheid en blindheid
- spraakbeperkingen
- motorische beperkingen
- cognitieve beperkingen

Naast permanente functiebeperkingen, zijn er ook:

- **Tijdelijke functiebeperkingen**, zoals een gebroken pols.
- **Situationele functiebeperkingen**, bijvoorbeeld fel zonlicht op een scherm
  of een gebruiker die een baby op de arm draagt.

De WCAG 2.1 bevat succescriteria die barrières wegnemen. Denk aan bijvoorbeeld: 

- dat de website goed blijft werken als de gebruiker inzoomt.
- dat de website niet afhankelijk is van muisgebruik, maar net zo goed werkt met toetsenbord, stem- en touchbediening.
- dat een bepaalde bewerking duidelijk gemarkeerd is als "gevaarlijk", zonder dat dit afhangt van de rode kleur van de de desbetreffende knop. 

De WCAG 2.1 dient toegepast te worden op:

- Websites, waaronder Single Page Applications (denk aan HTML, CSS, SVG,
  JavaScript)
- Documenten (zoals PDF, Word, Excel)
- Mobiele apps (zoals op iOS en Android)

## Drie conformiteitsniveaus (A, AA, AAA)

Elk van de 78 successcriteria in WCAG 2.1 heeft een conformiteitsniveau.
Websites en apps kunnen verklaren tot op welk niveau ze voldoen. De drie niveaus
die WCAG onderscheidt, zijn:

- Niveau A (laagste niveau), 30 succescriteria
- Niveau AA, 20 succescriteria
- Niveau AAA (hoogste niveau), 28 succescriteria

In Nederland is het voor overheden verplicht om te voldoen tot niveau AA. Op
niveau AAA kun je het beste per criterium inschatten of mogelijk is om te
voldoen.

## Correct HTML-gebruik voor toegankelijkheid

Belangrijk voor een toegankelijke website is dat je HTML-syntax correct
gebruikt. Je wilt ervoor zorgen dat de structuur in je websites en apps die
visueel zichtbaar is, terugkomt in de HTML. Zo kunnen hulptechnologieën, zoals
screenreaders, je structuur ontsluiten op een manier die werkt voor de
gebruiker. Bovendien maak je je eigen code leesbaarder en profiteer je van de
standaardfunctionaliteiten die HTML biedt.

Wat je misschien niet direct zou verwachten, is dat HTML zelf ook een standaard
is. Forum Standaardisatie
[beveelt de Nederlandse overheid aan](https://www.forumstandaardisatie.nl/open-standaarden/html)
om de HTML standaard te gebruiken zoals die door de standaardisatie-organisatie
WHATWG is vastgelegd.

[WHATWG: The elements of HTML](https://html.spec.whatwg.org/multipage/#toc-semantics)

### Alt text

Om afbeeldingen toegankelijk te maken voor gebruikers met screenreaders is een
beschrijving of "alt-text" nodig. De screenreader leest dan deze tekst voor als
hij de afbeelding tegenkomt.

Een voorbeeld van een alt-text:

```html
<img
  src="domtoren.jpg"
  alt="Een foto van de Domtoren in Utrecht op een zonnige middag in de zomer"
/>
```

### Touch target size

Een makkelijke manier om de gebruiksvriendelijkheid van je website te verhogen
is door de minimale "target size" te hanteren. Een target kan alles zijn waar
een gebruiker op poogt te klikken, bijvoorbeeld een button of een link. De
minimale size van dit element dient **24 × 24 pixels** te zijn. Gebruikers die
moeite hebben met hun motoriek hebben hier profijt van, maar denk ook aan
touchscreens.

### Kleurgebruik

Zorg ervoor dat kleur niet het enige visuele middel is om informatie over te
brengen, een actie aan te geven, tot een reactie op te roepen of een visueel
element te onderscheiden. Niet iedereen kan alle kleuren onderscheiden of
kleurcontrast even goed opmerken.

## NL Design System

NL Design System is een community die zich bezighoudt met het gezamenlijk
ontwikkelen van components met een hele hoge kwaliteitsstandaard als het gaat om
toegankelijkheid. Het kan dus strategisch slim zijn om NL Design System te gaan
gebruiken in jouw project, omdat je dan toegang hebt tot een hele rits aan
componenten waarvan de toegankelijkheid al gewaarborgd is.

### Acceptatiecriteria per component uit NL Design System

Naast het direct gebruiken van components kan je ook per component opzoeken
welke acceptatiecriteria erop van toepassing zijn. Een voorbeeld hiervan is het
button component:
[Button documentatie NL Design System](https://nldesignsystem.nl/button)

### Alle succescriteria uitgelegd

Je kunt uitleg en interpretatie bij alle succescriteria van de WCAG 2.1 vinden in de documentatie van NL
Design System. De uitleg is aangevuld met voorbeelden zodat het
makkelijker te begrijpen is hoe je precies aan een criterium kunt voldoen. De
uitleg per criterium vind je hier:
[WCAG criteria op NL Design System](https://nldesignsystem.nl/wcag/)

_Let op: de verplichte norm is DigiToegankelijk zelf, de teksten bij NL Design System geven een praktische interpretatie. Het werk van NL Design System is work in progress, nog niet alle
tekstjes zijn compleet. Het goede nieuws is dat jij kunt bijdragen aan het
compleet maken van alle criteria, door bijvoorbeeld een
[issue](https://github.com/nl-design-system/documentatie/issues) aan te dragen._

## Pleio community

Er is een [DigiToegankelijk Pleio community](https://digitoegankelijk.pleio.nl/), waar iedereen van de overheid met elkaar kan sparren over vragen rondom het implementeren van digitale toegankelijkheid, denk aan projectmanagement, interpretatie van de eisen en verklaringen (emailadres van de overheid verplicht).

## Links

- [DigiToegankelijk.nl](https://www.digitoegankelijk.nl/)
- [DigiToegankelijk Pleio community](https://digitoegankelijk.pleio.nl/) (beschikbaar voor mensen met een emailadres van de overheid)

## Tools

### Axe

Met Axe kun je een deel van de WCAG-criteria automatisch testen. Voor Axe is een specifiek artikel met instructies en gelijk te gebruiken
configuratie: [Axe accessibility checker](./run-axe.md).

### Microsoft Accessibility Insights

[Microsoft Accessibility Insights](https://accessibilityinsights.io/) helpt bij automatisch en handmatig testen, met hulpmiddelen die je direct op pagina's kunt toepassen (zoals visuele weergave van waar je focus naartoe gaat) en uitgebreide uitleg van de criteria.

### Playwright

Het end-to-end testing framework Playwright kan gebruikt worden om een deel van je toegankelijkheidsproblemen op te sporen. Een link naar de documentatie vind je hier:
[Playwright](https://playwright.dev/docs/accessibility-testing)

### Wave

Wave is een online tool die websites kan scannen op sommige toegankelijkheidsproblemen:
[Wave](https://wave.webaim.org/)

## Communities

- [DigiToegankelijk](/communities/digitoegankelijk)

## Bronnen

- [Wetgeving - DigiToegankelijk](https://www.digitoegankelijk.nl/wetgeving)
- [Overzicht componenten NL Design System](https://nldesignsystem.nl/componenten/)
- [Forum Standaardisatie: DigiToegankelijk](https://www.forumstandaardisatie.nl/open-standaarden/digitoegankelijk-en-301-549-met-wcag-21)