# ZE-WebLab – HTML-Referenz: HTML Parsing

## Arbeitsstand / Quellenstand

**Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Parsing Concept / Processing Model / Normative Concept / Integration Feature

**Zielpfad:** `docs/html/21-parsing.md`

**Normative Primärquelle:** WHATWG HTML Living Standard.

**Relevante normative Hauptbereiche:**

- §13 The HTML syntax
- §13.1 Writing HTML documents
- §13.2 Parsing HTML documents
- §13.2.1 Overview of the parsing model
- §13.2.2 Parse errors
- §13.2.3 The input byte stream
- §13.2.3.1 Parsing with a known character encoding
- §13.2.3.2 Determining the character encoding
- §13.2.3.3 Character encodings
- §13.2.3.4 Changing the encoding while parsing
- §13.2.3.5 Preprocessing the input stream
- §13.2.4 Parse state
- §13.2.4.1 The insertion mode
- §13.2.4.2 The stack of open elements
- §13.2.4.3 The list of active formatting elements
- §13.2.4.4 The element pointers
- §13.2.4.5 Other parsing state flags
- §13.2.5 Tokenization
- §13.2.6 Tree construction
- §13.2.7 The end
- §13.2.8 Speculative HTML parsing
- §13.2.9 Coercing an HTML DOM into an infoset
- §13.2.10 An introduction to error handling and strange cases in the parser
- §13.3 Serializing HTML fragments
- §13.4 Parsing HTML fragments

**Geprüfter WHATWG-Stand:** HTML Living Standard, zuletzt aktualisiert am 20. Juli 2026.

**Projekt-/Bestandsquelle:** ZE-WebLab GitHub-Repository, Branch `main`.

**Repository-Abgrenzung:**

- `17-custom-elements.md` dokumentiert die Custom-Elements-Featurefamilie.
- `21-parsing.md` dokumentiert die Parsing-Semantik und deren Interaktion mit Custom Elements.
- `22-svg-mathml-integration.md` dokumentiert die SVG-/MathML-Integrationsfeaturefamilie ausführlicher.
- Parsing wird hier nicht als Element, Content Category, Content Model, Link Type, DOM Interface oder API behandelt.

---

## Einordnung

HTML Parsing ist das normative Verarbeitungsmodell, mit dem der User Agent eine `text/html`-Ressource beziehungsweise einen HTML-Eingabestrom verarbeitet und daraus eine DOM-Struktur erzeugt.

Das Parsing-Modell ist nicht lediglich eine Beschreibung der HTML-Syntax.

Es definiert insbesondere:

- Verarbeitung des Input Byte Stream,
- Character Encoding und Encoding Determination,
- Preprocessing des Input Stream,
- Parse Errors,
- Parser State,
- Insertion Mode,
- Stack of Open Elements,
- List of Active Formatting Elements,
- Element Pointers,
- weitere Parsing State Flags,
- Tokenization,
- Tokenizer States,
- Token-Erzeugung,
- Tree Construction,
- Node Creation und Node Insertion,
- Implied End Tags,
- Scope-Prüfungen,
- Formatting Reconstruction,
- Adoption Agency Algorithm,
- Tabellen-Parsing und Foster Parenting,
- Template Parsing,
- Foreign Content,
- SVG-/MathML-Integration,
- Parser-/Scripting-Interaktion,
- Speculative HTML Parsing,
- Stop Parsing,
- Fragment Parsing.

Parsing ist damit ein eigenständiges HTML-Processing-Model.

Es ist weder:

- ein HTML-Element,
- eine Content Category,
- ein Content Model,
- ein Link Type,
- ein DOM Interface,
- noch eine API.

---

## WHATWG-Struktur

Die WHATWG-Spezifikation trennt HTML-Syntax, Parsing und Serialisierung.

### §13 The HTML syntax

Der Syntaxbereich beschreibt unter anderem:

- Schreiben von HTML-Dokumenten,
- DOCTYPE,
- Elemente,
- Start-Tags,
- End-Tags,
- Attribute,
- optionale Tags,
- Einschränkungen von Content Models,
- Raw Text,
- Escapable Raw Text,
- Text,
- Character References,
- CDATA Sections,
- Kommentare,
- Processing Instructions.

Diese Syntaxregeln sind nicht mit dem Parserzustand selbst gleichzusetzen.

### §13.2 Parsing HTML documents

§13.2 beschreibt das normative HTML-Parsing-Modell.

Die aktuelle Struktur umfasst:

1. Overview of the parsing model
2. Parse errors
3. The input byte stream
4. Parse state
5. Tokenization
6. Tree construction
7. The end
8. Speculative HTML parsing
9. Coercing an HTML DOM into an infoset
10. An introduction to error handling and strange cases in the parser

### §13.3 Serializing HTML fragments

Die Serialisierung eines DOM zu HTML-Quelltext ist ein eigenes normatives Modell.

Sie gehört deshalb nicht vollständig in diese Parsing-Datei.

### §13.4 Parsing HTML fragments

Das HTML Fragment Parsing ist dagegen Teil dieser Datei, weil es einen eigenen HTML-Parser mit einem definierten Kontext und speziellen Parserzuständen erzeugt.

---

## Abgrenzung Syntax vs. Parsing

HTML-Syntax und HTML-Parsing sind eng verbunden, aber nicht identisch.

### HTML-Syntax

Die Syntax definiert, wie HTML-Markup geschrieben werden kann und welche Markupformen konform sind.

Beispiel:

```html
<!DOCTYPE html>
<html>
  <head></head>
  <body>
    <p class="example">Hello</p>
  </body>
</html>
```

### HTML-Parsing

Das Parsing definiert dagegen, wie der User Agent den Eingabestrom verarbeitet und daraus eine DOM-Struktur erzeugt.

Dazu gehören auch nicht-konforme Eingaben.

Damit gilt:

**Syntax beschreibt Markupformen und Konformitätsanforderungen.**

**Parsing beschreibt die normative Verarbeitung des Eingabestroms.**

Die beiden Ebenen dürfen in der Dokumentation nicht zusammengeführt werden.

---

## Parsing-Pipeline

Das Parsing lässt sich konzeptionell als folgende Verarbeitungskette darstellen:

```text
Input Bytes
    │
    ▼
Character Encoding Determination
    │
    ▼
Byte Decoding
    │
    ▼
Input Stream Preprocessing
    │
    ▼
Tokenization
    │
    ▼
Tokens
    │
    ▼
Tree Construction
    │
    ├── Parse State
    ├── Stack of Open Elements
    ├── Active Formatting Elements
    ├── Element Pointers
    ├── Insertion Modes
    ├── Template State
    └── Foreign Content
    │
    ▼
DOM
```

Diese Darstellung ist eine konzeptionelle Vereinfachung.

Der normative Parser ist kein rein linearer Pipeline-Prozess.

Insbesondere kann Tree Construction reentrant werden, wenn Scripts während des Parsings zusätzliche Zeichen in den Input Stream einfügen.

---

## Overview of the Parsing Model

Der HTML-Parsing-Prozess erhält als unmittelbaren Input einen Strom von Code Points.

Dieser Input wird zunächst tokenisiert und anschließend durch die Tree Construction verarbeitet.

Das Ergebnis ist ein `Document`-Objekt beziehungsweise im Fragment-Fall ein `DocumentFragment`.

Wesentliche Parserkomponenten sind:

- Tokenizer State Machine,
- Tree Builder,
- Parse State,
- Input Stream,
- Parser Pause Flag,
- Script Nesting Level,
- Insertion Point,
- Stack of Open Elements,
- List of Active Formatting Elements.

### Reentrancy

Die Tree Construction kann reentrant sein.

Während ein Token verarbeitet wird, kann Script-Ausführung dazu führen, dass der Tokenizer erneut aktiviert wird und zusätzliche Tokens erzeugt.

Beispiel:

```html
<script>
  document.write("<p>");
</script>
```

Der Parser muss deshalb nicht als einfache Funktion

```text
Input → Tokenize all → Build DOM
```

verstanden werden.

Vielmehr können sich Tokenization und Tree Construction gegenseitig beeinflussen.

### Script Nesting Level

Der Parser besitzt ein Script Nesting Level.

Es wird initial auf `0` gesetzt.

Während relevanter Script-Verarbeitung kann es erhöht und anschließend wieder verringert werden.

### Parser Pause Flag

Der Parser besitzt ein Parser Pause Flag.

Es wird initial auf `false` gesetzt.

Bei bestimmten Script-Verarbeitungsschritten wird es auf `true` gesetzt, damit keine unerlaubte reentrante Verarbeitung stattfindet.

---

## Input Byte Stream

Der HTML-Parser erhält Netzwerk- oder Dateiinhalte zunächst als Bytes.

Diese Bytes werden anhand eines Character Encodings in Code Points umgewandelt.

Damit ist zwischen folgenden Ebenen zu unterscheiden:

```text
Byte Stream
    ↓
Character Encoding
    ↓
Decoded Input Stream
    ↓
Tokenizer
```

Der HTML-Parser arbeitet nicht unmittelbar auf den ursprünglichen Bytes.

### Byte Order Mark

Ein führender Byte Order Mark kann die Character-Encoding-Verarbeitung beeinflussen.

Das BOM wird entsprechend den Encoding-Regeln behandelt und nicht als normaler HTML-Text an den Tokenizer weitergegeben.

### Decoding

Das Decoding des Byte Streams muss den Regeln des WHATWG Encoding Standard folgen.

Abweichungen beim Decoding können zu unterschiedlichen DOM-Ergebnissen führen.

Insbesondere können Unterschiede beim Umgang mit ungültigen Byte-Sequenzen sicherheitsrelevant sein.

---

## Character Encoding

Der HTML-Parser arbeitet mit:

- einem Character Encoding,
- einer Encoding Confidence.

Die Confidence kann insbesondere sein:

- `tentative`,
- `certain`,
- `irrelevant`.

### Tentative

Das Encoding wurde ermittelt, ist aber noch nicht endgültig bestätigt.

### Certain

Das Encoding gilt für die aktuelle Parserinstanz als bestimmt.

### Irrelevant

Eine Encoding-Entscheidung ist nicht erforderlich, beispielsweise wenn bereits ein Unicode-Code-Point-Stream vorliegt.

---

## Determining the Character Encoding

Die Encoding-Ermittlung kann Informationen aus verschiedenen Quellen berücksichtigen.

Dazu gehören insbesondere:

- Byte Order Mark,
- explizite User-Einstellungen,
- Transport-Metadaten,
- Encoding-Deklarationen in HTML,
- Prescan des Byte Streams,
- Container-Dokument-Kontext,
- weitere spezifizierte Fallback-Regeln.

