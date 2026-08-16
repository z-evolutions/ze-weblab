# ZE-WebLab – HTML-Referenz: Global Attributes

## Arbeitsstand / Quellenstand

- **Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien
- **Feature-Familie:** Global Attributes
- **Feature-Typ:** Attribute Family / normative HTML-Konzeptfamilie
- **Normative Primärquelle:** WHATWG HTML Living Standard
- **Aktueller WHATWG-Stand der Recherche:** 17. Juli 2026
- **ZE-WebLab-Projektquelle:** `docs/html/01-document-element.md` bis `docs/html/12-scripting.md`
- **Zieldatei:** `docs/html/13-global-attributes.md`
- **Prüfstatus:** vollständig recherchiert für den hier abgegrenzten Global-Attributes-Bereich
- **Browser-Kompatibilität:** nicht Bestandteil dieser Datei
- **V1-Status:** projektspezifische Einstufung und nicht mit dem WHATWG-Status gleichzusetzen

### Quellenabgrenzung

Der WHATWG HTML Living Standard ist die normative Primärquelle für Definitionen, Syntax, Zustände, Konformitätsanforderungen, Verarbeitung und DOM-/IDL-Beziehungen.

Das ZE-WebLab-Repository ist die maßgebliche Quelle für den bereits vorhandenen Projektbestand.

Externe Spezifikationen werden nur dort herangezogen, wo der HTML Standard ausdrücklich auf sie verweist oder wo ein Feature nicht durch HTML selbst definiert wird.

Insbesondere gilt:

- WHATWG-Status ist nicht gleich Browser-Support.
- ZE-WebLab-V1-Status ist nicht gleich WHATWG-Status.
- DOM-definierte Attribute sind nicht automatisch HTML-definierte Global Attributes.
- ARIA-Attribute sind nicht automatisch WHATWG-definierte Global Attributes.
- Event-Handler-Content-Attributes bilden eine eigene Feature-Familie.
- `data-*` bildet ein eigenes HTML-Konzept innerhalb des Bereichs der gemeinsamen Attribute.
- Attribute sind keine HTML-Elemente.

---

## Einordnung

Global Attributes sind Attribute, die nach der HTML-Spezifikation grundsätzlich auf allen HTML-Elementen angegeben werden können.

Die aktuelle WHATWG-Systematik führt hierfür 28 HTML-definierte Global Attributes:

1. `accesskey`
2. `autocapitalize`
3. `autocorrect`
4. `autofocus`
5. `contenteditable`
6. `dir`
7. `draggable`
8. `enterkeyhint`
9. `headingoffset`
10. `headingreset`
11. `hidden`
12. `inert`
13. `inputmode`
14. `is`
15. `itemid`
16. `itemprop`
17. `itemref`
18. `itemscope`
19. `itemtype`
20. `lang`
21. `nonce`
22. `popover`
23. `spellcheck`
24. `style`
25. `tabindex`
26. `title`
27. `translate`
28. `writingsuggestions`

Diese Liste ist die normative HTML-Inventarliste der Global Attributes.

Sie ist nicht mit sämtlichen Attributen gleichzusetzen, die auf HTML-Elementen verwendet werden können.

Insbesondere existieren daneben:

- DOM-definierte gemeinsame Attribute: `class`, `id`, `slot`
- benutzerdefinierte Datenattribute: `data-*`
- Event-Handler-Content-Attributes: `on*`
- ARIA-Attribute: `role`, `aria-*`
- elementbezogene Attribute
- Attribute aus anderen Spezifikationen oder Vokabularen

Diese Gruppen müssen getrennt behandelt werden.

---

## WHATWG-Struktur

### Maßgeblicher Abschnitt

Der zentrale WHATWG-Abschnitt ist:

- §3.2.5 Global attributes

Darin befinden sich insbesondere:

- §3.2.5.1 `title`
- §3.2.5.2 `lang` und `xml:lang`
- §3.2.5.3 `translate`
- §3.2.5.4 `dir`
- §3.2.5.5 `style`
- §3.2.5.6 `data-*`

Die Definitionen der übrigen Global Attributes sind auf die fachlich zuständigen WHATWG-Bereiche verteilt.

### Relevante verteilte Bereiche

Für die vollständige Recherche dieser Feature-Familie sind insbesondere relevant:

- User Interaction
- Focus
- Keyboard Shortcuts
- Editing
- Drag and Drop
- Popover
- Headings
- Microdata
- Content Security Policy / Nonce-Verarbeitung
- Custom Elements
- DOM
- ARIA / Accessibility
- Event Handler
- Rendering
- Parsing und Foreign Content

Global Attributes sind daher eine Querschnittsfamilie und nicht auf einen einzelnen WHATWG-Unterabschnitt beschränkt.

---

## Inventar

### 1. HTML-definierte Global Attributes

| Attribut | Typ / Wertmodell | Hauptfunktion |
|---|---|---|
| `accesskey` | Token-Liste aus einzelnen Code Points | Tastaturkürzel-Hinweis |
| `autocapitalize` | enumerated attribute | Autokapitalisierungshinweis |
| `autocorrect` | enumerated attribute | Autokorrektur |
| `autofocus` | Boolean Attribute | automatisches Fokussieren |
| `contenteditable` | enumerated attribute | Editierbarkeit |
| `dir` | enumerated / Sonderwertmodell | Schreibrichtung |
| `draggable` | enumerated attribute | Drag-Verhalten |
| `enterkeyhint` | enumerated attribute | Beschriftung/Aktion der Enter-Taste |
| `headingoffset` | nicht-negativer Integer, eingeschränkt auf 0–8 | Verschiebung der Heading-Ebene |
| `headingreset` | Boolean Attribute | Zurücksetzen des Heading-Kontexts |
| `hidden` | enumerated attribute | verborgen / Hidden Until Found |
| `inert` | Boolean Attribute | Inertness eines Subtrees |
| `inputmode` | enumerated attribute | gewünschte Eingabemodalität |
| `is` | Custom-Element-Name | customized built-in element |
| `itemid` | URL | Microdata-Identifier |
| `itemprop` | Token-/Vokabularsystem | Microdata-Property |
| `itemref` | ID-Token-Liste | zusätzliche Microdata-Knoten |
| `itemscope` | Boolean Attribute | Einführung eines Microdata Items |
| `itemtype` | URL-Token-Liste | Microdata-Typen |
| `lang` | BCP-47-Sprach-Tag oder leer | Primärsprache |
| `nonce` | Text | kryptographischer Nonce für CSP-bezogene Verarbeitung |
| `popover` | enumerated attribute | Popover-Verhalten |
| `spellcheck` | enumerated attribute | Rechtschreib-/Grammatikprüfung |
| `style` | Text / CSS-Deklarationen | Inline-Style |
| `tabindex` | gültiger Integer | Fokusierbarkeit und Fokusreihenfolge |
| `title` | Text | Advisory Information |
| `translate` | enumerated attribute | Übersetzungsverhalten |
| `writingsuggestions` | enumerated attribute | Schreibvorschläge |

### 2. Nicht Bestandteil der 28er-HTML-Liste

Zusätzlich können HTML-Elemente folgende gemeinsame Attribute besitzen:

- `class`
- `id`
- `slot`

Diese Attribute werden durch DOM definiert.

### 3. Weitere gemeinsame HTML-Attributfamilien

Zusätzlich:

- `data-*`
- Event-Handler-Content-Attributes

### 4. Externe bzw. separate Semantik

Nicht als HTML-Global-Attributes zu zählen:

- `role`
- `aria-*`

Diese gehören zur ARIA-/Accessibility-Spezifikation und deren Integration mit HTML.

---

## Begriffsdefinitionen

### Global Attribute

Ein Global Attribute ist ein Attribut, das nach der HTML-Spezifikation auf allen HTML-Elementen angegeben werden kann.

Die Aussage „global“ bedeutet nicht:

> Dieses Attribut besitzt auf jedem Element dieselbe praktische Wirkung.

Viele Global Attributes haben kontextabhängige Verarbeitung.

Beispiele:

- `autofocus` ist besonders für fokussierbare Elemente relevant.
- `contenteditable` wirkt auf editierbare Bereiche.
- `inputmode` ist für Eingabesituationen relevant.
- `popover` steht mit dem Popover-Modell in Verbindung.
- `itemprop` besitzt seine Bedeutung innerhalb des Microdata-Modells.
- `headingoffset` steht mit Heading-Verarbeitung in Verbindung.

### Content Attribute

Ein Content Attribute ist das Attribut im DOM-/Markup-Modell des Elements.

Die HTML-Spezifikation unterscheidet dieses Konzept von den zugehörigen IDL-Attributen.

### IDL Attribute

Ein IDL Attribute ist eine Eigenschaft eines DOM-Interfaces.

Es kann:

- den Content-Attribute-Wert reflektieren,
- einen verarbeiteten Zustand liefern,
- einen internen Zustand exponieren,
- oder ein eigenes API-Verhalten besitzen.

Beispiele:

