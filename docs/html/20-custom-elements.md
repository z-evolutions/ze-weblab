# ZE-WebLab – HTML-Referenz: Custom Elements

## Arbeitsstand / Quellenstand

**Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Custom Elements Feature / API / DOM-Konzept / Processing Model

**Zielpfad:** `docs/html/20-custom-elements.md`

**Normative Primärquelle:** WHATWG HTML Living Standard, Abschnitt 4.13 „Custom elements“.

**Geprüfter WHATWG-Stand:** Living Standard, zuletzt aktualisiert am 11. August 2026.

**Projektquelle:** ZE-WebLab GitHub-Repository, Branch `main`.

**Wichtige Abgrenzung:** Custom Elements sind keine zusätzliche endliche Liste nativer HTML-Elemente. Sie bilden ein Erweiterungs- und Definitionsmodell für DOM-Elemente und sind deshalb als übergreifende Feature-Familie der zweiten Rechercheebene zu dokumentieren.

**Prüfstatus:** Detailrecherche für die WHATWG-Struktur von Abschnitt 4.13 durchgeführt. Die Repository-Bestandsprüfung der bereits vorhandenen Datei Nr. 19 konnte über die derzeit öffentlich abrufbare Verzeichnisansicht des `main`-Branches nicht verifiziert werden. Deshalb werden für Datei Nr. 19 keine nicht belegten Aussagen über deren tatsächlichen Inhalt gemacht.

---

## Einordnung

Custom Elements stellen im WHATWG HTML Living Standard ein Modell bereit, mit dem Autoren eigene DOM-Elemente definieren und deren Verhalten über JavaScript-Klassen, Registrierung, Konstruktion und Reaktionen an den DOM-Lebenszyklus anbinden können.

Die Spezifikation unterscheidet insbesondere zwischen:

- autonomen Custom Elements,
- form-associated Custom Elements,
- customized built-in elements,
- Custom-Element-Definitionen,
- Custom-Element-Upgrades,
- Custom-Element-Reactions,
- `CustomElementRegistry`,
- `ElementInternals`,
- Custom States,
- scoped Custom Element Registries.

Custom Elements sind damit ein systemisches HTML-/DOM-Konzept und kein Bestandteil der nativen HTML-Elementinventarliste.

---

## WHATWG-Struktur

Die aktuelle WHATWG-Struktur von Abschnitt 4.13 umfasst:

### 4.13 Custom elements

- **4.13.1 Introduction**
  - 4.13.1.1 Creating an autonomous custom element
  - 4.13.1.2 Creating a form-associated custom element
  - 4.13.1.3 Creating a custom element with default accessible roles, states, and properties
  - 4.13.1.4 Creating a customized built-in element
  - 4.13.1.5 Drawbacks of autonomous custom elements
  - 4.13.1.6 Upgrading elements after their creation
  - 4.13.1.7 Scoped custom element registries
  - 4.13.1.8 Exposing custom element states
- **4.13.2 Requirements for custom element constructors and reactions**
  - 4.13.2.1 Preserving custom element state when moved
- **4.13.3 Core concepts**
- **4.13.4 The `CustomElementRegistry` interface**
- **4.13.5 Upgrades**
- **4.13.6 Custom element reactions**
- **4.13.7 Element internals**
  - 4.13.7.1 The `ElementInternals` interface
  - 4.13.7.2 Shadow root access
  - 4.13.7.3 Form-associated custom elements
  - 4.13.7.4 Accessibility semantics
  - 4.13.7.5 Custom state pseudo-class

Die Einführung sowie die beispielorientierten Abschnitte sind teilweise ausdrücklich nicht-normativ. Die normativen Anforderungen und Definitionen befinden sich insbesondere in den nachfolgenden Konzept-, Registry-, Upgrade-, Reaction- und Element-Internals-Abschnitten.

---

## Begriffsdefinitionen

### Custom Element

Ein Custom Element ist ein Element, dessen Definition über den Custom-Element-Mechanismus bereitgestellt wird.

Der Mechanismus ermöglicht insbesondere:

- eigene Elementklassen,
- Registrierung eines Custom-Element-Namens,
- Konstruktion über DOM-APIs,
- Konstruktion durch den HTML-Parser,
- Lifecycle-Reaktionen,
- nachträgliches Upgrade bereits vorhandener Elemente.

### Autonomous Custom Element

Ein autonomes Custom Element besitzt einen eigenen Custom-Element-Namen und basiert typischerweise auf `HTMLElement`.

Beispiel:

```html
<flag-icon country="nl"></flag-icon>
```

Das konkrete Elementverhalten wird über eine registrierte Klasse definiert.

### Customized Built-in Element

