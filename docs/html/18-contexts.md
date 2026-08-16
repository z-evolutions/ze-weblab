# ZE-WebLab – HTML-Referenz: Contexts

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab

**Datei:** `docs/html/18-contexts.md`

**Rechercheebene:** Zweite Rechercheebene – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Context / normative Informationsdimension der Elementdefinition

**Normative Primärquelle:** WHATWG HTML Living Standard

**Maßgeblicher WHATWG-Bereich:**

- §3.2.4 Element definitions
- §3.2.5 Content models
- die jeweiligen Elementdefinitionen in §4
- ergänzend die Definitionen für Custom Elements in §4.13

**Geprüfter Spezifikationsstand:** aktuelle WHATWG HTML Living Standard, August 2026

**Projektquelle:** ZE-WebLab, bestehende HTML-Elementreferenz und zweite Rechercheebene

**Browser-Kompatibilität:** nicht Bestandteil der WHATWG-Statusbewertung

**V1-Status:** projektspezifisch; nicht mit dem WHATWG-Status gleichzusetzen

**Prüfstatus:** vollständig recherchiert für die übergreifende Context-Systematik

---

## Quellenabgrenzung

Die WHATWG HTML Living Standard ist die normative Primärquelle für:

- die Definition des Begriffs „Contexts in which this element can be used“
- die zulässigen Verwendungskontexte einzelner HTML-Elemente
- die Beziehung zwischen Context-Angabe und Content Models
- spezielle strukturelle Verwendungskontexte
- elementbezogene Context-Bedingungen
- kontextabhängige Bedingungen aufgrund von Attributen
- kontextabhängige Bedingungen aufgrund der Position im DOM
- Sonderfälle innerhalb von Form Controls
- Sonderfälle innerhalb von Tabellen
- Sonderfälle innerhalb von Metadata-Strukturen
- Sonderfälle für `html`, `head` und `body`
- Sonderfälle für HTML-Elemente in Fremdsprachen-/Compound-Dokumenten
- Orphan-Node-Regeln
- Custom-Element-Contextregeln

Das ZE-WebLab-Repository ist die maßgebliche Quelle für die Frage, wie diese Informationen bereits in den vorhandenen Elementdateien dokumentiert wurden.

Die beiden Ebenen werden getrennt behandelt:

```text
WHATWG
→ Welche Context-Angaben definiert die Spezifikation?

ZE-WebLab
→ Wo wurden diese Context-Angaben bereits elementbezogen dokumentiert?
```

Eine Context-Angabe gilt daher nicht automatisch als vollständig dokumentiert, nur weil sie in mehreren Elementdateien vorkommt.

---

## Einordnung

### Grundprinzip

WHATWG führt in jeder Elementdefinition unter anderem eine Angabe:

> Contexts in which this element can be used

Diese Angabe beschreibt, wo das jeweilige Element verwendet werden kann.

Die WHATWG bezeichnet diese Information ausdrücklich als **nicht-normative Beschreibung**.

Sie ist nach der Spezifikation:

- eine Beschreibung des vorgesehenen Verwendungskontexts,
- redundant zu den Content Models der umgebenden Elemente,
- eine Vereinfachung für Leser,
- auf die jeweils spezifischste Erwartung reduziert.

Die Context-Angabe ist deshalb eine wichtige Referenzdimension, aber kein eigenständiges normatives Inhaltsmodell.

### Beispiel

Ein Element kann als Context erhalten:

```text
Where phrasing content is expected.
```

Das bedeutet:

```text
Das Element ist dort vorgesehen, wo Phrasing Content erwartet wird.
```

Es bedeutet nicht:

```text
"Phrasing Content" ist ein neues HTML-Element.
```

Ebenso bedeutet es nicht:

```text
Das Content Model des Elements selbst ist Phrasing Content.
```

Context und Content Model beschreiben unterschiedliche Richtungen:

```text
Context
→ Wo darf dieses Element verwendet werden?

Content Model
→ Welche Inhalte darf dieses Element enthalten?
```

---

# WHATWG-Struktur

## §3.2.4 Element definitions

Die WHATWG definiert für jedes HTML-Element eine Elementdefinition.

Diese umfasst unter anderem:

1. Categories
2. Contexts in which this element can be used
3. Content model
4. Tag omission in text/html
5. Content attributes
6. Accessibility considerations
7. Sanitization
8. DOM interface
9. zusätzliche normative Konformitätskriterien

Die Context-Angabe steht damit auf derselben Elementdefinitions-Ebene wie diese anderen Informationsdimensionen, besitzt aber eine andere normative Funktion.

---

## §3.2.4 – Contexts in which this element can be used

WHATWG beschreibt den Context als:

- nicht-normative Beschreibung,
- Beschreibung des Ortes bzw. Umfelds, in dem ein Element verwendet werden kann,
- aus den Content Models der umgebenden Elemente ableitbare Information.

Die Spezifikation weist ausdrücklich darauf hin, dass nur die **spezifischsten Erwartungen** angegeben werden.

---

## Spezifität der Context-Angaben

Die Content Categories bilden teilweise Hierarchien.

Beispielsweise gilt:

```text
Phrasing Content
⊂ Flow Content
```

Daher kann ein Element, das Phrasing Content ist, in einem Context wie:

```text
Where phrasing content is expected.
```

beschrieben werden.

Es muss nicht zusätzlich angegeben werden:

```text
Where flow content is expected.
```

obwohl Phrasing Content auch Flow Content ist.

Die WHATWG verwendet für die Elementdefinition deshalb die spezifischere Angabe.

### Konsequenz

Eine Context-Angabe darf nicht als vollständige Aufzählung aller logisch möglichen Oberkontexte interpretiert werden.

Beispiel:

```text
Where phrasing content is expected.
```

impliziert aufgrund der Content-Category-Beziehungen auch die Verwendbarkeit an Stellen, an denen Flow Content erwartet wird.

Die Elementdefinition listet jedoch den spezifischeren Context.

---

# Inventar

## Context-Feature-Inventar

