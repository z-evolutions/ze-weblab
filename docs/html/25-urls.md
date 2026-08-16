# ZE-WebLab – HTML-Referenz: URLs

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab  
**Datei:** `docs/html/25-urls.md`  
**Rechercheebene:** Zweite Rechercheebene – übergreifende HTML-Konzepte  
**Feature-Typ:** URL-Systematik / Infrastruktur / Processing Concept  
**WHATWG-Bereich:** §2.4 URLs  
**Geprüfter WHATWG-Stand:** HTML Living Standard, 11. August 2026  
**Status:** vollständig recherchiert für den in diesem Dokument abgegrenzten WHATWG-Bereich §2.4 „URLs“

Diese Datei dokumentiert die übergreifende URL-Systematik des HTML Living
Standard.

Die Datei behandelt insbesondere:

- URL-Terminologie innerhalb von HTML
- gültige URL-Zeichenfolgen
- URL-Parsing im HTML-Kontext
- Encoding beim URL-Parsing
- Basis-URLs
- Document Base URL
- Fallback Base URL
- `base`-Element als Quelle der Document Base URL
- Auswirkungen von Änderungen der Base URL
- Beziehungen zu DOM- und URL-Konzepten
- Querverweise zu Fetching und Navigation

Die Datei behandelt **keine vollständige allgemeine URL-Spezifikation**.
Die eigentliche URL-Syntax, der URL Parser und das URL Record Modell sind
im WHATWG URL Standard definiert.

Ebenso behandelt diese Datei nicht die vollständige
Ressourcen-Fetch-Verarbeitung aus WHATWG §2.5. Diese gehört fachlich in
eine eigene Feature-Familie.

---

## Quellenabgrenzung

### WHATWG

Die normative Primärquelle beantwortet:

> Welche URL-Konzepte definiert HTML selbst, welche URL-Begriffe verwendet
> HTML und wie werden URLs innerhalb des HTML-Verarbeitungsmodells
> aufgelöst und verarbeitet?

### ZE-WebLab

Das Repository beantwortet:

> Welche dieser übergreifenden URL-Konzepte wurden in der bestehenden
> Elementreferenz bereits elementbezogen dokumentiert?

Diese beiden Ebenen werden getrennt behandelt.

Eine Erwähnung von `href` in einer Elementdatei bedeutet daher nicht,
dass die gesamte URL-Systematik bereits als übergreifendes Konzept
dokumentiert wurde.

---

## Abgrenzung zu anderen Spezifikationen

Die HTML-Spezifikation verweist für die eigentliche URL-Syntax und
URL-Verarbeitung auf den WHATWG URL Standard.

Damit sind insbesondere folgende Konzepte nicht eigenständige HTML-URL-
Algorithmen:

- URL Record
- Scheme
- Username
- Password
- Host
- Port
- Path
- Query
- Fragment
- URL Parser im allgemeinen Sinn
- URL Serializer im allgemeinen Sinn

HTML definiert dagegen die für HTML relevanten Anwendungs- und
Verarbeitungsregeln, insbesondere:

- gültige URL-Werte im HTML-Kontext
- URL-Auflösung relativ zu einer Basis
- Document Base URL
- Fallback Base URL
- Verwendung der Document Base URL
- Encoding-abhängiges URL-Parsing im HTML-Kontext

---

# Einordnung

## URL als übergreifendes HTML-Konzept

URLs werden in HTML an zahlreichen Stellen verwendet.

Beispiele sind:

- `a[href]`
- `area[href]`
- `base[href]`
- `blockquote[cite]`
- `del[cite]`
- `ins[cite]`
- `img[src]`
- `iframe[src]`
- `script[src]`
- `link[href]`
- `form[action]`
- `object[data]`
- `video[poster]`
- `source[src]`
- `track[src]`

Die konkrete Semantik jedes einzelnen Attributs wird in der jeweiligen
Elementdefinition beschrieben.

Die allgemeine URL-Auflösung ist jedoch ein übergreifendes Infrastruktur-
Konzept.

---

## URL ist kein HTML-Element

Eine URL ist:

- kein HTML-Element,
- keine Content Category,
- kein Content Model,
- kein DOM Interface,
- kein Link Type,
- kein Custom Element.

Sie ist ein Datentyp bzw. ein Wert, der von zahlreichen HTML-Features
verwendet wird.

---

## URL ist nicht dasselbe wie Hyperlink

Ein Hyperlink ist ein HTML-Konzept, das unter anderem durch bestimmte
Elemente und Link Types entstehen kann.

Eine URL kann dagegen auch verwendet werden, ohne einen Hyperlink zu
erzeugen.

Beispiele:

- `img[src]`
- `script[src]`
- `form[action]`
- `iframe[src]`
- `base[href]`

Daher gilt:

**URL ≠ Hyperlink**

und:

**URL ≠ Link Type**

---

# WHATWG-Struktur

Der relevante Bereich des aktuellen HTML Living Standard ist:

## 2.4 URLs

### 2.4.1 Terminology

Behandelt die URL-Terminologie und die für HTML relevanten
Gültigkeitsbegriffe.

### 2.4.2 Parsing URLs

Behandelt URL-Parsing im HTML-Kontext einschließlich:

- Base URL
- Character Encoding
- URL Parser
- URL Serialization
- Encoding Parsing

