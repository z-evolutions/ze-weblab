# ZE-WebLab – HTML-Referenz: Document metadata

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab  
**Datei:** `docs/html/02-document-metadata.md`  
**Themenbereich:** Document metadata  
**WHATWG-Bereich:** §4.2 Document metadata  
**Geprüfter WHATWG-Stand:** HTML Living Standard, 11. August 2026

Diese Datei dokumentiert den vollständigen WHATWG-Bereich §4.2
„Document metadata“.

Der Bereich definiert folgende HTML-Elemente:

- `head`
- `title`
- `base`
- `link`
- `meta`
- `style`

Zusätzlich enthält §4.2 umfangreiche normative Unterkonzepte:

- Link-Verarbeitung
- Link Types
- externe Ressourcen
- Hyperlinks über `link`
- `Link`-Header
- Early Hints
- Meta-Namen
- Pragma Directives
- Character Encoding Declarations
- Styling Processing
- Interaktionen zwischen Styling und Scripting

Diese Konzepte werden nicht fälschlich als zusätzliche HTML-Elemente
gezählt.

Insbesondere werden:

- Link Types,
- Metadata Names,
- `http-equiv`-States,
- CSS Style Sheets,
- Fetch-/Processing Models,
- HTTP `Link`-Header,
- Early Hints,
- CSS Style Sheet Sets

als eigene Feature-/Konzept-Ebenen behandelt.

---

# WHATWG-Struktur

Der aktuelle WHATWG-Bereich ist:

## 4.2 Document metadata

### 4.2.1 The `head` element

### 4.2.2 The `title` element

### 4.2.3 The `base` element

### 4.2.4 The `link` element

#### 4.2.4.1 Processing the `media` attribute

#### 4.2.4.2 Processing the `type` attribute

#### 4.2.4.3 Fetching and processing a resource from a `link` element

#### 4.2.4.4 Processing `Link` headers

#### 4.2.4.5 Early hints

#### 4.2.4.6 Providing users with a means to follow hyperlinks created using
the `link` element

### 4.2.5 The `meta` element

#### 4.2.5.1 Standard metadata names

#### 4.2.5.2 Other metadata names

#### 4.2.5.3 Pragma directives

#### 4.2.5.4 Specifying the document's character encoding

### 4.2.6 The `style` element

### 4.2.7 Interactions of styling and scripting

---

# Inventar

| Feature | WHATWG-Abschnitt | Feature-Typ | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Accessibility | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| `head` | §4.2.1 | HTML-Element | Keine | Als erstes Element in `html` | Metadata Content gemäß Dokumentkontext | Start-/End-Tag unter Bedingungen auslassbar | Global Attributes | WHATWG Accessibility Considerations | Default | `HTMLHeadElement` | Im WHATWG-Standard definiert |
| `title` | §4.2.2 | HTML-Element | Metadata | In `head`, wenn kein anderes `title` vorhanden ist | Text, der kein inter-element whitespace ist | keine Auslassung | Global Attributes | WHATWG Accessibility Considerations | Default | `HTMLTitleElement` | Im WHATWG-Standard definiert |
| `base` | §4.2.3 | HTML-Element | Metadata | In `head`, das kein anderes `base` enthält | Nothing | kein End-Tag | Global + `href`, `target` | WHATWG Accessibility Considerations | Unsafe | `HTMLBaseElement` | Im WHATWG-Standard definiert |
| `link` | §4.2.4 | HTML-Element | Metadata; unter Bedingungen Flow/Phrasing | Metadata Context; bestimmte body-/`noscript`-Kontexte | Nothing | kein End-Tag | Global + `href`, `crossorigin`, `rel`, `media`, `integrity`, `hreflang`, `type`, `referrerpolicy`, `sizes`, `imagesrcset`, `imagesizes`, `as`, `blocking`, `color`, `disabled`, `fetchpriority`; spezielles `title` | WHATWG Accessibility Considerations | Uncategorized | `HTMLLinkElement` | Im WHATWG-Standard definiert |
| `meta` | §4.2.5 | HTML-Element | Metadata; mit `itemprop` zusätzlich Flow/Phrasing | abhängig von `charset`, `http-equiv`, `name`, `itemprop` | Nothing | kein End-Tag | Global + `name`, `http-equiv`, `content`, `charset`, `media` | WHATWG Accessibility Considerations | Uncategorized | `HTMLMetaElement` | Im WHATWG-Standard definiert |
| `style` | §4.2.6 | HTML-Element | Metadata | Metadata Context; `noscript` innerhalb von `head` | Text, der ein konformes Stylesheet bildet | keine Auslassung | Global + `media`, `blocking`; spezielles `title` | WHATWG Accessibility Considerations | Uncategorized | `HTMLStyleElement` | Im WHATWG-Standard definiert |

---

# Detailprüfung: `head`

## WHATWG-Zuordnung

`head` ist in §4.2.1 definiert.

Das Element repräsentiert eine Sammlung von Metadaten für das
`Document`.

`head` ist damit kein allgemeiner Container für sichtbaren Seiteninhalt.

## Content Categories

`head` besitzt:

**Keine Content Categories.**

## Context

`head` darf als erstes Element innerhalb eines `html`-Elements verwendet
werden.

Die Position ist damit strukturell festgelegt.

## Content Model

Das Content Model ist abhängig davon, ob:

- das Dokument ein `iframe`-`srcdoc`-Dokument ist oder
- Titelinformationen durch ein höhergeordnetes Protokoll bereitgestellt
  werden.

### Wenn kein eigener Titel erforderlich ist

Dann sind null oder mehr Elemente von Metadata Content erlaubt.

Zusätzlich gelten:

- höchstens ein `title`
- höchstens ein `base`

### Im Normalfall

Dann sind ein oder mehrere Elemente von Metadata Content erforderlich.

Dabei gilt:

- genau ein `title`
- höchstens ein `base`

Damit ist `title` grundsätzlich Bestandteil des normalen `head`-Modells.

Eine Ausnahme besteht, wenn das Dokument vernünftigerweise keinen eigenen
Titel benötigt bzw. Titelinformationen von einem höheren Protokoll
bereitgestellt werden.

## Tag Omission

### Start-Tag

Das Start-Tag von `head` kann in `text/html` ausgelassen werden, wenn:

- das Element leer ist oder
- das erste Ding innerhalb von `head` ein Element ist.

### End-Tag

Das End-Tag kann ausgelassen werden, wenn `head` nicht unmittelbar gefolgt
wird von:

- ASCII whitespace oder
- einem Kommentar.

## Content Attributes

`head` besitzt keine eigenen Content Attributes.

Es gelten die Global Attributes.

## Accessibility

WHATWG verweist auf Accessibility Considerations für:

- Autoren
- Implementierer

Die konkrete Accessibility-Semantik wird nicht als zusätzliche
Elementdefinition innerhalb von §4.2 erfunden.

## Sanitization

Sanitization:

**Default**

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLHeadElement : HTMLElement {
  [HTMLConstructor] constructor();
};
```

Interface:

`HTMLHeadElement`

Vererbung:

```text
EventTarget
└── Node
    └── Element
        └── HTMLElement
            └── HTMLHeadElement
```

## Semantik

`head` sammelt Metadaten für das `Document`.

Typische Inhalte sind:

- `title`
- `base`
- `link`
- `meta`
- `style`

Außerdem können unter den jeweiligen Regeln andere Metadata- bzw.
Script-supporting Elements vorkommen.

`head` repräsentiert selbst nicht die sichtbare Seitenstruktur.

---

# Detailprüfung: `title`

## WHATWG-Zuordnung

`title` ist in §4.2.2 definiert.

## Semantik

`title` repräsentiert den Titel bzw. Namen des Dokuments.

Der Titel soll das Dokument auch außerhalb seines unmittelbaren
Kontexts identifizierbar machen.

Geeignete Verwendungsorte sind beispielsweise:

- Browser History
- Bookmarks
- Suchergebnisse
- Benutzeroberflächen

Der Dokumenttitel muss nicht identisch mit der ersten Überschrift sein.

## Content Categories

`title` ist:

**Metadata Content**

## Context

`title` darf innerhalb eines `head`-Elements verwendet werden, das noch
kein anderes `title`-Element enthält.

Damit ist pro Dokument höchstens ein `title`-Element vorgesehen.

## Content Model

Das Content Model lautet:

**Text, der kein inter-element whitespace ist.**

Damit ist beispielsweise reiner Leerraum kein sinnvoller Titelinhalt.

## Tag Omission

Weder Start- noch End-Tag sind auslassbar.

## Content Attributes

`title` besitzt keine eigenen Content Attributes.

Es gelten Global Attributes.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLTitleElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions] attribute DOMString text;
};
```

