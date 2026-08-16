# ZE-WebLab – HTML-Referenz: Document element

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab  
**Datei:** `docs/html/01-document-element.md`  
**Themenbereich:** Document element  
**WHATWG-Bereich:** §4.1 The document element  
**Element:** `html`  
**Geprüfter WHATWG-Stand:** HTML Living Standard, 11. August 2026

Diese Datei dokumentiert den WHATWG-Bereich §4.1 „The document element“.

Der Bereich enthält aktuell genau eine HTML-Elementdefinition:

- `html`

Das `Document`-Objekt selbst sowie DOM-APIs wie `document.documentElement`
sind keine zusätzlichen HTML-Elemente. Sie werden deshalb als
Querverweis bzw. API-Ebene behandelt.

Die fachliche Prüfung folgt dem ZE-WebLab-Modell:

- HTML-Element
- WHATWG-Abschnitt
- Content Categories
- Context
- Content Model
- Tag Omission
- Content Attributes
- Accessibility
- Sanitization
- DOM Interface
- normative Sonderregeln
- Querverweise
- Status / V1
- offene Punkte

Browser-Kompatibilität wird nicht als WHATWG-Status verwendet.

---

## WHATWG-Struktur

Der aktuelle WHATWG-Bereich ist:

### 4 The elements of HTML

#### 4.1 The document element

##### 4.1.1 The `html` element

§4.1 besteht damit auf Elementebene ausschließlich aus:

- `html`

Die Spezifikation enthält außerhalb der eigentlichen Elementdefinition
weitere allgemeine Dokument-, DOM- und Syntaxregeln, die für das Verständnis
von `html` relevant sind.

Insbesondere bestehen Querverbindungen zu:

- §3.1 Documents
- §3.2 Elements in the DOM
- §3.2.4 Element definitions
- §3.2.5 Content models
- §3.2.6 Global attributes
- §8 The HTML syntax
- DOM Standard

---

# Inventar

| Feature | WHATWG-Abschnitt | Feature-Typ | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Accessibility | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| `html` | §4.1.1 | HTML-Element | Keine | Als Document Element; außerdem dort, wo ein Subdocument Fragment in einem Compound Document erlaubt ist | `head` gefolgt von `body` | Start- und End-Tag können unter den jeweils definierten Bedingungen ausgelassen werden | Global Attributes | WHATWG verweist auf Accessibility Considerations für Autoren und Implementierer | Default | `HTMLHtmlElement` | Im WHATWG-Standard definiert |

---

# Detailprüfung: `html`

## WHATWG-Zuordnung

Das Element ist in:

**§4.1.1 The `html` element**

definiert.

`html` repräsentiert die Wurzel eines HTML-Dokuments.

Das Element ist damit das zentrale Wurzelelement der HTML-Dokumentstruktur.

---

## Semantik

Das `html`-Element repräsentiert den Root eines HTML-Dokuments.

Es ist nicht lediglich ein technischer Container.

Seine Position hat normative Bedeutung:

- Es ist das Document Element eines HTML-Dokuments.
- Unterhalb davon befinden sich die zentralen Dokumentbereiche.
- Das Content Model verlangt `head`, gefolgt von `body`.

Die Wurzelstruktur ist deshalb Bestandteil des HTML-Dokumentmodells und
nicht lediglich eine optionale organisatorische Konvention.

---

# Content Categories

Für `html` weist WHATWG:

**Keine Content Categories**

aus.

Das bedeutet insbesondere:

- nicht Metadata Content,
- nicht Flow Content,
- nicht Sectioning Content,
- nicht Heading Content,
- nicht Phrasing Content,
- nicht Embedded Content,
- nicht Interactive Content,
- nicht Palpable Content,
- nicht Script-supporting Element.

Die fehlende Zuordnung zu einer Content Category ist von der Tatsache zu
unterscheiden, dass `html` selbstverständlich eine definierte
Dokumentstruktur besitzt.

---

# Context

WHATWG definiert für `html` zwei relevante Verwendungszusammenhänge.

## Als Document Element

`html` darf als Document Element des Dokuments verwendet werden.

Dies ist der normale und zentrale Anwendungsfall:

```html
<!doctype html>
<html>
  <head>
    ...
  </head>
  <body>
    ...
  </body>
</html>
```

## In Compound Documents