### 2.4.3 Document base URLs

Behandelt:

- Document Base URL
- Fallback Base URL
- `base[href]`
- `about:blank`
- `about:srcdoc`
- Änderungen der Base URL
- Reaktionen auf Base-URL-Änderungen

---

# Inventar

| ID | Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| URL-001 | URL terminology | Normative Concept | §2.4.1 | teilweise über URL-Attribute verteilt | eigenständig |
| URL-002 | Valid non-empty URL | Value Definition | §2.4.1 | elementbezogen | eigenständig |
| URL-003 | Valid URL potentially surrounded by spaces | Value Definition | §2.4.1 | elementbezogen | eigenständig |
| URL-004 | Valid non-empty URL potentially surrounded by spaces | Value Definition | §2.4.1 | elementbezogen | eigenständig |
| URL-005 | HTML URL parsing | Processing Concept | §2.4.2 | teilweise | eigenständig |
| URL-006 | Encoding-parsing a URL | Processing Concept | §2.4.2 | nicht als allgemeines Konzept | eigenständig |
| URL-007 | URL serialization | Processing Concept | §2.4.2 | nicht als allgemeines Konzept | eigenständig |
| URL-008 | Document Base URL | Processing Concept | §2.4.3 | `base` elementbezogen in `02-document-metadata.md` | eigenständig |
| URL-009 | Fallback Base URL | Processing Concept | §2.4.3 | elementbezogen | eigenständig |
| URL-010 | Frozen Base URL | Processing Concept | §2.4.3 | teilweise über `base` | eigenständig |
| URL-011 | Base URL changes | Processing Model | §2.4.3 | nicht vollständig | eigenständig |
| URL-012 | `about:blank` URL matching | Normative Concept | §2.4.1 / §2.4.3 | elementbezogen bzw. nicht vollständig | eigenständig |
| URL-013 | `about:srcdoc` URL matching | Normative Concept | §2.4.1 / §2.4.3 | `iframe` elementbezogen | eigenständig |
| URL-014 | HTML ↔ WHATWG URL Standard | Integration Feature | §2.4 | implizit | eigenständig |

---

# Begriffsdefinitionen

## URL

Eine URL ist im HTML-Kontext eine URL im Sinne des WHATWG URL Standards.

HTML verwendet URLs als Werte zahlreicher Attribute und als Grundlage
für die Verarbeitung von Ressourcen, Navigationen und anderen
Webplattform-Funktionen.

Die eigentliche URL-Datenstruktur und Syntax wird nicht vollständig von
HTML neu definiert.

---

## Valid URL string

Die HTML-Spezifikation verwendet die Definition einer gültigen URL aus
dem WHATWG URL Standard.

Ein String ist im HTML-Kontext nur dann als URL-Wert gültig, wenn er die
entsprechenden Anforderungen des referenzierten URL-Modells erfüllt.

---

## Valid non-empty URL

Eine gültige nichtleere URL ist eine gültige URL-Zeichenfolge, die nicht
die leere Zeichenfolge ist.

Diese Unterscheidung ist für verschiedene HTML-Attribute relevant.

Beispielsweise verlangt `link[href]` eine gültige nichtleere URL.

---

## Valid URL potentially surrounded by spaces

Bei bestimmten HTML-Attributen darf eine gültige URL von ASCII-Whitespace
umgeben sein.

Die HTML-Definition berücksichtigt deshalb nicht nur die URL selbst,
sondern auch das Entfernen von führendem und nachgestelltem ASCII-
Whitespace vor der URL-Prüfung.

---

## Valid non-empty URL potentially surrounded by spaces

Hier gelten beide Bedingungen:

1. führender und nachgestellter ASCII-Whitespace wird bei der Prüfung
   berücksichtigt;
2. die verbleibende Zeichenfolge muss eine gültige nichtleere URL sein.

---

# Normative Regeln

## URL-Werte werden nicht pauschal gleich behandelt

Nicht jedes HTML-Attribut, dessen Wert wie eine URL aussieht, besitzt
automatisch dieselben Konformitätsregeln.

Die konkrete Elementdefinition bestimmt:

- ob eine URL verlangt wird,
- ob eine leere URL zulässig ist,
- ob ASCII-Whitespace erlaubt ist,
- welche zusätzliche Verarbeitung stattfindet,
- ob die URL relativ oder absolut sein darf,
- welche weitere Verarbeitung nach der URL-Auflösung erfolgt.

Daher müssen URL-Attribute immer im Zusammenhang mit ihrer jeweiligen
HTML-Definition betrachtet werden.

---

# 2.4.1 Terminology

## Gültige URL

Eine URL muss im Sinne der URL-Spezifikation gültig sein, sofern die
betreffende HTML-Regel eine gültige URL verlangt.

HTML definiert dafür keine zweite konkurrierende URL-Syntax.

---

## ASCII-Whitespace

Bei URL-Werten, für die die HTML-Spezifikation eine URL beschreibt, die
potenziell von Leerzeichen umgeben sein darf, wird führender und
nachgestellter ASCII-Whitespace entsprechend den HTML-Regeln entfernt
bzw. berücksichtigt.

Dies ist von einer beliebigen Unicode-Whitespace-Behandlung zu
unterscheiden.

---

## `about:legacy-compat`