Die WHATWG-Spezifikation sieht hierfür einen Encoding-Sniffing-Algorithmus vor.

### Prescan

User Agents können den Anfang des Byte Streams vorscannen, um beispielsweise eine relevante `meta`-Encoding-Deklaration zu erkennen.

Das Prescan-Modell ist ein Parsing-/Encoding-Mechanismus und darf nicht mit dem normalen Tokenizer verwechselt werden.

### Zwei-Pass-Situation

Wenn die zunächst angenommene Codierung nicht der tatsächlichen Codierung entspricht, kann der Parser erneut gestartet werden.

Das ist insbesondere relevant, wenn während des Ladens eine widersprechende Encoding-Deklaration erkannt wird.

---

## Changing the Encoding While Parsing

Das HTML-Parsing-Modell kennt einen expliziten Mechanismus zum Ändern der verwendeten Character Encoding.

Ein solcher Wechsel kann beispielsweise durch eine `meta`-Encoding-Deklaration ausgelöst werden.

Je nach aktuellem Encoding und bereits verarbeitetem Input kann:

- die Confidence auf `certain` gesetzt werden,
- die Decodierung umgestellt werden,
- die Verarbeitung fortgesetzt werden,
- oder die Navigation beziehungsweise das Parsing neu gestartet werden.

Ein Encoding-Wechsel ist deshalb kein bloßes Attribut-Update.

Er kann Auswirkungen auf den gesamten bisherigen Parsing-Vorgang haben.

---

## Preprocessing the Input Stream

Vor der Tokenization wird der Input Stream normalisiert.

Wesentliche Regeln betreffen:

- Newline Normalization,
- U+000D CARRIAGE RETURN,
- U+000C FORM FEED,
- U+0000 NULL,
- Surrogates,
- Noncharacters,
- bestimmte Control Characters.

### Newline Normalization

Vor der Tokenization werden Newlines normalisiert.

Dadurch verwendet der Parser für Zeilenumbrüche U+000A LINE FEED.

U+000D CARRIAGE RETURN gelangt dadurch nicht als solcher in die normale Tokenizer-Eingabe.

### NULL

U+0000 NULL wird nicht überall identisch behandelt.

Je nach Parserzustand kann es:

- ignoriert werden,
- als Parse Error behandelt werden,
- oder durch U+FFFD REPLACEMENT CHARACTER ersetzt werden.

Die konkrete Verarbeitung wird durch die späteren Tokenization- und Tree-Construction-Regeln bestimmt.

### Insertion Point

Der Parser besitzt einen Insertion Point.

Dieser beschreibt die Position im Input Stream, an der durch dynamische Markup-Insertion eingefügte Zeichen verarbeitet werden.

Der Insertion Point ist insbesondere für `document.write()` relevant.

---

## Parse Errors

HTML Parsing definiert Parsing-Regeln sowohl für konforme als auch für nicht-konforme HTML-Eingaben.

Bestimmte Punkte der Algorithmen sind als Parse Errors definiert.

Ein Parse Error bedeutet nicht automatisch:

- Exception,
- ungültiges DOM,
- sofortiges Ende des Parsings,
- fehlende Verarbeitung.

Die Spezifikation definiert für Parse Errors normalerweise konkrete Verarbeitungsschritte.

### Parser-Abbruch

Wichtig ist jedoch die genaue normative Aussage:

User Agents dürfen den Parser bei einem Parse Error abbrechen, wenn sie die spezifizierten Recovery-Regeln für diesen Fehler nicht anwenden wollen.

Daher ist folgende Aussage zu vermeiden:

> „Ein Parse Error führt niemals zu einem Parserabbruch.“

Korrekt ist:

> Die HTML-Spezifikation definiert die Verarbeitung von Parse Errors; User Agents dürfen unter den spezifizierten Bedingungen dennoch das Parsing abbrechen.

### Parse Error vs. Conformance Error

Parse Errors sind Teil der HTML-Parsing-/Syntaxverarbeitung.

Ein Dokument kann zusätzlich gegen andere Konformitätsanforderungen verstoßen.

Daher gilt:

```text
Parse Error
    ≠
jede mögliche HTML-Konformitätsverletzung
```

---

## Beispiele für Parse Errors

Typische Parse-Error-Klassen umfassen unter anderem:

- Duplicate Attribute,
- End Tag mit Attributen,
- End Tag mit Trailing Solidus,
- ungültiges erstes Zeichen eines Tag-Namens,
- EOF an unerwarteter Stelle,
- ungültige Character References,
- NULL Characters,
- ungültige DOCTYPE-Syntax,
- ungültige Processing-Instruction-Ziele,
- CDATA im HTML Content,
- fehlerhafte Attribute,
- unerwartete Markup-Sequenzen.

Die WHATWG-Spezifikation definiert hierfür konkrete Verarbeitung.

Die Fehlernamen sind für Konformitätsprüfer relevant; diese Datei dokumentiert nicht das vollständige Fehlercode-Verzeichnis.

---

## Parse State

Der aktuelle WHATWG-Stand definiert `Parse state` als eigenen strukturellen Bereich.

Zum Parse State gehören insbesondere:

1. Insertion Mode
2. Stack of Open Elements
3. List of Active Formatting Elements
4. Element Pointers
5. Other Parsing State Flags

Diese Unterteilung ist für die aktuelle Dokumentationsstruktur zentral.

---

## Insertion Mode

Der Insertion Mode ist eine State Variable der Tree Construction.

Er bestimmt, wie das nächste Token verarbeitet wird.

Aktuelle Insertion Modes umfassen:

- `initial`
- `before html`
- `before head`
- `in head`
- `in head noscript`
- `after head`
- `in body`
- `text`
- `in table`
- `in table text`
- `in caption`
- `in column group`
- `in table body`
- `in row`
- `in cell`
- `in template`
- `after body`
- `in frameset`
- `after frameset`
- `after after body`
- `after after frameset`

Die vollständigen Tokenverarbeitungsregeln gehören zum Tree-Construction-Algorithmus.

### Foreign Content ist kein eigener Insertion Mode

Die Regeln für Foreign Content sind kein zusätzlicher Insertion Mode.

Der Tree-Construction-Dispatcher kann abhängig vom aktuellen Kontext die Foreign-Content-Regeln auswählen.

Der aktuelle Insertion Mode bleibt dabei erhalten.

---

## Resetting the Insertion Mode Appropriately

Der Parser besitzt einen Algorithmus zum Zurücksetzen des Insertion Mode.

Dieser ist insbesondere relevant bei:

- Fragment Parsing,
- Template Contents,
- bestimmten Änderungen des Stack of Open Elements.

Der Parser betrachtet dafür den Stack und bestimmte relevante Elemente.

Das Ergebnis ist beispielsweise ein Wechsel zu:

- `in body`,
- `in table`,
- `in table body`,
- `in row`,
- `in cell`,
- `in caption`,
- `in column group`,
- `in template`,
- `in head`,
- `after head`,
- `in frameset`.

---

## Stack of Open Elements

Der Stack of Open Elements ist eine zentrale interne Parserdatenstruktur.

Er repräsentiert den aktuellen offenen Parsing-Kontext.

Der Stack wird unter anderem verwendet für:

- Current Node,
- Scope-Prüfungen,
- Elementabschluss,
- Insertion Modes,
- Implied End Tags,
- Formatting-Reconstruction,
- Adoption Agency Algorithm,
- Tabellenverarbeitung,
- Foreign Content,
- Template Processing.

Der Stack ist kein DOM-API-Objekt.

### Stack und DOM sind nicht identisch

Ein Element kann aus dem DOM verschoben oder entfernt werden, ohne dass der Stack automatisch entsprechend verändert wird.

Dadurch kann der Parser zeitweise Nodes auf dem Stack enthalten, die nicht mehr an derselben Stelle im DOM liegen.

Das ist insbesondere bei Script-Manipulation und Parser-Reentrancy relevant.

---

## Current Node

Der Current Node ist der unterste beziehungsweise zuletzt eingefügte Node des Stack of Open Elements.

Er ist nicht zwingend identisch mit:

- dem zuletzt erzeugten DOM-Node,
- dem zuletzt eingefügten DOM-Node,
- dem DOM-Element, das visuell „aktuell“ erscheint.

Der Current Node ist eine interne Parserdefinition.

---

## Adjusted Current Node

Der Adjusted Current Node ist insbesondere im Fragment-Parsing-Fall relevant.

Wenn der Parser im Fragment Case erzeugt wurde und der Stack of Open Elements nur den initialen Root enthält, kann das Kontext-Element als Adjusted Current Node verwendet werden.

Außerhalb dieses Sonderfalls entspricht der Adjusted Current Node dem Current Node.

Dieses Konzept ist insbesondere für:

- Fragment Parsing,
- Foreign Content,
- Integration Points,
- Namespace-abhängige Verarbeitung

relevant.

---

## Scope

Scope-Prüfungen sind ein grundlegender Bestandteil der Tree Construction.

Ein Element kann in einem bestimmten Scope liegen oder nicht.

Der Parser prüft dafür den Stack of Open Elements rückwärts.

Verschiedene Scope-Arten besitzen unterschiedliche Grenzlisten.

Relevant sind insbesondere:

- ordinary scope,
- list item scope,
- button scope,
- table scope.

Weitere spezialisierte Scope-Definitionen können in einzelnen Parseralgorithmen auftreten.

### Ordinary Scope

Die allgemeine Scope-Prüfung verwendet eine definierte Gruppe von Boundary-Elementen.

Wenn beim Rückwärtslaufen:

- das gesuchte Element erreicht wird → Match,
- ein Boundary-Element erreicht wird → Failure.

Scope ist daher keine DOM-Traversierung.

Es ist eine Prüfung auf dem internen Parserstack.

### List Item Scope

Für List-Item-Regeln werden zusätzlich `ol` und `ul` als relevante Grenzen berücksichtigt.

### Button Scope

Für Button-Scope kommt `button` als zusätzliche Grenze hinzu.

### Table Scope

Für Table Scope sind insbesondere:

- `html`,
- `table`,
- `template`

relevant.

Scope-Prüfungen sind für das korrekte Verhalten zahlreicher End-Tag- und Recovery-Algorithmen erforderlich.

---

## List of Active Formatting Elements

Die List of Active Formatting Elements verwaltet Formatting-Elemente separat vom Stack of Open Elements.

Sie dient insbesondere zur Behandlung von:

- misnested Formatting,
- Formatting Reconstruction,
- Adoption Agency Algorithm.

Die Liste kann außerdem `marker`-Einträge enthalten.

Marker verhindern unter anderem, dass Formatting-Strukturen über bestimmte Parsergrenzen hinweg „leaken“.

### Noah's Ark Clause

