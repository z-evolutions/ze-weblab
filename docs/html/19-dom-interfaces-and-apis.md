# ZE-WebLab – HTML-Referenz: DOM Interfaces und APIs

## Arbeitsstand / Quellenstand

- **Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien
- **Feature-Familie:** DOM Interfaces / APIs
- **Feature-Typ:** DOM Interface / API / Processing Model / normative HTML-DOM-Integration
- **Normative Primärquelle:** WHATWG HTML Living Standard
- **Aktueller WHATWG-Stand der Recherche:** 11. August 2026
- **ZE-WebLab-Projektquelle:** `docs/html/01-document-element.md` bis `docs/html/18-contexts.md`
- **Zieldatei:** `docs/html/19-dom-interfaces-and-apis.md`
- **Prüfstatus:** vollständig recherchiert für den in dieser Datei abgegrenzten HTML-DOM-/API-Bereich
- **Browser-Kompatibilität:** nicht Bestandteil dieser Datei
- **V1-Status:** projektspezifische Einstufung; nicht mit dem WHATWG-Status gleichzusetzen

### Quellenabgrenzung

Der WHATWG HTML Living Standard ist die normative Primärquelle für HTML-spezifische DOM-Interfaces, HTML-definierte IDL-Erweiterungen, HTML-spezifische API-Verarbeitung und die Integration von HTML mit dem DOM.

Der WHATWG DOM Standard bleibt die normative Quelle für allgemeine DOM-Kernkonzepte wie:

- `Node`
- `Element`
- `Document`
- `DocumentFragment`
- `NodeList`
- `HTMLCollection`
- Attribut- und Tree-Operationen
- Events
- Mutation Observer
- Namespaces
- grundlegende DOM-Manipulation

Diese Datei dokumentiert deshalb nicht den vollständigen DOM Standard.

Sie dokumentiert vielmehr:

1. die HTML-spezifische Erweiterung des DOM,
2. die HTML-definierten Interfaces,
3. die Beziehung zwischen HTML-Elementen und ihren DOM-Interfaces,
4. HTML-spezifische IDL-Mitglieder,
5. HTML-spezifische API-Verarbeitung,
6. gemeinsame HTML-DOM-Mechanismen,
7. Collections und spezielle HTML-DOM-Objekte,
8. HTML-Konstruktoren,
9. Custom-Element- und DOM-Beziehungen,
10. die Querverbindungen zwischen HTML, DOM, Parsing und anderen Feature-Familien.

### Abgrenzung zu den Elementreferenzen

Die Dateien `01` bis `12` dokumentieren HTML-Elemente.

Diese Datei dokumentiert dagegen die DOM-/API-Ebene.

Ein Beispiel:

- `button` ist ein HTML-Element.
- `HTMLButtonElement` ist dessen HTML-DOM-Interface.
- `HTMLElement` ist eine übergeordnete HTML-DOM-Schnittstelle.
- `Element` ist ein DOM-Konzept.
- `click()` ist ein API-Mitglied eines DOM-Interfaces.
- `CustomElementRegistry` ist ein API-Interface.
- ein Processing Model für ein IDL-Attribut ist kein HTML-Element.

Diese Ebenen dürfen nicht miteinander vermischt werden.

---

## Einordnung

### Was ist ein DOM Interface?

Ein DOM Interface ist eine durch Web IDL beschriebene Programmierschnittstelle, über die HTML- beziehungsweise DOM-Objekte aus Skripten angesprochen werden.

Beispielsweise:

```js
const button = document.querySelector("button");

button.disabled = true;
button.focus();
```

Das HTML-Element ist:

```html
<button>...</button>
```

Das zugehörige DOM-Objekt implementiert das für `button` vorgesehene Interface, insbesondere `HTMLButtonElement`.

### Was ist ein HTML-spezifisches DOM Interface?

HTML definiert oder erweitert Interfaces, die das Verhalten von HTML-Dokumenten und HTML-Elementen exponieren.

Beispiele:

- `Document`
- `HTMLElement`
- `HTMLHtmlElement`
- `HTMLHeadElement`
- `HTMLBodyElement`
- `HTMLFormElement`
- `HTMLInputElement`
- `HTMLButtonElement`
- `HTMLCanvasElement`
- `HTMLMediaElement`
- `HTMLScriptElement`
- `HTMLTemplateElement`
- `HTMLSlotElement`
- `HTMLUnknownElement`
- `HTMLAllCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`
- `RadioNodeList`
- `DOMStringMap`

Die vollständige Menge der elementbezogenen Interfaces wird jedoch nicht erneut als Elementinventar geführt. Die erste Ebene behandelt die Elementdefinitionen; diese Datei behandelt die übergreifende DOM-Systematik.

### DOM Interface ist nicht gleich HTML-Element

Ein Interface kann mehreren Elementtypen als gemeinsame Basisschnittstelle dienen.

Beispielsweise:

```text
HTMLElement
├── HTMLDivElement
├── HTMLParagraphElement
├── HTMLButtonElement
├── HTMLInputElement
└── ...
```

Umgekehrt kann ein DOM Interface auch durch HTML-spezifische Regeln erweitert werden, ohne dass dadurch ein neues HTML-Element entsteht.

### API ist nicht gleich Interface

Ein Interface beschreibt eine Programmierschnittstelle.

Ein API-Mitglied kann beispielsweise sein:

- Attribut
- Methode
- Konstruktor
- statische Methode
- Collection-Zugriff
- Event-bezogene Eigenschaft
- Zustandsexposition

Beispiel:

```text
Interface:
    HTMLInputElement

API-Mitglieder:
    value
    checked
    disabled
    form
    select()
    setRangeText()
    setSelectionRange()
```

---

## WHATWG-Struktur

### Relevante zentrale Bereiche

Die aktuelle WHATWG-Systematik verteilt die HTML-DOM-Themen über mehrere Abschnitte.

Für diese Feature-Familie sind insbesondere relevant:

- §2.6 Common DOM interfaces
- §3.1 Documents
- §3.2 Elements
- §3.2.2 Elements in the DOM
- §3.2.3 HTML element constructors
- §3.2.4 Element definitions
- §3.2.6 Global attributes
- §3.2.7 `innerText` und `outerText`
- §3.2.9 ARIA und Platform Accessibility APIs
- §4 The elements of HTML
- §4.13 Custom elements
- weitere HTML-Featurebereiche mit eigenen DOM-Interfaces und APIs

### §2.6 Common DOM interfaces

Der zentrale allgemeine HTML-spezifische DOM-Hilfsbereich behandelt:

- Reflection von Content Attributes auf IDL Attributes
- `reflect`
- Reflection-Algorithmen
- Collections
- `HTMLAllCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`
- `RadioNodeList`
- `DOMStringList`

### §3.1 Documents

Der Dokumentbereich behandelt insbesondere:

- `Document`
- HTML-spezifische Erweiterungen des `Document`-Interfaces
- Dokumentzustände
- Dokumentzugriff
- Dokumentmetadaten
- DOM-Tree-Accessor
- dynamische Markup-Insertion
- Script-bezogene Dokumentzustände
- named properties
- document-spezifische API-Verarbeitung

### §3.2 Elements

Der Elementbereich behandelt insbesondere:

- Elemente im DOM
- Elementtypen
- HTML-Element-Interfaces
- Konstruktoren
- `[HTMLConstructor]`
- Interface-Ermittlung
- gemeinsame HTML-/SVG-/MathML-Funktionen
- Content Attributes
- IDL Attributes
- Beziehungen zu Content Categories und Content Models