HTML definiert `about:legacy-compat` als reservierte, nicht auflösbare
`about:`-URL.

Sie wird für DOCTYPEs in HTML-Dokumenten verwendet, wenn Kompatibilität
mit XML-Werkzeugen erforderlich ist.

Diese URL ist daher kein gewöhnlicher Zielort einer Webressource.

---

## `about:html-kind`

HTML definiert `about:html-kind` als reservierte, nicht auflösbare
`about:`-URL.

Sie dient als Identifikator für Arten von Media Tracks.

---

## `about:srcdoc`

HTML definiert `about:srcdoc` als reservierte, nicht auflösbare
`about:`-URL.

Sie wird für die URL von `iframe`-`srcdoc`-Dokumenten verwendet.

---

## `about:blank`

HTML definiert Regeln dafür, wann eine URL `about:blank` entspricht.

Eine solche URL besitzt:

- Scheme `about`
- genau einen Path-Eintrag `blank`
- keinen Host
- leeren Username
- leeres Password

Query und Fragment können vorhanden sein.

Damit kann beispielsweise auch eine URL mit Query oder Fragment die
`about:blank`-Matching-Regeln erfüllen, sofern die übrigen Bedingungen
erfüllt sind.

---

## `about:srcdoc` Matching

Eine URL entspricht `about:srcdoc`, wenn:

- das Scheme `about` ist,
- der Path genau `srcdoc` enthält,
- der Query null ist,
- Username leer ist,
- Password leer ist,
- Host null ist.

Das Fragment kann variieren.

---

# 2.4.2 Parsing URLs

## HTML URL Parsing

HTML verwendet für URL-Parsing den URL Parser des WHATWG URL Standards.

HTML ergänzt diesen Prozess um HTML-spezifische Informationen.

Dazu gehören insbesondere:

- Base URL
- Character Encoding
- Environment
- Document
- Environment Settings Object

---

## Parsing relativ zu einer Document Base URL

Eine relative URL wird nicht isoliert interpretiert.

Sie wird relativ zu einer Basis aufgelöst.

Im Fall eines `Document` ist die relevante Basis grundsätzlich dessen
Document Base URL.

Beispiel:

```html
<base href="https://example.test/news/">
<a href="article.html">Artikel</a>
```

Die relative URL `article.html` wird relativ zur Document Base URL
aufgelöst.

Das Ergebnis ist sinngemäß:

```text
https://example.test/news/article.html
```

Die konkrete URL-Auflösung erfolgt nach dem WHATWG URL-Modell.

---

## Environment

Beim HTML-URL-Parsing wird zwischen verschiedenen Umgebungen
unterschieden.

Für ein `Document` wird dessen Base URL verwendet.

Für andere Umgebungen kann die API Base URL des Environment Settings
Object relevant sein.

Damit ist URL-Auflösung nicht ausschließlich eine Eigenschaft des
HTML-Markups.

---

## Character Encoding

Beim Encoding-Parsing einer URL wird die Zeichenkodierung der Umgebung
berücksichtigt.

Für ein `Document` wird dessen Character Encoding verwendet.

Ist die relevante Umgebung keine `Document`-Umgebung, gelten die
entsprechenden Regeln für das Environment Settings Object und dessen
relevante globale Umgebung.

UTF-8 bildet dabei die Ausgangsbasis für die definierten Regeln, soweit
keine spezifischere Encoding-Information der Umgebung greift.

---

## URL Parser

Der eigentliche URL Parser ist im WHATWG URL Standard definiert.

HTML ruft diesen Parser mit:

- einer URL-Zeichenfolge,
- einer Base URL,
- gegebenenfalls einer Character Encoding

auf.

Die HTML-Spezifikation definiert damit die Einbindung des URL Parsers
in das HTML-Verarbeitungsmodell.

---

## URL Serialization

Nach erfolgreichem Parsing kann ein URL Record serialisiert werden.

HTML verwendet hierfür den URL Serializer des WHATWG URL Standards.

Die Serialisierung ist daher ebenfalls kein zweiter HTML-eigener
URL-Serializer.

---

# Encoding-parsing a URL

Das HTML-Verarbeitungsmodell unterscheidet insbesondere zwischen:

- normalem URL-Parsing,
- Encoding-Parsing,
- Encoding-Parsing mit anschließender Serialisierung.

Beim Encoding-Parsing wird die für die Umgebung relevante
Character Encoding berücksichtigt.

Für ein `Document`:

1. Ausgangspunkt ist UTF-8.
2. Die Character Encoding des Documents kann diese Vorgabe ersetzen.
3. Die Document Base URL wird als Base URL verwendet.
4. Der URL Parser wird mit diesen Informationen ausgeführt.

Für andere Umgebungen wird die API Base URL entsprechend berücksichtigt.

---

# Document Base URL

## Grundprinzip

Jedes `Document` besitzt eine Document Base URL.

Sie bestimmt die Basis, gegen die relative URLs aufgelöst werden.

Die Document Base URL ist daher ein zentrales Infrastrukturkonzept für
HTML.

---

## Bestimmung der Document Base URL

Die Document Base URL wird nach den folgenden Grundregeln bestimmt:

1. Existiert kein relevantes `base`-Element mit `href`, wird die
   Fallback Base URL verwendet.
2. Existiert ein solches `base`-Element, wird dessen Frozen Base URL
   verwendet.