| ID | Feature | Feature-Typ | WHATWG-Bereich | Erste-Ebene-Abdeckung | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| CTX-001 | Context allgemein | Context | §3.2.4 | elementbezogen | eigenständig |
| CTX-002 | Where metadata content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | eigenständig |
| CTX-003 | Where flow content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | eigenständig |
| CTX-004 | Where sectioning content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | eigenständig |
| CTX-005 | Where heading content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | eigenständig |
| CTX-006 | Where phrasing content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | eigenständig |
| CTX-007 | Where embedded content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | eigenständig |
| CTX-008 | Where interactive content is expected | Context Expression | §3.2.4 / Elementdefinitionen | elementbezogen | relevant, soweit verwendet |
| CTX-009 | Attribute-dependent Context | Context Condition | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-010 | Parent-specific Context | Context Condition | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-011 | Descendant-specific Context | Context Condition | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-012 | Position-specific Context | Context Condition | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-013 | First-child Context | Structural Context | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-014 | Child-of Context | Structural Context | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-015 | Descendant-of Context | Structural Context | jeweilige Elementdefinition | elementbezogen | eigenständig |
| CTX-016 | Context in `head` | Structural Context | §4.2 | in Dokument-Metadata | eigenständig |
| CTX-017 | Context in `body` / Flow | Structural Context | §4.3 ff. | elementbezogen | relevant |
| CTX-018 | Table-specific Context | Structural Context | §4.9 | in Tabular Data | eigenständig |
| CTX-019 | Form-specific Context | Structural Context | §4.10 | in Forms | eigenständig |
| CTX-020 | Select-specific Context | Structural Context | §4.10 | in Forms | eigenständig |
| CTX-021 | Interactive-specific Context | Structural Context | §4.11 | in Interactive Elements | eigenständig |
| CTX-022 | Scripting-related Context | Structural Context | §4.12 | in Scripting | relevant |
| CTX-023 | Custom-Element Context | Integration Context | §4.13 | in Custom Elements | eigenständig |
| CTX-024 | Foreign-namespace Context | Integration Context | §13 / §3.2.5 | teilweise | eigenständig |
| CTX-025 | Compound-document Context | Integration Context | §3.2.5 | teilweise | relevant |
| CTX-026 | Orphan Node | DOM / Context Exception | §3.2.5 | nicht als Familie | eigenständig |
| CTX-027 | Context versus Content Model | Normative Abgrenzung | §3.2.4–§3.2.5 | elementbezogen | eigenständig |
| CTX-028 | Context versus Content Category | Normative Abgrenzung | §3.2.4–§3.2.5.2 | elementbezogen | eigenständig |
| CTX-029 | Context versus Parsing | Normative Abgrenzung | §3.2.5 / §13 | teilweise | eigenständig |
| CTX-030 | Context versus DOM creation | DOM / Conformance | §3.2.5 | teilweise | eigenständig |

---

# Begriffsdefinitionen

## Context

Ein Context beschreibt in der WHATWG-Elementdefinition, **wo ein Element verwendet werden kann**.

Die Context-Angabe ist eine nicht-normative Beschreibung.

Sie dient insbesondere dazu, die erwartete Verwendung eines Elements schnell erkennbar zu machen.

---

## Context Expression

Eine Context Expression ist eine Formulierung wie:

```text
Where phrasing content is expected.
```

oder:

```text
Where flow content is expected.
```

Sie beschreibt eine Klasse von Stellen, an denen das Element verwendet werden kann.

---

## Structural Context

Ein Structural Context beschreibt eine konkrete strukturelle Bedingung.

Beispiele:

```text
As a child of a `dl` element.
```

```text
As the first child of a `fieldset` element.
```

```text
As the first child of a `select` element.
```

```text
As a descendant of an `option` element.
```

Solche Angaben sind häufig spezifischer als allgemeine Content-Category-Erwartungen.

---

## Parent-specific Context

Ein Parent-specific Context hängt vom direkten Elternelement ab.

Beispiel:

```text
As a child of a `tr` element.
```

Das ist eine strukturelle Einschränkung.

Ein Element mit diesem Context darf nicht einfach an beliebiger Stelle eingesetzt werden.

---

## Descendant-specific Context

Ein Descendant-specific Context hängt davon ab, ob sich das Element innerhalb eines bestimmten Vorfahren befindet.

Beispiel:

```text
As a descendant of an `option` element.
```

Dies unterscheidet sich von:

```text
As a child of an `option` element.
```

Die beiden Bedingungen dürfen nicht gleichgesetzt werden.

---

## First-child Context

Ein First-child Context verlangt eine bestimmte Position innerhalb des Elternknotens.

Beispiel:

```text
As the first child of a `select` element.
```

Diese Bedingung ist strenger als:

```text
As a child of a `select` element.
```

---

# Allgemeine Context-Ausdrücke

## Where metadata content is expected

Diese Formulierung wird für Elemente verwendet, die innerhalb von Metadata Content eingesetzt werden.

Typische Beispiele sind:

- `title`
- `base`
- `link`
- `style`
- bestimmte Verwendungen von `meta`
- bestimmte Verwendungen von `noscript`

Die konkrete Context-Angabe ist immer anhand der aktuellen Elementdefinition zu prüfen.

---

## Where flow content is expected

Flow Content ist die zentrale allgemeine Inhaltskategorie für die meisten Elemente des Dokumentkörpers.

Viele Elemente werden mit:

```text
Where flow content is expected.
```

beschrieben.

Beispiele aus den Elementdefinitionen umfassen unter anderem:

- `div`
- `section`
- `article`
- `aside`
- `search`
- `details`
- viele Form- und Gruppierungselemente

Die Kategorie selbst ist in `docs/html/14-content-categories.md` dokumentiert.

---

## Where phrasing content is expected

Dieser Context wird für viele Elemente verwendet, die in Text- und Phrasing-Strukturen eingesetzt werden.

Beispiele umfassen unter anderem:

- `a`
- `span`
- `abbr`
- `strong`
- `em`
- `code`
- `q`
- `label`
- viele Form Controls

Die genaue Context-Zuordnung bleibt elementbezogen.

---

## Where embedded content is expected

Dieser Context wird insbesondere bei Elementen verwendet, die externe Ressourcen oder eingebettete Inhalte repräsentieren.

Beispiel:

```text
Where embedded content is expected.
```

Ein typisches Beispiel ist `video`.

Auch hier darf der Context nicht mit dem Content Model verwechselt werden.

---

# Spezielle strukturelle Contexts

## `html`

Das `html`-Element besitzt einen besonderen Context.

Es kann verwendet werden:

```text
As the document's document element.
```

Darüber hinaus berücksichtigt WHATWG die Verwendung in Compound Documents.

Das `html`-Element ist deshalb kein normales Flow-Content-Element.

---

## `head`

Das `head`-Element besitzt einen speziellen strukturellen Context als Bestandteil der Dokumentstruktur.

Seine Kinder sind insbesondere Metadata Content.

Die konkrete Zulässigkeit einzelner Metadata-Elemente ergibt sich aus deren jeweiligen Elementdefinitionen.

---

## `body`

Das `body`-Element besitzt einen eigenen Dokumentstruktur-Context.