- `HTMLElement.hidden`
- `HTMLElement.inert`
- `HTMLElement.tabIndex`
- `HTMLElement.contentEditable`
- `HTMLElement.isContentEditable`
- `HTMLElement.inputMode`
- `HTMLElement.enterKeyHint`
- `HTMLElement.writingSuggestions`
- `HTMLElement.nonce`
- `HTMLElement.popover`
- `HTMLElement.headingOffset`
- `HTMLElement.headingReset`

Ein IDL Attribute ist daher nicht automatisch ein zweites HTML-Attribut.

### Boolean Attribute

Bei einem Boolean Attribute ist die Anwesenheit des Attributes maßgeblich.

Der konkrete Attributwert ist nicht als beliebiger Wahrheitswert zu interpretieren.

Beispiele:

- `autofocus`
- `headingreset`
- `inert`
- `itemscope`

### Enumerated Attribute

Enumerated Attributes besitzen definierte Keywords und Zustände.

Die Zustände können sich unterscheiden von den literalen Keyword-Werten.

Beispiele:

- `hidden`
- `contenteditable`
- `spellcheck`
- `autocapitalize`
- `autocorrect`
- `inputmode`
- `enterkeyhint`
- `translate`
- `dir`
- `draggable`
- `popover`
- `writingsuggestions`

### Vererbter bzw. berechneter Zustand

Einige Attribute erzeugen einen Zustand, der nicht allein aus dem eigenen Content-Attribut bestimmt wird.

Beispiele:

- `lang`
- `dir`
- `translate`
- `contenteditable`
- `spellcheck`
- `writingsuggestions`
- `autocapitalize`
- `autocorrect`

Für diese Features müssen daher eigene Processing Models berücksichtigt werden.

---

## Normative Regeln

### Allgemeine Geltung

Die 28 HTML-definierten Global Attributes dürfen grundsätzlich auf HTML-Elementen angegeben werden.

Die Tatsache, dass ein Attribut global ist, bedeutet nicht, dass jedes Element für jede mögliche Funktion des Attributes geeignet ist.

Kontextregeln und die jeweiligen Feature-Definitionen bestimmen die konkrete Wirkung.

### Namespace-Abgrenzung

Die HTML-Definition eines Global Attributes bezieht sich auf HTML-Elemente.

Ein gleichnamiges Attribut auf einem Element eines anderen Namespace ist nicht automatisch dasselbe HTML-Attribut.

Dies ist insbesondere bei SVG und MathML relevant.

### Attribute und DOM

Für `class`, `id` und `slot` definiert DOM die Anforderungen für Elemente in beliebigen Namespaces.

HTML dokumentiert deren Verwendung auf HTML-Elementen, ist aber nicht die alleinige normative Definitionsquelle.

### Attribute und Custom Elements

Global Attributes können auch bei Custom Elements relevant sein.

Insbesondere:

- `is` ist direkt mit customized built-in elements verbunden.
- `class`, `id`, `slot` und `data-*` sind nicht auf native Elemente beschränkt.
- Global Attributes können auf autonomen Custom Elements verwendet werden, soweit ihre jeweilige Definition dies vorsieht.

---

## Detailprüfung

## `accesskey`

### Feature-Typ

- Attribute
- User Interaction
- Processing Model
- DOM API

### WHATWG-Bereich

- §6.7 Assigning keyboard shortcuts
- insbesondere §6.7.2 `accesskey`
- §6.7.3 Processing model

### Semantik

`accesskey` liefert dem User Agent einen Hinweis zur Vergabe eines Tastaturkürzels für ein Element.

Der User Agent bestimmt die tatsächlich verwendete Tastenkombination.

Der Attributwert ist eine geordnete Menge eindeutiger, durch ASCII-Whitespace getrennter Tokens.

Jedes Token muss genau einen Code Point enthalten.

### Processing Model

Beim Setzen, Ändern oder Entfernen des Attributes aktualisiert der User Agent den zugewiesenen Access Key.

Der User Agent kann:

1. die Tokens der Reihe nach prüfen,
2. ungeeignete Tokens überspringen,
3. eine geeignete Kombination mit Modifier Keys auswählen,
4. optional eine eigene Fallback-Kombination vergeben.

Die konkrete Tastenkombination ist daher nicht aus dem Attributwert deterministisch abzuleiten.

### DOM

`HTMLElement.accessKey` repräsentiert das Attribut.

`HTMLElement.accessKeyLabel` liefert die vom User Agent bestimmte menschenlesbare Darstellung des tatsächlich zugewiesenen Kürzels.

### Konformität

Der Attributwert muss aus eindeutigen, durch ASCII-Whitespace getrennten Ein-Zeichen-Tokens bestehen.

### Querverweise

- Focus
- Commands
- User Interaction
- DOM
- `hidden`
- `inert`

---

## `autocapitalize`

### Feature-Typ

- Attribute
- User Interaction
- Editing
- Input Modality
- Processing Model

### WHATWG-Bereich

- §6.8.7 Autocapitalization

### Zustände

Die definierten Zustände sind:

- Default
- None
- Sentences
- Words
- Characters

Die Keyword-Zuordnung umfasst insbesondere:

- `off` → None
- `none` → None
- `on` → Sentences
- `sentences` → Sentences
- `words` → Words
- `characters` → Characters

Der Missing Value Default ist Default.

Der Invalid Value Default ist Sentences.

### Verarbeitung

Der verwendete Autocapitalization Hint entsteht nicht ausschließlich aus dem eigenen Attribut.

Zu berücksichtigen sind unter anderem:

- Elementtyp
- Editing Host
- Form Owner
- Input Type
- Vererbung innerhalb der vorgesehenen Editing-/Input-Situationen.

Für `input` in URL-, Email- oder Password-Zuständen wird Autokapitalisierung nicht durch `autocapitalize` aktiviert.

### DOM

`HTMLElement.autocapitalize` steht als DOM-Eigenschaft zur Verfügung.

### Konformität

Das Attribut darf nicht als Eingabevalidierung verwendet werden.

Autokapitalisierung ist eine Eingabehilfe und keine Validierungsregel.

---

## `autocorrect`

### Feature-Typ

- Attribute
- User Interaction
- Editing
- Input Modality
- Processing Model

### WHATWG-Bereich

- §6.8.8 Autocorrection

### Zustände

- `on` → On
- `off` → Off

Missing Value Default, Invalid Value Default und Empty Value Default sind On.

### Verarbeitung

Die verwendete Autokorrektur kann von folgenden Faktoren abhängen:

- eigenes `autocorrect`-Attribut
- Form Owner
- Elementtyp
- Editing Host
- Input Type.

Bei URL-, Email- und Password-Input-Zuständen wird Autokorrektur nicht aktiviert.

### DOM

`HTMLElement.autocorrect` exponiert den verwendeten Autokorrekturzustand.

### Querverweise

- `autocapitalize`
- `spellcheck`
- `contenteditable`
- Forms
- Editing

---

## `autofocus`

### Feature-Typ

- Boolean Attribute
- Focus
- Processing Model

### WHATWG-Bereich

- §6.6.7 The `autofocus` attribute

### Semantik

`autofocus` kennzeichnet ein Element als Kandidaten für automatisches Fokussieren.

Es ist ein Boolean Attribute.

### Scoping

WHATWG definiert Autofocus Scoping Roots und eine Candidate-Verarbeitung.

Besondere Scoping-Beziehungen bestehen unter anderem für:

- `dialog`
- Popover-Elemente
- Dokumentkontext.

### Processing

Beim Laden beziehungsweise beim Anzeigen geeigneter Interaktionscontainer wird der Autofocus-Mechanismus ausgeführt.

Bei `dialog` und Popover kann der Fokus beim Anzeigen des Containers erfolgen.

### DOM

`HTMLElement.autofocus` steht als IDL-Attribut zur Verfügung.

### Querverweise

- Focus
- `dialog`
- `popover`
- `tabindex`
- User Activation

---

## `contenteditable`

### Feature-Typ

- Enumerated Attribute
- Editing
- DOM API
- Processing Model

### WHATWG-Bereich

- §6.8.1 Making document regions editable

### Zustände

- True
- False
- Plaintext-Only
- Inherit

Keywords:

- `true`
- `false`
- `plaintext-only`

Der Missing Value Default und Invalid Value Default sind Inherit.

Der Empty Value Default ist True.

### Semantik

`contenteditable` bestimmt, ob ein Element beziehungsweise ein von ihm erzeugter Editing-Kontext editierbar ist.

Bei fehlendem beziehungsweise ungültigem Wert kann die Entscheidung vom Elternkontext abhängen.

### Plaintext-Only

`plaintext-only` erlaubt die Bearbeitung von Text, ohne Rich-Text-Formatierung als Bearbeitungsmodell zu verwenden.

### DOM

`ElementContentEditable` definiert unter anderem:

- `contentEditable`
- `isContentEditable`
- `enterKeyHint`
- `inputMode`

`contentEditable` kann die Werte:

- `true`
- `plaintext-only`
- `false`
- `inherit`

liefern.