3. Maßgeblich ist das erste entsprechende `base`-Element in Tree Order.

Damit ist nicht jedes beliebige `base`-Element automatisch die
Document Base URL.

---

# `base[href]` und Document Base URL

Das `base`-Element ist das zentrale HTML-Element für die explizite
Definition einer Document Base URL.

Die elementbezogene Definition befindet sich in:

`docs/html/02-document-metadata.md`

Die übergreifende URL-Bedeutung wird hier dokumentiert.

---

## Erstes relevantes `base`-Element

Für die Document Base URL ist das erste `base`-Element mit `href` in
Tree Order relevant.

Spätere `base[href]`-Elemente ändern diese Auswahl nicht.

Daraus folgt:

```html
<head>
  <base href="https://example.test/first/">
  <base href="https://example.test/second/">
</head>
```

führt nicht dazu, dass das zweite `base`-Element die Document Base URL
übernimmt.

---

## `base` ohne `href`

Ein `base`-Element kann auch nur `target` besitzen.

Ein solches Element definiert nicht die Document Base URL.

Die URL-Systematik und die Default-Navigation über `base[target]` sind
daher getrennte Konzepte.

---

# Frozen Base URL

Die Document Base URL verwendet bei einem relevanten `base`-Element
dessen Frozen Base URL.

Damit wird die Base-URL-Information in einer definierten Form für die
Dokumentverarbeitung festgehalten.

Die konkrete Erzeugung und Verwendung ist Teil des normativen
Verarbeitungsmodells von HTML.

---

# Fallback Base URL

Wenn kein relevantes `base[href]` vorhanden ist, verwendet das Document
seine Fallback Base URL.

---

## Normalfall

Im normalen Fall entspricht die Fallback Base URL der URL des Documents.

Damit gilt vereinfacht:

```text
Document URL
    ↓
Fallback Base URL
    ↓
Document Base URL
```

wenn kein relevantes `base[href]` vorhanden ist.

---

## `iframe srcdoc`

Für ein `iframe`-`srcdoc`-Document gelten besondere Regeln.

Ein solches Document besitzt eine `about base URL`.

Diese wird für die Fallback Base URL des `srcdoc`-Documents verwendet.

Die `srcdoc`-Regel ist deshalb nicht einfach mit einer gewöhnlichen
Document URL gleichzusetzen.

---

## `about:blank`

Auch für Documents mit einer `about:blank`-URL kann eine nichtleere
`about base URL` relevant sein.

In diesem Fall kann die Fallback Base URL auf diese `about base URL`
zurückgreifen.

Damit können insbesondere neu erzeugte oder initialisierte Documents
eine andere effektive Base URL besitzen als eine naive Betrachtung der
URL-Zeichenfolge `about:blank` vermuten lässt.

---

# Base URL und relative URLs

Relative URLs werden gegen die Document Base URL aufgelöst.

Beispiel:

```html
<base href="https://example.test/docs/">

<img src="image.png">
```

Die relative Ressource wird relativ zu:

```text
https://example.test/docs/
```

aufgelöst.

Die konkrete Darstellung bzw. der konkrete Fetch der Ressource ist
davon zu unterscheiden.

Die URL-Auflösung beantwortet zunächst:

> Welche absolute URL ergibt sich aus dem relativen URL-Wert und der
> aktuellen Base URL?

---

# Base URL und Elementverarbeitung

Viele HTML-Elemente besitzen URL-behaftete Attribute.

Beispiele:

- `a[href]`
- `area[href]`
- `img[src]`
- `script[src]`
- `iframe[src]`
- `form[action]`
- `link[href]`

Die konkrete Verarbeitung jedes Attributes wird durch die jeweilige
Elementdefinition bestimmt.

Die URL-Auflösung erfolgt jedoch grundsätzlich im Kontext der
entsprechenden Base-URL-Regeln.

---

# Auswirkungen von Base-URL-Änderungen

## Grundprinzip

Eine Änderung der Base URL kann Auswirkungen auf die URL-Auflösung
haben.

Sie bedeutet jedoch nicht, dass bereits geladene Ressourcen
automatisch neu geladen werden.

---

## Bereits geladene Ressourcen

Die WHATWG-Spezifikation weist ausdrücklich darauf hin, dass eine
Änderung der Base URL beispielsweise nicht automatisch die bereits von
einem `img`-Element angezeigte Ressource verändert.

Damit sind folgende Konzepte zu unterscheiden:

1. URL-Wert im Content Attribute
2. daraus ermittelte bzw. aufgelöste URL
3. bereits durchgeführte Ressourcenverarbeitung
4. spätere IDL-Abfrage

Eine nachträgliche Base-URL-Änderung kann daher dazu führen, dass eine
spätere URL-Auflösung einen anderen absoluten URL-Wert ergibt, ohne dass
eine bereits geladene Ressource rückwirkend ersetzt wird.

---

# Respond to base URL changes

Bei Änderungen der Base URL existieren normative Reaktionsschritte.

Dazu gehören insbesondere:

- Aktualisierung betroffener Benutzeroberflächen,
- Aktualisierung der Link-/Visited-Verarbeitung,
- Neubewertung bestimmter URL-bezogener Informationen,
- Berücksichtigung von Speculation Rules,
- Berücksichtigung spekulativer Loads.

