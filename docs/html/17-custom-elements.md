# ZE-WebLab – HTML-Referenz: Custom Elements

## Arbeitsstand / Quellenstand

- Rechercheebene: 2 – übergreifende HTML-Konzepte und Feature-Familien
- Feature-Familie: Custom Elements
- Feature-Typ: Custom Elements Feature / API / DOM- und Processing-Konzept
- Zieldatei: `docs/html/17-custom-elements.md`
- Normative Primärquelle: WHATWG HTML Living Standard
- Maßgeblicher WHATWG-Bereich: §4.13 Custom elements
- WHATWG-Stand der Recherche: 11. August 2026
- Projektquelle: öffentliches ZE-WebLab-Repository
- Browser-Kompatibilität: nicht Bestandteil der normativen Statusbewertung
- V1-Status: projektspezifisch; nicht mit WHATWG-Status gleichzusetzen
- Prüfstatus: vollständig recherchiert für den abgegrenzten Custom-Elements-Bereich

### Quellenabgrenzung

Die WHATWG HTML Living Standard ist die normative Primärquelle für:

- Definitionen
- Konformitätsanforderungen
- Custom-Element-Namen
- Custom-Element-Definitionen
- Registrierung
- DOM- und IDL-Beziehungen
- Upgrades
- Lifecycle-/Reaction-Verarbeitung
- Form-Integration
- Accessibility-Integration
- Custom States
- Element Internals
- Verarbeitung durch User Agents
- normative Algorithmen

Das ZE-WebLab-Repository ist die maßgebliche Quelle für die Feststellung, welche Aspekte im bestehenden Projekt bereits dokumentiert sind.

Die erste Rechercheebene enthält bereits elementbezogene Bezüge zu Attributen und DOM-Konzepten. Diese stellen jedoch keine vollständige Dokumentation der Custom-Elements-Feature-Familie dar.

Insbesondere gilt:

- `is` ist bereits Bestandteil der Global-Attributes-Dokumentation.
- Die bloße Erwähnung von `is` dokumentiert nicht die gesamte Customized-Built-In-Systematik.
- Ein Custom Element ist kein zusätzliches Element aus dem endlichen nativen HTML-Elementinventar.
- Autonomous Custom Elements bilden keine endliche WHATWG-Elementliste.
- `CustomElementRegistry` ist ein DOM-/API-Konzept und kein HTML-Element.
- `ElementInternals` ist ein DOM-/API-Konzept und kein HTML-Element.
- Custom Element Reactions sind ein Processing Model und kein HTML-Element.
- Lifecycle Callbacks sind Bestandteile der Custom-Element-Verarbeitung und keine HTML-Elemente.
- Browser-Support ist kein WHATWG-Status.
- Externe Accessibility-Spezifikationen werden nicht als WHATWG-Definitionen ausgegeben.

---

## Einordnung

Custom Elements stellen die standardisierte Erweiterungsmechanik für HTML-Elemente dar.

Die WHATWG definiert Custom Elements als Elemente, deren Konstruktor und Prototyp vom Autor bereitgestellt werden, anstatt vom User Agent. Der vom Autor bereitgestellte Konstruktor wird als Custom Element Constructor bezeichnet.

Custom Elements ermöglichen damit eine Erweiterung des HTML-Vokabulars über eine definierte DOM-/JavaScript-Schnittstelle.

Die Feature-Familie umfasst insbesondere:

1. autonome Custom Elements
2. customized built-in elements
3. Custom Element Names
4. Custom Element Definitions
5. `CustomElementRegistry`
6. Definition und Registrierung
7. Upgrades
8. Custom Element Constructors
9. Lifecycle Callbacks
10. Custom Element Reactions
11. `[CEReactions]`
12. form-associated custom elements
13. `ElementInternals`
14. Accessibility-Semantik über `ElementInternals`
15. Custom States und `:state()`
16. Scoped Custom Element Registries
17. Parsing-/DOM-Integration
18. Beziehungen zu HTML Element Constructors
19. Beziehungen zu Shadow DOM
20. Beziehungen zu Formularen und Constraint Validation

Custom Elements sind damit eine eigenständige zweite-Ebenen-Feature-Familie.

---

## WHATWG-Struktur

Der maßgebliche WHATWG-Bereich ist:

- §4.13 Custom elements

### Unterabschnitte

#### §4.13.1 Introduction

- §4.13.1.1 Creating an autonomous custom element
- §4.13.1.2 Creating a form-associated custom element
- §4.13.1.3 Creating a custom element with default accessible roles, states, and properties
- §4.13.1.4 Creating a customized built-in element
- §4.13.1.5 Drawbacks of autonomous custom elements
- §4.13.1.6 Upgrading elements after their creation
- §4.13.1.7 Scoped custom element registries
- §4.13.1.8 Exposing custom element states

#### §4.13.2 Requirements for custom element constructors and reactions

- §4.13.2.1 Preserving custom element state when moved

#### §4.13.3 Core concepts

#### §4.13.4 The `CustomElementRegistry` interface

#### §4.13.5 Upgrades

#### §4.13.6 Custom element reactions

#### §4.13.7 Element internals

- §4.13.7.1 The `ElementInternals` interface
- §4.13.7.2 Shadow root access
- §4.13.7.3 Form-associated custom elements
- §4.13.7.4 Accessibility semantics
- §4.13.7.5 Custom state pseudo-class

Diese gesamte Unterstruktur wurde für diese Datei berücksichtigt.

---

## Inventar

### Feature-Inventar

