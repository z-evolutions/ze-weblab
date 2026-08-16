# ZE-WebLab – HTML-Referenz: HTML Parsing

## Arbeitsstand / Quellenstand

**Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Parsing Concept / Processing Model / Normative Concept / Integration Feature

**Zielpfad:** `docs/html/21-parsing.md`

**Normative Primärquelle:** WHATWG HTML Living Standard.

**Relevante Hauptabschnitte:**

- §13 The HTML syntax
- §13.1 Writing HTML documents
- §13.2 Parsing HTML documents
- §13.2.1 Overview of the parsing model
- §13.2.2 The input byte stream
- §13.2.3 Preprocessing the input stream
- §13.2.4 Tokenization
- §13.2.5 Tree construction
- §13.2.6 The end
- §13.2.7 Speculative HTML parsing
- §13.3 Serializing HTML fragments
- §13.4 Parsing XHTML fragments
- §13.5 Parsing HTML fragments
- §13.6 Creating and inserting nodes
- §13.7 Scripting
- §13.8 Events and event loops

**Geprüfter WHATWG-Stand:** Living Standard, zuletzt aktualisiert am 11. August 2026.

**Projekt-/Bestandsquelle:** ZE-WebLab GitHub-Repository, Branch `main`.

**Repository-Abgleich:** `20-custom-elements.md` ist im aktuellen `main`-Stand direkt vorhanden. Die Datei dokumentiert bereits den Zusammenhang zwischen Custom Elements und HTML-Parsing. Parsing wird deshalb hier als eigenständiges, übergreifendes Processing Model dokumentiert und nicht erneut als Unterabschnitt der Custom-Elements-Datei behandelt.

---

## Einordnung

HTML Parsing ist das normative Verarbeitungsmodell, mit dem eine Ressource mit HTML-MIME-Type beziehungsweise HTML-Quelltext in eine DOM-Struktur überführt wird.

Das Parsing-Modell ist nicht lediglich eine Beschreibung der HTML-Syntax.

Es definiert insbesondere:

- Verarbeitung des Eingabebytestroms,
- Zeichendecodierung,
- Vorverarbeitung,
- Tokenisierung,
- Tokenizer States,
- Erzeugung von Tokens,
- Tree Construction,
- Insertion Modes,
- Stack of Open Elements,
- Active Formatting Elements,
- Form Element Pointer,
- Template Insertion Modes,
- Pending Table Character Tokens,
- Frameset-Ok-Flag,
- Scripting Flag,
- Foreign-Content-Verarbeitung,
- SVG- und MathML-Integration,
- Fehlerbehandlung,
- Fragment Parsing,
- Node-Insertion-Algorithmen,
- Interaktion mit Custom Elements,
- Interaktion mit Skripten.

Parsing ist damit ein eigenständiges HTML-Processing Model.

Es ist weder:

- ein HTML-Element,
- eine Content Category,
- ein Content Model,
- ein Link Type,
- ein DOM Interface,
- noch eine API.

---

## WHATWG-Struktur

Die WHATWG-Spezifikation trennt HTML-Syntax und Parsing.

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
- Raw-Text,
- Escapable Raw Text,
- Text,
- Character References,
- CDATA Sections,
- Kommentare,
- Processing Instructions.

### §13.2 Parsing HTML documents

Der Parsing-Bereich beschreibt das normative Parsing-Modell.

Zu den zentralen Unterbereichen gehören:

- Overview of the parsing model
- The input byte stream
- Preprocessing the input stream
- Tokenization
- Tree construction
- The end
- Speculative HTML parsing

Darüber hinaus existieren weitere Parsing- und Serialisierungsbereiche für Fragmente und XHTML.

---

## Abgrenzung Syntax vs. Parsing

HTML-Syntax und HTML-Parsing sind eng verbunden, aber nicht identisch.

### HTML-Syntax

Die Syntax definiert unter anderem, wie HTML-Markup geschrieben wird.

Beispiele:

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

Das Parsing definiert dagegen, wie ein User Agent aus dem Eingabestrom eine DOM-Struktur erzeugt.

Dazu gehören auch Situationen, in denen der Quelltext nicht den idealisierten Authoring-Regeln entspricht.

Damit gilt:

**Syntax beschreibt zulässige bzw. definierte Markupformen.**

**Parsing beschreibt die normative Verarbeitung des Eingabestroms.**

Diese Unterscheidung ist für die ZE-WebLab-Informationsstruktur wesentlich.

---

## Dokumentaufbau

Für HTML-Dokumente definiert §13.1 eine grundlegende Dokumentstruktur.

Ein HTML-Dokument besteht grundsätzlich aus:

1. optionalem BOM,
2. beliebig vielen Kommentaren und ASCII-Whitespace,
3. DOCTYPE,
4. weiteren Kommentaren und ASCII-Whitespace,
5. dem Dokumentelement `html`,
6. anschließendem Kommentar-/Whitespace-Inhalt.

Die Spezifikation weist gleichzeitig darauf hin, dass Whitespace außerhalb des Dokumentelements beim Parsing nicht einfach unverändert an derselben Stelle im DOM verbleibt.

Damit ist die Quelltextstruktur nicht grundsätzlich identisch mit der resultierenden DOM-Struktur.

---

## DOCTYPE