### §4 The elements of HTML

Jede HTML-Elementdefinition kann ein eigenes DOM Interface enthalten.

Beispielhafte Zuordnung:

```text
html       → HTMLHtmlElement
head       → HTMLHeadElement
title      → HTMLTitleElement
body       → HTMLBodyElement
form       → HTMLFormElement
input      → HTMLInputElement
button     → HTMLButtonElement
canvas     → HTMLCanvasElement
script     → HTMLScriptElement
template   → HTMLTemplateElement
slot       → HTMLSlotElement
```

Die Elementdefinitionen bleiben jedoch Bestandteil der ersten Rechercheebene.

### §4.13 Custom elements

Custom Elements bilden eine eigenständige Feature-Familie in `17-custom-elements.md`.

Diese Datei dokumentiert deshalb nur die DOM-/API-Beziehungen:

- `CustomElementRegistry`
- Elementkonstruktion
- `HTMLElement`
- Element-Interfaces
- `ElementInternals`
- Lifecycle-Integration
- DOM-Erzeugung und Upgrade
- API-/IDL-Beziehungen

Die vollständige Custom-Elements-Systematik bleibt in `17-custom-elements.md`.

---

## Inventar

### 1. Zentrale HTML-DOM-Interfaces

| Interface | Ebene | Funktion |
|---|---|---|
| `Document` | HTML erweitert DOM | Repräsentation des HTML-Dokuments und HTML-spezifische Dokument-APIs |
| `HTMLElement` | HTML | gemeinsame Basis für HTML-Element-Interfaces |
| `HTMLUnknownElement` | HTML | Interface für unbekannte beziehungsweise nicht speziell zugeordnete HTML-Elementtypen |
| `HTMLHtmlElement` | HTML | DOM-Interface für `html` |
| `HTMLHeadElement` | HTML | DOM-Interface für `head` |
| `HTMLTitleElement` | HTML | DOM-Interface für `title` |
| `HTMLBaseElement` | HTML | DOM-Interface für `base` |
| `HTMLLinkElement` | HTML | DOM-Interface für `link` |
| `HTMLMetaElement` | HTML | DOM-Interface für `meta` |
| `HTMLStyleElement` | HTML | DOM-Interface für `style` |
| `HTMLBodyElement` | HTML | DOM-Interface für `body` |
| `HTMLFormElement` | HTML | DOM-Interface für `form` |
| `HTMLInputElement` | HTML | DOM-Interface für `input` |
| `HTMLButtonElement` | HTML | DOM-Interface für `button` |
| `HTMLSelectElement` | HTML | DOM-Interface für `select` |
| `HTMLTextAreaElement` | HTML | DOM-Interface für `textarea` |
| `HTMLOptionElement` | HTML | DOM-Interface für `option` |
| `HTMLOptGroupElement` | HTML | DOM-Interface für `optgroup` |
| `HTMLScriptElement` | HTML | DOM-Interface für `script` |
| `HTMLTemplateElement` | HTML | DOM-Interface für `template` |
| `HTMLSlotElement` | HTML | DOM-Interface für `slot` |
| `HTMLCanvasElement` | HTML | DOM-Interface für `canvas` |
| `HTMLMediaElement` | HTML | gemeinsame DOM-Basis für Audio-/Video-Funktionen |
| `HTMLImageElement` | HTML | DOM-Interface für `img` |
| `HTMLIFrameElement` | HTML | DOM-Interface für `iframe` |
| `HTMLObjectElement` | HTML | DOM-Interface für `object` |
| `HTMLEmbedElement` | HTML | DOM-Interface für `embed` |

Die Liste ist bewusst keine zweite Elementinventarliste.

### 2. Gemeinsame beziehungsweise DOM-definierte Interfaces

Für HTML relevant sind außerdem DOM-definierte Interfaces wie:

- `Node`
- `Element`
- `Document`
- `DocumentFragment`
- `Text`
- `Comment`
- `NodeList`
- `HTMLCollection`
- `DOMTokenList`
- `DOMStringMap`

Diese Interfaces dürfen nicht als HTML-eigene Interfaces klassifiziert werden, wenn ihre normative Definition aus DOM stammt.

HTML kann diese Interfaces jedoch erweitern oder für HTML-spezifische Verarbeitung verwenden.

### 3. HTML-spezifische Collections

Besonders relevant sind:

- `HTMLAllCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`
- `RadioNodeList`

### 4. Weitere API-Konzepte

HTML definiert oder erweitert außerdem API-Konzepte für:

- Dokumentzugriff
- Elementerzeugung
- HTML-Konstruktoren
- Form Controls
- Medien
- Scripting
- Templates
- Slots
- Custom Elements
- Element Internals
- Navigation und Dokumentzustände
- Markup Parsing
- dynamische Markup-Insertion

---

## Begriffsdefinitionen

### Content Attribute

Ein Content Attribute ist das Attribut eines DOM-Elements, das im HTML-Markup beziehungsweise im DOM-Attributmodell repräsentiert wird.

Beispiel:

```html
<input disabled>
```

Das Content Attribute ist:

```text
disabled
```

### IDL Attribute

Ein IDL Attribute ist eine Eigenschaft eines DOM-Interfaces.

Beispiel:

```js
input.disabled
```

Das IDL Attribute muss nicht einfach den Text des Content Attributes zurückgeben.

### Reflection

Reflection bezeichnet die normativ definierte Beziehung zwischen einem Content Attribute und einem IDL Attribute.

Beispiel:

```html
<input id="search">
```

kann über:

```js
input.id
```

zugänglich sein.

Die genaue Reflection hängt vom definierten Typ und vom jeweiligen Attributmodell ab.

### Boolean Reflection

Bei Boolean Attributes wird die Anwesenheit des Content Attributes in einen booleschen IDL-Zustand übersetzt.

Beispiel:

```html
<button disabled></button>
```

führt typischerweise zu:

```js
button.disabled === true
```

### Enumerated Reflection

Enumerated Content Attributes können über definierte Zustände und Keywords verarbeitet werden.

Der IDL Getter muss dabei nicht zwangsläufig den rohen Attributstring zurückgeben.

### URL Reflection

Bei bestimmten URL-bezogenen IDL Attributes wird der Attributwert relativ zum entsprechenden Dokumentkontext verarbeitet.

Das Ergebnis kann daher vom wörtlichen Markupstring abweichen.

### DOM Interface

Ein DOM Interface definiert die durch Web IDL beschriebene API-Oberfläche eines DOM-Objekts.

### Interface Mixin

Ein Interface Mixin stellt gemeinsame API-Mitglieder bereit, die von mehreren Interfaces verwendet werden können.

HTML verwendet solche Mechanismen insbesondere für gemeinsame Funktionalität von HTML-, SVG- und MathML-Elementen.

### HTML Constructor

`[HTMLConstructor]` ist ein Web-IDL-bezogener Mechanismus, mit dem HTML-spezifische Konstruktorsemantik für HTML-Element-Interfaces definiert wird.

### Named Properties

Bestimmte HTML-Objekte unterstützen named properties.

Dazu gehören insbesondere:

- `Document`
- bestimmte HTML Collections
- historische Mechanismen wie `document.all`

Named Properties sind keine normalen JavaScript-Objekteigenschaften ohne weitere normative Regeln.