Ein customized built-in element erweitert ein vorhandenes natives HTML-Element.

Die lokale Elementbezeichnung des nativen Elements bleibt dabei erhalten.

Beispiel:

```html
<button is="plastic-button">Click Me!</button>
```

Die Definition wird mit einer `extends`-Angabe registriert.

### Custom Element Definition

Eine Definition verbindet unter anderem:

- einen Custom-Element-Namen,
- eine Konstruktorfunktion,
- den Definitionstyp,
- gegebenenfalls ein zu erweiterndes natives Element,
- Lifecycle-Reaktionsinformationen.

### Custom Element Registry

Eine `CustomElementRegistry` verwaltet Custom-Element-Definitionen und stellt unter anderem APIs für Registrierung, Suche und Upgrade bereit.

### Upgrade

Ein Upgrade wandelt ein bereits erzeugtes Element nach einer passenden Registrierung in ein Custom Element um.

Das ist insbesondere für Elemente relevant, die bereits durch Parsing oder DOM-Operationen erzeugt wurden, bevor die entsprechende Definition registriert wurde.

### Custom Element Reaction

Custom Element Reactions verbinden Änderungen an einem Custom Element mit den dafür vorgesehenen Callback-Mechanismen.

Zu den relevanten Lifecycle-Reaktionen gehören insbesondere:

- `connectedCallback`,
- `disconnectedCallback`,
- `adoptedCallback`,
- `attributeChangedCallback`.

Die konkrete Verarbeitung wird vom WHATWG-Processing-Modell definiert.

### Element Internals

`ElementInternals` stellt Custom Elements interne Integrationsmöglichkeiten mit Plattformfunktionen bereit.

Dazu gehören unter anderem:

- Formularintegration,
- Accessibility-Semantik,
- Custom States,
- Zugriff auf bestimmte interne Elementfunktionen.

---

## Custom Element Names

Custom Element Names unterliegen besonderen Namensanforderungen.

Ein Custom-Element-Name muss insbesondere:

- einen Bindestrich enthalten,
- mit einem geeigneten Kleinbuchstaben beginnen,
- aus zulässigen Zeichen bestehen,
- kein reservierter Name sein.

Der Bindestrich ist ein wesentlicher Bestandteil der Namenssyntax und unterscheidet Custom-Element-Namen von den Namen der meisten nativen HTML-Elemente.

Beispiele für syntaktisch typische Custom-Element-Namen:

```text
my-element
user-card
x-dialog
date-picker
```

Die genaue normative Namensprüfung ist Teil des Custom-Element-Definitionsmodells und darf nicht durch eine bloße Annahme „beliebiger HTML-Tags“ ersetzt werden.

---

## Autonome Custom Elements

Autonome Custom Elements werden als eigenständige Elementnamen verwendet.

Typischer Ablauf:

1. Eine Klasse wird definiert.
2. Die Klasse erweitert `HTMLElement`.
3. Die Klasse wird mit `customElements.define()` registriert.
4. Der Custom-Element-Name kann im HTML verwendet werden.
5. Der Parser oder DOM-APIs können Instanzen erzeugen.
6. Die vorgesehenen Lifecycle-Reaktionen werden verarbeitet.

Beispiel:

```js
class FlagIcon extends HTMLElement {
  connectedCallback() {
    // Initialisierung bzw. Rendering
  }
}

customElements.define("flag-icon", FlagIcon);
```

Danach kann das Element beispielsweise als

```html
<flag-icon></flag-icon>
```

verwendet werden.

---

## Customized Built-in Elements

Customized built-in elements erweitern bestehende native HTML-Elemente.

Die Definition verwendet unter anderem die Option `extends`.

Beispiel:

```js
class PlasticButton extends HTMLButtonElement {
  constructor() {
    super();
  }
}

customElements.define("plastic-button", PlasticButton, {
  extends: "button"
});
```

Im HTML wird anschließend das native Element zusammen mit dem `is`-Attribut verwendet:

```html
<button is="plastic-button">Click Me!</button>
```

Das bloße Verwenden

```html
<plastic-button></plastic-button>
```

erzeugt dagegen kein customized built-in `button`.

Das native lokale Element bleibt für die Semantik und die damit verbundenen Plattformfunktionen maßgeblich.

---

## Erweiterung nativer Elemente

Customized built-in elements sind auf bestehende HTML-Elemente ausgerichtet.

Sie dürfen nicht beliebige unbekannte oder historische Legacy-Elemente als Grundlage verwenden.

Die WHATWG-Spezifikation nennt hierfür ausdrücklich verschiedene Legacy-Namen, die mit `HTMLUnknownElement` verbunden sind.