Der HTML-DOCTYPE ist ein definierter Bestandteil der HTML-Syntax.

Die kanonische Form ist:

```html
<!DOCTYPE html>
```

Die Schreibweise ist hinsichtlich ASCII-Groß-/Kleinschreibung entsprechend den WHATWG-Regeln tolerant.

Der DOCTYPE erfüllt insbesondere eine historische Kompatibilitätsfunktion.

Er beeinflusst unter anderem den Rendering-Modus des User Agents.

Für moderne HTML-Dokumente ist die kurze Form

```html
<!DOCTYPE html>
```

die vorgesehene Form.

---

## Elemente und Syntaxklassen

Die HTML-Syntax unterscheidet mehrere Elementtypen:

- Void Elements,
- `template`,
- Raw Text Elements,
- Escapable Raw Text Elements,
- Foreign Elements,
- normale Elemente.

### Void Elements

Void Elements besitzen nur ein Start-Tag und kein End-Tag.

Dazu gehören unter anderem:

- `area`
- `base`
- `br`
- `col`
- `embed`
- `hr`
- `img`
- `input`
- `link`
- `meta`
- `source`
- `track`
- `wbr`

Ein End-Tag für ein Void Element darf nicht verwendet werden.

### Raw Text Elements

Dazu gehören:

- `script`
- `style`

Ihr Inhalt wird unter besonderen Tokenizer-Regeln verarbeitet.

### Escapable Raw Text Elements

Dazu gehören:

- `textarea`
- `title`

Sie erlauben Text und Character References unter den jeweils geltenden Einschränkungen.

### Foreign Elements

Foreign Elements stammen aus insbesondere:

- SVG Namespace,
- MathML Namespace.

Sie werden über das HTML-Parsing-Modell in den jeweiligen Namespace eingeordnet.

---

## Start-Tags

Ein Start-Tag beginnt mit:

```text
<
```

Darauf folgen der Elementname, gegebenenfalls Attribute und abschließend:

```text
>
```

Bei Void Elements beziehungsweise Foreign Elements kann eine Solidus-Syntax auftreten.

Beispiel:

```html
<img src="image.png">
```

Bei Foreign Elements kann eine Self-Closing-Syntax normativ relevant sein.

---

## End-Tags

Ein End-Tag beginnt mit:

```text
</
```

gefolgt vom Elementnamen und dem abschließenden `>`.

Beispiel:

```html
</p>
```

Ob ein End-Tag tatsächlich erforderlich ist, hängt von den Regeln für das konkrete Element ab.

Die Syntax und die Parserverarbeitung sind hierbei getrennt zu betrachten.

---

## Attribute Parsing

Attribute befinden sich innerhalb eines Start-Tags.

Die HTML-Syntax unterstützt insbesondere:

- leere Attributsyntax,
- unquoted attribute value syntax,
- single-quoted attribute value syntax,
- double-quoted attribute value syntax.

Beispiele:

```html
<input disabled>
<input value=yes>
<input type='checkbox'>
<input name="example">
```

Attributnamen sind im HTML-Syntaxmodell ASCII-case-insensitive.

Zwei Attribute auf demselben Start-Tag dürfen nicht denselben Attributnamen im ASCII-case-insensitiven Sinn besitzen.

---

## Duplicate Attributes

Die Syntax erlaubt nicht mehrere Attribute desselben Namens auf einem Start-Tag.

Das Parsing-Modell behandelt entsprechende Eingaben dennoch nach seinen definierten Tokenizer-Regeln.

Daraus folgt eine wichtige Trennung:

- Konformitätsregeln bestimmen, ob der Quelltext konform ist.
- Der Parser bestimmt, wie der Eingabestrom verarbeitet wird.

Ein nicht-konformes Dokument kann daher trotzdem ein definiertes Parsing-Ergebnis besitzen.

---

## Tokenization

Die Tokenisierung ist die erste zentrale Stufe des HTML-Parsers.

Der Tokenizer verarbeitet den Eingabestrom und erzeugt Tokens.

Zu den zentralen Tokenarten gehören:

- DOCTYPE Tokens,
- Start Tag Tokens,
- End Tag Tokens,
- Comment Tokens,
- Character Tokens,
- End-of-file Token.

Der Tokenizer arbeitet mit einem Zustandsautomaten.

---

## Tokenizer States

Der HTML-Tokenizer besitzt zahlreiche Zustände.

Dazu gehören unter anderem:

- Data state,
- Character reference state,
- RCDATA state,
- RAWTEXT state,
- Script data state,
- Plaintext state,
- Tag open state,
- End tag open state,
- Tag name state,
- Before attribute name state,
- Attribute name state,
- Before attribute value state,
- Attribute value (double-quoted) state,
- Attribute value (single-quoted) state,
- Attribute value (unquoted) state,
- Self-closing start tag state,
- Bogus comment state,
- DOCTYPE states.

Darüber hinaus existieren weitere spezialisierte Zustände insbesondere für:

- Script Data,
- Character References,
- CDATA,
- Escapes,
- Foreign Content.

---

## Character References

Character References ermöglichen die Darstellung bestimmter Zeichen über HTML-Referenzen.

Beispiele:

```html
&amp;
&lt;
&gt;
&quot;
```

Der Tokenizer besitzt dafür eigene Character-Reference-Zustände.