---

## Normative Regeln

### HTML erweitert DOM

HTML verwendet den DOM Standard als grundlegende Objekt- und Baumstruktur.

HTML definiert darauf aufbauend zusätzliche Semantik und API-Verarbeitung.

Die beiden Spezifikationen sind deshalb nicht austauschbar.

### DOM-Interface eines Elements

Die HTML-Spezifikation bestimmt für einen HTML-Elementtyp, welches Interface für diesen Elementtyp verwendet wird.

Die Ermittlung erfolgt anhand von:

1. Elementtyp beziehungsweise local name,
2. Namespace,
3. HTML-Definition,
4. gegebenenfalls Definitionen anderer anwendbarer Spezifikationen,
5. Custom-Element-Regeln,
6. Fallback auf `HTMLUnknownElement` beziehungsweise `HTMLElement` entsprechend der normativen Regeln.

### HTML-Elemente im HTML Namespace

Ein HTML-Element im HTML Namespace erhält die für seinen Elementtyp vorgesehene HTML-Interface-Zuordnung.

Ein Element mit gleichem local name in einem anderen Namespace erhält dadurch nicht automatisch dasselbe HTML-Interface.

### Custom Element Names

Ein gültiger Custom Element Name führt nicht automatisch zu einem nativen HTML-Element-Interface.

Autonome Custom Elements basieren auf `HTMLElement`, sofern die Custom-Element-Definition dies entsprechend festlegt.

### Customized Built-In Elements

Customized Built-In Elements erweitern ein vorhandenes HTML-Element-Interface.

Die Zuordnung des nativen Elementtyps bleibt dabei Bestandteil der Konstruktor- und Custom-Element-Verarbeitung.

### Gemeinsame HTML-/SVG-/MathML-Features

HTML definiert gemeinsame Funktionalität über gemeinsame Interfaces beziehungsweise Mixins.

Das bedeutet nicht, dass HTML-, SVG- und MathML-Elemente identische Interfaces besitzen.

Es bedeutet vielmehr, dass bestimmte API-Mitglieder über eine gemeinsame normative Abstraktion bereitgestellt werden können.

### DOM API kann nicht-konforme Markup-Strukturen erzeugen

Die Existenz eines DOM-Knotens bedeutet nicht automatisch, dass dieselbe Struktur in `text/html` konform autorisiert werden darf.

Beispiel:

```js
const element = document.createElement("div");
```

ist eine DOM-Operation.

Ob ein entsprechendes `div` an einer bestimmten Position im HTML-Markup konform wäre, ist eine Frage der HTML-Content-Model- und Context-Regeln.

### DOM-Manipulation und HTML-Konformität sind getrennt

Die DOM-API beschreibt, welche Operationen programmgesteuert durchgeführt werden können.

HTML-Konformitätsanforderungen beschreiben, welche Dokumentstruktur Autoren erzeugen dürfen.

Diese beiden Ebenen dürfen nicht vermischt werden.

---

## Detailprüfung

## `Document`

### Feature-Typ

- DOM Interface
- HTML Interface Extension
- API
- Processing Model

### WHATWG-Bereich

- §3.1 Documents
- §3.1.1 The `Document` object
- §3.1.2 `DocumentOrShadowRoot`
- §3.1.3 Ancestor origins
- §3.1.4 Resource metadata management
- §3.1.5 Reporting document loading status
- §3.1.6 Render-blocking mechanism
- §3.1.7 DOM tree accessors

### Herkunft

`Document` ist ein DOM-Interface.

HTML erweitert dieses Interface um HTML-spezifische Attribute und Methoden.

### HTML-spezifische API-Beispiele

Unter anderem relevant:

```js
document.title
document.body
document.head
document.images
document.forms
document.scripts
document.currentScript
document.getElementsByName()
```

Weitere Mitglieder werden in den jeweils zuständigen HTML-Featurefamilien behandelt.

### `Document.title`

`document.title` ist mit der HTML-Dokumenttitelverarbeitung verbunden.

Die zugrunde liegende Verarbeitung berücksichtigt die Dokumentstruktur und unterscheidet insbesondere HTML- und SVG-Dokumentkontexte.

### `Document.body`

`document.body` liefert das für das Dokument bestimmte `body`- beziehungsweise `frameset`-Element oder `null`.

Der Setter besitzt normative Einschränkungen.

Eine beliebige `HTMLElement`-Instanz kann nicht als neuer Dokumentkörper eingesetzt werden.

### `Document.head`

`document.head` liefert das `head`-Element des HTML-Dokuments beziehungsweise `null`, wenn kein entsprechendes Element vorhanden ist.

### `Document.images`

`document.images` ist eine `HTMLCollection` mit einer HTML-spezifischen Filterdefinition.

### `Document.forms`

`document.forms` ist eine HTML Collection der entsprechenden Formularelemente.

### `Document.scripts`

`document.scripts` ist eine HTML Collection der entsprechenden `script`-Elemente.

### `Document.currentScript`

`document.currentScript` liefert das aktuell ausgeführte klassische Script unter den von WHATWG definierten Bedingungen.

Es gilt insbesondere:

- nicht für alle Scriptarten,
- nicht als allgemeiner Mechanismus für beliebige JavaScript-Ausführung,
- nicht für Module in derselben Weise,
- nicht automatisch für Shadow Trees.

Die API besitzt damit einen klar abgegrenzten historischen beziehungsweise klassischen Script-Anwendungsbereich.

---

## `HTMLElement`

### Feature-Typ

- DOM Interface
- HTML Base Interface
- API
- Interface inheritance

### Bedeutung

`HTMLElement` bildet die gemeinsame HTML-spezifische Basisschnittstelle für HTML-Elemente.

Viele HTML-Element-Interfaces erben mittelbar oder unmittelbar von `HTMLElement`.

### Gemeinsame API-Bereiche

Je nach aktueller WHATWG-Definition gehören unter anderem folgende gemeinsame HTML-Funktionen zum HTMLElement-Bereich:

- globale Attribute
- Fokus
- Editing
- Drag and Drop
- `dataset`
- `nonce`
- `tabIndex`
- `focus()`
- `blur()`
- weitere HTML-spezifische gemeinsame Mitglieder

Die konkrete Definition einzelner Attribute verbleibt in den jeweils zuständigen Featurefamilien.

### Vererbung

Vereinfacht:

```text
EventTarget
└── Node
    └── Element
        └── HTMLElement
            ├── HTMLDivElement
            ├── HTMLButtonElement
            ├── HTMLInputElement
            └── ...
```

Die exakte Vererbung einzelner Interfaces wird durch DOM, HTML und Web IDL bestimmt.

---

## `HTMLOrSVGOrMathMLElement`

### Feature-Typ

- Interface Mixin
- Integration Feature
- DOM API

### Bedeutung

HTML verwendet eine gemeinsame Interface-Abstraktion für bestimmte Features, die HTML-, SVG- und MathML-Elementen gemeinsam sind.

Dazu können insbesondere gehören:

- `dataset`
- `nonce`
- `autofocus`
- `tabIndex`
- `focus()`
- `blur()`

Die gemeinsame Abstraktion bedeutet nicht, dass die jeweiligen Elementinterfaces identisch sind.

### Integrationsbezug

Diese Systematik ist besonders relevant für:

- HTML
- SVG
- MathML
- Namespaces
- Foreign Content
- DOM
- Parsing