Die Beschränkung dient unter anderem der Zukunftskompatibilität der Plattform.

---

## `CustomElementRegistry`

Die zentrale Registry-API ist:

```js
customElements
```

Sie stellt eine `CustomElementRegistry` bereit.

Wesentliche Konzepte sind:

- Registrierung einer Definition,
- Ermittlung einer registrierten Definition,
- Warten auf die Definition eines Namens,
- Upgrade von Elementen.

Eine Registrierung erfolgt grundsätzlich mit:

```js
customElements.define(name, constructor);
```

Für customized built-in elements kann zusätzlich eine Erweiterungsoption angegeben werden:

```js
customElements.define(name, constructor, {
  extends: "button"
});
```

Die Registry ist damit ein zentrales API-Objekt des Custom-Element-Systems.

---

## `CustomElementRegistry.define()`

`define()` registriert eine Custom-Element-Definition.

Die Definition muss den normativen Anforderungen des Custom-Element-Modells entsprechen.

Dazu gehören unter anderem:

- ein zulässiger Custom-Element-Name,
- eine geeignete Konstruktorfunktion,
- die korrekte Beziehung zwischen Konstruktor und Basiselement,
- gegebenenfalls eine zulässige `extends`-Angabe.

Eine fehlerhafte Definition kann zu einer entsprechenden DOM-/JavaScript-Ausnahme führen.

Die genaue Fehlerbehandlung ist Bestandteil des normativen Registry-Algorithmus.

---

## `CustomElementRegistry.get()`

`get()` ermöglicht die Ermittlung des Konstruktors, der unter einem Custom-Element-Namen registriert wurde.

Konzeptionell:

```js
const Constructor = customElements.get("my-element");
```

Existiert keine entsprechende Definition, liefert die API keinen registrierten Konstruktor.

---

## `CustomElementRegistry.whenDefined()`

`whenDefined()` ermöglicht die Synchronisierung mit der Registrierung eines bestimmten Custom-Element-Namens.

Konzeptionell:

```js
await customElements.whenDefined("user-card");
```

Damit kann Code auf die Registrierung eines Custom Elements warten.

Die API ist insbesondere bei asynchron geladenen Custom-Element-Definitionen relevant.

---

## `CustomElementRegistry.upgrade()`

Die Registry stellt eine explizite Upgrade-Funktion bereit.

Sie ermöglicht es, einen DOM-Teilbaum im Hinblick auf registrierte Custom-Element-Definitionen zu aktualisieren.

Dies ist vom allgemeinen automatischen Upgrade-Verhalten zu unterscheiden.

---

## Konstruktoranforderungen

Die WHATWG-Spezifikation definiert normative Anforderungen an Custom-Element-Konstruktoren.

Zu den ausdrücklich genannten Anforderungen gehören unter anderem:

- Ein parameterloser Aufruf von `super()` muss als erste Anweisung des Konstruktors erfolgen.
- Ein `return` darf im Konstruktor grundsätzlich nicht verwendet werden, außer in den dafür zulässigen einfachen Early-Return-Formen.
- `document.write()` und `document.open()` dürfen vom Konstruktor nicht verwendet werden.
- Attribute und Kinder des Elements dürfen im Konstruktor nicht inspiziert werden.
- Der Konstruktor darf das Element nicht mit eigenen Attributen oder Kindern versehen.
- Initialisierungsarbeiten sollen soweit möglich in `connectedCallback()` erfolgen.
- Der Konstruktor eignet sich insbesondere für Initialzustand, Defaultwerte, Event-Listener und gegebenenfalls das Einrichten eines Shadow Root.

Diese Anforderungen sind normative Teile des Custom-Element-Definitionsmodells und nicht lediglich Stilregeln.

---

## Lifecycle-Callbacks

Custom Elements können auf bestimmte Lebenszyklusänderungen reagieren.

### `connectedCallback()`

Wird verwendet, wenn das Element mit einem relevanten Dokumentbaum verbunden wird.

### `disconnectedCallback()`

Wird verwendet, wenn das Element aus einem relevanten Dokumentbaum entfernt wird.

### `adoptedCallback()`

Wird verwendet, wenn das Element in ein anderes Dokument übernommen wird.

### `attributeChangedCallback()`

Reagiert auf Änderungen beobachteter Attribute.

Welche Attribute beobachtet werden, wird typischerweise über `observedAttributes` festgelegt.

Beispiel:

```js
class MyElement extends HTMLElement {
  static observedAttributes = ["value"];

  attributeChangedCallback(name, oldValue, newValue) {
    // Reaktion auf die Attributänderung
  }
}
```

---

## `observedAttributes`