Es ist nicht lediglich ein beliebiges Element, das dort verwendet wird, wo Flow Content erwartet wird.

Seine Position ist durch die Dokumentstruktur bestimmt.

---

# Parent-spezifische Contexts

## Allgemeines Muster

WHATWG verwendet häufig Formulierungen wie:

```text
As a child of a `...` element.
```

Diese Formulierung bezeichnet eine direkte Elternbeziehung.

Beispiel:

```text
th
→ As a child of a `tr` element.
```

Dies ist ein struktureller Context und keine Content Category.

---

## `dl`-bezogene Contexts

Bestimmte Elemente können abhängig davon unterschiedlich verwendet werden, ob sie Kind eines `dl` sind.

Beispiel:

```text
div
→ As a child of a `dl` element.
```

Die konkrete Verwendung kann dann ein spezielles Content Model besitzen.

---

## `fieldset`-bezogene Contexts

`legend` besitzt einen speziellen Context:

```text
As the first child of a `fieldset` element.
```

Der Context definiert damit eine strukturelle Position und nicht nur eine allgemeine Content Category.

---

## `optgroup`-bezogene Contexts

`legend` kann außerdem unter einem speziellen `optgroup`-Context auftreten.

Die genaue Context-Bedingung ist anhand der aktuellen Elementdefinition zu beachten.

---

# Form-bezogene Contexts

Form Controls besitzen zahlreiche Context-Bedingungen, die nicht auf die allgemeinen Content Categories reduziert werden können.

Beispiele:

- `label`
- `legend`
- `option`
- `optgroup`
- `select`
- `selectedcontent`
- `button`
- Form-associated Elemente

---

## `option`

`option` besitzt einen spezialisierten Context innerhalb von `select` bzw. den entsprechenden Form-Control-Strukturen.

Die konkrete Zulässigkeit ist nicht einfach durch:

```text
Where phrasing content is expected.
```

beschreibbar.

Die Form-Control-Infrastruktur definiert zusätzliche strukturelle Bedingungen.

---

## `selectedcontent`

Das `selectedcontent`-Element besitzt einen besonders engen Context.

Es kann als Nachkomme eines `button`-Elements verwendet werden, wenn dieses `button`-Element selbst Kind eines `select`-Elements ist.

Die aktuelle WHATWG-Definition beschreibt damit eine konkrete verschachtelte Struktur.

Diese Bedingung ist ein Beispiel dafür, dass Contexts auch mehrstufige DOM-Strukturen ausdrücken können.

---

# Tabellenbezogene Contexts

Tabellenelemente besitzen zahlreiche strukturelle Contexts.

Beispiele:

```text
tr
→ als Kind von table-bezogenen Containern
```

```text
td
→ als Kind von `tr`
```

```text
th
→ als Kind von `tr`
```

```text
caption
→ als Kind eines `table`
```

```text
colgroup
→ als struktureller Bestandteil eines `table`
```

Diese Contexts sind elementbezogen zu prüfen.

Sie dürfen nicht durch eine allgemeine Aussage wie:

```text
Where flow content is expected.
```

ersetzt werden.

---

# Interactive Contexts

Interaktive Elemente besitzen eigene strukturelle Einschränkungen.

Beispiele:

- `details`
- `summary`
- `dialog`

`summary` besitzt einen speziellen Context innerhalb von `details`.

Die Beziehung lautet konzeptionell:

```text
details
└── summary
```

Der Context von `summary` darf deshalb nicht nur als allgemeiner Flow-Content-Context beschrieben werden.

---

# Scripting-bezogene Contexts

Auch Scripting-Elemente besitzen spezielle Contexts.

Beispiele:

- `script`
- `noscript`
- `template`
- `slot`

Die konkrete Context-Beschreibung hängt vom Element und teilweise vom Attributzustand ab.

Insbesondere `script` und `noscript` können je nach Position im Dokument unterschiedliche Anforderungen besitzen.

---

# Attributabhängige Contexts

Ein Context kann von Attributen abhängen.

Beispielhaft kann ein Element je nach vorhandenem Attribut unterschiedliche Kategorien oder unterschiedliche erlaubte Verwendungsbedingungen besitzen.

Dies ist von der reinen Context-Angabe zu unterscheiden.

Beispiel:

```text
Wenn ein bestimmtes Attribut vorhanden ist:
→ zusätzlicher oder anderer Verwendungsfall
```

Die Context-Bedingung muss daher immer gemeinsam mit den relevanten Content Attributes geprüft werden.

---

# Context und Content Categories

Diese beiden Ebenen sind strikt zu trennen.

## Content Category

Eine Content Category klassifiziert ein Element.

Beispiel:

```text
p
→ Flow Content
→ Palpable Content
```

## Context

Der Context beschreibt, wo das Element verwendet werden kann.

Beispiel:

```text
p
→ Where flow content is expected.
```

Damit gilt:

```text
Content Category
→ Was für eine Art von Inhalt ist dieses Element?

Context
→ Wo kann dieses Element verwendet werden?
```

---

# Context und Content Model

Diese Unterscheidung ist für ZE-WebLab zentral.

## Context

```text
Wo darf das Element stehen?
```

## Content Model

```text
Was darf innerhalb des Elements stehen?
```

Beispiel:

```text
Element:
    video

Context:
    Where embedded content is expected.

Content Model:
    abhängig vom Zustand und den konkreten Anforderungen der
    `video`-Elementdefinition
```

Der Context beschreibt die äußere Position.

Das Content Model beschreibt die innere Struktur.

---

# Context ist nicht normativ

WHATWG bezeichnet die Context-Angabe ausdrücklich als:

```text
non-normative
```

Das bedeutet nicht, dass die tatsächliche Dokumentstruktur frei wäre.

Vielmehr gilt:

```text
Context-Angabe
→ informative Kurzbeschreibung

Content Models der umgebenden Elemente
→ normative Grundlage der erlaubten Struktur
```

Die Context-Angabe ist damit eine benutzerfreundliche Darstellung der strukturellen Anforderungen.

---

# Normative Regeln

## CTX-R001 – Context ist Teil der Elementdefinition

Die Context-Angabe ist Bestandteil der standardisierten Elementdefinition.

---

## CTX-R002 – Context ist nicht-normativ

Die Angabe:

```text
Contexts in which this element can be used
```

ist in der WHATWG-Elementdefinition eine nicht-normative Beschreibung.

---

## CTX-R003 – Content Model ist die normative Strukturgrundlage

Die normative Zulässigkeit der Inhaltsstruktur ergibt sich aus den Content Models.