Die vollständigen SVG-/MathML-Integrationsregeln werden in späteren Integrationsdateien behandelt.

---

## `HTMLUnknownElement`

### Feature-Typ

- DOM Interface
- Element Interface
- Fallback Interface

### Bedeutung

`HTMLUnknownElement` ist das HTML-Interface für HTML-Elementnamen, für die keine passend definierte spezielle HTML-Interface-Zuordnung vorliegt und die nicht aufgrund der Custom-Element-Regeln als `HTMLElement` behandelt werden.

### Custom-Element-Abgrenzung

Ein gültiger Custom Element Name führt nicht einfach zu `HTMLUnknownElement`.

Die HTML-Spezifikation verwendet für gültige Custom Element Names `HTMLElement` als Ausgangspunkt, damit spätere Upgrades eine definierte Prototypstruktur erhalten können.

---

## HTML-Element-Konstruktoren

### Feature-Typ

- API
- DOM Interface
- Constructor Processing Model
- Custom Elements Integration

### WHATWG-Bereich

- §3.2.3 HTML element constructors

### `[HTMLConstructor]`

HTML-Element-Interfaces können mit `[HTMLConstructor]` versehen sein.

Dieser Mechanismus definiert besondere Konstruktorregeln.

Er ist nicht mit einem beliebigen JavaScript-Konstruktor gleichzusetzen.

### Zweck

Die Konstruktorregeln sind insbesondere erforderlich für:

- native HTML-Element-Interfaces,
- Custom Elements,
- customized built-in elements,
- korrekte Zuordnung des `NewTarget`,
- Custom-Element-Registry,
- Konstruktor- und Upgrade-Verarbeitung.

### Konstruktoraufruf

Ein HTML-Element-Konstruktor kann nicht beliebig wie eine normale Klasse verwendet werden.

Die WHATWG definiert Prüfungen für:

- `NewTarget`
- aktiven Konstruktor
- Registry
- Custom-Element-Definition
- local name
- Namespace
- Custom-Element-State
- Construction Stack

### Named Constructors

Einige HTML-APIs besitzen historische beziehungsweise spezielle named constructors.

Diese sind von normalen Interface-Konstruktoren zu unterscheiden.

---

## Element Interface Lookup

### Feature-Typ

- Processing Model
- DOM Interface Resolution
- HTML Integration

### Grundprinzip

Bei der Erzeugung eines Elements muss bestimmt werden, welches Interface das Objekt implementiert.

Die normative Verarbeitung berücksichtigt:

1. Namespace,
2. local name,
3. HTML-Definition,
4. andere anwendbare Spezifikationen,
5. Custom-Element-Regeln,
6. Fallback-Regeln.

### Ergebnis

Mögliche Ergebnisse können unter anderem sein:

- spezifisches HTML-Interface,
- `HTMLElement`,
- `HTMLUnknownElement`,
- Interface aus einer anderen anwendbaren Spezifikation.

### Custom Elements

Bei einem gültigen Custom Element Name ist die Ausgangsbasis `HTMLElement`, bevor eine spätere Custom-Element-Definition das Objekt auf ein spezielleres Interface beziehungsweise eine entsprechende Prototypkette hebt.

---

## Common DOM Interfaces

## Reflection von Content Attributes auf IDL Attributes

### Feature-Typ

- API Processing Model
- IDL
- Attribute Processing

### WHATWG-Bereich

- §2.6.1 Reflecting content attributes in IDL attributes

### Grundprinzip

Ein reflektierendes IDL Attribute stellt eine definierte Beziehung zu einem Content Attribute her.

Die Getter- und Setter-Semantik ist abhängig vom Typ des reflektierten Attributes.

### Unterstützte Reflection-Modelle

WHATWG definiert unter anderem Regeln für:

- `DOMString`
- nullable `DOMString`
- `USVString`
- Boolean
- Integer
- nicht-negative Integer
- unsigned Integer
- clamped Integer
- `DOMTokenList`
- Elementreferenzen
- Listen beziehungsweise Collection-bezogene Reflection

### Wichtig

Reflection bedeutet nicht:

```text
IDL-Wert = immer exakt derselbe String wie im Markup
```

Je nach Attributtyp kann der Getter:

- normalisieren,
- Keywords kanonisieren,
- Default-Zustände liefern,
- Werte parsen,
- URLs auflösen,
- boolesche Zustände liefern,
- Exceptions auslösen.

---

## Enumerated Attribute Reflection

Enumerated Content Attributes besitzen Zustände und Keywords.

Ein IDL Getter kann dabei:

- einen kanonischen Keyword-Wert,
- einen leeren String,
- `null`,
- oder einen anderen definierten Zustand

zurückgeben.

Der rohe Content-Attribute-String und der verarbeitete IDL-Zustand sind deshalb nicht automatisch identisch.

---

## Boolean Attribute Reflection

Boolean Attributes werden über ihre Anwesenheit interpretiert.

Beispiel:

```html
<input disabled>
```

Der zugehörige IDL-Zustand ist:

```js
input.disabled === true
```

Ein beliebiger String wie:

```html
<input disabled="false">
```

macht ein Boolean Attribute nicht semantisch falsch beziehungsweise `false`.

Die Anwesenheit des Attributes ist entscheidend.

---

## Integer Reflection

Numerische IDL Attributes können definierte Parsingregeln besitzen.

Je nach Definition können relevant sein:

- Integer Parsing
- Non-negative Integer Parsing
- Bereichsgrenzen
- Default Values
- Fehlerzustände
- Clamping
- Exceptions beim Setzen

Diese Regeln dürfen nicht durch eine allgemeine JavaScript-Konvertierungsannahme ersetzt werden.

---

## `DOMTokenList`

`DOMTokenList` ist ein DOM-Interface.

HTML verwendet es unter anderem für Attribute, deren Werte als Token-Mengen modelliert sind.

Beispiel:

```js
element.classList.add("active");
element.classList.remove("active");
element.classList.contains("active");
```

`DOMTokenList` selbst ist keine HTML-spezifische Interfacefamilie.

Die konkrete Verwendung eines `DOMTokenList`-IDL-Attributes wird jeweils durch das zuständige Feature definiert.

---

## `DOMStringMap` und `dataset`

### Feature-Typ

- DOM Interface
- HTML API
- Attribute API

### HTML-Bezug

`data-*`-Attribute werden über `HTMLElement.dataset` beziehungsweise `DOMStringMap` programmgesteuert zugänglich.

Beispiel:

```html
<div data-user-id="42" data-user-name="Sascha"></div>
```

Zugriff:

```js
element.dataset.userId
element.dataset.userName
```

### Namensumwandlung

Die HTML-Spezifikation definiert eine konkrete Umwandlung zwischen:

```text
data-user-id
```

und:

```text
userId
```

Die Umwandlung ist algorithmisch definiert.

### Schreibzugriff

Ein Schreibzugriff wie:

```js
element.dataset.userId = "43";
```

führt zur entsprechenden Erzeugung beziehungsweise Änderung des `data-*`-Attributes.

### Fehlerfälle

Bestimmte Property-Namen können aufgrund der vorgeschriebenen Umwandlung zu ungültigen Attributnamen führen.

Die Spezifikation definiert dafür entsprechende Exceptions.

---

## Collections

### Feature-Typ

- DOM Interface
- Collection API
- Live Collection
- Named Properties

### Allgemeine DOM Collections

DOM definiert unter anderem:

- `NodeList`
- `HTMLCollection`