Die Verarbeitung ist kontextabhängig.

Insbesondere Raw-Text- und bestimmte andere Parserzustände behandeln Character References unterschiedlich.

---

## Kommentare

HTML-Kommentare werden über eigene Tokenizer-Regeln verarbeitet.

Beispiel:

```html
<!-- comment -->
```

Der Parser erzeugt daraus ein Comment Token und anschließend einen entsprechenden DOM-Comment-Node.

Nicht jede beliebige Zeichenfolge, die wie ein Kommentar aussieht, ist hinsichtlich Konformität und Parsing identisch.

Die Fehlerbehandlung ist Teil des Tokenizer-Modells.

---

## DOCTYPE Token

Der Tokenizer erzeugt ein DOCTYPE Token.

Dieses Token enthält Informationen über den DOCTYPE und kann insbesondere den Quirks- bzw. No-Quirks-Status beeinflussen.

Die Verarbeitung des DOCTYPE ist deshalb sowohl:

- ein Syntaxkonzept,
- als auch ein Parsing-/Dokumentverarbeitungsfeature.

---

## Tree Construction

Nach der Tokenisierung werden Tokens von der Tree-Construction-Stufe verarbeitet.

Die Tree Construction:

- erzeugt DOM-Nodes,
- fügt Nodes in den DOM-Baum ein,
- verwaltet offene Elemente,
- verarbeitet verschiedene Insertion Modes,
- führt Parser-Reparaturregeln aus,
- verarbeitet Templates,
- behandelt Foreign Content,
- berücksichtigt bestimmte Form- und Formatting-Strukturen.

Die Tree Construction ist damit nicht bloß eine einfache Abbildung:

```text
Token → DOM Node
```

Sie enthält ein umfangreiches zustandsabhängiges Processing Model.

---

## Stack of Open Elements

Der Stack of Open Elements ist eine zentrale interne Datenstruktur des Tree Builders.

Er repräsentiert die aktuell offenen Elemente des Parsing-Kontexts.

Der Stack wird unter anderem verwendet für:

- Prüfung des aktuellen Elements,
- Ermittlung des aktuellen Parsing-Kontexts,
- Schließen von Elementen,
- implied end tags,
- Insertion Modes,
- spezielle Reparaturalgorithmen.

Der Stack ist kein DOM-API-Objekt.

Er ist eine interne Datenstruktur des normativen Parsing-Modells.

---

## Current Node

Der Current Node ist das Element, das am oberen Ende des Stack of Open Elements liegt.

Der Current Node ist für zahlreiche Parsing-Entscheidungen relevant.

Er ist nicht mit dem zuletzt erzeugten DOM-Node gleichzusetzen.

---

## Adjusted Current Node

Bei Template-Inhalten kann der sogenannte Adjusted Current Node relevant werden.

Damit kann der Parser einen abweichenden Parsing-Kontext bestimmen, insbesondere wenn Template Contents verarbeitet werden.

Dieses Konzept gehört zum internen Tree-Construction-Modell.

---

## Active Formatting Elements

Der Parser verwaltet zusätzlich eine Liste der Active Formatting Elements.

Sie ist insbesondere für die Behandlung von Formatting-Elementen und bestimmten fehlerhaften bzw. verschachtelten Markupstrukturen relevant.

Das Modell ermöglicht unter anderem die Anwendung des Adoption Agency Algorithm.

Die Active Formatting Elements sind eine interne Parserdatenstruktur und keine Content Category.

---

## Adoption Agency Algorithm

Der Adoption Agency Algorithm behandelt bestimmte problematische Verschachtelungen von Formatting Elements.

Er ist ein bewusst definiertes Reparaturverfahren des HTML-Parsers.

Das Parsing-Modell ist deshalb nicht als strikt XML-artiger Stack-Parser zu verstehen.

Beispielhafte Problemklasse:

```html
<b><i>text</b>more</i>
```

Das konkrete Parsing-Ergebnis wird durch den normativen Tree-Construction-Algorithmus bestimmt.

---

## Insertion Modes

Der Tree Builder arbeitet mit Insertion Modes.

Zu den relevanten Zuständen gehören unter anderem:

- initial,
- before html,
- before head,
- in head,
- in head noscript,
- after head,
- in body,
- text,
- in table,
- in table text,
- in caption,
- in column group,
- in table body,
- in row,
- in cell,
- in select,
- in select in table,
- in template,
- after body,
- in frameset,
- after frameset,
- after after body,
- after after frameset.

Die jeweils aktive Insertion Mode bestimmt, wie das nächste Token verarbeitet wird.

---

## Initial Mode

Beim Beginn des Parsing-Prozesses befindet sich der Tree Builder im initialen Zustand.

DOCTYPE-Tokens und bestimmte Whitespace-/Comment-Situationen werden dort entsprechend den normativen Regeln verarbeitet.

Anschließend wechselt der Parser in weitere Insertion Modes.

---

## Before HTML

Der Parser verarbeitet in diesem Zustand insbesondere Tokens, die vor dem eigentlichen `html`-Element auftreten.

Bei Bedarf wird das `html`-Element implizit erzeugt.

Damit kann der Parser auch Eingaben verarbeiten, in denen das `html`-Start-Tag nicht explizit geschrieben wurde.

---

## In Head

