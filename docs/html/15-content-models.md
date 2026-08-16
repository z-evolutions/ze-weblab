``````````markdown
# ZE-WebLab – HTML-Referenz: Content Models

## Arbeitsstand / Quellenstand

**Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Content Model

**Zielpfad:** `docs/html/15-content-models.md`

**Normative Primärquelle:** WHATWG HTML Living Standard, Abschnitt `3.2.5 Content models` einschließlich der zugehörigen Unterabschnitte.

**Geprüfter WHATWG-Stand:** aktuelle Living-Standard-Fassung, abgerufen am 16.08.2026. Die von WHATWG angezeigte Fassung wurde am 11.08.2026 aktualisiert.

**Projektquelle:** ZE-WebLab, vorhandene HTML-Elementreferenz unter `docs/html/01-*.md` bis `docs/html/12-*.md`.

### Abgrenzung

Diese Datei dokumentiert das übergreifende System der **Content Models**.

Sie ist keine erneute Elementreferenz.

Die konkreten Content Models einzelner HTML-Elemente bleiben Bestandteil der jeweiligen Elementdefinitionen der ersten Rechercheebene. Diese Datei beschreibt dagegen die gemeinsamen Begriffe, Modelltypen und normativen Regeln, die von den Elementdefinitionen verwendet werden.

Content Models sind:

- keine HTML-Elemente,
- keine Attribute,
- keine Content Categories,
- keine Contexts,
- keine DOM Interfaces,
- keine APIs,
- keine Link Types.

Ein Content Model beschreibt normativ, welche Inhalte ein Element als Kinder bzw. Nachkommen enthalten darf bzw. muss.

---

## Einordnung

WHATWG definiert für jedes in der Spezifikation definierte HTML-Element ein **Content Model**.

Das Content Model ist Bestandteil der Elementdefinition und beschreibt die erwarteten Inhalte eines Elements.

Die Spezifikation unterscheidet dabei ausdrücklich zwischen:

- `Categories`
- `Contexts in which this element can be used`
- `Content model`
- `Sanitization`
- `DOM interface`

Diese Informationen haben unterschiedliche normative Funktionen.

### Content Categories

Content Categories gruppieren Elemente nach gemeinsamen Eigenschaften.

Sie werden unter anderem verwendet, um Content Models anderer Elemente auszudrücken.

Beispiel:

```text
section → Content Model: Flow content
```

Das bedeutet nicht, dass `Flow content` ein eigenes Element oder ein alternatives Markup ist.

### Context

Der in einer Elementdefinition angegebene Context beschreibt, wo ein Element verwendet werden kann.

WHATWG bezeichnet diese Angabe als nicht-normative Beschreibung und stellt klar, dass sie aus den Content Models der umgebenden Elemente ableitbar bzw. redundant ist.

Der Context darf deshalb nicht mit dem Content Model gleichgesetzt werden.

### Content Model

Das Content Model ist dagegen eine normative Beschreibung der Inhalte, die ein Element als Kinder bzw. Nachkommen enthalten darf.

---

## WHATWG-Struktur

Der relevante normative Bereich befindet sich im Abschnitt:

`3.2.5 Content models`

Dazu gehören aktuell insbesondere:

- `3.2.5.1 The "nothing" content model`
- `3.2.5.2 Kinds of content`
  - `3.2.5.2.1 Metadata content`
  - `3.2.5.2.2 Flow content`
  - `3.2.5.2.3 Sectioning content`
  - `3.2.5.2.4 Heading content`
  - `3.2.5.2.5 Phrasing content`
  - `3.2.5.2.6 Embedded content`
  - `3.2.5.2.7 Interactive content`
  - `3.2.5.2.8 Palpable content`
  - `3.2.5.2.9 Script-supporting elements`
  - sowie zusätzliche spezialisierte Kategorien für bestimmte Form-Control-Inhalte
- `3.2.5.3 Transparent content models`
- `3.2.5.4 Paragraphs`

Die genaue Abschnittsnummerierung kann zwischen der vollständigen Living Standard und der für Webentwickler aufbereiteten Edition abweichen. Maßgeblich ist die aktuelle WHATWG-Living-Standardstruktur.

---

## Inventar

### CM-001 – Content Model

**Feature-Typ:** Content Model