`html` darf außerdem dort verwendet werden, wo ein Subdocument Fragment
in einem Compound Document erlaubt ist.

Diese Regel ist von der normalen Verwendung als Wurzelelement eines
eigenständigen HTML-Dokuments zu unterscheiden.

Die Context-Regel bedeutet daher nicht, dass beliebige `html`-Elemente
innerhalb eines normalen HTML-Dokuments verschachtelt werden dürfen.

---

# Content Model

Das Content Model von `html` lautet:

```text
A head element followed by a body element.
```

Damit besteht die definierte Dokumentstruktur aus:

1. `head`
2. `body`

in genau dieser Reihenfolge.

## Strukturmodell

Das konzeptionelle Grundmodell lautet:

```text
html
├── head
└── body
```

`head` und `body` sind damit nicht einfach zwei beliebige Kinder des
`html`-Elements.

Ihre Reihenfolge ist Bestandteil des Content Models.

## Keine beliebige Kindstruktur

Das `html`-Element besitzt kein transparentes Content Model.

Insbesondere kann nicht beliebiger Flow Content direkt anstelle der
definierten Dokumentstruktur eingesetzt werden.

Die Konformitätsprüfung muss daher zwischen:

- dem `html`-Element,
- `head`,
- `body`,
- den jeweiligen Content Models dieser Elemente

unterscheiden.

---

# Tag Omission

Für `html` definiert WHATWG spezielle Regeln zur Tag-Auslassung in
`text/html`.

## Start-Tag

Das Start-Tag des `html`-Elements kann ausgelassen werden, wenn:

**das erste Element innerhalb des `html`-Elements kein Kommentar ist.**

Die Auslassung ist damit an den tatsächlichen Anfang des Inhalts gekoppelt.

Beispiel einer konformen HTML-Darstellung mit ausgelassenem `html`-Starttag:

```html
<head>
  <title>Beispiel</title>
</head>
<body>
  <p>Inhalt</p>
</body>
```

Das Weglassen des Tags ist eine Eigenschaft der HTML-Syntax.

Es bedeutet nicht, dass das `html`-Element semantisch nicht existiert.

Der Parser erzeugt weiterhin das entsprechende Document Element.

## End-Tag

Das End-Tag des `html`-Elements kann ausgelassen werden, wenn das
`html`-Element nicht unmittelbar von einem Kommentar gefolgt wird.

Auch hier handelt es sich um eine syntaktische Auslassungsregel.

## XML-Syntax

Die Tag-Omission-Regeln sind ausdrücklich Regeln für:

`text/html`

Sie dürfen nicht auf XML-Syntax übertragen werden.

---

# Content Attributes

Das `html`-Element besitzt keine eigenen elementbezogenen Content
Attributes.

Es akzeptiert:

**Global Attributes**

Damit sind insbesondere keine speziellen Attribute wie etwa:

- `href`
- `src`
- `action`
- `name`

Teil der `html`-Elementdefinition.

---

# Global Attributes auf `html`

Für `html` gelten die allgemeinen Regeln für Global Attributes.

Besonders relevant ist das `lang`-Attribut.

## `lang`

WHATWG ermutigt Autoren ausdrücklich dazu, auf dem Root-`html`-Element
ein `lang`-Attribut anzugeben.

Beispiel:

```html
<html lang="de">
```

Die Angabe der Dokumentsprache unterstützt unter anderem:

- Sprachverarbeitung,
- Sprachsynthese,
- Aussprachebestimmung,
- Übersetzungswerkzeuge.

`lang` ist dabei kein spezielles `html`-Attribut.

Es ist ein Global Attribute.

Die Empfehlung, `lang` am Root-Element zu setzen, ergibt sich aus der
besonderen Rolle des `html`-Elements als Dokumentwurzel.

## `dir`

Auch `dir` ist ein Global Attribute.

Die Bidirektionalitätsregeln für HTML werden nicht durch §4.1 allein
definiert, sondern über die allgemeinen Anforderungen an Global Attributes
und den Bidirectional-Text-Bereich.

## `class`, `id`, `slot`

Auch diese Attribute sind grundsätzlich Global Attributes.

Ihre allgemeinen DOM-/HTML-Regeln werden nicht erneut als spezielle
`html`-Attribute inventarisiert.

---

# Accessibility

Die WHATWG-Elementdefinition von `html` verweist für Accessibility auf:

- Accessibility Considerations für Autoren
- Accessibility Considerations für Implementierer

Diese Informationen werden nicht durch eine zusätzliche eigene
Accessibility-Semantik des `html`-Elements ersetzt.

## Sprache des Dokuments

Für Autoren ist insbesondere die Angabe der Dokumentsprache relevant.

Beispiel:

```html
<html lang="de">
```

Die WHATWG-Spezifikation weist ausdrücklich darauf hin, dass die
Sprachangabe auf dem Root-Element unter anderem Sprachsynthese und
Übersetzung unterstützt.

## Keine erfundene ARIA-Rolle

Für ZE-WebLab wird keine zusätzliche ARIA-Rolle als Bestandteil der
WHATWG-Elementdefinition erfunden.

ARIA- und Platform-Accessibility-API-Zuordnungen werden als separate
Accessibility-Rechercheebene behandelt.

---

# Sanitization

WHATWG weist für `html` die Sanitization-Kategorie:

**Default**

aus.

Damit ist `html` hinsichtlich der WHATWG-Sanitization-Klassifikation nicht
als `Unsafe` eingestuft.

Diese Einstufung ist jedoch nicht gleichbedeutend mit einer Aussage, dass
beliebige HTML-Dokumente oder beliebige Attribute automatisch sicher seien.

Die Sanitization-Kategorie des Elements ist von:

- HTML-Konformität,
- Security Policies,
- Trusted Types,
- Sanitizer-Konfigurationen,
- URL-Sicherheit,
- Script-Ausführung

zu unterscheiden.

---

# DOM Interface

Das DOM Interface für `html` lautet:

```webidl
[Exposed=Window]
interface HTMLHtmlElement : HTMLElement {
  [HTMLConstructor] constructor();
  // also has obsolete members
};
```

Das Interface ist:

`HTMLHtmlElement`

und erbt von:

`HTMLElement`

## Vererbung

Konzeptionell:

```text
EventTarget
  └── Node
      └── Element
          └── HTMLElement
              └── HTMLHtmlElement
```

Die vollständige Vererbung wird durch DOM und HTML definiert.

## Keine speziellen modernen Content-Attribute

Die aktuelle `HTMLHtmlElement`-Definition enthält keine eigenständigen
modernen elementbezogenen Attribute wie beispielsweise `href` oder
`src`.

Die semantisch wichtigen Attribute des Elements stammen überwiegend aus
dem Global-Attribute-Modell.

---

# `document.documentElement`

Das `html`-Element steht in direktem Zusammenhang mit dem
`Document`-Objekt.

WHATWG definiert für das DOM-Dokumentmodell:

> The `html` element of a document is its document element, if it's an
> `html` element, and null otherwise.

Für ZE-WebLab ist diese Regel wichtig, weil sie zwei Ebenen trennt:

## HTML-Ebene

```html
<html>
```

ist das HTML-Element.

## DOM-Ebene

```javascript
document.documentElement
```

liefert das Document Element gemäß DOM-/HTML-Dokumentmodell.

`document.documentElement` ist daher keine zweite Form des
`html`-Elements, sondern eine DOM-API zum Zugriff auf das entsprechende
Element.

---

# `Document` und `html`

Jedes HTML- und XML-Dokument in einem HTML User Agent wird durch ein
`Document`-Objekt repräsentiert.

Das `Document`-Objekt besitzt unter anderem:

- URL
- Origin
- Referrer
- Loading State
- Visibility State
- weitere Dokumentzustände

Diese Eigenschaften gehören zur Dokument-/DOM-Ebene.

Sie sind nicht zusätzliche Attribute des `html`-Elements.

---

# Beziehung zu `head`

Das `html`-Content-Model verlangt:

```text
head → body
```

`head` ist damit das erste strukturelle Element innerhalb des
Dokumentwurzelmodells.

WHATWG definiert `head` separat in §4.2.1.

Die Detailregeln für:

- Metadata Content,
- `title`,
- `base`,
- `link`,
- `meta`,
- `style`,
- weitere Metadaten

gehören nicht in die `html`-Elementdefinition.

Sie werden in:

`docs/html/02-document-metadata.md`

behandelt.

---

# Beziehung zu `body`

`body` bildet den zweiten Teil des Content Models von `html`.

WHATWG definiert `body` separat in §4.3.