Die konkrete Verarbeitung ist algorithmisch definiert.

Diese Algorithmen sind Processing Models und keine zusätzlichen
HTML-Elemente.

---

# URL und DOM

URLs stehen in enger Beziehung zu DOM-Objekten.

Beispiele:

- `Document` besitzt eine URL.
- `Document` besitzt eine Character Encoding.
- Elemente können URL-bezogene IDL-Attribute besitzen.
- `base` beeinflusst die Document Base URL.
- URL-Werte können durch IDL-Reflection bzw. URL-spezifische
  Verarbeitung zugänglich sein.

Die DOM-Schnittstellen werden nicht in dieser Datei vollständig
definiert.

Sie werden in:

`docs/html/19-dom-interfaces-and-apis.md`

als eigene Feature-Familie behandelt.

---

# URL und `document.URL`

Die URL eines Documents ist ein DOM-Konzept.

Die URL eines Documents ist nicht dasselbe wie:

- der String des zuletzt gelesenen `href`-Attributes,
- die Document Base URL,
- die Fallback Base URL.

Diese Konzepte können unterschiedliche Werte besitzen.

---

# URL und `base`

Es ist insbesondere zwischen folgenden Begriffen zu unterscheiden:

| Begriff | Bedeutung |
|---|---|
| Document URL | URL des Documents |
| Fallback Base URL | Fallback-Basis für URL-Auflösung |
| Document Base URL | tatsächlich für das Document verwendete Basis |
| Frozen Base URL | aus einem relevanten `base`-Element bestimmte eingefrorene Basis |
| `base[href]` | HTML-Quelle für eine explizite Base URL |
| relative URL | URL, die gegen eine Basis aufgelöst werden muss |
| absolute URL | URL, die bereits vollständig gemäß URL-Modell bestimmt ist |

---

# Content Categories

## URL selbst

Eine URL besitzt keine Content Category.

Content Categories klassifizieren HTML-Inhalte bzw. Elemente.

Eine URL ist dagegen ein Wert.

---

## URL-behaftete Elemente

Elemente mit URL-Attributen können beliebigen Content Categories
angehören.

Beispiele:

- `a` → Flow / Phrasing / ggf. Interactive Content
- `img` → Flow / Phrasing / Embedded Content
- `script` → Metadata / Flow / Phrasing / Script-supporting
- `link` → Metadata und unter bestimmten Bedingungen Flow/Phrasing
- `form` → Flow Content

Die URL-Systematik verändert diese Content Categories nicht.

---

# Context

Die URL-Systematik selbst besitzt keinen Element-Context.

Der Context eines URL-behafteten Elements wird durch dessen
Elementdefinition bestimmt.

Beispiele:

- `base` → `head`-bezogener Kontext
- `link` → abhängig von `rel`, `itemprop` und Position
- `a` → dort, wo Phrasing Content erlaubt ist
- `form` → dort, wo Flow Content erlaubt ist

URL-Auflösung und Element-Context sind deshalb getrennte
Informationsdimensionen.

---

# Content Model

URLs besitzen kein Content Model.

Ein Content Model beschreibt die zulässigen Kindinhalte eines
Elements.

URL-Werte sind dagegen Attributwerte.

---

# Attribute

## Allgemeine URL-Attribute

HTML besitzt zahlreiche Attribute mit URL-Semantik.

Zu den wichtigen Beispielen gehören:

| Element | Attribut | URL-Bezug |
|---|---|---|
| `a` | `href` | Hyperlink |
| `area` | `href` | Hyperlink |
| `base` | `href` | Document Base URL |
| `blockquote` | `cite` | Zitatquelle |
| `del` | `cite` | Änderungsquelle |
| `ins` | `cite` | Änderungsquelle |
| `form` | `action` | Submission-Ziel |
| `img` | `src` | Bildressource |
| `img` | `srcset` | Source-Set-Verarbeitung |
| `iframe` | `src` | Navigable-/Document-Ziel |
| `link` | `href` | Link-/Ressourcenadresse |
| `object` | `data` | externe Ressource |
| `script` | `src` | Scriptressource |
| `video` | `poster` | Posterressource |
| `source` | `src` | Medienressource |
| `track` | `src` | Trackressource |

Diese Liste ist eine Orientierung und kein Ersatz für das vollständige
Attributinventar der Elementreferenz.

---

# URL-Attribute und leere Werte

Nicht jedes URL-Attribut verlangt eine nichtleere URL.

Deshalb darf aus dem allgemeinen Begriff „URL-Attribut“ nicht
abgeleitet werden, dass:

```text
leer
```

immer ungültig ist.

Die konkrete Attributdefinition entscheidet.

---

# URL-Attribute und Whitespace

Bei den in HTML definierten URL-Werttypen können führender und
nachgestellter ASCII-Whitespace nach den jeweiligen Regeln berücksichtigt
werden.

Das bedeutet nicht, dass beliebige Whitespaces an jeder Stelle eines
URL-Wertes ignoriert werden.

---

# Processing Models

## Allgemeines URL-Processing

Ein URL-behaftetes HTML-Feature durchläuft typischerweise mehrere
normative Ebenen:

```text
Content Attribute
        ↓
Attributwert
        ↓
URL-Gültigkeitsprüfung
        ↓
Base-URL-Bestimmung
        ↓
URL-Parsing
        ↓
URL Record
        ↓
Serialisierung / weitere Verarbeitung
        ↓
Navigation / Fetch / sonstige Nutzung
```