Im `head`-Kontext werden unter anderem Elemente wie:

- `base`,
- `basefont`,
- `bgsound`,
- `link`,
- `meta`,
- `title`,
- `noscript`,
- `noframes`,
- `style`,
- `template`

entsprechend den jeweiligen Regeln verarbeitet.

Das Parsing-Verhalten hängt nicht ausschließlich vom Elementnamen ab, sondern auch vom aktuellen Insertion Mode.

---

## In Body

Der Insertion Mode `in body` verarbeitet einen großen Teil des normalen HTML-Inhalts.

Dabei existieren spezielle Regeln für:

- Paragraphen,
- Heading Elements,
- Formatting Elements,
- Lists,
- Links,
- Embedded Content,
- Tables,
- Forms,
- Scripts,
- Templates,
- Custom Elements.

---

## Implied End Tags

Das Parsing-Modell kennt Fälle, in denen End-Tags impliziert werden.

Beispielsweise kann das Starten bestimmter Elemente dazu führen, dass ein vorheriges Element automatisch geschlossen wird.

Das ist Teil des Tree-Construction-Modells und darf nicht mit den Authoring-Regeln für optionale End-Tags gleichgesetzt werden.

---

## Optional Tags vs. Implied End Tags

Diese Begriffe müssen getrennt behandelt werden.

### Optional Tag

Ein optionales Tag ist eine syntaktische Eigenschaft eines Elements.

### Implied End Tag

Ein implied end tag ist eine interne Parseroperation bzw. Parserregel.

Ein Element kann daher im Quelltext ohne End-Tag erscheinen und gleichzeitig der Parser aufgrund seiner Tree-Construction-Regeln einen Abschlusszustand erzeugen.

---

## Tables

Tabellen besitzen im HTML-Parser ein umfangreiches eigenes Processing Model.

Relevante Insertion Modes umfassen unter anderem:

- in table,
- in table text,
- in caption,
- in column group,
- in table body,
- in row,
- in cell.

Der Parser besitzt außerdem spezielle Regeln für:

- Foster Parenting,
- Tabellenkontext,
- Character Tokens,
- Fehlermarkup.

---

## Foster Parenting

Foster Parenting ist ein spezielles HTML-Parsing-Verfahren für bestimmte Inhalte im Tabellenkontext.

Wenn Inhalte an einer Stelle auftreten, an der sie im aktuellen Tabellenkontext nicht zulässig sind, können sie nach den Tree-Construction-Regeln außerhalb der Tabelle eingefügt werden.

Dies ist eine zentrale Ursache dafür, dass Quelltextreihenfolge und resultierende DOM-Struktur bei fehlerhaftem Tabellen-Markup voneinander abweichen können.

---

## Templates

`template` besitzt ein eigenes Parsing-Modell.

Template Contents sind nicht einfach normale Child Nodes des `template`-Elements.

Die Spezifikation verwendet hierfür einen separaten Template-Inhaltskontext.

Relevante Parserkonzepte sind:

- Template Contents Owner Document,
- Template Insertion Modes,
- Template Insertion Mode Stack,
- Template Contents.

Das `template`-Element ist deshalb eine besondere Parsing-Klasse.

---

## Foreign Content

HTML Parsing integriert Inhalte aus anderen XML-basierten Vokabularen.

Relevant sind insbesondere:

- SVG,
- MathML.

Diese Elemente werden als Foreign Elements verarbeitet.

Der Parser wechselt abhängig vom Kontext zwischen HTML- und Foreign-Content-Regeln.

---

## SVG Integration

SVG wird über den SVG Namespace in HTML integriert.

Beispiel:

```html
<svg>
  <circle cx="50" cy="50" r="40"></circle>
</svg>
```

Der Parser muss hierbei erkennen, dass `svg` und die darin enthaltenen relevanten Elemente nicht im HTML Namespace liegen.

Die HTML-Syntax unterstützt keine frei definierbaren XML-Namespace-Deklarationen.

Ein Attribut wie:

```html
xmlns:foo="..."
```

ändert im HTML-Parsing nicht beliebig den Namespace eines Elements.

---

## MathML Integration

MathML wird ebenfalls über einen Foreign Namespace in HTML integriert.

Beispiel:

```html
<math>
  <mi>x</mi>
  <mo>=</mo>
  <mn>1</mn>
</math>
```

Der HTML-Parser besitzt dafür eigene Foreign-Content- und Integration-Point-Regeln.

---

## Integration Points

Für Foreign Content existieren spezielle Integration Points.

Diese bestimmen unter anderem, wann HTML-Parsing-Regeln innerhalb von SVG- oder MathML-Strukturen wieder relevant werden.

Damit kann ein Baum beispielsweise zwischen:

```text
HTML
  ↓
SVG
  ↓
HTML integration point
  ↓
HTML
```

wechseln.

Die Integration Points sind ein normatives Parsing-Konzept.

---

## Adjusted Attributes

Bei Foreign Content können Attribute hinsichtlich Namespace und Namen angepasst werden.

Insbesondere existieren definierte Zuordnungen für:

- XML Namespace,
- XMLNS Namespace,
- XLink Namespace.

Die HTML-Syntax verwendet hierfür spezifizierte Attributnamen wie:

```text
xlink:href
xml:lang
xmlns
```