Die Regeln für:

- Flow Content,
- Dokumentinhalt,
- Event Handler,
- Rendering,
- Body-/Frameset-Verhalten

gehören daher nicht als Unterelementregeln von `html` in diese Datei.

Die Verbindung besteht ausschließlich über das Content Model und die
Dokumentstruktur.

---

# HTML-Syntax und Dokumentstruktur

Die HTML-Syntax definiert für HTML-Dokumente eine feste Grundstruktur.

Ein HTML-Dokument besteht in der Schreibsyntax grundsätzlich aus:

1. optionalem BOM,
2. Kommentaren und ASCII Whitespace,
3. DOCTYPE,
4. Kommentaren und ASCII Whitespace,
5. Document Element in Form eines `html`-Elements.

Damit ist `html` in der HTML-Syntax das eigentliche Document Element.

## DOCTYPE

Ein typisches Dokument beginnt mit:

```html
<!doctype html>
<html>
  ...
</html>
```

Der DOCTYPE ist kein Kind des `html`-Elements.

Er gehört zur HTML-Syntax vor dem Document Element.

## Kommentare vor `html`

Kommentare und ASCII Whitespace können in der HTML-Syntax vor dem
Document Element vorkommen.

Sie werden deshalb nicht als Kinder des `html`-Elements behandelt.

---

# Parser-Beziehung

Das `html`-Element besitzt eine besondere Stellung im HTML-Parser.

Der HTML-Parser erzeugt bei der Verarbeitung eines normalen HTML-Dokuments
die entsprechende Dokumentstruktur auch dann, wenn bestimmte Tags in der
Eingabe fehlen.

Daher gilt:

**Tag omission ist nicht gleichbedeutend mit dem Fehlen des Elements im
DOM.**

Beispiel:

```html
<!doctype html>
<head>
  <title>Beispiel</title>
</head>
<body>
  <p>Text</p>
</body>
```

kann vom HTML-Parser als Dokument mit einem `html`-Document-Element
repräsentiert werden, obwohl das `html`-Start- und End-Tag im Quelltext
nicht explizit stehen.

---

# `html` in `text/html` und XML

Die HTML-Spezifikation unterscheidet zwischen:

- HTML-Syntax für `text/html`
- XML-Syntax

Die Tag-Omission-Regeln für `html` gehören zur HTML-Syntax.

Die allgemeine DOM-Bedeutung eines `html`-Elements darf nicht mit den
Parsing-Regeln für XML gleichgesetzt werden.

Insbesondere:

- `text/html` wird durch den HTML-Parser verarbeitet,
- XML wird nach XML-Regeln verarbeitet,
- HTML-spezifische Tag-Omission ist keine XML-Regel.

---

# Compound Documents und Subdocuments

Die Context-Definition von `html` enthält neben der normalen
Document-Element-Verwendung den Fall:

> Wherever a subdocument fragment is allowed in a compound document.

Damit berücksichtigt WHATWG, dass HTML auch als Bestandteil eines
größeren Dokument-/Integrationsmodells auftreten kann.

Dieser Kontext darf nicht mit beliebiger Verschachtelung von vollständigen
HTML-Dokumenten verwechselt werden.

Für ZE-WebLab ist daher zwischen:

- eigenständigem HTML-Dokument,
- Subdocument Fragment,
- Compound Document,
- HTML-Element innerhalb des DOM

zu unterscheiden.

---

# Normative Sonderregeln

## 1. `html` ist das Document Element

Das `html`-Element repräsentiert den Root eines HTML-Dokuments.

## 2. Content Model ist strukturell

Das Content Model ist:

```text
head gefolgt von body
```

## 3. Keine Content Category

`html` besitzt keine WHATWG Content Category.

## 4. Global Attributes

Das Element besitzt keine speziellen Content Attributes.

Es akzeptiert Global Attributes.

## 5. `lang`

Autoren werden ausdrücklich dazu angehalten, `lang` auf dem Root-Element
anzugeben, wenn die Dokumentsprache bekannt ist.

## 6. Tag-Omission

Start- und End-Tag können unter exakt definierten Bedingungen ausgelassen
werden.

Diese Regeln gelten für `text/html`.

## 7. DOM-Zugriff

Das Document Element ist über:

```javascript
document.documentElement
```

zugänglich.