`observedAttributes` bestimmt, welche Content Attributes eine `attributeChangedCallback()`-Reaktion auslösen können.

Die konkrete Reaktionsverarbeitung ist Teil des Custom-Element-Reaction-Modells.

Die Existenz eines beobachteten Attributs bedeutet nicht, dass dieses Attribut dadurch zu einem neuen globalen HTML-Attribut wird.

Es bleibt ein Attribut des konkreten Elements bzw. des Custom-Element-Modells.

---

## Upgrades

Custom Elements können nach ihrer initialen Erstellung upgraded werden.

Ein typischer Ablauf ist:

1. HTML enthält ein noch nicht definiertes Custom Element.
2. Der Parser erzeugt das Element.
3. Die Custom-Element-Definition wird später registriert.
4. Das bereits vorhandene Element wird entsprechend upgraded.
5. Die registrierte Klasse und ihre Reaktionen werden auf das Element angewendet.

Das ermöglicht unter anderem progressive enhancement und asynchrones Laden von Custom-Element-Definitionen.

Wichtig ist die Unterscheidung zwischen:

- Definition,
- Registrierung,
- Elementerzeugung,
- Upgrade,
- Lifecycle-Reaktionen.

Diese Begriffe sind im WHATWG-Modell nicht synonym.

---

## Upgrade und Dokumentbaum

Die WHATWG-Spezifikation beschreibt ausdrücklich Unterschiede zwischen Elementen, die bereits mit dem Dokumentbaum verbunden sind, und Elementen außerhalb des Dokumentbaums.

Ein Element kann vor der Registrierung einer Definition erzeugt werden.

Wird die Definition später registriert, können verbundene Elemente upgraded werden.

Ein außerhalb des relevanten Dokumentbaums erzeugtes Element bleibt dagegen unter bestimmten Bedingungen zunächst nicht upgraded und kann beim späteren Einfügen in den Dokumentbaum entsprechend behandelt werden.

Das Upgrade-Verhalten ist daher nicht ausschließlich als einfache Eigenschaft der Namensregistrierung zu verstehen.

---

## Custom Element Reactions

Custom Element Reactions stellen ein eigenes Processing-Modell bereit.

Sie sind erforderlich, damit bestimmte DOM-Operationen und Änderungen an Custom Elements die vorgesehenen Callback-Reaktionen in definierter Weise auslösen.

Das Modell umfasst insbesondere:

- Reaction Queues,
- das Enqueueing von Reactions,
- das Ausführen von Reactions,
- die Zuordnung von Reactions zu Custom Elements,
- die Interaktion mit DOM-Operationen.

Die Reaktionsverarbeitung ist deshalb ein Processing Model und kein zusätzliches HTML-Elementinventar.

---

## Reaction Stack

Die Custom-Element-Reaction-Verarbeitung verwendet ein Stack-/Queue-Modell für die geordnete Verarbeitung von Reaktionen.

Die Spezifikation definiert hierfür normative Algorithmen.

Die genaue Reihenfolge der Reaktionen ist relevant, weil DOM-Operationen weitere Reaktionen erzeugen können.

Daraus folgt:

> Lifecycle-Callbacks dürfen nicht als einfache unmittelbare JavaScript-Hooks modelliert werden.

Ihre tatsächliche Ausführung unterliegt dem normativen Reaction-Processing-Modell.

---

## Erzeugung von Custom Elements

Custom Elements können auf unterschiedliche Weise entstehen.

Relevant sind insbesondere:

- HTML-Parsing,
- `Document.createElement()`,
- Konstruktion über den registrierten Konstruktor,
- Erzeugung customized built-in elements mit passender Optionsangabe.

Beispiel für ein autonomes Custom Element:

```js
const element = document.createElement("my-element");
```

Beispiel für ein customized built-in:

```js
const button = document.createElement("button", {
  is: "plastic-button"
});
```

Die Erzeugungsalgorithmen berücksichtigen die vorhandenen Registrierungen und die Art des Custom Elements.

---

## Parsing

Custom Elements sind unmittelbar mit dem HTML-Parsing verbunden.

Der HTML-Parser muss erkennen können, wann ein Elementname einer Custom-Element-Definition entspricht bzw. wann ein Element zunächst als noch nicht definiertes Custom Element erzeugt werden soll.

Dies ist ein wesentlicher Grund dafür, Custom Elements nicht ausschließlich als JavaScript-API zu dokumentieren.

Die Feature-Familie berührt mindestens:

- HTML-Syntax,
- Tokenisierung,
- Tree Construction,
- Elementerzeugung,
- Definitionen,
- Upgrades,
- DOM-Integration,
- Reactions.

---

## `is`-Attribut

