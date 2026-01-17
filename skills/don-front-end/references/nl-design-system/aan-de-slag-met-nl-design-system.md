# Aan de slag met NL Design System

Wil je snel aan de slag met NL Design System? In deze handleiding laten we je
zien hoe je het lokaal kunt opzetten en hoe je experimenteert met de beschikbare
componenten.

## Benodigdheden

- [NVM](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating)

## Aan de slag

### Stap 1: Installeer de juiste versie van NodeJS met nvm

Gebruik nvm om de juiste versie van node te installeren.

```sh
nvm install 22.13.1
```

```sh
nvm use 22.13.1
```

### Stap 2: Installeer Vite, genereer een React project

```sh
npm install -g vite@6.1.0
```

Maak vervolgens een nieuwe React-app met Vite:

```shs
npm create vite@6.1.0 nl-design-system-playground -- --template react
```

### Stap 3: Installeer dependencies

Ga naar je nieuwe projectmap en installeer de benodigde pakketten:

```sh
cd nl-design-system-playground
npm install
```

Voeg vervolgens de benodigde NL Design System libraries toe:

```sh
npm install --save-dev @rijkshuisstijl-community/components-react
npm install --save-dev @rijkshuisstijl-community/design-tokens
npm install --save-dev @rijkshuisstijl-community/font
```

### Stap 4: Importeer het thema en de componenten

Open `src/App.jsx` en voeg de volgende imports toe:

```js

```

### Stap 5: Voeg je eerste componenten toe

Gebruik een paar standaardcomponenten om te zien hoe het werkt. Voeg deze code
toe aan `src/App.jsx`:

```js

  Button,
  Card,
  Alert,
  Checkbox,
  Blockquote,
} from "@rijkshuisstijl-community/components-react";
```

Vervang de huidige template voor een wrapper met daarin het button component.

```html
return (
<div className="rhc-theme">
  <button>Klik hier!</button>
  <button appearance="primary-action-button">Of hier!</button>

  <br /><br />

  

  <br />

  

  <br />

  

  <br /><br />

  <blockquote attribution="— Aaron Swartz" variation="pink-background">
    “Be curious. Read widely. Try new things. What people call intelligence just
    boils down to curiosity.”
  </blockquote>
</div>
);
```

### Stap 6: Verwijder de boilerplate CSS

Comment twee regels uit om de standaard-styling van Vite uit te schakelen.

In `src/main.jsx`:

```jsx
// import './index.css'
```

In `src/App.jsx`:

```js
// import './App.css'
```

### Stap 7: Start de development server

Draai je project lokaal met:

```sh
npm run dev
```

Je zou nu een werkende interface moeten zien in je browser.

## Bekijk meer componenten

Meer componenten vind je in de
[Storybook omgeving](https://rijkshuisstijl-community.vercel.app) van de
Rijkshuisstijl Community van NL-Design-System.

## Bijdragen

De componenten van Rijkshuisstijl Community zijn open source, als je wilt
meedoen zijn de volgende links handig.

- **_Bug gevonden of code bekijken?_** Bezoek de
  [GitHub repository](https://github.com/nl-design-system/rijkshuisstijl-community).
- **_Benieuwd naar onze voortgang?_** Bekijk de huidige werkzaamheden op het
  [Sprint Board](https://github.com/orgs/nl-design-system/projects/59).
- **_Blijf in contact met de community!_** Word lid van de
  [Code for NL Slack](https://praatmee.codefor.nl/) en join het
  `#nl-design-system` kanaal om samen te werken met de community.