| ID | Feature | Feature-Typ | WHATWG-Bereich | Abdeckung erste Ebene | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| CE-001 | Custom Elements allgemein | Custom Elements Feature | §4.13 | teilweise elementbezogen | vollständig relevant |
| CE-002 | Autonomous Custom Elements | Custom Elements Feature | §4.13.1.1, §4.13.3 | nicht als Familie | vollständig relevant |
| CE-003 | Customized Built-In Elements | Custom Elements Feature | §4.13.1.4, §4.13.3 | `is` elementbezogen | vollständig relevant |
| CE-004 | Valid Custom Element Names | Normative Definition | §4.13.3 | nicht als System | vollständig relevant |
| CE-005 | Custom Element Definition | Normatives Konzept | §4.13.3, §4.13.4 | nicht vollständig | vollständig relevant |
| CE-006 | `CustomElementRegistry` | API / DOM Interface | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-007 | `customElements` | API / DOM-Bezug | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-008 | `define()` | API / Processing Model | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-009 | `get()` | API | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-010 | `getName()` | API | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-011 | `whenDefined()` | API | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-012 | `upgrade()` | API / Processing Model | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-013 | `initialize()` | API / Processing Model | §4.13.4 | nicht vollständig | vollständig relevant |
| CE-014 | Scoped Custom Element Registries | API / DOM-Konzept | §4.13.1.7, §4.13.4 | nicht vollständig | vollständig relevant |
| CE-015 | Custom Element Constructor | DOM-/JS-Konzept | §4.13.1, §4.13.2 | nicht vollständig | vollständig relevant |
| CE-016 | Constructor Requirements | Konformitätsanforderung | §4.13.2 | nicht vollständig | vollständig relevant |
| CE-017 | Lifecycle Callbacks | Processing Model | §4.13.3, §4.13.6 | nicht vollständig | vollständig relevant |
| CE-018 | `connectedCallback` | Lifecycle Feature | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-019 | `disconnectedCallback` | Lifecycle Feature | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-020 | `connectedMoveCallback` | Lifecycle Feature | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-021 | `adoptedCallback` | Lifecycle Feature | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-022 | `attributeChangedCallback` | Lifecycle Feature | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-023 | Form-associated callbacks | Lifecycle Feature | §4.13.3, §4.13.7.3 | formbezogen teilweise | vollständig relevant |
| CE-024 | `formAssociatedCallback` | Lifecycle Feature | §4.13.3 | nicht vollständig | vollständig relevant |
| CE-025 | `formDisabledCallback` | Lifecycle Feature | §4.13.3 | nicht vollständig | vollständig relevant |
| CE-026 | `formResetCallback` | Lifecycle Feature | §4.13.3 | nicht vollständig | vollständig relevant |
| CE-027 | `formStateRestoreCallback` | Lifecycle Feature | §4.13.3, §4.13.7.3 | nicht vollständig | vollständig relevant |
| CE-028 | Custom Element Reactions | Processing Model | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-029 | Reaction Queue | Processing Model | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-030 | `[CEReactions]` | Web IDL / Processing Model | §4.13.6 | nicht vollständig | vollständig relevant |
| CE-031 | Upgrading | Processing Model | §4.13.5 | nicht vollständig | vollständig relevant |
| CE-032 | `ElementInternals` | DOM Interface / API | §4.13.7.1 | nicht vollständig | vollständig relevant |
| CE-033 | `attachInternals()` | API | §4.13.7 | nicht vollständig | vollständig relevant |
| CE-034 | Shadow Root Access | API / DOM | §4.13.7.2 | nicht vollständig | relevant |
| CE-035 | Form Association | HTML-/DOM-Konzept | §4.13.7.3 | teilweise in Forms | vollständig relevant |
| CE-036 | Form Submission Value | Processing Model | §4.13.7.3 | teilweise in Forms | vollständig relevant |
| CE-037 | Form State | Processing Model | §4.13.7.3 | teilweise in Forms | vollständig relevant |
| CE-038 | Constraint Validation | HTML-/DOM-Konzept | §4.13.7.3 | teilweise in Forms | relevant |
| CE-039 | Accessibility Semantics | Accessibility Integration | §4.13.7.4 | teilweise in Elementdateien | vollständig relevant |
| CE-040 | `ElementInternals` ARIA | API / Accessibility | §4.13.7.4 | nicht vollständig | vollständig relevant |
| CE-041 | Custom States | API / DOM-/CSS-Integration | §4.13.7.5 | nicht vollständig | vollständig relevant |
| CE-042 | `CustomStateSet` | DOM Interface | §4.13.7.5 | nicht vollständig | vollständig relevant |
| CE-043 | `:state()` | CSS-Integrationsfeature | §4.13.1.8, §4.13.7.5 | nicht vollständig | relevant |
| CE-044 | `is` | Global Attribute / Integration | §4.13.3 und Global Attributes | bereits in 13 | Querverweis, nicht duplizieren |
| CE-045 | Custom Element Registry Lookup | Processing Model | §4.13.3 | nicht vollständig | relevant |
| CE-046 | Construction Stack | Processing Model | §4.13.3 | nicht vollständig | relevant |
| CE-047 | Custom Element State | DOM-Konzept | §4.13.3, §4.13.5 | nicht vollständig | relevant |
| CE-048 | Parsing-Integration | Processing / Parsing | §4.13.1, §4.13.5 | nicht vollständig | relevant |
| CE-049 | `createElement()`-Integration | DOM/API | §4.13.1, §4.13.4 | nicht vollständig | relevant |
| CE-050 | `createElementNS()`-Bezug | DOM/API | §4.13.2 | nicht vollständig | relevant |

---

## Begriffsdefinitionen

### Custom Element

Ein Custom Element ist ein Element, das im Sinne des DOM-Konzepts `custom` ist.

Informell bedeutet dies, dass Konstruktor und Prototyp des Elements durch den Autor bereitgestellt werden.

Der autorenseitige Konstruktor ist der Custom Element Constructor.

### Autonomous Custom Element

Ein Autonomous Custom Element wird ohne `extends`-Option definiert.

Sein definierter Name entspricht seinem Local Name.

Beispiel:

`my-element`

Ein Autonomous Custom Element wird typischerweise als eigenes Tag verwendet:

`<my-element></my-element>`

Es übernimmt nicht automatisch die Semantik eines ähnlich benannten nativen HTML-Elements.

### Customized Built-In Element

Ein Customized Built-In Element wird mit einer `extends`-Option definiert.

Der Local Name bleibt der Local Name des erweiterten nativen HTML-Elements.

Der definierte Custom-Element-Name wird über den `is`-Mechanismus verwendet.

Beispiel:

`customElements.define("plastic-button", PlasticButton, { extends: "button" })`

Die entsprechende HTML-Syntax ist:

`<button is="plastic-button"></button>`

Das Element bleibt dabei ein `button` mit dessen nativer Semantik und Verhalten, erweitert um die Custom-Element-Definition.

### Custom Element Name

Ein Custom Element Name ist ein Name, der die normativen Anforderungen für Custom Elements erfüllt.

Wesentliche Anforderungen sind:

- gültiger Element Local Name
- erstes Code Point ist ein ASCII-Kleinbuchstabe
- keine ASCII-Großbuchstaben
- mindestens ein U+002D (`-`)
- nicht einer der reservierten hyphenhaltigen Namen aus den relevanten SVG-/MathML-Vokabularen

Reservierte Namen:

- `annotation-xml`
- `color-profile`
- `font-face`
- `font-face-src`
- `font-face-uri`
- `font-face-format`
- `font-face-name`
- `missing-glyph`

Der Bindestrich dient insbesondere der Abgrenzung und Forward Compatibility.

### Custom Element Definition

Eine Custom Element Definition beschreibt die normative Zuordnung eines Custom Elements zu seinem Konstruktor und seinen Verarbeitungsinformationen.

Sie umfasst insbesondere:

- Name
- Local Name
- Constructor
- beobachtete Attribute
- Lifecycle Callback Collection
- Construction Stack
- Form-associated Boolean
- Disable-Internals-Boolean
- Disable-Shadow-Boolean

### Custom Element Registry

Eine `CustomElementRegistry` verwaltet Custom Element Definitions.

Sie kann:

- Definitionen registrieren
- Definitionen nach Namen suchen
- Konstruktoren nach Namen zurückgeben
- Namen nach Konstruktoren suchen
- auf Definitionen warten
- Elemente gezielt upgraden
- einen Registry-bezogenen Initialisierungsvorgang ausführen

### Custom Element Reactions

Custom Element Reactions sind die normative Verarbeitungsschicht, über die der User Agent autorenseitige Lifecycle-Reaktionen ausführt.

Sie werden insbesondere bei folgenden Vorgängen relevant:

- Upgrade
- Verbindung mit dem Dokument
- Entfernung aus dem Dokument
- Bewegung
- Adoption in ein anderes Dokument
- Attributänderungen
- Form-Zustandsänderungen

### Element Internals

`ElementInternals` stellt einem Custom Element interne Plattformfunktionen zur Verfügung, die nicht als gewöhnliche öffentliche Elementattribute modelliert werden.

Dazu gehören insbesondere:

- Form-Integration
- Constraint Validation
- Zugriff auf bestimmte Shadow-Root-Informationen
- Accessibility-Semantik
- Custom States

### Form-associated Custom Element

Ein Autonomous Custom Element ist ein form-associated custom element, wenn die zugehörige Custom Element Definition das `form-associated`-Feld auf `true` setzt.

Damit kann ein Custom Element an Formularverarbeitung und Constraint Validation teilnehmen.

### Custom State

Ein Custom State ist ein vom Custom Element bereitgestellter Zustand, der über `ElementInternals.states` verwaltet und über die `:state()`-Pseudo-Klasse für CSS verfügbar gemacht werden kann.

---

## Normative Regeln

### Allgemeine Typen

WHATWG unterscheidet:

- Autonomous Custom Elements
- Customized Built-In Elements

Diese beiden Typen dürfen nicht miteinander gleichgesetzt werden.

### Autonomous Custom Elements

Für Autonomous Custom Elements gilt als Elementdefinition:

- Flow Content
- Phrasing Content
- Palpable Content
- bei form-associated Custom Elements zusätzlich die entsprechenden Form-Kategorien

Das Context-Modell ist auf Stellen ausgerichtet, an denen Phrasing Content erwartet wird.

Das Content Model ist transparent.

Als Content Attributes gelten:

- Global Attributes mit Ausnahme von `is`
- für form-associated Custom Elements zusätzlich `form`
- `disabled`
- `readonly`
- `name`
- weitere namespace-lose Attribute gemäß der normativen Regel

Ein Autonomous Custom Element besitzt keine automatisch durch seinen Namen vermittelte spezielle HTML-Semantik.

### Customized Built-In Elements

Customized Built-In Elements behalten den Local Name des nativen Elements, das sie erweitern.

