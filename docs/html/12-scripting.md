# ZE-WebLab – HTML-Referenz: Scripting

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab  
**Datei:** `docs/html/12-scripting.md`  
**Themenbereich:** HTML Scripting  
**WHATWG-Bereich:** §4.12 Scripting  
**Primärquelle:** WHATWG HTML Living Standard  
**Geprüfter Spezifikationsstand:** Living Standard, 11. August 2026

Diese Datei dokumentiert den WHATWG-Bereich §4.12 „Scripting“ auf Ebene der
HTML-Elemente und der zugehörigen normativen Konzepte.

Dabei werden HTML-Elemente, Attribute, Processing Models, DOM-Interfaces,
Rendering-APIs und sonstige Unterkonzepte bewusst getrennt behandelt.

### HTML-Elementinventar dieses Bereichs

§4.12 definiert bzw. behandelt folgende HTML-Elemente:

- `script`
- `noscript`
- `template`
- `slot`
- `canvas`

Diese fünf Elemente bilden das Elementinventar dieses Themenblocks.

Nicht als zusätzliche HTML-Elemente gezählt werden insbesondere:

- klassische Scripts
- JavaScript Module
- Import Maps
- Speculation Rules
- Data Blocks
- Script Processing Model
- Scripting Modes
- Canvas Rendering Contexts
- `CanvasRenderingContext2D`
- `ImageBitmapRenderingContext`
- `OffscreenCanvas`
- WebGL-/WebGPU-Rendering-Kontexte
- Template Contents
- Shadow Roots
- Slot Assignment
- `Path2D`
- Canvas-Mixins
- sonstige in §4.12 definierte APIs, Dictionaries, Enums, Typedefs,
  Algorithmen und Verarbeitungsmodelle

Diese sind eigenständige Konzepte bzw. API-Ebenen und werden in dieser Datei
als solche dokumentiert.

---

## WHATWG-Struktur

Der aktuelle WHATWG-Bereich ist wie folgt gegliedert:

### 4.12 Scripting

Grundlagen und allgemeine Anforderungen an Scripting.

### 4.12.1 The `script` element

#### 4.12.1.1 Processing model

Verarbeitungsmodell des `script`-Elements einschließlich Parser-Integration,
Script-Vorbereitung, Fetching, Ausführung und Ausführungsreihenfolge.

#### 4.12.1.2 Scripting languages

Regeln für Script-Sprachen und insbesondere JavaScript.

#### 4.12.1.3 Restrictions for contents of `script` elements

Besondere Einschränkungen des Inhalts von `script`-Elementen aufgrund des
historischen HTML-Parsing-Modells.

#### 4.12.1.4 Inline documentation for external scripts

Regeln für Dokumentationsinhalt innerhalb eines `script`-Elements, wenn
gleichzeitig `src` verwendet wird.

#### 4.12.1.5 Interaction of `script` elements and XSLT

Nicht-normativer Abschnitt zu XSLT und `script`.

### 4.12.2 The `noscript` element

Fallback- und Parsing-Verhalten abhängig vom Scripting-Zustand.

### 4.12.3 The `template` element

Declarative Template Contents sowie deklarative Shadow Roots.

#### 4.12.3.1 Interaction of `template` elements with XSLT and XPath

Nicht-normativer Abschnitt zu XSLT und XPath.

### 4.12.4 The `slot` element

Shadow-DOM-Slot und Slot Assignment.

### 4.12.5 The `canvas` element

Bitmap-basierte Zeichenfläche und zugehörige Rendering-APIs.

Unter diesem Abschnitt liegen umfangreiche API- und Rendering-Unterbereiche,
die nicht als zusätzliche HTML-Elemente zu inventarisieren sind.

---

# Inventar

| Feature | WHATWG-Abschnitt | Feature-Typ | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| `script` | §4.12.1 | HTML-Element | Metadata, Flow, Phrasing, Script-supporting | Metadata, Phrasing oder Script-supporting Content je nach Kontext | abhängig von `src` und `type`; bei externen Scripts leer oder Script-Dokumentation | keine Auslassung | Global + `type`, `src`, `nomodule`, `async`, `defer`, `blocking`, `crossorigin`, `referrerpolicy`, `integrity`, `fetchpriority` | Unsafe | `HTMLScriptElement` | Im WHATWG-Standard definiert |
| `noscript` | §4.12.2 | HTML-Element | Metadata, Flow, Phrasing | abhängig von Position, Scripting-Zustand und HTML-Kontext | abhängig von Scripting-Zustand und Position | keine Auslassung | Global Attributes | Uncategorized | `HTMLElement` | Im WHATWG-Standard definiert |
| `template` | §4.12.3 | HTML-Element | Metadata, Flow, Phrasing, Script-supporting | Metadata, Phrasing, Script-supporting; zusätzlich als Kind von geeignetem `colgroup` | `Nothing` | keine Auslassung | Global + `shadowrootmode`, `shadowrootdelegatesfocus`, `shadowrootslotassignment`, `shadowrootclonable`, `shadowrootserializable`, `shadowrootcustomelementregistry` | Uncategorized | `HTMLTemplateElement` | Im WHATWG-Standard definiert |
| `slot` | §4.12.4 | HTML-Element | Flow, Phrasing | Wo Phrasing Content erwartet wird | Transparent | keine Auslassung | Global + `name` | Uncategorized | `HTMLSlotElement` | Im WHATWG-Standard definiert |
| `canvas` | §4.12.5 | HTML-Element | Flow, Phrasing, Embedded, Palpable | Wo Embedded Content erwartet wird | Transparent mit Einschränkungen für Interactive Content | keine Auslassung | Global + `width`, `height` | Uncategorized | `HTMLCanvasElement` | Im WHATWG-Standard definiert |

---

# Detailprüfung: `script`

## WHATWG-Zuordnung

`script` ist in §4.12.1 definiert.

Das Element dient zum Einbinden von dynamischem Script, Anweisungen für
User Agents sowie bestimmten Datenblöcken.

Das Element repräsentiert selbst keinen für den Benutzer dargestellten
Inhalt.

## Content Categories

WHATWG führt für `script` folgende Kategorien auf:

- Metadata content
- Flow content
- Phrasing content
- Script-supporting element

## Context

`script` darf verwendet werden:

- wo Metadata Content erwartet wird,
- wo Phrasing Content erwartet wird,
- wo Script-supporting Elements erwartet werden.

Damit ist `script` nicht auf einen einzigen Dokumentbereich beschränkt.

## Content Model

Das Content Model hängt vom Vorhandensein von `src` und vom `type`-Wert ab.

Ohne `src` hängt der zulässige Inhalt vom `type`-Wert ab und muss zusätzlich
den besonderen Script-Content-Restrictions entsprechen.

Mit `src` muss das Element entweder leer sein oder ausschließlich
Script-Dokumentation enthalten, die ebenfalls die entsprechenden
Content-Restrictions erfüllt.

## Tag Omission

Für `script` ist weder das Start- noch das End-Tag auslassbar.

## Content Attributes

Neben den Global Attributes definiert `script`:

### `type`

Bestimmt den Typ des enthaltenen Scripts bzw. Datenblocks.

WHATWG unterscheidet insbesondere:

- fehlendes `type` bzw. leerer Wert oder JavaScript-MIME-Type-Essence-Match:
  Classic Script
- `module`: JavaScript Module Script
- `importmap`: Import Map
- `speculationrules`: Speculation Rules
- sonstiger gültiger MIME-Type: Data Block

Ein beliebiger Nicht-MIME-String darf nicht einfach als Data-Block-Typ
verwendet werden.

### `src`

Bezeichnet die externe Ressource.

`src` darf nur für Classic Scripts und JavaScript Module Scripts verwendet
werden.

Bei Verwendung muss der Wert eine gültige, nicht-leere URL sein, die
gegebenenfalls von Leerraum umgeben sein darf.

### `nomodule`

Boolean Attribute.

Es verhindert die Ausführung des Scripts in User Agents, die Module Scripts
unterstützen.

Dadurch kann ein Classic-Script-Fallback für ältere User Agents zusammen
mit einem Module Script eingesetzt werden.

### `async`

Boolean Attribute.

Bei externen Classic Scripts führt `async` dazu, dass das Script parallel
zum Parsing geladen und ausgeführt wird, sobald es verfügbar ist.

Bei Module Scripts führt `async` dazu, dass das Modul und seine
Abhängigkeiten parallel zum Parsing geladen und das Modul ausgeführt wird,
sobald es verfügbar ist.

### `defer`

Boolean Attribute.

Bei externen Classic Scripts führt `defer` dazu, dass der Fetch parallel
zum Parsing stattfindet und die Ausführung nach Abschluss des Parsings
erfolgt.

Bei Module Scripts hat `defer` keine Wirkung.

### `blocking`

Bezeichnet, ob das Element potentiell render-blocking ist.

Das Attribut ist ein Blocking Attribute.

### `crossorigin`

CORS Settings Attribute.

Bei externen Classic Scripts steuert es insbesondere die Behandlung von
Fehlerinformationen bei Cross-Origin-Ressourcen.

Bei externen Module Scripts beeinflusst es die Credentials Mode des
entsprechenden Fetch-Vorgangs.

Für Module Scripts ist Cross-Origin-Fetching an das CORS-Protokoll gebunden.

### `referrerpolicy`

Referrer Policy Attribute.

Es bestimmt die Referrer Policy für den initialen Fetch eines externen
Scripts sowie für den Fetch importierter Module.

### `integrity`

Enthält Integrity Metadata für Subresource Integrity.

### `fetchpriority`

Setzt die Fetch-Priorität für durch das Element ausgelöste Fetch-Vorgänge.

Die WHATWG-Spezifikation weist ausdrücklich darauf hin, dass `fetchpriority`
bei Inline Scripts nicht die Fetch-Vorgänge von Module Imports beeinflusst.

## Script-Typen

Das `script`-Element kann im aktuellen WHATWG-Modell unter anderem folgende
Script-/Datenformen repräsentieren:

- Classic Script
- JavaScript Module Script
- Import Map
- Speculation Rule Set
- Data Block

Diese sind keine zusätzlichen HTML-Elemente.

---

# `script` – Processing Model

Das Processing Model ist ein eigenständiges normatives Unterkonzept und
wird nicht als Element gezählt.

Ein `script`-Element besitzt unter anderem Zustandsinformationen für:

- Parser Document
- Preparation-Time Document
- Force Async
- From an External File
- Ready to Be Parser-Executed
- Already Started
- Delaying the Load Event
- Script Type
- Script Result
- weitere interne Verarbeitungszustände

Die Vorbereitung eines Scripts ist eng mit HTML Parsing, XML Parsing,
Fetching und Script Execution verbunden.

## Parser-inserted Scripts

Ein vom Parser eingefügtes `script`-Element kann besondere Beziehungen
zum Parser Document und zur Parser-Ausführung besitzen.

Das Processing Model unterscheidet insbesondere:

- parser-blockierende Scripts,
- Scripts, die so bald wie möglich ausgeführt werden,
- Scripts, die in einer bestimmten Reihenfolge ausgeführt werden,
- Scripts, die nach Abschluss des Dokument-Parsings ausgeführt werden.

## Classic Scripts

Für externe Classic Scripts gelten grundsätzlich folgende Modi:

- ohne `async` und `defer`: Fetch und Ausführung blockieren den Parser,
- mit `defer`: Fetch parallel zum Parsing, Ausführung nach Parsing,
- mit `async`: Fetch parallel zum Parsing, Ausführung sobald verfügbar.

## Module Scripts

Module Scripts werden grundsätzlich nach dem Module-Script-Processing-Modell
behandelt.

Ohne `async` entsprechen sie hinsichtlich der zeitlichen Ausführung
grundsätzlich dem defer-artigen Verhalten.

Mit `async` können sie ausgeführt werden, sobald Modul und Abhängigkeiten
bereit sind.

Das `defer`-Attribut hat auf Module Scripts keine Wirkung.

## Dynamisch eingefügte Scripts

Die Spezifikation unterscheidet parser-inserted Scripts und Scripts, die
beispielsweise per DOM-API eingefügt werden.

Für dynamisch eingefügte externe Scripts existiert ein eigenes
Ausführungsreihenfolge-Modell.

## `document.write()`

Über `document.write()` eingefügte `script`-Elemente können typischerweise
ausgeführt werden und dabei weitere Script-Ausführung oder HTML-Parsing
blockieren.