Context und Content Model dürfen deshalb nicht gleichgesetzt werden.

---

## CTX-R004 – Nur spezifischste Contexts werden angegeben

Wenn ein spezifischerer Content-Context bereits eine allgemeinere Kategorie einschließt, wird in der Elementdefinition nur der spezifischere Context angegeben.

Beispiel:

```text
Phrasing Content
⊂ Flow Content
```

Daher kann ein Element als:

```text
Where phrasing content is expected.
```

beschrieben werden, ohne zusätzlich:

```text
Where flow content is expected.
```

aufzuführen.

---

## CTX-R005 – Parent-Bedingungen sind eigenständige Contexts

Eine Angabe wie:

```text
As a child of a `tr` element.
```

ist nicht mit:

```text
Where flow content is expected.
```

gleichzusetzen.

Die Parent-Beziehung ist eine strukturelle Bedingung.

---

## CTX-R006 – Descendant-Bedingungen sind nicht Parent-Bedingungen

Die folgenden Bedingungen sind unterschiedlich:

```text
As a child of `X`.
```

und:

```text
As a descendant of `X`.
```

Die erste verlangt eine direkte Elternbeziehung.

Die zweite erlaubt eine beliebige Tiefe innerhalb des entsprechenden Vorfahrenbaums.

---

## CTX-R007 – First-child-Bedingungen sind positionsabhängig

```text
As the first child of `X`.
```

ist strenger als:

```text
As a child of `X`.
```

Die Reihenfolge der Geschwister ist daher Teil der Context-Bedingung.

---

## CTX-R008 – Attribute können die Verwendung beeinflussen

Wenn die WHATWG-Definition die Verwendung eines Elements von einem Attribut abhängig macht, muss diese Bedingung zusammen mit dem Context dokumentiert werden.

---

## CTX-R009 – Context ist keine Parsing-Regel

Der Parser kann auch nicht-konforme Strukturen verarbeiten.

Daraus folgt nicht, dass der entsprechende Context erfüllt wurde.

```text
Parser verarbeitet Struktur
≠
Struktur ist konform
```

---

## CTX-R010 – Context ist kein DOM-API-Konzept

Ein Element kann über DOM APIs erzeugt werden, auch wenn seine Position im Dokument den normalen Context-Anforderungen nicht entspricht.

Die Möglichkeit der DOM-Erzeugung hebt die Konformitätsanforderungen für Dokumente nicht auf.

---

# DOM-Erzeugung und Orphan Nodes

WHATWG unterscheidet Dokumentkonformität von der bloßen Existenz eines DOM-Knotens.

HTML-Elemente können als sogenannte Orphan Nodes existieren.

Beispiel:

```javascript
const cell = document.createElement("td");
```

Ein `td`-Element ist normalerweise nur in der Tabellenstruktur vorgesehen.

Es kann jedoch als DOM-Knoten ohne entsprechenden Elternknoten erzeugt und gehalten werden.

Das bedeutet nicht:

```text
td darf überall im HTML-Dokument stehen.
```

Es bedeutet:

```text
DOM-Erzeugung eines Elements
≠
Konformität einer HTML-Dokumentstruktur
```

---

# Context und Parsing

## Grundprinzip

Parsing und Context sind unterschiedliche Ebenen.

```text
Context
→ beschreibt die konforme Verwendung

Parsing
→ beschreibt die Verarbeitung von HTML-Quelltext
```

Ein Parser muss auch fehlerhafte oder nicht-konforme HTML-Strukturen verarbeiten können.

Daher kann folgende Situation auftreten:

```text
HTML-Quelle nicht konform
↓
Parser verarbeitet Quelle
↓
DOM-Baum entsteht
```

Die Existenz des DOM-Baums macht die ursprüngliche Struktur nicht konform.

---

# Context und DOM

Ein DOM-Baum kann Strukturen enthalten, die bei einer statischen HTML-Quelle nicht konform wären.

Beispiel:

```javascript
const td = document.createElement("td");
document.body.append(td);
```

Die DOM-API kann den Knoten erzeugen.

Das ist jedoch nicht automatisch gleichbedeutend mit:

```html
<body>
  <td></td>
</body>
```

als konformer HTML-Struktur.

Für ZE-WebLab müssen deshalb mindestens drei Ebenen getrennt bleiben:

```text
Context
Content Model
DOM-Manipulation
```

---

# Context und Custom Elements

Autonome Custom Elements besitzen in der WHATWG-Definition einen eigenen Context.

Für autonome Custom Elements wird insbesondere angegeben:

```text
Where phrasing content is expected.
```

Ihr Content Model ist:

```text
Transparent.
```

Damit ist ein wichtiger Zusammenhang sichtbar:

```text
Custom Element
    │
    ├── Context
    │     → Where phrasing content is expected
    │
    └── Content Model
          → Transparent
```

Context und Content Model sind auch hier zwei unterschiedliche Dimensionen.

Die vollständige Custom-Elements-Systematik ist in:

```text
docs/html/17-custom-elements.md
```

dokumentiert.

---

# Context und SVG / MathML

HTML-Elemente können im Rahmen von Compound Documents und Foreign Content in Umgebungen anderer Namespaces auftreten.

WHATWG weist ausdrücklich darauf hin, dass für XML-Compound-Dokumente Kontexte auch innerhalb von Elementen anderer Namespaces entstehen können, sofern diese anderen Spezifikationen den entsprechenden Context bereitstellen.

Daraus folgt:

```text
HTML Context
≠
ausschließlich HTML-Namespace
```

Gleichzeitig darf nicht angenommen werden, dass ein beliebiges SVG- oder MathML-Element automatisch einen HTML-Context bereitstellt.

Die konkrete Integrationsregel muss aus der jeweiligen normativen Spezifikation abgeleitet werden.

---

# Context und Compound Documents

WHATWG berücksichtigt Compound Documents.

Ein HTML-Element kann innerhalb eines Elements eines anderen Namespace verwendet werden, wenn die entsprechende Fremdspezifikation diesen Context bereitstellt.

Das bedeutet:

```text
HTML-Spezifikation
+
andere normative Spezifikation
```

können gemeinsam bestimmen, ob ein HTML-Element in einem bestimmten Compound Document-Kontext zulässig ist.

Diese Situation ist von normalem HTML-Parsing zu unterscheiden.

---

# Attribute

Contexts sind keine Attribute.

Allerdings können Attribute die Context- oder Kategorienbeschreibung eines Elements beeinflussen.

Beispiele für solche Beziehungen:

- `href` beim `a`-Element
- `controls` bei Media-Elementen
- `type` bei `input`
- `itemprop` bei bestimmten Metadata-/Flow-Kontexten
- `usemap` bei `img`
- `is` bei Customized Built-In Elements