Customized built-in elements verwenden das `is`-Attribut zur Kennzeichnung der konkreten Custom-Element-Definition.

Beispiel:

```html
<button is="plastic-button"></button>
```

Das `is`-Attribut darf deshalb nicht einfach als allgemeines Custom-Element-Attribut behandelt werden.

Es steht in direktem Zusammenhang mit dem customized-built-in-Modell.

Die normative Definition und Verarbeitung des `is`-Attributs muss gemeinsam mit den Regeln für customized built-in elements betrachtet werden.

---

## Form-associated Custom Elements

Custom Elements können in das Formularmodell integriert werden.

Ein autonomes Custom Element kann durch die entsprechende Definition als form-associated custom element ausgelegt werden.

Typischerweise wird hierfür die statische Eigenschaft

```js
static formAssociated = true;
```

verwendet.

Anschließend kann `ElementInternals` zur Formularintegration verwendet werden.

Die WHATWG-Spezifikation behandelt hierfür unter anderem:

- Formzugehörigkeit,
- Formularwerte,
- Validierungszustände,
- Formularlebenszyklus,
- Interaktion mit `form`,
- Interaktion mit `label`,
- Submission-Verhalten.

---

## `ElementInternals`

`ElementInternals` ist die zentrale Schnittstelle für bestimmte interne Integrationsmöglichkeiten von Custom Elements.

Sie verbindet Custom Elements unter anderem mit:

- Formularfunktionen,
- Accessibility-Semantik,
- Custom States,
- Shadow-DOM-bezogenen Funktionen.

Beispiel:

```js
class MyControl extends HTMLElement {
  static formAssociated = true;

  constructor() {
    super();
    this._internals = this.attachInternals();
  }
}
```

Das Vorhandensein von `ElementInternals` bedeutet nicht, dass jedes Custom Element automatisch ein Formular-Control wird.

Die konkrete Integration hängt von der Definition und den entsprechenden normativen Regeln ab.

---

## Form-associated Custom Element und `ElementInternals`

Für ein form-associated Custom Element können über `ElementInternals` unter anderem Formularwerte bereitgestellt werden.

Ein typischer Mechanismus verwendet:

```js
this._internals.setFormValue(value);
```

Damit kann die Implementierung einen Wert für die Formularübermittlung bereitstellen.

Die konkrete Verarbeitung ist Bestandteil des normativen Form-Control-Modells und darf nicht lediglich aus einem JavaScript-Beispiel abgeleitet werden.

---

## Accessibility

Custom Elements erhalten ihre Accessibility-Semantik nicht automatisch allein durch ihren Namen.

Ein autonomes Custom Element mit einem Namen wie:

```html
<taco-button></taco-button>
```

wird nicht allein aufgrund dieses Namens automatisch wie ein natives `button` behandelt.

Die WHATWG-Spezifikation beschreibt deshalb ausdrücklich die Möglichkeit, über `ElementInternals` Default-Accessibility-Semantik bereitzustellen.

Dazu gehören unter anderem:

- Default-Rollen,
- States,
- Properties.

Diese Default-Semantik kann durch Autor-Markup entsprechend den geltenden Accessibility-Regeln beeinflusst werden.

Die normative Accessibility-Definition selbst verweist teilweise auf externe Accessibility-Spezifikationen. Diese sind nicht mit dem WHATWG-Status des Custom-Element-Features gleichzusetzen.

---

## Accessibility über `ElementInternals`

`ElementInternals` kann Default-Semantik für ein Custom Element bereitstellen.

Beispielsweise kann eine Rolle über die Internals gesetzt werden:

```js
this._internals.role = "checkbox";
```

Ebenso können entsprechende ARIA-Zustände und Eigenschaften über die dafür vorgesehenen `ElementInternals`-Mechanismen bereitgestellt werden.

Wichtig:

- Dies definiert Default-Semantik.
- Es ersetzt nicht die allgemeine Accessibility-Spezifikation.
- Es macht ein autonomes Custom Element nicht automatisch semantisch identisch mit jedem beliebigen nativen Element.
- Die Konformität von Autor-Markup und Accessibility-Semantik ist separat zu bewerten.

---

## Custom States

Custom Elements können eigene Zustände bereitstellen.

Die WHATWG-Spezifikation verwendet hierfür `ElementInternals.states`.

Ein Zustand kann beispielsweise mit:

```js
this._internals.states.add("checked");
```

gesetzt und mit:

```js
this._internals.states.delete("checked");
```

entfernt werden.

Diese Zustände können über die CSS-Pseudoklasse `:state()` angesprochen werden.

Beispiel:

```css
labeled-checkbox:state(checked) {
  border: solid;
}
```