Die HTML-Parserregeln bestimmen anschließend die tatsächlichen Namespace-/Local-Name-Eigenschaften im DOM.

---

## Foreign Attribute Adjustment

Der Parser kann bei Foreign Elements bestimmte Attribute entsprechend den Foreign-Content-Regeln anpassen.

Damit wird die HTML-Syntax in eine DOM-Struktur überführt, die die Namespace-Anforderungen von SVG und MathML berücksichtigt.

Dies ist ein Parsing-/Integrationskonzept und keine allgemeine Attributfamilie der ersten Ebene.

---

## Character Tokens im Foreign Content

Character Tokens werden innerhalb von Foreign Content abhängig vom aktuellen Kontext verarbeitet.

Insbesondere können Whitespace und bestimmte andere Character Tokens die Tree Construction unterschiedlich beeinflussen.

Der Parser entscheidet anhand des aktuellen Foreign-Content-Kontexts, ob HTML- oder Foreign-Content-Regeln angewendet werden.

---

## Custom Elements und Parsing

Custom Elements sind direkt mit der Tree Construction verbunden.

Der Parser kann:

- ein autonomes Custom Element erkennen,
- ein noch nicht definiertes Custom Element erzeugen,
- eine registrierte Definition berücksichtigen,
- customized built-in elements anhand des `is`-Mechanismus verarbeiten.

Damit ist Parsing ein wesentlicher Bestandteil der Custom-Elements-Featurefamilie.

Die detaillierte Custom-Elements-Semantik ist in `20-custom-elements.md` dokumentiert.

---

## Scripting Flag

Das Parsing-Modell verwendet ein Scripting Flag.

Dieses beeinflusst unter anderem die Behandlung bestimmter Elemente und Parserzustände.

Das Scripting Flag ist nicht identisch mit der bloßen Existenz eines `<script>`-Elements.

Es ist ein interner Zustand des Parsing-Modells.

---

## Parser-Insertion und Scripts

Skripte können den Parsing-Ablauf beeinflussen.

Insbesondere können klassische Scripts, die vom Parser verarbeitet werden, den Parser anhalten bzw. die weitere Verarbeitung von der Ausführung des Scripts abhängig machen.

Dies führt zu einer engen Beziehung zwischen:

- Tokenization,
- Tree Construction,
- Script Processing,
- DOM,
- Event Loop.

Die konkreten Regeln sind im WHATWG-Parsing- und Scripting-Modell festgelegt.

---

## Parser-Insertion Mode und Script Execution

Die Verarbeitung eines Script-Tokens kann dazu führen, dass:

1. das Script-Element erzeugt wird,
2. das Element in den DOM eingefügt wird,
3. der Script-Verarbeitungsschritt erfolgt,
4. der Parser gegebenenfalls angehalten wird,
5. nach Abschluss der relevanten Verarbeitung das Parsing fortgesetzt wird.

Das genaue Verhalten hängt vom Script-Typ und den jeweiligen Scripting-Regeln ab.

---

## Speculative HTML Parsing

Die WHATWG-Spezifikation beschreibt speculative HTML parsing als Optimierungsmechanismus.

Dabei kann ein User Agent Parsing-Arbeit spekulativ vorwegnehmen, während die normale Parserverarbeitung durch ein Script blockiert ist.

Dieses Verfahren darf nicht mit dem normativen DOM-Ergebnis gleichgesetzt werden.

Es ist eine User-Agent-Verarbeitung innerhalb des spezifizierten Modells und kein alternatives HTML-Syntaxmodell.

---

## Error Handling

HTML Parsing ist bewusst fehlertolerant.

Ein nicht-konformer HTML-Quelltext führt nicht automatisch zu einem Parserabbruch.

Stattdessen definieren die Parsing-Algorithmen für viele fehlerhafte Situationen ein bestimmtes Verhalten.

Wichtig ist daher die Unterscheidung:

```text
Konformität des Quelltexts
        ≠
Existenz eines Parsing-Ergebnisses
```

Ein Dokument kann nicht konform sein und trotzdem ein deterministisch beschriebenes DOM-Ergebnis erzeugen.

---

## Parse Errors

Das Parsing-Modell kennt Parsing-Fehler.

Ein Parse Error bedeutet nicht grundsätzlich:

- Abbruch,
- Exception,
- ungültiges DOM,
- fehlende Verarbeitung.

Stattdessen wird der Parser nach den jeweiligen Recovery-Regeln fortgesetzt.

Die normative Fehlerbehandlung ist ein wesentlicher Teil des HTML-Parsing-Modells.

---

## End-of-file

Der Parser erzeugt beziehungsweise verarbeitet ein End-of-file Token.

Die Verarbeitung des EOF hängt vom aktuellen Parsing-Kontext und Insertion Mode ab.

Bei bestimmten offenen Strukturen können vor dem endgültigen Ende weitere Tree-Construction-Schritte erforderlich sein.

EOF ist daher nicht einfach ein unmittelbares „Stop Parsing“.

---

## Fragment Parsing

HTML-Fragmente können separat geparst werden.

Das ist insbesondere relevant für DOM-APIs wie:

- `innerHTML`,
- `outerHTML`,
- `insertAdjacentHTML`,
- fragmentbezogene Parsing-Algorithmen.

Beim Fragment Parsing ist ein Kontext-Element relevant.

