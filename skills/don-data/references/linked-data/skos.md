# SKOS

SKOS (Simple Knowledge Organization System) is een W3C-standaard die wordt
gebruikt om kennisorganisatiesystemen, zoals thesauri, taxonomieën,
classificaties en andere gecontroleerde vocabulaires, te modelleren en te delen.
Het is gebaseerd op RDF en biedt een eenvoudige manier om concepten en hun
relaties te beschrijven, zodat ze machine-leesbaar en interoperabel zijn.

Met SKOS kun je concepten definiëren en organiseren in hiërarchieën of
netwerken. Elk concept kan labels, definities en relaties hebben, zoals bredere
of nauwere termen. Dit maakt SKOS ideaal voor het structureren van kennis in
toepassingen zoals zoekmachines, kennisbanken en semantische webtoepassingen.

## Voorbeeld

Hier is een voorbeeld van een SKOS-vocabulaire:

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .
@prefix ex: <http://example.org/> .

ex:Fruit a skos:Concept ;
    skos:prefLabel "Fruit"@nl ;
    skos:narrower ex:Apple, ex:Banana ;
    skos:definition "Eetbare vruchten van planten."@nl .

ex:Apple a skos:Concept ;
    skos:prefLabel "Appel"@nl ;
    skos:broader ex:Fruit ;
    skos:definition "Een ronde vrucht van de appelboom."@nl .

ex:Banana a skos:Concept ;
    skos:prefLabel "Banaan"@nl ;
    skos:broader ex:Fruit ;
    skos:definition "Een langwerpige, gele vrucht."@nl .
```

### Uitleg

1. Concepten
   - `ex:Fruit`, `ex:Apple`, en `ex:Banana` zijn concepten.
1. Labels
   - `skos:prefLabel` geeft het voorkeurslabel van een concept, zoals "Fruit" of
     "Appel".
1. Relaties:
   - `skos:narrower` geeft aan dat Apple en Banana nauwere termen zijn van
     Fruit.
   - `skos:broader` geeft aan dat Fruit een bredere term is voor Apple en
     Banana.
1. Definities
   - `skos:definition` biedt een beschrijving van elk concept.

Met SKOS kunnen ontwikkelaars gecontroleerde vocabulaires creëren en beheren,
wat helpt bij het verbeteren van de semantiek en consistentie van gegevens in
toepassingen.