## `innerHTML` und `outerHTML`

`script`-Elemente, die über `innerHTML` oder `outerHTML` eingefügt werden,
werden nicht einfach dadurch ausgeführt.

Das ist eine wichtige normative Unterscheidung gegenüber
parser-inserted Scripts und `document.write()`.

---

# `script` – Scripting Languages

Die WHATWG-Spezifikation behandelt JavaScript als die relevante
Script-Sprache für das definierte Processing Model.

User Agents sind nicht verpflichtet, JavaScript zu unterstützen.

Die aktuelle Spezifikation definiert das Script Processing Model jedoch
nicht als allgemeines Mehrsprachenmodell.

Für JavaScript-Ressourcen sollen Server `text/javascript` verwenden.

Nicht-JavaScript-MIME-Typen dürfen nicht als JavaScript-Ressourcen
verwendet werden.

Für externe Ressourcen sind MIME-Type-Parameter grundsätzlich vom
Ressourcen-Fetch zu unterscheiden; beim `type`-Attribut des
`script`-Elements ist insbesondere der JavaScript MIME Type Essence Match
relevant.

---

# `script` – Content Restrictions

Die Inhalte von `script`-Elementen unterliegen besonderen
Parsing-Beschränkungen.

Historisch bedingt behandelt der HTML-Parser bestimmte Sequenzen innerhalb
von Script-Blöcken speziell.

Besonders relevant sind ASCII-case-insensitive Vorkommen von:

- `<!--`
- `<script`
- `</script`

Die Spezifikation empfiehlt, problematische Sequenzen in Script-Literalen
entsprechend zu escapen, beispielsweise durch die Verwendung von
`\x3C`.

Die Regeln sind nicht bloß JavaScript-Syntaxregeln, sondern ergeben sich
aus dem Zusammenspiel von HTML-Parsing und Script-Inhalten.

---

# `script` – Inline Documentation

Wenn `src` vorhanden ist, darf der Inhalt eines `script`-Elements nur
bestimmte Dokumentationsinhalte enthalten.

Die Spezifikation definiert dafür eine ABNF-Produktion namens
`documentation`.

Die Dokumentation besteht aus Leerraum, Tabs, Kommentaren,
Zeilenkommentaren und Zeilenumbrüchen.

Damit soll verhindert werden, dass neben einer externen Ressource
versehentlich ausführbarer Script-Code im Elementinhalt steht.

---

# `script` – XSLT

§4.12.1.5 ist ausdrücklich nicht-normativ.

WHATWG definiert dort nicht allgemein, wie XSLT mit `script` interagiert.

Es werden lediglich Implementierungsrichtlinien beschrieben, unter anderem
für:

- durch XSLT erzeugte `script`-Elemente,
- `XSLTProcessor.transformToDocument()`,
- `XSLTProcessor.transformToFragment()`.

Dieser Abschnitt ist deshalb als Querverweis-/Implementierungsinformation
zu behandeln und nicht als zusätzliche HTML-Elementdefinition.

---

# Detailprüfung: `noscript`

## WHATWG-Zuordnung

`noscript` ist in §4.12.2 definiert.

Das Element dient dazu, unterschiedliche Inhalte abhängig vom
Scripting-Zustand bzw. vom Parsing-Verhalten bereitzustellen.

## Content Categories

WHATWG führt auf:

- Metadata content
- Flow content
- Phrasing content

## Context

`noscript` kann abhängig vom Kontext insbesondere verwendet werden:

- innerhalb eines `head` eines HTML-Dokuments, wenn kein `noscript`-Vorfahre
  vorhanden ist,
- dort, wo Phrasing Content erwartet wird, wenn die entsprechenden
  Bedingungen erfüllt sind,
- als Nachfahre von `select` oder `optgroup` unter den in der Spezifikation
  definierten Bedingungen.

## Content Model

Das Content Model ist abhängig von Position und Scripting-Zustand.

### Im `head`, Scripting deaktiviert

Zulässig sind:

- `link`
- `style`
- `meta`

in beliebiger Reihenfolge und Anzahl innerhalb der entsprechenden Regeln.

### Im `head`, Scripting aktiviert

Der Inhalt muss Text sein.

Dieser Text muss so beschaffen sein, dass die Anwendung des
HTML-Fragment-Parsing-Algorithmus im entsprechenden Kontext ausschließlich
konforme `link`-, `style`- und `meta`-Elemente erzeugt und keine Parse Errors
auftreten.

### Außerhalb von `head`, Scripting deaktiviert

Das Content Model ist transparent.

Zusätzlich darf kein `noscript`-Element als Vorfahre vorhanden sein.

### Außerhalb von `head`, Scripting aktiviert

Der Inhalt muss Text sein.

Für diesen Text gelten zusätzliche Anforderungen, die durch einen
Algorithmus geprüft werden.

Insbesondere muss die Transformation zu einem konformen Dokument ohne
`noscript`- und `script`-Elemente führen.

## Tag Omission

Weder Start- noch End-Tag von `noscript` sind auslassbar.

## Content Attributes

`noscript` besitzt keine eigenen Content Attributes.

Es gelten die Global Attributes.

## XML

`noscript` darf nicht in XML-Dokumenten verwendet werden.

Das Element ist nur in der HTML-Syntax wirksam.

In XML existiert das entsprechende Parsing-Verhalten nicht.

## Darstellung

Bei aktiviertem Scripting repräsentiert `noscript` nichts.

Bei deaktiviertem Scripting repräsentiert es seine zulässigen Inhalte.

Damit ist `noscript` nicht einfach ein normales Container-Element; seine
Bedeutung ist unmittelbar mit dem Parsing- und Scripting-Modell verbunden.

---

# Detailprüfung: `template`

## WHATWG-Zuordnung

`template` ist in §4.12.3 definiert.

Das Element dient zur Deklaration von HTML-Fragmenten, die später per Script
geklont und in ein Dokument eingefügt werden können.

## Content Categories

WHATWG führt auf:

- Metadata content
- Flow content
- Phrasing content
- Script-supporting element

## Context

`template` kann verwendet werden:

- wo Metadata Content erwartet wird,
- wo Phrasing Content erwartet wird,
- wo Script-supporting Elements erwartet werden,
- als Kind eines `colgroup`, das kein `span`-Attribut besitzt.