HTML verwendet diese Interfaces und definiert darauf aufbauend zusätzliche Collections.

### Live Collections

Einige HTML Collections repräsentieren eine dynamische Sicht auf den DOM.

Die konkrete Live-Semantik ist Bestandteil der jeweiligen Interface-Definition.

### Tree Order

Viele Collection-Ergebnisse werden in Tree Order bestimmt.

Das bedeutet, dass die Reihenfolge nicht einfach der Erstellungsreihenfolge eines Objekts entsprechen muss.

---

## `HTMLAllCollection`

### Feature-Typ

- Legacy API
- DOM Interface
- Collection
- Named Properties
- JavaScript Integration

### Bedeutung

`HTMLAllCollection` ist das Interface hinter dem historischen:

```js
document.all
```

### Legacy-Verhalten

Die Spezifikation definiert für dieses Objekt besondere JavaScript-Integrationsregeln.

Unter anderem besitzt es:

- spezielle Boolean-Konvertierung,
- spezielles Verhalten bei Loose Equality,
- spezielles `typeof`-Verhalten,
- ein `[[IsHTMLDDA]]`-internes Slot,
- ein eigenes `[[Call]]`-Verhalten.

### Status

Das Feature ist historisch beziehungsweise legacy-geprägt.

Es ist nicht als modernes allgemeines DOM-Collection-Modell zu verwenden.

### ZE-WebLab-Einstufung

- **WHATWG:** definiert
- **Feature-Typ:** Legacy DOM/API
- **V1:** nur dokumentarisch
- **Browser-Support:** separate Rechercheebene

---

## `HTMLFormControlsCollection`

### Feature-Typ

- HTML DOM Interface
- Form API
- Collection

### Bedeutung

`HTMLFormControlsCollection` repräsentiert die gelisteten Form Controls eines Formulars.

### Vererbung

```text
HTMLCollection
└── HTMLFormControlsCollection
```

### `namedItem()`

`namedItem()` kann abhängig von der Anzahl und Art der Treffer:

- ein einzelnes Element,
- `null`,
- oder eine `RadioNodeList`

liefern.

### Querverweise

- `10-forms.md`
- `15-content-models.md`
- DOM
- Form-associated Elements

---

## `RadioNodeList`

### Feature-Typ

- DOM Interface
- Form API
- Collection

### Bedeutung

`RadioNodeList` repräsentiert eine Gruppe von Form Controls, die über eine Namens- beziehungsweise ID-Zuordnung zusammengehören können.

### API

Insbesondere:

```js
radioNodeList.value
```

liefert beziehungsweise setzt den für die Radio- beziehungsweise Form-Control-Gruppe definierten Wert.

### Beziehung zu `HTMLFormControlsCollection`

`HTMLFormControlsCollection.namedItem()` kann eine `RadioNodeList` zurückgeben, wenn mehrere passende Controls gefunden werden.

---

## `HTMLOptionsCollection`

### Feature-Typ

- HTML DOM Interface
- Form API
- Collection
- Mutation API

### Bedeutung

`HTMLOptionsCollection` repräsentiert die `option`-Elemente eines `select`-Elements.

### Vererbung

```text
HTMLCollection
└── HTMLOptionsCollection
```

### API-Mitglieder

Unter anderem:

- `length`
- indexed getter/setter
- `add()`
- `remove()`
- `selectedIndex`

### Besondere Verarbeitung

Die Setter- und Mutationsregeln können tatsächlich DOM-Operationen auslösen.

Beispielsweise kann eine Änderung von `length` neue leere `option`-Elemente erzeugen oder vorhandene Elemente entfernen.

---

## `DOMStringList`

### Feature-Typ

- DOM Interface
- Legacy/Compatibility API

### Bedeutung

`DOMStringList` stellt eine Liste von Strings mit:

- `length`
- `item()`
- `contains()`

bereit.

### Status

WHATWG weist ausdrücklich darauf hin, dass neue APIs `sequence<DOMString>` oder vergleichbare moderne Web-IDL-Typen statt `DOMStringList` verwenden sollen.

### ZE-WebLab-Einstufung

- **WHATWG:** definiert
- **Feature-Typ:** Legacy-/Kompatibilitätsinterface
- **V1:** dokumentarisch
- **Neuentwicklung:** nicht als bevorzugtes API-Modell

---

## DOM Interfaces / APIs in den Elementfamilien

Die erste Rechercheebene enthält elementbezogene API-Informationen.

Beispiele für die Beziehung:

| Element | DOM Interface | Typische API-Ebene |
|---|---|---|
| `html` | `HTMLHtmlElement` | Dokumentwurzel |
| `head` | `HTMLHeadElement` | Metadaten |
| `title` | `HTMLTitleElement` | `text` |
| `base` | `HTMLBaseElement` | `href`, `target` |
| `form` | `HTMLFormElement` | Form API |
| `input` | `HTMLInputElement` | Value, Selection, Validation |
| `button` | `HTMLButtonElement` | Button State |
| `select` | `HTMLSelectElement` | Options, Selection |
| `textarea` | `HTMLTextAreaElement` | Value, Selection |
| `script` | `HTMLScriptElement` | Script Attributes |
| `template` | `HTMLTemplateElement` | `content` |
| `slot` | `HTMLSlotElement` | Slot Assignment |
| `canvas` | `HTMLCanvasElement` | Rendering Context API |
| `audio` | `HTMLAudioElement` / `HTMLMediaElement` | Media API |
| `video` | `HTMLVideoElement` / `HTMLMediaElement` | Media API |

Diese Tabelle dient der Querverweisstruktur und ersetzt nicht die jeweiligen Elementdefinitionen.

---

## API-Verarbeitung

### IDL ist normativ

Die Web-IDL-Deklaration ist Teil der normativen API-Beschreibung.

Beispiel:

```text
interface HTMLButtonElement : HTMLElement {
    ...
};
```

Die IDL definiert unter anderem:

- Interface-Vererbung
- Attribute
- Methoden
- Typen
- optionale Parameter
- Exceptions
- Extended Attributes
- Exposure

### Getter und Setter

Ein IDL Attribute kann eigene normative Getter- und Setter-Schritte besitzen.

Daher ist:

```js
element.foo
```

nicht bloß ein direkter Zugriff auf einen gespeicherten JavaScript-Wert.

### `[CEReactions]`

HTML verwendet `[CEReactions]` an vielen IDL-Mitgliedern.

Damit wird die Beziehung zwischen API-Operationen und Custom-Element-Reactions hergestellt.

Dieses Thema wird vollständig in `17-custom-elements.md` behandelt und hier nur als DOM-/API-Querverweis dokumentiert.

### `[Reflect]`

`[Reflect]` und verwandte Web-IDL-Mechanismen unterstützen die normative Zuordnung zwischen Content Attributes und IDL Attributes.

Die genaue Verarbeitung richtet sich nach dem jeweiligen Attributtyp.

### `[SameObject]`

`[SameObject]` kennzeichnet API-Mitglieder, bei denen wiederholte Zugriffe unter den definierten Bedingungen dasselbe Objekt liefern müssen.

Dies ist insbesondere bei Collections relevant.

---

## Element Creation APIs

### `Document.createElement()`

`document.createElement()` ist eine DOM-API mit HTML-spezifischer Elementerzeugungslogik.

Beispiel:

```js
const element = document.createElement("button");
```