Interface:

`HTMLTitleElement`

## `text`

Die IDL-Eigenschaft:

```javascript
title.text
```

liefert den Child Text Content des Elements.

Beim Setzen ersetzt sie den vorhandenen Inhalt durch den angegebenen
String.

## `document.title`

Der für das Dokument verwendete Titel wird über die DOM-IDL-Eigenschaft:

```javascript
document.title
```

bereitgestellt.

Das ist ein DOM-/Document-Konzept und kein zweites HTML-Element.

## Eindeutigkeit

Es darf nicht mehr als ein `title`-Element pro Dokument geben.

Die konkrete Notwendigkeit eines `title` ergibt sich aus dem Content Model
von `head`.

## Richtung

Wenn der Titel in der Benutzeroberfläche verwendet wird, soll die
Richtung des `title`-Elements für die Darstellung des Titels berücksichtigt
werden.

## Accessibility

Die WHATWG-Spezifikation verweist auf Accessibility Considerations für
Autoren und Implementierer.

Ein aussagekräftiger Titel ist insbesondere wichtig, weil er außerhalb
des unmittelbaren Dokumentkontexts verwendet werden kann.

## Sanitization

Sanitization:

**Default**

---

# Detailprüfung: `base`

## WHATWG-Zuordnung

`base` ist in §4.2.3 definiert.

## Semantik

`base` ermöglicht die Festlegung:

1. der Document Base URL für URL-Auflösung,
2. des Default-Namens eines Navigable für Navigationen und
   Form-Submissions.

Das Element repräsentiert keinen sichtbaren Inhalt.

## Content Categories

`base` ist:

**Metadata Content**

## Context

`base` darf in einem `head` verwendet werden, das kein anderes
`base`-Element enthält.

## Content Model

Das Content Model ist:

**Nothing**

## Tag Omission

Das End-Tag ist nicht erforderlich.

`base` ist ein Void Element.

## Content Attributes

Neben Global Attributes:

### `href`

Definiert die Document Base URL.

Wenn vorhanden, muss der Wert eine gültige URL sein, die gegebenenfalls
von Leerraum umgeben sein darf.

### `target`

Definiert den Default-Navigable für:

- Hyperlink-Navigation
- Form Submission Navigation

Der Wert muss ein gültiger Navigable Target Name oder ein gültiges
Target Keyword sein.

## Pflichtbedingung

Ein `base`-Element muss mindestens eines besitzen:

- `href`
- `target`

oder beide.

## Mehrere `base`-Elemente

Es darf nicht mehr als ein `base`-Element pro Dokument geben.

Wenn mehrere `base`-Elemente mit `href` bzw. `target` vorhanden sind,
werden nur die jeweils ersten berücksichtigt.

## Position

Ein `base` mit `href` muss vor anderen Elementen im Tree stehen, die
Attribute besitzen, deren Werte URLs sind.

Damit ist die Position des Elements für die URL-Auflösung relevant.