Nicht jedes Feature durchläuft exakt dieselben nachgelagerten Schritte.

---

## URL Parsing ist nicht Fetching

Ein erfolgreicher URL-Parse bedeutet nicht automatisch, dass eine
Ressource geladen wird.

Beispiel:

```html
<img src="image.png">
```

Die URL-Auflösung kann erfolgreich sein.

Ob und wann anschließend ein Fetch erfolgt, ist ein separates
Processing Model.

---

# DOM Interfaces / APIs

Die URL-Systematik verwendet und beeinflusst insbesondere:

- `Document`
- `Element`
- `HTMLBaseElement`
- URL-bezogene IDL-Attribute
- Environment Settings Objects

Die eigentliche URL-API des Webplattform-Ökosystems wird nicht als
HTML-eigenes DOM Interface behandelt.

Insbesondere:

- `URL`
- `URLSearchParams`

gehören nicht deshalb zur HTML-Elementreferenz, weil HTML URLs
verwendet.

Sie stammen aus der allgemeinen Webplattform-/URL-Infrastruktur.

---

# API Base URL

Nicht jede URL-Verarbeitung findet direkt in einem `Document` statt.

Für ein Environment Settings Object kann eine API Base URL relevant
sein.

Damit ist die HTML-URL-Verarbeitung auch mit Webplattform-APIs
verbunden, die außerhalb des klassischen Document-Kontexts laufen.

---

# Accessibility

Die URL-Systematik besitzt keine eigenständige Accessibility-Semantik.

Accessibility ergibt sich aus dem konkreten Feature, das die URL
verwendet.

Beispiele:

- `a[href]` kann einen Hyperlink repräsentieren.
- `img[src]` verweist auf eine Ressource, deren alternative
  Repräsentation über andere HTML-Mechanismen bestimmt wird.
- `form[action]` bestimmt ein Submission-Ziel.
- `base[href]` ist kein sichtbares Benutzerinterface.

Die URL selbst erhält dadurch keine zusätzliche Accessibility-Bedeutung.

---

# Sanitization

Die URL-Systematik definiert in §2.4 keine allgemeine HTML-Sanitization-
Policy.

URL-Sicherheit und Sanitization sind deshalb getrennt zu behandeln.

Insbesondere darf aus der Tatsache, dass ein String als URL geparst
werden kann, nicht abgeleitet werden, dass seine Verwendung in jedem
HTML-Kontext sicher oder konform ist.

Die konkrete Sicherheitswirkung hängt unter anderem ab von:

- dem verwendenden Element,
- dem verwendenden Attribut,
- dem URL-Scheme,
- dem jeweiligen Processing Model,
- Sicherheitsrichtlinien,
- Fetch- oder Navigationsregeln.

---

# Konformitätsregeln

## Gültigkeit eines URL-Wertes

Wenn eine Elementdefinition eine gültige URL verlangt, muss der
Attributwert die dort spezifizierte URL-Definition erfüllen.

Die konkrete Definition darf nicht pauschal durch eine vereinfachte
Regex-Regel ersetzt werden.

---

## Relative URLs

Relative URLs sind in HTML grundsätzlich möglich, sofern das konkrete
Attribut nicht ausdrücklich eine andere Form verlangt.

Die relative URL wird gegen die relevante Base URL aufgelöst.

---

## Absolute URLs

Eine URL kann bereits absolut sein.

In diesem Fall ist keine relative Pfadauflösung erforderlich.

Sie durchläuft dennoch das allgemeine URL-Modell.

---

## URL-Scheme

Das URL-Scheme ist Bestandteil des URL-Modells.

HTML definiert nicht pauschal:

> jedes URL-Scheme ist in jedem HTML-Attribut erlaubt.

Die konkrete Verwendung kann zusätzliche Anforderungen besitzen.

Beispielsweise können Sicherheits- oder Processing-Regeln die
Verwendung bestimmter Schemes beeinflussen.

---

# Navigation und URL-Auflösung

URL-Auflösung ist von Navigation zu unterscheiden.

Bei einem Hyperlink können mindestens folgende Schritte unterschieden
werden:

1. Attributwert lesen.
2. URL gegen die Base URL auflösen.
3. resultierende URL bestimmen.
4. Hyperlink-Processing anwenden.
5. Navigationsregeln anwenden.

Damit ist die URL-Auflösung nur ein Teil des gesamten
Navigationsmodells.

---

# Fetching und URL-Auflösung

Auch beim Ressourcenladen ist URL-Auflösung nur ein Teilprozess.

Vereinfacht:

```text
URL-Attribut
    ↓
URL-Auflösung
    ↓
absolute URL / URL Record
    ↓
Fetch-Verarbeitung
    ↓
Response
    ↓
ressourcenspezifische Verarbeitung
```

Der Bereich „Fetching resources“ befindet sich im WHATWG HTML Living
Standard unmittelbar nach §2.4 als §2.5.

Er ist fachlich eine eigenständige Feature-Familie.

---

# Sonderfall: `about:blank`

`about:blank` ist kein gewöhnlicher externer Ressourcen-URL.

HTML verwendet die URL insbesondere im Zusammenhang mit Documents und
Navigables.