Die konkrete Wirkung muss jeweils aus der Elementdefinition bzw. der entsprechenden Attributdefinition entnommen werden.

---

# Content Categories

Contexts verwenden häufig Content Categories als Referenz.

Typische Beziehungen sind:

```text
Where metadata content is expected
Where flow content is expected
Where phrasing content is expected
Where embedded content is expected
```

Die Content-Category-Systematik ist eigenständig dokumentiert in:

```text
docs/html/14-content-categories.md
```

Die dortigen Kategorien werden in dieser Datei nicht erneut als eigene Featurefamilien definiert.

---

# Content Model

Content Models sind eine eigene zweite-Ebenen-Feature-Familie.

Sie sind dokumentiert in:

```text
docs/html/15-content-models.md
```

Die Beziehung lautet:

```text
Context
    ↓
äußerer Verwendungskontext

Content Model
    ↓
innerer erlaubter Inhalt
```

---

# Processing Models

Contexts sind keine Processing Models.

Ein Processing Model beantwortet beispielsweise:

```text
Wie verarbeitet der User Agent dieses Element?
```

Ein Context beantwortet:

```text
Wo ist dieses Element vorgesehen?
```

Beide Informationen können in derselben Elementdefinition vorkommen.

Sie sind jedoch fachlich getrennt zu erfassen.

---

# Accessibility

WHATWG behandelt Accessibility als eigene Dimension der Elementdefinition.

Aus einer Context-Angabe darf keine Accessibility-Eigenschaft abgeleitet werden.

Beispiel:

```text
Where phrasing content is expected.
```

bedeutet nicht automatisch:

```text
Accessibility role = ...
```

oder:

```text
Accessibility requirement = ...
```

Accessibility muss anhand der entsprechenden WHATWG-Regeln und gegebenenfalls externer Accessibility-Spezifikationen geprüft werden.

---

# Sanitization

Sanitization ist ebenfalls eine eigenständige Informationsdimension.

Aus einem Context darf keine Sanitization-Kategorie abgeleitet werden.

Daher gilt:

```text
Context
≠
Sanitization
```

Die Sanitization-Regeln bleiben Bestandteil der entsprechenden Elementdefinitionen und der dafür vorgesehenen Sanitization-Systematik.

---

# Link Types

Link Types sind keine Contexts.

Ein Link Type wie:

```text
stylesheet
```

oder:

```text
alternate
```

beschreibt eine Beziehung bzw. Bedeutung eines Links.

Ein Context beschreibt dagegen, wo ein Element verwendet werden kann.

Die Link-Type-Systematik ist separat dokumentiert in:

```text
docs/html/16-link-types.md
```

---

# Erste-Ebene-Abdeckung

Die erste Rechercheebene enthält die Context-Angaben jeweils innerhalb der Elementdefinitionen.

Dort sind sie Bestandteil der individuellen Referenzbeschreibung.

Beispielhafte Darstellung:

```text
Element
→ Categories
→ Contexts
→ Content Model
→ Tag Omission
→ Content Attributes
→ Accessibility
→ Sanitization
→ DOM Interface
```

Diese elementbezogene Dokumentation ist nicht dasselbe wie eine übergreifende Context-Systematik.

---

## Bewertung

| Dimension | Erste Ebene | Zweite Ebene |
|---|---|---|
| Context eines einzelnen Elements | vorhanden | Querverweis |
| allgemeiner Begriff Context | teilweise | eigenständiges Konzept |
| `Where flow content is expected` | verteilt | systematisch |
| `Where phrasing content is expected` | verteilt | systematisch |
| Metadata Context | verteilt | systematisch |
| Parent-specific Context | verteilt | systematisch |
| Descendant-specific Context | verteilt | systematisch |
| First-child Context | verteilt | systematisch |
| Tabellenkontext | in `09-tabular-data.md` | Querverweis |
| Form-Kontext | in `10-forms.md` | Querverweis |
| Interactive Context | in `11-interactive-elements.md` | Querverweis |
| Scripting Context | in `12-scripting.md` | Querverweis |
| Custom-Element Context | in `17-custom-elements.md` | Querverweis |
| Context vs. Content Model | teilweise | vollständig |
| Context vs. Content Category | teilweise | vollständig |
| Context vs. Parsing | teilweise | vollständig |
| Context vs. DOM | teilweise | vollständig |

---

# Detailprüfung

## Allgemeine Context-Prüfung

Bei jedem Element ist zu prüfen:

1. Welche Context-Angabe definiert WHATWG?
2. Ist der Context allgemein oder strukturell?
3. Hängt der Context von Attributen ab?
4. Hängt der Context vom Elternknoten ab?
5. Hängt der Context von einem Vorfahren ab?
6. Ist die Position innerhalb der Geschwister relevant?
7. Gibt es mehrere alternative Contexts?
8. Ist der Context nur für eine bestimmte Elementvariante gültig?
9. Gibt es zusätzliche Anforderungen außerhalb der Context-Kurzbeschreibung?
10. Welche Content Models der umgebenden Elemente liefern die normative Grundlage?

---

## Allgemeine Context-Klassen

Die aktuelle WHATWG-Systematik verwendet insbesondere folgende Formen:

### Kategorie-basierter Context

```text
Where metadata content is expected.
Where flow content is expected.
Where phrasing content is expected.
Where embedded content is expected.
```

### Parent-basierter Context

```text
As a child of a `...` element.
```

### Descendant-basierter Context

```text
As a descendant of a `...` element.
```

### Positionsbasierter Context

```text
As the first child of a `...` element.
```

### Dokumentstruktur-Context

```text
As the document's document element.
```

### Bedingter Context

Ein Context kann von Attributen, Zuständen oder strukturellen Bedingungen abhängen.

---

# Sonderfälle

## `a`

Der Context des `a`-Elements wird als:

```text
Where phrasing content is expected.
```

beschrieben.

Das Content Model ist dagegen transparent und besitzt zusätzliche Einschränkungen hinsichtlich interaktiver Nachkommen und bestimmter Attribute.

Damit zeigt `a` exemplarisch:

```text
Context ≠ Content Model
```

---

## `video`

`video` besitzt als allgemeine Verwendung:

```text
Where embedded content is expected.
```

Gleichzeitig hängt die Interactive-Content-Zugehörigkeit vom Vorhandensein von `controls` ab.

Damit zeigt das Element:

```text
Context
+
attribute-dependent category
```

---

## `input`

`input` wird grundsätzlich dort verwendet, wo Phrasing Content erwartet wird.