Ein `base` mit `target` muss vor Elementen stehen, die Hyperlinks
repräsentieren.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLBaseElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, ReflectSetter] attribute USVString href;
  [CEReactions, Reflect] attribute DOMString target;
};
```

Interface:

`HTMLBaseElement`

## Sanitization

Sanitization:

**Unsafe**

## Accessibility

WHATWG verweist auf Accessibility Considerations.

`base` repräsentiert keinen Benutzerinhalt und sollte deshalb nicht als
sichtbares semantisches Element behandelt werden.

---

# Document Base URL

Das `base`-Element wirkt sich auf die Auflösung relativer URLs aus.

Beispiel:

```html
<base href="https://www.example.com/news/index.html">
<a href="archives.html">archives</a>
```

Die relative URL wird relativ zur Document Base URL aufgelöst.

Im Beispiel führt sie zu:

```text
https://www.example.com/news/archives.html
```

Die Regeln gehören zur URL-/Document-Base-Ebene und nicht zur
Elementdarstellung.

---

# Default Target

Das `target`-Attribut von `base` definiert den Default-Navigable für
Navigationen.

Für ein `a`, `area` oder `form` wird zunächst ein eigenes `target`
berücksichtigt.

Fehlt dieses, kann der erste passende `base[target]`-Wert des Dokuments
verwendet werden.

WHATWG definiert hierfür einen eigenen Algorithmus.

Ein Zielname mit bestimmten problematischen Kombinationen aus ASCII Tab/
Newline und `<` wird dabei auf `_blank` gesetzt.

---

# Detailprüfung: `link`

## WHATWG-Zuordnung

`link` ist in §4.2.4 definiert.

Der Abschnitt ist wesentlich umfangreicher als die reine
Elementdefinition.

Er umfasst:

- externe Ressourcen,
- Hyperlinks,
- Link Types,
- Fetching,
- MIME-Type-Verarbeitung,
- Media Queries,
- SRI,
- Referrer Policy,
- Image Source Sets,
- Preload,
- Module Preload,
- HTTP Link Headers,
- Early Hints.

## Content Categories

`link` ist:

- Metadata Content

Zusätzlich, wenn das Element im `body` erlaubt ist:

- Flow Content
- Phrasing Content

## Context

`link` kann verwendet werden:

- wo Metadata Content erwartet wird,
- innerhalb eines `noscript`, das Kind von `head` ist,
- wenn im `body` erlaubt: wo Phrasing Content erwartet wird.

## Content Model

Das Content Model ist:

**Nothing**

## Tag Omission

Das End-Tag ist nicht erforderlich.

`link` ist ein Void Element.

## DOM Interface

`HTMLLinkElement`

Wesentliche IDL-Mitglieder:

```text
href
crossOrigin
rel
as
relList
media
integrity
hreflang
type
sizes
imageSrcset
imageSizes
referrerPolicy
blocking
disabled
fetchPriority
```

Das Interface umfasst außerdem das CSSOM-Interface `LinkStyle`.

## Sanitization

Sanitization:

**Uncategorized**

---

# `link` – Grundregel

Ein `link`-Element verbindet das Dokument mit anderen Ressourcen oder
erzeugt Hyperlinks.

Die Adresse wird durch `href` angegeben.

Wenn `href` vorhanden ist, muss sein Wert eine gültige nicht-leere URL
sein, gegebenenfalls von Leerraum umgeben.

Mindestens eines muss vorhanden sein:

- `href`
- `imagesrcset`

Wenn beide fehlen, definiert das Element keinen Link.

---

# `link` – `rel`

`rel` bestimmt die Beziehungen zwischen:

- dem Dokument,
- dem Ziel bzw. der Ressource.

Der Wert ist eine ungeordnete Menge eindeutiger, durch Leerraum getrennter
Tokens.

Die erlaubten Link Types werden separat definiert.

Wenn:

- `rel` fehlt,
- `rel` keine Keywords enthält oder
- kein verwendetes Keyword für `link` zulässig ist,

entstehen keine Links.

## Supported Tokens

WHATWG nennt für `link` insbesondere:

- `alternate`
- `dns-prefetch`
- `expect`
- `icon`
- `manifest`
- `modulepreload`
- `next`
- `pingback`
- `preconnect`
- `prefetch`
- `preload`
- `search`
- `stylesheet`

Welche Tokens tatsächlich als `supported tokens` exponiert werden, hängt
davon ab, welche Processing Models der User Agent unterstützt.

`relList.supports()` kann zur Feature Detection verwendet werden.

## `canonical`

`canonical` ist nicht Bestandteil der allgemeinen Liste der von einem
User Agent typischerweise unterstützten `link`-Tokens.

WHATWG weist darauf hin, dass ein User Agent theoretisch ein Processing
Model dafür unterstützen könnte, insbesondere in einem Suchmaschinen-
Kontext.

---

# `link` – `rel` oder `itemprop`

Ein `link`-Element muss:

- entweder `rel`
- oder `itemprop`

besitzen.

Beide gleichzeitig sind nicht erlaubt.

Wenn `itemprop` vorhanden ist oder `rel` ausschließlich aus body-ok
Keywords besteht, kann das Element im `body` verwendet werden.

Damit ist `link` kein ausschließlich auf `head` beschränktes Element.

---

# `link` – Hyperlinks und externe Ressourcen

Mit `link` können zwei wesentliche Kategorien erzeugt werden:

- Hyperlinks
- Links zu externen Ressourcen

Ein einzelnes `link`-Element kann mehrere Links erzeugen.

Beispiel:

```html
<link rel="next stylesheet" href="next.css">
```

kann gleichzeitig:

- einen Hyperlink über `next`
- einen externen Ressourcen-Link über `stylesheet`

erzeugen.

Die Verarbeitung erfolgt pro erzeugtem Link und nicht pauschal pro
Element.

---

# `link` – `href`

`href` gibt die Adresse des Links an.

Der Wert muss eine gültige nicht-leere URL sein, gegebenenfalls umgeben
von Leerraum.

Bei bestimmten Preload-Konfigurationen kann zusätzlich
`imagesrcset` die Ressourcenauswahl beeinflussen.

---

# `link` – `crossorigin`

`crossorigin` ist ein CORS Settings Attribute.

Es ist insbesondere für externe Ressourcen vorgesehen.

Die konkrete CORS-Behandlung hängt vom jeweiligen Link Type und dessen
Processing Model ab.

---

# `link` – `media`

Der Wert muss eine gültige Media Query List sein.

Die Semantik unterscheidet zwischen:

## Hyperlink

`media` ist rein beratend.

Es beschreibt, für welches Medium das Dokument bzw. die Ressource
gedacht ist.

## Externe Ressource

`media` ist normativ für die Anwendung der Ressource.

Die Ressource wird nur angewendet, wenn:

- die Media Query auf die Umgebung zutrifft und
- die übrigen Bedingungen des jeweiligen Link Types erfüllt sind.

Default:

```text
all
```

---

# `link` – `integrity`

`integrity` enthält Integrity Metadata für Requests, für die das
Element verantwortlich ist.

Das Attribut darf nur verwendet werden, wenn `rel` mindestens einen
der folgenden Link Types enthält:

- `stylesheet`
- `preload`
- `modulepreload`

Die eigentliche Prüfung erfolgt nach dem Subresource-Integrity-Modell.

---

# `link` – `hreflang`

`hreflang` beschreibt die Sprache der verlinkten Ressource.

WHATWG gibt ihm für `link` dieselbe grundlegende Semantik wie dem
entsprechenden `hreflang`-Attribut von `a`.

---

# `link` – `type`

`type` gibt den MIME-Type der referenzierten Ressource als Hinweis an.

Das Attribut ist rein beratend.

Der Wert muss eine gültige MIME-Type-Zeichenfolge sein.

Bei externen Ressourcen kann der User Agent dadurch vermeiden, Ressourcen
zu laden, deren Typ er nicht unterstützt.

Wichtig:

`type` ist nicht autoritativ.

Nach dem Fetch wird der tatsächliche Typ der Ressource anhand der
entsprechenden Regeln bestimmt.

---

# `link` – `referrerpolicy`

`referrerpolicy` ist ein Referrer Policy Attribute.

Es beeinflusst die Referrer Policy für Fetches, die durch das
`link`-Element ausgelöst werden.

---

# `link` – `title`

`title` besitzt auf `link` besondere Semantik.

Grundsätzlich bezeichnet es den Titel des Links.

Eine wichtige Ausnahme betrifft Stylesheet-Links:

Bei einem Stylesheet-Link im Dokumentbaum definiert `title` den Namen
eines CSS Style Sheet Sets.

Der `title`-Wert eines `link`-Elements wird nicht einfach vom
`title`-Attribut eines Vorfahren geerbt.

---

# `link` – `sizes`

`sizes` beschreibt die Größen von Icons.

Die Werte sind eine ungeordnete Menge eindeutiger Tokens.

Zulässig sind:

- `any`
- Dimensionen der Form `widthxheight`

Die Werte müssen gültige nicht-negative Integer ohne führende Null sein.

`sizes` darf nur bei `link`-Elementen mit:

- `rel="icon"`
- oder `rel="apple-touch-icon"`

verwendet werden.

`apple-touch-icon` ist eine registrierte Erweiterung eines Link Types;
User Agents müssen dafür kein bestimmtes Processing Model implementieren.

---

# `link` – `imagesrcset`

`imagesrcset` ist ein `srcset`-Attribut.

Zusammen mit `href` kann es die Image Sources eines Source Sets bestimmen.

Es ist insbesondere für:

```text
rel=preload
as=image
```

vorgesehen.

---

# `link` – `imagesizes`

`imagesizes` ist ein `sizes`-Attribut und bestimmt bei
`imagesrcset` die Source Size.

Wenn `imagesrcset` Width Descriptors verwendet, muss `imagesizes`
vorhanden sein.

`imagesrcset` und `imagesizes` dürfen nur im entsprechenden
Preload-Image-Kontext verwendet werden.

---

# `link` – `as`

`as` bestimmt das Ziel eines Preload- oder Module-Preload-Requests.

Es ist ein Enumerated Attribute.

Bei:

```text
rel=preload
```

muss es einen gültigen Preload Destination State angeben.

Bei:

```text
rel=modulepreload
```

kann es einen gültigen Module Preload Destination State angeben.

Für andere `link`-Elemente darf es nicht verwendet werden.

Für `preload` ist ein fehlender bzw. ungültiger Wert ein Fehler.

Bei `modulepreload` wird ein fehlender Wert als `script` behandelt.

---

# `link` – `blocking`

`blocking` ist ein Blocking Attribute.

Im `link`-Kontext wird es insbesondere von:

- `stylesheet`
- `expect`

verwendet.

Es darf nur zusammen mit diesen Link Types verwendet werden.

---

# `link` – `color`

`color` wird mit dem Link Type `mask-icon` verwendet.

Der Wert muss der CSS-`<color>`-Syntax entsprechen.

Das Attribut darf nur bei `rel` mit `mask-icon` angegeben werden.

WHATWG definiert für `color` derzeit keine allgemeinen User-Agent-
Anforderungen zur konkreten Nutzung.

`mask-icon` ist eine registrierte Erweiterung des Link-Type-Sets.

---

# `link` – `disabled`

`disabled` ist ein Boolean Attribute.

Es wird für Stylesheet-Links verwendet.

Es darf nur bei:

```text
rel=stylesheet
```

angegeben werden.

`link`-Elemente besitzen dafür einen internen Zustand:

**explicitly enabled**

Dieser ist initial `false`.

Das dynamische Entfernen des `disabled`-Attributs setzt diesen Zustand
entsprechend und kann dazu führen, dass ein Stylesheet geladen und
angewendet wird.

---

# `link` – `fetchpriority`

`fetchpriority` ist ein Fetch Priority Attribute.

Es dient bei externen Ressourcen dazu, die Fetch-Priorität des
verursachten Fetch-Vorgangs zu beeinflussen.

Die konkrete Verarbeitung erfolgt über das Fetch-Modell.

---

# Link Processing Model

§4.2.4 enthält mehrere eigene Processing Models.

Diese sind keine zusätzlichen HTML-Elemente.

## Processing the `media` attribute

Unterscheidet:

- advisory semantics bei Hyperlinks
- prescriptive semantics bei externen Ressourcen

## Processing the `type` attribute

Der deklarierte Typ dient als Hint.

Der tatsächlich empfangene Ressourcentyp bleibt maßgeblich.

## Fetching and processing

Externe Ressourcen besitzen ein eigenes:

**fetch and process the linked resource**

Processing Model.

Das Modell erzeugt unter anderem:

- Link Processing Options
- Requests
- Fetches
- Response Processing
- Erfolgs-/Fehlerzustände

## Link Processing Options

WHATWG definiert hierfür eine interne Struktur mit unter anderem:

- `href`
- `initiator`
- `integrity`
- `type`
- cryptographic nonce metadata
- destination
- crossorigin
- referrer policy
- source set
- base URL
- origin
- environment
- policy container
- document
- on document ready
- fetch priority

Diese Struktur ist kein HTML-Element.

---

# `Link`-Header

§4.2.4.4 behandelt die Verarbeitung von HTTP-`Link`-Headern.

Diese Header sind keine `link`-Elemente.

WHATWG definiert jedoch eine Beziehung zwischen:

- HTTP `Link`-Headern
- `link`-Elementen

Link Header werden geparst und in entsprechende Link-Processing-
Informationen überführt.

Dabei können insbesondere:

- `rel`
- Ziel-URL
- Attribute
- Media
- `as`
- `crossorigin`
- `integrity`
- `type`

in die Verarbeitung eingehen.

---

# Early Hints

§4.2.4.5 behandelt HTTP 103 Early Hints.

Early Hints erlauben User Agents, bestimmte Ressourcen bereits vor der
endgültigen HTTP-Antwort zu laden.

Beispiel:

```http
103 Early Hint
Link: </style.css>; rel=preload; as=style
```

Danach kann die endgültige Antwort folgen.

## Zweck

Early Hints ermöglichen insbesondere:

- spekulatives Laden
- frühzeitiges Preloading
- Nutzung von Ressourcen, bevor das vollständige HTML-Dokument
  verarbeitet wurde

## Reihenfolge

Early-Hint-`Link`-Header werden vor `Link`-Headern aus der finalen
Response verarbeitet.

Anschließend werden `link`-Elemente im Dokument verarbeitet.

## CSP

Eine Early-Hint-Response kann auch eine Content-Security-Policy enthalten,
die beim Verarbeiten der Early Hints berücksichtigt wird.

## Elementabgrenzung

Early Hints sind:

**HTTP-/Fetch-Konzept**

und kein HTML-Element.

---

# `link` – Benutzeroberfläche

Interactive User Agents können Benutzern eine Möglichkeit geben,
Hyperlinks anzuzeigen bzw. zu verfolgen, die durch `link` erzeugt wurden.

Die Spezifikation schreibt die konkrete Benutzeroberfläche nicht vor.

Mögliche Informationen sind:

- Beziehung (`rel`)
- Titel (`title`)
- Adresse (`href`)
- Sprache (`hreflang`)
- Medium (`media`)
- Typ (`type`)

Die Hyperlinks werden normalerweise nicht als Bestandteil der normalen
Dokumentdarstellung angezeigt.

---

# Detailprüfung: `meta`

## WHATWG-Zuordnung

`meta` ist in §4.2.5 definiert.

## Semantik

`meta` repräsentiert Metadaten, die nicht durch:

- `title`
- `base`
- `link`
- `style`
- `script`

ausgedrückt werden können.

`meta` kann unter anderem darstellen:

- Dokument-Metadaten
- Pragma Directives
- Character Encoding Declarations

## Content Categories

`meta` ist:

- Metadata Content

Wenn `itemprop` vorhanden ist, zusätzlich:

- Flow Content
- Phrasing Content

## Context

Der Kontext hängt vom verwendeten Attribut ab.

### `charset`

Wenn `charset` vorhanden ist:

- innerhalb von `head`

### `http-equiv`

Wenn `http-equiv` vorhanden ist und im Encoding Declaration State steht:

- innerhalb von `head`

Wenn `http-equiv` vorhanden ist, aber nicht im Encoding Declaration
State:

- innerhalb von `head`
- oder innerhalb eines `noscript`, das Kind von `head` ist

### `name`

Wenn `name` vorhanden ist:

- wo Metadata Content erwartet wird

### `itemprop`

Wenn `itemprop` vorhanden ist:

- wo Metadata Content erwartet wird
- wo Phrasing Content erwartet wird

## Content Model

`meta` besitzt:

**Nothing**

## Tag Omission

Das End-Tag ist nicht erforderlich.

`meta` ist ein Void Element.

---

# `meta` – Attributkombinationen

Genau eines der folgenden Attribute muss angegeben werden:

- `name`
- `http-equiv`
- `charset`
- `itemprop`

Wenn eines der folgenden Attribute verwendet wird:

- `name`
- `http-equiv`
- `itemprop`

muss zusätzlich `content` angegeben werden.

Wenn `charset` verwendet wird, muss `content` weggelassen werden.

---

# `meta` – `charset`

`charset` definiert eine Character Encoding Declaration.

Wenn vorhanden, muss der Wert ASCII-case-insensitive genau:

```text
utf-8
```

entsprechen.

Mehr als ein `meta`-Element mit `charset` ist pro Dokument nicht erlaubt.

## XML

`charset` hat in XML-Dokumenten keine Wirkung.

Es ist dort dennoch zulässig, um Migration zwischen HTML und XML zu
erleichtern.

---

# `meta` – `content`

`content` enthält den Wert:

- der Dokument-Metadaten oder
- der Pragma Directive.

Welche Syntax zulässig ist, hängt vom konkreten `name`- oder
`http-equiv`-Kontext ab.

Bei `name` bildet `name` zusammen mit `content` ein
Metadata Name-Value-Paar.

---

# `meta` – `media`

`media` bestimmt grundsätzlich, auf welches Medium die Metadaten
angewendet werden.

Der Wert muss eine gültige Media Query List sein.

Ausnahme:

Für den `name`-Wert:

```text
theme-color
```

besitzt `media` ein eigenes normatives Processing Model.

Für andere standardisierte Metadata Names hat `media` keine Wirkung auf
das Processing Model und darf von Autoren nicht verwendet werden.

---

# Standard Metadata Names

WHATWG definiert aktuell unter §4.2.5.1 mehrere Standardwerte für
`meta[name]`.

Die Namen werden ASCII-case-insensitive verglichen.

## `application-name`

Bezeichnet den Namen einer Web Application.

Der Wert muss ein kurzer freier String sein.

Wenn die Seite keine Web Application repräsentiert, darf dieser Name nicht
verwendet werden.

Übersetzungen können über unterschiedliche `lang`-Werte bereitgestellt
werden.

Pro Sprache darf es nicht mehr als einen entsprechenden
`application-name` geben.

User Agents können den Application Name für UI-Zwecke bevorzugen.

## `author`

Der Wert muss den Namen eines Autors der Seite enthalten.

## `description`

Der Wert muss eine freie Zeichenfolge sein, die die Seite beschreibt.

Die Beschreibung soll insbesondere für Verzeichnisse von Seiten,
beispielsweise Suchsysteme, geeignet sein.

Pro Dokument darf nicht mehr als ein `description`-Element vorhanden sein.

## `generator`

Bezeichnet ein Softwarepaket, das zur Generierung des Dokuments
verwendet wurde.

Es darf nicht für Seiten verwendet werden, deren Markup nicht durch
Software generiert wurde.

## `keywords`

Der Wert ist eine Menge von durch Kommas getrennten Tokens.

User Agents können diese Informationen beispielsweise für interne
Suchfunktionen verwenden.

WHATWG weist darauf hin, dass Suchmaschinen diese Angaben aufgrund
historischen Missbrauchs nicht zuverlässig berücksichtigen sollten.

## `referrer`

Der Wert muss eine Referrer Policy darstellen.

Damit wird die Default Referrer Policy des Dokuments beeinflusst.

Historische Werte werden von WHATWG auf moderne Referrer Policies
abgebildet, darunter:

| Legacy-Wert | Referrer Policy |
|---|---|
| `never` | `no-referrer` |
| `default` | Default Referrer Policy |
| `always` | `unsafe-url` |
| `origin-when-crossorigin` | `origin-when-cross-origin` |

Die Verarbeitung von `referrer` besitzt besondere historische Regeln:

- Entfernen des Elements hat nicht dieselbe Wirkung wie bei anderen
  Metadata Names.
- Tree Order wird nicht in derselben Weise verwendet.
- Das zuletzt eingefügte bzw. zuletzt geänderte passende `meta`-Element
  hat die Wirkung.

## `theme-color`

`theme-color` definiert eine vorgeschlagene Farbe, die User Agents zur
Anpassung der Darstellung oder umgebender UI verwenden können.

Der Wert muss der CSS-`<color>`-Syntax entsprechen.

`media` darf hierbei verwendet werden.

Innerhalb eines Dokuments muss der `media`-Wert unter den
`theme-color`-Elementen eindeutig sein.

User Agents suchen passende `theme-color`-Elemente in Tree Order.

Wenn ein Element:

- eingefügt,
- entfernt,
- hinsichtlich `name`, `content` oder `media` verändert

wird oder sich die Umgebung bezüglich `media` ändert, muss der User Agent
die Bestimmung des Theme Colors erneut ausführen.

## `color-scheme`

`color-scheme` gibt an, welche Farbschemata die Seite unterstützt.

Der Wert muss der CSS-`color-scheme`-Property-Syntax entsprechen.

Pro Dokument darf nicht mehr als ein entsprechendes
`meta[name=color-scheme]` vorhanden sein.

Mehrere Werte können als Fallback angegeben werden.

Die Auswertung erfolgt in Tree Order.

---

# Weitere Metadata Names

§4.2.5.2 erlaubt Erweiterungen des Sets standardisierter Metadata Names.

Eine Registrierung ist nicht zwingend erforderlich.

WHATWG beschreibt jedoch Regeln und Empfehlungen.

## Keine neuen Namen für URLs

Wenn:

- der Name selbst eine URL ist oder
- der `content`-Wert eine URL ist,

soll stattdessen eine Erweiterung der Link Types verwendet werden.

## Keine neuen Namen mit eigenem UA-Processing

Wenn ein Metadata Name eigene User-Agent-Processing-Anforderungen
benötigt, sollte er standardisiert werden.

## WHATWG MetaExtensions

Für neue Namen wird die Konsultation der WHATWG Wiki MetaExtensions
empfohlen.

Eine Erweiterung soll insbesondere dokumentieren:

- Keyword
- Brief Description
- Specification
- Synonyms
- Status

## Statuswerte von Metadata Extensions

WHATWG beschreibt:

### Proposed

Noch keine breite Peer Review/Anerkennung.

### Ratified

Breit geprüft und mit eindeutig definierter Verarbeitung spezifiziert.

### Discontinued

Breit geprüft und als problematisch eingestuft.

Neue Inhalte sollen einen solchen Namen vermeiden.

Diese Statuswerte gehören zur Metadata-Extension-Ebene und sind nicht
mit dem generellen WHATWG-Status des `meta`-Elements gleichzusetzen.

---

# Pragma Directives

## Grundprinzip

Wenn `http-equiv` auf einem `meta`-Element angegeben wird, handelt es sich
um eine Pragma Directive.

Der Name `http-equiv` darf nicht so verstanden werden, dass damit
automatisch ein HTTP-Header simuliert wird.

WHATWG weist ausdrücklich darauf hin, dass Pragma Directives und HTTP
Headers weitgehend unterschiedliche Konzepte sind.

---

# `http-equiv` – standardisierte Zustände

Die aktuelle WHATWG-Tabelle umfasst insbesondere:

| Keyword | Konformität | State | Bedeutung |
|---|---|---|---|
| `content-language` | Nein | Content language | Setzt Pragma-set Default Language |
| `content-type` | Ja | Encoding declaration | Alternative Character Encoding Declaration |
| `default-style` | Ja | Default style | Setzt Default CSS Style Sheet Set |
| `refresh` | Ja | Refresh | Timed Redirect |
| `x-ua-compatible` | historisches Processing | X-UA-Compatible | Historische IE-Kompatibilitätssteuerung |
| `content-security-policy` | Ja | Content security policy | Setzt CSP für das Dokument |

Nicht standardisierte `http-equiv`-Werte erzeugen kein eigenes normatives
Processing Model.

---

# `http-equiv="content-language"`

Dieser Zustand ist:

**non-conforming**

Autoren sollen stattdessen:

```html
<html lang="...">
```

verwenden.

Die Pragma Directive kann einen Pragma-set Default Language State
bestimmen.

Sie ersetzt jedoch nicht die moderne Sprachangabe über `lang`.

---

# `http-equiv="content-type"`

Dies ist die Encoding Declaration State.

Sie stellt eine alternative Form der Character Encoding Declaration dar.

Der `content`-Wert muss ASCII-case-insensitive der Form entsprechen:

```text
text/html;
```

optional gefolgt von ASCII whitespace und:

```text
charset=utf-8
```

Ein Dokument darf nicht gleichzeitig enthalten:

- `meta[http-equiv]` im Encoding Declaration State
- `meta[charset]`

Die Encoding Declaration State ist für HTML zulässig.

Sie darf nicht für XML-Dokumente verwendet werden.

---

# `http-equiv="default-style"`

Dieser Zustand setzt den Namen des Default CSS Style Sheet Sets.

Der `content`-Wert muss den Namen des gewünschten Style Sheet Sets
enthalten.

---

# `http-equiv="refresh"`

`refresh` implementiert eine deklarative zeitgesteuerte Navigation.

Der `content`-Wert muss entweder:

```text
<non-negative integer>
```

oder:

```text
<non-negative integer>; URL=<valid URL>
```

entsprechen.

Der Integer bestimmt die Verzögerung in Sekunden.

Ohne URL erfolgt ein Reload.

Mit URL erfolgt eine Navigation zur angegebenen URL.

Beispiel:

```html
<meta http-equiv="refresh" content="300">
```

oder:

```html
<meta http-equiv="refresh" content="20; URL=page4.html">
```

Die Spezifikation enthält zusätzliche Sicherheits- und Parsing-Regeln,
unter anderem darf die URL kein `javascript:`-Schema verwenden.

---

# `http-equiv="x-ua-compatible"`

Dieser Zustand ist historisch mit Internet Explorer verbunden.

WHATWG definiert die erforderliche Form:

```text
IE=edge
```

User Agents sind verpflichtet, diese Pragma Directive zu ignorieren.

Sie ist daher kein modernes allgemeines Feature zur Browsersteuerung.

---

# `http-equiv="content-security-policy"`

Damit kann eine Content Security Policy für das Dokument über ein
`meta`-Element angewendet werden.

Das Element muss Kind von `head` sein.

`content` darf nicht fehlen oder leer sein.

Die Policy wird als CSP serialisiert und anschließend angewendet.

Bestimmte CSP-Direktiven werden aus diesem Meta-Kontext entfernt:

- `report-uri`
- `frame-ancestors`
- `sandbox`

Es darf nicht mehr als ein `meta`-Element mit demselben
`http-equiv`-State gleichzeitig im Dokument vorhanden sein.

Wichtig:

Eine spät eingefügte CSP kann Ressourcen nicht zuverlässig rückwirkend
blockieren, die bereits geladen wurden.

---

# Character Encoding

§4.2.5.4 enthält ein eigenes Processing Model für
Character Encoding Declarations.

## UTF-8

Die aktuelle WHATWG-/Encoding-Spezifikation verlangt UTF-8.

Eine Character Encoding Declaration muss deshalb die Encoding Label:

```text
utf-8
```

verwenden.

## Tatsächliche Kodierung

Unabhängig davon, ob eine Declaration vorhanden ist, muss die tatsächliche
Zeichenkodierung des Dokuments UTF-8 sein.

## Position

Die Character Encoding Declaration muss innerhalb der ersten:

**1024 Bytes**

des Dokuments vollständig serialisiert sein.

## Keine Character References

Die Declaration darf nicht über Character References oder Character
Escapes serialisiert werden.

Beispiel:

```html
<meta charset="utf-8">
```

## Nur eine Declaration

Es darf pro Dokument nur eine Meta-basierte Character Encoding
Declaration geben.

---

# `iframe srcdoc` und Character Encoding

Ein `iframe`-`srcdoc`-Dokument darf keine Character Encoding Declaration
enthalten.

Der Inhalt ist bereits als Teil des umgebenden Dokuments dekodiert.

---

# `style`

## WHATWG-Zuordnung

`style` ist in §4.2.6 definiert.

## Semantik

`style` ermöglicht das Einbetten von CSS Stylesheets in ein Dokument.

Das Element ist ein Input des Styling Processing Models.

`style` repräsentiert selbst keinen Benutzerinhalt.

## Content Categories

`style` ist:

**Metadata Content**

## Context

`style` darf verwendet werden:

- wo Metadata Content erwartet wird,
- in einem `noscript`, das Kind eines `head` ist.

## Content Model

Das Content Model ist:

**Text, der ein konformes Stylesheet bildet.**

## Tag Omission

Weder Start- noch End-Tag sind auslassbar.

## Content Attributes

Neben Global Attributes:

### `media`

Gibt an, für welche Medien das Stylesheet gilt.

Der Wert muss eine gültige Media Query List sein.

Default:

```text
all
```

### `blocking`

Blocking Attribute.

Es bestimmt, ob das Element potentiell render-blocking ist.

### `title`

`title` besitzt beim `style`-Element spezielle CSSOM-Semantik.

Es definiert den Namen eines CSS Style Sheet Sets.

Das Verhalten unterscheidet sich vom allgemeinen Global-`title`-Modell.

Ein `style`-Element ohne eigenen `title` erbt keinen `title`-Wert vom
Vorfahren.

## DOM Interface

```webidl
[Exposed=Window]
interface HTMLStyleElement : HTMLElement {
  [HTMLConstructor] constructor();