## Content Model

Das Content Model des `template`-Elements ist ausdrücklich:

`Nothing`

Das ist eine wichtige Besonderheit.

Die sichtbare Template-Struktur im HTML-Quelltext befindet sich nicht als
normale Kindstruktur des `template`-Elements im DOM.

Sie wird als Template Contents in einem separaten `DocumentFragment`
gespeichert.

## Tag Omission

Weder Start- noch End-Tag sind auslassbar.

## Content Attributes

Neben den Global Attributes besitzt `template`:

### `shadowrootmode`

Enumerated Attribute.

Bekannte Zustände:

- `open`
- `closed`

Die Zustände bestimmen, ob ein deklarativer Shadow Root offen oder
geschlossen erzeugt wird.

Missing Value Default und Invalid Value Default sind `None`.

### `shadowrootdelegatesfocus`

Boolean Attribute.

Steuert `delegatesFocus` eines deklarativen Shadow Roots.

### `shadowrootslotassignment`

Enumerated Attribute.

Bekannte Zustände:

- `named`
- `manual`

Der Missing Value Default und Invalid Value Default ist `named`.

### `shadowrootclonable`

Boolean Attribute.

Steuert, ob der deklarative Shadow Root beim Klonen entsprechend
behandelt werden kann.

### `shadowrootserializable`

Boolean Attribute.

Steuert die Serialisierbarkeit des deklarativen Shadow Roots.

### `shadowrootcustomelementregistry`

Boolean Content Attribute.

Gibt an, dass ein deklarativer Shadow Root eine Custom Element Registry
verwenden soll.

## Template Contents

Die Template Contents sind nicht die normalen Child Nodes des
`template`-Elements.

Ein `template`-Element besitzt ein zugeordnetes `DocumentFragment`.

Dieses `DocumentFragment` stellt die Template Contents dar.

Die Template Contents besitzen keine eigenen Conformance Requirements
als normale Kinder des `template`-Elements.

## Inert Template Document

Template Contents werden über ein geeignetes Template-Contents-Owner-Document
verwaltet.

Für normale Dokumente wird dafür ein inert Template Document verwendet.

Dadurch befinden sich Template Contents nicht in einem Browsing Context und
bleiben inert.

Insbesondere werden Scripts innerhalb der Template Contents nicht einfach
bei der Erstellung des Templates ausgeführt.

## DOM-Manipulation

Die Spezifikation unterscheidet das `template`-Element selbst von seinen
Template Contents.

DOM-Manipulationen am `template`-Element und Manipulationen an
`template.content` sind daher nicht gleichwertig.

Das Einfügen normaler Child Nodes direkt in ein `template`-Element kann
aufgrund des Content Models konformitätswidrig sein.

## Declarative Shadow Roots

Das aktuelle `template`-Modell enthält zusätzlich die Attribute für
deklarative Shadow Roots.

Damit verbindet §4.12.3 das Template-Modell mit:

- Shadow DOM,
- Slot Assignment,
- Cloning,
- Serialisierung,
- Custom Element Registries.

Diese sind Unterkonzepte des Template-/Shadow-DOM-Modells und keine
zusätzlichen HTML-Elemente.

---

# `template` – XSLT und XPath

§4.12.3.1 ist nicht-normativ.

WHATWG definiert dort nicht abschließend die Interaktion von XSLT und XPath
mit Template Elements.

Die angegebenen Richtlinien betreffen insbesondere:

- XSLT-Transformationen,
- DOM-Ausgabe durch XSLT,
- Template Contents,
- XPath-Auswertung.

Diese Informationen sind als Implementierungs-/Querverweisinformation
zu behandeln.

---

# Detailprüfung: `slot`

## WHATWG-Zuordnung

`slot` ist in §4.12.4 definiert.

Das Element definiert einen Slot innerhalb eines Shadow Trees.

## Content Categories

WHATWG führt auf:

- Flow content
- Phrasing content

## Context

`slot` darf verwendet werden, wo Phrasing Content erwartet wird.

## Content Model

Das Content Model ist:

Transparent.

## Tag Omission

Weder Start- noch End-Tag sind auslassbar.

## Content Attributes

Neben den Global Attributes besitzt `slot`:

### `name`

Der Wert kann beliebige Strings enthalten.

Er definiert den Namen des Slots.

Ein Element kann einem benannten Slot zugeordnet werden, wenn sein
`slot`-Attribut mit dem Namen des entsprechenden `slot`-Elements
übereinstimmt und die übrigen Shadow-Tree-Zuordnungsregeln erfüllt sind.

## Repräsentation

Ein `slot` repräsentiert:

- seine zugewiesenen Nodes, wenn solche vorhanden sind,
- andernfalls seinen eigenen Inhalt.

Damit ist die Darstellung eines Slots vom Ergebnis des Slot-Assignment-
Algorithmus abhängig.

---

# `slot` – DOM Interface

Das DOM Interface lautet:

`HTMLSlotElement`

Wesentliche Mitglieder sind:

- `name`
- `assignedNodes()`
- `assignedElements()`
- `assign()`

### `name`

Liest oder setzt den Namen des Slots.

### `assignedNodes()`

Gibt die dem Slot zugewiesenen Nodes zurück.

### `assignedNodes({ flatten: true })`

Gibt bei vorhandener Zuordnung die zugewiesenen Nodes zurück und
berücksichtigt ansonsten die Fallback-Kinder.

Die Auflösung wird für darin auftretende Slots rekursiv fortgeführt.

### `assignedElements()`

Gibt die zugewiesenen Element-Nodes zurück.

### `assign()`

Ermöglicht die manuelle Zuordnung von Element- oder Text-Nodes gemäß dem
definierten Slot-Assignment-Modell.

---

# Detailprüfung: `canvas`

## WHATWG-Zuordnung

`canvas` ist in §4.12.5 definiert.

Der Abschnitt enthält neben dem HTML-Element eine sehr umfangreiche
API- und Rendering-Spezifikation.

## Content Categories

WHATWG führt auf:

- Flow content
- Phrasing content
- Embedded content
- Palpable content

## Context

`canvas` darf verwendet werden, wo Embedded Content erwartet wird.

## Content Model