Ihre Semantik und ihre sonstigen nativen Elementregeln stammen vom erweiterten HTML-Element.

Der Custom-Element-Name wird für die Definition und das `is`-Konzept verwendet.

Customized Built-In Elements können nur geeignete native HTML-Elemente erweitern.

Die Erweiterung eines unbekannten beziehungsweise als `HTMLUnknownElement` definierten Legacy-Elements ist nicht zulässig.

### Verhalten des `is`-Attributs

`is` ist bereits in `13-global-attributes.md` dokumentiert.

Für Custom Elements ist zusätzlich relevant:

- `is` identifiziert bei Customized Built-In Elements die Custom-Element-Definition.
- Nach Erstellung des Elements ändert eine spätere Änderung des `is`-Attributwerts nicht das bereits festgelegte Custom-Element-Verhalten.
- Bei programmgesteuerter Erstellung kann der `is`-Wert intern gesetzt sein, ohne dass das Attribut zunächst explizit im DOM vorhanden ist.
- Bei Serialisierung kann der `is`-Wert wieder als `is`-Attribut erscheinen.

### Valid Custom Element Names

Ein gültiger Custom Element Name muss:

1. ein gültiger Element Local Name sein,
2. mit einem ASCII-Kleinbuchstaben beginnen,
3. keine ASCII-Großbuchstaben enthalten,
4. einen Bindestrich enthalten,
5. darf keiner der reservierten Namen sein.

Der Bindestrich stellt zugleich eine Forward-Compatibility-Grenze gegenüber zukünftigen nativen HTML-, SVG- und MathML-Namen dar.

### Definitionen

Eine Definition wird über `CustomElementRegistry.define()` registriert.

Dabei werden unter anderem geprüft:

- Konstruktorfähigkeit
- Gültigkeit des Namens
- bereits registrierter Name
- bereits registrierter Konstruktor
- `extends`-Wert
- Zulässigkeit des zu erweiternden nativen Elements
- Reentrancy der Elementdefinition

Bei Fehlern können insbesondere `TypeError`, `SyntaxError` oder `NotSupportedError` auftreten.

### Autonomous Definition

Bei einer Definition ohne `extends` entspricht der Local Name dem Custom Element Name.

Beispiel:

`customElements.define("my-element", MyElement)`

### Customized Built-In Definition

Bei einer Definition mit `extends`:

`customElements.define("plastic-button", PlasticButton, { extends: "button" })`

gilt:

- definierter Name: `plastic-button`
- Local Name: `button`
- `is`-Wert: `plastic-button`

Ein Custom Element Name darf nicht selbst als `extends`-Wert verwendet werden.

Das zu erweiternde Element muss ein zulässiges natives HTML-Element sein.

### Konstruktoranforderungen

Für Custom Element Constructors gelten normative Anforderungen.

Insbesondere:

- `super()` muss als parameterloser Aufruf am Anfang des Constructors ausgeführt werden.
- Ein `return` innerhalb des Constructors ist grundsätzlich nicht zulässig, außer als einfacher früher Rücksprung.
- `document.write()` darf nicht verwendet werden.
- `document.open()` darf nicht verwendet werden.
- Attribute und Children sollen im Constructor nicht inspiziert werden.
- Der Constructor darf nicht eigenständig Attribute oder Children hinzufügen.
- Initialisierung soll grundsätzlich auf den Constructor beschränkt bleiben.
- Arbeiten, die vom verbundenen DOM abhängen, sollen grundsätzlich in geeignete Lifecycle Callbacks verschoben werden.

Diese Anforderungen sind für die korrekte Instanziierung durch DOM-APIs und Parser relevant.

### Constructor und Upgrade

Der Constructor muss so implementiert sein, dass sowohl reguläre Konstruktion als auch Upgrade-Verarbeitung korrekt funktionieren.

Insbesondere darf der Constructor nicht davon ausgehen, dass bei jedem Aufruf bereits alle Attribute und Children vorhanden sind.

Das ist insbesondere relevant, weil ein Element nachträglich upgraded werden kann.

---

## Lifecycle Callbacks

Eine Custom Element Definition kann Lifecycle Callbacks enthalten.

Die aktuelle WHATWG-Systematik umfasst:

- `connectedCallback`
- `disconnectedCallback`
- `connectedMoveCallback`
- `adoptedCallback`
- `attributeChangedCallback`
- `formAssociatedCallback`
- `formDisabledCallback`
- `formResetCallback`
- `formStateRestoreCallback`

Nicht jeder Callback ist für jedes Custom Element relevant.

### `connectedCallback`

Wird als Reaction verwendet, wenn ein Custom Element verbunden wird.

Der Callback kann mehrfach ausgeführt werden.

Daher darf eine Implementierung nicht davon ausgehen, dass `connectedCallback` nur einmal im Lebenszyklus eines Elements ausgeführt wird.

### `disconnectedCallback`

Wird verwendet, wenn das Element aus dem verbundenen DOM entfernt beziehungsweise disconnected wird.

### `connectedMoveCallback`

`connectedMoveCallback` dient der state-preserving Behandlung von DOM-Bewegungen.

Wenn ein Element innerhalb des verbundenen DOM bewegt wird, kann die Implementierung damit vermeiden, dass die klassische Folge:

- `disconnectedCallback`
- `connectedCallback`

ausgeführt wird.

Das ist insbesondere relevant für zustandsbehaftete Komponenten.

### `adoptedCallback`

Wird verwendet, wenn ein Custom Element in ein anderes Dokument übernommen wird.

Der Callback erhält Informationen über altes und neues Dokument.

### `attributeChangedCallback`

Wird verwendet, wenn ein beobachtetes Attribut geändert, hinzugefügt, entfernt oder ersetzt wird.

Die Callback-Argumente umfassen:

- Attribut Local Name
- alten Wert
- neuen Wert
- Namespace

Ein Attribut löst diese Reaction nur aus, wenn es in der Liste der `observedAttributes` enthalten ist.

### Form Lifecycle Callbacks

Für form-associated Custom Elements sind zusätzlich relevant:

- `formAssociatedCallback`
- `formDisabledCallback`
- `formResetCallback`
- `formStateRestoreCallback`

Diese Callbacks verbinden die Custom-Element-Verarbeitung mit der Formularverarbeitung.

---

## Custom Element Reactions

Custom Element Reactions bilden ein eigenes normatives Processing Model.

Ein Custom Element besitzt eine Reaction Queue.

Zu den Reaction-Typen gehören insbesondere:

- Upgrade Reaction
- Callback Reaction

### Reaction Stack

Für einen relevanten Agent existiert ein Custom Element Reactions Stack.

Dieser wird zur Verarbeitung verschachtelter DOM-Operationen verwendet.

### Element Queue

Elemente werden in Element Queues eingeordnet.

Die Verarbeitung der Queue führt anschließend die zugehörigen Reactions des jeweiligen Elements aus.

### Backup Element Queue

Wenn kein regulärer Reaction-Stack-Kontext vorhanden ist, kann die Backup Element Queue verwendet werden.

Die Verarbeitung erfolgt über einen Microtask.

### Callback Reaction

Eine Callback Reaction enthält insbesondere:

- Callback
- Argumente
- Ziel-Element

### Upgrade Reaction

Eine Upgrade Reaction enthält die Custom Element Definition, mit der das Element upgraded werden soll.

### Reaktionsreihenfolge

Die Reihenfolge der Reactions ist normativ relevant.

Upgrade-, Attribut- und Lifecycle-Reaktionen dürfen nicht als frei verfügbare synchrone JavaScript-Aufrufe verstanden werden.

Die WHATWG definiert hierfür ein eigenes Queue-/Stack-Verarbeitungsmodell.

---

## `[CEReactions]`

`[CEReactions]` ist ein Web-IDL Extended Attribute.

Es kennzeichnet relevante Operationen, Attribute, Setter und Deleter, deren Ausführung mit der Custom-Element-Reaktionsverarbeitung verbunden werden muss.

Die Kennzeichnung:

- nimmt keine Argumente entgegen,
- darf nicht beliebig verwendet werden,
- darf nicht auf readonly Attributes erscheinen.

Die ergänzende Verarbeitung umfasst:

1. Push einer neuen Element Queue auf den Reaction Stack.
2. Ausführung der ursprünglichen Operation.
3. Behandlung von Rückgabewert oder Exception.
4. Pop der Element Queue.
5. Ausführung der Custom Element Reactions.
6. erneutes Werfen einer ursprünglichen Exception.
7. Rückgabe eines ursprünglichen Return Values.

Die `[CEReactions]`-Systematik ist ein normatives Bindeglied zwischen Web-IDL-APIs und Custom Element Reactions.

---

## Upgrades

Ein Element kann zunächst als nicht-custom Element erstellt und später nach Registrierung einer passenden Definition upgraded werden.

Das Upgrade ist insbesondere relevant für:

- Parser-erzeugte Elemente
- bereits vorhandene Elemente
- Progressive Enhancement
- asynchron geladene Custom-Element-Definitionen

### Upgrade-Voraussetzung

Die Definition muss registriert sein und zum Element passen.

Die Suche berücksichtigt insbesondere:

- Custom Element Registry
- Namespace
- Local Name
- `is`-Wert

### Upgrade von verbundenen Elementen

Bei der Definition eines Custom Elements werden passende bereits verbundene Elemente gesucht und für das Upgrade vorgemerkt beziehungsweise mit Upgrade Reactions versehen.

### Nicht verbundene Elemente

Ein nicht in einem Dokument verbundener Kandidat wird nicht allein durch die Registrierung automatisch in derselben Weise upgraded wie ein entsprechendes verbundenes Element.

Beim späteren Einfügen in den Dokumentbaum kann das Upgrade erfolgen.

### `upgrade()`

`CustomElementRegistry.upgrade(root)` ermöglicht das explizite Upgrade geeigneter Nachfahren eines angegebenen Roots.

Dabei werden shadow-including descendants berücksichtigt.

---

## Custom Element Registry

### Interface

Die aktuelle WHATWG-IDL für `CustomElementRegistry` umfasst:

- `constructor()`
- `define()`
- `get()`
- `getName()`
- `whenDefined()`
- `upgrade()`
- `initialize()`

Zusätzlich existieren die für die Definition benötigten Konzepte:

- `CustomElementConstructor`
- `ElementDefinitionOptions`

### `constructor()`

Erzeugt eine neue `CustomElementRegistry`.

Die aktuelle Spezifikation verwendet hierfür auch den scoped Registry-Mechanismus.

### `define(name, constructor, options)`

Registriert eine Custom Element Definition.

Parameter:

- `name`
- `constructor`
- optional `options`

`options` kann insbesondere:

- `extends`

enthalten.

### `get(name)`

Liefert den registrierten Constructor für einen Custom Element Name.

Wenn keine passende Definition existiert, wird `undefined` geliefert.

### `getName(constructor)`

Liefert den Custom Element Name, der mit einem registrierten Constructor verbunden ist.

Wenn kein passender Eintrag existiert, wird `null` geliefert.

### `whenDefined(name)`

Liefert ein Promise für die Definition eines gültigen Custom Element Names.

Wenn der Name bereits definiert ist, kann das Promise unmittelbar mit dem Constructor erfüllt werden.

Wenn der Name noch nicht definiert ist, wird ein entsprechender Promise-Eintrag verwaltet und bei der Definition aufgelöst.

Ein ungültiger Custom Element Name führt zu einer Ablehnung mit `SyntaxError`.

### `upgrade(root)`

Versucht, passende Custom Elements innerhalb des angegebenen Roots zu upgraden.

Dabei werden shadow-including descendants in der normativ definierten Reihenfolge betrachtet.

### `initialize(root)`

Die aktuelle WHATWG-Definition enthält `initialize()` als Operation der `CustomElementRegistry`.

Diese Operation gehört zum aktuellen Registry-Modell und ist nicht mit `define()` oder `upgrade()` gleichzusetzen.

Die genaue Semantik ist im Zusammenhang mit Scoped Custom Element Registries und der DOM-/HTML-Registry-Integration zu betrachten.

---

## Scoped Custom Element Registries

Die aktuelle HTML-Spezifikation unterstützt scoped Custom Element Registries.

Ziel ist unter anderem die Koexistenz mehrerer Bibliotheken, die gleiche Custom Element Names unabhängig voneinander definieren können.

Eine Registry kann mit:

`new CustomElementRegistry()`

erzeugt werden.

Eine Definition kann anschließend registriert werden.

Ein Element beziehungsweise ein Node kann mit einer bestimmten Registry verbunden werden.

Die Registry-Zuordnung beeinflusst die Custom-Element-Operationen, die für diesen Node-Kontext verwendet werden.

### Registry-Zuordnung

Die aktuelle Spezifikation berücksichtigt Registry-Zuordnungen für:

- Elements
- Shadow Roots
- Documents

### Globale Registry

Die `window.customElements`-Eigenschaft liefert die Registry des zugehörigen Documents.

### Scoped Registry

Eine explizit erzeugte `CustomElementRegistry` kann als scoped Registry verwendet werden.

Dies ist ein eigenständiges Konzept und darf nicht mit der globalen `window.customElements`-Registry gleichgesetzt werden.

---

## Custom Element Definition – internes Modell

Eine Custom Element Definition enthält normativ unter anderem:

- Name
- Local Name
- Constructor
- observed attributes
- Lifecycle Callback Collection
- Construction Stack
- Form-associated Boolean
- Disable Internals Boolean
- Disable Shadow Boolean

### Observed Attributes

Die Definition enthält eine Liste von Attributnamen, für die `attributeChangedCallback`-Reaktionen erzeugt werden können.

### Construction Stack

Der Construction Stack wird während der Upgrade- und Constructor-Verarbeitung verwendet.

Er enthält Elemente beziehungsweise bereits-konstruierte Marker.

Dieses interne Modell ist für die korrekte Integration von HTML Element Constructors und Custom Element Constructors relevant.

### Form-associated Boolean

Wenn `true`, wird das Element als form-associated Custom Element behandelt.

### Disable Internals Boolean

Steuert, ob `attachInternals()` für die Definition deaktiviert ist.

### Disable Shadow Boolean

Steuert, ob `attachShadow()` für die Definition deaktiviert ist.

---

## DOM Interfaces / APIs

### `HTMLElement`

Autonomous Custom Elements erben typischerweise von `HTMLElement`.

Der Custom Element Constructor ist damit in der Regel ein Constructor, der auf `HTMLElement` aufbaut.

### `HTMLButtonElement` und andere native Interfaces

Customized Built-In Elements können von dem Interface des nativen Elements erben, das sie erweitern.

Beispiel:

`class PlasticButton extends HTMLButtonElement`

Die semantische Identität des nativen Elements bleibt erhalten.

### `CustomElementRegistry`

Primäres Registry-Interface der Feature-Familie.

### `ElementInternals`

Primäres Interface für interne Plattformintegration.

### `CustomStateSet`

Set-like Interface für Custom States.

---

## ElementInternals

`ElementInternals` stellt einem Custom Element interne Plattformfähigkeiten zur Verfügung.

### `attachInternals()`

`HTMLElement.attachInternals()` liefert ein `ElementInternals`-Objekt für ein geeignetes Custom Element.

Die Methode kann insbesondere fehlschlagen, wenn:

- das Element kein zulässiges Custom Element ist,
- die Internals-Funktion in der Definition deaktiviert wurde,
- bereits Internals für das Element angehängt wurden,
- das Element beziehungsweise seine Definition nicht die erforderlichen Voraussetzungen erfüllt.

### `ElementInternals`-IDL

Die aktuelle WHATWG-Systematik umfasst unter anderem:

- `shadowRoot`
- `setFormValue()`
- `form`
- `setValidity()`
- `willValidate`
- `validity`
- `validationMessage`
- `checkValidity()`
- `reportValidity()`
- `labels`
- `states`

Zusätzlich wird `ElementInternals` mit `ARIAMixin` integriert.

---

## Shadow Root Access

`ElementInternals.shadowRoot` ermöglicht Zugriff auf den relevanten Shadow Root eines Custom Elements, sofern die normativen Voraussetzungen erfüllt sind.

Wenn das Ziel-Element kein Shadow Host ist oder der Shadow Root nicht für Element Internals verfügbar ist, liefert der Getter `null`.