Das Parsing-Ergebnis hängt deshalb vom Kontext ab.

---

## Kontextabhängiges Fragment Parsing

Das Parsen von:

```html
<tr><td>Example</td></tr>
```

ist beispielsweise nicht dasselbe wie das Parsen derselben Zeichenfolge als gewöhnlicher Dokumentinhalt.

Der Kontext bestimmt unter anderem:

- Initialisierung des Tree Builders,
- Stack of Open Elements,
- Insertion Mode,
- Scripting Flag,
- Template-Kontext,
- Foreign-Content-Kontext.

Fragment Parsing ist deshalb ein eigenständiger Parsing-Anwendungsfall.

---

## `innerHTML`

`innerHTML` verwendet die HTML-Parsing- und Serialisierungsmechanismen.

Beim Setzen:

```js
element.innerHTML = "<p>Hello</p>";
```

wird der angegebene String nach dem HTML-Fragment-Parsing-Modell verarbeitet.

Das Ergebnis ist eine DOM-Struktur.

Damit ist `innerHTML` nicht einfach eine Zeichenkettenzuweisung.

---

## `outerHTML`

`outerHTML` verwendet Parsing- und Serialisierungsmechanismen.

Beim Setzen von `outerHTML` wird die angegebene Zeichenfolge als HTML verarbeitet und in den relevanten DOM-Kontext eingefügt.

Die genaue Verarbeitung hängt vom Elementtyp und seinem Kontext ab.

---

## `insertAdjacentHTML()`

`insertAdjacentHTML()` ist ebenfalls an HTML-Fragment-Parsing gebunden.

Die Einfügeposition beeinflusst den Parsing-Kontext.

Die möglichen Positionen sind:

- `beforebegin`,
- `afterbegin`,
- `beforeend`,
- `afterend`.

Damit ist auch diese API Teil des größeren HTML-Parsing-Ökosystems.

---

## XHTML Parsing

HTML und XHTML dürfen nicht als identisches Parsing-Modell behandelt werden.

Die HTML-Syntax gilt für Ressourcen mit HTML MIME Type.

XML/XHTML-Ressourcen werden nach XML-Regeln verarbeitet.

Die WHATWG-Spezifikation trennt deshalb:

- HTML syntax,
- XML syntax.

Das HTML-Parsing-Modell darf nicht auf XHTML-Ressourcen übertragen werden.

---

## MIME Type und Parsing

Der MIME Type beeinflusst, welches Parsing-/Verarbeitungsmodell angewendet wird.

Die HTML-Syntax-Regeln gelten ausdrücklich für Ressourcen mit HTML MIME Type.

XML-Ressourcen werden nach XML-Regeln verarbeitet.

Diese Unterscheidung ist für die Dokumentation von HTML Parsing wesentlich.

---

## DOM-Erzeugung

Tree Construction erzeugt und fügt DOM-Nodes ein.

Dazu gehören unter anderem:

- Document,
- DocumentType,
- Element,
- Text,
- Comment.

Das Parsing-Modell verwendet dafür spezifizierte Node-Creation- und Insertion-Algorithmen.

Diese internen Algorithmen sind von den öffentlichen DOM-APIs zu unterscheiden.

---

## Creating and Inserting Nodes

Die WHATWG-Spezifikation beschreibt eigene Algorithmen für die Erzeugung und Einfügung von Nodes.

Dabei können unter anderem berücksichtigt werden:

- Custom Elements,
- CE-Reactions,
- Shadow Roots,
- Template Contents,
- Document Type,
- Form-associated Elemente,
- DOM-Struktur.

Die Node-Erzeugung ist deshalb nicht vollständig mit `document.createElement()` gleichzusetzen.

---

## Custom Element Reactions während des Parsings

Das Parsing kann Custom-Element-Reactions auslösen.

Die Reactions werden entsprechend dem Custom-Elements-Processing-Modell verarbeitet.

Damit bestehen folgende Querverbindungen:

```text
HTML Tokenizer
      ↓
Tree Construction
      ↓
Element Creation
      ↓
Custom Element Definition
      ↓
Custom Element Reactions
      ↓
DOM
```

Die Details des Custom-Element-Reaction-Modells sind in `20-custom-elements.md` dokumentiert.

---

## Content Categories

Parsing definiert keine neue Content Category.

Content Categories beeinflussen die zulässige Struktur und semantische Einordnung von Elementen, während Parsing die konkrete Verarbeitung des Eingabestroms bestimmt.

Ein Parserzustand ist daher nicht mit einer Content Category gleichzusetzen.

---

## Content Models

Content Models und Parsing sind ebenfalls getrennte Ebenen.

Das Content Model eines Elements beschreibt, welche Inhalte dort konform sind.

Das Parsing-Modell bestimmt dagegen, wie der User Agent den tatsächlichen Eingabestrom verarbeitet.

Daher kann nicht aus einem Parsing-Ergebnis rückwirkend geschlossen werden, dass der Quelltext konform zum Content Model war.

---

## Context

Der Begriff Context besitzt im Parsing eine andere Funktion als in einer Elementdefinition.

Beim Fragment Parsing kann ein Kontext-Element die Tree Construction bestimmen.

Bei Foreign Content bestimmen Namespace und Integration Points den Parsing-Kontext.