Das Content Model ist transparent, jedoch mit einer wesentlichen
Einschränkung:

Es darf grundsätzlich kein Interactive Content als Nachfahre enthalten
sein, außer den ausdrücklich erlaubten Fällen.

Die WHATWG-Ausnahme umfasst insbesondere:

- `a`
- `img` mit `usemap`
- `button`
- `input` im Checkbox- oder Radio-Button-State
- `input`, das als Button gilt
- `select` mit `multiple`
- `select` mit Display Size größer als 1

## Tag Omission

Weder Start- noch End-Tag sind auslassbar.

## Content Attributes

Neben den Global Attributes:

### `width`

Horizontale Dimension der Bitmap.

Der Wert muss ein gültiger nicht-negativer Integer sein.

Default:

`300`

### `height`

Vertikale Dimension der Bitmap.

Der Wert muss ein gültiger nicht-negativer Integer sein.

Default:

`150`

## Fallback Content

Der Inhalt eines `canvas`-Elements ist Fallback Content.

Autoren müssen bei Verwendung von `canvas` zusätzlich Inhalte bereitstellen,
die bei Darstellung für den Benutzer im Wesentlichen dieselbe Funktion oder
denselben Zweck vermitteln wie die Bitmap.

Die Fallback-Inhalte sind deshalb ein wesentlicher Bestandteil der
Zugänglichkeits- und Konformitätsbetrachtung.

## Repräsentation

Die Repräsentation des `canvas`-Elements hängt vom Medium, vom
Scripting-Zustand, vom Support für Canvas und vom Vorhandensein eines
Rendering Contexts ab.

In interaktiven visuellen Medien kann die Bitmap repräsentiert werden.

In nicht-visuellen Medien oder bei deaktiviertem Canvas/Scripting wird
stattdessen der Fallback Content repräsentiert.

Bei statischen visuellen Medien kann ein zuvor erzeugter Bitmap-Zustand
weiter repräsentiert werden.

## Accessibility-relevante Fallback-Regel

Wenn Canvas als Embedded Content repräsentiert wird, können Nachfahren aus
dem Fallback Content weiterhin fokussiert werden.

Dadurch kann eine interaktive Canvas-Anwendung über zugängliche
Fallback-Strukturen Tastaturinteraktion ermöglichen.

Die WHATWG-Spezifikation empfiehlt eine Eins-zu-eins-Zuordnung zwischen
interaktiven Bereichen des Canvas und fokussierbaren Bereichen des
Fallback Contents.

## Canvas Bitmap

Die Bitmap besitzt eine Auflösung, die über `width` und `height` bestimmt
wird.

Die Standardgröße beträgt:

- 300 × 150 Pixel.

CSS kann die Darstellung unabhängig von der Bitmap-Größe skalieren.

Die natürliche Größe der Bitmap entspricht der Bitmap-Größe.

## Canvas Context Modes

Ein Canvas besitzt ein internes Context Mode-Konzept.

Die Spezifikation unterscheidet unter anderem:

- `none`
- `placeholder`
- `2d`
- `bitmaprenderer`
- `webgl`
- `webgl2`
- `webgpu`

Diese Werte sind keine HTML-Elemente.

Sie beschreiben den Zustand des Canvas-Rendering-Modells.

---

# Canvas APIs und Unterkonzepte

Der Abschnitt §4.12.5 enthält umfangreiche API-Definitionen.

Diese werden ausdrücklich nicht in das HTML-Elementinventar aufgenommen.

Dazu gehören unter anderem:

- `CanvasRenderingContext2D`
- `ImageBitmapRenderingContext`
- `OffscreenCanvas`
- `Path2D`
- WebGL Rendering Contexts
- WebGL2 Rendering Contexts
- GPU Canvas Context
- Canvas Settings
- Canvas State
- Canvas Transform
- Canvas Compositing
- Canvas Image Smoothing
- Canvas Fill/Stroke Styles
- Canvas Shadow Styles
- Canvas Filters
- Canvas Rect
- Canvas Draw Path
- Canvas User Interface
- Canvas Text
- Canvas Draw Image
- Canvas Image Data
- Canvas Path Drawing Styles
- Canvas Text Drawing Styles
- Canvas Path

Diese Konzepte gehören zur API-/Processing-Ebene.

---

# Canvas Rendering Contexts

## 2D Rendering Context

§4.12.5.1 definiert den 2D Rendering Context.

Das zugehörige Interface ist:

`CanvasRenderingContext2D`

Es umfasst zahlreiche Zeichen-, Transformations-, Text-, Pfad-,
Bild-, Pixel-, Compositing- und Zustandsoperationen.

## ImageBitmap Rendering Context

§4.12.5.2 behandelt den `ImageBitmap` Rendering Context.

Das zugehörige Interface ist:

`ImageBitmapRenderingContext`

## OffscreenCanvas

§4.12.5.3 behandelt:

`OffscreenCanvas`

Dabei kann ein Canvas-Element durch
`transferControlToOffscreen()` mit einem OffscreenCanvas verbunden werden.

Das ursprüngliche Canvas-Element kann anschließend als Placeholder Canvas
dienen.

## Weitere Rendering-Technologien

Der Canvas-Bereich definiert bzw. referenziert außerdem:

- WebGL
- WebGL2
- WebGPU

Diese sind API-/Rendering-Technologien und keine zusätzlichen HTML-Elemente.

---

# Canvas Security

§4.12.5 enthält einen eigenen Abschnitt zur Sicherheit von Canvas-Elementen.

Von besonderer Bedeutung ist das `origin-clean`-Flag.

Bitmaps von Canvas-Elementen und bestimmte weitere Bitmaps besitzen ein
`origin-clean`-Flag.

Dieses ist initial `true`.

Durch bestimmte Cross-Origin-Ressourcen und die damit verbundenen
Sicherheitsregeln kann dieser Zustand verändert werden.

Das Canvas-API-Modell verhindert dadurch, dass aus nicht vertrauenswürdigen
Quellen stammende Bilddaten beliebig als Script-lesbare Pixelinformationen
ausgelesen werden können.

Die konkrete Sicherheitsprüfung ist Teil des Canvas-API-/Rendering-Modells
und kein eigenes HTML-Element.

---

# Gemeinsame / zugehörige Attribute

