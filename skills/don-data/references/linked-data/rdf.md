# RDF

RDF (Resource Description Framework) is een standaardmodel voor het uitwisselen
en structureren van gegevens op het web. Het maakt gebruik van een
grafenstructuur om relaties tussen gegevens te beschrijven in de vorm van
subject-predicate-object-triples. Dit maakt het mogelijk om semantische
verbanden te leggen tussen verschillende datasets en informatie op een
machine-leesbare manier te presenteren. RDF wordt vaak gebruikt in combinatie
met andere standaarden zoals RDFa, RDFS en OWL om het semantische web te
ondersteunen.

## RDFa

RDFa (Resource Description Framework in Attributes) is een uitbreiding van HTML,
XHTML en XML waarmee metadata en semantische gegevens direct in webpagina's
kunnen worden ingebed. Het stelt ontwikkelaars in staat om gestructureerde
gegevens toe te voegen aan webinhoud zonder de visuele presentatie te
beïnvloeden. RDFa maakt gebruik van HTML-attributen zoals `about`, `property` en
`content` om RDF-triples te definiëren.

```html
<div vocab="http://schema.org/" typeof="Person">
  <span property="name">Jan Jansen</span> is een
  <span property="jobTitle">Softwareontwikkelaar</span> bij
  <span property="worksFor" typeof="Organization">
    <span property="name">TechBedrijf BV</span> </span
  >. Zijn e-mailadres is
  <a property="email" href="mailto:jan.jansen@example.com"
    >jan.jansen@example.com</a
  >.
</div>
```

| Attribuut    | Omschrijving                                                                                                                                                                                                                                              |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **vocab**    | Het attribuut vocab specificeert de vocabulaire (`<http://schema.org/>`) die wordt gebruikt.                                                                                                                                                              |
| **typeof**   | Het attribuut typeof geeft aan dat het element een instantie is van een bepaalde klasse, zoals `Person`.                                                                                                                                                  |
| **property** | Het attribuut `property` wordt gebruikt om eigenschappen van het onderwerp te definiëren, zoals `name`, `jobTitle`, en `worksFor`. Binnen `worksFor` wordt een andere instantie (`Organization`) gedefinieerd met zijn eigen eigenschappen, zoals `name`. |

Met RDFa kun je dus semantische gegevens toevoegen aan HTML-documenten, waardoor
zoekmachines en andere systemen de inhoud beter kunnen begrijpen.

## RDFS

RDFS (RDF Schema) is een uitbreiding van RDF die een vocabulaire en structuur
toevoegt aan het basismodel van RDF. Het biedt mechanismen om klassen,
eigenschappen en hiërarchieën te definiëren, waardoor complexere
gegevensmodellen mogelijk worden. Met RDFS kun je bijvoorbeeld aangeven dat een
bepaalde eigenschap alleen van toepassing is op een specifieke klasse of dat een
klasse een subklasse is van een andere. Dit maakt het mogelijk om semantische
relaties en regels binnen datasets te specificeren, wat essentieel is voor het
bouwen van rijke en betekenisvolle gegevensmodellen.

## Verschil tussen RDF, RDFa en RDFS

- **RDF** is het basismodel voor het beschrijven van gegevens in de vorm van
  subject-predicate-object-triples. Het biedt een generiek framework voor het
  structureren van gegevens.
- **RDFa** is een implementatie van RDF die specifiek is ontworpen voor het
  annoteren van webpagina's. Het voegt semantische betekenis toe aan
  HTML-elementen.
- **RDFS** (RDF Schema) breidt RDF uit door vocabulaire en structuur toe te
  voegen, zoals klassen en eigenschappen, waarmee complexere gegevensmodellen
  kunnen worden gedefinieerd.

Kort gezegd: RDF is het fundament, RDFa is een toepassing ervan in
webdocumenten, en RDFS biedt een uitbreidbare vocabulaire voor RDF.