Die Funktion ist damit eine kontrollierte interne Schnittstelle und kein allgemeiner Ersatz für `Element.shadowRoot`.

---

## Form-associated Custom Elements

Form-associated Custom Elements verbinden Custom Elements mit der HTML-Formularinfrastruktur.

Ein form-associated Custom Element kann unter anderem:

- einem Form Owner zugeordnet sein,
- an Form Submission teilnehmen,
- Constraint Validation unterstützen,
- disabled sein,
- resettable sein,
- labelable sein,
- einen Submission Value bereitstellen,
- einen internen State bereitstellen.

### Form Attribute

Für form-associated Custom Elements sind insbesondere relevant:

- `form`
- `disabled`
- `readonly`
- `name`

### `form`

Das `form`-Attribut kann eine explizite Zuordnung zum Form Owner ermöglichen.

### `disabled`

Bei einem form-associated Custom Element verhindert `disabled` unter anderem die normale interaktive Teilnahme und die Submission des Submission Value.

### `readonly`

`readonly` bewirkt bei form-associated Custom Elements, dass das Element von Constraint Validation ausgeschlossen ist.

Die Spezifikation verlangt dabei nicht automatisch dieselbe Bearbeitungslogik wie bei nativen Form Controls.

### `name`

`name` stellt den Namen bereit, unter dem das Custom Element bei Form Submission beziehungsweise entsprechenden Formular-APIs berücksichtigt wird.

---

## Form Lifecycle

### `formAssociatedCallback`

Wird verwendet, wenn sich die Form Association des Custom Elements ändert.

### `formDisabledCallback`

Wird verwendet, wenn sich der Disabled-Zustand im Rahmen der Formularinfrastruktur ändert.

### `formResetCallback`

Wird im Rahmen des Form Reset Algorithmus als Reaction ausgeführt.

### `formStateRestoreCallback`

Kann verwendet werden, wenn der User Agent den State eines form-associated Custom Elements wiederherstellen möchte.

Das kann beispielsweise im Zusammenhang mit:

- Navigation
- Wiederherstellung des Formularzustands
- Form-Filling-Funktionen

relevant sein.

---

## Submission Value und State

Ein form-associated Custom Element besitzt:

- Submission Value
- State

### Submission Value

Der Submission Value wird für die Formularübermittlung verwendet.

Der initiale Wert ist `null`.

Mögliche Zustände umfassen unter anderem:

- `null`
- String
- `File`
- Liste von Entries

### State

Der State dient insbesondere der Wiederherstellung von Benutzereingaben.

Der initiale Wert ist `null`.

State und Submission Value können bewusst unterschiedliche Repräsentationen besitzen.

Beispielhafte fachliche Unterscheidung:

- User-Eingabe: `3/15/2019`
- Submission Value: `2019-03-15`

### `setFormValue()`

`ElementInternals.setFormValue()` setzt den Submission Value.

Optional kann zusätzlich ein separater State gesetzt werden.

Wenn der Submission Value `null` ist, nimmt das Element nicht an der Form Submission teil.

---

## Constraint Validation

Form-associated Custom Elements können an Constraint Validation teilnehmen.

`ElementInternals` stellt hierfür insbesondere bereit:

- `willValidate`
- `validity`
- `validationMessage`
- `checkValidity()`
- `reportValidity()`
- `setValidity()`

### Validity Flags

Die WHATWG-Definition verwendet unter anderem:

- `valueMissing`
- `typeMismatch`
- `patternMismatch`
- `tooLong`
- `tooShort`
- `rangeUnderflow`
- `rangeOverflow`
- `stepMismatch`
- `badInput`
- `customError`

### `setValidity()`

`setValidity()` setzt die vom Custom Element gemeldeten Validitätszustände.

Wenn mindestens ein Validitätsflag gesetzt wird, muss eine nichtleere Fehlermeldung bereitgestellt werden.

Ein optionaler Validation Anchor kann angegeben werden.

Der Anchor muss die normativen Anforderungen an die Beziehung zum Ziel-Element erfüllen.

### `checkValidity()`

Prüft die Constraint-Validity des Custom Elements.

Bei ungültigem Zustand wird das entsprechende `invalid`-Verhalten ausgelöst.

### `reportValidity()`

Prüft die Constraint-Validity und kann zusätzlich die entsprechende Fehlermeldung an den Benutzer melden, sofern das Event nicht abgebrochen wird.

---

## Accessibility

Custom Elements erhalten nicht allein aufgrund ihres Namens automatisch die Semantik eines nativen HTML-Elements.

Ein Autonomous Custom Element mit dem Namen `custom-button` wird daher nicht automatisch zu einem Button.

Das ist eine zentrale normative und fachliche Abgrenzung.

### Accessibility über `ElementInternals`

`ElementInternals` kann Default-Accessibility-Semantik bereitstellen.

Dazu gehören insbesondere:

- Default ARIA Role
- Default ARIA States
- Default ARIA Properties

### `role`

`ElementInternals.role` kann die Default-ARIA-Rolle des Custom Elements festlegen.

Die Semantik kann grundsätzlich durch den Seitenautor überschrieben werden, soweit die jeweiligen Accessibility-Regeln dies zulassen.

### `aria-*`

`ElementInternals` integriert ARIA-Zustände und Eigenschaften in die interne Semantik des Custom Elements.

Die über `ElementInternals` gesetzten Werte sind Default-Semantik und nicht automatisch unveränderbare starke Semantik.

### Externe Accessibility-Spezifikationen

WHATWG verweist für die konkrete Accessibility-Integration auf externe Accessibility-/ARIA-Spezifikationen.

Diese Informationen sind daher nicht als ausschließlich in HTML definierte ARIA-Semantik zu interpretieren.

Die HTML-Referenz dokumentiert hier die HTML-seitige Integrationsregel.

---

## Sanitization

Für Autonomous Custom Elements weist die aktuelle Elementdefinition die Sanitization-Kategorie als `Uncategorized` aus.

Daraus folgt:

- Custom Elements erhalten keine pauschale, eigenständige Sanitization-Regel allein durch ihre Definition.
- Benutzerdefinierte Attribute können Bestandteil der elementeigenen Funktion sein.
- Sanitization darf nicht pauschal mit der Custom-Element-Definition gleichgesetzt werden.

Für konkrete Parsing-, Sanitization- oder DOM-Manipulationsoperationen sind die jeweils zuständigen WHATWG-Algorithmen separat zu prüfen.

---

## Custom States

Custom Elements können eigene Zustände exponieren.

Die HTML-Spezifikation verwendet hierfür:

- `ElementInternals.states`
- `CustomStateSet`
- CSS `:state()`

### `states`

`ElementInternals.states` liefert die `CustomStateSet` des Custom Elements.

### `CustomStateSet`

`CustomStateSet` ist ein `setlike<DOMString>`-Interface.

Es unterstützt unter anderem:

- `add()`
- `has()`
- `delete()`
- `clear()`
- Iteration
- `forEach()`
- `size`

### `:state()`

Mit `:state()` können Custom States als CSS-Pseudo-Klasse angesprochen werden.

Beispiel:

`:state(checked)`

Der State muss vorher über `ElementInternals.states` gesetzt worden sein.

### Mehrwertige Zustände

Die `states`-Systematik stellt einzelne String-Werte als Zustände bereit.

Ein logisch mehrwertiger Zustand kann in mehrere exklusive boolesche Zustände abgebildet werden.

Beispielsweise:

- `loading`
- `interactive`
- `complete`

können als drei Zustandswerte modelliert werden.

---

## Content Categories

Autonomous Custom Elements sind nach aktueller WHATWG-Definition insbesondere:

- Flow Content
- Phrasing Content
- Palpable Content

Für form-associated Custom Elements kommen entsprechende Form-Kategorien hinzu.

Die vollständige Definition der Content Categories ist in:

`docs/html/14-content-categories.md`

dokumentiert.

Diese Datei behandelt daher nur die Custom-Element-spezifische Beziehung zu den Kategorien.

### Wichtig

Custom Elements stellen keine zusätzliche allgemeine Content Category dar.

`autonomous custom elements` erscheinen innerhalb der bestehenden Kategoriensystematik.

---

## Context

Für Autonomous Custom Elements ist der Context insbesondere an Stellen gebunden, an denen Phrasing Content erwartet wird.