## 8. DOM-Interface

Das Element implementiert:

`HTMLHtmlElement`

## 9. Sanitization

Die WHATWG-Sanitization-Kategorie ist:

`Default`

## 10. Accessibility

Die Spezifikation verweist auf eigene Accessibility Considerations.

Die detaillierte Accessibility-Zuordnung ist eine separate Ebene.

---

# Häufige Fehlinterpretationen

## `html` ist kein Flow-Content-Container

Das `html`-Element besitzt keine Flow-Content-Kategorie.

Seine Funktion ist strukturell und dokumentbezogen.

## `html` ist nicht optional

Die Möglichkeit, Tags wegzulassen, bedeutet nicht, dass das
Document-Element konzeptionell optional wäre.

Tag omission betrifft die Quellsyntax.

Das Dokumentmodell besitzt weiterhin das entsprechende Document Element.

## `html` ist nicht nur ein Wrapper

Eine Beschreibung wie „`html` ist einfach der Container für die ganze
Seite“ ist für die Referenz zu unpräzise.

WHATWG definiert das Element als Root des HTML-Dokuments und verbindet
es mit einem konkreten Content Model und dem DOM Document Model.

## `lang` ist kein spezielles `html`-Attribut

`lang` ist ein Global Attribute.

Seine besondere Empfehlung auf `html` ergibt sich aus der Rolle des
Elements als Dokumentwurzel.

## `document.documentElement` ist kein eigenes HTML-Element

Es handelt sich um eine DOM-Eigenschaft, die auf das Document Element
verweist.

---

# Querverweise

## §3.1 Documents

Relevant für:

- `Document`
- URL
- Origin
- Referrer
- Document State
- `document.documentElement`

## §3.2 Elements

Relevant für:

- DOM-Repräsentation von Elementen
- Element Interfaces
- Element Definitions
- Content Models
- Global Attributes

## §3.2.5 Content Models

Relevant für die allgemeine Bedeutung von:

- Content Model
- inter-element whitespace
- Nothing Content Model
- Content Categories

Das `html`-Element selbst besitzt ein spezifisches strukturelles
Content Model.

## §3.2.6 Global Attributes

Relevant für alle Global Attributes des `html`-Elements, insbesondere:

- `lang`
- `dir`
- `id`
- `class`
- `style`
- `title`
- `data-*`

## §3.2.9 ARIA und Platform Accessibility APIs

Relevant für die übergreifende Accessibility-Behandlung von HTML.

## §4.2 Document metadata

`head` ist der erste Teil des Content Models von `html`.

## §4.3 Sections

`body` ist der zweite Teil des Content Models von `html`.

## §8 The HTML syntax

Relevant für:

- DOCTYPE
- Document Element
- Start-Tag
- End-Tag
- Tag omission
- Parsing

## DOM Standard

Relevant für:

- `Document`
- `document.documentElement`
- `Element`
- `HTMLElement`
- DOM Tree

---

# Status / V1

## WHATWG-Status

`html` ist im aktuellen WHATWG HTML Living Standard definiert.

**WHATWG-Definition:** vorhanden.

## Konformität

Die Verwendung ist nicht pauschal durch die bloße Existenz des Elements
konform.

Für eine konkrete Konformitätsprüfung sind insbesondere zu prüfen:

- Context
- Content Model
- Tag-Omission-Regeln
- Global Attributes
- HTML-Syntax
- Dokumentstruktur

## Browser-Support

Browser-Kompatibilität wird in ZE-WebLab nicht als WHATWG-Status geführt.

Dass aktuelle Browser `html` unterstützen, ist daher keine Begründung für
den WHATWG-Status.

Die Browser-Kompatibilitätsmatrix bleibt eine separate Rechercheebene.

---

# V1-Referenz

| Eigenschaft | Wert |
|---|---|
| Feature | `html` |
| Bereich | Document element |
| Feature-Typ | HTML-Element |
| WHATWG | §4.1.1 |
| Status | Im WHATWG-Standard definiert |
| Content Categories | Keine |
| Context | Document Element; Subdocument Fragment in Compound Documents |
| Content Model | `head` gefolgt von `body` |
| Tag Omission | Start- und End-Tag unter definierten Bedingungen auslassbar |
| Content Attributes | Global Attributes |
| Accessibility | WHATWG Accessibility Considerations für Autoren/Implementierer |
| Sanitization | Default |
| DOM Interface | `HTMLHtmlElement` |
| Browser-Support | separate Rechercheebene |

