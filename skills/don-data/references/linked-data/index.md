# Linked Data

Linked Data is een methode om gestructureerde gegevens op het web te publiceren
en te verbinden, zodat deze machine-leesbaar en semantisch betekenisvol zijn.
Het maakt gebruik van standaarden zoals RDF (Resource Description Framework),
URIs (Uniform Resource Identifiers) en HTTP om gegevens te identificeren, te
beschrijven en te koppelen aan andere datasets.

Het doel van Linked Data is om een web van verbonden gegevens te creëren,
vergelijkbaar met hoe hyperlinks webpagina's verbinden. Dit stelt ontwikkelaars
in staat om gegevens uit verschillende bronnen te combineren en te gebruiken in
toepassingen zoals zoekmachines, kennisgrafen en data-integratieplatforms.

## Principes van Linked Data

1. **Gebruik URIs** om dingen te identificeren.
2. **Gebruik HTTP-URIs** zodat gegevens opvraagbaar zijn.
3. **Geef betekenis aan gegevens** door RDF te gebruiken om relaties tussen
   gegevens te beschrijven.
4. **Link naar andere datasets** om een netwerk van verbonden gegevens te
   creëren.

## Voorbeeld van Linked Data

Hier is een voorbeeld in Turtle-syntaxis dat een persoon beschrijft en koppelt
aan andere gegevens:

```turtle
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix dbpedia: <http://dbpedia.org/resource/> .

<http://example.org/person/JanJansen>
    a foaf:Person ;
    foaf:name "Jan Jansen" ;
    foaf:knows <http://example.org/person/PietPietersen> ;
    foaf:homepage <http://janjansen.example.org> ;
    foaf:based_near dbpedia:Amsterdam .
```

### Uitleg

1. URIs: Elk object (zoals `Jan Jansen`) heeft een unieke URI.
1. Relaties: Eigenschappen zoals `foaf:name` en `foaf:knows` beschrijven
   relaties en kenmerken
1. Koppelingen: De `foaf:based_near` eigenschap linkt naar een externe dataset
   (`dbpedia:Amsterdam`).