Beim normalen Dokumentparsing bestimmen Insertion Mode und Stack of Open Elements den internen Zustand.

Diese verschiedenen Bedeutungen dürfen nicht zusammengeführt werden.

---

## Accessibility

Das HTML-Parsing-Modell definiert nicht die vollständige Accessibility-Semantik eines Dokuments.

Parsing erzeugt die DOM-Struktur, auf deren Grundlage weitere Plattform- und Accessibility-Mechanismen arbeiten.

Accessibility-Regeln sind deshalb separat zu dokumentieren.

Wenn die WHATWG Parsing-Spezifikation für ein bestimmtes Element eine spezielle DOM-/Parsing-Verarbeitung vorsieht, ist diese als Parsing-Regel zu dokumentieren und nicht als eigenständige Accessibility-Regel auszugeben.

---

## Sanitization

HTML Parsing und Sanitization sind unterschiedliche Verarbeitungsebenen.

Parsing beantwortet:

> Wie wird HTML-Markup in eine DOM-Struktur verarbeitet?

Sanitization beantwortet:

> Welche Inhalte oder Strukturen dürfen bei einer Sicherheits-/Bereinigungsverarbeitung erhalten bleiben oder entfernt werden?

Eine Sanitization-Regel darf daher nicht aus einer Parsing-Recovery-Regel abgeleitet werden.

Für die Sanitization-Featurefamilie ist eine separate WHATWG-Recherche erforderlich.

---

## Status / V1

### WHATWG-Status

HTML Parsing ist im aktuellen WHATWG HTML Living Standard normativ definiert.

Die relevanten Regeln umfassen sowohl:

- Syntaxdefinitionen,
- Tokenization,
- Tree Construction,
- Fragment Parsing,
- Foreign Content,
- Node-Insertion,
- Scripting-Integration,
- Fehlerbehandlung.

### ZE-WebLab-V1

**V1-Einstufung:** Feature-Familie der zweiten Rechercheebene.

**Begründung:** Parsing ist ein eigenständiges Processing Model und kann nicht sinnvoll als Bestandteil einer einzelnen Elementreferenz dokumentiert werden.

### Browser-Kompatibilität

Browser-Kompatibilität ist nicht Bestandteil dieser Statusbewertung.

---

## Querverweise

### Parsing ↔ HTML Syntax

Die Syntax definiert die Eingabeformen; Parsing verarbeitet den Eingabestrom.

### Parsing ↔ DOM

Tree Construction erzeugt die resultierende DOM-Struktur.

### Parsing ↔ Custom Elements

Custom-Element-Erzeugung und Upgrades sind mit Parsing verbunden.

### Parsing ↔ SVG

SVG wird als Foreign Content integriert.

### Parsing ↔ MathML

MathML wird als Foreign Content integriert.

### Parsing ↔ Content Models

Content Models definieren Konformitätsanforderungen; Parsing verarbeitet auch nicht-konforme Eingaben.

### Parsing ↔ Forms

Bestimmte Form-Elemente besitzen besondere Tree-Construction-Regeln.

### Parsing ↔ Tables

Tabellen besitzen umfangreiche spezielle Insertion Modes und Reparaturalgorithmen.

### Parsing ↔ Templates

`template` besitzt eigene Template Contents und spezielle Parsing-Regeln.

### Parsing ↔ Scripting

Script-Verarbeitung kann den Parser beeinflussen.

### Parsing ↔ DOM APIs

`innerHTML`, `outerHTML` und `insertAdjacentHTML()` verwenden Fragment-Parsing-Mechanismen.

---

## Normative Sonderregeln

### Parser-Reparatur

Der HTML-Parser ist kein reiner Validierungsparser.

Viele nicht-konforme Eingaben werden nach definierten Recovery-Regeln verarbeitet.

### Implizite Elemente

Bestimmte Elemente können durch den Parser erzeugt werden, obwohl sie im Quelltext nicht explizit geschrieben wurden.

### Implied End Tags

Bestimmte Elemente können aufgrund des Parsing-Zustands implizit beendet werden.

### Foster Parenting

Bestimmte Inhalte im Tabellenkontext werden nach speziellen Regeln außerhalb der erwarteten Tabellenposition eingefügt.

### Adoption Agency Algorithm

Bestimmte verschachtelte Formatting-Strukturen werden durch einen speziellen Reparaturalgorithmus verarbeitet.

### Foreign Content

SVG und MathML werden über Namespace- und Integration-Point-Regeln integriert.

### Custom Elements

Custom Elements können vor ihrer Definition erzeugt und später upgraded werden.

---

## Prüfstatus