  attribute boolean disabled;
  [CEReactions, Reflect] attribute DOMString media;
  [SameObject, PutForwards=value, Reflect] readonly attribute DOMTokenList blocking;

  // also has obsolete members
};

HTMLStyleElement includes LinkStyle;
```

## Sanitization

Sanitization:

**Uncategorized**

---

# `style` – `media`

`media` muss eine gültige Media Query List enthalten.

Das Stylesheet wird angewendet, wenn:

- die Media Query auf die aktuelle Umgebung zutrifft und
- die übrigen Bedingungen erfüllt sind.

CSS-interne Einschränkungen, beispielsweise über `@media`, bleiben davon
unberührt.

---

# `style` – `disabled`

`HTMLStyleElement.disabled` bezieht sich auf das zugehörige CSS Style
Sheet.

Wenn kein Associated CSS Style Sheet vorhanden ist, liefert der Getter
`false`.

Ist das Stylesheet disabled, liefert er `true`.

Der Setter verändert den Disabled Flag des zugehörigen CSS Stylesheets.

Die Zuweisung hat daher erst Bedeutung, wenn das `style`-Element ein
Associated CSS Style Sheet besitzt.

---

# `style` – `title`

Bei `style` definiert `title` den CSS Style Sheet Set Name.

Das Attribut wird nur berücksichtigt, wenn das Element im Document Tree
steht.

Ein `style`-Element ohne `title` besitzt keinen Style Sheet Set Name.

Der `title`-Wert eines Vorfahren wird nicht übernommen.

---

# `style` – Render Blocking

Ein `style`-Element kann potentiell render-blocking sein.

Ein durch den Parser erzeugtes `style`-Element ist implizit potentiell
render-blocking.

Das `blocking`-Attribut ist zusätzlich ein explizites Blocking Attribute.

Die genaue Auswirkung hängt vom Styling- und Rendering-Processing Model ab.

---

# `style` – Update a style block

WHATWG definiert einen eigenen Algorithmus:

**update a style block**

Dieser wird unter anderem ausgelöst, wenn:

- das Element vom Stack of Open Elements entfernt wird,
- es connected oder disconnected wird,
- sich seine Children ändern, wenn es nicht auf dem Parser-Stack liegt.

Der Algorithmus:

1. entfernt ein vorhandenes Associated CSS Style Sheet,
2. prüft, ob das Element connected ist,
3. prüft gegebenenfalls `type`,
4. prüft CSP,
5. erzeugt ein CSS Style Sheet,
6. verbindet es mit dem Element,
7. berücksichtigt Script-Blocking Style Sheets,
8. berücksichtigt Render Blocking.

---

# `style` – `type`

Für die Styling-Verarbeitung wird `type` berücksichtigt, falls vorhanden.

Zulässig für die Verarbeitung ist:

- leerer Wert
- ASCII-case-insensitive `text/css`

Ein Wert wie:

```text
text/css; charset=utf-8
```

führt gemäß dem aktuellen Processing Model nicht zur Erstellung des
Stylesheets.

`type` ist hier kein in der Elementreferenz aufgeführtes Content Attribute
von `style`, spielt aber im Processing Model eine Rolle.

---

# Styling und Scripting

§4.2.7 behandelt die Interaktion zwischen Styling und Scripting.

Dieser Abschnitt ist ein eigenes Processing-/Timing-Konzept und kein
zusätzliches HTML-Element.

Von besonderer Bedeutung sind:

- Script-Blocking Style Sheets
- Render Blocking
- Parser
- Script-Ausführung
- Stylesheet-Verarbeitung
- Dokumentzustand

Ein Stylesheet kann Einfluss darauf haben, wann Scripts ausgeführt
werden können.

Die genaue Beziehung wird über das Styling- und Script-Processing Model
definiert.

---

# Script-Blocking Style Sheets

Ein Stylesheet kann Teil des Script-Blocking Style Sheet Sets eines
Dokuments werden.

Dies beeinflusst die Bedingungen, unter denen Scripts ausgeführt werden.

Damit besteht eine normative Beziehung zwischen:

```text
style
```

und:

```text
script
```

Diese Beziehung darf nicht als einfache DOM-Kindbeziehung verstanden
werden.

Sie gehört zur Verarbeitungslogik des Browsers.

---

# Processing Models als separate Feature-Ebene

§4.2 enthält neben sechs HTML-Elementen zahlreiche eigenständige
Processing Models.

Diese werden nicht in das HTML-Elementinventar aufgenommen.

Dazu gehören insbesondere:

## Head Processing

- Ermittlung der Dokumentmetadaten
- Titelermittlung
- Base URL
- Default Target

## Link Processing

- Link Creation
- External Resource Links
- Hyperlinks
- Link Type Processing
- Media Matching
- MIME Type Hinting
- Fetch
- SRI
- Referrer Policy
- Preload
- Modulepreload
- Image Source Sets
- HTTP Link Headers
- Early Hints

## Meta Processing

- Metadata Name/Value Pairs
- Standard Metadata Names
- Meta Extensions
- Pragma Directives
- Refresh
- CSP
- Character Encoding Declarations

## Style Processing

- CSS Style Sheet Creation
- Style Sheet Sets
- Disabled Stylesheets
- Render Blocking
- Script Blocking
- Style Block Updates

---

# Content Categories und Kontexte

Die Kategorien dieses Bereichs müssen sauber getrennt betrachtet werden.

| Element | Categories |
|---|---|
| `head` | keine |
| `title` | Metadata |
| `base` | Metadata |
| `link` | Metadata; unter Bedingungen Flow/Phrasing |
| `meta` | Metadata; mit `itemprop` zusätzlich Flow/Phrasing |
| `style` | Metadata |

## Wichtige Kontextabhängigkeit

Insbesondere `link` und `meta` sind nicht mit einem einzigen statischen
Context vollständig beschrieben.

`link` kann abhängig von `rel` bzw. `itemprop` auch im `body` auftreten.

`meta` kann abhängig von `name`, `http-equiv`, `charset` und `itemprop`
unterschiedliche Kontexte besitzen.

---

# Accessibility

WHATWG weist für alle sechs Elemente Accessibility Considerations aus.

## `head`

Keine direkte Benutzerinhaltsrepräsentation.

Accessibility-Relevanz entsteht primär durch die enthaltenen Metadaten.

## `title`

Der Dokumenttitel ist für Benutzeroberflächen und die Identifikation des
Dokuments wichtig.

## `base`

Kein dargestellter Inhalt.

## `link`

Hyperlinks über `link` werden normalerweise nicht als normale
Dokumentbestandteile dargestellt.

Interactive User Agents können jedoch eigene UI zur Verfolgung solcher
Links anbieten.

## `meta`

Kein dargestellter Inhalt.

Einige Metadata Names beeinflussen jedoch Dokument- und UI-Verhalten.

## `style`

Das Element repräsentiert keinen Benutzerinhalt.

Seine Accessibility-Auswirkungen ergeben sich indirekt aus dem angewendeten
Styling.

Die detaillierte Plattform-/ARIA-Auswertung bleibt eine separate
Accessibility-Ebene.

---

# Sanitization

Die WHATWG-Sanitization-Klassifikation lautet:

| Element | Sanitization |
|---|---|
| `head` | Default |
| `title` | Default |
| `base` | Unsafe |
| `link` | Uncategorized |
| `meta` | Uncategorized |
| `style` | Uncategorized |

## Besonders relevant: `base`

`base` ist **Unsafe**.

Der Grund für die getrennte Behandlung ist insbesondere seine Wirkung auf:

- URL-Auflösung
- Navigation
- Form Submission Targets

## Keine Gleichsetzung mit Security

Sanitization-Status ist nicht dasselbe wie:

- CSP
- Trusted Types
- Browser Security Policy
- URL Validation
- XSS-Schutz

Diese Mechanismen gehören zu unterschiedlichen Ebenen.

---

# DOM Interfaces

| Element | DOM Interface |
|---|---|
| `head` | `HTMLHeadElement` |
| `title` | `HTMLTitleElement` |
| `base` | `HTMLBaseElement` |
| `link` | `HTMLLinkElement` |
| `meta` | `HTMLMetaElement` |
| `style` | `HTMLStyleElement` |

## `HTMLHeadElement`

```webidl
interface HTMLHeadElement : HTMLElement
```

## `HTMLTitleElement`

```webidl
interface HTMLTitleElement : HTMLElement {
  attribute DOMString text;
}
```

## `HTMLBaseElement`

```webidl
interface HTMLBaseElement : HTMLElement {
  attribute USVString href;
  attribute DOMString target;
}
```

## `HTMLLinkElement`

Das Interface exponiert unter anderem:

```text
href
crossOrigin
rel
as
relList
media
integrity
hreflang
type
sizes
imageSrcset
imageSizes
referrerPolicy
blocking
disabled
fetchPriority
```

## `HTMLMetaElement`

Das Interface exponiert:

```text
name
httpEquiv
content
media
```

## `HTMLStyleElement`

Das Interface exponiert:

```text
disabled
media
blocking
```

und enthält das `LinkStyle`-Interface.

---

# Normative Sonderregeln

## `head`

- erstes Element in `html`
- Content Model abhängig von Titelverfügbarkeit
- maximal ein `title`
- maximal ein `base`
- Tag-Omission möglich

## `title`

- höchstens ein `title` pro Dokument
- Text muss nicht-inter-element-whitespace sein
- Titel soll kontextunabhängig identifizierbar sein

## `base`

- maximal ein `base` pro Dokument
- `href`, `target` oder beide erforderlich
- `href` beeinflusst Document Base URL
- `target` beeinflusst Default Navigable
- Position ist für die Wirkung relevant
- nur das erste passende `base` wird berücksichtigt
- Sanitization: Unsafe

## `link`

- mindestens `href` oder `imagesrcset`
- `rel`/`itemprop`-Exklusivität
- Link Types bestimmen das Processing Model
- ein Element kann mehrere Links erzeugen
- Links werden pro Link verarbeitet
- `type` ist nur ein Hint
- tatsächlicher Ressourcentyp bleibt maßgeblich
- `media` ist bei externen Ressourcen preskriptiv
- SRI, CORS, Referrer Policy und Fetch Priority sind eigene
  Verarbeitungsebenen

## `meta`

- genau eines von `name`, `http-equiv`, `charset`, `itemprop`
- `content` ist bei `name`, `http-equiv` und `itemprop` erforderlich
- `charset` muss `utf-8` sein
- maximal eine Charset Declaration
- `http-equiv`-Zustände besitzen eigene Processing Models
- `content-language` ist nicht konform
- `refresh` ist eine deklarative Navigation
- CSP kann über `meta` angewendet werden
- Character Encoding Declaration muss innerhalb der ersten 1024 Bytes
  vollständig serialisiert sein

## `style`

- Inhalt muss ein konformes Stylesheet bilden
- `media` ist eine gültige Media Query List
- `title` besitzt Style-Sheet-Set-Semantik
- `disabled` wirkt auf das Associated CSS Style Sheet
- Parser-erzeugte Style Blocks können render-blocking sein
- `type` wird im Processing Model berücksichtigt
- CSP kann die Verarbeitung blockieren
- Style Sheet Processing ist mit Script Blocking verknüpft

---

# Querverweise

## §4.1 The document element

`html` enthält:

```text
head
body
```

`head` ist dabei der erste Teil des `html`-Content-Models.

## §4.3 Sections

`body` bildet den zweiten Teil des Document Element Content Models.

## §4.6 Links

Die durch `link` erzeugten Beziehungen stehen mit dem allgemeinen
Hyperlink-/Link-Type-Modell in Verbindung.

## §4.12 Scripting

Besonders relevant:

- `script`
- Module Scripts
- Script Blocking
- Styling/Scripting Interaction

## DOM Standard

Relevant für:

- `Document`
- `document.title`
- `document.documentElement`
- Child Text Content
- `Node`
- `Element`
- `DocumentFragment`

## Fetch Standard

Relevant für:

- `link`-Fetches
- CORS
- Referrer Policy
- Fetch Priority
- Requests
- Responses

## URL Standard

Relevant für:

- Document Base URL
- URL Parsing
- relative URL Resolution

## Encoding Standard

Relevant für:

- UTF-8
- Character Encoding Declaration
- Encoding Labels

## CSSOM

Relevant für:

- CSS Style Sheet Sets
- Associated CSS Style Sheet
- Disabled Flag
- Style Sheet Processing

## Content Security Policy

Relevant für:

- `meta[http-equiv=content-security-policy]`
- Inline Style Blocking
- Policy Enforcement

## Subresource Integrity

Relevant für:

- `link[integrity]`

---

# Abgrenzung: Elemente vs. Feature-Familien

Für die ZE-WebLab-Elementinventarliste zählen in §4.2 ausschließlich:

```text
head
title
base
link
meta
style
```

Nicht als zusätzliche HTML-Elemente zählen:

```text
application-name
author
description
generator
keywords
referrer
theme-color
color-scheme
```

Diese sind Metadata Names.

Ebenso keine zusätzlichen Elemente:

```text
content-language
content-type
default-style
refresh
x-ua-compatible
content-security-policy
```

Diese sind `http-equiv`-States.

Ebenfalls keine zusätzlichen Elemente:

```text
preload
modulepreload
stylesheet
icon
manifest
next
alternate
dns-prefetch
preconnect
prefetch
search
pingback
expect
```

Diese sind Link Types.

---

# Status / V1

## Elementstatus

Alle sechs Elemente sind im aktuellen WHATWG HTML Living Standard
definiert:

- `head`
- `title`
- `base`
- `link`
- `meta`
- `style`

## Konformitätsstatus

Die bloße Existenz der Elementdefinition bedeutet nicht, dass jede
Verwendung konform ist.

Die Konformität ist insbesondere abhängig von:

- Context
- Content Model
- Attributkombinationen
- Link Types
- Metadata Names
- `http-equiv`-States
- Dokumentstruktur
- Processing Model

## `head`

Konformität hängt insbesondere von:

- Position
- Anzahl von `title`
- Anzahl von `base`
- Metadata Content

ab.

## `title`

Konformität hängt insbesondere von:

- Position in `head`
- maximal einem Element
- zulässigem Textinhalt

ab.

## `base`

Konformität hängt insbesondere von:

- maximal einem Element
- `href`/`target`
- Position
- gültigen URLs bzw. Target Names

ab.

## `link`

Konformität hängt insbesondere von:

- `href`/`imagesrcset`
- `rel`/`itemprop`
- Link Type
- Attributkombinationen
- Kontext

ab.

## `meta`

Konformität hängt insbesondere von:

- genau einem Klassifizierungsattribut
- erforderlichem `content`
- `charset`
- `http-equiv`-State
- Metadata Name
- Kontext

ab.

## `style`

Konformität hängt insbesondere von:

- Kontext
- CSS-Inhalt
- `media`
- `blocking`
- `title`
- Processing Model

ab.

---

# Browser-Support

Browser-Kompatibilität wird nicht als WHATWG-Status übernommen.

Insbesondere werden die im WHATWG-Dokument eingeblendeten MDN-
Kompatibilitätsinformationen nicht als V1-Status verwendet.

Für ZE-WebLab gilt:

```text
WHATWG-Definition
        ≠
