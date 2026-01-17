# Publiccode.yml

Om inzichtelijk te maken wat de code van een open source project precies doet is
het nodig dat er ergens metadata over het project beschikbaar is. Hiervoor is de
`publiccode.yml` standaard in het leven geroepen. Deze standaard heeft twee
belangrijke doelen:

- Open source projecten vindbaar maken
- Informatie over een open source project centraliseren

## Waar voeg ik de `publiccode.yml` toe?

Je voegt de `publiccode.yml` toe in de root (`./`) van je project.

## Example

```yaml showLineNumbers title="./publiccode.yml"
# This repository adheres to the publiccode.yml standard by including this
# metadata file that makes public software easily discoverable.
# More info at https://github.com/publiccodeyml/publiccode.yml

publiccodeYmlVersion: "0.5"

# Dit veld bevat de korte naam van het project. Kies hier de naam waaronder het
# project bekend is bij de meeste mensen.
name: Developer Overheid NL Website
# De url naar de source code.
url: "https://github.com/developer-overheid-nl/don-site"

# De url naar de productieomgeving van de software.
landingURL: "https://developer.overheid.nl" # optioneel

# Type software zoals te vinden op: https://yml.publiccode.tools/schema.core.html#key-softwaretype
softwareType: standalone/web

# Vul hier in op welke platforms de gebruiker de applicatie uitendelijk gaat
# gebruiken. Dus niet op welk platform de software zelf draait.
platforms:
  - web

# Vul hier een aantal tags in die beschrijven wat jouw sofware doet. De tags
# zijn te vinden op: https://yml.publiccode.tools/categories-list.html#categories-list
categories:
  - collaboration
  - digital-asset-management
  - it-asset-management
  - it-development
  - it-management
  - it-security
  - it-service-management
  - knowledge-management

# De beschrijving van de verschillende statussen zijn te vinden op: https://yml.publiccode.tools/schema.core.html#key-developmentstatus
developmentStatus: beta

description:
  nl:
    longDescription: >
      Developer Overheid NL is de wegwijzer voor developers die voor of bij de
      overheid ontwikkelen. Zij vervult deze rol door het aanbieden van
      standaarden, best practices en tools.

      Een belangrijke feature van het platform is de API catalogus. Deze maakt
      inzichtelijk welke API's er beschikbaar zijn in het publieke landschap.
      Tevens kan je hier per API de informatie vinden die je nodig hebt om met
      de API aan de slag te gaan.
       
      Ook biedt het platform inzicht in welke open source software projecten er
      beschikbaar zijn in het  publieke landschap. Per project krijgt de
      gebruiker inzicht in de vitaliteit van de repository en andere waardevolle
      datapunten.

    # Mand!
    shortDescription:
      Developer Overheid NL is de wegwijzer voor developers die voor of bij de
      overheid ontwikkelen.
    features:
      - Kennisbank
      - API catalogus
      - Open Source catalogus

legal:
  # De licentie volgens de identifier van de SPDX standaard: https://spdx.org/licenses/
  license: EUPL-1.2
  # Wie is de eigenaar van de copyright op de code?
  mainCopyrightOwner: Stichting Geonovum

# Voor welk publiek is deze repository bedoeld?
intendedAudience: # optioneel
  # In welk land?
  countries:
    - NL
  # En in welke sector?
  # De mogelijke tags vind je hier: https://yml.publiccode.tools/scope-list.html#scope-list
  scope:
    - government

localisation:
  # In welke talen is dit project beschikbaar?
  # Invullen volgens IETF BCP 47 standaard: https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry
  availableLanguages:
    - NL
  # Kunnen er meerdere talen geconfigureerd worden?
  localisationReady: false

maintenance:
  # Hoe is het onderhoud georganiseerd?
  # Doet een extern bedrijf het onderhoud? Kies dan: contract
  # Is het onderhoud intern belegd? Kies dan: internal
  type: internal

  # Wie kan ik bereiken bij vragen?
  contacts:
    - name: Dimitri van Hees
      email: d.vanhees@geonovum.nl
      affiliation: Geonovum
    - name: Tom Ootes
      email: tom@ootes.io
      affiliation: Geonovum
      phone: "+31623447230"
```

- [Voorbeelden uit de documentatie van de standaard](https://yml.publiccode.tools/example.html)
- [Publiccode.yml van Open Zaak](https://github.com/open-zaak/open-zaak/blob/main/publiccode.yaml)

## Voordelen

### Git-platform agnostische oplossing

Veel metadata van open source projecten zit opgeslagen in bijvoorbeeld Gitlab of
Github. Op het moment dat je de code wilt migreren is het een hoop werk alle
gegevens opnieuw in te voeren. Publiccode.yml lost dit voor je op, het bestandje
is namelijk onderdeel van je codebase.

### Machine-leesbare metadata

Door het publiccode.yml bestand in te vullen voorzie je je project van
machine-leesbare metadata. Deze meta-data kan ingelezen worden door Open Source
Software Catalogi om jou code zo nog beter vindbaar te maken.

### Vindbaarheid

De publiccode.yml-standaard zorgt op een eenvoudige manier voor vindbaarheid. Op
het momet dat een codebase een `publiccode.yml` bestand bevat in de root van het
project, kan het project worden gemarkeerd als een open source project. Bots
kunnen op die manier makkelijk platforms als Gitlab en Github afstruinen op zoek
naar projecten met een `publiccode.yml` bestand.

## Een open standaard in ontwikkeling

De standaard achter publiccode.yml wordt voortdurend doorontwikkeld. Het team
achter de standaard waardeert het enorm als wij als developers bijdragen door
middel van feedback en suggesties. Je kunt input aanleveren door een
[issue aan te maken](https://github.com/publiccodeyml/publiccode.yml/issues) op
de GitHub-pagina van de standaard.

## Externe links

- [Publiccode.yml editor](https://publiccode-editor.developers.italia.it/?lang=nl)
- [De documentatie van de standaard](https://yml.publiccode.tools/index.html)
- [De documentatie van het `publiccode.yml` schema](https://yml.publiccode.tools/schema.core.html)

## Gerelateerde artikelen

- [Voeg een publiccode.yml toe aan je project met VSCode](../tutorials/voeg-een-publiccode-yml-bestand-toe)

<br />
<br />