## `script`

Elementbezogene Content Attributes:

- `type`
- `src`
- `nomodule`
- `async`
- `defer`
- `blocking`
- `crossorigin`
- `referrerpolicy`
- `integrity`
- `fetchpriority`

## `noscript`

Keine eigenen Content Attributes.

Es gelten Global Attributes.

## `template`

Elementbezogene Content Attributes:

- `shadowrootmode`
- `shadowrootdelegatesfocus`
- `shadowrootslotassignment`
- `shadowrootclonable`
- `shadowrootserializable`
- `shadowrootcustomelementregistry`

## `slot`

Elementbezogenes Content Attribute:

- `name`

## `canvas`

Elementbezogene Content Attributes:

- `width`
- `height`

---

# Accessibility

Die WHATWG-Elementdefinitionen enthalten für die behandelten Elemente
Accessibility Considerations.

Für:

- `script`
- `noscript`
- `template`
- `slot`
- `canvas`

verweist die WHATWG-Spezifikation jeweils auf die einschlägigen
Accessibility Considerations für Autoren und Implementierer.

Die konkrete Accessibility-Ausarbeitung wird nicht vollständig durch
§4.12 selbst definiert.

Deshalb werden hier keine zusätzlichen ARIA-Rollen, States oder Properties
als vermeintliche WHATWG-Elementdefinitionen erfunden.

## Besonders relevante WHATWG-Aussagen

### `script`

`script` repräsentiert keinen Benutzerinhalt.

Seine Accessibility-Bedeutung besteht daher primär darin, dass es
Dokumentverhalten beeinflusst und nicht selbst als sichtbarer Inhalt
modelliert wird.

### `noscript`

Die repräsentierte Information hängt vom Scripting-Zustand ab.

### `template`

`template` repräsentiert in einer Darstellung nichts.

Die Template Contents sind für sich genommen inert.

### `slot`

Ein Slot repräsentiert seine zugewiesenen Nodes bzw. bei fehlender
Zuordnung seinen Fallback Content.

### `canvas`

Canvas benötigt ausdrücklich Fallback Content, der dieselbe wesentliche
Funktion oder denselben Zweck vermittelt.

Dies ist für die Accessibility-Betrachtung des Elements besonders wichtig.

---

# Sanitization

Die aktuelle WHATWG-Elementreferenz weist folgende Sanitization-Einstufungen
aus:

| Element | WHATWG Sanitization |
|---|---|
| `script` | Unsafe |
| `noscript` | Uncategorized |
| `template` | Uncategorized |
| `slot` | Uncategorized |
| `canvas` | Uncategorized |

## `script`

WHATWG klassifiziert `script` ausdrücklich als:

**Unsafe**

Das ist für die Sanitization-Ebene relevant.

`script` darf daher nicht als gewöhnliches, unkritisches Inhaltselement
behandelt werden.

## `noscript`

Die Elementreferenz führt:

**Uncategorized**

## `template`

Die Elementreferenz führt:

**Uncategorized**

## `slot`

Die Elementreferenz führt:

**Uncategorized**

## `canvas`

Die Elementreferenz führt:

**Uncategorized**

Die Sanitization-Klassifikation ist von der normalen HTML-Konformität und
vom Browser-Support zu unterscheiden.

---

# DOM Interfaces

## `script`

DOM Interface:

`HTMLScriptElement`

Wesentliche IDL-Mitglieder umfassen:

- `type`
- `src`
- `noModule`
- `async`
- `defer`
- `blocking`
- `crossOrigin`
- `referrerPolicy`
- `integrity`
- `fetchPriority`
- `text`
- `supports()`

Das Interface ist von `HTMLElement` abgeleitet.

## `noscript`

DOM Interface:

`HTMLElement`

WHATWG definiert für `noscript` kein eigenes spezialisiertes DOM Interface.

## `template`

DOM Interface:

`HTMLTemplateElement`

Wesentliche Mitglieder:

- `content`
- `shadowRootMode`
- `shadowRootDelegatesFocus`
- `shadowRootSlotAssignment`
- `shadowRootClonable`
- `shadowRootSerializable`
- `shadowRootCustomElementRegistry`

`content` liefert das zugehörige `DocumentFragment` mit den Template
Contents.

## `slot`

DOM Interface:

`HTMLSlotElement`

Wesentliche Mitglieder:

- `name`
- `assignedNodes()`
- `assignedElements()`
- `assign()`

## `canvas`

DOM Interface:

`HTMLCanvasElement`

Wesentliche Mitglieder:

- `width`
- `height`
- `getContext()`
- `toDataURL()`
- `toBlob()`
- `transferControlToOffscreen()`

Das Canvas-Interface steht in Beziehung zu mehreren Rendering-Context-
Interfaces.

---

# Normative Sonderregeln

## `script`

Besonders relevant:

- Script Processing ist abhängig von `type`, `src`, `async`, `defer`,
  Parser-Zustand und weiteren internen Zuständen.
- Classic und Module Scripts besitzen unterschiedliche Processing Models.
- `defer` wirkt nicht auf Module Scripts.
- `async` verändert die Ausführungsplanung.
- `nomodule` verhindert die Ausführung in Module-fähigen User Agents.
- `src` ist nur für Classic und Module Scripts zulässig.
- Inline Module Scripts unterliegen dem Module Processing Model.
- Import Maps und Speculation Rules werden über `script`-Elemente eingebettet,
  sind aber keine Script-Elemente im Sinne separater HTML-Tags.
- Data Blocks werden über `type` identifiziert und nicht vom User Agent als
  ausführbare Scripts verarbeitet.
- `script`-Inhalte unterliegen besonderen HTML-Parsing-Regeln.
- `innerHTML` und `outerHTML` führen nicht zur normalen Script-Ausführung.
- `document.write()` besitzt dagegen ein spezielles Script-Verhalten.

## `noscript`

Besonders relevant:

- Verhalten hängt vom Scripting-Zustand ab.
- Parsing unterscheidet zwischen `head` und Nicht-`head`.
- Das Element darf nicht verschachtelt werden.
- `noscript` ist in XML nicht zulässig.
- Das Verhalten ist an die HTML-Syntax gekoppelt.

## `template`

Besonders relevant:

- Content Model ist `Nothing`.
- Template Contents sind nicht normale Child Nodes des Elements.
- Template Contents werden in einem `DocumentFragment` gehalten.
- Template Contents sind inert.
- Scripts innerhalb von Template Contents werden nicht einfach bei
  Template-Erstellung ausgeführt.
- `template.content` liefert das zugehörige `DocumentFragment`.
- Declarative Shadow Roots werden über spezielle Template Attributes
  beschrieben.

## `slot`

Besonders relevant:

- Slot Assignment ist Teil des Shadow-DOM-Modells.
- `name` bestimmt den Namen eines benannten Slots.
- Zugewiesene Nodes werden anstelle des Fallback Contents repräsentiert.
- `assignedNodes()` und `assignedElements()` exponieren das
  Assignment-Ergebnis.
- `flatten` ermöglicht rekursive Berücksichtigung von Slots.

## `canvas`

Besonders relevant:

- `width` und `height` bestimmen die Bitmap-Dimension.
- Default ist 300 × 150.
- Canvas benötigt bei Verwendung geeigneten Fallback Content.
- Interactive Content innerhalb des transparenten Content Models ist
  grundsätzlich eingeschränkt.
- Canvas besitzt einen eigenen Context-Mode-Zustand.
- `getContext()` bestimmt bzw. liefert den Rendering Context.
- `transferControlToOffscreen()` kann den Canvas an ein `OffscreenCanvas`
  übertragen.
- Canvas besitzt ein `origin-clean`-Sicherheitsmodell.
- Pixelzugriff und Export sind an die Canvas-Sicherheitsregeln gebunden.

---

# Verarbeitungsmodelle und APIs

Dieser Abschnitt ist für die Vollständigkeitskontrolle besonders wichtig.

§4.12 enthält wesentlich mehr als fünf HTML-Elemente.

Die folgenden Konzepte werden deshalb nicht in das HTML-Elementinventar
aufgenommen.

## Script Processing

- Script Preparation
- Fetching
- Script Execution
- Parser-inserted Scripts
- Parser-blocking Scripts
- Async Scripts
- Defer Scripts
- Module Script Graphs
- Classic Scripts
- Data Blocks
- Import Maps
- Speculation Rules

## Template Processing

- Template Contents
- Template Contents Owner Document
- Inert Template Document
- Template Adopting Steps
- Declarative Shadow Roots

## Slot Processing

- Slot Assignment
- Assigned Nodes
- Assigned Elements
- Fallback Content
- Flattening

## Canvas Processing

- Canvas Bitmap
- Canvas Context Mode
- Rendering Contexts
- Origin-Clean Flag
- Canvas State
- 2D Rendering
- ImageBitmap Rendering
- OffscreenCanvas
- WebGL
- WebGL2
- WebGPU
- Bitmap Serialization
- Pixel Manipulation
- Security Model

Diese Konzepte sind fachlich relevant, dürfen aber nicht als zusätzliche
HTML-Tags gezählt werden.

---

# Querverweise

§4.12 besitzt zahlreiche Beziehungen zu anderen WHATWG-Bereichen.

## HTML Parsing

`script` und `noscript` sind eng mit dem HTML-Parsing-Modell verbunden.

Insbesondere:

- Script Start-/End-Tag-Verarbeitung
- Raw-Text-/Script-Parsing
- Parser-Insertion
- Parser-Blocking
- Scripting Mode

sind nicht ausschließlich innerhalb der Elementdefinitionen isoliert.

## DOM

Die Elemente verwenden bzw. implementieren DOM-Konzepte wie:

- `HTMLElement`
- `DocumentFragment`
- Node
- Element
- Shadow Root
- Template Contents

## Fetch

`script` verwendet Fetch-bezogene Konzepte unter anderem für:

- externe Scripts,
- Module,
- Module Dependencies,
- CORS,
- Credentials Mode,
- Referrer Policy,
- Fetch Priority,
- Integrity Metadata.

## JavaScript

Classic Scripts und Module Scripts beziehen sich auf die JavaScript-
Spezifikation.

Das konkrete JavaScript-Grammatikmodell wird nicht von HTML selbst
vollständig definiert.

## Import Maps

Import Maps werden über:

`<script type="importmap">`

eingebettet.

Import Maps sind ein eigenes Konzept und kein neues HTML-Element.

## Speculation Rules

Speculation Rules werden über:

`<script type="speculationrules">`

eingebettet.

Auch Speculation Rules sind eine eigene Feature-/Processing-Ebene.

## Shadow DOM

`template` und `slot` stehen in direktem Zusammenhang mit:

- Shadow Trees
- Shadow Roots
- Slot Assignment
- Declarative Shadow Roots
- Custom Element Registries

## XSLT / XPath

WHATWG enthält für `script` und `template` nicht-normative Hinweise zu
XSLT bzw. XPath.

Diese Abschnitte sind keine zusätzlichen HTML-Elemente.

---

# Status / V1

## WHATWG-Definition

Die folgenden Elemente sind im aktuellen WHATWG HTML Living Standard
definiert:

- `script`
- `noscript`
- `template`
- `slot`
- `canvas`

Damit besteht auf Feature-Ebene eine WHATWG-Definition.

## Konformität

Die Existenz einer Elementdefinition bedeutet nicht automatisch, dass jede
beliebige Verwendung konform ist.

Für die Konformitätsprüfung sind insbesondere relevant:

- Context
- Content Model
- Content Attributes
- Scripting-Zustand
- Parser-Zustand
- spezielle Processing Models
- Fallback Content
- Shadow-DOM-Zustände
- Canvas-spezifische Regeln
- Script-Typ
- URL-/MIME-Type-Regeln

## Browser-Support

Browser-Support ist ausdrücklich nicht Bestandteil des WHATWG-Status.

Die in der WHATWG-Dokumentation angezeigten historischen bzw. aktuellen
Browser-Supportinformationen werden daher nicht als ZE-WebLab-Status
übernommen.

## V1-Kategorisierung

Für die ZE-WebLab-Referenz:

| Element / Feature | WHATWG | Konformität | Browser-Support |
|---|---|---|---|
| `script` | definiert | kontext-/attributabhängig | separate Recherche |
| `noscript` | definiert | kontext-/scriptingabhängig | separate Recherche |
| `template` | definiert | Content Model und Attribute beachten | separate Recherche |
| `slot` | definiert | insbesondere Shadow-DOM-Kontext beachten | separate Recherche |
| `canvas` | definiert | Content Model, Fallback und API-Regeln beachten | separate Recherche |