**Definition:**

Das Content Model eines Elements ist die normative Beschreibung dessen, welche Inhalte ein Element als Kinder bzw. Nachkommen enthalten darf.

**WHATWG:** `3.2.5 Content models`

**Status:** im WHATWG HTML Living Standard definiertes normatives Konzept.

**Erste-Ebene-Abdeckung:** teilweise.

Die vorhandenen Elementdateien dokumentieren Content Models im Zusammenhang mit einzelnen Elementdefinitionen. Die übergreifende Systematik der Content Models ist jedoch eine eigenständige zweite-Ebenen-Funktion.

**Zweite-Ebene-Relevanz:** vollständig relevant.

---

### CM-002 – "nothing" Content Model

**Feature-Typ:** Content Model

**WHATWG:** `3.2.5.1 The "nothing" content model`

Ein Element mit dem Content Model `nothing` darf grundsätzlich keine Elementknoten und keine Textknoten enthalten, wobei Inter-Element-Whitespace entsprechend der WHATWG-Regel ausgenommen ist.

Das `nothing` Content Model ist damit ein normatives Inhaltsmodell.

Es ist nicht mit einem Void Element gleichzusetzen.

---

### CM-003 – Kinds of Content

**Feature-Typ:** Content Model / Content Category System

**WHATWG:** `3.2.5.2 Kinds of content`

WHATWG ordnet HTML-Elemente in verschiedene Content Categories ein.

Diese Kategorien werden unter anderem zur Formulierung von Content Models verwendet.

Die wichtigsten allgemeinen Kategorien sind:

- Metadata content
- Flow content
- Sectioning content
- Heading content
- Phrasing content
- Embedded content
- Interactive content

Weitere spezialisierte Kategorien existieren an anderer Stelle bzw. für bestimmte HTML-Funktionsbereiche.

Die Kategorien sind deshalb nicht als vollständig disjunkte Klassen zu verstehen.

Ein Element kann gleichzeitig mehreren Kategorien angehören.

---

### CM-004 – Transparent Content Model

**Feature-Typ:** Content Model

**WHATWG:** `3.2.5.3 Transparent content models`

Ein transparentes Content Model übernimmt die relevanten Anforderungen aus dem Content Model des Elternelements.

Der transparente Teil des Content Models wird dadurch nicht unabhängig vom Kontext betrachtet.

Bei einem transparenten Element wird die zulässige Inhaltsstruktur aus dem Content Model des Elements abgeleitet, in dessen Inhalt das transparente Element eingesetzt wurde.

Bei mehreren ineinander geschachtelten transparenten Elementen muss diese Ableitung iterativ erfolgen.

Transparent bedeutet deshalb nicht:

> beliebiger Inhalt ist immer erlaubt.

Transparent bedeutet vielmehr:

> Die zulässigen Inhalte werden vom umgebenden Content Model bestimmt.

---

### CM-005 – Paragraph

**Feature-Typ:** Content Model / strukturelles Konzept

**WHATWG:** `3.2.5.4 Paragraphs`

WHATWG definiert den Begriff `paragraph` nicht ausschließlich über das `p`-Element.

Der Begriff wird für die Beschreibung von Text- und Phrasing-Strukturen verwendet.

Die Paragraph-Definition ist deshalb ein übergreifendes strukturelles Konzept und kein Synonym für das HTML-Element `p`.

---

### CM-006 – Select Inner Content

**Feature-Typ:** spezialisiertes Content Model / Content Category

**WHATWG:** Bereich der Kinds-of-content-Definitionen für Form Controls.

Die aktuelle WHATWG-Spezifikation enthält spezialisierte Inhaltskategorien für den Inhalt von `select`-Elementen.

Diese Kategorie ist von den allgemeinen Kategorien wie Flow Content und Phrasing Content zu unterscheiden.

Sie dient dazu, die zulässige Struktur innerhalb bestimmter Form Controls präzise zu definieren.

---

### CM-007 – Optgroup Inner Content

**Feature-Typ:** spezialisiertes Content Model / Content Category

**WHATWG:** Bereich der Kinds-of-content-Definitionen für Form Controls.

Für `optgroup` existiert eine eigene spezialisierte Inhaltsdefinition.

Diese Definition ist nicht als allgemeine Content Category für beliebige HTML-Elemente zu behandeln.

