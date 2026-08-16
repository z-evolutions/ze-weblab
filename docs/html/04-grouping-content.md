# ZE-WebLab – HTML-Referenz: Grouping content

## Arbeitsstand / Quellenstand

- **Datei:** `docs/html/04-grouping-content.md`
- **Themenbereich:** HTML Grouping content
- **WHATWG-Bereich:** HTML Living Standard §4.4 "Grouping content"
- **Primärquelle:** WHATWG HTML Living Standard
- **Geprüfter Spezifikationsstand:** aktuelle Living Standard-Fassung zum Recherchezeitpunkt
- **Rechercheprinzip:** WHATWG-Definitionen, Content Categories, Contexts, Content Models, Tag-Omission-Regeln, Content Attributes, Accessibility-Hinweise, Sanitization, DOM Interfaces und normative Elementregeln wurden getrennt geprüft.
- **Browser-Support:** wird nicht als WHATWG-Status übernommen und ist nicht Bestandteil der Statusbewertung dieser Datei.
- **Externe Accessibility-Quellen:** Die WHATWG-Elementdefinitionen verweisen bei den Accessibility Considerations auf einschlägige externe Accessibility-Spezifikationen. Deren Detailinhalt wird hier nicht als WHATWG-Regel ausgegeben, sofern er nicht Bestandteil der HTML-Spezifikation selbst ist.

### Abgrenzung

Dieser Themenblock dokumentiert die in §4.4 definierten HTML-Elemente.

Er behandelt nicht als zusätzliche Elemente:

- Content Categories als eigenständige Feature-Familien
- Flow Content
- Phrasing Content
- Palpable Content
- Script-supporting elements
- Transparent Content Model
- List Owner
- Ordinal Value
- Name-Value Groups
- Hierarchically Correct `main`
- sonstige DOM-/Rendering-/Verarbeitungsmodelle

Diese Konzepte werden innerhalb der jeweiligen Elementdefinitionen bzw. als Querverweise dokumentiert.

---

## WHATWG-Struktur

Der aktuelle WHATWG-Bereich §4.4 ist wie folgt strukturiert:

1. §4.4.1 – The `p` element
2. §4.4.2 – The `hr` element
3. §4.4.3 – The `pre` element
4. §4.4.4 – The `blockquote` element
5. §4.4.5 – The `ol` element
6. §4.4.6 – The `ul` element
7. §4.4.7 – The `menu` element
8. §4.4.8 – The `li` element
9. §4.4.9 – The `dl` element
10. §4.4.10 – The `dt` element
11. §4.4.11 – The `dd` element
12. §4.4.12 – The `figure` element
13. §4.4.13 – The `figcaption` element
14. §4.4.14 – The `main` element
15. §4.4.15 – The `search` element
16. §4.4.16 – The `div` element

Damit umfasst der Elementbestand dieses Themenblocks:

`p`, `hr`, `pre`, `blockquote`, `ol`, `ul`, `menu`, `li`, `dl`, `dt`, `dd`, `figure`, `figcaption`, `main`, `search`, `div`.

---

# Inventar

| ID | Feature-Typ | Feature | WHATWG-Abschnitt | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| GC-001 | Element | `p` | §4.4.1 | Flow, Palpable | Flow Content; zusätzlich als Kind von `hgroup` | Phrasing Content | End-Tag unter definierten Bedingungen omissible | Global Attributes | Default | `HTMLParagraphElement` | definiert |
| GC-002 | Element | `hr` | §4.4.2 | Flow | Flow Content; zusätzlich als Descendant von `select` | Nothing | Kein End-Tag | Global Attributes | Default | `HTMLHRElement` | definiert |
| GC-003 | Element | `pre` | §4.4.3 | Flow, Palpable | Flow Content | Phrasing Content | Keine | Global Attributes | Default | `HTMLPreElement` | definiert |
| GC-004 | Element | `blockquote` | §4.4.4 | Flow, Palpable | Flow Content | Flow Content | Keine | Global Attributes, `cite` | Default + `cite` | `HTMLQuoteElement` | definiert |
| GC-005 | Element | `ol` | §4.4.5 | Flow; Palpable, wenn mindestens ein `li`-Kind vorhanden | Flow Content | `li` + Script-supporting | Keine | Global Attributes, `reversed`, `start`, `type` | Default + `reversed`, `start`, `type` | `HTMLOListElement` | definiert |
| GC-006 | Element | `ul` | §4.4.6 | Flow; Palpable, wenn mindestens ein `li`-Kind vorhanden | Flow Content | `li` + Script-supporting | Keine | Global Attributes | Default | `HTMLUListElement` | definiert |
| GC-007 | Element | `menu` | §4.4.7 | Flow; Palpable, wenn mindestens ein `li`-Kind vorhanden | Flow Content | `li` + Script-supporting | Keine | Global Attributes | Default | `HTMLMenuElement` | definiert |
| GC-008 | Element | `li` | §4.4.8 | keine | Innerhalb `ol`, `ul`, `menu` | Flow Content | End-Tag unter definierten Bedingungen omissible | Global Attributes; zusätzlich `value` unter definierter Bedingung | Default + `value` | `HTMLLIElement` | definiert |
| GC-009 | Element | `dl` | §4.4.9 | Flow; Palpable bei mindestens einer Name-Value-Gruppe | Flow Content | Name-Value-Gruppen oder `div`-Gruppen | Keine | Global Attributes | Default | `HTMLDListElement` | definiert |
| GC-010 | Element | `dt` | §4.4.10 | keine | Vor `dd`/`dt` in `dl` bzw. zulässigem `div` innerhalb `dl` | Flow Content ohne `header`, `footer`, Sectioning Content oder Heading Content als Descendants | End-Tag unter definierter Bedingung omissible | Global Attributes | Default | `HTMLElement` | definiert |
| GC-011 | Element | `dd` | §4.4.11 | keine | Nach `dt`/`dd` in `dl` bzw. zulässigem `div` innerhalb `dl` | Flow Content | End-Tag unter definierten Bedingungen omissible | Global Attributes | Default | `HTMLElement` | definiert |
| GC-012 | Element | `figure` | §4.4.12 | Flow, Palpable | Flow Content | Flow Content optional mit genau einer `figcaption` am Anfang oder Ende | Keine | Global Attributes | Default | `HTMLElement` | definiert |
| GC-013 | Element | `figcaption` | §4.4.13 | keine | Erster oder letzter Child eines `figure` | Flow Content | Keine | Global Attributes | Default | `HTMLElement` | definiert |
| GC-014 | Element | `main` | §4.4.14 | Flow, Palpable | Flow Content, aber nur als hierarchisch korrektes `main` | Flow Content | Keine | Global Attributes | Default | `HTMLElement` | definiert |
| GC-015 | Element | `search` | §4.4.15 | Flow, Palpable | Flow Content | Flow Content | Keine | Global Attributes | Default | `HTMLElement` | definiert |
| GC-016 | Element | `div` | §4.4.16 | Flow, Palpable | Flow Content; zusätzlich als Kind von `dl`; besondere Kontexte innerhalb `option`, `optgroup` oder `select` | Kontextabhängig: Name-Value-Gruppen, Transparent oder Flow Content | Keine | Global Attributes | Default | `HTMLDivElement` | definiert |

---

# Detailprüfung: `p`