Die Liste begrenzt bestimmte identische Formatting-Elemente.

Innerhalb des relevanten Bereichs nach dem letzten Marker werden nicht beliebig viele identische Formatting-Elemente gehalten.

Der aktuelle Algorithmus begrenzt die Zahl identischer Einträge auf drei.

### Reconstruction

Wenn ein Formatting-Element zwar in der Active Formatting Elements List vorhanden, aber nicht mehr auf dem Stack of Open Elements ist, kann der Parser es rekonstruieren.

Dadurch können Formatting-Elemente im resultierenden DOM wieder auftauchen, obwohl sie im Quelltext nicht erneut geöffnet wurden.

---

## Element Pointers

Der aktuelle WHATWG-Parse-State definiert Element Pointers.

Initial sind insbesondere:

- `head element pointer` → `null`
- `form element pointer` → `null`

### Head Element Pointer

Sobald das `head`-Element geparst wurde, verweist der Head Element Pointer auf dieses Element.

Das gilt unabhängig davon, ob das `head`-Element explizit oder implizit erzeugt wurde.

### Form Element Pointer

Der Form Element Pointer verweist auf das zuletzt geöffnete relevante `form`-Element.

Er ermöglicht historische Form-Association bei fehlerhaftem Markup.

Der Pointer ist nicht einfach eine alternative DOM-Traversierung.

Er ist eine eigene Parser-State-Struktur.

Innerhalb von `template`-Inhalten wird der Form Element Pointer ignoriert.

---

## Other Parsing State Flags

Der aktuelle Parse State enthält weitere Parserzustände.

Dazu gehören insbesondere:

- Root Insertion Target,
- Allow Declarative Shadow Roots,
- Scripting Mode,
- Frameset-Ok Flag.

Diese Zustände sind vom klassischen Begriff „Scripting Flag“ zu unterscheiden.

---

## Root Insertion Target

Der Root Insertion Target ist initial `null`.

Im Fragment-Parsing-Modell wird er auf das erzeugte `DocumentFragment` gesetzt.

Er bestimmt damit das Ziel bestimmter Node-Insertion-Operationen.

Das Konzept ist insbesondere für Fragment Parsing und bestimmte Template-/Shadow-Root-Verarbeitungen relevant.

---

## Allow Declarative Shadow Roots

Der Parser besitzt ein Boolean-Flag:

`allow declarative shadow roots`

Initial ist es `false`.

Der Wert wird in relevanten Parserinstanzen, insbesondere beim Fragment Parsing, explizit gesetzt.

Dieses Flag ist von der allgemeinen Existenz einer Shadow Root zu unterscheiden.

---

## Parser Scripting Mode

Der aktuelle WHATWG-Stand verwendet einen Parser Scripting Mode.

Mögliche Werte sind:

- `Normal`
- `Disabled`
- `Inert`
- `Fragment`

### Normal

Scripts werden entsprechend den normalen Parser-/Scripting-Regeln verarbeitet.

Parser-blockierende klassische Scripts können den Parser anhalten.

### Disabled

Scripting ist deaktiviert.

Dies beeinflusst insbesondere die Verarbeitung von `noscript` und Script-bezogenen Parserregeln.

### Inert

Scripts sind grundsätzlich vorhanden, werden aber in diesem Parsing-Kontext nicht normal ausgeführt.

Dieser Modus ist insbesondere der Default für das HTML Fragment Parsing.

### Fragment

Dieser Modus wird unter anderem von `createContextualFragment()` verwendet.

Scripts werden dabei nach den für diesen Parsermodus definierten Regeln behandelt.

---

## Frameset-Ok Flag

Der Frameset-Ok Flag ist ein Parserzustand.

Er startet als:

```text
ok
```

und wird durch bestimmte Tokens beziehungsweise Inhalte auf:

```text
not ok
```

gesetzt.

Er beeinflusst, ob ein `frameset` an bestimmten Stellen noch als zulässige Tree-Construction-Alternative behandelt werden kann.

Der Frameset-Ok Flag ist keine allgemeine HTML-Konformitätsprüfung.

---

## Template Insertion Modes

`template` besitzt zusätzlich einen Stack von Template Insertion Modes.

Der Parser kann beim Betreten von Template Contents einen neuen Template Insertion Mode auf diesen Stack legen.

Der aktuelle Template Insertion Mode wird verwendet, wenn der Parser auf ein `template`-bezogenes Parsing zurückgesetzt wird.

Damit ist Template Parsing nicht einfach eine normale Unterform von `in body`.

---

## Tokenization

Die Tokenization ist die erste große Verarbeitungsstufe des HTML-Parsers.

Der Tokenizer arbeitet als State Machine.

Der aktuelle WHATWG-Stand definiert eine umfangreiche Menge von Tokenizer States.

Das Ziel ist nicht eine abstrakte „Tag-Erkennung“, sondern eine normative Zeichen-für-Zeichen-Verarbeitung.

---

## Token Model

Die Tokenization erzeugt folgende Tokenarten:

- DOCTYPE Token
- Start Tag Token
- End Tag Token
- Comment Token
- Character Token
- End-of-file Token

### DOCTYPE Token

Ein DOCTYPE Token besitzt unter anderem:

- Name,
- Public Identifier,
- System Identifier,
- Force-Quirks Flag.

Die Werte können den Zustand „missing“ besitzen; dieser Zustand ist von einem leeren String zu unterscheiden.

### Start-/End-Tag Token

Start- und End-Tag Tokens besitzen:

- Tag Name,
- Self-Closing Flag,
- Attribute List.

### Attribute

Jedes Token-Attribut besitzt:

- Name,
- Value.

### Comment Token

Comment Tokens besitzen Daten.

### Character Token

Character Tokens repräsentieren einzelne beziehungsweise zusammengefasste Character-Token-Daten entsprechend den Tokenizer-Regeln.

### EOF Token

Das End-of-file Token repräsentiert das Ende des Input Streams.

---

## Token Creation vs. Token Emission

Das Erzeugen eines Tokens und das Emittieren eines Tokens sind unterschiedliche Schritte.

Ein Token kann erzeugt werden, aber bei bestimmten EOF- oder Fehlerbedingungen nie emittiert werden.

Wenn ein Token emittiert wird, wird es unmittelbar an die Tree Construction weitergegeben.

Die Tree Construction kann anschließend wiederum den Zustand des Tokenizers beeinflussen.

---

## Reconsume

Die Tokenizer-State-Machine verwendet das Konzept des Reconsume.

Dabei wird nicht einfach ein neuer Character aus dem Input Stream gelesen.

Stattdessen wird der aktuelle Character erneut verarbeitet, aber nach den Regeln eines anderen Tokenizer States.

Reconsume ist ein zentraler Mechanismus der State Machine.

---

## Temporary Buffer

Bestimmte Tokenizer States verwenden einen Temporary Buffer.

Er wird insbesondere für:

- Character References,
- Processing Instructions,
- bestimmte Script-Data-Übergänge

verwendet.

Der Temporary Buffer ist eine interne Parserstruktur und kein DOM-Objekt.

---

## Return State

Der Character Reference State verwendet einen Return State.

Dadurch weiß der Tokenizer, in welchen vorherigen Zustand er nach der Character-Reference-Verarbeitung zurückkehren muss.

Dies ist insbesondere relevant, wenn Character References innerhalb von:

- Text,
- Attributwerten

auftreten.

---

## Tokenizer States – vollständige State-Familien

Der aktuelle WHATWG-Stand definiert unter anderem folgende State-Familien.

### Data States

- Data state
- RCDATA state
- RAWTEXT state
- Script data state
- PLAINTEXT state

### Tag States

- Tag open state
- End tag open state
- Tag name state

### RCDATA States

- RCDATA less-than sign state
- RCDATA end tag open state
- RCDATA end tag name state

### RAWTEXT States

- RAWTEXT less-than sign state
- RAWTEXT end tag open state
- RAWTEXT end tag name state

### Script Data States

- Script data less-than sign state
- Script data end tag open state
- Script data end tag name state
- Script data escape start state
- Script data escape start dash state
- Script data escaped state
- Script data escaped dash state
- Script data escaped dash dash state
- Script data escaped less-than sign state
- Script data escaped end tag open state
- Script data escaped end tag name state
- Script data double escape start state
- Script data double escaped state
- Script data double escaped dash state
- Script data double escaped dash dash state
- Script data double escaped less-than sign state
- Script data double escape end state

### Attribute States

- Before attribute name state
- Attribute name state
- After attribute name state
- Before attribute value state
- Attribute value (double-quoted) state
- Attribute value (single-quoted) state
- Attribute value (unquoted) state
- After attribute value (quoted) state
- Self-closing start tag state

### Comment States

- Bogus comment state
- Markup declaration open state
- Comment start state
- Comment start dash state
- Comment state
- Comment less-than sign state
- Comment less-than sign bang state
- Comment less-than sign bang dash state
- Comment less-than sign bang dash dash state
- Comment end dash state
- Comment end state
- Comment end bang state

### DOCTYPE States

- DOCTYPE state
- Before DOCTYPE name state
- DOCTYPE name state
- After DOCTYPE name state
- After DOCTYPE public keyword state
- Before DOCTYPE public identifier state
- DOCTYPE public identifier (double-quoted) state
- DOCTYPE public identifier (single-quoted) state
- After DOCTYPE public identifier state
- Between DOCTYPE public and system identifiers state
- After DOCTYPE system keyword state
- Before DOCTYPE system identifier state
- DOCTYPE system identifier (double-quoted) state
- DOCTYPE system identifier (single-quoted) state
- After DOCTYPE system identifier state
- Bogus DOCTYPE state

### CDATA States

- CDATA section state
- CDATA section bracket state
- CDATA section end state

CDATA wird innerhalb des HTML-Parsers insbesondere im Foreign Content relevant.

### Processing Instruction States

Der aktuelle Tokenizer besitzt ausdrücklich:

- Processing instruction open state
- Processing instruction target state
- After processing instruction target state
- Processing instruction data state
- Processing instruction questionable state

Processing Instructions werden damit nicht lediglich als „unbekannte Tags“ behandelt.

### Character Reference States

- Character reference state
- Named character reference state
- Ambiguous ampersand state
- Numeric character reference state
- Hexadecimal character reference start state
- Hexadecimal character reference state
- Decimal character reference state
- Numeric character reference end state

---

## Data State

Der Data State ist der initiale Tokenizer State.

Typische Übergänge:

```text
&   → Character Reference
<   → Tag Open
EOF → EOF Token
sonst → Character Token
```

NULL Characters und weitere Sonderfälle werden nach den jeweils definierten Regeln verarbeitet.

---

## RCDATA State

RCDATA wird insbesondere für:

- `textarea`
- `title`

verwendet.

Character References werden verarbeitet.

Ein `<` kann in die RCDATA-spezifischen End-Tag-States führen.

---

## RAWTEXT State

RAWTEXT wird unter anderem für:

- `style`,
- `xmp`,
- `iframe`,
- `noembed`,
- `noframes`

verwendet.

Der Tokenizer interpretiert den Inhalt grundsätzlich als Text, verwendet aber spezielle Regeln, um das passende End-Tag erkennen zu können.

---

## Script Data State

`script`-Inhalte werden mit einer eigenen State-Familie verarbeitet.

Dazu gehören unter anderem:

- Script Data,
- Escaped,
- Double Escaped,
- End Tag Detection.

Das HTML-Parsing darf dabei nicht mit dem JavaScript-Parser verwechselt werden.

Der HTML-Tokenizer bestimmt lediglich, welche Zeichen als Script-Element-Inhalt verarbeitet werden.

Die eigentliche JavaScript-Syntax wird durch das JavaScript-Processing-Modell bestimmt.

---

## PLAINTEXT State

Im PLAINTEXT State wird der restliche Input grundsätzlich als Text behandelt.

Das End-of-file bleibt als Parsergrenze relevant.

---

## Character References

Character References werden durch eigene Tokenizer States verarbeitet.

Beispiele:

```html
&amp;
&lt;
&gt;
&quot;
```

Die Verarbeitung unterscheidet unter anderem:

- named character references,
- numeric character references,
- hexadecimal character references,
- decimal character references,
- ambiguous ampersands.

Character References sind kontextabhängig.

Insbesondere unterscheiden sich:

- normaler Text,
- Attributwerte,
- RCDATA,
- RAWTEXT,
- Script Data.

---

## Attribute Tokenization

Der Tokenizer verarbeitet Attribute über eigene States.

Unterstützt werden insbesondere:

- unquoted values,
- single-quoted values,
- double-quoted values,
- empty attribute values.

Beispiele:

```html
<input disabled>
<input value=yes>
<input type='checkbox'>
<input name="example">
```

Die Tokenizer-Regeln sind von den Authoring-Konformitätsregeln zu unterscheiden.

---

## Duplicate Attributes

Doppelte Attribute desselben Namens stellen einen Parse Error dar.

Beim Parsing werden spätere Duplikate nach den definierten Tokenizer-Regeln ignoriert.

Daraus folgt:

```text
Quelltext-Konformität
        ≠
Parser-Verhalten
```

Ein nicht-konformes Start-Tag kann deshalb trotzdem ein deterministisch beschriebenes Token und DOM-Ergebnis erzeugen.

---

## Comments

Kommentare werden über eine eigene Tokenizer-State-Familie verarbeitet.

Beispiel:

```html
<!-- comment -->
```

Der Parser erzeugt daraus ein Comment Token.

Die Tree Construction erzeugt anschließend einen DOM Comment Node.

Fehlerhafte Kommentarformen werden nicht einfach verworfen; sie unterliegen den definierten Parse-Error- und Recovery-Regeln.

---

## DOCTYPE Tokenization

DOCTYPE-Markup wird über eigene Tokenizer States verarbeitet.

Das Token enthält:

- Name,
- Public Identifier,
- System Identifier,
- Force-Quirks Flag.

Die Tree Construction entscheidet anschließend, wie das DOCTYPE Token in das Dokumentmodell übernommen wird.

---

## Processing Instructions

Der aktuelle HTML-Tokenizer besitzt Processing-Instruction-States.

HTML unterstützt diese nicht als XML-Processing-Instruction-Modell.

Wenn eine Processing Instruction im HTML-Parser erkannt wird, gelten die HTML-spezifischen Regeln.

Bei ungültigen Targets können die betreffenden Daten in ein Comment Token überführt werden.

Das Parsing von HTML ist daher nicht mit dem XML-Processing-Instruction-Modell gleichzusetzen.

---

## CDATA

CDATA Sections besitzen im HTML-Parser einen besonderen Status.

Innerhalb von Foreign Content können CDATA Sections entsprechend den Foreign-Content-Regeln verarbeitet werden.

Außerhalb von Foreign Content stellt eine CDATA Section einen Parse Error dar und wird nach den HTML-Parsing-Regeln verarbeitet.

---

## Tokenization und Tree Construction

Die Tokenization und Tree Construction sind nicht unabhängig voneinander.

Wenn ein Token emittiert wird:

```text
Tokenizer
    ↓
Token
    ↓
Tree Builder
    ↓
DOM / Parser State
```

Die Tree Construction kann dabei:

- Parser State verändern,
- den Tokenizer State verändern,
- zusätzliche Zeichen in den Input Stream einfügen,
- Script-Ausführung auslösen.

Damit besteht eine Rückkopplung zwischen beiden Stufen.

---

## Tree Construction

Die Tree Construction verarbeitet Tokens und erzeugt daraus DOM-Nodes.

Sie ist ein zustandsabhängiges Processing Model.

Sie verwaltet insbesondere:

- Stack of Open Elements,
- Active Formatting Elements,
- Insertion Mode,
- Template Insertion Mode Stack,
- Element Pointers,
- Parsing State Flags.

Die Abbildung ist deshalb nicht einfach:

```text
Token → DOM Node
```

---

## Creating and Inserting Nodes

Der aktuelle WHATWG-Stand definiert eigene Parseralgorithmen für Node Creation und Node Insertion.

Diese Algorithmen sind von öffentlichen DOM-APIs wie:

```js
document.createElement()
```

zu unterscheiden.

Die Parseralgorithmen berücksichtigen unter anderem:

- HTML Namespace,
- Foreign Namespaces,
- Custom Element Registry,
- Custom Element Creation,
- Template Contents,
- Shadow-Root-bezogene Verarbeitung,
- Root Insertion Target,
- Attribute,
- Document Type,
- Parserzustand.

---

## Appropriate Place for Inserting a Node

Die Tree Construction bestimmt nicht in jedem Fall einfach:

> Parent = Current Node

Stattdessen gibt es einen definierten Mechanismus zur Bestimmung des geeigneten Einfügeorts.

Relevant sind unter anderem:

- Current Node,
- Adjusted Current Node,
- Template Contents,
- Root Insertion Target,
- Foster Parenting.

Dieser Mechanismus ist insbesondere für Templates und Tabellen erforderlich.

---

## Adjusted Insertion Location

Der Adjusted Insertion Location bestimmt, an welcher Stelle ein neu zu erzeugender Node tatsächlich eingefügt wird.

Das Konzept ist insbesondere relevant für:

- normale DOM-Insertion,
- Template Contents,
- Fragment Parsing,
- Foster Parenting,
- Root Insertion Target.

Der Adjusted Insertion Location ist daher nicht mit dem einfachen Parent des Current Node gleichzusetzen.

---

## Implied End Tags

Der Parser besitzt eigene Algorithmen zum Generieren beziehungsweise Schließen von Implied End Tags.

Ein Implied End Tag ist eine Parseroperation.

Es ist nicht dasselbe wie ein optionales End-Tag in der HTML-Syntax.

### Beispiel

```html
<p>One
<p>Two
```

Die Tree Construction kann beim zweiten `p`-Start-Tag die zuvor offene `p`-Struktur entsprechend den Parsing-Regeln schließen.

---

## Optional Tags vs. Implied End Tags

Diese Begriffe müssen strikt getrennt werden.

### Optional Tag

Ein optionales Tag ist eine Eigenschaft der HTML-Syntax beziehungsweise der Authoring-Regeln.

### Implied End Tag

Ein Implied End Tag ist eine Operation beziehungsweise ein Algorithmus der Tree Construction.

Daher gilt:

```text
Optional Tag
    → Syntax / Authoring

Implied End Tag
    → Parser / Tree Construction
```

---

## Reconstructing the Active Formatting Elements

Wenn Formatting Elements im Active Formatting Elements List vorhanden, aber nicht mehr auf dem Stack of Open Elements sind, kann der Parser sie rekonstruieren.

Das ermöglicht beispielsweise:

```html
<p><b>one
<p>two
```

ein Verhalten, bei dem die Formatting-Struktur in späteren Abschnitten wieder aufgebaut wird.

Die Rekonstruktion ist eine normative Parseroperation.

---

## Adoption Agency Algorithm

Der Adoption Agency Algorithm behandelt bestimmte misnested Formatting Elements.

Beispiel:

```html
<b><i>text</b>more</i>
```

Der Parser versucht nicht einfach, einen XML-artigen Stack abzuwickeln.

Stattdessen verwendet er:

- Active Formatting Elements,
- Stack of Open Elements,
- Scope,
- Formatting Reconstruction,
- Adoption Agency Algorithm.

Der Algorithmus kann den Stack und die Active Formatting Elements List in einer kontrollierten Form verändern.

---

## Insertion Modes – Übersicht

Der Tree Builder kennt folgende Insertion Modes:

| Insertion Mode | Funktion |
|---|---|
| `initial` | Dokumentbeginn / DOCTYPE |
| `before html` | Aufbau des Dokumentelements |
| `before head` | Aufbau des `head`-Kontexts |
| `in head` | Verarbeitung von Head-Inhalt |
| `in head noscript` | spezieller `noscript`-Head-Kontext |
| `after head` | Übergang zum Body |
| `in body` | normaler Dokumentinhalt |
| `text` | Textinhalt bestimmter Elemente |
| `in table` | Tabellenkontext |
| `in table text` | Character Tokens im Tabellenkontext |
| `in caption` | Tabellen-Caption |
| `in column group` | Spaltengruppen |
| `in table body` | `tbody`, `thead`, `tfoot` |
| `in row` | Tabellenzeile |
| `in cell` | Tabellenzelle |
| `in template` | Template Contents |
| `after body` | Inhalt nach dem Body |
| `in frameset` | Frameset |
| `after frameset` | Inhalt nach Frameset |
| `after after body` | Dokumentabschluss nach Body |
| `after after frameset` | Dokumentabschluss nach Frameset |

---

## Initial Insertion Mode

Der Parser beginnt im `initial` Insertion Mode.

Dort werden insbesondere:

- DOCTYPE Tokens,
- Whitespace,
- Comments

nach den definierten Regeln verarbeitet.

Danach wechselt der Tree Builder in die nachfolgenden Modi.

---

## Before HTML

Der `before html`-Mode verarbeitet Tokens vor dem Dokumentelement.

Wenn kein explizites `html`-Element vorhanden ist, kann der Parser ein solches implizit erzeugen.

---

## Before Head

Der `before head`-Mode verarbeitet Tokens zwischen dem Dokumentelement und dem Aufbau des Head-Kontexts.