Sie unterstützt die präzise Beschreibung der erlaubten Struktur innerhalb von `select`-bezogenen Form Controls.

---

### CM-008 – Option Inner Content

**Feature-Typ:** spezialisiertes Content Model / Content Category

**WHATWG:** Bereich der Kinds-of-content-Definitionen für Form Controls.

Für `option` existiert ebenfalls eine spezialisierte Inhaltsdefinition.

Sie beschreibt die besondere Inhaltsstruktur eines Option-Elements und darf nicht mit allgemeinen Kategorien wie Phrasing Content gleichgesetzt werden.

---

## Begriffsdefinitionen

### Content Model

Ein Content Model beschreibt normativ, welche Inhalte ein Element enthalten darf.

Die Formulierung erfolgt in der WHATWG-Spezifikation häufig über Begriffe wie:

- Flow content
- Phrasing content
- Metadata content
- Nothing
- Transparent
- bestimmte konkrete Elemente
- Kombinationen aus Kategorien und konkreten Elementen
- spezialisierte Form-Control-Inhaltskategorien

---

### Child Content und Descendant Content

Ein Content Model kann Anforderungen an die Inhalte eines Elements stellen, ohne dass dies lediglich als einfache Liste unmittelbarer Kinder verstanden werden darf.

Insbesondere bei transparenten Content Models kann die normative Zulässigkeit über den Kontext des Elements und über mehrere Ebenen der DOM-Struktur bestimmt werden.

---

### Nothing ist nicht Void

Diese Unterscheidung ist ausdrücklich relevant.

Ein Element mit `nothing` als Content Model darf keinen normalen Element- oder Textinhalt enthalten.

Ein **Void Element** ist dagegen ein Begriff der HTML-Syntax.

Die beiden Konzepte sind unabhängig voneinander.

Daher gilt:

```text
Content Model = nothing
```

ist nicht gleichbedeutend mit:

```text
Void Element
```

Die Tatsache, dass viele Void Elements ein Content Model ohne normalen Inhalt besitzen, ändert nichts an der konzeptionellen Trennung.

---

### Transparent

Ein transparentes Content Model wird anhand des umgebenden Content Models bestimmt.

Es ist deshalb kontextabhängig.

Beispielhafte Konsequenz:

Ein transparentes Element kann in einem Kontext Phrasing Content aufnehmen, während dasselbe Element in einem anderen Kontext andere Inhalte zulassen kann.

---

## Normative Regeln

### Regel CM-R001 – Jedes HTML-Element besitzt ein Content Model

Jedes in der HTML-Spezifikation definierte Element besitzt eine Definition seines erwarteten Inhalts.

Das Content Model ist Bestandteil der Elementdefinition.

---

### Regel CM-R002 – Content Model ist normativ

Das Content Model beschreibt normative Anforderungen an die Inhaltsstruktur eines Elements.

Es darf nicht als rein informative Dokumentationshilfe behandelt werden.

---

### Regel CM-R003 – Context und Content Model sind getrennt

Der Context eines Elements und sein Content Model sind unterschiedliche Informationen.

Der Context ist in den Elementdefinitionen eine nicht-normative Beschreibung der vorgesehenen Verwendung.

Das Content Model definiert dagegen normativ, welche Inhalte zulässig sind.

---

### Regel CM-R004 – Content Categories können Content Models ausdrücken

Die Content Categories dienen unter anderem dazu, Content Models kompakt zu formulieren.

Ein Content Model wie:

```text
Flow content
```

verweist deshalb auf die entsprechende Content Category.

---

### Regel CM-R005 – Ein Element kann mehreren Kategorien angehören

Content Categories sind nicht gegenseitig exklusiv.

Ein Element kann gleichzeitig beispielsweise:

- Flow Content
- Phrasing Content
- Embedded Content

sein, sofern die jeweilige WHATWG-Definition dies vorsieht.

---

### Regel CM-R006 – Transparent ist kontextabhängig

Bei einem transparenten Content Model wird die zulässige Inhaltsstruktur aus dem relevanten Content Model des Elternelements abgeleitet.

Eine pauschale Interpretation als `any content` ist nicht konform.

---

### Regel CM-R007 – Transparenz kann verschachtelt werden