## WHATWG-Abschnitt

**§4.4.1 – The `p` element**

## Bedeutung

Das `p`-Element repräsentiert einen **Paragraphen**.

Die WHATWG-Spezifikation beschreibt einen Paragraphen dabei als strukturelles HTML-Konzept. Ein visuell durch Leerraum getrennter Textblock ist lediglich eine mögliche Darstellung.

Ein Paragraph ist daher nicht automatisch mit einer logisch zusammengehörigen Aussage oder einem beliebigen "Textabsatz" im redaktionellen Sinn gleichzusetzen.

## Content Categories

`p` gehört zu:

- Flow Content
- Palpable Content

## Context

Das Element kann verwendet werden:

- dort, wo Flow Content erwartet wird;
- als Kind eines `hgroup`.

## Content Model

Das Content Model besteht aus:

- Phrasing Content.

Ein `p` darf daher nicht beliebige Flow-Content-Elemente als Kinder enthalten.

Insbesondere können `ul`, `ol`, `div`, `section` und andere nicht-Phrasing-Elemente nicht als reguläre Kinder eines `p` verwendet werden.

## Tag Omission

Das End-Tag von `p` kann in Text/HTML weggelassen werden, wenn das `p` unmittelbar von einem der dafür definierten Elemente gefolgt wird.

Dazu gehören unter anderem:

- `address`
- `article`
- `aside`
- `blockquote`
- `details`
- `dialog`
- `div`
- `dl`
- `fieldset`
- `figcaption`
- `figure`
- `footer`
- `form`
- `h1` bis `h6`
- `header`
- `hgroup`
- `hr`
- `main`
- `menu`
- `nav`
- `ol`
- `p`
- `pre`
- `search`
- `section`
- `table`
- `ul`

Das End-Tag kann außerdem weggelassen werden, wenn kein weiterer Inhalt im Parent vorhanden ist und der Parent die in der Spezifikation definierte Gruppe von HTML-Elementen erfüllt.

## Content Attributes

`p` besitzt keine eigenen elementbezogenen Content Attributes.

Es gelten:

- Global Attributes.

## Accessibility

Die WHATWG-Definition enthält eigene Accessibility Considerations für Autoren und Implementierer.

Die Detailausarbeitung der Accessibility-Semantik wird nicht aus Browserverhalten abgeleitet.

## Sanitization

Sanitization:

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLParagraphElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLParagraphElement`

## Normative Sonderregeln

Ein `p` soll nicht verwendet werden, wenn ein spezifischeres Element für den jeweiligen Inhalt angemessener ist.

Die Spezifikation stellt ausdrücklich klar, dass Listen nicht innerhalb eines `p` liegen. Enthält eine logisch gedachte Aussage eine Liste, entstehen aus struktureller HTML-Sicht mehrere Paragraphen.

Für das gemeinsame Styling mehrerer solcher struktureller Paragraphen kann stattdessen ein `div` verwendet werden.

---

# Detailprüfung: `hr`

## WHATWG-Abschnitt

**§4.4.2 – The `hr` element**

## Bedeutung

`hr` repräsentiert einen **paragraph-level thematic break**.

Typische normative Beispiele der Spezifikation sind:

- ein Szenenwechsel in einer Geschichte;
- ein Übergang zu einem anderen Thema innerhalb eines Abschnitts;
- alternativ ein Separator zwischen einer Menge von Optionen eines `select`.

`hr` ist damit nicht bloß als dekorative horizontale Linie definiert.

## Content Categories

- Flow Content.

## Context

`hr` kann verwendet werden:

- dort, wo Flow Content erwartet wird;
- als Descendant eines `select`.

## Content Model

`hr` besitzt kein Content Model:

- Nothing.

Es handelt sich um ein Void Element.

## Tag Omission

- Kein End-Tag.

## Content Attributes

Nur:

- Global Attributes.

## Accessibility

Die WHATWG-Spezifikation verweist auf Accessibility Considerations für Autoren und Implementierer.

## Sanitization

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLHRElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLHRElement`

## Normative Sonderregeln

`hr` verändert nicht die Dokumentgliederung bzw. das Outline-Modell.

Ein `hr` zwischen zwei `section`-Elementen ist nicht erforderlich, wenn die Sections und ihre Überschriften den thematischen Wechsel bereits ausdrücken.

---

# Detailprüfung: `pre`

## WHATWG-Abschnitt

**§4.4.3 – The `pre` element**

## Bedeutung

`pre` repräsentiert einen Block vorformatierten Textes.

Die Struktur des Inhalts wird dabei durch typografische Konventionen und nicht primär durch HTML-Elemente dargestellt.

## Content Categories

- Flow Content
- Palpable Content

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

- Phrasing Content.

## Tag Omission

- Start-Tag nicht omissible.
- End-Tag nicht omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## HTML-Syntax-Sonderregel

Ein unmittelbar auf das `pre`-Start-Tag folgendes führendes Newline-Zeichen wird in der HTML-Syntax entfernt.

Diese Regel gehört zum HTML-Syntax-/Parsing-Verhalten und ist nicht mit CSS-Whitespace-Verarbeitung gleichzusetzen.

## Typische Verwendungen

Die WHATWG-Spezifikation nennt unter anderem:

- vorformatierten Text;
- E-Mail-Darstellungen;
- Codefragmente;
- ASCII-Art.

Für Computercode kann `pre` zusammen mit `code` verwendet werden.

Für Computerausgabe kann `pre` zusammen mit `samp` verwendet werden.

`kbd` kann innerhalb eines `pre` verwendet werden, um Benutzereingaben darzustellen.

## Accessibility

Die WHATWG-Spezifikation weist ausdrücklich darauf hin, dass Autoren berücksichtigen sollten, wie vorformatierter Inhalt erlebt wird, wenn visuelle Formatierung verloren geht.

Als Beispiele werden unter anderem genannt:

- Sprachsynthese;
- Braille-Ausgabe.

Bei ASCII-Art kann eine alternative textuelle Beschreibung universeller zugänglich sein.

## Sanitization

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLPreElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLPreElement`

## Normative Sonderregeln

Die Spezifikation enthält für `pre` außerdem Rendering-Anforderungen im Zusammenhang mit dem bidirektionalen Algorithmus.

---

# Detailprüfung: `blockquote`

## WHATWG-Abschnitt

**§4.4.4 – The `blockquote` element**

## Bedeutung

`blockquote` repräsentiert einen Abschnitt, der aus einer anderen Quelle zitiert wird.

Der Inhalt eines `blockquote` muss aus einer anderen Quelle stammen.

## Content Categories

- Flow Content
- Palpable Content

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

- Flow Content.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes
- `cite`

### `cite`

`cite` verweist auf die Quelle des Zitats oder auf weitere Informationen zum Zitat.

Wenn vorhanden, muss der Wert eine gültige URL sein, die gegebenenfalls von Leerzeichen umgeben ist.

Der Wert wird relativ zum Node Document des Elements aufgelöst.

Die Spezifikation stellt klar, dass solche Citation Links primär für private Zwecke vorgesehen sind, beispielsweise für serverseitige Statistikverarbeitung. User Agents können sie für Benutzer zugänglich machen.

## Accessibility

Die WHATWG-Definition besitzt Accessibility Considerations für Autoren und Implementierer.

## Sanitization

- Default mit Attribut `cite`.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLQuoteElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, ReflectURL] attribute USVString cite;
};
```

