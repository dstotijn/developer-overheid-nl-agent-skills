# Voeg een publiccode.yml toe met VSCode

> ****publiccode.yml editor beschikbaar****
Werk jij liever in een web-editor? Dan kan je gebruik maken van de
[Publiccode.yml Editor](https://publiccode-editor.developers.italia.it/?lang=nl)

In deze tutorial leggen we uit hoe je met behulp van VSCode gemakkelijk een
`publiccode.yml`-bestand kan toevoegen aan je project. Als je hier VSCode
hiervoor gebruikt maak je automatisch gebruik van de
[JSON Schema van publiccode.yml ](https://json.schemastore.org/publiccode.json)
waardoor je inline tips krijgt over welke properties je nog mist, of eventuele
spelfouten.

## Waarom een publiccode.yml toevoegen aan je project?

### Groene "flag"

De belangrijkste reden om een publiccode.yml-bestand aan je project toe te
voegen, is om je project beter vindbaar te maken. Dit bestand fungeert als een
herkenbare flag voor open source softwarecatalogi, waarmee jouw project wordt
geïdentificeerd als een potentieel herbruikbaar stuk code.

### Machine-leesbare metadata

Door het publiccode.yml bestand in te vullen voorzie je je project van
machine-leesbare metadata. Deze meta-data kan ingelezen worden door Open Source
Software Catalogi om jou code zo nog beter vindbaar te maken.

Voor meer informatie, ga naar de
[pagina over de publiccode.yml standaard](../standaarden/publiccode-yml).

## Vereisten

- VSCode

### Stap 1 - Voeg een publiccode.yml bestand toe

Open je project in VSCode en voeg een bestand toe aan de root van je project met
de filename: `publiccode.yml`.

### Stap 2 - Kopieer ons voorbeeld

Kopieer ons voorbeeld op [deze pagina](../standaarden/publiccode-yml). En plak
deze in jouw `publiccode.yml`-bestand.

### Stap 3 - Pas het voorbeeld aan

Pas alle waarden aan met informatie over jouw project. Ben je opzoek naar
informatie over de properties van de standard? Ga dan naar de
[documentatie van de standaard](https://yml.publiccode.tools/schema.core.html).