Bei verschachtelten transparenten Elementen muss die Ermittlung des relevanten Content Models gegebenenfalls über mehrere Ebenen fortgesetzt werden.

---

### Regel CM-R008 – Transparent ohne Parent

Wenn ein transparentes Element keinen Parent besitzt, wird für den transparenten Teil des Content Models die in WHATWG definierte Ersatzbehandlung angewendet.

Diese darf nicht durch eine freie Interpretation ersetzt werden.

---

### Regel CM-R009 – Spezialisierte Inhaltskategorien sind keine neuen HTML-Elemente

Spezielle Kategorien für Form-Control-Inhalte, beispielsweise im Zusammenhang mit `select`, `optgroup` und `option`, sind Feature-/Content-Model-Konzepte.

Sie werden nicht als HTML-Elementinventar gezählt.

---

## Detailprüfung

### 1. Nothing Content Model

Das `nothing` Content Model bedeutet, dass das Element keine normalen Text- oder Elementknoten als Inhalt enthalten darf.

Inter-Element-Whitespace ist nach der WHATWG-Regel gesondert zu behandeln.

Die Regel ist insbesondere für die Abgrenzung zu syntaktischen Void Elements relevant.

---

### 2. Allgemeine Content Categories

Die grundlegenden Kategorien bilden ein hierarchisches bzw. überlappendes System.

WHATWG beschreibt insbesondere folgende Beziehungen:

- Sectioning Content ist Flow Content.
- Heading Content ist Flow Content.
- Phrasing Content ist Flow Content.
- Embedded Content ist Flow Content.
- Interactive Content ist Flow Content.
- Embedded Content ist zugleich Phrasing Content.
- Bestimmte Metadata-Elemente können Flow Content sein.
- Bestimmte Metadata- und Interactive-Elemente können Phrasing Content sein.
- Bestimmte Embedded-Elemente können Interactive Content sein.

Diese Beziehungen sind fachlich relevant, weil Content Models dadurch indirekt weitere Elementmengen zulassen können.

---

### 3. Elementlisten der Kategorien

Die vollständigen Elementzugehörigkeiten der Content Categories werden nicht als unabhängige Elementinventarliste dieser Datei dupliziert.

Sie sind Bestandteil der Content-Category-Dokumentation.

Diese Datei referenziert sie als normative Bausteine der Content Models.

---

### 4. Transparent Content Models

Transparent Content Models sind besonders wichtig bei Elementen, deren zulässiger Inhalt vom umgebenden Kontext abhängt.

Die Prüfung eines transparenten Elements darf daher nicht isoliert anhand einer statischen Liste durchgeführt werden.

Die relevante Struktur ist:

```text
Elternelement
    ↓
Content Model des Elternelements
    ↓
Position des transparenten Elements
    ↓
zulässiger Inhalt des transparenten Elements
```

Bei mehreren transparenten Ebenen wird die Ableitung fortgesetzt.

---

### 5. Paragraphen

Der WHATWG-Begriff `paragraph` ist ein struktureller Begriff.

Er darf nicht automatisch durch:

```html
<p>...</p>
```

ersetzt werden.

Das `p`-Element ist ein konkretes HTML-Element.

`paragraph` ist dagegen ein übergreifendes Konzept der HTML-Strukturdefinition.

---

## Attribute

Content Models sind keine Attribute.

Einzelne Attribute können allerdings den Status eines Elements oder die Einordnung in bestimmte Content Categories beeinflussen.

Beispiele aus der WHATWG-Systematik sind zustandsabhängige Kategorien:

- `a` ist Interactive Content, wenn `href` vorhanden ist.
- `audio` ist Interactive Content, wenn `controls` vorhanden ist.
- `video` ist Interactive Content, wenn `controls` vorhanden ist.
- `img` ist unter bestimmten Bedingungen Interactive Content, beispielsweise bei `usemap` oder `controls`.
- `input` ist abhängig vom `type`-Zustand Interactive Content.

Damit kann ein Attribut indirekt die für ein Content Model relevante Kategorisierung beeinflussen.

Das Attribut selbst wird dadurch jedoch nicht Teil des Content Models.

---

## Content Categories

Content Categories und Content Models müssen getrennt dokumentiert werden.

Die grundlegenden WHATWG-Kategorien sind:

### Metadata Content

Metadateninhalt beschreibt Informationen, die unter anderem die Darstellung oder das Verhalten des übrigen Inhalts vorbereiten oder Beziehungen zu anderen Dokumenten herstellen.

Typische HTML-Elemente dieser Kategorie sind:

- `base`
- `link`
- `meta`
- `noscript`
- `script`
- `style`
- `template`
- `title`

Zusätzliche Elemente bzw. Inhalte aus anderen Namespaces können entsprechend ihrer Semantik ebenfalls unter die von WHATWG definierte Kategorie fallen.

---

### Flow Content

Flow Content umfasst den Großteil der Elemente, die im Body von Dokumenten und Anwendungen verwendet werden.

Viele andere Kategorien sind Untergruppen bzw. Spezialfälle von Flow Content.

---

### Sectioning Content

Sectioning Content definiert den Geltungsbereich von `header`- und `footer`-Elementen.

Die aktuelle WHATWG-Definition umfasst insbesondere:

- `article`
- `aside`
- `nav`
- `section`

---

### Heading Content

Heading Content definiert Überschriften von Sections.

Dazu gehören:

- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `hgroup`, sofern es einen entsprechenden `h1`- bis `h6`-Nachfahren besitzt.

---

### Phrasing Content

Phrasing Content ist der Text eines Dokuments sowie Elemente, die diesen Text auf der Intra-Paragraph-Ebene auszeichnen.

Phrasing Content bildet damit einen wesentlichen Bestandteil von Paragraph-Inhalten.

---

### Embedded Content

Embedded Content umfasst Inhalte, die:

- eine andere Ressource in das Dokument einbinden,
- oder Inhalte aus einem anderen Vokabular in das Dokument integrieren.

WHATWG nennt unter anderem:

- `audio`
- `canvas`
- `embed`
- `iframe`
- `img`
- MathML `math`
- `object`
- `picture`
- SVG `svg`
- `video`

Elemente aus anderen Namespaces können für die entsprechenden Content-Model-Regeln ebenfalls als Embedded Content gelten, sofern die WHATWG-Regel dies vorsieht.

---

### Interactive Content

Interactive Content bezeichnet Inhalte, die ausdrücklich für Benutzerinteraktion bestimmt sind.

Die Kategorie kann abhängig von Attributen oder Zuständen sein.

Beispiele:

- `a`, wenn `href` vorhanden ist
- `audio`, wenn `controls` vorhanden ist
- `button`
- `details`
- `embed`
- `iframe`
- `img` unter den entsprechenden Bedingungen
- `input`, außer im Hidden-Zustand
- `label`
- `select`
- `textarea`
- `video`, wenn `controls` vorhanden ist

Die vollständige normative Zuordnung bleibt der aktuellen WHATWG-Definition vorbehalten.

---

### Palpable Content

Palpable Content ist eine weitere Content Category.

WHATWG verwendet sie insbesondere für Anforderungen daran, dass Elemente mit erlaubtem Flow- oder Phrasing-Inhalt nicht leer bzw. für Benutzer ohne wahrnehmbaren Inhalt bleiben.

Die Kategorie ist deshalb nicht einfach ein weiteres Synonym für Flow oder Phrasing Content.

---

### Script-supporting Elements

Script-supporting Elements repräsentieren selbst nichts bzw. werden nicht als regulär dargestellter Inhalt behandelt, unterstützen aber Script-Funktionalität.

Die aktuelle Definition nennt:

- `script`
- `template`

Diese Kategorie darf nicht mit "Scripting" als vollständigem HTML-Featurebereich verwechselt werden.

---

## Context

Context ist von Content Model zu unterscheiden.

In der WHATWG-Elementdefinition beschreibt der Context, wo ein Element verwendet werden kann.

WHATWG bezeichnet diese Angabe als nicht-normative Beschreibung.

Die eigentliche normative Einschränkung ergibt sich aus den Content Models der umgebenden Elemente.

### Konsequenz für ZE-WebLab

Für die zweite Ebene gilt:

```text
Context ≠ Content Model
```

Context wird deshalb nicht als Untertyp eines Content Models modelliert.

Es ist eine eigene Informationsdimension des Referenzmodells.

---

## Content Model

### Allgemeines Modell

