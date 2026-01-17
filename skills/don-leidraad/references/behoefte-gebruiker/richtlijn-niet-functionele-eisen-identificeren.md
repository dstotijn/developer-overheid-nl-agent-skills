# Richtlijn: Niet-functionele eisen identificeren

Waar **functionele** eisen beschrijven welke functionaliteit software zou moeten bieden, beschrijven **niet-functionele** eisen op welke wijze de software de functionaliteit aanbiedt. Werkt de software snel of langzaam? Is de applicatie gebruikersvriendelijk of moeilijk te begrijpen? Zijn de opgeslagen gegevens veilig? Is de software robuust ook als gekoppelde systemen niet werken? Is de software makkelijk aan te passen aan veranderende functionele eisen?

## Rationale: Waarom niet-functionele eisen identificeren?

Vaak conflicteren niet-functionele eisen met elkaar. Denk aan gebruiksvriendelijkheid en beveiliging. Twee-factor authenticatie maakt het systeem veiliger maar minder gebruiksvriendelijk. Het is dus nuttig te begrijpen welke prioriteit de verschillende niet-functionele eisen hebben.

Niet-functionele eisen vereisen vaak bepaalde architecturele keuzes. Als de software een lage responstijd moet hebben leidt dat mogelijk tot andere keuzes dan als er grote volumes aan gegevens moeten worden verwerkt.

## Doelgroep: Wie zijn er betrokken bij het identificeren van niet-functionele eisen?

In de ideale wereld worden alle belanghebbenden bij de applicatie betrokken bij het identificeren van de niet-functionele eisen. Uiteraard is het vaak niet mogelijk iedereen te betrekken. Zorg dat er vertegenwoordigers zijn uit de verschillende gebruikersgroepen en andere groepen van belanghebbenden.

De volgende doelgroepen helpen niet-functionele eisen identificeren: product owner, gebruikers, architecten, functioneel beheerders, security officer, privacy officer, developers en testers.

## Implementatie: Hoe identificeer je niet-functionele eisen?

### Methoden en technieken

#### Niet-functionele eisen workshop

Breng de belanghebbenden bij elkaar in een workshop. Presenteer de context van de software zodat alle deelnemers over dezelfde achtergrondinformatie beschikken. Behandel welk probleem de software moet oplossen, wat de omgeving is waarin dat gebeurt, welke gebruikersgroepen er zijn, welke bedrijfsprocessen, en wat de tijdslijnen zijn. Presenteer vervolgens de mogelijk relevante niet-functionele eigenschappen, bijvoorbeeld aan de hand van IEC/ISO 25010, en prioriteer deze, bijvoorbeeld met behulp van multi-voting. Werk in een paar groepjes vervolgens de top 5-7 van de niet-functionele eigenschappen uit in concrete eisen. Presenteer deze eisen plenair en rond de workshop af. Na afloop van de workshop review en prioriteer je eisen verder en leg je deze vast.

#### Gebruik IEC/ISO 25010:2023 om de eisen in te delen

Er zijn veel verschillende niet-functionele eigenschappen van software. De ISO 25010 standaard geeft een indeling van de verschillende eigenschappen in een hiërarchische structuur, inclusief definities van de verschillende eigenschappen. Op het hoogste niveau zijn de eigenschappen:

- functional suitability,
- performance efficiency,
- compatability,
- interaction capability,
- reliability,
- security,
- maintainability,
- flexibility en
- safety.

Elk van deze hoofdeigenschappen is dan weer verder onderverdeeld. Maintainability bestaat bijvoorbeeld weer uit modularity, reusability, analysability, modifiability en testability.

Deze indeling kun je gebruiken om te bedenken welke mogelijke niet-functionele eigenschappen relevant zouden kunnen zijn. En je kunt het gebruiken om de niet-functionele eisen te ordenen. De ISO 25010 standaard bevat dus geen concrete eisen aan software, die zul je zelf moeten bedenken.

#### Prioriteer de niet-functionele eigenschappen met multi-voting

Om te voorkomen dat je veel tijd besteed aan het identificeren van niet-functionele eisen voor eigenschappen die relatief onbelangrijk zijn kun je de niet-functionele eigenschappen ordenen. Zorg dat (vertegenwoordigers van) alle belanghebbenden aanwezig zijn in een workshop. Loop met elkaar door de mogelijk relevante niet-functionele eigenschappen, bijvoorbeeld aan de hand van IEC/ISO 25010. Geef vervolgens elke (groep van) belanghebbenden een aantal stemmen dat ze naar eigen inzicht mogen verdelen over de niet-functionele eigenschappen. Tel de stemmen op per eigenschap om de volgorde te bepalen. Door deze volgorde te gebruiken bij het uitwerken van de eisen besteed je de meeste tijd aan de belangrijkste eigenschappen.

#### Prioriteer de eisen met MoSCoW

Om de eisen te prioriteren kun je denken aan technieken als MoSCoW, waarbij je elke eis een classificatie "Must have", "Should have", "Could have" of "Would have" geeft.

#### Review de eisen tegen de SMART-criteria

Om te controleren of je een eis concreet genoeg hebt geformuleerd kun je de SMART-criteria gebruiken: is de eis Specifiek, Meetbaar, Acceptabel, Realistisch en Tijdgebonden? Bijvoorbeeld: "Het systeem moet beschikbaar zijn met 99,99% uptime per kwartaal." is specifiek, meetbaar, acceptabel (voor de gebruikers), en tijdgebonden, maar wellicht niet realistisch.

### Tools

#### Backlog management

De niet-functionele eisen kun je vastleggen in dezelfde tool als waar je je product backog vastlegt. Denk aan tools als Jira, GitLab of Azure DevOps.

#### Architectuur

Voor het uitwerken van niet-functionele eisen in relatie tot de architectuur kun je tools als Archi (dat de Archimate architectuur modelleertaal ondersteunt) gebruiken.

#### Template

ICTU heeft in haar ["Kwaliteitsaanpak Softwareontwikkeling"](https://ictu.github.io/Kwaliteitsaanpak/) verschillende templates, waaronder een Word-template voor het vastleggen van niet-functionele eisen aan de hand van IEC/ISO 25010:2023.

### Gerelateerde richtlijnen

Nog geen.

### Succescriteria

Wanneer voldoe je aan deze richtlijn?

- Je identificeert samen met belanghebbenden de niet-functionele eisen aan de software en legt deze vast.
- Je gebruikt de niet-functionele eisen als input voor architecturele keuzes, product backlog en testaanpak.

Wanneer ben je echt goed bezig?

- Je bent in staat niet-functionele eisen via tussenproducten te traceren naar geautomatiseerde testresultaten, waarmee je geautomatiseerd kan aantonen dat de eisen zijn gerealiseerd.

## Wanneer is deze richtlijn van toepassing?

Bijna altijd. Er zijn maar weinig uitzonderingen. Een uitzondering zou het ontwikkelen van een prototype kunnen zijn, waarbij de investering in het identificeren van niet-functionele eisen zich niet terugverdient.

## Bronnen

### Wetten

Geen bekend.

### Beleid

Geen bekend.

### Standaarden

- [ISO/IEC 25010:2023](https://www.iso.org/standard/78176.html) Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model.

### Communities

Geen bekend.

### Literatuur

Nog geen.

### Bronnen op developer.overheid.nl

Geen bekend.