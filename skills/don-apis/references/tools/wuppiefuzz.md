"@rijkshuisstijl-community/components-react"; import Author from
'@theme/Blog/Components/Author';

# WuppieFuzz

## Coverage-Guided REST API Fuzzing voor Veiligere Digitale Overheidsdiensten

In een tijd waarin digitale overheidsdiensten steeds vaker via
[REST API’s](/blog/2025/07/10/openapi-31-in-zicht#van-rest-naar-http)
communiceren, is het waarborgen van de veiligheid van deze interfaces cruciaal.
**[WuppieFuzz](https://github.com/TNO-S3/WuppieFuzz)**, ontwikkeld door
[TNO](https://tno.nl), is een open-source, coverage-guided fuzzer die specifiek
is ontworpen voor het testen van REST API’s. Het doel: kwetsbaarheden en bugs
opsporen voordat ze misbruikt kunnen worden, met een sterke focus op
gebruiksvriendelijkheid, modulariteit en inzichtelijkheid.

![Logo of WuppieFuzz](./img/WuppieFuzz.svg)

## Hoe werkt WuppieFuzz?

[![How to use WuppieFuzz? - YouTube](./img/demo_video.png)](https://www.youtube.com/watch?v=-oR4d9aXrqo)

WuppieFuzz is gebouwd bovenop het
[LibAFL-framework](https://github.com/AFLplusplus/LibAFL) en ondersteunt drie
testmodi:

- **Black box**: zonder kennis van de interne werking.
- **Grey box**: met beperkte kennis en observatie van gedrag.
- **White box**: met volledige toegang tot de broncode en interne structuur.

Op basis van een [OpenAPI-specificatie](../openapi-specification) genereert
WuppieFuzz automatisch zinvolle sequenties van HTTP-requests. Deze sequenties
worden vervolgens gemuteerd om diepere logica en edge cases in de API te
bereiken. De tool meet test coverage via response codes en/of via instrumentatie
van de backend (bijv. met `JaCoCo` voor Java of `coverage.py` voor Python).

## Waarom is WuppieFuzz Relevant voor de Overheid?

REST API’s vormen de ruggengraat van veel overheidsapplicaties. Denk aan
systemen voor burgerzaken, vergunningverlening of gegevensuitwisseling tussen
departementen. WuppieFuzz helpt ontwikkelaars en testers om:

- Automatisch kwetsbaarheden te detecteren.
- Complexe sequentiële bugs op te sporen.
- Afwijkingen van de API-specificatie te identificeren.

## Gebruiksgemak en Extensibiliteit

WuppieFuzz is ontworpen met de eindgebruiker in gedachten:

- Out-of-the-box configuratie.
- Modulaire opzet voor uitbreiding naar andere programmeertalen.
- Open source beschikbaarheid en vrij te gebruiken middels een Apache
  2.0-licentie.

## Conclusie

WuppieFuzz biedt een krachtige, toegankelijke en uitbreidbare oplossing voor het
testen van REST API's binnen overheidscontexten. Door gebruik te maken van
coverage-guided fuzzing en slimme mutatiestrategieën, helpt het ontwikkelaars om
robuuste, betrouwbare en veilige digitale diensten te bouwen.

---