Ein ungültiger Setter-Wert führt zu einer `SyntaxError`-DOMException.

### Querverweise

- Editing
- Selection
- Input Events
- `spellcheck`
- `autocapitalize`
- `autocorrect`
- `writingsuggestions`
- `inputmode`
- `enterkeyhint`

---

## `dir`

### Feature-Typ

- Enumerated Attribute
- Text Directionality
- Bidirectional Text
- Processing Model

### WHATWG-Bereich

- §3.2.5.4 The `dir` attribute
- Anforderungen zum bidirektionalen Algorithmus

### Zustände

Das Attribut unterstützt die Richtungszustände:

- `ltr`
- `rtl`
- `auto`

Zusätzlich existieren besondere Regeln für den fehlenden Wert und die automatische Ermittlung.

### Semantik

`dir` bestimmt die Text-Richtung eines Elements.

`auto` ermöglicht die automatische Ermittlung anhand des Textes nach den dafür definierten Regeln.

### Vererbung

Bei fehlendem Attribut wird die Richtung grundsätzlich aus dem umgebenden Kontext bestimmt, wobei spezielle Regeln für bestimmte HTML-Konstruktionen und Shadow-DOM-Situationen gelten.

### DOM

Die Richtung ist außerdem über die DOM-/HTML-Verarbeitung und `HTMLElement.dir` zugänglich.

### Querverweise

- Bidirectional Algorithm
- `lang`
- Text-Level Semantics
- Rendering
- Shadow DOM

---

## `draggable`

### Feature-Typ

- Enumerated Attribute
- Drag and Drop
- User Interaction

### WHATWG-Bereich

- §6.11 Drag and drop

### Semantik

`draggable` liefert einen Hinweis beziehungsweise Zustand dafür, ob ein Element für Drag-and-Drop-Interaktionen als draggable behandelt wird.

### Zustandsmodell

Das Attribut besitzt ein enumeriertes Zustandsmodell, insbesondere:

- `true`
- `false`
- Auto

Der genaue verwendete Zustand hängt vom Attributwert und den dafür definierten Default-Regeln ab.

### Querverweise

- Drag and Drop
- `tabindex`
- User Interaction
- DOM Drag Events

---

## `enterkeyhint`

### Feature-Typ

- Enumerated Attribute
- Input Modality
- Editing
- DOM API

### WHATWG-Bereich

- §6.8.10 Input modalities: the `enterkeyhint` attribute

### Zustände

Definierte Keywords:

- `enter`
- `done`
- `go`
- `next`
- `previous`
- `search`
- `send`

### Semantik

Das Attribut gibt dem User Agent einen Hinweis, welche Aktion beziehungsweise Beschriftung oder welches Symbol für die Enter-Taste einer virtuellen Tastatur angezeigt werden sollte.

### Verarbeitung

Der User Agent kann weitere Kontextinformationen berücksichtigen, insbesondere:

- `inputmode`
- `type`
- `pattern`

### DOM

`HTMLElement.enterKeyHint` reflektiert den bekannten Attributwert.

### Querverweise

- `contenteditable`
- `inputmode`
- Forms
- Virtual Keyboard / Input Method
- Editing

---

## `headingoffset`

### Feature-Typ

- Integer Attribute
- Heading Model
- DOM API

### WHATWG-Bereich

- §4.3.11 Headings and outlines

### Wert

`headingoffset` ist auf einen nicht-negativen Integer begrenzt und besitzt einen zulässigen Wertebereich von 0 bis 8.

### Semantik

Das Attribut beeinflusst die Berechnung der effektiven Heading-Ebene eines Heading-Kontexts.

Es ist daher kein bloßes Präsentationsattribut.

### DOM

Das entsprechende IDL-Attribut ist:

`HTMLElement.headingOffset`

Die Reflection ist auf den Wertebereich 0 bis 8 begrenzt.

### Querverweise

- `h1`–`h6`
- Heading Model
- `headingreset`
- Sections
- Accessibility

---

## `headingreset`

### Feature-Typ

- Boolean Attribute
- Heading Model
- DOM API

### WHATWG-Bereich

- §4.3.11 Headings and outlines

### Semantik

`headingreset` beeinflusst den Heading-Kontext und ermöglicht das Zurücksetzen des Heading-Offset-Kontexts.

### DOM

Das entsprechende IDL-Attribut ist:

`HTMLElement.headingReset`

### Querverweise

- `headingoffset`
- Heading Context
- Sectioning
- Accessibility

---

## `hidden`

### Feature-Typ

- Enumerated Attribute
- User Interaction
- Rendering
- Find-in-Page
- Fragment Navigation
- Processing Model
- Accessibility

### WHATWG-Bereich

- §6.1 The `hidden` attribute
- Rendering-Regeln für Hidden Elements

### Zustände

- Hidden
- Hidden Until Found
- Not Hidden

Keywords:

- `hidden`
- `until-found`

Missing Value Default:

- Not Hidden

Invalid Value Default:

- Hidden

Empty Value Default:

- Hidden

### Hidden State

Im Hidden State soll das Element nicht gerendert werden.

Die Rendering-Implementierung erfolgt über die im Rendering-Teil beschriebenen Regeln.

### Hidden Until Found

`hidden="until-found"` unterscheidet sich vom klassischen Hidden State.

Der Inhalt bleibt für:

- Find-in-Page
- Fragment Navigation

zugänglich.

Wenn eine Suche oder Navigation auf ein verborgenes Ziel trifft, kann der User Agent das Element durch den Ancestor-Revealing-Mechanismus offenlegen.

### `beforematch`

Beim Aufdecken eines Hidden-Until-Found-Ancestors wird ein `beforematch`-Event ausgelöst, bevor das Attribut entfernt wird.

### Rendering

Der WHATWG-Rendering-Bereich beschreibt für:

- `hidden`
- `hidden=until-found`

unterschiedliche empfohlene CSS-basierte Rendermechanismen.

### Konformität

`hidden` darf nicht dazu verwendet werden, Inhalte nur für eine einzelne Darstellungsform zu verstecken.

Insbesondere ist es nicht das korrekte Modell für UI-Inhalte, die lediglich in einer alternativen Präsentation verborgen werden sollen.

### Accessibility

Hidden Content soll nicht als für Benutzer generell zugänglicher alternativer Inhalt verstanden werden.

Die Spezifikation weist ausdrücklich darauf hin, dass `hidden` auch für Assistive Technologies verborgen ist.

### DOM

`HTMLElement.hidden` kann den Zustand beziehungsweise den `until-found`-Zustand über die definierten Getter-/Setter-Regeln repräsentieren.

### Querverweise

- `details`
- `popover`
- `inert`
- Find-in-Page
- Fragment Navigation
- Rendering
- Accessibility
- `beforematch`

---

## `inert`

### Feature-Typ

- Boolean Attribute
- User Interaction
- Focus
- Accessibility
- Processing Model

### WHATWG-Bereich

- §6.3 Inert subtrees
- §6.3.2 The `inert` attribute

### Semantik

Das Vorhandensein von `inert` bewirkt, dass das Element und seine entsprechenden Flat-Tree-Descendants inert werden, soweit sie nicht ausdrücklich aus der Inertness ausgenommen sind.

### Wirkung eines inert Nodes

Bei einem inert Node gelten unter anderem:

- Hit Testing verhält sich wie bei `pointer-events: none`.
- Textauswahl verhält sich wie bei `user-select: none`.
- Editierbarkeit wird unterbunden.
- Find-in-Page soll den Node grundsätzlich ignorieren.
- Fokus ist grundsätzlich nicht möglich.
- Der Node wird nicht in Accessibility APIs beziehungsweise gegenüber Assistive Technologies exponiert.
- Commands innerhalb eines inert Kontextes werden inoperabel.

### Modal Dialogs

Ein Modal Dialog erzeugt eine Inertness des übrigen Dokuments.

Der Dialog selbst und seine Flat-Tree-Descendants werden dabei ausgenommen.

### Accessibility

`inert` besitzt direkte Accessibility-Auswirkungen.

Es darf daher nicht nur als visuelles Attribut dokumentiert werden.

### DOM

`HTMLElement.inert` steht als Boolean IDL Attribute zur Verfügung.

### Querverweise

- `dialog`
- `popover`
- Focus
- Accessibility
- `tabindex`
- Editing
- Commands

---

## `inputmode`

### Feature-Typ

- Enumerated Attribute
- Input Modality
- Editing
- DOM API

### WHATWG-Bereich

- §6.8.9 Input modalities: the `inputmode` attribute

### Semantik

`inputmode` gibt dem User Agent einen Hinweis darauf, welche Eingabemethode für die Eingabe am hilfreichsten ist.

### Zustände

Die definierten Keywords umfassen:

- `none`
- `text`
- `decimal`
- `numeric`
- `tel`
- `search`
- `email`
- `url`

### Abgrenzung

`inputmode` bestimmt nicht den semantischen Datentyp beziehungsweise die Validierung eines Formularfeldes.

Es ist ein Input-Hint.

### DOM

