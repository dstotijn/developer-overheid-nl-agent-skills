# OWL

OWL (Web Ontology Language) is een W3C-standaard die wordt gebruikt om rijke en
complexe kennismodellen (ontologieën) te definiëren en te delen op het
semantische web. Het is gebaseerd op RDF en RDFS, maar biedt extra
expressiviteit om relaties, regels en beperkingen tussen gegevens te
beschrijven. OWL wordt vaak gebruikt in toepassingen zoals kennisgrafen,
semantische zoekmachines en AI-systemen.

## Kenmerken van OWL

1. **Klassen en Individuen**:
   - OWL maakt het mogelijk om klassen (categorieën) en individuen (instanties)
     te definiëren.
2. **Eigenschappen**:
   - Ondersteunt objecteigenschappen (relaties tussen individuen) en
     datatype-eigenschappen (relaties met waarden zoals getallen of strings).
3. **Beperkingen**:
   - OWL kan beperkingen definiëren, zoals kardinaliteit (bijvoorbeeld "een
     persoon heeft precies één geboortedatum") of domeinen en bereiken van
     eigenschappen.
4. **Redenering**:
   - OWL ondersteunt inferentie, waardoor nieuwe kennis kan worden afgeleid op
     basis van bestaande gegevens en regels.

## Voorbeeld van OWL

Hier is een voorbeeld in Turtle-syntaxis dat een eenvoudige ontologie
beschrijft:

```turtle
@prefix owl: <http://www.w3.org/2002/07/owl#> .
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix ex: <http://example.org/> .

ex:Person a owl:Class .
ex:Employee a owl:Class ;
    rdfs:subClassOf ex:Person .

ex:worksFor a owl:ObjectProperty ;
    rdfs:domain ex:Employee ;
    rdfs:range ex:Organization .
```