Custom States sind damit ein Integrationsfeature zwischen:

- Custom Elements,
- `ElementInternals`,
- DOM-Zuständen,
- CSS.

---

## Scoped Custom Element Registries

Die aktuelle WHATWG-Spezifikation enthält Regeln für scoped custom element registries.

Damit können mehrere Bibliotheken bzw. Komponentenbereiche unterschiedliche Registries verwenden, ohne zwingend eine globale Namenskollision verursachen zu müssen.

Beispiel:

```js
const scoped = new CustomElementRegistry();

scoped.define("example-element", ExampleElement);

const element = document.createElement(
  "example-element",
  { customElementRegistry: scoped }
);
```

Die Registry kann einem relevanten DOM-Kontext zugeordnet werden.

Das Konzept ist insbesondere für isolierte Komponenten- oder Bibliotheksumgebungen relevant.

---

## Custom Element States und CSS

Custom States werden nicht als neue HTML-Attribute behandelt.

Sie bilden einen eigenen Zustand eines Custom Elements und können über `:state()` selektiert werden.

Damit ist die Informationsebene:

```text
Custom Element
    ↓
ElementInternals
    ↓
states
    ↓
:state()
```

von der Ebene der Content Attributes zu unterscheiden.

---

## Shadow DOM

Custom Elements können mit Shadow Roots kombiniert werden.

Beispielsweise kann ein Konstruktor einen Shadow Root erzeugen:

```js
const shadowRoot = this.attachShadow({
  mode: "closed"
});
```

Shadow DOM ist jedoch ein eigenständiges Plattformkonzept.

Daher gilt:

**Custom Elements ≠ Shadow DOM**

Die beiden Features werden häufig gemeinsam verwendet, sind aber konzeptionell und normativ getrennte Mechanismen.

---

## DOM Interfaces / APIs

Für die Custom-Element-Familie sind insbesondere folgende APIs und Interfaces relevant:

| Interface / API | Funktion |
|---|---|
| `CustomElementRegistry` | Verwaltung von Custom-Element-Definitionen |
| `customElements` | Zugriff auf die Registry des relevanten globalen Kontexts |
| `ElementInternals` | interne Plattformintegration für Custom Elements |
| `HTMLElement` | typische Basisklasse autonomer Custom Elements |
| `HTMLButtonElement` | beispielhafte Basisklasse eines customized built-in |
| `Document.createElement()` | DOM-Erzeugung von Elementen einschließlich Custom-Element-Optionen |

Die DOM-Interfaces sind nicht als zusätzliche HTML-Elemente zu zählen.

---

## Attribute

### `is`

Das `is`-Attribut ist unmittelbar mit customized built-in elements verbunden.

Beispiel:

```html
<button is="plastic-button"></button>
```

Es ist von den allgemeinen Global Attributes zu unterscheiden.

### Benutzerdefinierte Attribute

Custom Elements können eigene Content Attributes verwenden.

Beispiel:

```html
<user-card user-id="42"></user-card>
```

Die Tatsache, dass ein Custom Element ein solches Attribut verwendet, macht dieses nicht automatisch zu einem global definierten HTML-Attribut.

Die Verarbeitung liegt grundsätzlich in der Definition des jeweiligen Custom Elements.

---

## Content Categories

Custom Elements bilden keine eigene native Content Category.

Ein Custom Element ist daher nicht allein aufgrund seiner Existenz automatisch:

- Flow Content,
- Phrasing Content,
- Interactive Content,
- oder einer anderen konkreten nativen Content Category.

Die Einordnung hängt vom konkreten Element und den jeweils geltenden HTML-Regeln ab.

Dies ist besonders wichtig für die Trennung zwischen:

- Custom Element,
- Content Category,
- Content Model.

Diese drei Ebenen dürfen nicht miteinander gleichgesetzt werden.

---

## Context

Ein Custom Element besitzt nicht automatisch einen einheitlichen globalen HTML-Context.

Der zulässige Kontext hängt insbesondere davon ab:

- ob es autonom oder customized built-in ist,
- welche native Funktion gegebenenfalls erweitert wird,
- welche HTML-Strukturregeln für das konkrete Verwendungsszenario gelten.

Custom Elements sind daher nicht als generische Ausnahme von allen HTML-Kontextregeln zu verstehen.

---

## Content Model

Ein autonomes Custom Element erhält durch seine Definition nicht automatisch ein beliebiges universelles Content Model.

Die konkrete Verwendung muss weiterhin im Rahmen der geltenden HTML- und DOM-Regeln betrachtet werden.

Bei customized built-in elements bleiben die strukturellen und semantischen Eigenschaften des erweiterten nativen Elements relevant.

---