`HTMLElement.inputMode` reflektiert den bekannten Wert.

### Querverweise

- `contenteditable`
- `enterkeyhint`
- Forms
- Virtual Keyboards
- Input States

---

## `is`

### Feature-Typ

- Custom Elements Feature
- Attribute
- Parsing
- DOM
- CustomElementRegistry

### WHATWG-Bereich

- §4.13 Custom elements
- Customized built-in elements

### Semantik

`is` kennzeichnet ein Element als customized built-in element.

Der Wert muss ein gültiger Custom-Element-Name sein, für den eine entsprechende Definition registriert wurde.

### Abgrenzung

`is` erzeugt kein autonomes Custom Element.

Es erweitert vielmehr ein bestehendes natives Element.

Beispiel:

```html
<button is="fancy-button">...</button>
```

Die eigentliche Custom-Element-Definition erfolgt über die Custom Elements API.

### Parsing

`is` besitzt besondere Bedeutung im Parsing und bei der Erstellung beziehungsweise Aufwertung customized built-in elements.

### DOM / API

Das Feature ist eng verbunden mit:

- `CustomElementRegistry`
- `customElements.define()`
- Custom Element Definitions
- Reactions
- Upgrade Processing

### Querverweise

- Custom Elements
- Parsing
- DOM
- `customElements`
- `ElementInternals`

---

## `itemid`

### Feature-Typ

- Microdata Attribute
- URL Value
- Semantic Annotation

### WHATWG-Bereich

- §5 Microdata

### Semantik

`itemid` definiert den globalen Identifier eines Microdata Items.

Das Attribut ist nur im Rahmen des Microdata-Modells sinnvoll.

### Wert

Der Wert muss den für Microdata definierten URL-Anforderungen entsprechen.

### Querverweise

- `itemscope`
- `itemtype`
- `itemprop`
- `itemref`
- Microdata

---

## `itemprop`

### Feature-Typ

- Microdata Attribute
- Token Set
- Semantic Annotation

### WHATWG-Bereich

- §5 Microdata

### Semantik

`itemprop` definiert Property-Namen eines Microdata Items.

Die Property-Werte können aus unterschiedlichen Quellen stammen, abhängig vom Elementtyp und dem Microdata-Modell.

### Wertmodell

Der Attributwert ist ein ungeordnetes Set eindeutiger, durch ASCII-Whitespace getrennter Tokens.

Die Tokens können unter anderem:

- absolute URLs
- definierte Property-Namen
- textuelle Property-Namen

darstellen.

### Querverweise

- `itemscope`
- `itemtype`
- `itemid`
- `itemref`
- Microdata Value Extraction

---

## `itemref`

### Feature-Typ

- Microdata Attribute
- ID Token Set
- Semantic Annotation

### WHATWG-Bereich

- §5 Microdata

### Semantik

`itemref` erweitert die Menge der DOM-Knoten, die zu einem Microdata Item gehören.

Damit können Properties referenziert werden, die nicht direkte Descendants des Items sind.

### Wertmodell

Der Wert ist ein ungeordnetes Set eindeutiger, durch ASCII-Whitespace getrennter IDs.

### Querverweise

- `itemscope`
- `itemprop`
- Microdata Item Properties
- DOM IDs

---

## `itemscope`

### Feature-Typ

- Boolean Attribute
- Microdata
- Semantic Annotation

### WHATWG-Bereich

- §5 Microdata

### Semantik

`itemscope` führt ein Microdata Item ein.

Ein Element mit `itemscope` bildet den Ausgangspunkt eines Items.

### Kombination mit `itemtype`

`itemscope` kann mit `itemtype` kombiniert werden, um den Typ des Items zu bestimmen.

### Kombination mit `itemprop`

Ein Element kann gleichzeitig Bestandteil eines übergeordneten Items sein und ein eigenes Item bilden.

### Querverweise

- `itemtype`
- `itemid`
- `itemprop`
- `itemref`
- Microdata Parsing / Extraction

---

## `itemtype`

### Feature-Typ

- Microdata Attribute
- URL Token Set
- Semantic Annotation

### WHATWG-Bereich

- §5 Microdata

### Semantik

`itemtype` definiert die Typen eines Microdata Items.

### Wertmodell

Der Wert ist ein ungeordnetes Set eindeutiger, durch ASCII-Whitespace getrennter URLs.

Die URLs müssen die für Microdata definierten Anforderungen erfüllen.

### Kontext

`itemtype` ist nur in einem geeigneten Microdata Item-Kontext sinnvoll und insbesondere mit `itemscope` verbunden.

### Querverweise

- `itemscope`
- `itemid`
- `itemprop`
- Microdata Vocabulary

---

## `lang`

### Feature-Typ

- Global Attribute
- Language
- Internationalization
- Processing Model

### WHATWG-Bereich

- §3.2.5.2 The `lang` and `xml:lang` attributes

### Semantik

`lang` bestimmt die Primärsprache für:

- den Inhalt des Elements
- Attribute des Elements, deren Werte Text enthalten

### Wert

Der Wert muss ein gültiger BCP 47 Language Tag oder der leere String sein.

Der leere String bedeutet, dass die Primärsprache unbekannt ist.

### Vererbung

Wenn `lang` fehlt, wird die Sprache grundsätzlich vom Elternkontext übernommen.

Die Spezifikation definiert besondere Regeln, unter anderem für Shadow Trees und `slot`.

### `xml:lang`

`xml:lang` im XML-Namespace wird durch XML definiert.

Es ist nicht dasselbe wie ein HTML-`lang`-Attribut ohne Namespace.

### DOM

`HTMLElement.lang` ist Bestandteil der HTML-/DOM-Schnittstelle.

### Accessibility

Die Sprachinformation ist für die korrekte Interpretation von Inhalten durch User Agents und Assistive Technologies relevant.

### Querverweise

- BCP 47
- Internationalization
- Accessibility
- `translate`
- Shadow DOM

---

## `nonce`

### Feature-Typ

- Security Attribute
- CSP Integration
- Processing Model
- DOM API

### WHATWG-Bereich

- §2.5.6 Nonce attributes
- aktuelle URL-/Fetch-bezogene Bereiche

### Semantik

`nonce` repräsentiert einen kryptographischen Nonce-Wert, der im Zusammenhang mit Content Security Policy verwendet werden kann.

### Interner Zustand

Der Wert wird in einem internen Slot `[[CryptographicNonce]]` verwaltet.

Die Spezifikation schützt den Wert vor einfacher Exfiltration über Mechanismen, die Content-Attribute auslesen können.

### Content Attribute

Unter bestimmten Bedingungen wird der Content-Attributwert geleert, während der interne Nonce erhalten bleibt.

### DOM

`HTMLOrSVGOrMathMLElement` stellt den Nonce über das IDL-Attribut `nonce` bereit.

Der Setter aktualisiert den internen kryptographischen Nonce-Wert und nicht einfach den entsprechenden Content-Attributwert.

### Security

`nonce` ist kein eigenständiges CSP-Policy-System.

Die konkrete Durchsetzung der Ressourcenfreigabe erfolgt über CSP.

### Querverweise

- Content Security Policy
- Fetch
- `script`
- `style`
- HTML/SVG/MathML
- DOM

---

## `popover`

### Feature-Typ

- Enumerated Attribute
- User Interaction
- Popover API
- Top Layer
- Focus
- Processing Model

### WHATWG-Bereich

- §6.12 Popovers

### Semantik

`popover` aktiviert beziehungsweise konfiguriert das Popover-Modell.

### Zustandsmodell

Das Attribut besitzt ein enumeriertes Zustandsmodell, das insbesondere zwischen:

- No Popover
- Auto
- Manual

unterscheidet.

### Popover-Infrastruktur

Das Feature ist mit folgenden Konzepten verbunden:

- Popover State
- Popover Trigger
- Popover Target
- Popover Showing State
- Top Layer
- Light Dismiss
- Close Requests
- Invoker Commands
- Focus Management

### DOM

`HTMLElement` stellt unter anderem bereit:

- `popover`
- `showPopover()`
- `hidePopover()`
- `togglePopover()`

### Processing

Die Popover-Verarbeitung umfasst unter anderem:

- Anzeigen
- Verbergen
- Toggle
- Light Dismiss
- Top-Layer-Integration
- Fokusverarbeitung
- Trigger-/Target-Beziehungen.

### Querverweise

- `autofocus`
- `inert`
- `hidden`
- Commands
- User Activation
- Focus
- Dialogs
- Top Layer

---

## `spellcheck`

### Feature-Typ

- Enumerated Attribute
- Editing
- Input Processing
- Accessibility-/Language-Bezug

### WHATWG-Bereich

- §6.8.5 Spelling and grammar checking

### Zustände

- True
- False
- Default

Keywords:

- `true`
- `false`

Missing Value Default:

- Default

Invalid Value Default:

- Default

Empty Value Default:

- True

### Verarbeitung

Die tatsächliche Prüfung kann von folgenden Faktoren abhängen:

- eigener Attributzustand
- Ancestor mit nicht-default Zustand
- elementabhängiges Default-Verhalten
- Elternkontext
- User Preferences

### Checkbare Inhalte

Die Spezifikation unterscheidet unter anderem:

- Werte geeigneter `input`-Elemente
- Werte von `textarea`
- Text in Editing Hosts
- Text in Attributen editierbarer Elemente

### DOM

`HTMLElement.spellcheck` liefert einen Boolean-Zustand entsprechend den definierten Getter-Regeln.

Die IDL-Eigenschaft muss nicht die tatsächliche Benutzerpräferenz widerspiegeln, wenn der User Agent die Funktionalität durch User Preferences überschreibt.

### Querverweise

- `contenteditable`
- `lang`
- `autocorrect`
- Editing
- Forms

---

## `style`

### Feature-Typ

- Global Attribute
- CSS Integration
- Processing Model

### WHATWG-Bereich

- §3.2.5.5 The `style` attribute

### Semantik

`style` enthält CSS-Deklarationen, die als Inline Style des Elements verarbeitet werden.

### Wert

Der Attributwert wird als CSS Declaration Block interpretiert.

### CSS Integration

Die Bedeutung der einzelnen CSS-Eigenschaften wird nicht durch HTML definiert.

HTML definiert die Einbindung des Attributwertes in das CSS-/Rendering-Modell.

### DOM

`HTMLElement.style` stellt die zugehörige `CSSStyleDeclaration`-Schnittstelle bereit.

Das DOM-/CSSOM-Modell ist für die detaillierte API-Semantik maßgeblich.

### Querverweise

- CSS
- CSSOM
- Rendering
- Sanitization
- `nonce`
- CSP

---

## `tabindex`

### Feature-Typ

- Integer Attribute
- Focus
- Navigation
- Processing Model
- DOM API

### WHATWG-Bereich

- §6.6.3 The `tabindex` attribute

### Wert

Wenn angegeben, muss der Wert ein gültiger Integer sein.

Die geparste `tabindex`-Zahl kann:

- null
- negativ
- null beziehungsweise 0
- positiv

sein.

### Semantik

`tabindex` kann:

- ein Element beziehungsweise dessen Focusable Areas fokussierbar machen,
- sequenzielle Fokussierbarkeit beeinflussen,
- relative Reihenfolge innerhalb eines Focus Navigation Scope bestimmen.

### Negative Werte

Negative Werte verhindern grundsätzlich die sequenzielle Fokussierbarkeit.

Sie machen ein Element aber nicht automatisch unfokussierbar.

### Positive Werte

Positive Werte erzeugen eine relative Ordnung innerhalb des entsprechenden `tabindex`-geordneten Focus Navigation Scope.

Höhere Werte kommen dabei später.

### Null

`0` nimmt an der sequenziellen Fokusnavigation teil und wird in die entsprechende Ordnung eingeordnet.

### DOM

`HTMLElement.tabIndex` exponiert den Tabindex-Wert.

### Abgrenzung

`tabindex` ist nicht gleichbedeutend mit:

> „Position in einer globalen Tab-Reihenfolge“.

Das aktuelle HTML-Focus-Modell verwendet Focus Navigation Scopes und Shadow-DOM-bezogene Begriffe.

### Querverweise

- Focusable Area
- Focus Navigation Scope
- Shadow DOM
- `inert`
- disabled controls
- `autofocus`
- User Interaction

---

## `title`

### Feature-Typ

- Global Attribute
- Advisory Information
- Accessibility

### WHATWG-Bereich

- §3.2.5.1 The `title` attribute

### Semantik

`title` stellt Advisory Information über ein Element bereit.

Die konkrete Information kann beispielsweise sein:

- Zusatzinformation
- Beschreibung
- Tooltip-geeignete Information
- Hinweis zur Verwendung
- Information über ein Ziel
- ergänzende Information zu einer Quelle

### Wert

Der Wert ist Text.

### Accessibility

Die Spezifikation weist darauf hin, dass die alleinige Abhängigkeit von `title` für zugängliche Information problematisch ist.

Insbesondere können User Agents die Information nicht für alle Benutzergruppen gleichermaßen zugänglich präsentieren.

### Konformitätsgrundsatz

`title` soll nicht als universeller Ersatz für eine zugängliche Beschriftung oder Beschreibung behandelt werden.

### Querverweise

- Accessibility
- ARIA
- `aria-label`
- `aria-describedby`
- Links
- Images
- Interactive Content

---

## `translate`

### Feature-Typ

- Enumerated Attribute
- Internationalization
- Processing Model

### WHATWG-Bereich

- §3.2.5.3 The `translate` attribute

### Zustände

Das Attribut unterscheidet insbesondere:

- Translate
- No Translate

### Semantik

`translate` gibt an, ob Inhalte und bestimmte Attribute eines Elements für Übersetzungsprozesse als übersetzbar behandelt werden sollen.

### Vererbung

Der effektive Translate-Zustand kann aus dem nächsten relevanten Vorfahren übernommen werden.

### Übersetzbare Inhalte

Die Spezifikation unterscheidet zwischen:

- Textinhalt
- bestimmten Attributwerten
- Attributen, die explizit als translatable oder nicht translatable definiert sind.

### Querverweise

- Internationalization
- `lang`
- Metadata
- Microdata
- Text-Level Semantics

---

## `writingsuggestions`

### Feature-Typ

- Enumerated Attribute
- Editing
- Input Assistance
- Processing Model
- DOM API

### WHATWG-Bereich

- §6.8.6 Writing suggestions

### Zustände

- True
- False
- Default

Keywords:

- `true`
- `false`

Missing Value Default:

- Default

Invalid Value Default:

- True

Empty Value Default:

- True

### Berechnung

Der berechnete Writing-Suggestions-Wert berücksichtigt:

1. den eigenen Attributzustand,
2. gegebenenfalls den Elternzustand,
3. die dafür definierten Default-Regeln.

### Geeignete Kontexte

Die Spezifikation berücksichtigt insbesondere:

- geeignete `input`-Elemente
- `textarea`
- Editing Hosts
- editable Elements

### User Preferences

Der User kann Writing Suggestions deaktivieren.

Die IDL-Eigenschaft muss eine solche User Preference nicht unmittelbar widerspiegeln.

### DOM

`HTMLElement.writingSuggestions` liefert den berechneten Zustand entsprechend den WHATWG-Regeln.

### Querverweise

- `contenteditable`
- `autocapitalize`
- `autocorrect`
- `spellcheck`
- Forms
- Editing

---

## Gemeinsame Attribute außerhalb der 28er-HTML-Liste

## `class`

### Feature-Typ

- DOM-defined common attribute
- CSS Selector Integration

### Normative Quelle

DOM definiert die Anforderungen für `class` auf Elementen in beliebigen Namespaces.

HTML beschreibt die Verwendung auf HTML-Elementen.

### Semantik

`class` ist eine Menge durch ASCII-Whitespace getrennter Tokens.

Die Tokens repräsentieren Klassen, denen ein Element angehört.

### Querverweise

- DOM
- CSS Selectors
- `classList`
- `getElementsByClassName()`

---

## `id`

### Feature-Typ

- DOM-defined common attribute
- Identifier

### Normative Quelle

DOM definiert die allgemeinen Anforderungen.

### Semantik

`id` stellt einen Identifier für das Element bereit.

Der Identifier ist grundsätzlich opak.

Es darf keine zusätzliche Bedeutung allein aus dem konkreten Zeichenwert abgeleitet werden.

### Querverweise

- Fragment Navigation
- DOM
- CSS Selectors
- Labels
- Form Controls
- `itemref`

---

## `slot`

### Feature-Typ

- DOM-defined common attribute
- Shadow DOM
- Slot Assignment

### Normative Quelle

DOM definiert die allgemeinen Anforderungen für `slot`; HTML definiert die Integration in das HTML-/Shadow-DOM-Modell.

### Semantik

Ein Element mit `slot` kann einem gleichnamigen Slot im relevanten Shadow Tree zugewiesen werden.

### Querverweise

- Shadow DOM
- `<slot>`
- Custom Elements
- `lang`
- `hidden`
- Focus Navigation

---

## `data-*`

### Feature-Typ

- HTML Attribute Family
- Custom Data
- DOM API

### WHATWG-Bereich

- §3.2.5.6 Embedding custom non-visible data with the `data-*` attributes

### Semantik

`data-*` ermöglicht benutzerdefinierte, nicht sichtbare Daten auf HTML-Elementen.

Die Werte besitzen keine von HTML vorgegebene semantische Bedeutung.

### Syntax

Der Name muss mit `data-` beginnen und die für Custom Data Attributes definierten Namensregeln erfüllen.

### DOM

Das DOM stellt die Daten über `HTMLElement.dataset` beziehungsweise `DOMStringMap` bereit.

### Abgrenzung

`data-*` ist:

- kein einzelnes Attribut,
- keine endliche Attributliste,
- kein Custom Element,
- kein Microdata-System.

### Sanitization

Die Verwendung von `data-*` kann für Anwendungen und Frameworks relevant sein, die HTML sanitizen oder dynamisch interpretieren.