Ein Content Model kann unter anderem aus folgenden Bausteinen bestehen:

- einer Content Category,
- mehreren Content Categories,
- konkreten Elementen,
- einem konkreten Elementtyp,
- `nothing`,
- `transparent`,
- einer spezialisierten Inhaltskategorie,
- einer Kombination mehrerer Bedingungen.

Die tatsächliche normative Definition ist immer der jeweiligen Elementdefinition zu entnehmen.

---

### Normative Bedeutung

Wenn die Spezifikation für ein Element beispielsweise `Phrasing content` als Content Model angibt, bedeutet dies nicht nur:

> Phrasing Content ist üblicherweise sinnvoll.

Vielmehr definiert WHATWG damit die zulässige Inhaltsstruktur des Elements.

---

## Processing Models

Content Models sind keine Processing Models.

Die beiden Konzepte sind zu trennen:

### Content Model

Beschreibt:

> Welche Inhalte darf das Element enthalten?

### Processing Model

Beschreibt:

> Wie muss ein User Agent bzw. eine HTML-Verarbeitung mit dem Element, seinen Attributen oder seinem Inhalt umgehen?

Beide können in einer Elementdefinition gemeinsam vorkommen.

Eine Content-Model-Prüfung darf deshalb nicht automatisch als Processing-Model-Prüfung betrachtet werden.

---

## DOM Interfaces / APIs

Content Models sind keine DOM APIs.

Das DOM Interface eines Elements wird in dessen Elementdefinition separat angegeben.

Ein Content Model beschreibt die zulässige Dokumentstruktur.

Ein DOM Interface beschreibt dagegen die programmatische Schnittstelle des entsprechenden DOM-Objekts.

Beispiel:

```text
Content Model:
    Welche Inhalte darf ein Element enthalten?

DOM Interface:
    Welche DOM-Eigenschaften und -Methoden besitzt das Element?
```

Beide Dimensionen sind über das Element miteinander verbunden, aber nicht identisch.

---

## Accessibility

WHATWG behandelt Accessibility-Anforderungen und Beziehungen zu ARIA bzw. Plattform-Accessibility-APIs in eigenen Abschnitten.

Ein Content Model darf deshalb nicht automatisch als Accessibility-Anforderung interpretiert werden.

Insbesondere gilt:

```text
zulässiger Inhalt
```

ist nicht automatisch gleichbedeutend mit:

```text
zugänglicher Inhalt
```

Für Accessibility-Aussagen sind die entsprechenden WHATWG-Regeln sowie gegebenenfalls externe normative Accessibility-Spezifikationen separat zu prüfen.

### Projektregel

Diese Datei macht keine eigenständigen Accessibility-Aussagen aus der bloßen Existenz eines Content Models.

---

## Sanitization

Sanitization ist eine eigenständige Informationsdimension.

WHATWG ordnet Sanitization-Informationen den jeweiligen Elementdefinitionen bzw. den entsprechenden Sanitization-Regeln zu.

Ein Content Model bestimmt nicht automatisch die Sanitization-Kategorie eines Elements.

Deshalb gilt:

```text
Content Model ≠ Sanitization Model
```

Für die vollständige Sanitization-Dokumentation ist die dafür vorgesehene zweite-Ebenen-Feature-Familie heranzuziehen.

---

## Konformitätsregeln

### Autorenkonformität

Autoren müssen die für das jeweilige Element geltenden Content-Model-Anforderungen einhalten.

Eine Inhaltsstruktur kann daher trotz syntaktisch erfolgreicher HTML-Verarbeitung nicht konform sein.

### Parser-Verhalten

Die Tatsache, dass ein Browser ungültige oder nicht konforme Strukturen verarbeitet, ändert nicht die normative Definition des Content Models.

Insbesondere darf aus erfolgreichem DOM-Aufbau nicht geschlossen werden:

> Das Content Model erlaubt diese Struktur.

Parser-Fehlerbehandlung und Autorenkonformität sind getrennte Konzepte.

### DOM-Manipulation

Auch dynamisch über DOM APIs erzeugte Strukturen dürfen nicht automatisch als konforme HTML-Strukturen angesehen werden.

Die Möglichkeit, einen DOM-Baum zu erzeugen, ist nicht identisch mit der Konformität einer HTML-Quelle.