Bei einem HTML-Dokument wird der Name entsprechend der HTML-Elementerzeugungsregeln verarbeitet.

### `Document.createElementNS()`

`createElementNS()` berücksichtigt den Namespace.

Beispiel:

```js
document.createElementNS(
  "http://www.w3.org/2000/svg",
  "svg"
);
```

Das Ergebnis ist deshalb nicht automatisch ein HTML-Element.

### Namespace ist entscheidend

Ein local name allein bestimmt nicht das HTML-Interface.

Beispielhaft:

```text
HTML namespace + "svg"
    ≠
SVG namespace + "svg"
```

Dies ist für HTML/SVG-/MathML-Integration wesentlich.

---

## Dynamic Markup Insertion

### Feature-Typ

- DOM API
- HTML Parsing
- Processing Model

HTML definiert APIs für dynamische Markup-Verarbeitung.

Dazu gehören insbesondere APIs aus dem Bereich der dynamischen Markup-Insertion.

Die genaue Verarbeitung ist mit dem HTML Parsing-Modell verbunden.

### Abgrenzung

Diese APIs sind nicht identisch mit:

- `Node.append()`
- `Element.append()`
- `appendChild()`
- `replaceChildren()`

Diese allgemeinen DOM-Manipulationsmethoden gehören zur DOM-API.

HTML-Markup-Insertion kann dagegen HTML-Parsing auslösen.

---

## Parsing-bezogene Document APIs

Die aktuelle HTML-Spezifikation definiert auch dokumentbezogene Parsing-APIs, darunter HTML-spezifische Methoden zur Erzeugung beziehungsweise Verarbeitung von Dokumenten aus Markup.

Diese APIs sind von allgemeinen DOM-Konstruktionsmethoden zu unterscheiden.

### Sicherheitsbezug

Bei HTML-Markup-Verarbeitung können Trusted Types und Sanitization-Kontexte relevant sein.

Die Sicherheitssemantik wird nicht durch eine allgemeine Aussage wie „DOM API ist sicher“ ersetzt.

---

## Processing Models

### DOM API Processing

DOM-/HTML-APIs besitzen häufig normative Algorithmen.

Beispiele:

- Elementerzeugung
- Attribut-Reflection
- Collection-Ermittlung
- named properties
- Konstruktoren
- Form Control Lookup
- Script-Zustand
- HTML Parsing
- Custom Element Upgrade

### API-Aufruf ist nicht immer atomar

Ein API-Aufruf kann mehrere normative Verarbeitungsschritte auslösen.

Beispielsweise kann eine Änderung eines HTML-Attributes:

1. den Attributwert ändern,
2. eine Reflection-Regel auslösen,
3. eine Custom-Element-Reaction auslösen,
4. einen internen Zustand verändern,
5. weitere Verarbeitung beeinflussen.

### DOM-Reaktionen

Bei Custom Elements können API-Operationen in das Reaction-System eingreifen.

Deshalb ist die DOM-API-Ebene mit:

- Custom Elements,
- `[CEReactions]`,
- Upgrade,
- Lifecycle Callbacks

verbunden.

---

## Events

Events sind eine eigenständige DOM-/HTML-Featurefamilie.

Diese Datei dokumentiert lediglich die Interface-/API-Beziehung.

Ein HTML-Interface kann:

- Event Handler IDL Attributes besitzen,
- Events auslösen,
- Events empfangen,
- Event-bezogene Zustände exponieren.

Die vollständige Event-Systematik gehört nicht als Unterinventar in diese Datei.

### Event Handler IDL Attributes

HTML definiert beziehungsweise integriert Event Handler IDL Attributes.

Beispielhaft:

```js
element.onclick = handler;
```

Das ist von:

```html
<button onclick="...">
```

zu unterscheiden.

Das erste ist ein IDL-/DOM-API-Zugriff.

Das zweite ist ein Content Attribute.

---

## Accessibility

### HTML und DOM APIs

Accessibility ist keine reine DOM-Interface-Frage.

HTML definiert für viele Elemente:

- Accessibility Considerations
- Rollenbeziehungen
- Zustandsbeziehungen
- Anforderungen an Attribute
- Beziehungen zu Platform Accessibility APIs

### `ElementInternals`

`ElementInternals` verbindet Custom Elements mit:

- Accessibility Semantics
- ARIA
- Form Association
- Shadow DOM-bezogenen Zuständen
- Custom States

Die vollständige Behandlung erfolgt in `17-custom-elements.md`.

### Externe Spezifikationen

Für vollständige Accessibility-Semantik können unter anderem relevant sein:

- ARIA
- ARIA in HTML
- Platform Accessibility APIs

Diese externen Spezifikationen dürfen nicht als Teil des WHATWG-HTML-Status ausgegeben werden.

---

## Sanitization

DOM Interfaces und APIs können mit Sanitization-Regeln verbunden sein.

Dabei ist zu unterscheiden zwischen:

1. DOM-Manipulation,
2. HTML Parsing,
3. HTML Markup-Insertion,
4. Sanitization,
5. Trusted Types,
6. Safe HTML Parsing APIs.

Nicht jede DOM-Methode ist automatisch eine Sanitization-API.

### `Element.setHTML()` / HTML-Sanitization

HTML kann APIs bereitstellen, bei denen Sanitization explizit Teil des Verarbeitungsmodells ist.

Solche APIs sind von allgemeinen DOM-Manipulationsmethoden zu unterscheiden.

### Fachliche Regel

Die Aussage:

```text
DOM API = sicher
```

ist normativ nicht zulässig.

Sicherheitsverhalten muss für das konkrete API recherchiert werden.

---

## Konformitätsregeln

### API-Konformität

Autoren müssen bei der Verwendung von HTML-APIs die jeweils definierten Voraussetzungen einhalten.

Ein API-Aufruf kann:

- gültige Eingaben verlangen,
- bestimmte Interface-Typen verlangen,
- bestimmte Dokumentzustände voraussetzen,
- Exceptions auslösen,
- stillschweigend keine Wirkung entfalten,
- oder definierte Fallback-Verarbeitung auslösen.

### DOM-Erzeugung und Authoring Conformance

Ein DOM-Objekt kann existieren, ohne dass seine entsprechende HTML-Quelle konform wäre.

Beispiel:

```js
const div = document.createElement("div");
```

Das Erzeugen eines `div` sagt nichts darüber aus, ob ein `div` an einer beliebigen Stelle im HTML-Quelltext konform wäre.

### API-Status

Der Status eines DOM-Interfaces ist nicht mit dem Status des zugehörigen HTML-Elements gleichzusetzen.

Beispielsweise können:

- HTML-Element definiert,
- Interface definiert,
- einzelne API-Mitglieder obsolete,
- einzelne API-Mitglieder legacy

sein.

Status muss daher auf Feature-Ebene bewertet werden.

---

## Querverweise

### Element ↔ DOM Interface

```text
HTML-Element
    ↓
Element Interface
    ↓
IDL Attributes / Methods
    ↓
Processing Model
```

### Content Attribute ↔ IDL Attribute

```text
Content Attribute
    ↓
Reflection / Parsing
    ↓
IDL Attribute
```

### Element ↔ Context

```text
Context
    ↓
zulässige Verwendung
    ↓
HTML-Element
    ↓
DOM-Objekt
```

Ein DOM-Objekt kann anschließend unabhängig davon programmgesteuert verändert werden.

### Element ↔ Content Model