Die konkrete Verwendung eines Custom Elements kann darüber hinaus durch die Definition des umgebenden Elements und dessen Content Model beeinflusst werden.

Customized Built-In Elements folgen hinsichtlich Context und Content Model grundsätzlich dem nativen Element, das sie erweitern.

---

## Content Model

Für Autonomous Custom Elements ist das Content Model transparent.

Damit wird die konkrete zulässige Kindstruktur im Kontext des umgebenden Elements weiterbestimmt.

Das transparente Content Model ist in:

`docs/html/15-content-models.md`

ausführlich dokumentiert.

Customized Built-In Elements verwenden dagegen die Content-Model-Regeln des erweiterten nativen Elements.

---

## Content Attributes

### Autonomous Custom Elements

Grundsätzlich:

- Global Attributes außer `is`
- zusätzliche formbezogene Attribute für form-associated Custom Elements
- weitere zulässige namespace-lose Attribute nach den Custom-Element-Regeln

### `is`

`is` darf bei Autonomous Custom Elements nicht als Mechanismus zur Customized-Built-In-Definition verwendet werden.

### Benutzerdefinierte Attribute

Ein Autonomous Custom Element kann weitere namespace-lose Attribute verwenden, wenn:

- der Attributname gültig ist,
- keine ASCII-Großbuchstaben enthalten sind,
- das Attribut für die Funktion des Elements relevant ist.

Für zusätzliche eigene Attributinformationen empfiehlt die WHATWG-Systematik bei Customized Built-In Elements insbesondere die Verwendung von `data-*`, sofern ein eigenes Attributverhalten benötigt wird.

---

## Parsing

Custom Elements sind in das HTML-Parsing integriert.

Ein Custom Element kann bereits während der Parserverarbeitung erzeugt werden.

### Autonomous Custom Elements beim Parsing

Wenn ein passendes Custom Element registriert ist, kann der Parser die entsprechende Custom Element Definition bei der Konstruktion berücksichtigen.

Wenn die Definition noch nicht registriert ist, kann das Element zunächst als nicht-definiertes Element entstehen und später upgraded werden.

### Customized Built-In Elements beim Parsing

Bei Customized Built-In Elements ist der Local Name des Elements entscheidend.

Beispiel:

`<button is="plastic-button">`

ist ein `button` mit dem entsprechenden `is`-Wert.

`<plastic-button>`

ist dagegen nicht automatisch dasselbe Customized Built-In Element.

### Parser und Constructor

Die Parserverarbeitung muss die normativen Constructor-Anforderungen berücksichtigen.

Insbesondere darf die Custom-Element-Definition nicht davon ausgehen, dass im Constructor bereits alle späteren Attribute oder Children vorhanden sind.

---

## DOM-Erzeugung

Custom Elements können über DOM-APIs erzeugt werden.

### `document.createElement()`

Autonomous Custom Elements können über:

`document.createElement("my-element")`

erzeugt werden.

### Customized Built-In Elements

Customized Built-In Elements können über die entsprechende `is`-Option erzeugt werden.

Beispiel:

`document.createElement("button", { is: "plastic-button" })`

### Constructor

Ein registriertes Custom Element kann zusätzlich über seinen Constructor erzeugt werden:

`new MyElement()`

Bei Customized Built-In Elements verwendet der Constructor das native Element Interface als Basisklasse.

---

## DOM Registry Beziehungen

Die Custom Element Registry ist mit dem DOM verbunden.

Relevante Registry-Kontexte umfassen:

- Document
- Element
- ShadowRoot

Die Lookup-Regeln berücksichtigen:

- Registry
- Namespace
- Local Name
- `is`-Wert

Ein Lookup für einen nicht-HTML Namespace liefert keine Custom Element Definition nach dem entsprechenden HTML Custom-Elements-Mechanismus.

---

## Custom Element State

Ein Custom Element besitzt einen normativen Custom Element State.

Für die Verarbeitungsmodelle sind insbesondere Zustände relevant, die den Lebenszyklus und Upgrade-Vorgang beschreiben.

Dazu gehören unter anderem Zustände wie:

- `undefined`
- `failed`
- `precustomized`
- `custom`

Die konkrete Zustandsverwaltung ist Teil der Upgrade- und Construction-Algorithmen.

Die Zustände dürfen nicht mit den vom Autor über `CustomStateSet` definierten Custom States verwechselt werden.

### Abgrenzung

**Custom Element State**

ist ein internes HTML-/DOM-Verarbeitungskonzept.

**Custom State**

ist ein vom Autor exponierter Zustand über `ElementInternals.states` und `:state()`.

Diese beiden Konzepte sind fachlich verschieden.

---

## Upgrade Processing Model

Das Upgrade eines Elements umfasst im Kern:

1. Lookup der passenden Custom Element Definition.
2. Erzeugung beziehungsweise Enqueue einer Upgrade Reaction.
3. Verarbeitung der Upgrade Reaction.
4. Verwendung der Construction Stack-Mechanik.
5. Ausführung des Custom Element Constructors.
6. Verarbeitung der relevanten Form-Integration.
7. Übergang des Elements in den Custom State.

Fehler während der Konstruktion können dazu führen, dass das Element nicht erfolgreich upgraded wird.

### Fehlerfall

Bei einem fehlgeschlagenen Upgrade werden unter anderem:

- Custom Element Definition
- Reaction Queue
- Custom Element State

entsprechend dem normativen Fehlerverhalten behandelt.

---

## Form Processing Model

Form-associated Custom Elements werden in die bestehende Formularverarbeitung integriert.

Das umfasst:

- Form Owner
- Form Association
- Disabled State
- Submission Value
- State
- Reset
- Constraint Validation
- Label Association
- Form Elements Collection

### Submission

Ein form-associated Custom Element kann über `setFormValue()` einen Submission Value bereitstellen.

Der User Agent verarbeitet diesen Wert entsprechend dem Form Submission Model.

### State Restore

Der separate State ermöglicht die Wiederherstellung der Benutzereingabe.

Damit können State und Submission Value unterschiedliche Werte besitzen.

---

## Accessibility Processing Model

Custom Elements besitzen keine automatisch aus dem Tag-Namen abgeleitete native Semantik.

Autoren müssen bei Autonomous Custom Elements gegebenenfalls:

- Rolle
- Zustände
- Eigenschaften
- Fokusverhalten
- Tastaturverhalten
- Interaktionsverhalten

selbst modellieren.

`ElementInternals` ermöglicht dabei Default-Accessibility-Semantik.

Die konkrete Semantik ist zusätzlich im Verhältnis zu ARIA und Accessibility Platform APIs zu betrachten.

---

## Custom State Processing Model

Custom States werden intern als Set von Strings verwaltet.

Die grundlegenden Operationen sind:

- Hinzufügen
- Prüfen
- Entfernen
- vollständiges Leeren

Die CSS-Integration stellt die Werte über `:state()` bereit.

Custom States sind damit:

- DOM-/API-Zustand
- CSS-Schnittstelle
- kein Content Attribute
- kein HTML-Element
- keine Content Category

---

## Attribute

### Bereits separat dokumentiert

Das globale Attribut:

`is`

ist in:

`docs/html/13-global-attributes.md`

bereits dokumentiert.

Diese Datei ergänzt dort nur die Custom-Elements-spezifische Bedeutung.

### Custom Element Definition Options

Die API verwendet zusätzlich:

`extends`

als Option von `CustomElementRegistry.define()`.

`extends` ist dabei kein HTML-Content-Attribute.

Es ist ein API-/Definition-Parameter.

### Formbezogene Attribute

Für form-associated Custom Elements sind relevant:

- `form`
- `disabled`
- `readonly`
- `name`

Diese sind keine neuen Custom-Element-spezifischen Attribute im Sinne eines neuen Attributinventars.

Sie werden hier nur im Kontext der Custom-Element-Integration dokumentiert.

---

## DOM Interfaces / APIs – Detailinventar