Bei Bedarf wird ein `head`-Element implizit erzeugt.

---

## In Head

Der `in head`-Mode verarbeitet unter anderem:

- `base`,
- `basefont`,
- `bgsound`,
- `link`,
- `meta`,
- `title`,
- `noscript`,
- `noframes`,
- `style`,
- `template`.

Das Parsing hängt dabei sowohl vom Token als auch vom aktuellen Parserzustand ab.

---

## In Head Noscript

Der `in head noscript`-Mode besitzt spezielle Regeln für `noscript`-Inhalte im Head-Kontext.

Das konkrete Verhalten hängt vom Parser Scripting Mode ab.

---

## After Head

Der `after head`-Mode verarbeitet Tokens nach Abschluss des Head-Kontexts.

Bei Bedarf werden Body-Strukturen implizit erzeugt.

---

## In Body

Der `in body`-Mode verarbeitet einen großen Teil des normalen HTML-Dokuments.

Dazu gehören unter anderem:

- Paragraphen,
- Headings,
- Lists,
- Links,
- Formatting,
- Embedded Content,
- Forms,
- Tables,
- Scripts,
- Templates,
- Custom Elements.

Die konkreten Regeln sind token- und zustandsabhängig.

---

## Text Insertion Mode

Der `text`-Mode wird insbesondere bei Elementen verwendet, deren Inhalt über spezielle Tokenizer States verarbeitet wird.

Beispiele sind:

- `script`,
- `style`,
- `textarea`,
- `title`,
- weitere Raw-Text-/RCDATA-Kontexte.

Nach Abschluss des Textkontexts wird der vorherige Insertion Mode wiederhergestellt.

---

## Table Parsing

Tabellen besitzen ein eigenes Tree-Construction-Modell.

Relevante Insertion Modes:

- `in table`,
- `in table text`,
- `in caption`,
- `in column group`,
- `in table body`,
- `in row`,
- `in cell`.

Der Parser kann bei fehlerhaftem Tabellen-Markup DOM-Strukturen erzeugen, die deutlich von der Quelltextstruktur abweichen.

---

## In Table

Der `in table`-Mode verarbeitet Tokens im Tabellenkontext.

Er unterscheidet unter anderem:

- `caption`,
- `colgroup`,
- `tbody`,
- `tfoot`,
- `thead`,
- `tr`,
- Character Tokens,
- sonstige Tokens.

Nicht zum Tabellenkontext passende Inhalte können nach Foster-Parenting-Regeln verarbeitet werden.

---

## In Table Text

Character Tokens werden im Tabellenkontext zunächst gesammelt.

Hierfür existiert der Zustand:

- Pending Table Character Tokens.

Nachfolgend wird entschieden, ob die Character Tokens als geeigneter Tabelleninhalt verarbeitet oder über die speziellen Tabellen-Recovery-Regeln behandelt werden.

---

## Foster Parenting

Foster Parenting ist ein spezieller Tree-Construction-Mechanismus im Tabellenkontext.

Wenn Markup an einer Stelle erscheint, an der es nach den Tabellenregeln nicht direkt eingefügt werden kann, kann der Parser den Node außerhalb der Tabelle einfügen.

Dadurch kann beispielsweise:

```html
<table>
  <div>Example</div>
</table>
```

zu einer DOM-Struktur führen, in der der `div` nicht einfach als Child der `table` erscheint.

Foster Parenting ist ein Parseralgorithmus und keine allgemeine DOM-Regel.

---

## In Caption

Der `in caption`-Mode verarbeitet den Inhalt eines `caption`-Elements.

Beim Verlassen des Caption-Kontexts werden unter anderem:

- Scope,
- Active Formatting Elements,
- Stack of Open Elements

entsprechend den Tree-Construction-Regeln verarbeitet.

---

## In Column Group

Der `in column group`-Mode verarbeitet insbesondere:

- `col`,
- `template`,
- weitere für den Tabellenaufbau relevante Tokens.

---

## In Table Body

Der `in table body`-Mode verarbeitet:

- `tr`,
- `th`,
- `td`,
- weitere Tabellenstrukturen.

Bei Bedarf werden Tabellenzeilen beziehungsweise Tabellenkörperstrukturen implizit erzeugt.

---

## In Row

Der `in row`-Mode verarbeitet insbesondere:

- `td`,
- `th`,
- `tr`,
- bestimmte Tabellenabschluss-Tokens.

---

## In Cell

Der `in cell`-Mode verarbeitet den Inhalt einer Tabellenzelle.

Beim Verlassen einer Zelle werden unter anderem:

- implied end tags,
- Active Formatting Elements,
- Stack of Open Elements

entsprechend den Regeln zurückgesetzt beziehungsweise bereinigt.

---

## Templates

`template` besitzt ein eigenes Parsing-Modell.

Template Contents sind nicht einfach normale Child Nodes des `template`-Elements.

Der Parser verwendet dafür:

- Template Contents,
- Template Insertion Mode Stack,
- Current Template Insertion Mode,
- Adjusted Current Node,
- Template-spezifische Insertion Modes.

Das Template Contents DocumentFragment ist damit ein eigener Parsing-Kontext.

---

## Foreign Content

HTML Parsing integriert insbesondere:

- SVG,
- MathML

als Foreign Content.

Foreign Content ist kein eigener Insertion Mode.

Der Tree-Construction-Dispatcher entscheidet anhand des aktuellen Parserkontexts, ob:

- HTML Content Rules,
- oder Foreign Content Rules

anzuwenden sind.

Die vollständige SVG-/MathML-Integrationssystematik ist in `22-svg-mathml-integration.md` dokumentiert.

Diese Datei behandelt hier nur den Parsing-Mechanismus.

---

## Foreign Content Dispatcher

Bei Foreign Content wird der Token nach den speziellen Foreign-Content-Regeln verarbeitet.

Bestimmte Tokens können jedoch dazu führen, dass der Parser:

1. Foreign Content verlässt,
2. Elemente vom Stack entfernt,
3. den Token erneut verarbeitet,
4. die HTML-Insertion-Mode-Regeln verwendet.

Damit kann der Parser innerhalb eines einzelnen Dokuments zwischen HTML- und Foreign-Content-Regeln wechseln.

---

## Integration Points

Integration Points bestimmen unter anderem, wann HTML-Regeln innerhalb von SVG-/MathML-Kontexten wieder relevant werden.

Dazu gehören insbesondere:

- HTML Integration Points,
- MathML Text Integration Points.

Sie ermöglichen Übergänge wie:

```text
HTML
  ↓
SVG / MathML
  ↓
Integration Point
  ↓
HTML Parsing
```

Die vollständige Liste und die spezifischen SVG-/MathML-Regeln gehören in `22-svg-mathml-integration.md`.

---

## Foreign Element Creation

Beim Erzeugen eines Foreign Elements werden unter anderem berücksichtigt:

- Namespace,
- Local Name,
- Adjusted Attributes,
- Self-Closing Flag,
- Current/Adjusted Current Node.

Der Parser erzeugt dabei nicht automatisch ein HTML-Namespace-Element.

---

## SVG Name Adjustment

Der HTML-Parser kann bestimmte SVG-Namen korrigieren.

Beispielsweise werden bestimmte kleingeschriebene Token-Namen in die korrekten SVG-Namen überführt.

Beispiele:

```text
foreignobject → foreignObject
lineargradient → linearGradient
radialgradient → radialGradient
textpath → textPath
```

Die vollständige Adjustment-Tabelle gehört in die SVG-/MathML-Integrationsdatei.

---

## SVG Attribute Adjustment

Bestimmte SVG-Attribute werden beim HTML-Parsing auf ihre spezifizierten Namen angepasst.

Diese Anpassung ist erforderlich, weil HTML-Tokenization Namen zunächst nach den HTML-Regeln verarbeitet.

Die vollständige Mapping-Tabelle gehört in `22-svg-mathml-integration.md`.

---

## MathML Attribute Adjustment

Auch MathML besitzt definierte Attribute, deren Schreibweise beziehungsweise Semantik beim HTML-Parsing angepasst werden kann.

Die vollständige Mapping-Tabelle gehört in die SVG-/MathML-Integrationsdatei.

---

## Foreign Attribute Adjustment

Bestimmte Foreign Attributes werden Namespace-bezogen angepasst.

Relevant sind insbesondere:

- XML Namespace,
- XMLNS Namespace,
- XLink Namespace.

Beispiele:

```text
xml:lang
xmlns
xlink:href
```

Die HTML-Syntax erzeugt daraus im DOM die entsprechenden Namespace-/Local-Name-Kombinationen.

---

## Character Tokens in Foreign Content

Character Tokens werden auch im Foreign Content nach den Foreign-Content-Regeln verarbeitet.

Whitespace kann dabei anders behandelt werden als andere Character Tokens.

Nicht-Whitespace-Character führen unter anderem dazu, dass der Frameset-Ok Flag auf `not ok` gesetzt wird.

---

## Custom Elements und Parsing

Custom Elements sind mit der Tree Construction verbunden.

Der Parser kann unter anderem:

- autonome Custom Elements erzeugen,
- noch nicht definierte Custom Elements erzeugen,
- definierte Custom Elements über die Custom-Elements-Infrastruktur erzeugen,
- customized built-in elements anhand des `is`-Mechanismus erzeugen.

Die detaillierte Custom-Elements-Semantik gehört zu:

`17-custom-elements.md`

Diese Datei dokumentiert lediglich die Parsing-Integration.

---

## Custom Element Reactions

Bei der Parser-basierten Elementerzeugung können Custom Element Reactions relevant werden.

Konzeptionell:

```text
Tokenizer
    ↓
Tree Construction
    ↓
Element Creation
    ↓
Custom Element Definition / Lookup
    ↓
Custom Element Reactions
    ↓
DOM
```

Das Reaction-Stack-Modell selbst wird nicht in dieser Datei dupliziert.

---

## `is` und Customized Built-in Elements

Beim Parsing kann das `is`-Attribut die Erzeugung eines customized built-in element beeinflussen.

Das Parsing muss deshalb den Wert nicht nur als gewöhnliches Attribut betrachten.

Die Custom-Elements-Definition bestimmt, welche Konstruktor-/Registry-Semantik daraus folgt.

---

## Parser und Scripting

Parsing und Scripting sind eng gekoppelt.

Das Parsing kann beeinflusst werden durch:

- klassische parser-blocking Scripts,
- `document.write()`,
- Script Execution,
- Parser Pause Flag,
- Script Nesting Level,
- Insertion Point,
- Event Loop.

Diese Datei dokumentiert die Parsing-Seite.

Das vollständige Scripting-Modell gehört zu `12-scripting.md` und den entsprechenden späteren Web-Platform-Featurefamilien.

