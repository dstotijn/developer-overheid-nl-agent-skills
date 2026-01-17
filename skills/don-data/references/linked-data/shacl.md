# SHACL

SHACL (Shapes Constraint Language) is een W3C-standaard die wordt gebruikt om
validatieregels en beperkingen te definiëren voor RDF-gegevens. Het stelt
ontwikkelaars in staat om te specificeren hoe RDF-data gestructureerd moet zijn
en welke waarden of relaties toegestaan zijn. SHACL wordt vaak gebruikt om de
kwaliteit en consistentie van RDF-datasets te waarborgen.

Met SHACL kun je zogenaamde "shapes" definiëren, die beschrijven hoe een
RDF-graf moet worden gevalideerd. Een shape kan bijvoorbeeld specificeren dat
een bepaald type entiteit een verplichte eigenschap moet hebben, dat een
eigenschap een specifieke datatype moet hebben, of dat een waarde binnen een
bepaald bereik moet liggen.

## Voorbeeld

Hier is een voorbeeld van een SHACL-shape die valideert dat een `Person` een
verplichte `name`-eigenschap heeft en dat de waarde van `age` een geheel getal
moet zijn:

```turtle
@prefix sh: <http://www.w3.org/ns/shacl#> .
@prefix ex: <http://example.org/> .

ex:PersonShape
    a sh:NodeShape ;
    sh:targetClass ex:Person ;
    sh:property [
        sh:path ex:name ;
        sh:datatype xsd:string ;
        sh:minCount 1 ;
    ] ;
    sh:property [
        sh:path ex:age ;
        sh:datatype xsd:integer ;
        sh:minInclusive 0 ;
    ] .
```

| Attribuut          | Omschrijving                                                                                                                                                                                                 |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **sh:NodeShape**   | Definieert een shape die wordt toegepast op RDF-resources.                                                                                                                                                   |
| **sh:targetClass** | Geeft aan dat de shape van toepassing is op alle instanties van de klasse `ex:Person`.                                                                                                                       |
| **sh:property**    | Beschrijft beperkingen voor specifieke eigenschappen: `ex:name` moet een string zijn en is verplicht (`sh:minCount 1`). `ex:age` moet een geheel getal zijn en mag niet negatief zijn (`sh:minInclusive 0`). |