Für `about:blank` ist insbesondere relevant, dass eine `about:blank`-
Document-URL eine nicht-null `about base URL` besitzen kann.

Dadurch kann die Fallback Base URL von der bloßen Zeichenfolge
`about:blank` abweichen.

---

# Sonderfall: `iframe srcdoc`

Ein `srcdoc`-Document besitzt eine besondere URL:

```text
about:srcdoc
```

Diese URL dient als Identifikator des `srcdoc`-Documents.

Für die URL-Auflösung ist zusätzlich die `about base URL` relevant.

Damit sind mindestens drei Konzepte auseinanderzuhalten:

- `iframe[srcdoc]`
- Document URL `about:srcdoc`
- Fallback Base URL des `srcdoc`-Documents

---

# Querverweise

## Element ↔ URL

URL-bezogene Elemente:

- `a`
- `area`
- `base`
- `blockquote`
- `del`
- `form`
- `iframe`
- `img`
- `ins`
- `link`
- `object`
- `script`
- `source`
- `track`
- `video`

---

## `base` ↔ Document Base URL

```text
base[href]
    ↓
Frozen Base URL
    ↓
Document Base URL
    ↓
Auflösung relativer URLs
```

---

## Document ↔ Base URL

```text
Document
 ├── Document URL
 ├── Fallback Base URL
 └── Document Base URL
```

Diese Werte sind nicht synonym.

---

## URL ↔ WHATWG URL Standard

```text
HTML
 ├── HTML-spezifische URL-Verwendung
 ├── Base-URL-Regeln
 └── HTML-spezifisches URL-Parsing
          ↓
WHATWG URL Standard
 ├── URL Record
 ├── URL Parser
 ├── URL Serializer
 ├── Scheme
 ├── Host
 ├── Port
 ├── Path
 ├── Query
 └── Fragment
```

---

## URL ↔ Fetch

```text
HTML URL
    ↓
URL Parsing
    ↓
URL Record
    ↓
Fetch
```

Fetch ist nicht Bestandteil der URL-Syntax.

---

## URL ↔ Navigation

```text
Hyperlink
    ↓
URL
    ↓
Navigation Processing
```

Die URL selbst ist nicht die Navigation.

---

## URL ↔ Link Type

Ein Link Type kann die Semantik einer URL-Verwendung bestimmen.

Beispiel:

```html
<link rel="stylesheet" href="style.css">
```

Dabei sind mindestens folgende Ebenen beteiligt:

- URL
- Link Type `stylesheet`
- `link`-Element
- externe Ressourcenverarbeitung
- Fetch
- Stylesheet-Verarbeitung

Diese Ebenen dürfen nicht miteinander verschmolzen werden.

---

# Status / V1

## WHATWG-Status

Die in dieser Datei behandelten Konzepte sind im aktuellen WHATWG HTML
Living Standard definiert.

Sie sind daher:

**im WHATWG-Standard definiert**

bzw. Bestandteil normativer HTML-Verarbeitungsregeln.

---

## Normativer Status

Die folgenden Konzepte besitzen normative Bedeutung:

- URL-Gültigkeitsdefinitionen
- URL Parsing
- Encoding Parsing
- Document Base URL
- Fallback Base URL
- Frozen Base URL
- `about:blank` Matching
- `about:srcdoc` Matching
- Base-URL-Änderungsverarbeitung

---

## ZE-WebLab-V1

Die V1-Einstufung ist eine Projektebene und kein WHATWG-Status.

Für diese Datei gilt:

**V1-Ebene: übergreifendes HTML-Infrastruktur-Feature**

Begründung:

Die URL-Systematik wird von zahlreichen Elementen und APIs verwendet
und kann deshalb nicht sinnvoll als Bestandteil nur einer einzelnen
Elementreferenz behandelt werden.

---

# Erste-Ebene-Abdeckung

## `02-document-metadata.md`

`02-document-metadata.md` behandelt insbesondere:

- `base`
- `base[href]`
- Document Base URL
- `base[target]`
- URL-bezogene Verarbeitung des `base`-Elements
- URL-bezogene Attribute von `link`
- `link[href]`

Die Datei behandelt diese Konzepte überwiegend aus Sicht der
Elementdefinition.

Die vorliegende Datei hebt dagegen die URL-Systematik als
übergreifendes Infrastrukturkonzept heraus.

---

## `06-links.md`

`06-links.md` behandelt:

- Hyperlinks
- URL-bezogene Link-Attribute
- Link Types
- Navigationsbeziehungen

Die URL-Systematik selbst bleibt davon als eigenständige
Infrastrukturebene getrennt.

---

## `08-embedded-content.md`

`08-embedded-content.md` behandelt URL-bezogene Attribute unter anderem
für:

- `img`
- `iframe`
- `object`
- `video`
- `audio`
- `source`
- `track`

Diese Attribute werden dort elementbezogen beschrieben.

Die vorliegende Datei dokumentiert dagegen die gemeinsame
URL-Infrastruktur.

---

## `10-forms.md`

`10-forms.md` behandelt `form[action]` und damit einen konkreten
URL-Anwendungsfall.

Die URL-Auflösung selbst ist ein separates Konzept.

---

## `12-scripting.md`

`12-scripting.md` behandelt unter anderem `script[src]`.