---

## Parser-Insertion

Ein parser-inserted Script kann sich anders verhalten als ein Script, das später über DOM APIs erzeugt wird.

Der Parser führt bestimmte Schritte in einer definierten Reihenfolge aus:

```text
Script Token
    ↓
Script Element Creation
    ↓
DOM Insertion
    ↓
Script Processing
    ↓
Parser Pause / Resume
```

Die konkrete Ausführung hängt vom Script-Typ und den Scripting-Regeln ab.

---

## Script Nesting Level

Der Parser führt ein Script Nesting Level.

Bei relevanter Script-Verarbeitung:

```text
script nesting level += 1
```

Nach Abschluss:

```text
script nesting level -= 1
```

Wenn der Wert wieder `0` erreicht, kann der Parser Pause Flag entsprechend zurückgesetzt werden.

---

## Parser Pause Flag

Das Parser Pause Flag verhindert bestimmte reentrante Parserverarbeitung.

Es ist insbesondere relevant, wenn ein Script während der Tree Construction ausgeführt wird.

Während der Pause kann der Tokenizer nicht einfach unkontrolliert weitere verschachtelte Parseraufrufe abarbeiten.

---

## Insertion Point und `document.write()`

`document.write()` kann neue Zeichen in den Input Stream einfügen.

Der Parser verwendet dafür den Insertion Point.

Das ist ein wesentlicher Grund dafür, dass HTML Parsing nicht als rein statische Verarbeitung eines bereits vollständig vorhandenen Strings modelliert werden kann.

---

## Speculative HTML Parsing

Die WHATWG-Spezifikation definiert Speculative HTML Parsing als Optimierungsmechanismus.

Es kann parallel zur normalen Parserverarbeitung ausgeführt werden, insbesondere wenn der normale Parser durch Script-Ausführung blockiert ist.

### Wichtige Eigenschaften

Ein Speculative Parser:

- verwendet einen eigenen Parserzustand,
- erzeugt speculative mock elements,
- erzeugt kein normales finales DOM,
- kann spekulative Fetches auslösen,
- darf das normative DOM-Ergebnis nicht ersetzen.

### Active Speculative HTML Parser

Ein HTML Parser kann einen Active Speculative HTML Parser besitzen.

Beim Start wird ein spekulativer Parser mit entsprechendem Zustand erzeugt.

### Speculative Mock Elements

Speculative Mock Elements repräsentieren:

- Namespace,
- Local Name,
- Attribute,
- Children.

Sie sind keine normalen DOM-Elemente.

### Speculative Fetches

Speculative Parsing kann Ressourcen-Fetches vorwegnehmen.

Relevant sind insbesondere:

- `base`,
- bestimmte `meta`-Elemente,
- Ressourcenreferenzen.

Die eigentliche Fetch-Semantik gehört zur Fetching-/Resource-Featurefamilie.

---

## Speculative Parsing und `26-fetching-resources.md`

Die Parsing-Datei dokumentiert:

- warum speculative parsing existiert,
- welche Parserstrukturen verwendet werden,
- wie speculative fetches mit dem Parser verbunden sind.

Die vollständige Resource-Fetch-Semantik wird nicht dupliziert.

---

## The End

Der aktuelle WHATWG-Stand besitzt einen eigenen Abschnitt:

**§13.2.7 The end**

Das Ende des Parsings ist mehr als die Verarbeitung eines EOF Tokens.

Wenn der User Agent das Dokumentparsing beendet, werden unter anderem:

- der Active Speculative HTML Parser beendet,
- der Insertion Point aufgehoben,
- Document Readiness auf `interactive` aktualisiert,
- der Stack of Open Elements geleert,
- parser-blockierte beziehungsweise nach dem Parsing auszuführende Scripts verarbeitet,
- `DOMContentLoaded` ausgelöst,
- weitere Event-Loop- und Load-Schritte ausgeführt.

Diese Datei dokumentiert die Parsing-Seite.

Die vollständige Document-Lifecycle-Semantik wird in der entsprechenden Lifecycle-Dokumentation behandelt.

---

## EOF Processing

EOF ist ein Tokenizer-Konzept.

Das EOF Token kann in verschiedenen Insertion Modes unterschiedliche Auswirkungen haben.

Daher gilt:

```text
EOF Token
    ≠
sofortiges Stop Parsing
```

Die Tree Construction kann beim EOF noch definierte Abschlussoperationen ausführen.

Erst anschließend wird das eigentliche Stop-Parsing-Verfahren erreicht.

---

## Stop Parsing

Wenn das Dokumentparsing beendet wird, muss der Parser die dafür definierten Abschlussoperationen durchführen.

Dazu gehört insbesondere:

1. Speculative Parsing beenden,
2. Insertion Point aufheben,
3. Document Readiness aktualisieren,
4. Stack of Open Elements leeren,
5. relevante nach dem Parsing auszuführende Scripts verarbeiten,
6. `DOMContentLoaded`-Verarbeitung vorbereiten beziehungsweise auslösen,
7. spätere Load-bezogene Schritte gemäß dem Dokument-Lifecycle durchführen.

Die vollständigen Event- und Lifecycle-Regeln sind nicht Bestandteil dieser Parsing-Datei.

---

## Coercing an HTML DOM into an Infoset

Der aktuelle WHATWG-Stand enthält einen eigenen Abschnitt zum Überführen eines HTML-DOM in ein XML-/Infoset-kompatibles Modell.

Dieser Bereich ist nicht mit normalem HTML Parsing gleichzusetzen.

Relevant sind insbesondere mögliche Probleme mit:

- `xmlns`,
- XMLNS Namespace,
- XLink,
- ungewöhnlichen lokalen Namen,
- Kommentaren,
- nicht-XML-kompatiblen Zeichen,
- Quirks-/Limited-Quirks-/No-Quirks-Information,
- Form Association,
- Template Contents.

Dieser Mechanismus wird erst nach Anwendung der HTML-Parserregeln relevant.

Er ist daher als angrenzendes Verarbeitungsmodell zu betrachten.

---

## Error Handling und Strange Cases

Der aktuelle WHATWG-Standard enthält zusätzlich einen erklärenden Bereich zu ungewöhnlichen Parsing-Fällen.

Dazu gehören insbesondere:

- misnested tags,
- unerwartetes Markup in Tabellen,
- Scripts, die die Seite während des Parsings verändern,
- Scripts über mehrere Documents hinweg,
- unclosed Formatting Elements.

Diese Beispiele dienen der Erklärung der normativen Parserregeln.

Sie stellen kein separates alternatives Parsing-Modell dar.

---

## Misnested Formatting

Beispiel:

```html
<b><i></b></i>
```

Die DOM-Struktur wird nicht nach einer simplen XML-Stack-Regel erzeugt.

Stattdessen greifen:

- Active Formatting Elements,
- Scope,
- Reconstruction,
- Adoption Agency Algorithm.

---

## Unerwartetes Markup in Tabellen

Beispiel:

```html
<table>
  <div>Example</div>
</table>
```

Die resultierende DOM-Struktur kann aufgrund des Foster Parenting erheblich von der Quelltextstruktur abweichen.

---

## Scripts, die das Dokument während des Parsings verändern

Beispiel:

```html
<script>
  document.write("<p>Generated</p>");
</script>
```

Das Script verändert den Input Stream, während der Parser arbeitet.

Damit entsteht die zuvor beschriebene Reentrancy zwischen:

- Tokenizer,
- Tree Builder,
- Script Processing.

---

## Fragment Parsing

HTML Fragment Parsing ist ein eigener Parser-Anwendungsfall.

Der aktuelle WHATWG-Algorithmus erhält insbesondere:

- `target`,
- `input`,
- `allowDeclarativeShadowRoots`,
- `scriptingMode`.

Das Ergebnis ist ein `DocumentFragment`.

---

## Fragment Context

Beim Fragment Parsing wird ein Kontext-Element bestimmt.

Der Kontext beeinflusst unter anderem:

- Tokenizer State,
- Insertion Mode,
- Stack of Open Elements,
- Scripting Mode,
- Template-Kontext,
- Foreign-Content-Kontext.

Deshalb ist:

```html
<tr><td>Example</td></tr>
```

nicht unabhängig vom Parsing-Kontext.

---

## Fragment Parsing Initialisierung

Konzeptionell:

```text
Target
  ↓
Context Element
  ↓
Neuer HTML Parser
  ↓
Parser Scripting Mode
  ↓
Tokenizer Initial State
  ↓
Root Element
  ↓
Stack of Open Elements
  ↓
DocumentFragment
```

Der Fragment Parser verwendet ein künstliches `html`-Root-Element für seine interne Tree Construction.

Dieses Root-Element wird nicht einfach als normales Ergebnis des Fragment Parsing zurückgegeben.

---

## Fragment Parsing und Quirks Mode

Beim Fragment Parsing wird der Modus des Kontext-Dokuments berücksichtigt.

Dazu gehören:

- quirks mode,
- limited-quirks mode,
- no-quirks mode.

Der neu erzeugte Parser verwendet diese Informationen entsprechend den Fragment-Parsing-Regeln.

---

## Fragment Scripting Mode

Das Fragment Parsing verwendet einen Parser Scripting Mode.

Der Default ist:

```text
Inert
```

Bestimmte APIs können einen anderen Modus verwenden.

`createContextualFragment()` ist insbesondere mit dem `Fragment`-Scripting Mode verbunden.

---

## Fragment Tokenizer State

Der Kontext kann bestimmen, in welchem Tokenizer State der Fragment Parser startet.

Beispiele:

| Kontext | Tokenizer State |
|---|---|
| `title` | RCDATA |
| `textarea` | RCDATA |
| `style` | RAWTEXT |
| `xmp` | RAWTEXT |
| `iframe` | RAWTEXT |
| `noembed` | RAWTEXT |
| `noframes` | RAWTEXT |
| `script` | Script Data |
| `noscript` bei aktiviertem Scripting | RAWTEXT |
| `plaintext` | PLAINTEXT |
| sonst | Data |

Diese Zuordnung ist ein zentraler Grund dafür, dass Fragment Parsing kontextabhängig ist.

---

## Fragment Root

Beim Fragment Parsing wird ein internes Root-Element erzeugt und auf den Stack of Open Elements gelegt.

Das eigentliche Parsing-Ergebnis wird jedoch in einem `DocumentFragment` gesammelt.

Der Root Insertion Target wird auf dieses Fragment gesetzt.

---

## Fragment Parsing und Templates

Wenn das Kontext-Element ein `template` ist, wird ein entsprechender Template Insertion Mode auf den Template Insertion Mode Stack gelegt.

Damit werden Template Contents auch im Fragment Case nach den dafür vorgesehenen Parserregeln verarbeitet.