Die Existenz eines `data-*`-Attributes macht seinen Wert aber nicht automatisch vertrauenswürdig.

### Querverweise

- DOM
- `dataset`
- Sanitization
- Custom Elements
- Scripting

---

## Event-Handler-Content-Attributes

### Feature-Typ

- Attribute Family
- Events
- DOM API
- JavaScript Integration

### Abgrenzung

Event-Handler-Content-Attributes sind nicht Teil der 28 HTML-definierten Global Attributes.

Sie bilden eine eigene gemeinsame Attributfamilie.

Beispiele:

- `onclick`
- `oninput`
- `onchange`
- `onfocus`
- `onblur`
- `onkeydown`
- `onkeyup`
- `onbeforeinput`
- `onbeforematch`
- `onbeforetoggle`
- `onclose`
- `ondrag`
- `ondrop`
- `onload`
- `onsubmit`
- `ontoggle`

Die aktuelle Liste ist über die WHATWG-Event-Handler-Infrastruktur definiert und kann sich entsprechend dem Standard weiterentwickeln.

### Verarbeitung

Die Attribute stellen Event Handler Content Attributes dar.

Ihre Ausführung steht mit der Event-/DOM-/JavaScript-Verarbeitung in Verbindung.

### Security

Inline Event Handler besitzen eine unmittelbare Beziehung zur JavaScript-Ausführung und zu Content Security Policy.

Sie sind deshalb bei Sanitization und Security gesondert zu betrachten.

### Querverweise

- DOM Events
- `GlobalEventHandlers`
- JavaScript
- CSP
- Sanitizer API
- Scripting

---

## ARIA-Abgrenzung

### Feature-Typ

- externe normative Accessibility-Familie
- Integration Feature

### Attribute

Insbesondere:

- `role`
- `aria-*`

### Einordnung

Diese Attribute sind nicht als HTML-definierte Global Attributes der 28er-Liste zu zählen.

HTML enthält Regeln zur Integration von ARIA und zu Plattform-Accessibility-APIs, verweist für die eigentliche ARIA-Semantik aber auf die entsprechende Accessibility-Spezifikation.

### ZE-WebLab-Regel

ARIA darf in dieser Datei nicht als WHATWG-Global-Attribute inventarisiert werden.

Es muss vielmehr zwischen:

- HTML-Attribut
- DOM-Attribut
- ARIA-Attribut
- Accessibility API Mapping

unterschieden werden.

### Querverweise

- HTML §3.2.9 Requirements related to ARIA and platform accessibility APIs
- WAI-ARIA
- Accessibility API Mappings
- Element-specific semantics

---

## Content Categories

Global Attributes selbst besitzen keine Content Category.

Ihre Verwendung kann aber die Kategoriezugehörigkeit oder Verarbeitung eines Elements beeinflussen.

Beispiele:

- `href` kann bei `a` die Interactive-Content-Zuordnung beeinflussen.
- `popover` steht mit User Interaction in Verbindung.
- `itemscope` erzeugt Microdata-Strukturen.
- `contenteditable` verändert den Editing-Kontext.
- `hidden` verändert die Darstellung und Interaktion.
- `inert` verändert Interaktion und Accessibility.

Daher muss die Category-Zuordnung auf Elementebene bleiben.

Die Global-Attributes-Datei dokumentiert nur die relevanten Querverbindungen.

---

## Context

Global Attributes besitzen grundsätzlich globale Geltung.

Die konkrete Verarbeitung kann jedoch einen bestimmten Kontext voraussetzen.

Beispiele:

| Attribut | relevanter Kontext |
|---|---|
| `autofocus` | Fokus-/Dialog-/Popover-Kontext |
| `contenteditable` | Editing Context |
| `inputmode` | Eingabesituation |
| `enterkeyhint` | Eingabesituation |
| `spellcheck` | editierbarer Text |
| `autocapitalize` | Textinput / Editing Host |
| `autocorrect` | Textinput / Editing Host |
| `writingsuggestions` | Textinput / Editing Host |
| `popover` | Popover Context |
| `itemprop` | Microdata Item |
| `itemtype` | Microdata Item |
| `itemid` | Microdata Item |
| `itemref` | Microdata Item |
| `headingoffset` | Heading Context |
| `headingreset` | Heading Context |
| `nonce` | Security-/Resource-Verarbeitung |

Global bedeutet daher nicht kontextlos.

---

## Content Model

Global Attributes verändern grundsätzlich nicht das Content Model eines Elements.

Sie können jedoch Feature-Zustände beeinflussen, die mit Content Models interagieren.

Beispiele:

- `contenteditable` → Editing-Verarbeitung
- `hidden` → Rendering-/Interaction-Verarbeitung
- `inert` → Interaction-/Accessibility-Verarbeitung
- `popover` → Top-Layer-/Interaction-Verarbeitung
- `itemprop` → Microdata-Struktur

Das Content Model eines Elements bleibt in der jeweiligen Elementdefinition normativ.

---

## Processing Models

Global Attributes besitzen zahlreiche eigene Processing Models.

### Access Key Processing

`accesskey` wird über einen eigenen Verarbeitungsalgorithmus in eine vom User Agent zugewiesene Tastenkombination überführt.

### Autofocus Processing

`autofocus` wird über Autofocus Candidates und Scoping Roots verarbeitet.

### Hidden Ancestor Revealing

`hidden=until-found` verwendet einen Ancestor-Revealing-Mechanismus.

### Inertness

`inert` wird über die Berechnung inert gewordener Nodes und Flat-Tree-Beziehungen verarbeitet.

### Focus Navigation

`tabindex` ist Teil des Focus Navigation Models.

### Editing

`contenteditable`, `spellcheck`, `autocapitalize`, `autocorrect`, `inputmode`, `enterkeyhint` und `writingsuggestions` greifen in das Editing-/Input-Modell ein.

### Popover

`popover` besitzt ein eigenes Anzeigen-/Verbergen-/Toggle-/Light-Dismiss-/Top-Layer-Modell.

### Nonce

`nonce` besitzt einen internen kryptographischen Zustand und spezielle Attributänderungs-/Browsing-Context-Connected-Regeln.

### Microdata

`item*`-Attribute werden im Microdata-Modell durch eigene Algorithmen verarbeitet.

### Custom Elements

`is` ist Teil des Custom-Element-Definition-, Parsing- und Upgrade-Modells.

---

## DOM Interfaces / APIs

### `HTMLElement`

Viele Global Attributes werden über `HTMLElement` beziehungsweise dort eingebundene Interface Mixins exponiert.

Relevante IDL-Eigenschaften umfassen unter anderem:

- `accessKey`
- `accessKeyLabel`
- `autocapitalize`
- `autocorrect`
- `autofocus`
- `contentEditable`
- `isContentEditable`
- `dir`
- `draggable`
- `enterKeyHint`
- `headingOffset`
- `headingReset`
- `hidden`
- `inert`
- `inputMode`
- `lang`
- `nonce`
- `popover`
- `spellcheck`
- `style`
- `tabIndex`
- `title`
- `translate`
- `writingSuggestions`

### `ElementContentEditable`

Relevant:

- `contentEditable`
- `enterKeyHint`
- `isContentEditable`
- `inputMode`

### `HTMLOrSVGOrMathMLElement`

Relevant insbesondere für:

- `nonce`

### `CustomElementRegistry`

Relevant für:

- `is`
- customized built-in elements

### `DOMStringMap`

Relevant für:

- `data-*`
- `dataset`

### `GlobalEventHandlers`

Relevant für:

- Event-Handler-Content-Attributes

### DOM APIs

Für `class`, `id`, `slot` und weitere gemeinsame Attribute ist DOM die maßgebliche API-/IDL-Quelle.

---

## Accessibility

### Allgemeiner Grundsatz

Global Attributes dürfen nicht pauschal als Accessibility Features klassifiziert werden.

Die konkrete Accessibility-Wirkung ist featureabhängig.

### `lang`

Kann für Sprachinterpretation und Accessibility-Verarbeitung relevant sein.

### `title`

Kann ergänzende Information liefern, darf aber nicht als universell zugängliche Beschriftung betrachtet werden.

### `hidden`

Verbirgt Inhalte auch vor Accessibility-Verarbeitung beziehungsweise Assistive Technologies entsprechend dem definierten Hidden-Modell.

### `inert`

Ein inert Node wird grundsätzlich nicht gegenüber Accessibility APIs beziehungsweise Assistive Technologies exponiert.

### `tabindex`

Beeinflusst Fokusierbarkeit und damit Keyboard Accessibility.

### `contenteditable`

Erzeugt einen Editing-Kontext und kann damit erhebliche Accessibility-Auswirkungen besitzen.

### `popover`

Besitzt eigene Focus-/Interaction-Regeln und muss gemeinsam mit den Accessibility-Regeln des Popover-Inhalts betrachtet werden.

### `aria-*`

ARIA ist eine separate Accessibility-Spezifikation.

