# DCAT

DCAT (Data Catalog Vocabulary) is een W3C-standaard die wordt gebruikt om
metadata over datasets te beschrijven en te publiceren. Het is ontworpen om
data-uitwisseling tussen datacatalogi te vergemakkelijken, zodat datasets beter
vindbaar en toegankelijk worden. DCAT is gebaseerd op RDF en maakt gebruik van
Linked Data-principes om datasets en hun metadata te verbinden.

Met DCAT kunnen ontwikkelaars datasets beschrijven met informatie zoals de
titel, beschrijving, publicatiedatum, licentie en distributieformaten. Dit maakt
het eenvoudiger om datasets te integreren in zoekmachines, data-portalen en
andere toepassingen.

## Voorbeeld van DCAT

Hier is een voorbeeld in Turtle-syntaxis dat een dataset beschrijft:

```turtle
@prefix dcat: <http://www.w3.org/ns/dcat#> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .

<http://example.org/dataset/123>
    a dcat:Dataset ;
    dct:title "Voorbeeld Dataset" ;
    dct:description "Een voorbeeld van een dataset beschreven met DCAT." ;
    dct:publisher <http://example.org/organization/456> ;
    dcat:distribution [
        a dcat:Distribution ;
        dct:format "text/csv" ;
        dcat:accessURL <http://example.org/dataset/123/data.csv>
    ] .
```

Uitleg:

1. Dataset:
   - De URI `<http://example.org/dataset/123>` vertegenwoordigt een dataset.
   - Eigenschappen zoals dct:title en dct:description beschrijven de dataset.
1. Distributie:
   - De dcat:distribution eigenschap beschrijft hoe de dataset beschikbaar is,
     inclusief het formaat (text/csv) en de download-URL (dcat:accessURL).
1. Publisher:
   - De dct:publisher eigenschap linkt naar de organisatie die de dataset heeft
     gepubliceerd.

DCAT helpt ontwikkelaars om datasets op een gestandaardiseerde manier te
beschrijven, wat de interoperabiliteit en vindbaarheid van gegevens aanzienlijk
verbetert.