## Processing Models

Custom Elements besitzen mehrere miteinander verbundene Processing Models:

1. Definition und Registrierung
2. Konstruktion
3. Parsing
4. Upgrade
5. Lifecycle-Reaktionen
6. Reaction-Queue-Verarbeitung
7. Formularintegration
8. Accessibility-Integration
9. Custom States
10. scoped Registry-Verarbeitung

Diese Modelle dürfen nicht auf die bloße Methode `customElements.define()` reduziert werden.

---

## Parsing und Definition

Die Definition eines Custom Elements kann zeitlich nach der Erzeugung eines Elements erfolgen.

Daher müssen Parsing und Registrierung getrennt betrachtet werden.

Ein Parser kann ein Custom Element bereits erzeugen, bevor dessen Definition verfügbar ist.

Später kann die Registrierung das Upgrade des Elements auslösen.

Dieses Verhalten ist ein zentraler Bestandteil des Custom-Element-Modells.

---

## Konformitätsregeln

Für Custom Elements bestehen mehrere Ebenen von Konformitätsanforderungen.

### Namenskonformität

Custom-Element-Namen müssen die spezifizierten Namensanforderungen erfüllen.

### Registrierungsregeln

`CustomElementRegistry.define()` muss mit einer zulässigen Definition verwendet werden.

### Konstruktorregeln

Custom-Element-Konstruktoren unterliegen den spezifizierten Anforderungen.

### Customized Built-ins

Bei customized built-in elements müssen die `extends`-Angabe, die Basisklasse und das verwendete native Element zusammenpassen.

### Lifecycle-Reaktionen

Callback-Mechanismen müssen entsprechend dem Custom-Element-Reaction-Modell verwendet werden.

### Form-associated Custom Elements

Für die Formularintegration gelten zusätzliche Anforderungen.

---

## Status / V1

### WHATWG-Status

Custom Elements sind im aktuellen WHATWG HTML Living Standard definiert.

Der normative Schwerpunkt liegt in Abschnitt **4.13 Custom elements**.

Das Feature ist damit:

- im WHATWG-Standard definiert,
- teilweise normativ spezifiziert,
- teilweise durch nicht-normative Einführungstexte erläutert,
- eng mit DOM- und JavaScript-APIs verbunden.

### ZE-WebLab-V1

Die Zuordnung zu einer ZE-WebLab-V1-Kategorie ist eine Projektebene und darf nicht mit dem WHATWG-Status verwechselt werden.

**V1-Einstufung:** Feature-Familie der zweiten Rechercheebene.

**Begründung:** Custom Elements sind kein einzelnes natives HTML-Element, sondern ein übergreifendes Erweiterungs-, DOM-, Parsing- und API-Modell.

---

## Querverweise

### Custom Elements ↔ DOM

Custom Elements sind direkt mit DOM-Elementerzeugung, Konstruktion, Verbindung und Dokumentbäumen verbunden.

### Custom Elements ↔ Parsing

Der HTML-Parser kann Custom Elements erzeugen, bevor die entsprechende Definition registriert wurde.

### Custom Elements ↔ APIs

`CustomElementRegistry` und `ElementInternals` bilden zentrale APIs der Feature-Familie.

### Custom Elements ↔ Forms

Form-associated custom elements können am HTML-Formularmodell teilnehmen.

### Custom Elements ↔ Accessibility

`ElementInternals` ermöglicht Default-Accessibility-Semantik.

### Custom Elements ↔ CSS

Custom States können über `:state()` exponiert werden.

### Custom Elements ↔ Shadow DOM

Custom Elements werden häufig gemeinsam mit Shadow DOM verwendet; beide Konzepte sind jedoch getrennte Plattformfeatures.

### Custom Elements ↔ HTML Elements

Customized built-in elements können bestehende native HTML-Elemente erweitern.

### Custom Elements ↔ Global Attributes

Custom Elements können globale Attribute verwenden. Eigene Attribute eines Custom Elements sind davon zu unterscheiden.

---

## Sanitization

Die Custom-Element-Spezifikation selbst ist nicht als eigenständige allgemeine Sanitization-Featurefamilie zu behandeln.

Bei der Verarbeitung von HTML mit Sanitization- oder Safe-HTML-Mechanismen können Custom Elements jedoch relevant sein.

Insbesondere ist zwischen:

- Custom-Element-Definition,
- HTML-Parsing,
- DOM-Erzeugung,
- Sanitization,
- Safe-HTML-APIs

zu unterscheiden.

Eine konkrete Sanitization-Regel darf nicht aus der bloßen Existenz des Custom-Element-Features abgeleitet werden.