Die Attribute dürfen nicht als HTML-Global-Attribute der 28er-Liste gezählt werden.

### Externe Quelle

Für detaillierte Accessibility-Semantik und Accessibility API Mappings sind neben WHATWG die einschlägigen WAI-ARIA-/ARIA-Integration-Spezifikationen erforderlich.

---

## Sanitization

### Allgemein

Global Attributes sind für Sanitization relevant, weil viele davon direkt Verhalten, Script-Ausführung, Navigation, Interaktion oder Semantik beeinflussen.

### Besonders sicherheitsrelevant

#### `nonce`

Direkte Verbindung mit CSP und kryptographischen Nonces.

#### Event-Handler-Content-Attributes

`on*`-Attribute können JavaScript ausführen und sind deshalb für Sanitizer-Regeln besonders relevant.

#### `style`

Kann CSS einbringen und muss entsprechend dem verwendeten Sanitization-Modell betrachtet werden.

#### `data-*`

Besitzt keine eigene ausführbare Semantik, kann aber von Anwendungscode oder Frameworks interpretiert werden.

#### `id` und `name`

Können in DOM-Clobbering-Kontexten relevant sein.

### Sanitizer API

Die Sanitizer API definiert eigene Allow-/Remove-Regeln.

Die bloße Existenz eines Global Attributes bedeutet nicht automatisch, dass es vom Sanitizer erlaubt oder entfernt wird.

Sanitization ist daher ein separates Feature und darf nicht mit der HTML-Konformität eines Attributes verwechselt werden.

---

## Konformitätsregeln

### Globales Attribut ≠ universelle sinnvolle Verwendung

Ein Global Attribute kann formal global sein, aber dennoch fachlich nur in bestimmten Situationen sinnvoll oder wirksam sein.

### Attribute Values

Jedes Attribut muss die für seinen Typ definierten Wertregeln erfüllen.

Dabei sind insbesondere zu unterscheiden:

- Boolean Attributes
- Enumerated Attributes
- Integer Values
- Token Sets
- URLs
- BCP 47 Language Tags
- CSS Declaration Blocks
- Custom Element Names
- Microdata Values

### Unbekannte Werte

Bei enumerierten Attributen bestimmen die jeweiligen Spezifikationsregeln:

- Missing Value Default
- Invalid Value Default
- Empty Value Default

Ein unbekannter Wert darf daher nicht pauschal wie ein Boolean oder beliebiger String behandelt werden.

### Foreign Elements

Ein Attribut mit demselben Namen auf einem SVG- oder MathML-Element ist nicht automatisch das entsprechende HTML-Global-Attribute.

Namespace und Vocabulary müssen berücksichtigt werden.

### Custom Elements

Autonome Custom Elements können Global Attributes verwenden.

Customized built-in elements stehen zusätzlich mit `is` und dem Custom-Element-Modell in Verbindung.

---

## Status / V1

### WHATWG-Status

Die 28 aufgeführten HTML-Global-Attribute sind im aktuellen WHATWG HTML Living Standard definiert.

### Normative Definition

Die Attribute besitzen je nach Feature:

- normative Definitionen
- normative Wertregeln
- normative Zustände
- normative Processing Models
- normative DOM-/IDL-Anforderungen
- normative Konformitätsregeln

### Obsolete / Deprecated

In der aktuellen 28er-Liste befindet sich kein Attribut allein deshalb, weil es historisch oder deprecated wäre.

Obsolete beziehungsweise historische Attribute sind separat im WHATWG-Obsolete-Bereich zu behandeln.

### Browser-Kompatibilität

Browser-Support wird hier nicht als Status geführt.

Die WHATWG-Spezifikation und Browser-Kompatibilität sind getrennte Informationsdimensionen.

### ZE-WebLab-V1

Die V1-Zuordnung ist eine Projektklassifikation.

Für diese Feature-Familie gilt:

- **WHATWG:** definiertes HTML-Konzept
- **ZE-WebLab-V1:** zweite Rechercheebene / Global Attributes
- **Elementebene:** bereits in den zwölf Elementdateien teilweise referenziert
- **Zweite Ebene:** zentrale Feature-Familie

Die Tatsache, dass ein Attribut in einer V1-Elementdatei erwähnt wird, bedeutet nicht, dass die Global-Attribute-Familie dort vollständig dokumentiert wäre.

---

## Querverweise

### Element ↔ Global Attribute

Jedes Global Attribute kann auf HTML-Elementebene auftreten, soweit die jeweilige Definition keine zusätzliche Kontextregel enthält.

### Global Attribute ↔ DOM

- `class`
- `id`
- `slot`
- `dataset`
- IDL Reflection
- Interface Mixins

### Global Attribute ↔ Content Categories

Die Attribute selbst sind keine Content Categories.

Sie können aber die Semantik beziehungsweise Verarbeitung eines Elements beeinflussen.

### Global Attribute ↔ Content Models

Die Attribute definieren grundsätzlich keine neuen Content Models.

Einzelne Attribute können jedoch Processing Models beeinflussen, die auf Content-Model-Kontexten aufbauen.

### Global Attribute ↔ User Interaction

Besonders eng:

- `accesskey`
- `autofocus`
- `hidden`
- `inert`
- `popover`
- `tabindex`
- `draggable`

### Global Attribute ↔ Editing

Besonders eng:

- `contenteditable`
- `spellcheck`
- `autocapitalize`
- `autocorrect`
- `inputmode`
- `enterkeyhint`
- `writingsuggestions`

### Global Attribute ↔ Microdata

Besonders eng:

- `itemscope`
- `itemtype`
- `itemid`
- `itemprop`
- `itemref`

### Global Attribute ↔ Custom Elements

Besonders eng:

- `is`

### Global Attribute ↔ Security

Besonders eng:

- `nonce`
- Event Handler Attributes
- `style`

### Global Attribute ↔ Accessibility

Besonders eng:

- `lang`
- `title`
- `hidden`
- `inert`
- `tabindex`
- `contenteditable`
- `popover`

### Global Attribute ↔ SVG/MathML

`nonce` besitzt ausdrücklich eine gemeinsame HTML/SVG/MathML-Schnittstellenbeziehung.

Für andere Attribute gilt jeweils die Namespace-/Vocabulary-Abgrenzung.

---

## Abgrenzung zur ersten Rechercheebene

Die zwölf Elementdateien bleiben die primäre Referenz für einzelne HTML-Elemente.

Diese Datei behandelt dagegen das **übergreifende Attributsystem**.

### Bereits vorhandene erste-Ebene-Abdeckung

Die erste Ebene enthält bereits zahlreiche Verweise auf:

- `class`
- `id`
- `style`
- `title`
- `lang`
- `dir`
- `data-*`
- `hidden`
- `contenteditable`
- `tabindex`
- `popover`
- `nonce`
- `itemscope`
- `itemprop`
- weitere Attribute

Diese Angaben werden hier nicht als neue Elemente gezählt.

### Keine Duplizierung

Die vollständigen Definitionen von Elementen wie:

- `html`
- `a`
- `form`
- `input`
- `dialog`
- `script`
- `template`
- `slot`

bleiben in ihren jeweiligen Elementdateien.

Diese Datei verweist nur auf die gemeinsame Attributdimension.

---

## Erste-Ebene-Referenzen

### `01-document-element.md`

Bereits vorhandene Bezüge:

- Global Attributes
- `lang`
- `dir`
- `id`
- `class`
- `style`
- `title`
- `data-*`

Bewertung:

**teilweise abgedeckt; Global-Attribute-System nicht zentral dokumentiert.**

### `02-document-metadata.md`

Bereits vorhandene Bezüge unter anderem:

- `lang`
- `dir`
- `title`
- `style`
- `nonce`
- Link-/Metadata-bezogene Attribute

Bewertung:

**teilweise abgedeckt.**

### `03-sections.md`

Bereits vorhandene Bezüge:

- `id`
- `class`
- `lang`
- `dir`
- Heading-bezogene Konzepte

Bewertung:

**teilweise abgedeckt; Heading Global Attributes werden zentral ergänzt.**

### `04-grouping-content.md`

Bereits vorhandene Bezüge:

- `id`
- `class`
- `style`
- `lang`
- `dir`
- `hidden`

Bewertung:

**teilweise abgedeckt.**

### `05-text-level-semantics.md`

Bereits vorhandene Bezüge:

- `title`
- `lang`
- `dir`
- `class`
- `id`
- `style`
- `data-*`
- weitere elementbezogene Attribute

Bewertung:

**teilweise abgedeckt.**

### `06-links.md`

Bereits vorhandene Bezüge:

- `id`
- `class`
- `title`
- `download`
- `href`
- Link Types
- Navigation

Bewertung:

**Global-Attribute-Bezüge vorhanden; Link-spezifische Attribute bleiben dort.**

### `07-edits.md`

Bereits vorhandene Bezüge:

- `datetime`
- `cite`
- globale Attribute als gemeinsamer Rahmen

Bewertung:

**elementbezogene Attribute bleiben in Ebene 1.**

### `08-embedded-content.md`