---

## `innerHTML`

`innerHTML` verwendet HTML-Fragment-Parsing beim Setzen eines Wertes.

Beispiel:

```js
element.innerHTML = "<p>Hello</p>";
```

Der String wird nicht als bloße Zeichenkette gespeichert.

Er wird als HTML Fragment in den jeweiligen Kontext verarbeitet.

Die anschließende DOM-Struktur hängt vom Kontext-Element ab.

---

## `outerHTML`

`outerHTML` kann beim Setzen ebenfalls HTML-Fragment-Parsing auslösen.

Beim Lesen ist dagegen die HTML-Fragment-Serialisierung relevant.

Deshalb muss zwischen:

```text
outerHTML getter
    → Serialization

outerHTML setter
    → Parsing
```

unterschieden werden.

---

## `insertAdjacentHTML()`

`insertAdjacentHTML()` verwendet HTML-Fragment-Parsing.

Die Einfügeposition beeinflusst den Parsing-Kontext.

Mögliche Positionen:

- `beforebegin`,
- `afterbegin`,
- `beforeend`,
- `afterend`.

Die API selbst ist ein DOM-Interface.

Das Parsing-Modell liefert die zugrunde liegende HTML-Verarbeitung.

---

## Parsing vs. Serialization

Parsing:

```text
HTML String
    ↓
Tokenizer
    ↓
Tree Construction
    ↓
DOM
```

Serialization:

```text
DOM
    ↓
HTML Fragment Serialization
    ↓
HTML String
```

Diese beiden Richtungen sind nicht allgemein verlustfrei invers.

Ein DOM kann serialisiert werden und beim anschließenden erneuten Parsen eine andere Struktur ergeben.

Daher wird Serialization nicht als Unterbereich von `21-parsing.md` dupliziert.

---

## Serialization Boundary

Die WHATWG-Serialisierung umfasst unter anderem:

- Element Serialization,
- Attribute Serialization,
- Text Escaping,
- Comment Serialization,
- DocumentType Serialization,
- ProcessingInstruction Serialization,
- Namespace Serialization,
- Shadow-Root-bezogene Serialization,
- `is`-Wert-Erhaltung.

Diese Regeln gehören zum separaten WHATWG-Bereich `§13.3 Serializing HTML fragments`.

Eine zukünftige ZE-WebLab-Datei für HTML Syntax und Serialization kann diesen Bereich vollständig dokumentieren.

---

## HTML Parsing vs. XML

HTML Parsing darf nicht mit XML Parsing gleichgesetzt werden.

Für `text/html` gilt das HTML-Parsing-Modell.

XML-Ressourcen werden nach dem XML-Syntax-/Parsermodell verarbeitet.

Damit gilt:

```text
text/html
    → HTML parser

XML/XHTML
    → XML parser
```

Die Tatsache, dass HTML und XML ähnliche Markup-Syntax besitzen, ändert daran nichts.

---

## XHTML-Abgrenzung

Der frühere Begriff „XHTML Parsing“ ist als Bezeichnung für den aktuellen WHATWG-Bereich zu vermeiden.

Der aktuelle HTML-Standard führt:

**§13.4 Parsing HTML fragments**

und behandelt XML separat im Bereich der XML-Syntax.

Daher dokumentiert diese Datei keine eigenständige „XHTML Parsing“-Engine.

Sie dokumentiert ausschließlich die Abgrenzung:

- HTML Parsing für `text/html`,
- XML Parsing für XML-Ressourcen.

---

## MIME Type und Parsing

Der MIME Type ist für die Wahl des Parsing-/Verarbeitungsmodells relevant.

Insbesondere gilt:

```text
text/html
    → HTML parser
```

während XML-Ressourcen nach dem XML-Modell verarbeitet werden.

Diese MIME-Type-Abgrenzung ist eine Voraussetzung für die korrekte Interpretation des HTML-Parsing-Modells.

---

## DOM-Erzeugung

Tree Construction erzeugt unter anderem:

- `Document`,
- `DocumentType`,
- `Element`,
- `Text`,
- `Comment`,
- weitere DOM Nodes.

Diese Nodes entstehen über die Parseralgorithmen.

Die interne Parser-Node-Creation ist nicht identisch mit einer vom Entwickler aufgerufenen DOM-API.

---

## Creating an Element

Beim Erzeugen eines Elements können unter anderem berücksichtigt werden:

- Namespace,
- Local Name,
- Custom Element Registry,
- `is` value,
- synchronous/custom element creation,
- Template Context,
- Parser Context.

Die genaue Custom-Elements-Semantik gehört zu `17-custom-elements.md`.

---

## Form Element Pointer und DOM Association

Der Form Element Pointer ist besonders relevant für historisch kompatibles Form Parsing.

Ein Form Control kann dadurch einem `form` zugeordnet werden, das nicht einfach sein nächster DOM-Vorfahre ist.

Das Parsingmodell verwendet hierfür den Parser Pointer.

Das ist eine wichtige Abgrenzung:

```text
DOM ancestry
    ≠
Parser form association
```

---

## Content Categories

Parsing definiert keine neue Content Category.

Content Categories beschreiben Eigenschaften und zulässige strukturelle Beziehungen von Elementen.

Parsing beschreibt dagegen die Verarbeitung des tatsächlichen Eingabestroms.

Ein Parserzustand ist deshalb keine Content Category.

---

## Content Models

Content Models und Parsing sind getrennte Ebenen.

Ein Content Model beschreibt, welche Inhalte konform sind.

Parsing bestimmt, wie ein User Agent tatsächlichen Input verarbeitet.

Daher gilt:

```text
Konformer Content
    ≠
einziger Input des Parsers
```

Der Parser verarbeitet auch nicht-konforme Eingaben nach den definierten Regeln.

---

## Context

Der Begriff „Context“ besitzt in verschiedenen Teilen des HTML-Standards unterschiedliche Bedeutungen.

Im Parsing kann er insbesondere bedeuten:

- Fragment Context Element,
- Namespace-/Foreign-Content-Kontext,
- aktueller Tree-Construction-Kontext,
- Template-Kontext.

Diese Bedeutungen dürfen nicht mit dem Content Model eines Elements verwechselt werden.

---

## Accessibility

Das HTML-Parsing-Modell definiert nicht die vollständige Accessibility-Semantik.

Parsing erzeugt beziehungsweise verändert die DOM-Struktur.

Weitere Plattform- und Accessibility-Mechanismen verwenden diese Struktur.

Accessibility-Regeln sind daher separat zu dokumentieren.

Wenn ein Parseralgorithmus eine besondere DOM-Verarbeitung für ein Element vorsieht, gehört diese konkrete Verarbeitung trotzdem in die Parsing-Dokumentation.

---

## Sanitization

Parsing und Sanitization sind unterschiedliche Verarbeitungsebenen.

Parsing beantwortet:

> Wie wird HTML-Markup in eine DOM-Struktur verarbeitet?

Sanitization beantwortet:

> Welche Inhalte oder Strukturen sollen in einem Bereinigungs-/Sicherheitsprozess erhalten oder entfernt werden?

Eine Parser-Recovery-Regel ist daher keine Sanitization-Regel.

Die Sanitization-Featurefamilie bleibt vollständig getrennt.

---

## Normative Sonderregeln

### Parser-Reparatur

Der HTML-Parser ist kein reiner Validierungsparser.

Viele nicht-konforme Eingaben werden nach definierten Recovery-Regeln verarbeitet.

### Implizite Elemente

Bestimmte Elemente können durch die Tree Construction erzeugt werden, obwohl kein entsprechendes Start-Tag im Quelltext vorhanden ist.

### Implied End Tags

Bestimmte Elemente werden aufgrund des Parserzustands implizit beendet.

### Foster Parenting

Bestimmte Inhalte im Tabellenkontext werden außerhalb der erwarteten Tabellenposition eingefügt.

### Adoption Agency Algorithm

Bestimmte misnested Formatting-Strukturen werden über einen speziellen Algorithmus repariert.

### Foreign Content

SVG und MathML werden über Namespace-, Dispatcher- und Integration-Point-Regeln integriert.

### Custom Elements

Custom Elements können durch die Parser-Elementerzeugung entstehen und mit der Custom-Elements-Infrastruktur interagieren.

---

## Fachliche Abgrenzung zu anderen ZE-WebLab-Dateien

### `17-custom-elements.md`

Dokumentiert:

- Custom Element Definitions,
- Autonomous Custom Elements,
- Customized Built-in Elements,
- Custom Element Registry,
- Reactions,
- Lifecycle-Semantik.

`21-parsing.md` dokumentiert nur die Parser-Integration.

### `19-dom-interfaces-and-apis.md`

Dokumentiert DOM Interfaces und APIs.

`21-parsing.md` beschreibt nur, wenn solche APIs Parsing auslösen oder den Parserzustand beeinflussen.

### `20-sanitization.md`

Dokumentiert Sanitization.

Parsing Recovery ist keine Sanitization.

### `22-svg-mathml-integration.md`

Dokumentiert die vollständige SVG-/MathML-Integrationssystematik.

`21` dokumentiert nur deren Rolle innerhalb der Tree Construction.

### `26-fetching-resources.md`

Dokumentiert Fetching und Ressourcenbeschaffung.

`21` dokumentiert lediglich den Parsing-seitigen Bezug zu speculative fetching.

### `12-scripting.md`

Dokumentiert Scripting.

`21` dokumentiert nur die Parser-/Scripting-Kopplung.

---

## Querverweise

### Parsing ↔ HTML Syntax

Syntax definiert Markupformen.

Parsing verarbeitet den Input Stream.

### Parsing ↔ DOM

Tree Construction erzeugt die resultierende DOM-Struktur.

### Parsing ↔ Custom Elements

Parser-basierte Elementerzeugung kann Custom Element Semantik auslösen.

### Parsing ↔ SVG

SVG wird über Foreign Content in HTML integriert.

### Parsing ↔ MathML

MathML wird über Foreign Content in HTML integriert.

### Parsing ↔ Forms

Form Element Pointer und spezielle Form-Regeln beeinflussen die Tree Construction.

### Parsing ↔ Tables

Tabellen besitzen spezielle Insertion Modes und Foster Parenting.

### Parsing ↔ Templates

Templates besitzen eigene Contents und Template Insertion Modes.

### Parsing ↔ Scripting

Scripts können den Parser pausieren, reentrant aktivieren und den Input Stream verändern.

### Parsing ↔ DOM APIs

`innerHTML`, `outerHTML` und `insertAdjacentHTML()` können HTML Fragment Parsing verwenden.

### Parsing ↔ Fetching

Speculative Parsing kann speculative fetches auslösen.