```text
Element
    ↓
Content Model
    ↓
zulässige Kindstruktur
```

Das DOM Interface beschreibt dagegen die Programmierschnittstelle des Objekts.

### DOM ↔ Custom Elements

```text
HTMLElement
    ↓
Custom Element Definition
    ↓
CustomElementRegistry
    ↓
Upgrade / Construction
    ↓
Lifecycle Reactions
```

### DOM ↔ Parsing

```text
HTML Source
    ↓
Tokenizer
    ↓
Tree Construction
    ↓
DOM
    ↓
HTML Interfaces
```

Parsing kann darüber hinaus Custom-Element-Verarbeitung auslösen.

### HTML ↔ SVG

```text
HTML Document
    ↓
Foreign Content / Namespace
    ↓
SVG Element
    ↓
SVG Interface
```

Das SVG-Interface ist nicht automatisch ein HTML-Interface.

### HTML ↔ MathML

Entsprechend:

```text
HTML Document
    ↓
Foreign Content / Namespace
    ↓
MathML Element
    ↓
MathML Interface
```

### DOM ↔ Accessibility

```text
HTML Element
    ↓
DOM Interface
    ↓
HTML Semantics
    ↓
Accessibility Mapping
    ↓
Platform Accessibility API
```

Die Accessibility-Schicht wird nicht vollständig durch das DOM Interface beschrieben.

---

## Status / V1

### Statussystem

Für DOM Interfaces und APIs sind mindestens folgende Dimensionen zu unterscheiden:

| Dimension | Bedeutung |
|---|---|
| WHATWG definiert | HTML definiert das Feature |
| DOM definiert | DOM ist die normative Primärquelle |
| HTML erweitert DOM | HTML ergänzt ein bestehendes DOM-Interface |
| API-Konzept | programmierbare Funktionalität |
| Legacy | historisch beziehungsweise Kompatibilitätszweck |
| Obsolete | von WHATWG als obsolete behandelt |
| Externe Spezifikation | normative Definition liegt außerhalb von HTML |
| V1-Referenz | projektspezifische ZE-WebLab-Einstufung |

### WHATWG-Status ist nicht Browser-Support

Ein Interface kann:

- normativ definiert,
- historisch,
- obsolete,
- extern definiert

sein.

Browser-Kompatibilität ist davon unabhängig und wird separat recherchiert.

### V1-Einstufung

| Feature | WHATWG-/Normebene | ZE-WebLab-Ebene | V1-Einstufung |
|---|---|---|---|
| `Document` | HTML erweitert DOM | Rechercheebene 2 | relevant |
| `HTMLElement` | HTML definiert | Rechercheebene 2 | relevant |
| HTML-Element-Interfaces | HTML definiert | Ebene 1 + Querverweis Ebene 2 | relevant |
| HTML Constructor | HTML/Web IDL | Rechercheebene 2 | relevant |
| Reflection | HTML/Dom-Verarbeitung | Rechercheebene 2 | relevant |
| `DOMStringMap` | HTML/DOM API | Rechercheebene 2 | relevant |
| `HTMLAllCollection` | HTML definiert, legacy | Rechercheebene 2 | dokumentarisch |
| `HTMLFormControlsCollection` | HTML definiert | Rechercheebene 2 | relevant |
| `RadioNodeList` | HTML definiert | Rechercheebene 2 | relevant |
| `HTMLOptionsCollection` | HTML definiert | Rechercheebene 2 | relevant |
| `DOMStringList` | HTML definiert, legacy | Rechercheebene 2 | dokumentarisch |
| `CustomElementRegistry` | HTML/DOM-Integration | Rechercheebene 2 | Querverweis zu 17 |
| `ElementInternals` | HTML/DOM-Integration | Rechercheebene 2 | Querverweis zu 17 |

### Nicht als neue HTML-Elemente zählen

Folgende Konzepte sind keine zusätzlichen nativen HTML-Elemente:

- `Document`
- `HTMLElement`
- `HTMLButtonElement`
- `HTMLFormElement`
- `HTMLCollection`
- `RadioNodeList`
- `DOMStringMap`
- `CustomElementRegistry`
- `ElementInternals`
- `DOMStringList`
- `HTMLAllCollection`
- IDL Attributes
- API Methods
- Constructors
- Interface Mixins

---

## Offene Punkte

### DOM Standard als separate normative Ebene

Diese Datei behandelt die HTML-DOM-Integration.

Eine vollständige DOM-Referenz würde deutlich über den Umfang der HTML-Referenz hinausgehen.

Daher bleiben folgende Bereiche außerhalb dieser Datei:

- vollständige `Node`-API
- vollständige `Element`-API
- vollständige Event-Systematik
- Mutation Observer
- Shadow Root als vollständige DOM-Featurefamilie
- Selection API
- Range API
- DOM Parsing als vollständige DOM-Spezifikation
- XML DOM
- vollständige Namespace-API

Diese Themen können eigene Rechercheebenen beziehungsweise Dateien erhalten.

### Vollständiges HTML-Interface-Inventar

Die erste Ebene enthält bereits elementbezogene DOM-Interfaces.

Ein vollständiges erneutes Inventar aller HTML-Elementinterfaces wäre daher redundante Dokumentation.

Die vorliegende Datei behandelt die übergreifenden Regeln.

### HTML-API-Verteilung

HTML definiert API-Mitglieder über zahlreiche Featurefamilien hinweg.

Daher ist diese Datei keine vollständige Liste jedes einzelnen API-Mitglieds aller HTML-Interfaces.

Die element- und featurebezogenen API-Details verbleiben in den jeweiligen Fachdateien.

### Shadow DOM

Shadow DOM ist eine eigenständige DOM-Featurefamilie.

Die Beziehung zu HTML und Custom Elements ist relevant, die vollständige Shadow-DOM-Referenz jedoch nicht Bestandteil dieser Datei.

### Parsing

HTML Parsing ist eine eigenständige Featurefamilie.

Die DOM-Erzeugung und das Ergebnis des Tree Construction werden hier nur insoweit behandelt, wie sie für die DOM-Interface-Zuordnung erforderlich sind.

### SVG und MathML

SVG- und MathML-Interfaces sind keine zusätzlichen nativen HTML-Elemente.

Die vollständige Integration sollte in separaten Dateien dokumentiert werden.

### Accessibility

Die HTML-zu-Accessibility-API-Beziehung kann nicht vollständig durch HTML-DOM-Interfaces beschrieben werden.

Für eine vollständige Accessibility-Referenz sind externe normative Spezifikationen erforderlich.

---

## Prüfstatus