---

# Offene Punkte

Für die Elementprüfung von §4.1 bestehen keine offenen Punkte hinsichtlich
des HTML-Elementinventars.

Bewusst separat zu behandeln bleiben:

1. vollständiges Global-Attribute-Inventar,
2. vollständige Accessibility-/ARIA-Zuordnungen,
3. vollständige DOM-Spezifikation des `Document`-Objekts,
4. vollständige HTML-Parsing- und Tree-Construction-Spezifikation,
5. Browser-Kompatibilität,
6. XML-/HTML-Integrationsdetails,
7. compound-document-spezifische Integrationsfälle.

Diese Punkte sind keine fehlenden Bestandteile der `html`-Elementdefinition,
sondern separate Wissensebenen des ZE-WebLab-Referenzmodells.

---

# Prüfstatus

| Prüfbereich | Status |
|---|---|
| WHATWG §4.1 Struktur geprüft | abgeschlossen |
| `html` geprüft | abgeschlossen |
| Content Categories geprüft | abgeschlossen |
| Context geprüft | abgeschlossen |
| Content Model geprüft | abgeschlossen |
| Tag Omission geprüft | abgeschlossen |
| Content Attributes geprüft | abgeschlossen |
| Global Attributes abgegrenzt | abgeschlossen |
| Accessibility-Verweise geprüft | abgeschlossen |
| Sanitization geprüft | abgeschlossen |
| DOM Interface geprüft | abgeschlossen |
| `Document`-Beziehung geprüft | abgeschlossen |
| `document.documentElement` geprüft | abgeschlossen |
| HTML-Syntax-Beziehung geprüft | abgeschlossen |
| Parser-/Tag-Omission-Beziehung geprüft | abgeschlossen |
| `head`-/`body`-Beziehung geprüft | abgeschlossen |
| Querverweise geprüft | abgeschlossen |
| Browser-Support getrennt behandelt | abgeschlossen |
| Offene Punkte dokumentiert | abgeschlossen |

---

# Quellen / Referenzen

## Primärquelle

WHATWG HTML Living Standard:

**§4.1 The document element**

Unterabschnitt:

**§4.1.1 The `html` element**

## Relevante WHATWG-Querverweise

- §3.1 Documents
- §3.1.1 The `Document` object
- §3.1.7 DOM tree accessors
- §3.2 Elements in the DOM
- §3.2.4 Element definitions
- §3.2.5 Content models
- §3.2.6 Global attributes
- §3.2.9 Requirements related to ARIA and to platform accessibility APIs
- §4.2 Document metadata
- §4.3 Sections
- §8 The HTML syntax

## Externe bzw. verknüpfte Standards

Die WHATWG-Definition verweist für einzelne Aspekte unter anderem auf:

- DOM Standard
- WAI-ARIA / Accessibility-Spezifikationen

Diese Standards werden hier nicht als Ersatz für die WHATWG-
Elementdefinition verwendet.

---

# Recherchefazit

§4.1 „The document element“ definiert auf HTML-Elementebene ausschließlich:

```text
html
```

Das Element:

- repräsentiert die Wurzel eines HTML-Dokuments,
- besitzt keine Content Category,
- wird als Document Element verwendet,
- kann unter den definierten Bedingungen als Subdocument Fragment in einem
  Compound Document verwendet werden,
- besitzt das Content Model `head` gefolgt von `body`,
- akzeptiert Global Attributes,
- besitzt keine eigenen elementbezogenen Content Attributes,
- besitzt spezielle Tag-Omission-Regeln für `text/html`,
- besitzt die Sanitization-Kategorie `Default`,
- implementiert `HTMLHtmlElement`,
- steht in direkter Beziehung zum DOM-`Document` und zu
  `document.documentElement`,
- und besitzt relevante Accessibility Considerations.

Besonders wichtig für ZE-WebLab ist die Trennung zwischen:

**HTML-Element**

```text
<html>
```

und

**DOM-Zugriff**

```javascript
document.documentElement
```

sowie zwischen:

**Tag omission**

und

**tatsächlichem Vorhandensein des Document Elements im DOM**.

Damit ist §4.1 auf der HTML-Elementebene vollständig erfasst.