### Parsing ↔ Document Lifecycle

Stop Parsing ist mit Document Readiness und späteren Lifecycle-Schritten verbunden.

---

## Status / V1

### WHATWG-Status

HTML Parsing ist im aktuellen WHATWG HTML Living Standard normativ definiert.

Die relevanten Regeln umfassen insbesondere:

- Input Byte Stream,
- Character Encoding,
- Preprocessing,
- Parse Errors,
- Parse State,
- Tokenization,
- Tree Construction,
- Foreign Content,
- Fragment Parsing,
- Speculative Parsing,
- Stop Parsing.

### ZE-WebLab-V1

**V1-Einstufung:** Feature-Familie der zweiten Rechercheebene.

**Begründung:** HTML Parsing ist ein eigenständiges Processing Model und kann nicht sinnvoll als Bestandteil einer einzelnen Elementreferenz dokumentiert werden.

### Browser-Kompatibilität

Browser-Kompatibilität ist nicht Bestandteil dieser WHATWG-Statusbewertung.

---

## Prüfstatus

| Prüfbereich | Status |
|---|---|
| §13 The HTML syntax | abgegrenzt |
| §13.1 Writing HTML documents | abgegrenzt |
| §13.2 Parsing HTML documents | geprüft |
| §13.2.1 Overview of the parsing model | geprüft |
| §13.2.2 Parse errors | geprüft |
| §13.2.3 The input byte stream | geprüft |
| Known Character Encoding | geprüft |
| Determining Character Encoding | geprüft |
| Character Encodings | geprüft |
| Changing Encoding While Parsing | geprüft |
| Preprocessing Input Stream | geprüft |
| §13.2.4 Parse state | geprüft |
| Insertion Mode | geprüft |
| Stack of Open Elements | geprüft |
| Scope | geprüft |
| Active Formatting Elements | geprüft |
| Element Pointers | geprüft |
| Other Parsing State Flags | geprüft |
| Root Insertion Target | geprüft |
| Allow Declarative Shadow Roots | geprüft |
| Parser Scripting Mode | geprüft |
| Frameset-Ok Flag | geprüft |
| §13.2.5 Tokenization | geprüft |
| Token Model | geprüft |
| Token Creation / Emission | geprüft |
| Reconsume | geprüft |
| Temporary Buffer | geprüft |
| Return State | geprüft |
| Data State | geprüft |
| RCDATA | geprüft |
| RAWTEXT | geprüft |
| Script Data | geprüft |
| PLAINTEXT | geprüft |
| Tag States | geprüft |
| Attribute States | geprüft |
| Comment States | geprüft |
| DOCTYPE States | geprüft |
| CDATA States | geprüft |
| Processing Instruction States | geprüft |
| Character Reference States | geprüft |
| §13.2.6 Tree Construction | geprüft |
| Creating and Inserting Nodes | geprüft |
| Adjusted Current Node | geprüft |
| Appropriate Place for Inserting a Node | geprüft |
| Implied End Tags | geprüft |
| Insertion Modes | geprüft |
| Active Formatting Reconstruction | geprüft |
| Adoption Agency Algorithm | geprüft |
| Tabellen-Parsing | geprüft |
| Pending Table Character Tokens | geprüft |
| Foster Parenting | geprüft |
| Template Parsing | geprüft |
| Foreign Content | geprüft |
| Integration Points | geprüft |
| SVG Name/Attribute Adjustment | abgegrenzt auf `22` |
| MathML Attribute Adjustment | abgegrenzt auf `22` |
| Foreign Attribute Adjustment | geprüft |
| Custom Elements / Parsing | geprüft |
| Custom Element Reactions | abgegrenzt auf `17` |
| Parser / Scripting Interaction | geprüft |
| Script Nesting Level | geprüft |
| Parser Pause Flag | geprüft |
| Insertion Point | geprüft |
| Speculative HTML Parsing | geprüft |
| Speculative Fetching | geprüft / abgegrenzt auf `26` |
| §13.2.7 The end | geprüft |
| Stop Parsing | geprüft |
| EOF Processing | geprüft |
| §13.2.8 Speculative HTML parsing | geprüft |
| §13.2.9 HTML DOM → Infoset | geprüft |
| §13.2.10 Strange Cases | geprüft |
| §13.3 Serialization | abgegrenzt |
| §13.4 HTML Fragment Parsing | geprüft |
| XML/XHTML-Abgrenzung | geprüft |
| DOM Node Creation | geprüft |
| Accessibility | abgegrenzt |
| Sanitization | abgegrenzt |
| Browser-Kompatibilität | bewusst getrennt |

---

## Offene Punkte

### Separate HTML Syntax / Serialization

Die vollständige HTML-Syntax und die vollständige HTML-Fragment-Serialisierung sind größer als das reine Parsing-Processing-Model.

Insbesondere gehören dazu:

- DOCTYPE Syntax,
- Element Syntax,
- Start Tags,
- End Tags,
- Attribute Syntax,
- Optional Tags,
- Character References,
- CDATA,
- Comments,
- Processing Instructions,
- HTML Fragment Serialization,
- Attribute Serialization,
- Text Escaping,
- Namespace Serialization,
- Shadow-Root Serialization.

Diese Themen sollten in einer späteren eigenen zweiten-Ebenen-Datei zusammengeführt werden.

`21-parsing.md` dokumentiert sie nur insoweit, wie sie für das Parsing-Processing-Model erforderlich sind.

### SVG-/MathML-Details

Die vollständigen SVG-/MathML-Integrationstabellen bleiben in:

`22-svg-mathml-integration.md`

### Custom-Elements-Details

Die vollständige Custom-Elements-Semantik bleibt in:

`17-custom-elements.md`

### Scripting

Die vollständige Script-Semantik bleibt in:

`12-scripting.md`

### Document Lifecycle

Die vollständige Document-Lifecycle-Semantik bleibt einer entsprechenden Lifecycle-Datei vorbehalten.

### Fetching

Die vollständige Fetch-/Resource-Semantik bleibt in:

`26-fetching-resources.md`

---

## Keine neue `30-parsing.md`

Der Parsing-Themenbereich ist mit dieser Datei bereits als:

`docs/html/21-parsing.md`

vorhanden.

Eine zusätzliche `30-parsing.md` würde den bestehenden Themenbereich duplizieren.

Die aktuelle Projektstruktur behandelt Parsing deshalb weiterhin in `21-parsing.md`.

Die Nummerierung des Arbeitsplans ist gegenüber dem tatsächlichen Repository-Bestand nachrangig.

---

## Quellen / Referenzen

### WHATWG HTML Living Standard

**Primärquelle:**

WHATWG HTML Living Standard

**HTML Parsing:**

`§13.2 Parsing HTML documents`

**HTML Syntax:**

`§13 The HTML syntax`

**HTML Fragment Parsing:**

`§13.4 Parsing HTML fragments`

**HTML Fragment Serialization:**

`§13.3 Serializing HTML fragments`

### Relevante WHATWG-Bereiche

- HTML Syntax
- Parsing HTML documents
- Parse Errors
- Input Byte Stream
- Character Encoding
- Parse State
- Tokenization
- Tree Construction
- Foreign Content
- The End
- Speculative HTML Parsing
- HTML DOM Infoset Coercion
- HTML Fragment Serialization
- HTML Fragment Parsing

### ZE-WebLab

**Projekt:** ZE-WebLab

**Zielpfad:** `docs/html/21-parsing.md`

**Custom Elements:** `docs/html/17-custom-elements.md`

**SVG/MathML Integration:** `docs/html/22-svg-mathml-integration.md`

**Fetching Resources:** `docs/html/26-fetching-resources.md`

---

## Fachliche Abgrenzung

Diese Datei dokumentiert **HTML Parsing als übergreifendes Processing Model**.

Nicht als zusätzliche HTML-Elemente gezählt werden:

- Tokenizer States,
- Tokens,
- Tokenizer State Machine,
- Parse State,
- Insertion Modes,
- Stack of Open Elements,
- Active Formatting Elements,
- Element Pointers,
- Parsing State Flags,
- Scope Algorithms,
- Parser Algorithms,
- Adoption Agency Algorithm,
- Foster Parenting,
- Foreign-Content-Regeln,
- Integration Points,
- Fragment-Parsing-Kontexte,
- Custom-Element-Reactions,
- Speculative Parser State.

Diese Konzepte gehören zur zweiten Rechercheebene.

Die native HTML-Elementreferenz der ersten Rechercheebene bleibt davon getrennt.

---

## Zusammenfassung des Feature-Typs

| Merkmal | Einordnung |
|---|---|
| Feature | HTML Parsing |
| Feature-Typ | Parsing Concept / Processing Model |
| WHATWG-Bereich | §13.2 Parsing HTML documents |
| HTML-Element | Nein |
| Content Category | Nein |
| Content Model | Nein |
| Link Type | Nein |
| DOM Interface | Nein |
| API | Nein |
| Processing Model | Ja |
| Parsing Concept | Ja |
| Integration Feature | Ja |
| Custom-Element-Bezug | Ja |
| SVG-Bezug | Ja |
| MathML-Bezug | Ja |
| normative Definition | Ja |
| Browser-Support-Status | separat zu behandeln |

---

## Kurzfassung

HTML Parsing ist ein zustandsbehaftetes Processing Model aus mehreren miteinander gekoppelten Komponenten:

```text
Input Byte Stream
        │
        ▼
Character Encoding
        │
        ▼
Preprocessing
        │
        ▼
Tokenizer State Machine
        │
        ▼
Tokens
        │
        ▼
Tree Construction
        │
        ├── Parse State
        ├── Stack of Open Elements
        ├── Active Formatting Elements
        ├── Element Pointers
        ├── Insertion Modes
        ├── Template State
        ├── Foreign Content
        └── Parser/Scripting State
        │
        ▼
DOM
```

Das Modell ist bewusst fehlertolerant und definiert auch für zahlreiche nicht-konforme HTML-Eingaben konkrete Verarbeitung.

Die wichtigsten strukturellen Parsermechanismen sind:

- Tokenizer State Machine,
- Parse State,
- Stack of Open Elements,
- Scope,
- Active Formatting Elements,
- Reconstruction,
- Adoption Agency Algorithm,
- Insertion Modes,
- Implied End Tags,
- Table Processing,
- Foster Parenting,
- Template Parsing,
- Foreign Content,
- Element Pointers,
- Parser Scripting Modes,
- Speculative HTML Parsing,
- Fragment Parsing.

Damit ist `21-parsing.md` die zentrale ZE-WebLab-Datei für das normative HTML-Parsing-Processing-Model.

Die vollständige HTML-Syntax und Serialization werden bewusst getrennt gehalten.