---

## Querverweise

### Content Model ↔ Content Category

Content Categories werden als Bausteine für Content Models verwendet.

---

### Content Model ↔ Context

Context beschreibt die vorgesehene Verwendung eines Elements.

Content Model definiert normativ die zulässige Inhaltsstruktur.

---

### Content Model ↔ Elementdefinition

Jede Elementdefinition enthält ein Content Model.

Die erste Rechercheebene dokumentiert diese Informationen elementbezogen.

Diese Datei abstrahiert sie auf die gemeinsame Modell-Ebene.

---

### Content Model ↔ Attributes

Attribute können zustandsabhängige Content-Category-Zuordnungen beeinflussen.

Beispielsweise kann `href` dazu führen, dass ein `a`-Element Interactive Content ist.

---

### Content Model ↔ Parsing

Der Parser muss HTML-Token und Baumstrukturen entsprechend dem HTML-Parsing-Modell verarbeiten.

Das Parsing-Modell ist jedoch nicht identisch mit dem Content Model.

Eine nicht-konforme Inhaltsstruktur kann vom Parser dennoch verarbeitet und in einen DOM-Baum überführt werden.

---

### Content Model ↔ DOM

Das DOM repräsentiert die resultierende Dokumentstruktur.

Die Existenz eines DOM-Knotens beweist nicht, dass die entsprechende HTML-Quelle hinsichtlich des Content Models konform ist.

---

### Content Model ↔ SVG / MathML

SVG und MathML sind keine zusätzlichen nativen HTML-Elementfamilien.

Bestimmte SVG- und MathML-Inhalte werden in den HTML-Content-Model-Regeln ausdrücklich als Embedded Content bzw. über Foreign-Content-/Integrationsregeln berücksichtigt.

Die eigentlichen Integrationsregeln werden in den entsprechenden zweiten-Ebenen-Dateien behandelt.

---

## Status / V1

### WHATWG-Status

**Definiert:** Ja.

Content Models sind Bestandteil der normativen HTML-Elementdefinitionen.

**Normative Definition:** Ja.

**Normative Konformitätsanforderung:** Ja.

**Browser-Kompatibilität:** Nicht Bestandteil dieser Statusbewertung.

### ZE-WebLab-V1

**V1-Einstufung:** übergreifendes Referenzkonzept.

**Begründung:**

Content Models wurden in der ersten Rechercheebene bereits elementbezogen dokumentiert. Die übergreifende Systematik ist jedoch eigenständig und wird deshalb auf Rechercheebene 2 geführt.

### Abgrenzung

Nicht als eigene Elemente zählen:

- `Flow content`
- `Phrasing content`
- `Sectioning content`
- `Heading content`
- `Embedded content`
- `Interactive content`
- `Metadata content`
- `Palpable content`
- `Script-supporting elements`
- `Transparent`
- `nothing`

Diese Begriffe sind Content-Model- bzw. Content-Category-Konzepte.

---

## Erste-Ebene-Abdeckung

Die zwölf bestehenden Elementdateien dokumentieren Content Models innerhalb der jeweiligen Elementdefinitionen.

Die dort vorhandenen Angaben sind jedoch nicht automatisch eine vollständige Dokumentation des Content-Model-Systems.

### Bewertung

| Dimension | Erste Ebene | Zweite Ebene |
|---|---|---|
| Elementbezogenes Content Model | vorhanden | Querverweis |
| Content Model als übergreifendes Konzept | teilweise | vollständig relevant |
| `nothing` | elementbezogen | eigenständiges Konzept |
| Transparent | teilweise elementbezogen | eigenständiges Konzept |
| Content Categories | elementbezogene Zuordnungen | separates System |
| Paragraph-Konzept | teilweise | eigenständiges Konzept |
| Spezialisierte Form-Control-Inhalte | elementbezogen | übergreifende Modellierung erforderlich |
| Context | elementbezogen | separate Informationsdimension |
| Parsing | elementbezogen/teilweise | eigene Feature-Familie |
| DOM | elementbezogen | eigene Feature-Familie |

---

## Abdeckungsstatus

### Vollständig behandelt

In dieser Datei:

- Definition des Content Models
- Abgrenzung zu Context
- Abgrenzung zu Content Categories
- `nothing` Content Model
- transparente Content Models
- Paragraph-Konzept
- grundlegende Kategorienbeziehungen
- Abgrenzung zu Void Elements
- Abgrenzung zu Processing Models
- Abgrenzung zu DOM/APIs
- Abgrenzung zu Parsing
- Querverweise
- WHATWG-Status

### Teilweise behandelt

Nicht vollständig elementweise aufgelistet werden:

- jedes einzelne Content Model aller HTML-Elemente,
- jede einzelne Kombination konkreter Elemente innerhalb von Content Models,
- sämtliche spezialisierten Form-Control-Inhaltsmodelle,
- sämtliche Parsing-Sonderfälle.

Diese Informationen gehören überwiegend in die jeweiligen Elementdefinitionen bzw. die spezialisierten zweiten-Ebenen-Dateien.

### Nicht Bestandteil dieser Datei

- vollständiges Attributinventar,
- vollständiges Link-Type-Inventar,
- vollständiges DOM-API-Inventar,
- vollständige Parsing-Algorithmen,
- vollständige SVG-Integrationsregeln,
- vollständige MathML-Integrationsregeln,
- Browser-Support.

---

## Offene Punkte

### CM-O001 – Vollständige Spezialkategorien

Die aktuelle WHATWG-Spezifikation verwendet neben den allgemeinen Content Categories zusätzliche spezialisierte Inhaltskategorien.

Diese müssen bei der separaten Content-Category-Datei und bei der Form-Control-Referenz konsistent weitergeführt werden.

**Status:** offen für Querverweis-/Konsistenzprüfung, nicht offen hinsichtlich der Existenz des Konzepts.

---

### CM-O002 – Elementweise Detailabdeckung

Die vollständige Prüfung, ob jedes der in der ersten Ebene dokumentierten Elemente sein aktuelles WHATWG-Content Model korrekt wiedergibt, bleibt eine eigene Qualitätssicherungsaufgabe.

**Status:** separate V1-/Erste-Ebene-Prüfung.

---

### CM-O003 – Parsing-Konformität

Die Beziehung zwischen Content-Model-Konformität und tatsächlichem Parser-Verhalten muss in der Parsing-Datei detaillierter behandelt werden.

**Status:** separate Feature-Familie.

---

## Quellen / Referenzen

### Primärquelle

**WHATWG HTML Living Standard**

Relevante Bereiche:

- `3.2.4 Element definitions`
- `3.2.5 Content models`
- `3.2.5.1 The "nothing" content model`
- `3.2.5.2 Kinds of content`
- `3.2.5.3 Transparent content models`
- `3.2.5.4 Paragraphs`

### Projektquelle

**ZE-WebLab – HTML-Referenz**

Relevante Bestandsdateien:

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

### Externe normative Bezüge

Je nach konkretem Content Model können weitere normative Spezifikationen relevant sein, insbesondere:

- DOM Standard
- HTML Parsing / Tree Construction innerhalb der WHATWG HTML-Spezifikation
- SVG-Spezifikation
- MathML-Spezifikation

Diese Quellen ersetzen nicht die WHATWG-HTML-Definition des jeweiligen HTML-Content Models.

---

## Prüfstatus

**Feature-Familie:** Content Models

**Rechercheebene:** 2

**WHATWG geprüft:** Ja

**Normative Hauptabschnitte geprüft:** Ja

**Erste-Ebene-Bezug geprüft:** Ja

**Content Categories berücksichtigt:** Ja

**Context berücksichtigt:** Ja

**Transparent Content Models berücksichtigt:** Ja

**Nothing Content Model berücksichtigt:** Ja

**Paragraph-Konzept berücksichtigt:** Ja

**DOM/API als getrennte Ebene behandelt:** Ja

**Processing Models als getrennte Ebene behandelt:** Ja

**Parsing als getrennte Ebene behandelt:** Ja

**Accessibility nicht aus Content Models abgeleitet:** Ja

**Sanitization nicht aus Content Models abgeleitet:** Ja

**Browser-Support nicht als WHATWG-Status verwendet:** Ja

**Abschlussstatus:** Recherche für die übergreifende Feature-Familie `Content Models` abgeschlossen; elementweise Detailvalidierung bleibt Bestandteil der jeweiligen Elementreferenzen.