Sein genauer Funktionszustand hängt jedoch vom `type`-Attribut ab.

Die Zustandsabhängigkeit darf nicht mit einer Änderung des allgemeinen Context-Begriffs verwechselt werden.

---

## `div`

`div` besitzt den allgemeinen Flow-Content-Context:

```text
Where flow content is expected.
```

Darüber hinaus existieren spezielle strukturelle Verwendungen, beispielsweise innerhalb bestimmter Form-Control-Strukturen.

Die aktuelle Elementdefinition ist deshalb maßgeblich.

---

## `legend`

`legend` besitzt spezielle Context-Bedingungen:

```text
As the first child of a `fieldset` element.
```

sowie einen weiteren Form-Control-Kontext.

Dies ist ein Beispiel für einen positionsabhängigen Context.

---

## `td` und `th`

Beide Tabellenelemente besitzen einen direkten Tabellenkontext:

```text
As a child of a `tr` element.
```

Das ist eine strukturelle Bedingung.

Sie darf nicht durch die Content Category `Flow Content` ersetzt werden.

---

## `selectedcontent`

`selectedcontent` besitzt einen besonders spezifischen Context innerhalb der aktuellen `select`-Struktur.

Diese Art Context zeigt, dass die Context-Systematik nicht auf die sieben allgemeinen Content Categories reduziert werden kann.

---

# Konformitätsregeln

## Autorenkonformität

Autoren dürfen HTML-Elemente nicht beliebig an jeder Stelle verwenden.

Die HTML-Spezifikation verlangt, dass Elemente nur dort verwendet werden, wo dies ausdrücklich erlaubt ist oder durch eine andere anwendbare Spezifikation verlangt wird.

Die Context-Angabe ist dabei eine verständliche Darstellung der vorgesehenen Verwendung.

Die normative Grundlage ergibt sich aus den entsprechenden Content Models und den sonstigen Konformitätsregeln.

---

## Nicht-konforme Strukturen können geparst werden

Eine nicht-konforme Struktur kann trotzdem vom HTML Parser verarbeitet werden.

Daher gilt:

```text
Parser-Akzeptanz
≠
Konformität
```

Dies ist für die ZE-WebLab-Dokumentation ausdrücklich zu berücksichtigen.

---

# DOM-Manipulation

Die DOM API erlaubt die Erzeugung von Elementen unabhängig davon, ob diese in der entsprechenden Dokumentstruktur konform platziert wären.

Beispiel:

```javascript
const td = document.createElement("td");
```

Dies ist eine gültige DOM-Operation.

Daraus folgt jedoch nicht:

```html
<td></td>
```

dürfe als beliebiges Kind von `body` verwendet werden.

Context und DOM-Erzeugbarkeit sind getrennte Ebenen.

---

# Orphan Nodes

HTML-Elemente dürfen als Orphan Nodes existieren.

Ein Orphan Node besitzt keinen entsprechenden Elternknoten im Dokument.

Beispiel:

```javascript
const cell = document.createElement("td");
```

Das kann als DOM-Objekt existieren, ohne Bestandteil einer gültigen Tabellenstruktur zu sein.

Diese Ausnahme darf nicht als allgemeine Lockerung der HTML-Strukturregeln interpretiert werden.

---

# Context in XML-Dokumenten

HTML-Elementdefinitionen gelten auch für HTML-Elemente in XML-Dokumenten.

In Compound Documents können HTML-Elemente innerhalb anderer Namespaces auftreten, sofern die entsprechende Spezifikation diesen Context bereitstellt.

Dies ist für die HTML/SVG/MathML-Integration relevant.

Die vollständigen Integrationsregeln gehören jedoch in die dafür vorgesehenen Integrations- bzw. Parsing-Dateien.

---

# SVG- und MathML-Beziehungen

Context darf nicht mit Namespace verwechselt werden.

Beispiel:

```text
HTML namespace
SVG namespace
MathML namespace
```

sind Namespace-Konzepte.

Ein Context ist dagegen eine Aussage darüber, wo ein Element verwendet werden kann.

Bei Foreign Content können zusätzliche Regeln gelten.

Daher:

```text
Namespace
≠
Context
```

und:

```text
Foreign Content
≠
HTML Context
```

---

# Querverweise

## Context ↔ Content Categories

Context Expressions verwenden häufig Content Categories.

Beispiel:

```text
Where phrasing content is expected.
```

Die Kategorie selbst ist in:

```text
docs/html/14-content-categories.md
```

dokumentiert.

---

## Context ↔ Content Models

Die normative Zulässigkeit des Contexts ergibt sich aus den Content Models der umgebenden Elemente.

Siehe:

```text
docs/html/15-content-models.md
```

---

## Context ↔ Elementdefinitionen

Jede Elementdefinition kann einen Context angeben.

Die erste Rechercheebene enthält diese Informationen elementbezogen.

Die zweite Ebene abstrahiert die gemeinsamen Context-Muster.

---

## Context ↔ Attributes

Attribute können die Kategoriezugehörigkeit oder das Verhalten eines Elements beeinflussen.

Beispiele:

```text
a + href
audio + controls
video + controls
input + type
img + usemap
```

Die jeweilige Elementdefinition ist maßgeblich.

---

## Context ↔ Forms

Form Controls besitzen zahlreiche spezialisierte Contexts.

Siehe:

```text
docs/html/10-forms.md
```

Insbesondere relevant sind:

- `label`
- `legend`
- `option`
- `optgroup`
- `select`
- `selectedcontent`
- Form-associated elements

---

## Context ↔ Tables

Tabellen besitzen besonders restriktive strukturelle Contexts.

Siehe:

```text
docs/html/09-tabular-data.md
```

Beispiele:

```text
table
caption
colgroup
thead
tbody
tfoot
tr
td
th
```

---

## Context ↔ Interactive Elements

Interaktive Elemente besitzen eigene strukturelle Beziehungen.

Siehe:

```text
docs/html/11-interactive-elements.md
```

Beispiele:

```text
details
summary
dialog
```

---

## Context ↔ Scripting

Scripting-Elemente besitzen eigene Context- und Zustandsregeln.

Siehe:

```text
docs/html/12-scripting.md
```

---

## Context ↔ Custom Elements

Autonome Custom Elements besitzen einen definierten Context.

Customized Built-In Elements übernehmen den Context des von ihnen erweiterten nativen Elements, soweit die jeweilige Definition dies bestimmt.

Siehe:

```text
docs/html/17-custom-elements.md
```

---

## Context ↔ Parsing

Parsing bestimmt die Verarbeitung von Quelltext.