| API / Interface | Typ | Funktion |
|---|---|---|
| `CustomElementRegistry` | DOM Interface | Verwaltung von Custom Element Definitions |
| `customElements` | Window-/Document-Bezug | Zugriff auf globale Registry |
| `CustomElementRegistry()` | Constructor | Erzeugung einer Registry |
| `define()` | Methode | Definition registrieren |
| `get()` | Methode | Constructor anhand des Namens abrufen |
| `getName()` | Methode | Namen anhand des Constructors abrufen |
| `whenDefined()` | Methode | auf Definition warten |
| `upgrade()` | Methode | passende Elemente upgraden |
| `initialize()` | Methode | Registry-/Initialisierungsmechanismus |
| `ElementInternals` | DOM Interface | interne Plattformintegration |
| `attachInternals()` | HTMLElement-Methode | `ElementInternals` erzeugen/zuordnen |
| `CustomStateSet` | DOM Interface | Custom States verwalten |
| `states` | ElementInternals-Attribut | Zugriff auf Custom State Set |
| `setFormValue()` | ElementInternals-Methode | Submission Value und State setzen |
| `setValidity()` | ElementInternals-Methode | Constraint Validation steuern |
| `checkValidity()` | ElementInternals-Methode | Validität prüfen |
| `reportValidity()` | ElementInternals-Methode | Validität prüfen und ggf. melden |

---

## Lifecycle / Callback-Inventar

| Callback | Auslöser / Zweck |
|---|---|
| `connectedCallback` | Verbindung mit dem DOM |
| `disconnectedCallback` | Trennung vom DOM |
| `connectedMoveCallback` | state-preserving DOM-Bewegung |
| `adoptedCallback` | Adoption in ein anderes Document |
| `attributeChangedCallback` | Änderung eines beobachteten Attributes |
| `formAssociatedCallback` | Änderung der Form Association |
| `formDisabledCallback` | Änderung des Disabled-Zustands |
| `formResetCallback` | Formular-Reset |
| `formStateRestoreCallback` | Wiederherstellung des Formularzustands |

---

## Konformitätsregeln

### Für Autoren von Autonomous Custom Elements

Zu beachten sind insbesondere:

- gültiger Custom Element Name
- gültige Constructor-Vererbung
- korrektes `super()`
- keine unzulässige Rückgabe aus dem Constructor
- kein `document.write()` im Constructor
- kein `document.open()` im Constructor
- keine Abhängigkeit von bereits vorhandenen Children im Constructor
- keine unzulässige Änderung von Attributen oder Children im Constructor
- korrekte Verwendung von `observedAttributes`
- korrekte Lifecycle-Callback-Semantik
- korrekte Behandlung wiederholter `connectedCallback`-Aufrufe
- korrekte Form-Integration bei form-associated Custom Elements
- korrekte Verwendung von `ElementInternals`

### Für Customized Built-In Elements

Zusätzlich:

- `extends` muss auf ein zulässiges natives HTML-Element verweisen.
- Ein Custom Element Name darf nicht als `extends`-Wert verwendet werden.
- Legacy-Elemente mit `HTMLUnknownElement` können nicht als zulässige Basis verwendet werden.
- Das HTML-Markup verwendet den Local Name des nativen Elements.
- Der Custom Element Name wird über `is` identifiziert.

### Für `is`

`is` darf nicht als nachträglicher Mechanismus verstanden werden, der das bereits erzeugte Element dynamisch in ein anderes Custom Element verwandelt.

Der relevante `is`-Wert ist Bestandteil der Custom-Element-Definition und des Elementzustands.

---

## Status / V1

### WHATWG-Status

Custom Elements sind im aktuellen WHATWG HTML Living Standard definiert.

Der relevante normative Bereich ist:

- §4.13 Custom elements

Die Feature-Familie umfasst normative Definitionen, APIs und Processing Models.

### Obsolete / Deprecated

Die in dieser Datei dokumentierte Custom-Elements-Systematik ist kein obsolete oder deprecated HTML-Feature.

### Browser-Kompatibilität

Browser-Kompatibilität wird nicht als WHATWG-Status verwendet.

Die WHATWG-Seite kann zusätzliche Kompatibilitätsinformationen anzeigen; diese sind für die Statusklassifikation von ZE-WebLab getrennt zu behandeln.

### ZE-WebLab V1

V1 ist eine Projektebene.

Für diese Feature-Familie gilt:

- Feature-Familie: Custom Elements
- Feature-Typ: Custom Elements Feature / API / Processing Model
- native HTML-Elementinventarliste: nein
- V1-Zuordnung: zweite Rechercheebene

Die konkrete V1-Kategorisierung darf nicht mit dem WHATWG-Status verwechselt werden.

---

## Querverweise

### Custom Elements ↔ Global Attributes

`is` ist bereits in:

`docs/html/13-global-attributes.md`

dokumentiert.

Custom Elements verwenden `is` insbesondere bei Customized Built-In Elements.

### Custom Elements ↔ Content Categories

Autonomous Custom Elements besitzen eigene Einträge innerhalb der WHATWG Content Categories.

Siehe:

`docs/html/14-content-categories.md`

### Custom Elements ↔ Content Models

Autonomous Custom Elements besitzen ein transparentes Content Model.

Siehe:

`docs/html/15-content-models.md`

### Custom Elements ↔ Forms

Form-associated Custom Elements integrieren sich in:

- Form Owner
- Form Submission
- Constraint Validation
- Form Reset
- Label Association

Siehe zusätzlich:

`docs/html/10-forms.md`

### Custom Elements ↔ DOM

Custom Elements verwenden zentrale DOM-Konzepte:

- Element
- Document
- ShadowRoot
- Node
- Registry
- Constructor
- Adoption
- DOM Movement

### Custom Elements ↔ Parsing

Der HTML Parser kann Custom Elements erzeugen und später registrierte Elemente upgraden.

Parsing und Custom Element Reactions sind daher miteinander verbunden.

### Custom Elements ↔ Shadow DOM

Scoped Registries und `ElementInternals.shadowRoot` stehen in direkter Beziehung zu Shadow DOM.

Shadow DOM selbst ist nicht Bestandteil dieser Datei als vollständige eigenständige Feature-Familie.

### Custom Elements ↔ Accessibility

`ElementInternals` integriert Custom Elements mit ARIA- und Accessibility-Semantik.

### Custom Elements ↔ CSS

Custom States werden über `:state()` in CSS verfügbar.

Diese Datei dokumentiert nur die HTML-/DOM-Seite dieser Integration.

### Custom Elements ↔ Link Types

Es besteht keine allgemeine direkte Link-Type-Feature-Familie.

Die Dokumentation von Link Types verbleibt in:

`docs/html/16-link-types.md`

---

## Nicht als Custom Elements zu zählen

Folgende Konzepte sind keine eigenständigen nativen HTML-Elemente:

- `CustomElementRegistry`
- `ElementInternals`
- `CustomStateSet`
- `CustomElementConstructor`
- Custom Element Definition
- Custom Element Reaction
- Reaction Queue
- Construction Stack
- Custom Element State
- `:state()`
- `[CEReactions]`
- Lifecycle Callbacks
- `is` als Attribut
- `extends` als API-Option
- Scoped Custom Element Registry

Ebenso ist ein beliebiges vom Autor definiertes Custom Element keine Erweiterung des nativen HTML-Elementinventars im Sinne einer zusätzlichen endlichen Elementliste.

---

## Abgrenzung zu Web Components

Der Begriff „Web Components“ ist breiter als die hier dokumentierte WHATWG-Custom-Elements-Feature-Familie.

Diese Datei behandelt insbesondere die WHATWG-definierten Custom-Element-Mechanismen.

Nicht automatisch Bestandteil dieser Datei sind sämtliche Technologien, die allgemein unter „Web Components“ zusammengefasst werden.

Dazu können beispielsweise gehören:

- Shadow DOM als eigenständige DOM-Feature-Familie
- HTML Templates als eigenständige HTML-Funktion
- CSS Shadow Parts
- Constructable Stylesheets
- externe Bibliotheken und Frameworks

Wenn solche Features für andere ZE-WebLab-Dateien relevant sind, werden sie dort eigenständig behandelt.

---

## Fachliche Sonderregeln

### Custom Element Name ist nicht gleich Tag-Inventar

Custom Element Names sind autorendefinierte Namen.

Es existiert deshalb keine endliche WHATWG-Liste aller möglichen Custom Elements.