| Prüfbereich | Status |
|---|---|
| HTML-DOM-Grundmodell | geprüft |
| §3.1 Documents | geprüft |
| `Document` | geprüft |
| `Document` HTML-Erweiterungen | geprüft |
| `Document.body` | geprüft |
| `Document.head` | geprüft |
| `Document.title` | geprüft |
| `Document.currentScript` | geprüft |
| `Document` Collections | geprüft |
| §3.2 Elements | geprüft |
| Elements in the DOM | geprüft |
| Element Interface Lookup | geprüft |
| HTML element constructors | geprüft |
| `[HTMLConstructor]` | geprüft |
| `HTMLElement` | geprüft |
| `HTMLUnknownElement` | geprüft |
| HTML-/SVG-/MathML-Interface-Mixin | geprüft |
| Element Interface ↔ Elementdefinition | geprüft |
| Content Attribute ↔ IDL Attribute | geprüft |
| Reflection | geprüft |
| Boolean Reflection | geprüft |
| Enumerated Reflection | geprüft |
| Numeric Reflection | geprüft |
| URL Reflection | geprüft |
| `DOMTokenList` | geprüft |
| `DOMStringMap` | geprüft |
| `dataset` | geprüft |
| `HTMLAllCollection` | geprüft |
| `HTMLFormControlsCollection` | geprüft |
| `RadioNodeList` | geprüft |
| `HTMLOptionsCollection` | geprüft |
| `DOMStringList` | geprüft |
| Named Properties | geprüft |
| Custom Element DOM-Beziehungen | geprüft |
| `[CEReactions]` | Querverweis geprüft |
| `ElementInternals` | Querverweis geprüft |
| Parsing-Beziehung | geprüft |
| Namespace-Beziehung | geprüft |
| SVG-Beziehung | geprüft |
| MathML-Beziehung | geprüft |
| Accessibility-Abgrenzung | geprüft |
| Sanitization-Abgrenzung | geprüft |
| Content Categories | Querverweis geprüft |
| Contexts | Querverweis geprüft |
| Content Models | Querverweis geprüft |
| Link Types | Querverweis geprüft |
| Global Attributes | Querverweis geprüft |
| Forms | Querverweis geprüft |
| Custom Elements | Querverweis geprüft |
| V1-Abgrenzung | geprüft |
| Browser-Support | bewusst nicht Bestandteil |

---

## Quellen / Referenzen

### Normative Primärquelle

**WHATWG HTML Living Standard**

Für diese Datei geprüfte Bereiche:

- §2.6 Common DOM interfaces
- §2.6.1 Reflecting content attributes in IDL attributes
- §2.6.2 Using `reflect` via IDL extended attributes
- §2.6.3 Using `reflect` in specifications
- §2.6.4 Collections
- §2.6.4.1 `HTMLAllCollection`
- §2.6.4.2 `HTMLFormControlsCollection`
- §2.6.4.3 `HTMLOptionsCollection`
- §2.6.5 `DOMStringList`
- §3.1 Documents
- §3.1.1 The `Document` object
- §3.1.2 The `DocumentOrShadowRoot` interface
- §3.1.3 Ancestor origins
- §3.1.4 Resource metadata management
- §3.1.5 Reporting document loading status
- §3.1.6 Render-blocking mechanism
- §3.1.7 DOM tree accessors
- §3.2 Elements
- §3.2.2 Elements in the DOM
- §3.2.3 HTML element constructors
- §3.2.4 Element definitions
- §3.2.5 Content models
- §3.2.6 Global attributes
- §3.2.7 `innerText` and `outerText`
- §3.2.9 Requirements related to ARIA and platform accessibility APIs
- §4 The elements of HTML
- §4.13 Custom elements
- jeweils einschlägige HTML-Elementdefinitionen mit DOM Interface

### Projektquelle

**ZE-WebLab – HTML-Referenz**

Berücksichtigte bestehende Dokumente:

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
- `docs/html/13-global-attributes.md`
- `docs/html/14-content-categories.md`
- `docs/html/15-content-models.md`
- `docs/html/16-link-types.md`
- `docs/html/17-custom-elements`
- `docs/html/18-contexts.md`

### Weitere normative Bezüge

Für diese Feature-Familie relevant:

- WHATWG DOM Standard
- WHATWG Web IDL
- WHATWG URL Standard
- WHATWG Infra Standard
- WHATWG HTML Parsing
- ARIA / ARIA in HTML
- SVG-Spezifikation
- MathML-Spezifikation
- gegebenenfalls weitere durch einzelne HTML-APIs referenzierte Standards

Diese externen Spezifikationen werden nicht als HTML-Definitionen ausgegeben.

---

## Zusammenfassung des Feature-Status

| Feature | Normative Ebene | ZE-WebLab-Ebene | Status |
|---|---|---|---|
| `Document` | DOM + HTML-Erweiterung | Rechercheebene 2 | dokumentiert |
| `HTMLElement` | HTML | Rechercheebene 2 | dokumentiert |
| HTML Element Interfaces | HTML | Ebene 1 + 2 | dokumentiert / querreferenziert |
| `HTMLUnknownElement` | HTML | Rechercheebene 2 | dokumentiert |
| `HTMLConstructor` | HTML + Web IDL | Rechercheebene 2 | dokumentiert |
| Element Interface Lookup | HTML | Rechercheebene 2 | dokumentiert |
| Content Attribute Reflection | HTML + DOM/Web IDL | Rechercheebene 2 | dokumentiert |
| Enumerated Reflection | HTML | Rechercheebene 2 | dokumentiert |
| Boolean Reflection | HTML | Rechercheebene 2 | dokumentiert |
| Numeric Reflection | HTML | Rechercheebene 2 | dokumentiert |
| URL Reflection | HTML + URL | Rechercheebene 2 | dokumentiert |
| `DOMStringMap` | HTML | Rechercheebene 2 | dokumentiert |
| `dataset` | HTML | Rechercheebene 2 | dokumentiert |
| `HTMLAllCollection` | HTML | Rechercheebene 2 | dokumentiert |
| `HTMLFormControlsCollection` | HTML | Rechercheebene 2 | dokumentiert |
| `RadioNodeList` | HTML | Rechercheebene 2 | dokumentiert |
| `HTMLOptionsCollection` | HTML | Rechercheebene 2 | dokumentiert |
| `DOMStringList` | HTML | Rechercheebene 2 | dokumentiert |
| Named Properties | HTML/Web IDL | Rechercheebene 2 | dokumentiert |
| Custom Element DOM Integration | HTML + DOM | Rechercheebene 2 | querreferenziert |
| `CustomElementRegistry` | HTML/DOM-Integration | Rechercheebene 2 | querreferenziert |
| `ElementInternals` | HTML/DOM-Integration | Rechercheebene 2 | querreferenziert |
| `[CEReactions]` | Web IDL + HTML | Rechercheebene 2 | querreferenziert |
| HTML ↔ SVG DOM Integration | HTML + SVG | Rechercheebene 2 | abgegrenzt |
| HTML ↔ MathML DOM Integration | HTML + MathML | Rechercheebene 2 | abgegrenzt |
| DOM Core | DOM | separate normative Ebene | abgegrenzt |
| Shadow DOM | DOM | separate Featurefamilie | abgegrenzt |
| Events | DOM/HTML | separate Featurefamilie | abgegrenzt |
| Parsing | HTML | separate Featurefamilie | abgegrenzt |

---

## Abschluss

Diese Datei behandelt DOM Interfaces und APIs als eigenständige zweite Rechercheebene.

Dabei werden ausdrücklich getrennt:

- HTML-Elemente
- HTML-Element-Interfaces
- DOM-Core-Interfaces
- HTML-spezifische API-Erweiterungen
- IDL Attributes
- Content Attributes
- Reflection
- Collections
- Processing Models
- Custom-Element-Integration
- Parsing
- Namespaces
- SVG-/MathML-Integration
- Accessibility
- Sanitization
- externe normative Spezifikationen

Die Datei zählt DOM Interfaces, APIs oder IDL-Mitglieder nicht als zusätzliche HTML-Elemente.

Die elementbezogene Dokumentation verbleibt in der ersten Rechercheebene; die übergreifenden DOM-/API-Regeln werden hier als Feature-Familie dokumentiert.