DOM Interface:

- `HTMLQuoteElement`

Dasselbe DOM Interface wird auch vom `q`-Element verwendet.

## Normative Sonderregeln

Die Attribution eines Zitats soll außerhalb des `blockquote`-Elements platziert werden.

Der Inhalt eines Zitats darf nach den konventionellen Regeln der jeweiligen Sprache verkürzt oder mit Kontext ergänzt werden.

---

# Detailprüfung: `ol`

## WHATWG-Abschnitt

**§4.4.5 – The `ol` element**

## Bedeutung

`ol` repräsentiert eine Liste von Elementen, deren Reihenfolge absichtlich festgelegt ist und deren Änderung die Bedeutung der Liste verändern würde.

Die Listenelemente sind die `li`-Kinder des `ol` in Tree Order.

## Content Categories

Immer:

- Flow Content

Zusätzlich:

- Palpable Content, wenn die Kinder mindestens ein `li`-Element enthalten.

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

- Zero or more `li` and script-supporting elements.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

Global Attributes sowie:

### `reversed`

Boolean Attribute.

Wenn vorhanden, ist die Liste absteigend nummeriert.

Wenn nicht vorhanden, ist die Liste aufsteigend nummeriert.

### `start`

Bestimmt den Startwert der Liste.

Wenn vorhanden, muss der Wert eine gültige Integer-Darstellung sein.

### `type`

Bestimmt die Art des Listenmarkers.

Die WHATWG-Spezifikation definiert folgende Zustände:

| Wert | Zustand | Bedeutung |
|---|---|---|
| `1` | decimal | Dezimalzahlen |
| `a` | lower-alpha | Kleinbuchstaben |
| `A` | upper-alpha | Großbuchstaben |
| `i` | lower-roman | Kleine römische Zahlen |
| `I` | upper-roman | Große römische Zahlen |

Fehlt `type` oder entspricht der Wert keinem definierten Schlüsselwort, wird der decimal state repräsentiert.

Zahlen kleiner oder gleich null werden unabhängig vom `type`-Attribut im Dezimalsystem dargestellt.

## Startwert

Der Startwert eines `ol` wird nach der WHATWG-Definition bestimmt:

1. Wenn `start` vorhanden ist und erfolgreich als Integer geparst wird, wird dieser Wert verwendet.
2. Andernfalls wird bei vorhandenem `reversed` die Anzahl der owned `li`-Elemente verwendet.
3. Andernfalls ist der Startwert `1`.

## Sanitization

- Default mit `reversed`, `start` und `type`.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLOListElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, Reflect] attribute boolean reversed;
  [CEReactions, Reflect, ReflectDefault=1] attribute long start;
  [CEReactions, Reflect] attribute DOMString type;

  // also has obsolete members
};
```

DOM Interface:

- `HTMLOListElement`

## Normative Sonderregeln

Die Spezifikation definiert für Listen ein Modell von:

- List Owner
- owned list items
- ordinal values

Das `value`-Attribut eines `li` kann die Nummerierung beeinflussen.

Das IDL-Attribut `li.value` entspricht dabei nicht unmittelbar dem berechneten ordinal value; es reflektiert das Content Attribute.

---

# Detailprüfung: `ul`

## WHATWG-Abschnitt

**§4.4.6 – The `ul` element**

## Bedeutung

`ul` repräsentiert eine Liste von Elementen, bei der die Reihenfolge keine materielle Bedeutung für das Dokument besitzt.

Das Ändern der Reihenfolge soll daher die Bedeutung nicht verändern.

## Content Categories

- Flow Content
- Palpable Content, wenn mindestens ein `li`-Kind vorhanden ist.

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

- Zero or more `li` and script-supporting elements.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Accessibility

Die WHATWG-Definition enthält Accessibility Considerations für Autoren und Implementierer.

## Sanitization

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLUListElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLUListElement`

## Normative Sonderregel

`ul` ist semantisch für ungeordnete Listen bestimmt.

Wenn die Reihenfolge der Items die Bedeutung beeinflusst, ist `ol` das dafür vorgesehene Element.

---

# Detailprüfung: `menu`

## WHATWG-Abschnitt

**§4.4.7 – The `menu` element**

## Bedeutung

`menu` repräsentiert eine Toolbar aus seinen Inhalten in Form einer ungeordneten Liste von Items.

Die Items werden durch `li` repräsentiert und stehen für Commands, die der Benutzer ausführen oder aktivieren kann.

Die Spezifikation beschreibt `menu` ausdrücklich als semantische Alternative zu `ul` für eine ungeordnete Liste von Commands bzw. eine Toolbar.

## Content Categories

- Flow Content
- Palpable Content, wenn mindestens ein `li`-Kind vorhanden ist.

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

- Zero or more `li` and script-supporting elements.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Accessibility

Die WHATWG-Definition enthält Accessibility Considerations für Autoren und Implementierer.

## Sanitization

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLMenuElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLMenuElement`

## Normative Sonderregeln

Die visuelle Gestaltung als Toolbar wird nicht durch das `menu`-Element selbst vorgeschrieben.

Die Anwendung ist für die entsprechende Darstellung verantwortlich.

---

# Detailprüfung: `li`

## WHATWG-Abschnitt

**§4.4.8 – The `li` element**

## Bedeutung

`li` repräsentiert ein List Item.

Ist der Parent ein:

- `ol`
- `ul`
- `menu`

ist das `li` ein Item der entsprechenden Parent-Liste.

Außerhalb dieser Parent-Beziehungen besitzt das `li` keine definierte List Relationship zu anderen `li`-Elementen.

## Content Categories

- Keine.

## Context

- Innerhalb von `ol`.
- Innerhalb von `ul`.
- Innerhalb von `menu`.

## Content Model

- Flow Content.

## Tag Omission

Das End-Tag kann entfallen:

- wenn das `li` unmittelbar von einem anderen `li` gefolgt wird;
- oder wenn kein weiterer Inhalt im Parent vorhanden ist.

## Content Attributes

- Global Attributes.

Zusätzlich kann `value` verwendet werden, wenn das `li` kein Kind von `ul` oder `menu` ist.

### `value`

`value` ist eine gültige Integer-Angabe und bestimmt den ordinal value des List Items, wenn der List Owner ein `ol` ist.

## Sanitization

- Default mit `value`.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLLIElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, Reflect] attribute long value;

  // also has obsolete members
};
```

DOM Interface:

- `HTMLLIElement`

## Normative Sonderregeln: List Owner

Die WHATWG-Spezifikation definiert ein eigenes Konzept des List Owner.

Für Elemente mit dem berechneten CSS-Wert `display: list-item` wird der List Owner algorithmisch bestimmt.

Dabei werden unter anderem:

- Rendering-Zustand,
- `ol`-, `ul`- und `menu`-Ancestors,
- der nächstgelegene entsprechende Ancestor,
- und der nächste inklusive Ancestor mit einer CSS Box

berücksichtigt.

Anschließend werden für die owned list items ordinal values bestimmt.

---

# Detailprüfung: `dl`

## WHATWG-Abschnitt

**§4.4.9 – The `dl` element**

## Bedeutung

`dl` repräsentiert eine Association List aus null oder mehr Name-Value-Gruppen.