Context bestimmt die konforme Verwendung.

Siehe die zukünftige eigenständige Parsing-Feature-Familie.

---

## Context ↔ DOM

DOM APIs können Elemente erzeugen und verschieben.

Das ist nicht identisch mit der Konformität einer HTML-Quelle.

---

# Status / V1

## WHATWG-Status

**Definiert:** Ja.

Die Context-Angabe ist Bestandteil der WHATWG-Elementdefinition.

**Normative Definition des Begriffs:** Ja.

**Normativer Charakter der Context-Angabe selbst:** Nein.

WHATWG bezeichnet die Context-Angabe ausdrücklich als nicht-normative Beschreibung.

**Normative Grundlage der zulässigen Struktur:** Ja.

Diese ergibt sich aus den Content Models und den sonstigen Konformitätsanforderungen.

---

## Obsolete / Deprecated

Das Context-System selbst ist weder als obsolete noch als deprecated HTML-Feature definiert.

Einzelne Elemente können unabhängig davon obsolete oder deprecated sein.

Der Status eines Elements darf daher nicht mit dem Status des Context-Konzepts gleichgesetzt werden.

---

## Browser-Kompatibilität

Browser-Kompatibilität wird nicht als WHATWG-Status verwendet.

Insbesondere gilt:

```text
Browser unterstützt Element
```

ist keine Aussage darüber, ob:

```text
WHATWG definiert den Context
```

oder:

```text
die konkrete HTML-Struktur konform ist
```

---

## ZE-WebLab V1

**Feature-Familie:** Contexts

**Feature-Typ:** Context / Informationsdimension

**Rechercheebene:** 2

**V1-Einstufung:** übergreifendes Referenzkonzept

**Begründung:**

Die erste Ebene dokumentiert Contexts elementbezogen.

Die zweite Ebene dokumentiert:

- die Bedeutung des Context-Feldes,
- die wiederkehrenden Context-Ausdrücke,
- strukturelle Context-Muster,
- die Abgrenzung zu Content Categories,
- die Abgrenzung zu Content Models,
- die Abgrenzung zu Parsing,
- die Beziehung zu DOM-Erzeugung,
- die Beziehungen zu spezialisierten HTML-Featurefamilien.

---

# Nicht als Context zu zählen

Folgende Konzepte sind keine Contexts:

- Flow Content
- Phrasing Content
- Metadata Content
- Embedded Content
- Interactive Content
- Sectioning Content
- Heading Content
- Palpable Content
- Script-supporting Elements
- Content Model
- Transparent Content Model
- `nothing`
- Link Type
- DOM Interface
- API
- Processing Model
- Parsing Mode
- Namespace
- Custom Element Name
- Attribute
- Sanitization Category
- Accessibility Role

Sie können jedoch Bestandteil der Definition oder Beschreibung eines Contexts sein.

---

# Abgrenzung: Context vs. Content Category

| Konzept | Frage |
|---|---|
| Content Category | Welcher Inhaltskategorie gehört das Element an? |
| Context | Wo kann das Element verwendet werden? |

Beispiel:

```text
Element:
    video

Content Categories:
    Flow
    Phrasing
    Embedded
    Palpable
    ggf. Interactive

Context:
    Where embedded content is expected.
```

---

# Abgrenzung: Context vs. Content Model

| Konzept | Richtung |
|---|---|
| Context | Umgebung → Element |
| Content Model | Element → Inhalt |

Beispiel:

```text
Context:
    Where flow content is expected.

Content Model:
    Flow content.
```

Diese beiden Angaben können zufällig ähnlich aussehen, haben aber unterschiedliche Bedeutungen.

---

# Abgrenzung: Context vs. Parsing

| Konzept | Zweck |
|---|---|
| Context | Konforme Verwendung |
| Parsing | Verarbeitung von Quelltext |

Ein Parser kann eine nicht-konforme Struktur verarbeiten.

Das ändert die Context-Anforderungen nicht.

---

# Abgrenzung: Context vs. DOM

| Konzept | Zweck |
|---|---|
| Context | konforme Dokumentstruktur |
| DOM API | programmgesteuerte Knotenerzeugung und -manipulation |

Ein DOM-Knoten kann existieren, obwohl seine Position in einer HTML-Quelle nicht konform wäre.

---

# Abgrenzung: Context vs. Namespace

Namespace:

```text
HTML
SVG
MathML
```

Context:

```text
Where phrasing content is expected.
```

Ein Namespace identifiziert die Vokabular-/Namensraumzugehörigkeit.

Ein Context beschreibt die zulässige bzw. vorgesehene Verwendung.

---

# Fachliche Sonderregeln

## Nur die spezifischste Erwartung wird angegeben

Wenn mehrere allgemeine Content Categories logisch zutreffen, verwendet WHATWG für die Context-Angabe die spezifischste Erwartung.

Beispiel:

```text
Phrasing Content
⊂
Flow Content
```

Ein Element wird daher als:

```text
Where phrasing content is expected.
```

beschrieben.

---

## Context kann mehrere Alternativen besitzen

Ein Element kann mehr als einen Context erhalten.

Beispielhaft:

```text
Where metadata content is expected.
```

und:

```text
In a `noscript` element that is a child of a `head` element.
```

Diese Angaben stellen alternative bzw. zusätzliche Verwendungsmöglichkeiten dar.

---

## Context kann von Struktur abhängen

Ein Element kann nur dann zulässig sein, wenn:

- es Kind eines bestimmten Elements ist,
- es Nachkomme eines bestimmten Elements ist,
- es an einer bestimmten Position steht,
- es ein bestimmtes Geschwisterverhältnis besitzt,
- es sich in einer bestimmten Dokumentstruktur befindet.

---

## Context kann mit Content Attributes interagieren

Die konkrete Bedeutung eines Elements kann von Attributen abhängen.

Dies kann wiederum die Content Category und die zulässige Verwendung beeinflussen.

Die Attribute müssen deshalb separat dokumentiert werden.

---

## Context ist keine vollständige Konformitätsprüfung

Das Context-Feld allein reicht nicht aus, um die Konformität eines Elements zu beurteilen.

Zusätzlich können relevant sein:

- Content Model
- Content Attributes
- Tag Omission
- Accessibility
- Sanitization
- zusätzliche normative Sonderregeln
- Attribute States
- DOM-/Processing-Regeln
- andere anwendbare Spezifikationen

---

# Offene Punkte

## CTX-O001 – Elementweise Detailvalidierung

Die vollständige elementweise Validierung jedes einzelnen Context-Eintrags gegen die aktuelle WHATWG-Fassung bleibt eine kontinuierliche Qualitätssicherungsaufgabe der jeweiligen Elementreferenzen.

