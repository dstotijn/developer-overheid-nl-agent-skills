# Foutmeldingen met Problem Details

:::info[TL;DR]

Problem JSON (`application/problem+json`) is een krachtige standaard voor het
verbeteren van de foutafhandeling in API's en het bieden van een betere ervaring
voor zowel developers als eindgebruikers.

- Consistentie: Alle foutmeldingen volgen hetzelfde formaat.
- Uitbreidbaarheid: Je kunt eenvoudig extra velden toevoegen voor specifieke
  use-cases.
- Betere debugging: Clients krijgen meer context over fouten, wat helpt bij het
  oplossen van problemen.

:::

Problem JSON is een internetstandaard
([RFC 7807](https://datatracker.ietf.org/doc/html/rfc7807)) die een
gestructureerd formaat biedt voor het beschrijven van fouten in API's. Het doel
is om een consistente manier te bieden om foutmeldingen te communiceren, zodat
clients deze eenvoudig kunnen begrijpen en verwerken. Dit formaat wordt vaak
gebruikt in RESTful API's om foutdetails te verstrekken in een machine-leesbare
en uitbreidbare manier.

Bij het ontwikkelen van API's is het belangrijk om duidelijke en consistente
foutmeldingen te geven. Traditionele foutmeldingen, zoals HTTP-statuscodes en
eenvoudige tekstberichten, bieden vaak onvoldoende context. Met Problem JSON kun
je extra details toevoegen, zoals een fouttype, een beschrijving en optionele
aanvullende informatie.

## Content-Type

Als je Problem JSON teruggeeft, dan moet dit vergezeld zijn van een
`Content-Type` header met waarde `application/problem+json`.

## Structuur

Een `application/problem+json`-object bevat standaard de volgende velden:

- **`type`** (URI, optioneel): Een URI die het type probleem identificeert. Dit
  kan een link zijn naar documentatie over de fout.
- **`title`** (string, verplicht): Een korte, leesbare titel die het probleem
  beschrijft.
- **`status`** (integer, optioneel): De HTTP-statuscode die bij het probleem
  hoort.
- **`detail`** (string, optioneel): Een gedetailleerde beschrijving van het
  probleem.
- **`instance`** (URI, optioneel): Een URI die verwijst naar de specifieke
  instantie van het probleem.

## Voorbeeld

Hier is een voorbeeld van een foutmelding in het
`application/problem+json`-formaat:

```json
{
  "type": "https://example.com/probs/out-of-credit",
  "title": "Bad Request",
  "status": 400,
  "detail": "De gegeven input is niet valid",
  "instance": "/account/12345/transactions/67890",
  "invalidParams": [
    {
      "name": "bouwjaar",
      "reason": "Kan niet in de toekomst liggen"
    },
    {
      "name": "gemeenteCode",
      "reason": "Dit is een verplicht veld"
    }
  ]
}
```

In dit voorbeeld gaat het om een `400 Bad Request` response. Deze wordt
teruggegeven als de API de request niet kan verwerken, bijvoorbeeld doordat de
verkeerde waarden zijn meegegeven. Met de custom uitbreiding `invalidParams`
geven we hier aan welke waarden niet kloppen. Zo blijkt uit deze array dat er 2
waarden niet kloppen, die van `bouwjaar` en `gemeenteCode`. Een client kan aan
de hand van deze response de eindgebruiker informeren over de foutieve input,
bijvoorbeeld door de `reason` tekst te tonen bij de corresponderende
formuliervelden.

## Implementatie

Bij het bouwen van een API kun je `application/problem+json` gebruiken door
foutmeldingen in dit formaat te retourneren. Hier is een voorbeeld in een
Node.js/Express-app:

```javascript
app.use((err, req, res, next) => {
  res.status(err.status || 500).json({
    type: "https://example.com/probs/" + (err.type || "unknown-error"),
    title: err.title || "Internal Server Error",
    status: err.status || 500,
    detail: err.message,
    instance: req.originalUrl,
  });
});
```