Die URL-Auflösung der Ressource und das Script-Processing sind
unterschiedliche Verarbeitungsebenen.

---

# Abdeckungsstatus

| Bereich | Status |
|---|---|
| §2.4.1 Terminology | vollständig geprüft |
| §2.4.2 Parsing URLs | vollständig geprüft |
| §2.4.3 Document base URLs | vollständig geprüft |
| URL terminology | vollständig |
| Valid URL definitions | vollständig |
| URL parsing integration | vollständig |
| Encoding parsing | vollständig |
| Document Base URL | vollständig |
| Fallback Base URL | vollständig |
| Frozen Base URL | vollständig |
| `about:blank` | vollständig |
| `about:srcdoc` | vollständig |
| Base URL changes | vollständig |
| HTML ↔ URL Standard | vollständig abgegrenzt |
| Fetching resources (§2.5) | bewusst nicht Bestandteil dieser Datei |
| Browser-Support | nicht Bestandteil dieser Datei |

---

# Bewusst nicht Bestandteil dieser Datei

## WHATWG §2.5 Fetching resources

Der direkt folgende Bereich:

**§2.5 Fetching resources**

wird nicht in diese Datei integriert.

Er umfasst unter anderem:

- Fetch terminology
- Resource type determination
- MIME sniffing
- Character encoding extraction
- CORS settings attributes
- Referrer policy attributes
- nonce attributes
- lazy loading attributes
- blocking attributes
- fetch priority attributes

Diese Gruppe stellt eine eigenständige Feature-Familie dar.

Die sinnvolle Folge-Datei ist daher:

`26-fetching-resources.md`

---

## WHATWG §2.6 Common DOM interfaces

Auch §2.6 gehört nicht in diese Datei.

Dieser Bereich betrifft DOM-/Interface-Infrastruktur und wird als
separate Feature-Familie behandelt.

---

# Offene Punkte

## Repository-Verifikation der Datei 24

Bei der direkten erneuten Prüfung des öffentlichen GitHub-Repositorys
konnte `24-common-microsyntaxes.md` über den aktuellen GitHub-Dateiverlauf
nicht als vorhandene Datei verifiziert werden.

Der direkte Dateiverlauf für:

`docs/html/24-common-microsyntaxes.md`

weist derzeit keine Commits aus.

Daher wird der Inhalt von Datei 24 hier nicht als verifizierter
Repository-Bestand behauptet.

Dies betrifft ausschließlich die Repository-Bestandsprüfung und nicht
die normative WHATWG-Recherche zu §2.4.

---

## Repository-Verifikation der Datei 25

`25-urls.md` besitzt zum Zeitpunkt dieser Recherche keinen im
öffentlichen GitHub-Dateiverlauf nachweisbaren Commit.

Die vorliegende Datei ist deshalb als:

**neue Recherchedatei / Erstellungsvorschlag**

einzustufen.

---

## URL Standard als externe normative Quelle

Die eigentliche URL-Syntax und der URL Parser werden vom WHATWG URL
Standard definiert.

Für eine vollständige Detailreferenz der URL-Syntax müsste daher
zusätzlich der WHATWG URL Standard recherchiert werden.

Das ist für diese Datei nur insoweit erforderlich, wie HTML auf diese
Regeln verweist.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard**

Relevanter Bereich:

- §2.4 URLs
- §2.4.1 Terminology
- §2.4.2 Parsing URLs
- §2.4.3 Document base URLs

Geprüfter Stand:

**11. August 2026**

---

## Verwandte WHATWG-Bereiche

- §2.3 Common microsyntaxes
- §2.5 Fetching resources
- §2.6 Common DOM interfaces
- §4.2 Document metadata
- §4.6 Links
- §4.8 Embedded content
- §4.10 Forms
- §4.12 Scripting

---

## Externe normative Spezifikationen

### WHATWG URL Standard

Wird von HTML für:

- URL Parser
- URL Record
- URL Serializer
- URL-Komponenten
- URL-Syntax
- URL-Auflösung

referenziert.

---

## ZE-WebLab-Projektquellen

Relevante bestehende Dateien:

- `docs/html/02-document-metadata.md`
- `docs/html/06-links.md`
- `docs/html/08-embedded-content.md`
- `docs/html/10-forms.md`
- `docs/html/12-scripting.md`

Diese Dateien bilden die erste Rechercheebene bzw. deren bereits
vorhandene elementbezogene Dokumentation.

---

# Prüfstatus

**Rechercheebene:** Zweite Rechercheebene  
**Feature-Familie:** URLs  
**WHATWG-Bereich:** §2.4  
**Normative Prüfung:** abgeschlossen  
**Elementbezogene Abgrenzung:** abgeschlossen  
**Content Categories:** geprüft  
**Context:** geprüft und abgegrenzt  
**Content Model:** nicht anwendbar auf URL als Feature  
**Attribute:** geprüft  
**Processing Models:** geprüft  
**DOM/API-Bezug:** geprüft  
**Accessibility:** geprüft  
**Sanitization:** geprüft  
**Parsing:** geprüft  
**Integration mit WHATWG URL:** geprüft  
**Querverweise:** geprüft  
**Status:** geprüft  
**V1-Abgrenzung:** geprüft  
**Offene Punkte:** dokumentiert

**Dateistatus:** Rechercheinhalt für §2.4 vollständig geprüft.