**Status:** kein offener Punkt hinsichtlich der Existenz oder Bedeutung des Context-Konzepts.

---

## CTX-O002 – Spezialisierte Contexts

Spezialisierte Contexts innerhalb von:

- Forms
- Tables
- Interactive Elements
- Scripting
- Custom Elements
- Foreign Content

sind jeweils in ihren Feature-Familien weiterzuführen.

**Status:** Querverweis-/Konsistenzthema, keine normative Lücke.

---

## CTX-O003 – Compound Documents

Die konkrete Zulässigkeit von HTML-Elementen in Compound Documents kann zusätzlich von anderen Spezifikationen abhängen.

**Status:** externe normative Abhängigkeit.

---

## CTX-O004 – Parsing

Die vollständige Beziehung zwischen Context-Konformität und tatsächlichem HTML-Parsing gehört in eine eigenständige Parsing-Feature-Familie.

**Status:** separate zweite-Ebenen-Datei.

---

## CTX-O005 – DOM-Manipulation

Die vollständige Abgrenzung zwischen HTML-Dokumentkonformität und DOM-Manipulation gehört teilweise in eine eigenständige DOM-/API-Feature-Familie.

**Status:** separate zweite-Ebenen-Datei.

---

# Prüfstatus

| Prüfbereich | Status |
|---|---|
| §3.2.4 Element definitions | geprüft |
| Context Definition | geprüft |
| Non-normative Charakterisierung | geprüft |
| Spezifischste Context-Erwartung | geprüft |
| Relationship zu Content Categories | geprüft |
| Relationship zu Content Models | geprüft |
| `metadata content` Context | geprüft |
| `flow content` Context | geprüft |
| `phrasing content` Context | geprüft |
| `embedded content` Context | geprüft |
| Parent-specific Context | geprüft |
| Descendant-specific Context | geprüft |
| First-child Context | geprüft |
| Form Contexts | geprüft |
| Table Contexts | geprüft |
| Interactive Contexts | geprüft |
| Scripting Contexts | geprüft |
| Custom-Element Context | geprüft |
| Foreign-/Compound-Document-Bezug | geprüft |
| Orphan Nodes | geprüft |
| DOM-Abgrenzung | geprüft |
| Parsing-Abgrenzung | geprüft |
| Accessibility-Abgrenzung | geprüft |
| Sanitization-Abgrenzung | geprüft |
| Link-Type-Abgrenzung | geprüft |
| V1-Abgrenzung | geprüft |
| offene normative Lücken | keine innerhalb des Context-Konzepts festgestellt |

---

# Quellen / Referenzen

## Normative Primärquelle

**WHATWG HTML Living Standard**

Relevante Bereiche:

- §3.2.4 Element definitions
- §3.2.5 Content models
- §3.2.5.2 Kinds of content
- §4 The elements of HTML
- die jeweiligen Elementdefinitionen
- §4.10 Forms
- §4.11 Interactive elements
- §4.12 Scripting
- §4.13 Custom elements
- §13 The HTML syntax
- die relevanten Foreign-Content- und Compound-Document-Regeln

---

## Projektquelle

**ZE-WebLab – HTML-Referenz**

Berücksichtigte bestehende Featurefamilien:

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
- `docs/html/17-custom-elements.md`

---

## Weitere normative Bezüge

Je nach konkretem Context können zusätzlich relevant sein:

- WHATWG DOM Standard
- WHATWG HTML Parsing-Regeln
- SVG-Spezifikation
- MathML-Spezifikation
- Atom-Spezifikation für entsprechende Compound-Document-Kontexte
- ARIA-/Accessibility-Spezifikationen für Accessibility-Fragen

Diese externen Spezifikationen ersetzen nicht die WHATWG-Definition des jeweiligen HTML-Elements.

---

# Zusammenfassung des Feature-Status

| Feature | WHATWG | ZE-WebLab-Ebene | Status |
|---|---|---|---|
| Context allgemein | definiert | Rechercheebene 2 | dokumentiert |
| Context als Elementdefinitions-Dimension | definiert | Rechercheebene 2 | dokumentiert |
| `Where metadata content is expected` | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| `Where flow content is expected` | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| `Where phrasing content is expected` | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| `Where embedded content is expected` | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| Parent-specific Context | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| Descendant-specific Context | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| First-child Context | definiert/verwendet | Rechercheebene 2 | dokumentiert |
| Attribute-dependent Context | elementbezogen definiert | Rechercheebene 2 | dokumentiert |
| Form Context | definiert | Rechercheebene 2 | dokumentiert |
| Table Context | definiert | Rechercheebene 2 | dokumentiert |
| Interactive Context | definiert | Rechercheebene 2 | dokumentiert |
| Scripting Context | definiert | Rechercheebene 2 | dokumentiert |
| Custom-Element Context | definiert | Rechercheebene 2 | dokumentiert |
| Foreign-/Compound-Document Context | integrationsabhängig | Rechercheebene 2 | dokumentiert |
| Orphan Node | definiert | Rechercheebene 2 | dokumentiert |
| Context vs. Content Category | definiert/abgegrenzt | Rechercheebene 2 | dokumentiert |
| Context vs. Content Model | definiert/abgegrenzt | Rechercheebene 2 | dokumentiert |
| Context vs. Parsing | abgegrenzt | Rechercheebene 2 | dokumentiert |
| Context vs. DOM | abgegrenzt | Rechercheebene 2 | dokumentiert |

---

# Abschluss

Contexts bilden eine eigenständige Informationsdimension der HTML-Elementdefinitionen.

Sie sind:

- keine HTML-Elemente,
- keine Content Categories,
- keine Content Models,
- keine Attribute,
- keine APIs,
- keine DOM Interfaces,
- keine Processing Models,
- keine Parsing Models,
- keine Link Types.

Die zentrale fachliche Trennung lautet:

```text
Content Category
→ klassifiziert das Element

Context
→ beschreibt den vorgesehenen Verwendungsort

Content Model
→ beschreibt den zulässigen Inhalt

Processing Model
→ beschreibt die Verarbeitung

DOM Interface
→ beschreibt die programmatische Schnittstelle
```

Die Context-Angabe der WHATWG ist nicht-normativ, stellt jedoch eine wichtige Referenzdimension der Elementdefinition dar. Die normative Konformität der Dokumentstruktur ergibt sich aus den entsprechenden Content Models und den weiteren Konformitätsanforderungen.

Damit ist die übergreifende Feature-Familie `Contexts` für die zweite Rechercheebene dokumentiert.