Die Spezifikation definiert stattdessen Regeln für zulässige Namen.

### Autonomous Custom Elements sind semantisch neutral

Ein Name wie:

`my-button`

verleiht dem Element nicht automatisch die Semantik eines Buttons.

Die Semantik muss durch die konkrete Implementierung und gegebenenfalls Accessibility-Semantik bereitgestellt werden.

### Customized Built-In Elements behalten native Semantik

Ein Customized Built-In Element erweitert ein natives Element.

Dadurch bleiben die nativen Eigenschaften und Verhaltensweisen des Basiselements erhalten.

### `is` ist zustandsbezogen

Eine spätere Änderung des `is`-Attributs ändert nicht das bereits bestimmte Custom-Element-Verhalten des Elements.

### Upgrade ist nicht dasselbe wie Erstellung

Ein Element kann:

1. zunächst als nicht-custom Element entstehen,
2. später eine Definition erhalten,
3. anschließend upgraded werden.

Damit sind Creation und Upgrade zwei unterschiedliche Verarbeitungsvorgänge.

### Constructor und Lifecycle sind getrennt

Der Constructor ist nicht als Ersatz für Lifecycle Callbacks gedacht.

Insbesondere DOM-abhängige Arbeiten sollen nicht unzulässig in den Constructor verlagert werden.

### Reactions sind keine beliebigen synchronen Callback-Aufrufe

Die WHATWG definiert hierfür eigene Queues und Stacks.

Die genaue Reihenfolge der Reactions ist Teil des normativen Processing Models.

---

## Offene Punkte

### Keine offenen normativen Lücken innerhalb von §4.13 festgestellt

Der abgegrenzte WHATWG-Bereich §4.13 wurde vollständig geprüft.

Für die hier dokumentierte Feature-Familie wurden keine offenen Punkte festgestellt, die eine normative Definition in dieser Datei verhindern.

### Abgrenzung zu Shadow DOM

Shadow DOM ist eine eigenständige DOM-Feature-Familie.

Die Custom-Elements-Spezifikation verweist jedoch auf Shadow Roots und stellt über `ElementInternals.shadowRoot` einen direkten Integrationspunkt bereit.

Eine spätere eigenständige Shadow-DOM-Datei sollte diese Beziehung über Querverweise dokumentieren.

### Abgrenzung zu CSS

`:state()` ist ein CSS-Integrationspunkt.

Die HTML-Spezifikation definiert die Custom-State-Seite, während die vollständige Selektorsemantik dem zuständigen CSS-Standard zugeordnet ist.

### Abgrenzung zu ARIA

Die HTML-Spezifikation definiert die Integration über `ElementInternals` und verweist für ARIA-Semantik auf die zuständigen externen Spezifikationen.

Eine vollständige ARIA-Referenz ist daher nicht Bestandteil dieser Datei.

### Abgrenzung zu DOM

Ein erheblicher Teil der Custom-Element-Infrastruktur ist mit der DOM-Spezifikation verzahnt.

Diese Datei dokumentiert die HTML-spezifische Custom-Element-Systematik und ersetzt keine vollständige DOM-Referenz.

---

## Prüfstatus

| Prüfbereich | Status |
|---|---|
| §4.13 Custom elements | geprüft |
| §4.13.1 Introduction | geprüft |
| §4.13.1.1 Autonomous Custom Elements | geprüft |
| §4.13.1.2 Form-associated Custom Elements | geprüft |
| §4.13.1.3 Accessibility | geprüft |
| §4.13.1.4 Customized Built-In Elements | geprüft |
| §4.13.1.5 Drawbacks | geprüft |
| §4.13.1.6 Upgrades | geprüft |
| §4.13.1.7 Scoped Registries | geprüft |
| §4.13.1.8 Custom States | geprüft |
| §4.13.2 Constructor Requirements | geprüft |
| §4.13.2.1 State-preserving Moves | geprüft |
| §4.13.3 Core Concepts | geprüft |
| §4.13.4 CustomElementRegistry | geprüft |
| §4.13.5 Upgrades | geprüft |
| §4.13.6 Custom Element Reactions | geprüft |
| `[CEReactions]` | geprüft |
| §4.13.7 Element Internals | geprüft |
| §4.13.7.1 ElementInternals | geprüft |
| §4.13.7.2 Shadow Root Access | geprüft |
| §4.13.7.3 Form-associated Custom Elements | geprüft |
| §4.13.7.4 Accessibility Semantics | geprüft |
| §4.13.7.5 Custom State Pseudo-class | geprüft |
| Content Categories | Querverweis geprüft |
| Content Models | Querverweis geprüft |
| Global Attributes / `is` | Querverweis geprüft |
| Forms | Querverweis geprüft |
| DOM / Registry | geprüft |
| Parsing-Beziehungen | geprüft |
| Sanitization | geprüft |
| Accessibility | geprüft |
| V1-Abgrenzung | geprüft |

---

## Quellen / Referenzen

### Normative Primärquelle

**WHATWG HTML Living Standard**

Relevanter Bereich:

- §4.13 Custom elements
- §4.13.1 Introduction
- §4.13.2 Requirements for custom element constructors and reactions
- §4.13.3 Core concepts
- §4.13.4 The `CustomElementRegistry` interface
- §4.13.5 Upgrades
- §4.13.6 Custom element reactions
- §4.13.7 Element internals

Stand der Recherche:

- 11. August 2026

### Projektquelle

**ZE-WebLab**

Repository:

- `z-evolutions/ze-weblab`
- Branch: `main`

Berücksichtigte bestehende Dokumente:

- `docs/html/10-forms.md`
- `docs/html/13-global-attributes.md`
- `docs/html/14-content-categories.md`
- `docs/html/15-content-models.md`
- `docs/html/16-link-types.md`

### Weitere normative Bezüge

Für einzelne Teilaspekte verweist die WHATWG-Spezifikation insbesondere auf:

- DOM Standard
- Web IDL
- ARIA / Accessibility-Spezifikationen
- SVG
- MathML
- CSS Selectors beziehungsweise CSS-Pseudo-Class-Spezifikationen

Diese externen Standards werden nicht als WHATWG-Definitionen behandelt.

---

## Zusammenfassung des Feature-Status

| Feature-Familie | WHATWG | ZE-WebLab-Ebene | Status |
|---|---|---|---|
| Custom Elements | definiert | Rechercheebene 2 | dokumentiert |
| Autonomous Custom Elements | definiert | Rechercheebene 2 | dokumentiert |
| Customized Built-In Elements | definiert | Rechercheebene 2 | dokumentiert |
| Custom Element Names | normativ definiert | Rechercheebene 2 | dokumentiert |
| CustomElementRegistry | definiert | Rechercheebene 2 | dokumentiert |
| Scoped Registries | definiert | Rechercheebene 2 | dokumentiert |
| Upgrades | normativ definiert | Rechercheebene 2 | dokumentiert |
| Custom Element Reactions | normativ definiert | Rechercheebene 2 | dokumentiert |
| `[CEReactions]` | normativ definiert | Rechercheebene 2 | dokumentiert |
| ElementInternals | definiert | Rechercheebene 2 | dokumentiert |
| Form-associated Custom Elements | definiert | Rechercheebene 2 | dokumentiert |
| Accessibility Semantics | HTML-Integration definiert | Rechercheebene 2 | dokumentiert |
| Custom States | definiert | Rechercheebene 2 | dokumentiert |
| `:state()` | CSS-Integration | Rechercheebene 2 | dokumentiert |
| `is` | globales Attribut + Custom-Element-Integration | 13 + 17 | Querverweis |
| `extends` | API-Definitionsoption | Rechercheebene 2 | dokumentiert |

## Abschluss

Diese Datei behandelt Custom Elements als eigenständige übergreifende Feature-Familie.

Sie zählt weder Custom Element Names noch Custom Element APIs noch Lifecycle Callbacks als zusätzliche native HTML-Elemente.

Die Datei bildet die aktuelle WHATWG-Systematik von §4.13 ab und trennt dabei:

- native Elemente
- autorendefinierte Custom Elements
- Attribute
- DOM Interfaces
- APIs
- Processing Models
- Lifecycle Reactions
- Form Integration
- Accessibility Integration
- CSS Integration

voneinander.