Für die vollständige Dokumentation der HTML-Sanitization-Mechanismen ist daher eine separate zweite-Ebenen-Recherche erforderlich.

---

## Accessibility-Abgrenzung

Die WHATWG-Spezifikation enthält für Custom Elements eigene Abschnitte zur Accessibility-Integration, insbesondere im Zusammenhang mit `ElementInternals`.

Externe Accessibility-Spezifikationen, insbesondere WAI-ARIA, sind davon getrennt zu behandeln.

Daher gilt:

**WHATWG-Regel:** normative HTML-/DOM-Integration.

**Externe Accessibility-Spezifikation:** normative Accessibility-Semantik, soweit die WHATWG darauf verweist.

**ZE-WebLab-Dokumentation:** muss beide Quellen getrennt ausweisen.

---

## Offene Punkte

### Repository-Abdeckung von Datei Nr. 19

Der aktuell über die öffentliche GitHub-Verzeichnisansicht abrufbare `main`-Stand zeigt nur `01`–`12` sowie `README.md`. Die zwischenzeitlich von der Projektarbeit erzeugten Dateien Nr. 13 ff. sind über diese Webansicht derzeit nicht sichtbar.

Daher wurde keine nicht belegte Aussage darüber getroffen, welche Teile von Datei Nr. 19 bereits Custom Elements abdecken.

### Vollständige Querverbindung zu früheren ZE-WebLab-Dateien

Die konkrete interne Verlinkung zu den bereits erstellten Dateien der zweiten Ebene sollte nach dem nächsten erfolgreichen Repository-Abgleich ergänzt bzw. validiert werden.

### Browser-Kompatibilität

Browser-Kompatibilität ist ausdrücklich nicht Bestandteil der WHATWG-Statusbewertung dieser Datei.

Eine Browser-Support-Matrix gehört in eine getrennte Rechercheebene.

### Externe Accessibility-Spezifikationen

Die konkrete Detailprüfung der referenzierten Accessibility-Spezifikationen ist nicht Bestandteil dieser WHATWG-Custom-Elements-Datei und muss als separate externe normative Recherche behandelt werden.

---

## Prüfstatus

| Prüfbereich | Status |
|---|---|
| WHATWG Abschnitt 4.13 | geprüft |
| Unterabschnitte 4.13.1–4.13.7 | geprüft |
| Autonomous Custom Elements | geprüft |
| Customized Built-in Elements | geprüft |
| Custom Element Names | geprüft |
| `CustomElementRegistry` | geprüft |
| Upgrades | geprüft |
| Custom Element Reactions | geprüft |
| Konstruktoranforderungen | geprüft |
| Form-associated Custom Elements | geprüft |
| `ElementInternals` | geprüft |
| Accessibility-Integration | geprüft |
| Custom States | geprüft |
| Scoped Custom Element Registries | geprüft |
| Parsing-Bezug | geprüft |
| DOM-Bezug | geprüft |
| Content Categories | geprüft |
| Context / Content Model | geprüft und abgegrenzt |
| Sanitization | abgegrenzt; separate Detailrecherche erforderlich |
| Browser-Kompatibilität | bewusst nicht Bestandteil |
| Repository-Datei Nr. 19 | über aktuelle öffentliche Verzeichnisansicht nicht verifizierbar |

---

## Quellen / Referenzen

### WHATWG HTML Living Standard

**Primärquelle:**

https://html.spec.whatwg.org/multipage/

**Custom Elements:**

https://html.spec.whatwg.org/multipage/custom-elements.html

Relevanter Abschnitt:

**4.13 Custom elements**

Die aktuelle WHATWG-Fassung wurde bei dieser Recherche als Living Standard mit dem Stand **11. August 2026** geprüft.

### ZE-WebLab

**Projekt-/Bestandsquelle:**

https://github.com/z-evolutions/ze-weblab

**HTML-Dokumentationsverzeichnis:**

https://github.com/z-evolutions/ze-weblab/tree/main/docs/html

Die Repository-Quelle dient ausschließlich zur Feststellung des vorhandenen ZE-WebLab-Projektbestands. Sie ersetzt nicht die normative WHATWG-Quelle.

---

## Fachliche Abgrenzung

Diese Datei dokumentiert die Custom-Elements-Featurefamilie.

Sie zählt insbesondere **nicht** als zusätzliche native HTML-Elemente:

- autonome Custom Elements,
- customized built-in elements,
- `CustomElementRegistry`,
- `ElementInternals`,
- Custom Element Reactions,
- Custom States,
- Upgrade-Mechanismen.

Diese Konzepte gehören zur zweiten Rechercheebene und sind von der nativen HTML-Elementreferenz der ersten Rechercheebene getrennt zu halten.