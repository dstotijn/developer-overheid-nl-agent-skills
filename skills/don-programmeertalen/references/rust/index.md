# Rust

Rust heeft de afgelopen jaren aan populariteit gewonnen door zijn performance en
zijn moderne tooling en ecosysteem.

Rust is een fijne taal omdat het helpt bugvrije software op te leveren. Ook is
het een expressieve taal met een uitgebreid typesystem waardoor je er complexe
concepten goed in kan vatten. De tooling om Rust heen is erg hulpvaardig en de
linter Clippy geeft handige tips voor het correct gebruik van Rust. Wel is het
een taal met een jong ecosysteem waardoor je soms specifieke functionaliteiten
binnen libraries mist.

## Voordelen

### 1. Snel en efficiënt

Omdat Rust een low-level taal is die gecompiled wordt, is het een zeer snelle en
efficiënte taal. Hierdoor is het bijzonder geschikt voor bijvoorbeeld:

- API's/microservices met veel requests in korte tijd
- Embedded systems waarbij de resources beperkt zijn
- Stukken software die op veel plekken snel moeten functioneren zoals drivers

### 2. Borrow checker voorkomt bugs

Een van Rust's meest onderscheidende kenmerken is de borrow checker. Deze dwingt
tijdens het compileren strenge regels af rondom geheugengebruik en ownership.
Hoewel dit een leercurve met zich meebrengt, zorgt het ervoor dat veel bugs die
in andere talen pas bij runtime optreden, al tijdens het compileren worden
gevonden. Naarmate projecten groter en complexer worden, wordt deze robuustheid
steeds waardevoller. De strikte compile-time checks leiden wel tot langere
compile times, wat zich kan uiten in langere CI-tijden.

### 3. Uitstekende WebAssembly (WASM) support

Rust wordt beschouwd als de beste taal voor het compileren naar WebAssembly
(WASM), met robuuste tooling. Dit maakt het mogelijk om Rust code te gebruiken
in webomgevingen met near-native performance.

### 4. Fijne developer experience

Doordat er flink is geïnvesteerd in een aantal producten naast de
programmeertaal zelf is de developer experience goed. Ook heeft het Rust team er
voor gekozen om het ontwikkelen van deze tools zelf te doen, en het niet over te
laten aan third-party projecten. Daardoor werken ze extra goed en is er geen
onnodige concurrentie. Het volgt de filosofie van "batteries included".

### 5. Secure

Memory safety zonder garbage collection: Rust voorkomt de meest voorkomende
beveiligingsproblemen door zijn unieke "ownership" systeem. Dit betekent dat
veel fouten die in C/C++ tot kwetsbaarheden leiden (zoals buffer overflows,
use-after-free, data races) al tijdens het compileren worden gevangen, niet pas
tijdens runtime.

Memory safety bugs zijn verantwoordelijk voor ongeveer 70% van alle **ernstige
beveiligingslekken** in software. In de praktijk kan dit leiden tot:

**Malicious code execution**: een aanvaller kan misbruik maken van memory bugs
om hun eigen kwaadaardige code op het systeem uit te voeren. Dit is vaak het
eindoel van exploits - volledige controle over het systeem krijgen.

**Data lekken**: door buiten de grenzen van een buffer te lezen kunnen
aanvallers gevoelige informatie stelen die eigenlijk niet toegankelijk zou
moeten zijn - denk aan wachtwoorden, cryptografische sleutels, of persoonlijke
gegevens die toevallig naast elkaar in het geheugen staan.

**Privilege escalation**: een aanvaller met beperkte rechten kan een memory bug
misbruiken om beheerdersrechten te krijgen.

## Nadelen

### 1. Jong ecosysteem, minder libraries

Omdat Rust een jonge taal is zijn er minder packages voor handen dan
bijvoorbeeld in Python of in Java. Een voorbeeld hiervan noemt ook de Kiesraad
in het [interview dat we met haar hielden][kiesraad-interview]. In het interview
komt naar voren dat de libraries die er zijn, niet altijd even volwassen of
uitgebouwd zijn. Ze noemen bijvoorbeeld de library `quick-xml` voor het
verwerken van XML en zeggen hierover:

"Je merkt dat de meest gebruikte XML library voor Rust (quick-xml) wel voldoet,
maar minder volwassen en uitgebreid is dan wat je in andere talen vindt.
Bijvoorbeeld in Java of .NET, die zijn ontwikkeld toen XML in opkomst was."

[kiesraad-interview]:
  https://developer.overheid.nl/blog/2025/03/26/interview-kiesraad-rust#een-jonger-ecosysteem-betekent-minder-uitgebreide-libraries-voor-legacy-standaarden-bijvoorbeeld-xml

### 2. Steile learning curve

Omdat Rust een strikte taal is heeft het een relatief steile learning curve. Ook
bevat de taal een aantal fundamentele concepten die anders zijn dan in de andere
mainstream programmeertalen. Daarnaast is **async** programming in Rust
complexer dan in veel andere talen, vooral wanneer je async combineert met
traits.

### 3. Lange compile time

Door de zeer robuuste compile-time type checking is de Rust-compiler notoir
langzaam. Dat betekent langere CI tijden en langere dev iteraties. Een van de
grootste nadelen van Rust.

## Tools

### Cargo

[Cargo] is Rust's officiële build system en package manager, de centrale tool
die bijna alles rondom Rust development voor je afhandelt.

### Clippy

[Clippy] is de linter van Rust en geeft je suggesties hoe je je code netter kan
schrijven. Het geeft je dus ook advies hoe je je functie zou kunnen refactoren.

### Cargo test

[Cargo test] is het test-framework dat standaard mee komt met Rust.

[Cargo]: https://doc.rust-lang.org/cargo/
[Clippy]: https://doc.rust-lang.org/clippy/
[Cargo test]: https://doc.rust-lang.org/rustc/tests/index.html

## Toekomstbestendigheid

Rust heeft een actieve open-source gemeenschap en wordt ondersteund door de Rust
Foundation, met steun van grote tech bedrijven. De taal evolueert gecontroleerd
via een transparant RFC-proces, wat langetermijnstabiliteit garandeert.

## Use cases voor de overheid

Rust is bijzonder geschikt voor:

- **Web services en APIs**: veilige en snelle backend systemen
- **CLI tools en automation**: betrouwbare command-line applicaties
- **IoT en embedded systems**: veilige software voor smart city toepassingen
- **Network services**: firewalls, proxies en andere netwerkapplicaties
- **Data processing**: efficiënte verwerking van grote datasets

## Aan de slag

De [Getting started page op rust-lang.org][getting-started] biedt een mooi
overzicht van de belangrijkste stappen om Rust te installeren en gaan gebruiken,
inclusief links naar uitgebreidere documentatie.

[getting-started]: https://rust-lang.org/learn/get-started/