---

# Elementabgrenzung

Für diesen Themenblock ist folgende Abgrenzung verbindlich:

## HTML-Elemente

Nur:

- `script`
- `noscript`
- `template`
- `slot`
- `canvas`

## Keine HTML-Elemente

Nicht in die Elementinventarliste aufzunehmen sind:

- `CanvasRenderingContext2D`
- `ImageBitmapRenderingContext`
- `OffscreenCanvas`
- `Path2D`
- WebGL Rendering Context
- WebGL2 Rendering Context
- GPU Canvas Context
- `DocumentFragment`
- Shadow Root
- Slot Assignment
- Import Map
- Speculation Rules
- Data Block
- Classic Script
- Module Script
- Script Processing Model
- Canvas State
- Canvas Settings
- Canvas Rendering APIs
- XSLT Processing
- XPath Processing

---

# Offene Punkte

Zum WHATWG-Primärbestand von §4.12 bestehen nach dieser Recherche keine
offenen Punkte hinsichtlich des HTML-Elementinventars.

Die folgenden Bereiche bleiben bewusst als separate Rechercheebenen
bestehen:

1. Detaillierte Accessibility-Auswertung anhand der einschlägigen
   Accessibility-Spezifikationen.
2. Browser-Kompatibilität und historische Implementierungsstände.
3. Detaillierte Fetch-Semantik der verwendeten Attribute.
4. Vollständige JavaScript-Spezifikationsauswertung für Script- und
   Module-Semantik.
5. Vollständige Canvas-API-Dokumentation einschließlich sämtlicher
   Rendering-Methoden.
6. Vollständige Shadow-DOM- und Custom-Elements-Dokumentation.
7. Vollständige Sanitization-/Security-Matrix über die Elementfamilien hinweg.

Diese Punkte stellen keine Lücken in der Recherche von §4.12 als
HTML-Elementbereich dar, sondern bewusst getrennte Folgeebenen des
ZE-WebLab-Referenzmodells.

---

# Prüfstatus

| Prüfbereich | Status |
|---|---|
| WHATWG §4.12 Struktur geprüft | abgeschlossen |
| Alle HTML-Elemente des Bereichs geprüft | abgeschlossen |
| `script` geprüft | abgeschlossen |
| `noscript` geprüft | abgeschlossen |
| `template` geprüft | abgeschlossen |
| `slot` geprüft | abgeschlossen |
| `canvas` geprüft | abgeschlossen |
| Content Categories geprüft | abgeschlossen |
| Contexts geprüft | abgeschlossen |
| Content Models geprüft | abgeschlossen |
| Tag Omission geprüft | abgeschlossen |
| Content Attributes geprüft | abgeschlossen |
| Accessibility-Verweise geprüft | abgeschlossen |
| Sanitization geprüft | abgeschlossen |
| DOM Interfaces geprüft | abgeschlossen |
| Normative Sonderregeln geprüft | abgeschlossen |
| Processing Models abgegrenzt | abgeschlossen |
| APIs von HTML-Elementen abgegrenzt | abgeschlossen |
| Querverweise geprüft | abgeschlossen |
| Browser-Support als separate Ebene behandelt | abgeschlossen |
| Offene Punkte dokumentiert | abgeschlossen |

---

# Quellen / Referenzen

## Primärquelle

WHATWG, **HTML Living Standard**, §4.12 „Scripting“.

Relevante Unterabschnitte:

- §4.12 Scripting
- §4.12.1 The `script` element
- §4.12.1.1 Processing model
- §4.12.1.2 Scripting languages
- §4.12.1.3 Restrictions for contents of `script` elements
- §4.12.1.4 Inline documentation for external scripts
- §4.12.1.5 Interaction of `script` elements and XSLT
- §4.12.2 The `noscript` element
- §4.12.3 The `template` element
- §4.12.3.1 Interaction of `template` elements with XSLT and XPath
- §4.12.4 The `slot` element
- §4.12.5 The `canvas` element
- §4.12.5.1 The 2D rendering context
- §4.12.5.2 The `ImageBitmap` rendering context
- §4.12.5.3 The `OffscreenCanvas` interface
- §4.12.5.4 Color spaces and color space conversion
- §4.12.5.5 Serializing bitmaps to a file
- §4.12.5.6 Security with `canvas` elements
- §4.12.5.7 Premultiplied alpha and the 2D rendering context

## Sekundäre Spezifikationsbeziehungen

Die WHATWG-Definition verweist für einzelne Aspekte unter anderem auf:

- DOM Standard
- Fetch Standard
- URL Standard
- MIME Sniffing Standard
- Web IDL
- Infra Standard

sowie auf externe bzw. fachlich zuständige Spezifikationen für:

- JavaScript
- Subresource Integrity
- Referrer Policy
- WebGL
- WebGPU
- Accessibility

Diese Quellen werden in dieser Datei nur dort als Querverweise betrachtet,
wo §4.12 selbst auf die entsprechenden Konzepte verweist.

---

# Zusammenfassung der fachlichen Abgrenzung

§4.12 „Scripting“ ist kein reiner „JavaScript-Tag“-Abschnitt.

Das WHATWG-Modell umfasst fünf HTML-Elemente:

1. `script`
2. `noscript`
3. `template`
4. `slot`
5. `canvas`

Darüber hinaus enthält der Bereich umfangreiche Processing Models und
APIs.

Insbesondere `canvas`, `template` und `script` besitzen jeweils komplexe
Untermodelle, die für eine vollständige HTML-Referenz berücksichtigt werden
müssen, ohne daraus zusätzliche HTML-Elemente zu konstruieren.

Damit bleibt die ZE-WebLab-Elementinventarliste sauber von:

- APIs,
- Rendering Contexts,
- Processing Models,
- Shadow-DOM-Konzepten,
- Script-Typen,
- Import Maps,
- Speculation Rules,
- Datenblöcken

getrennt.

Der Themenblock §4.12 ist damit auf der Element-/Feature-Ebene vollständig
für die weitere ZE-WebLab-Referenz erfasst.