Bereits vorhandene Bezüge:

- `id`
- `class`
- `style`
- `title`
- `hidden`
- `data-*`
- eingebettete Ressourcenattribute

Bewertung:

**teilweise abgedeckt.**

### `09-tabular-data.md`

Bereits vorhandene Bezüge:

- `id`
- `class`
- `style`
- Tabellenattribute
- DOM-Beziehungen

Bewertung:

**teilweise abgedeckt.**

### `10-forms.md`

Bereits vorhandene Bezüge:

- `autofocus`
- `autocomplete`
- `contenteditable`
- `spellcheck`
- `inputmode`
- `enterkeyhint`
- `autocapitalize`
- `autocorrect`
- `id`
- `class`
- `style`
- `title`
- weitere Form-Attribute

Bewertung:

**starke elementbezogene Abdeckung; zentrale Attributfamilie fehlt bislang.**

### `11-interactive-elements.md`

Bereits vorhandene Bezüge:

- `hidden`
- `inert`
- `popover`
- `tabindex`
- `autofocus`
- Commands
- Light Dismiss

Bewertung:

**starke Teilabdeckung; globale Systematik wird zentralisiert.**

### `12-scripting.md`

Bereits vorhandene Bezüge:

- `nonce`
- `data-*`
- `id`
- `class`
- `slot`
- `hidden`
- Shadow DOM
- Custom Elements
- APIs

Bewertung:

**starke Querschnittsabdeckung; `nonce`, `data-*`, `slot` und Custom-Element-Beziehungen werden hier systematisch eingeordnet.**

---

## Detailstatus des Inventars

| Feature | WHATWG-Status | Ebene-1-Abdeckung | Ebene-2-Status |
|---|---|---|---|
| `accesskey` | definiert | teilweise | vollständig geprüft |
| `autocapitalize` | definiert | teilweise | vollständig geprüft |
| `autocorrect` | definiert | teilweise | vollständig geprüft |
| `autofocus` | definiert | teilweise | vollständig geprüft |
| `contenteditable` | definiert | teilweise | vollständig geprüft |
| `dir` | definiert | teilweise | vollständig geprüft |
| `draggable` | definiert | teilweise | vollständig geprüft |
| `enterkeyhint` | definiert | teilweise | vollständig geprüft |
| `headingoffset` | definiert | teilweise | vollständig geprüft |
| `headingreset` | definiert | teilweise | vollständig geprüft |
| `hidden` | definiert | teilweise | vollständig geprüft |
| `inert` | definiert | teilweise | vollständig geprüft |
| `inputmode` | definiert | teilweise | vollständig geprüft |
| `is` | definiert | teilweise | vollständig geprüft |
| `itemid` | definiert | teilweise | vollständig geprüft |
| `itemprop` | definiert | teilweise | vollständig geprüft |
| `itemref` | definiert | teilweise | vollständig geprüft |
| `itemscope` | definiert | teilweise | vollständig geprüft |
| `itemtype` | definiert | teilweise | vollständig geprüft |
| `lang` | definiert | teilweise | vollständig geprüft |
| `nonce` | definiert | teilweise | vollständig geprüft |
| `popover` | definiert | teilweise | vollständig geprüft |
| `spellcheck` | definiert | teilweise | vollständig geprüft |
| `style` | definiert | teilweise | vollständig geprüft |
| `tabindex` | definiert | teilweise | vollständig geprüft |
| `title` | definiert | teilweise | vollständig geprüft |
| `translate` | definiert | teilweise | vollständig geprüft |
| `writingsuggestions` | definiert | teilweise | vollständig geprüft |

---

## Status der angrenzenden Attributfamilien

| Feature | Einordnung | Status |
|---|---|---|
| `class` | DOM-defined common attribute | separat zu DOM |
| `id` | DOM-defined common attribute | separat zu DOM |
| `slot` | DOM-defined common attribute | separat zu DOM / Shadow DOM |
| `data-*` | HTML common/custom-data feature | hier behandelt |
| `on*` | Event Handler Content Attributes | hier abgegrenzt, API separat |
| `role` | ARIA | externe normative Quelle |
| `aria-*` | ARIA | externe normative Quelle |

---

## Offene Punkte

### 1. Exakte vollständige Event-Handler-Liste

Die Event-Handler-Content-Attributes sind eine eigene Feature-Familie und werden deshalb hier nicht als zweites Global-Attribute-Inventar dupliziert.

Die vollständige aktuelle Event-Handler-Liste ist bei der späteren DOM-/Events-Datei erneut gegen den aktuellen WHATWG-Stand zu prüfen.

**Status:** bewusst ausgelagert.

### 2. Vollständige ARIA-Integration

WHATWG definiert die HTML-seitige Integration, aber die vollständige Semantik von `role` und `aria-*` liegt in externen Accessibility-Spezifikationen.

**Status:** nicht offen im Sinne einer fehlenden Recherche; bewusst externe Feature-Familie.

### 3. Vollständige CSS-Semantik von `style`

HTML definiert die Einbindung des `style`-Attributes.

Die vollständige Semantik der CSS-Deklarationen gehört nicht in die HTML-Referenz.

**Status:** bewusst CSS-/CSSOM-Querverweis.

### 4. Vollständige CSP-Semantik von `nonce`

HTML definiert den HTML-seitigen Nonce-Zustand und dessen Verarbeitung.

Die vollständige Policy-Semantik von Content Security Policy gehört in die CSP-Spezifikation.

**Status:** bewusst externe normative Abgrenzung.

### 5. Browser-Support

Nicht Bestandteil dieser Datei.

**Status:** separate Rechercheebene.

---

## Quellen / Referenzen

### Primärquelle

**WHATWG HTML Living Standard**

Relevante Abschnitte:

- §3.2.5 Global attributes
- §3.2.5.1 The `title` attribute
- §3.2.5.2 The `lang` and `xml:lang` attributes
- §3.2.5.3 The `translate` attribute
- §3.2.5.4 The `dir` attribute
- §3.2.5.5 The `style` attribute
- §3.2.5.6 Embedding custom non-visible data with the `data-*` attributes
- §3.2.7 `innerText` and `outerText`
- §3.2.8 Requirements relating to the bidirectional algorithm
- §3.2.9 Requirements related to ARIA and platform accessibility APIs
- §4.3.11 Headings and outlines
- §4.13 Custom elements
- §5 Microdata
- §6.1 The `hidden` attribute
- §6.3 Inert subtrees
- §6.6 Focus
- §6.7 Assigning keyboard shortcuts
- §6.8 Editing
- §6.11 Drag and drop
- §6.12 Popovers
- §2.5.6 Nonce attributes
- Rendering section for hidden elements
- DOM and event-handler infrastructure

### Projektquelle

**ZE-WebLab – GitHub Repository**

Geprüfte Bestandsdateien:

- `docs/html/01-document-element.md`
- `docs/html/02-document-metadata.md`
- `docs/html/03-sections.md`
- `docs/html/04-grouping-content.md`
- `docs/html/05-text-level-semantics.md`
- `docs/html/06-links.md`
- `docs/html/07-edits.md`
- `docs/html/08-embedded-content.md`
- `docs/html/09-tabular-data.md`
- `docs/html/10-forms.md`
- `docs/html/11-interactive-elements.md`
- `docs/html/12-scripting.md`

### Ergänzende normative Quellen

- DOM Standard für `class`, `id`, `slot` und zugehörige DOM-APIs
- WAI-ARIA für `role` und `aria-*`
- Content Security Policy für die Policy-Semantik von `nonce`
- CSS/CSSOM für die Semantik des `style`-Attributes
- BCP 47 für die Sprach-Tag-Syntax von `lang`

### Quellenbewertung

Die normative Priorität lautet:

1. WHATWG HTML Living Standard
2. ausdrücklich von WHATWG referenzierte normative Spezifikationen
3. ZE-WebLab als Projektbestandsquelle
4. Sekundärquellen nur ergänzend

Browser-Kompatibilitätsdaten wurden für diese Datei nicht als normative Quelle verwendet.

---

## Abschlussstatus

**Feature-Familie Global Attributes: vollständig recherchiert und für ZE-WebLab Ebene 2 dokumentiert.**

Die Datei behandelt:

- die 28 aktuellen HTML-definierten Global Attributes,
- DOM-definierte gemeinsame Attribute,
- `data-*`,
- Event-Handler-Abgrenzung,
- ARIA-Abgrenzung,
- Attribute-Wertmodelle,
- kontextabhängige Verarbeitung,
- Processing Models,
- DOM-/IDL-Beziehungen,
- Accessibility,
- Sanitization/Security,
- Custom Elements,
- Microdata,
- User Interaction,
- Editing,
- Focus,
- Rendering,
- Querverweise zur ersten Ebene,
- WHATWG-/V1-Status,
- offene beziehungsweise bewusst ausgelagerte Punkte.

Die Datei behandelt keine zusätzlichen HTML-Elemente. Attribute, APIs, Processing Models und externe Spezifikationskonzepte bleiben als eigene Informationsebenen getrennt.