Konformität
        ≠
Browser-Support
```

Eine spätere Browser-Kompatibilitätsrecherche muss deshalb separat
durchgeführt werden.

---

# V1-Referenzmatrix

| Element | WHATWG | Content Model | Tag Omission | Sanitization | DOM |
|---|---|---|---|---|---|
| `head` | definiert | Metadata Content mit `title`/`base`-Regeln | beide Tags unter Bedingungen | Default | `HTMLHeadElement` |
| `title` | definiert | Text ohne inter-element whitespace | keine | Default | `HTMLTitleElement` |
| `base` | definiert | Nothing | kein End-Tag | Unsafe | `HTMLBaseElement` |
| `link` | definiert | Nothing | kein End-Tag | Uncategorized | `HTMLLinkElement` |
| `meta` | definiert | Nothing | kein End-Tag | Uncategorized | `HTMLMetaElement` |
| `style` | definiert | konformes CSS Stylesheet als Text | keine | Uncategorized | `HTMLStyleElement` |

---

# Offene Punkte

Für die Elementinventarisierung von §4.2 bestehen keine offenen Punkte.

Folgende Themen bleiben bewusst als separate Folgeebenen bestehen:

1. Vollständige globale Attributreferenz.
2. Vollständige Link-Type-Matrix über §4.6.
3. Vollständige Browser-Kompatibilitätsmatrix.
4. Detaillierte Accessibility-Zuordnungen.
5. Vollständige CSSOM-Dokumentation.
6. Vollständige Fetch-/CORS-/Referrer-Policy-Dokumentation.
7. Vollständige CSP-Dokumentation.
8. Vollständige Encoding-Spezifikation.
9. Vollständige MetaExtensions-Wiki-Auswertung einschließlich externer
   Erweiterungsnamen.
10. Vollständige JavaScript-/Scripting-Interaktion aus §4.12.

Diese Punkte stellen keine fehlenden Elementdefinitionen in §4.2 dar.

---

# Prüfstatus

| Prüfbereich | Status |
|---|---|
| WHATWG §4.2 Struktur geprüft | abgeschlossen |
| Alle HTML-Elemente geprüft | abgeschlossen |
| `head` geprüft | abgeschlossen |
| `title` geprüft | abgeschlossen |
| `base` geprüft | abgeschlossen |
| `link` geprüft | abgeschlossen |
| `meta` geprüft | abgeschlossen |
| `style` geprüft | abgeschlossen |
| Content Categories geprüft | abgeschlossen |
| Contexts geprüft | abgeschlossen |
| Content Models geprüft | abgeschlossen |
| Tag Omission geprüft | abgeschlossen |
| Content Attributes geprüft | abgeschlossen |
| Accessibility-Verweise geprüft | abgeschlossen |
| Sanitization geprüft | abgeschlossen |
| DOM Interfaces geprüft | abgeschlossen |
| Link Processing Models geprüft | abgeschlossen |
| Link Header Processing geprüft | abgeschlossen |
| Early Hints geprüft | abgeschlossen |
| Metadata Names geprüft | abgeschlossen |
| Meta Extensions geprüft | abgeschlossen |
| Pragma Directives geprüft | abgeschlossen |
| Character Encoding geprüft | abgeschlossen |
| Styling Processing geprüft | abgeschlossen |
| Styling/Scripting Interaction geprüft | abgeschlossen |
| Element-/Feature-Ebenen getrennt | abgeschlossen |
| Browser-Support separat behandelt | abgeschlossen |
| Offene Punkte dokumentiert | abgeschlossen |

---

# Quellen / Referenzen

## Primärquelle

WHATWG HTML Living Standard:

**§4.2 Document metadata**

Relevante Unterabschnitte:

- §4.2.1 The `head` element
- §4.2.2 The `title` element
- §4.2.3 The `base` element
- §4.2.4 The `link` element
- §4.2.4.1 Processing the `media` attribute
- §4.2.4.2 Processing the `type` attribute
- §4.2.4.3 Fetching and processing a resource from a `link` element
- §4.2.4.4 Processing `Link` headers
- §4.2.4.5 Early hints
- §4.2.4.6 Providing users with a means to follow hyperlinks created using
  the `link` element
- §4.2.5 The `meta` element
- §4.2.5.1 Standard metadata names
- §4.2.5.2 Other metadata names
- §4.2.5.3 Pragma directives
- §4.2.5.4 Specifying the document's character encoding
- §4.2.6 The `style` element
- §4.2.7 Interactions of styling and scripting

## Relevante verknüpfte Standards

WHATWG §4.2 verweist unter anderem auf:

- DOM Standard
- URL Standard
- Fetch Standard
- Encoding Standard
- CSSOM
- Referrer Policy
- Subresource Integrity
- Content Security Policy
- MIME Sniffing
- CSS Specifications

Diese Standards werden in dieser Datei nur für die jeweils von §4.2
referenzierten Processing- und API-Beziehungen berücksichtigt.

---

# Zusammenfassung der fachlichen Abgrenzung

§4.2 „Document metadata“ definiert sechs HTML-Elemente:

1. `head`
2. `title`
3. `base`
4. `link`
5. `meta`
6. `style`

Der Abschnitt ist jedoch wesentlich größer als diese sechs
Elementdefinitionen.

Für die ZE-WebLab-Referenz müssen insbesondere folgende Ebenen getrennt
bleiben:

## HTML-Elemente

```text
head
title
base
link
meta
style
```

## Metadata Names

```text
application-name
author
description
generator
keywords
referrer
theme-color
color-scheme
```

## `http-equiv`-States

```text
content-language
content-type
default-style
refresh
x-ua-compatible
content-security-policy
```

## Link Types

```text
alternate
dns-prefetch
expect
icon
manifest
modulepreload
next
pingback
preconnect
prefetch
preload
search
stylesheet
```

## Weitere Konzepte

```text
Document Base URL
Default Navigable
Link Processing Options
External Resource Links
Hyperlinks
Link Headers
Early Hints
Character Encoding Declaration
CSS Style Sheet Sets
Script-Blocking Style Sheets
Render Blocking
Meta Extensions
```

Diese Konzepte sind fachlich Bestandteil der Recherche zu §4.2, aber keine
zusätzlichen HTML-Elemente.

Damit ist der WHATWG-Bereich **§4.2 Document metadata** auf der
Element-/Attribut-/Processing-/Querverweis-Ebene vollständig für die
ZE-WebLab-Referenz erfasst.