| Prüfbereich | Status |
|---|---|
| §13 The HTML syntax | geprüft |
| §13.1 Writing HTML documents | geprüft |
| §13.1.1 DOCTYPE | geprüft |
| §13.1.2 Elements | geprüft |
| Start Tags | geprüft |
| End Tags | geprüft |
| Attribute Syntax | geprüft |
| Optional Tags | abgegrenzt |
| Character References | geprüft |
| CDATA Sections | abgegrenzt |
| Kommentare | geprüft |
| §13.2 Parsing HTML documents | geprüft |
| Input Byte Stream | geprüft |
| Preprocessing | geprüft |
| Tokenization | geprüft |
| Tokenizer States | geprüft |
| Tree Construction | geprüft |
| Stack of Open Elements | geprüft |
| Active Formatting Elements | geprüft |
| Insertion Modes | geprüft |
| Implied End Tags | geprüft |
| Adoption Agency Algorithm | geprüft |
| Tabellen-Parsing | geprüft |
| Foster Parenting | geprüft |
| Template Parsing | geprüft |
| Foreign Content | geprüft |
| SVG Integration | geprüft |
| MathML Integration | geprüft |
| Integration Points | geprüft |
| Attribute Adjustment | geprüft |
| Custom Elements / Parsing | geprüft |
| Scripting Flag | geprüft |
| Speculative HTML Parsing | geprüft |
| EOF Processing | geprüft |
| Fragment Parsing | geprüft |
| XHTML-Abgrenzung | geprüft |
| DOM Node Creation | geprüft |
| Accessibility | abgegrenzt |
| Sanitization | abgegrenzt |
| Browser-Kompatibilität | bewusst getrennt |
| Custom-Element-Detaildefinition | Querverweis auf `20-custom-elements.md` |

---

## Offene Punkte

### Separate Syntax-Datei

Die vollständige HTML-Syntax ist größer als das reine Parsing-Processing-Model.

Insbesondere:

- DOCTYPE,
- Start-/End-Tags,
- Attribute,
- Character References,
- CDATA,
- Kommentare,
- optionale Tags

könnten in einer späteren zweiten-Ebenen-Datei `22-html-syntax.md` als eigenständige Featurefamilie dokumentiert werden.

Diese Entscheidung sollte anhand des tatsächlichen weiteren Repository-Bestands und der bereits vorhandenen Datei Nr. 19 getroffen werden.

### Separate SVG-/MathML-Integrationsdateien

SVG- und MathML-Integration sind zwar Bestandteil des Parsing-Modells, bilden aber zugleich eigenständige übergreifende Integration Features.

Die aktuelle Datei dokumentiert deren Parsing-Aspekt.

Eine spätere Datei kann die vollständige Integrationssystematik getrennt behandeln.

### Separate Sanitization-Datei

Sanitization ist nicht Bestandteil dieser Parsing-Datei.

Eine eigenständige zweite-Ebenen-Recherche sollte die aktuellen Sanitization-Regeln und APIs separat prüfen.

### Separate Scripting-/Parser-Interaktion

Die Interaktion zwischen Parser und Script-Ausführung reicht über reines Parsing hinaus.

Sie ist mit dem Scripting-Modell und den entsprechenden APIs zu verknüpfen.

---

## Quellen / Referenzen

### WHATWG HTML Living Standard

**Primärquelle:**

https://html.spec.whatwg.org/multipage/

**HTML Syntax:**

https://html.spec.whatwg.org/multipage/syntax.html

**Parsing HTML documents:**

https://html.spec.whatwg.org/multipage/parsing.html

Relevante normative Bereiche:

- §13 The HTML syntax
- §13.1 Writing HTML documents
- §13.2 Parsing HTML documents
- §13.3 Serializing HTML fragments
- §13.4 Parsing XHTML fragments
- §13.5 Parsing HTML fragments
- §13.6 Creating and inserting nodes
- §13.7 Scripting
- §13.8 Events and event loops

### ZE-WebLab

**Projekt-/Bestandsquelle:**

https://github.com/z-evolutions/ze-weblab

**HTML-Dokumentationsverzeichnis:**

https://github.com/z-evolutions/ze-weblab/tree/main/docs/html

**Vorherige zweite-Ebenen-Datei:**

https://github.com/z-evolutions/ze-weblab/blob/main/docs/html/20-custom-elements.md

Die Repository-Quelle dient der Bestandsprüfung des Projekts.

Die WHATWG HTML Living Standard bleibt die normative Primärquelle.

---

## Fachliche Abgrenzung

Diese Datei dokumentiert **HTML Parsing als übergreifendes Processing Model**.

Nicht als zusätzliche Elemente gezählt werden:

- Tokenizer States,
- Tokens,
- Insertion Modes,
- Stack of Open Elements,
- Active Formatting Elements,
- Parsing Flags,
- Parser Algorithms,
- Adoption Agency Algorithm,
- Foster Parenting,
- Foreign-Content-Regeln,
- Integration Points,
- Fragment-Parsing-Kontexte,
- Custom-Element-Reactions.

Diese Konzepte gehören zur zweiten Rechercheebene.

Die native HTML-Elementreferenz der ersten Rechercheebene bleibt davon getrennt.

---

## Zusammenfassung des Feature-Typs

| Merkmal | Einordnung |
|---|---|
| Feature | HTML Parsing |
| Feature-Typ | Parsing Concept / Processing Model |
| WHATWG-Bereich | §13 The HTML syntax / §13.2 Parsing HTML documents |
| HTML-Element | Nein |
| Content Category | Nein |
| Content Model | Nein |
| Link Type | Nein |
| DOM Interface | Nein |
| API | Nein, aber mehrere APIs verwenden Parsing |
| Processing Model | Ja |
| Parsing Concept | Ja |
| Integration Feature | Ja |
| Custom-Element-Bezug | Ja |
| SVG-Bezug | Ja |
| MathML-Bezug | Ja |
| normative Definition | Ja |
| Browser-Support-Status | separat zu behandeln |