Die Spezifikation bezeichnet dies als Description List.

Eine Name-Value-Gruppe besteht aus:

- einem oder mehreren `dt`-Elementen als Namen;
- gefolgt von einem oder mehreren `dd`-Elementen als Werte.

Alternativ kann die Gruppe durch `div`-Kinder strukturiert werden.

## Content Categories

- Flow Content
- Palpable Content, wenn mindestens eine Name-Value-Gruppe vorhanden ist.

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

Es gibt zwei zulässige Grundformen.

### Form 1

Null oder mehr Gruppen bestehend aus:

- einem oder mehreren `dt`;
- gefolgt von einem oder mehreren `dd`;

wobei Script-supporting Elements dazwischen stehen dürfen.

### Form 2

- Ein oder mehrere `div`-Elemente,
- optional durch Script-supporting Elements unterbrochen.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Sanitization

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLDListElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLDListElement`

## Name-Value-Gruppen

Die WHATWG-Spezifikation definiert algorithmisch, wie Name-Value-Gruppen aus `dt` und `dd` ermittelt werden.

Ein `dt` beginnt bzw. erweitert den Namen einer Gruppe.

Ein `dd` wird dem Wert der aktuellen Gruppe hinzugefügt.

Wenn nach bereits gesehenem `dd` ein neues `dt` folgt, wird die bisherige Gruppe abgeschlossen und eine neue Gruppe begonnen.

## Zulässige Anwendungsfälle

Die Spezifikation zeigt unter anderem:

- Vokabular-/Glossarlisten;
- Metadaten;
- Zuordnungen eines Namens zu mehreren Werten;
- mehrere Namen zu einem Wert;
- bedingte Anweisungen.

## Nicht geeigneter Anwendungsfall

`dl` ist nicht für Dialoge vorgesehen.

---

# Detailprüfung: `dt`

## WHATWG-Abschnitt

**§4.4.10 – The `dt` element**

## Bedeutung

`dt` repräsentiert den Term bzw. Namen einer Term-Description-Gruppe innerhalb einer `dl`.

Die Spezifikation stellt ausdrücklich klar:

`dt` allein bedeutet nicht automatisch, dass sein Inhalt ein definierter Begriff ist.

Für die Kennzeichnung eines tatsächlich definierten Begriffs kann `dfn` verwendet werden.

## Content Categories

- Keine.

## Context

`dt` kann stehen:

- vor `dd` oder `dt` innerhalb eines `dl`;
- vor `dd` oder `dt` innerhalb eines `div`, das Kind eines `dl` ist.

## Content Model

- Flow Content,

jedoch ohne:

- `header`-Descendants;
- `footer`-Descendants;
- Sectioning Content-Descendants;
- Heading Content-Descendants.

## Tag Omission

Das End-Tag kann entfallen, wenn `dt` unmittelbar von:

- einem weiteren `dt`;
- oder einem `dd`

gefolgt wird.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Sanitization

- Default.

## DOM Interface

- `HTMLElement`

Es wird kein eigenes spezialisiertes DOM Interface definiert.

---

# Detailprüfung: `dd`

## WHATWG-Abschnitt

**§4.4.11 – The `dd` element**

## Bedeutung

`dd` repräsentiert den Description-, Definition- oder Value-Teil einer Term-Description-Gruppe in einer `dl`.

## Content Categories

- Keine.

## Context

`dd` kann stehen:

- nach `dt` oder `dd` innerhalb eines `dl`;
- nach `dt` oder `dd` innerhalb eines `div`, das Kind eines `dl` ist.

## Content Model

- Flow Content.

## Tag Omission

Das End-Tag kann entfallen, wenn:

- das `dd` unmittelbar von einem weiteren `dd` gefolgt wird;
- das `dd` unmittelbar von einem `dt` gefolgt wird;
- oder kein weiterer Inhalt im Parent vorhanden ist.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Sanitization

- Default.

## DOM Interface

- `HTMLElement`

## Normative Beziehung zu `dt`

`dt` und `dd` sind gemeinsam die Bestandteile der Name-Value-Gruppen eines `dl`.

Mehrere `dt` können gemeinsam mit mehreren `dd` eine Gruppe bilden.

---

# Detailprüfung: `figure`

## WHATWG-Abschnitt

**§4.4.12 – The `figure` element**

## Bedeutung

`figure` repräsentiert Flow Content, der selbständig ist und typischerweise als eine Einheit aus dem Hauptfluss referenziert wird.

Die Spezifikation nennt unter anderem:

- Illustrationen;
- Diagramme;
- Fotos;
- Code Listings;
- Gedichte;
- audiovisuelle Inhalte.

"Self-contained" bedeutet dabei nicht zwingend, dass der Inhalt vollständig unabhängig ist.

## Content Categories

- Flow Content
- Palpable Content

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

Drei Formen sind zulässig:

1. ein `figcaption`, gefolgt von Flow Content;
2. Flow Content, gefolgt von einem `figcaption`;
3. Flow Content ohne `figcaption`.

Damit ist höchstens ein `figcaption` direkt als Caption des `figure` vorgesehen.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Caption

Das erste `figcaption`-Kind, sofern vorhanden, repräsentiert die Caption des `figure`.

Existiert kein `figcaption`-Kind, besitzt das `figure` keine solche Caption.

## Beziehung zum Dokumentfluss

Der Inhalt des `figure` bleibt Teil des umgebenden Dokumentflusses.

Wenn der Inhalt nur tangential mit dem umgebenden Inhalt zusammenhängt oder einen separaten Zweck erfüllt, verweist die Spezifikation auf `aside` als geeigneteres Konzept.

## Referenzierbarkeit

Die Spezifikation betont, dass Figures leichter verschoben werden können, wenn sie über stabile Kennzeichnungen oder Captions referenziert werden.

Relative Verweise wie "das Bild oben" können beim Verschieben problematisch sein.

## Sanitization

- Default.

## DOM Interface

- `HTMLElement`

Es wird kein eigenes spezialisiertes DOM Interface definiert.

---

# Detailprüfung: `figcaption`

## WHATWG-Abschnitt

**§4.4.13 – The `figcaption` element**

## Bedeutung

`figcaption` repräsentiert die Caption oder Legend für den übrigen Inhalt des Parent-`figure`.

## Content Categories

- Keine.

## Context

Nur:

- als erstes Kind eines `figure`;
- oder als letztes Kind eines `figure`.

## Content Model

- Flow Content.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Sanitization

- Default.

## DOM Interface

- `HTMLElement`

## Normative Sonderregel

Die Bedeutung als Figure-Caption ergibt sich aus der Beziehung zum Parent-`figure`.

Ein `figcaption` außerhalb eines `figure` besitzt nicht automatisch die entsprechende Figure-Caption-Semantik.

---

# Detailprüfung: `main`

## WHATWG-Abschnitt

**§4.4.14 – The `main` element**

## Bedeutung

`main` repräsentiert den dominanten Inhalt eines Dokuments.

## Content Categories

- Flow Content
- Palpable Content

## Context

`main` darf dort verwendet werden, wo Flow Content erwartet wird, aber nur wenn es sich um ein **hierarchically correct `main` element** handelt.

## Content Model

- Flow Content.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Hierarchically Correct `main`

Ein `main` ist hierarchisch korrekt, wenn seine Ancestor-Elemente auf folgende Elemente begrenzt sind:

- `html`;
- `body`;
- `div`;
- `form` ohne Accessible Name;
- autonome Custom Elements.

Jedes `main` muss ein hierarchically correct `main` sein.

## Anzahl sichtbarer `main`-Elemente

Ein Dokument darf nicht mehr als ein `main`-Element besitzen, bei dem das `hidden`-Attribut nicht angegeben ist.

Die Spezifikation erlaubt damit mehrere `main`-Elemente, wenn nicht mehr als eines gleichzeitig nicht verborgen ist.

Dies kann beispielsweise bei clientseitig gesteuerten Ansichten verwendet werden.

## Accessibility

Die WHATWG-Definition besitzt Accessibility Considerations für Autoren und Implementierer.

Die Semantik als dominanter Dokumentinhalt ist daher nicht mit einem beliebigen visuellen Container gleichzusetzen.

## Sanitization

- Default.

## DOM Interface

- `HTMLElement`

Es wird kein eigenes spezialisiertes `HTMLMainElement`-Interface definiert.

---

# Detailprüfung: `search`

## WHATWG-Abschnitt

**§4.4.15 – The `search` element**

## Bedeutung

`search` repräsentiert einen Teil eines Dokuments oder einer Anwendung, der eine Gruppe von Form Controls oder anderen Inhalten enthält, die mit einer Such- oder Filteroperation zusammenhängen.

Das kann beispielsweise sein:

- Suche innerhalb einer Website oder Anwendung;
- Suche bzw. Filterung der aktuellen Seite;
- globale bzw. Internet-weite Suche.

## Content Categories

- Flow Content
- Palpable Content

## Context

- Dort, wo Flow Content erwartet wird.

## Content Model

- Flow Content.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Sanitization

- Default.

## DOM Interface

- `HTMLElement`

Es wird kein eigenes spezialisiertes DOM Interface definiert.

## Normative Sonderregeln

`search` ist nicht dafür vorgesehen, lediglich Suchergebnisse darzustellen.

Eine Seite mit Suchergebnissen gehört grundsätzlich zum normalen Hauptinhalt.

Innerhalb eines `search` können dagegen Such- und Filtermechanismen sowie dazugehörige Controls und Inhalte enthalten sein.

Die Spezifikation zeigt unter anderem:

- Suchformulare;
- Suchfelder;
- Checkboxen zur Filterung;
- Ergebnisbereiche innerhalb einer Suchfunktion.

## Benennung

Die Spezifikation zeigt, dass die Funktion einer Suchinstanz durch umgebenden Kontext, Überschrift oder Attribute wie `title` verdeutlicht werden kann.

Ein `search` ist daher nicht auf klassische serverseitige `form`-Submission beschränkt.

---

# Detailprüfung: `div`

## WHATWG-Abschnitt

**§4.4.16 – The `div` element**

## Bedeutung

`div` besitzt keine eigene besondere Bedeutung.

Es repräsentiert seine Kinder.

Die Spezifikation beschreibt `div` ausdrücklich als Element, das insbesondere dann eingesetzt werden kann, wenn kein spezifischeres Element geeignet ist.

## Content Categories

- Flow Content
- Palpable Content

## Context

`div` kann verwendet werden:

- dort, wo Flow Content erwartet;
- als Kind eines `dl`;
- als Descendant eines `option`;
- als Descendant eines `optgroup`;
- als Descendant eines `select`.

## Content Model

Das Content Model hängt vom Kontext ab.

### `div` als Kind eines `dl`

Dann:

- ein oder mehrere `dt`;
- gefolgt von einem oder mehreren `dd`;
- optional mit Script-supporting Elements dazwischen.

### `div` als Descendant von `option`, `optgroup` oder `select`

Dann:

- Transparent.

### Sonstige Kontexte

- Flow Content.

## Tag Omission

- Keine Tags sind omissible.

## Content Attributes

- Global Attributes.

Keine eigenen elementbezogenen Content Attributes.

## Sanitization

- Default.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLDivElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

DOM Interface:

- `HTMLDivElement`

## Semantische Verwendung

Die WHATWG-Spezifikation nennt insbesondere:

- `class`;
- `lang`;
- `title`

als Attribute, mit denen gemeinsame Eigenschaften einer Gruppe aufeinanderfolgender Elemente ausgezeichnet werden können.

`div` kann außerdem innerhalb eines `dl` zur Gruppierung von `dt`-/`dd`-Gruppen verwendet werden.

## Accessibility und Semantik

Autoren werden ausdrücklich dazu angehalten, `div` als Element letzter Wahl zu betrachten, wenn kein geeigneteres Element vorhanden ist.

Die Verwendung semantisch passenderer Elemente kann:

- bessere Accessibility;
- bessere Wartbarkeit;
- präzisere Dokumentsemantik

ermöglichen.

Die Spezifikation nennt als Beispiele unter anderem:

- Blogpost → `article`
- Kapitel → `section`
- Navigation → `nav`
- Gruppe von Form Controls → `fieldset`

`div` bleibt dennoch für rein gruppierende bzw. stilistische Zwecke geeignet, beispielsweise zur gemeinsamen Auszeichnung mehrerer Paragraphen.

---

# Gemeinsame fachliche Modelle

## Flow Content

Ein großer Teil der Elemente in §4.4 ist Flow Content.

Dazu gehören:

- `p`
- `hr`
- `pre`
- `blockquote`
- `ol`
- `ul`
- `menu`
- `figure`
- `main`
- `search`
- `div`

Flow Content ist eine Content Category und kein eigenständiges HTML-Element.

## Palpable Content

Palpable Content wird bei mehreren Elementen ausdrücklich als Content Category angegeben.

Bei `ol`, `ul`, `menu` und `dl` ist die Palpable-Content-Zuordnung abhängig vom tatsächlichen Inhalt.

Insbesondere:

- `ol`: Palpable, wenn mindestens ein `li`-Kind vorhanden ist.
- `ul`: Palpable, wenn mindestens ein `li`-Kind vorhanden ist.
- `menu`: Palpable, wenn mindestens ein `li`-Kind vorhanden ist.
- `dl`: Palpable, wenn mindestens eine Name-Value-Gruppe vorhanden ist.

Diese Bedingungen sind Teil der Content-Category-Definition und nicht mit der bloßen Existenz des Elements gleichzusetzen.

---

# Listenmodell

## `ol`, `ul`, `menu`

Diese drei Elemente bilden die drei Listentypen dieses Themenbereichs:

- `ol` – geordnete Liste;
- `ul` – ungeordnete Liste;
- `menu` – ungeordnete Liste von Commands bzw. Toolbar-Semantik.

Ihre direkten Item-Elemente sind `li`.

## `li`

`li` ist selbst kein allgemeines Flow-Content-Listen-Container-Element.

Sein normativer Kontext ist:

- `ol`;
- `ul`;
- `menu`.

## List Owner

Die WHATWG-Spezifikation definiert zusätzlich das Konzept des List Owner.

Dieses Konzept ist nicht auf die bloße Parent-Child-Beziehung eines `li` beschränkt.

Es berücksichtigt auch Elemente mit `display: list-item` und definiert algorithmisch, welchem Listencontainer ein solches Element zugeordnet wird.

## Ordinal Values

Für owned list items werden ordinal values bestimmt.

Bei einem `ol` wird die Nummerierung vom Startwert beeinflusst.

Bei einem `li` mit `value` kann die Nummerierung an dieser Stelle geändert werden.

Bei `reversed` wird die Nummerierung anschließend rückwärts fortgesetzt.

---

# Description-List-Modell

## `dl`, `dt`, `dd`

`dl` ist kein bloßes Synonym für eine beliebige Liste.

Es modelliert Name-Value-Beziehungen.

Eine Gruppe besteht grundsätzlich aus:

```text
dt ... dt
dd ... dd
```

Mehrere Namen können daher einem oder mehreren Werten zugeordnet werden.

Ebenso können mehrere Werte einem Namen zugeordnet werden.

## `div` innerhalb `dl`

Die aktuelle WHATWG-Spezifikation erlaubt zusätzlich eine `div`-basierte Gruppierung.

Beispiel:

```html
<dl>
  <div>
    <dt>Author</dt>
    <dd>Example</dd>
  </div>
</dl>
```

Die `div`-Variante ist insbesondere dann relevant, wenn die Gruppen zusätzlich als zusammengehörige Einheiten strukturiert werden sollen.

## Keine Dialog-Semantik

`dl` ist laut Spezifikation nicht das geeignete Modell für Dialoge.

---

# Paragraphen und strukturelle Grenzen

## `p` ist strukturell

Das HTML-Paragraphenmodell unterscheidet sich vom allgemeinen redaktionellen Begriff eines Absatzes.

Ein `p` kann nicht beliebige Flow-Content-Elemente enthalten.

Daraus folgt insbesondere:

```html
<p>Text vor der Liste</p>
<ul>
  <li>Eintrag</li>
</ul>
<p>Text nach der Liste</p>
```

ist strukturell korrekt.

Dagegen ist das Modell

```html
<p>
  Text
  <ul>
    <li>...</li>
  </ul>
  Text
</p>
```

nicht konform.

## `div` als gruppierender Container

Wenn mehrere strukturelle Paragraphen gemeinsam behandelt werden sollen, kann ein `div` als übergeordneter Container verwendet werden.

---

# Thematic Breaks

`hr` ist ein semantischer thematischer Trenner.

Es soll daher nicht ausschließlich deshalb verwendet werden, weil eine horizontale Linie gewünscht ist.

Die visuelle Darstellung ist von der Semantik getrennt.

Ein `hr`:

- erzeugt keinen neuen Sectioning-Abschnitt;
- beeinflusst nicht die Dokumentgliederung;
- kann einen thematischen Wechsel innerhalb eines bestehenden Kontexts ausdrücken.

---

# Preformatted Text

`pre` besitzt ein eigenes semantisches Modell für vorformatierten Text.

Wichtige Punkte:

- Content Model ist Phrasing Content.
- Führendes Newline direkt nach dem Start-Tag wird in der HTML-Syntax entfernt.
- Code kann mit `code` kombiniert werden.
- Ausgabe kann mit `samp` kombiniert werden.
- Benutzereingaben können mit `kbd` markiert werden.
- Accessibility beim Verlust visueller Formatierung muss berücksichtigt werden.
- Rendering besitzt zusätzliche Anforderungen im Zusammenhang mit Bidirectional Text.

---

# Quotations

`blockquote` ist für Zitate aus einer anderen Quelle bestimmt.

Wesentliche Punkte:

- Inhalt muss aus einer anderen Quelle stammen.
- `cite` kann die Quelladresse angeben.
- `cite` ist eine URL.
- Attribution soll außerhalb des `blockquote` erfolgen.
- Das DOM Interface ist mit `q` geteilt: `HTMLQuoteElement`.

Das `cite`-Attribut ist dabei nicht mit dem `cite`-Element aus §4.5 zu verwechseln.

---

# Figures und Captions

## `figure`

`figure` beschreibt selbständigen Flow Content.

Der Inhalt kann beispielsweise:

- ein Bild;
- ein Diagramm;
- ein Code Listing;
- ein Video;
- ein Gedicht;
- eine Gruppe verwandter Inhalte

sein.

## `figcaption`

`figcaption` ist die Caption/Legend des Parent-`figure`.

Sie muss sich als erster oder letzter Child des `figure` befinden.

## Verschachtelte Figures

Die WHATWG-Spezifikation erlaubt verschachtelte `figure`-Elemente.

Damit können beispielsweise:

- eine Gesamtgruppe;
- mehrere Einzel-Figures;
- eine gemeinsame Caption;
- einzelne Captions

modelliert werden.

---

# Hauptinhalt und `main`

`main` ist semantisch nicht bloß ein generischer Container.

Es bezeichnet den dominanten Inhalt des Dokuments.

Die Spezifikation definiert hierfür:

- eine Hierarchieeinschränkung;
- die Regel für höchstens ein nicht verborgenes `main`.

Mehrere `main`-Elemente können in bestimmten Anwendungsfällen vorhanden sein, sofern die nicht aktuellen Ansichten mit `hidden` verborgen werden.

---

# Suche und `search`

`search` ist in der aktuellen WHATWG HTML-Spezifikation ein eigenes HTML-Element.

Es beschreibt einen Bereich mit:

- Suchcontrols;
- Filtercontrols;
- sonstigem suchbezogenem Inhalt.

Es ist nicht identisch mit:

- einem Suchfeld vom Typ `input type="search"`;
- einem `form`;
- einer Suchergebnisseite.

Diese Konzepte können innerhalb eines `search` vorkommen, sind aber eigenständige HTML-Konzepte.

---

# `div` als generischer Container

`div` besitzt keine eigene Dokumentsemantik.

Das ist eine normative Aussage und keine bloße Empfehlung.

Daraus folgt:

- `div` sollte nicht als Ersatz für jedes semantische Element verwendet werden;
- `div` kann aber korrekt sein, wenn kein spezifischeres Element passt;
- `div` ist insbesondere für Gruppierung und Styling weiterhin relevant;
- `div` hat im `dl`-Modell eine zusätzliche definierte strukturelle Funktion.

---

# Accessibility

## WHATWG-Ebene

Für alle in diesem Themenblock definierten Elemente enthält die WHATWG-Spezifikation Accessibility Considerations für Autoren und/oder Implementierer.

Die HTML-Spezifikation verweist hierfür teilweise auf externe Accessibility-Spezifikationen.

## Dokumentationsregel

Diese Datei übernimmt nicht pauschal:

- Browser-Accessibility-Verhalten;
- Screenreader-Verhalten;
- ARIA-Mapping-Details;
- Implementierungsdetails einzelner Assistive Technologies.

Solche Informationen gehören in eine separate Accessibility-Rechercheebene.

## Aus WHATWG unmittelbar ableitbare fachliche Punkte

Die HTML-Semantik selbst liefert insbesondere:

- `p` für Paragraphen;
- `blockquote` für Zitate;
- `ol` für bedeutungstragende Reihenfolge;
- `ul` für Reihenfolge ohne materielle Bedeutung;
- `menu` für Command-/Toolbar-Listen;
- `figure` für selbständigen referenzierbaren Flow Content;
- `main` für dominanten Dokumentinhalt;
- `search` für Such-/Filterfunktionen;
- `div` ohne eigene Semantik.

Diese Semantik darf bei einer Accessibility-Bewertung nicht durch rein visuelle Gestaltung ersetzt werden.

---

# Sanitization

Die aktuelle WHATWG-Spezifikation weist für alle Elemente dieses Themenblocks Sanitization-Informationen aus.

## Default

Folgende Elemente besitzen den Status:

- `p` → Default
- `hr` → Default
- `pre` → Default
- `ul` → Default
- `menu` → Default
- `dl` → Default
- `dt` → Default
- `dd` → Default
- `figure` → Default
- `figcaption` → Default
- `main` → Default
- `search` → Default
- `div` → Default

## Attribute mit expliziter Sanitization-Zuordnung

### `blockquote`

- `cite`

### `ol`

- `reversed`
- `start`
- `type`

### `li`

- `value`

Damit ist die Sanitization-Information getrennt von der allgemeinen Attributinventarisierung dokumentiert.

---

# DOM Interfaces

## Eigene spezialisierte Interfaces

| Element | DOM Interface |
|---|---|
| `p` | `HTMLParagraphElement` |
| `hr` | `HTMLHRElement` |
| `pre` | `HTMLPreElement` |
| `blockquote` | `HTMLQuoteElement` |
| `ol` | `HTMLOListElement` |
| `ul` | `HTMLUListElement` |
| `menu` | `HTMLMenuElement` |
| `li` | `HTMLLIElement` |
| `dl` | `HTMLDListElement` |
| `div` | `HTMLDivElement` |

## `HTMLElement`-basierte Elemente ohne eigenes spezialisiertes Interface

| Element | DOM Interface |
|---|---|
| `dt` | `HTMLElement` |
| `dd` | `HTMLElement` |
| `figure` | `HTMLElement` |
| `figcaption` | `HTMLElement` |
| `main` | `HTMLElement` |
| `search` | `HTMLElement` |

## Besondere DOM-Beziehung

`HTMLQuoteElement` wird sowohl von:

- `blockquote`
- `q`

verwendet.

---

# Elementbezogene Attribute

In diesem Themenblock existieren nur wenige eigene Content Attributes.

| Element | Attribut | Typ / Bedeutung |
|---|---|---|
| `blockquote` | `cite` | URL der Quelle bzw. weitere Informationen |
| `ol` | `reversed` | Boolean; rückwärts laufende Nummerierung |
| `ol` | `start` | Startwert der Nummerierung |
| `ol` | `type` | Listenmarker-Zustand |
| `li` | `value` | Integer; ordinaler Listenwert unter den definierten Bedingungen |

Alle anderen hier behandelten Elemente besitzen laut Elementdefinition nur:

- Global Attributes.

---

# Querverweise

## Beziehungen zu §4.3 Sections

`p`, `hr`, `main`, `div`, `figure` und andere Grouping-Content-Elemente können innerhalb von Sectioning-Strukturen vorkommen.

`hr` erzeugt selbst keine Section.

`main` ist dagegen semantisch der dominante Dokumentinhalt und besitzt eigene hierarchische Regeln.

## Beziehungen zu §4.5 Text-level semantics

`pre` kann insbesondere mit folgenden Text-Level-Elementen kombiniert werden:

- `code`
- `samp`
- `kbd`

`dt` kann `dfn` enthalten, wenn ein Term tatsächlich definiert wird.

`figure`-Captions können beispielsweise `cite` oder andere Text-Level-Semantik enthalten.

## Beziehungen zu §4.6 Links

`blockquote` besitzt mit `cite` ein URL-Attribut.

Das Attribut `cite` ist dabei nicht selbst ein Link-Element.

## Beziehungen zu §4.8 Embedded Content

`figure` wird häufig zusammen mit Embedded-Content-Elementen verwendet, beispielsweise:

- `img`
- `video`

Die Embedded-Content-Elemente gehören jedoch nicht zum Elementinventar von §4.4.

## Beziehungen zu §4.10 Forms

`search` kann Form Controls und `form`-Elemente enthalten.

`search` ist trotzdem kein Ersatz für `form`.

`hr` besitzt zusätzlich einen definierten Kontext als Descendant eines `select`.

## Beziehungen zu Custom Elements

`main` definiert seine hierarchische Korrektheit ausdrücklich unter Berücksichtigung autonomer Custom Elements.

`p` berücksichtigt autonome Custom Elements bei seiner Tag-Omission-Regel.

Custom Elements werden deshalb nicht als weitere Grouping-Content-Elemente gezählt.

---

# Normative Sonderregeln

## `p`

- Content Model ist ausschließlich Phrasing Content.
- Bestimmte End-Tags können weggelassen werden.
- `p` darf nicht als Container für Listen oder sonstigen Flow Content verwendet werden.
- Für logisch zusammengehörige, aber strukturell getrennte Paragraphen kann `div` verwendet werden.

## `hr`

- Kein End-Tag.
- Content Model ist Nothing.
- Repräsentiert einen thematischen Break auf Paragraph-Ebene.
- Erzeugt keine Section.

## `pre`

- Keine Tag-Omission.
- Führendes Newline nach Start-Tag wird in HTML-Syntax entfernt.
- Besitzt zusätzliche Rendering-Anforderungen für Bidirectional Text.

## `blockquote`

- Inhalt muss aus einer anderen Quelle stammen.
- `cite` enthält eine URL.
- Attribution wird außerhalb des `blockquote` platziert.

## `ol`

- Nur `li` und Script-supporting Elements als Content.
- `reversed` ist Boolean.
- `start` bestimmt den Startwert.
- `type` bestimmt den Markerzustand.
- List Items werden in Tree Order betrachtet.
- Ordinal Values werden nach dem definierten Algorithmus bestimmt.

## `ul`

- Nur `li` und Script-supporting Elements als Content.
- Semantik ist von `ol` durch die Bedeutung der Reihenfolge unterschieden.

## `menu`

- Semantische Alternative zu `ul` für Command-/Toolbar-Listen.
- Styling als Toolbar ist nicht durch das Element selbst vorgeschrieben.

## `li`

- Kontext auf `ol`, `ul` und `menu` beschränkt.
- End-Tag kann unter definierten Bedingungen entfallen.
- `value` beeinflusst den ordinal value eines `ol`-List Items.

## `dl`

- Modelliert Name-Value-Gruppen.
- Unterstützt direkte `dt`/`dd`-Struktur oder `div`-Gruppierung.
- `dt`- und `dd`-Sequenzen werden algorithmisch zu Gruppen verarbeitet.

## `dt`

- Darf bestimmte strukturierende Nachfahren nicht enthalten.
- End-Tag kann vor `dt` oder `dd` entfallen.

## `dd`

- End-Tag kann vor `dd`, `dt` oder am Ende des Parents entfallen.

## `figure`

- `figcaption` darf am Anfang oder Ende stehen.
- Selbständiger Inhalt soll als Einheit referenzierbar sein.
- Verschachtelte `figure` sind möglich.

## `figcaption`

- Nur als erster oder letzter Child eines `figure`.
- Kein eigenes DOM Interface.

## `main`

- Muss hierarchisch korrekt sein.
- Höchstens ein nicht verborgenes `main`.
- Mehrere `main` sind möglich, wenn nicht aktuelle Instanzen verborgen sind.

## `search`

- Beschreibt Such-/Filterfunktion.
- Ist nicht bloß ein Container für Suchergebnisse.
- Suchergebnisse selbst gehören grundsätzlich zum normalen Dokumentinhalt.

## `div`

- Keine eigene Semantik.
- Kann als generischer Container eingesetzt werden.
- Ist als Kind von `dl` Bestandteil des Description-List-Modells.
- Besitzt spezielle transparente Content-Regeln in bestimmten Select-Kontexten.

---

# Konformitätsrelevante Unterscheidungen

## `ol` vs. `ul`

Die Auswahl ist semantisch:

- `ol`: Reihenfolge verändert die Bedeutung.
- `ul`: Reihenfolge verändert die Bedeutung nicht wesentlich.

Die Wahl darf nicht allein anhand des gewünschten visuellen Markers erfolgen.

## `ul` vs. `menu`

`ul` ist die allgemeine ungeordnete Liste.

`menu` ist die semantische Variante für eine Liste von Commands bzw. Toolbar-Inhalten.

## `p` vs. `div`

`p` besitzt Paragraphensemantik und ein eingeschränktes Content Model.

`div` besitzt keine eigene Semantik und kann Flow Content gruppieren.

## `figure` vs. `aside`

`figure` ist für selbständigen, typischerweise als Einheit referenzierbaren Inhalt gedacht.

`aside` ist für tangentiale bzw. separat gelagerte Inhalte bestimmt.

Diese Elemente sind daher nicht austauschbare generische Container.

## `dl` vs. `ul`

`dl` modelliert Name-Value-Beziehungen.

`ul` modelliert eine ungeordnete Menge von List Items.

## `main` vs. `div`

`main` besitzt eine konkrete Dokumentsemantik und hierarchische Konformitätsregeln.

`div` besitzt keine eigene Semantik.

---

# Status / V1

## WHATWG-Status

Alle 16 in §4.4 definierten Elemente sind Bestandteil der aktuellen WHATWG HTML Living Standard:

- `p`
- `hr`
- `pre`
- `blockquote`
- `ol`
- `ul`
- `menu`
- `li`
- `dl`
- `dt`
- `dd`
- `figure`
- `figcaption`
- `main`
- `search`
- `div`

## Konformität

"Im WHATWG-Standard definiert" bedeutet nicht automatisch, dass jede beliebige Verwendung des Elements konform ist.

Die Konformität hängt insbesondere ab von:

- Context;
- Content Model;
- Content Attributes;
- Tag-Omission-Regeln;
- elementbezogenen Sonderregeln;
- sonstigen normativen Anforderungen.

## Browser-Support

Browser-Support wird in dieser Datei nicht als WHATWG-Status verwendet.

Insbesondere wird das in der WHATWG-Seite vorhandene MDN-Supportmaterial nicht in den Status des ZE-WebLab-Referenzmodells übernommen.

Das betrifft insbesondere `search`, dessen aktuelle Browser-Unterstützung nicht mit seiner Existenz als WHATWG-definiertes Element verwechselt werden darf.

## V1-Bewertung

Für die ZE-WebLab-V1-Referenz werden die Elemente als:

**WHATWG-definiert**

geführt.

Eine separate Browser-Kompatibilitätsmatrix bleibt davon unabhängig.

---

# Offene Punkte

Zum WHATWG-Abschnitt §4.4 bestehen nach der Primärquellenprüfung keine offenen Punkte hinsichtlich des Elementinventars.

Geprüft wurden:

- vollständige Abschnittsstruktur;
- alle 16 Elementdefinitionen;
- Content Categories;
- Contexts;
- Content Models;
- Tag Omission;
- Content Attributes;
- Accessibility-Hinweise;
- Sanitization;
- DOM Interfaces;
- normative Sonderregeln;
- relevante Querverweise;
- Listenmodell;
- Description-List-Modell;
- `figure`/`figcaption`-Beziehung;
- `main`-Hierarchieregel;
- `search`-Semantik;
- kontextabhängiges `div`-Content Model.

Nicht Bestandteil dieser Datei sind:

- vollständige externe Accessibility-Spezifikationen;
- Browser-Kompatibilität;
- vollständige CSS-Rendering-Spezifikationen;
- vollständige DOM-Spezifikation;
- vollständige Select-Processing-Modelle;
- vollständige Definition aller Global Attributes;
- vollständige Definition aller referenzierten Content Categories.

Diese Themen gehören in die jeweils dafür vorgesehenen Referenzebenen.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard – §4.4 Grouping content**

Relevante Unterabschnitte:

- §4.4.1 The `p` element
- §4.4.2 The `hr` element
- §4.4.3 The `pre` element
- §4.4.4 The `blockquote` element
- §4.4.5 The `ol` element
- §4.4.6 The `ul` element
- §4.4.7 The `menu` element
- §4.4.8 The `li` element
- §4.4.9 The `dl` element
- §4.4.10 The `dt` element
- §4.4.11 The `dd` element
- §4.4.12 The `figure` element
- §4.4.13 The `figcaption` element
- §4.4.14 The `main` element
- §4.4.15 The `search` element
- §4.4.16 The `div` element

## Verwendete WHATWG-Querverweise

Bei der Prüfung wurden insbesondere die von §4.4 referenzierten Definitionen berücksichtigt:

- Flow Content
- Phrasing Content
- Palpable Content
- Script-supporting Elements
- Transparent Content Model
- Global Attributes
- Tag Omission
- List Owner
- Owned List Items
- Ordinal Value
- Valid Integer
- URL Parsing
- Hierarchically Correct `main`
- Hidden
- Autonomous Custom Elements
- Accessible Name

## Externe Quellen

Die WHATWG-Elementdefinitionen verweisen bei Accessibility Considerations auf einschlägige externe Accessibility-Spezifikationen.

Diese externen Quellen wurden in diesem Dokument nicht dazu verwendet, zusätzliche WHATWG-Elementregeln zu erfinden oder Browser-Support als WHATWG-Status zu klassifizieren.

---

# QS-Abschluss

## Elementinventar

**16 / 16 Elemente geprüft**

- [x] `p`
- [x] `hr`
- [x] `pre`
- [x] `blockquote`
- [x] `ol`
- [x] `ul`
- [x] `menu`
- [x] `li`
- [x] `dl`
- [x] `dt`
- [x] `dd`
- [x] `figure`
- [x] `figcaption`
- [x] `main`
- [x] `search`
- [x] `div`

## Fachliche Prüfbereiche

- [x] WHATWG-Abschnittsstruktur
- [x] Elementinventar
- [x] Content Categories
- [x] Contexts
- [x] Content Models
- [x] Tag Omission
- [x] Content Attributes
- [x] Accessibility-Hinweise
- [x] Sanitization
- [x] DOM Interfaces
- [x] normative Sonderregeln
- [x] Listenmodell
- [x] Description-List-Modell
- [x] Figure-/Caption-Modell
- [x] `main`-Hierarchie
- [x] `search`-Semantik
- [x] kontextabhängiges `div`
- [x] relevante Querverweise
- [x] Status-/V1-Abgrenzung
- [x] Browser-Support von WHATWG-Status getrennt
- [x] offene Punkte dokumentiert

## Abschlussstatus

**§4.4 Grouping content ist für die ZE-WebLab-HTML-Referenz vollständig recherchiert und dokumentiert.**