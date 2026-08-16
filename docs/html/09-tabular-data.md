# ZE-WebLab – HTML-Referenz: Tabular data

## Arbeitsstand / Quellenstand

- **Projekt:** ZE-WebLab
- **Datei:** `docs/html/09-tabular-data.md`
- **Themenbereich:** HTML Tabular data
- **WHATWG-Hauptabschnitt:** §4.9 Tabular data
- **Primärquelle:** WHATWG HTML Living Standard
- **Recherchegegenstand:** aktueller WHATWG-Stand der Living Standard
- **Geprüfter Spezifikationsstand:** 11. August 2026
- **Prüfstatus:** vollständig recherchiert
- **Browser-Kompatibilität:** nicht Bestandteil des WHATWG-Status dieser Datei
- **Accessibility:** WHATWG verweist für Autoren und Implementierer auf die einschlägigen Accessibility Considerations; diese Datei übernimmt daraus keine nicht selbst geprüften ARIA- oder AT-spezifischen Aussagen.
- **Sanitization:** die von WHATWG für die einzelnen Elemente ausgewiesenen Sanitization-Angaben wurden separat erfasst.
- **DOM:** die von WHATWG definierten bzw. referenzierten DOM Interfaces werden separat dokumentiert.

> Diese Datei dokumentiert §4.9 als fachliche WHATWG-Referenz. Die in diesem Abschnitt enthaltenen Algorithmen, Tabellenmodellregeln, Beispiele und Konformitätsanforderungen werden nicht als zusätzliche HTML-Elemente inventarisiert.

---

## WHATWG-Struktur

Der aktuelle WHATWG-Abschnitt §4.9 ist wie folgt aufgebaut:

1. **4.9 Tabular data**
2. **4.9.1 The `table` element**
   - 4.9.1.1 Techniques for describing tables
   - 4.9.1.2 Techniques for table design
3. **4.9.2 The `caption` element**
4. **4.9.3 The `colgroup` element**
5. **4.9.4 The `col` element**
6. **4.9.5 The `tbody` element**
7. **4.9.6 The `thead` element**
8. **4.9.7 The `tfoot` element**
9. **4.9.8 The `tr` element**
10. **4.9.9 The `td` element**
11. **4.9.10 The `th` element**
12. **4.9.11 Attributes common to `td` and `th` elements**
13. **4.9.12 Processing model**
    - 4.9.12.1 Forming a table
    - 4.9.12.2 Forming relationships between data cells and header cells
14. **4.9.13 Examples**

Damit umfasst §4.9 sowohl die HTML-Elemente des Tabellenmodells als auch normative Unterkonzepte und Verarbeitungsalgorithmen.

---

## Inventar

### HTML-Elemente

| Element | WHATWG-Abschnitt | Feature-Typ | Content Categories | Context | Content Model | Tag Omission | Content Attributes | DOM Interface |
|---|---|---|---|---|---|---|---|---|
| `table` | 4.9.1 | HTML element | Flow, Palpable | Wo Flow Content erwartet wird | `caption?`, `colgroup*`, `thead?`, danach `tbody*` oder `tr+`, danach `tfoot?`, jeweils mit möglichen script-supporting elements | Keine Auslassung | Global Attributes | `HTMLTableElement` |
| `caption` | 4.9.2 | HTML element | Keine | Als erstes Element-Kind von `table` | Flow Content, aber keine Nachfahren-`table` | End-Tag kann unter Bedingungen entfallen | Global Attributes | `HTMLTableCaptionElement` |
| `colgroup` | 4.9.3 | HTML element | Keine | Als Kind von `table`, nach `caption`, vor `thead`/`tbody`/`tfoot`/`tr` | Mit `span`: Nothing; ohne `span`: `col*` und `template*` | Start- und End-Tag unter Bedingungen auslassbar | Global Attributes, `span` | `HTMLTableColElement` |
| `col` | 4.9.4 | HTML element | Keine | Kind eines `colgroup` ohne `span` | Nothing | Kein End-Tag | Global Attributes, `span` | `HTMLTableColElement` |
| `tbody` | 4.9.5 | HTML element | Keine | Kind von `table` in der vorgesehenen Tabellenreihenfolge | `tr*` und script-supporting elements | End-Tag unter Bedingungen auslassbar | Global Attributes | `HTMLTableSectionElement` |
| `thead` | 4.9.6 | HTML element | Keine | Kind von `table`, vor `tbody`/`tfoot`/`tr`, höchstens ein `thead` | `tr*` und script-supporting elements | End-Tag bei anschließendem `tbody` oder `tfoot` auslassbar | Global Attributes | `HTMLTableSectionElement` |
| `tfoot` | 4.9.7 | HTML element | Keine | Kind von `table`, nach den anderen Tabellenkomponenten, höchstens ein `tfoot` | `tr*` und script-supporting elements | End-Tag bei fehlendem weiteren Inhalt im Parent auslassbar | Global Attributes | `HTMLTableSectionElement` |
| `tr` | 4.9.8 | HTML element | Keine | Kind von `thead`, `tbody`, `tfoot` oder unter den speziellen direkten-`table`-Bedingungen | `td*`, `th*` und script-supporting elements | End-Tag unter Bedingungen auslassbar | Global Attributes | `HTMLTableRowElement` |
| `td` | 4.9.9 | HTML element | Keine | Kind von `tr` | Flow Content | End-Tag unter Bedingungen auslassbar | Global Attributes, `colspan`, `rowspan`, `headers` | `HTMLTableCellElement` |
| `th` | 4.9.10 | HTML element | Keine | Kind von `tr` | Flow Content ohne `header`, `footer`, Sectioning Content oder Heading Content als Nachfahren | End-Tag unter Bedingungen auslassbar | Global Attributes, `colspan`, `rowspan`, `headers`, `scope`, `abbr` | `HTMLTableCellElement` |

### Nicht als zusätzliche Elemente inventarisierte Konzepte

Folgende Bestandteile von §4.9 sind eigenständige fachliche Konzepte und keine weiteren HTML-Elemente:

- Table model
- Tabellen-Slots
- Rows
- Columns
- Cells
- Row groups
- Column groups
- Table model errors
- Header-cell assignment
- Header cell categories
- Processing model
- Techniques for describing tables
- Techniques for table design
- Beispiele aus §4.9.13

---

# Detailprüfung: `table`

## WHATWG-Abschnitt

**§4.9.1 The `table` element**

## Semantik

`table` repräsentiert Daten mit mehr als einer Dimension in Form einer Tabelle.

Das Element nimmt am **table model** teil. Die Nachfahren des Elements bilden Zeilen, Spalten und Zellen. Das Tabellenmodell bildet daraus ein Raster. Die Zellen einer konformen Tabelle müssen dieses Raster vollständig und ohne Überlappungen abdecken.

Eine Tabelle darf nicht als reines Layout-Hilfsmittel verwendet werden. Die Verwendung von Tabellen zur visuellen Seitenlayoutsteuerung ist nach WHATWG nicht konform.

## Content Categories

- Flow content
- Palpable content

## Context

`table` kann verwendet werden, wo Flow Content erwartet wird.

## Content Model

In dieser Reihenfolge:

1. optional ein `caption`
2. null oder mehr `colgroup`
3. optional ein `thead`
4. entweder:
   - null oder mehr `tbody`
   - oder ein oder mehr `tr`
5. optional ein `tfoot`

Script-supporting elements können entsprechend den WHATWG-Regeln zwischengeschaltet sein.

## Tag Omission

- Start-Tag: nicht auslassbar
- End-Tag: nicht auslassbar

## Content Attributes

- Global Attributes

Der Abschnitt weist außerdem historische, nicht konforme Attribute wie `summary`, `border`, `cellspacing` und `cellpadding` im Zusammenhang mit Heuristiken zur Erkennung von Layout-Tabellen aus. Diese gehören nicht zum konformen aktuellen Content-Attribute-Inventar von `table`.

## Accessibility

WHATWG weist für `table` gesonderte Accessibility Considerations für Autoren und Implementierer aus.

Besonders relevant ist die normative Zweckbestimmung: Tabellen sind für tabellarische Daten gedacht und nicht für Layout. Die Spezifikation weist darauf hin, dass Layout-Tabellen für Nutzer von Accessibility-Tools, insbesondere Screenreadern, problematisch sein können.

Für komplexe Tabellen empfiehlt WHATWG, zusätzliche Informationen bereitzustellen, die den Aufbau und die Interpretation der Tabelle erklären.

## Sanitization

WHATWG weist für `table` die **Default**-Sanitization aus.

## DOM Interface

`HTMLTableElement`

Das Interface stellt unter anderem bereit:

- `caption`
- `createCaption()`
- `deleteCaption()`
- `tHead`
- `createTHead()`
- `deleteTHead()`
- `tFoot`
- `createTFoot()`
- `deleteTFoot()`
- `tBodies`
- `createTBody()`
- `rows`
- `insertRow()`
- `deleteRow()`

Die Tabelle besitzt damit eine eigene DOM-API zur Verwaltung ihrer strukturellen Bestandteile.

---

# Detailprüfung: Tabellenbeschreibung

## §4.9.1.1 Techniques for describing tables

WHATWG behandelt komplexe Tabellen ausdrücklich als ein Problem der Verständlichkeit und Navigation.

Eine Beschreibung einer komplexen Tabelle sollte insbesondere:

- den Zweck der Tabelle erklären,
- ihre grundlegende Zellstruktur erläutern,
- Trends oder Muster hervorheben,
- erklären, wie die Tabelle zu benutzen bzw. zu interpretieren ist.

WHATWG zeigt mehrere Möglichkeiten:

- erläuternde Prosa vor oder neben der Tabelle,
- zusätzliche Informationen innerhalb von `caption`,
- Verwendung von `details` innerhalb von `caption`,
- Kombination mit `figure` und `figcaption`,
- Verbesserung der Tabellenstruktur selbst.

Die Spezifikation bevorzugt grundsätzlich eine Tabellenstruktur, die möglichst selbsterklärend ist.

Ein Beispiel ist die Umordnung von Spalten und Zeilen, sodass die Header sinnvoll angeordnet sind und dadurch eine zusätzliche Erläuterung bzw. ein Teil der expliziten `headers`-Beziehungen entfallen kann.

## Fachliche Einordnung

Dieser Unterabschnitt ist kein Elementinventar. Die dort genannten Techniken begründen keine zusätzlichen HTML-Elemente innerhalb der Tabellenreferenz.

---

# Detailprüfung: Tabellendesign

## §4.9.1.2 Techniques for table design

Gutes Tabellendesign soll die Lesbarkeit und Nutzbarkeit verbessern.

WHATWG nennt unter anderem:

- sichtbare Zeilen- und Spaltenbegrenzungen,
- alternierende Zeilenhintergründe,
- monospaced Fonts bei großen Mengen numerischer Daten,
- Navigation in einer Rasterstruktur bei sprachbasierter Ausgabe,
- Ansage der zugehörigen Header vor dem Inhalt einer Zelle.

Autoren werden ausdrücklich dazu angehalten, CSS für diese visuellen bzw. präsentationsbezogenen Effekte zu verwenden.

User Agents werden dazu angehalten, solche Darstellungsweisen insbesondere dann einzusetzen, wenn kein CSS verwendet wird und die Tabelle nicht als Layout-Tabelle klassifiziert wurde.

---

# Detailprüfung: `caption`

## WHATWG-Abschnitt

**§4.9.2 The `caption` element**

## Semantik

`caption` repräsentiert den Titel der zugehörigen Tabelle.

Wenn `caption` einen `table`-Parent besitzt, ist es der Titel dieser Tabelle.

## Content Categories

Keine.

## Context

`caption` darf als erstes Element-Kind eines `table` verwendet werden.

## Content Model

Flow Content, jedoch ohne `table`-Elemente als Nachfahren.

## Tag Omission

Das End-Tag kann entfallen, wenn `caption` nicht unmittelbar von ASCII Whitespace oder einem Kommentar gefolgt wird.

## Content Attributes

- Global Attributes

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

Eine Caption kann Kontext für eine Tabelle liefern und dadurch deren Verständnis wesentlich verbessern.

Wenn eine `table` das einzige weitere Content-Element eines `figure` neben dessen `figcaption` ist, empfiehlt WHATWG, statt `caption` die `figcaption`-Struktur zu verwenden.

## Sanitization

- Default

## DOM Interface

`HTMLTableCaptionElement`

---

# Detailprüfung: `colgroup`

## WHATWG-Abschnitt

**§4.9.3 The `colgroup` element**

## Semantik

`colgroup` repräsentiert eine Gruppe von einer oder mehreren Spalten der übergeordneten Tabelle.

## Content Categories

Keine.

## Context

Als Kind von `table`:

- nach beliebigen `caption`-Elementen,
- vor `thead`, `tbody`, `tfoot` und `tr`.

## Content Model

Wenn `span` vorhanden ist:

- Nothing.

Wenn `span` nicht vorhanden ist:

- null oder mehr `col`
- null oder mehr `template`

## Tag Omission

### Start-Tag

Der Start-Tag kann entfallen, wenn:

- das erste Element innerhalb von `colgroup` ein `col` ist,
- und das Element nicht unmittelbar auf ein anderes `colgroup` folgt, dessen End-Tag ausgelassen wurde.

Bei einem leeren `colgroup` kann der Start-Tag nicht auf diese Weise entfallen.

### End-Tag

Der End-Tag kann entfallen, wenn `colgroup` nicht unmittelbar von ASCII Whitespace oder einem Kommentar gefolgt wird.

## Content Attributes

- Global Attributes
- `span`

`span` gibt die Anzahl der von der Gruppe umfassten Spalten an.

Wenn `colgroup` keine `col`-Kinder besitzt, darf `span` verwendet werden. Der Wert muss eine gültige positive Zahl bis einschließlich 1000 sein.

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

## Sanitization

- Default
- zusätzlich `span`

## DOM Interface

`HTMLTableColElement`

---

# Detailprüfung: `col`

## WHATWG-Abschnitt

**§4.9.4 The `col` element**

## Semantik

`col` repräsentiert eine oder mehrere Spalten innerhalb der durch das übergeordnete `colgroup` repräsentierten Spaltengruppe.

## Content Categories

Keine.

## Context

Als Kind eines `colgroup`, das selbst kein `span`-Attribut besitzt.

## Content Model

- Nothing

## Tag Omission

`col` besitzt keinen End-Tag.

## Content Attributes

- Global Attributes
- `span`

`span` gibt die Anzahl der Spalten an, die das Element repräsentiert.

Der konforme Wert ist eine gültige positive Zahl bis einschließlich 1000.

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

## Sanitization

- Default
- zusätzlich `span`

## DOM Interface

`HTMLTableColElement`

`col` verwendet dasselbe Interface wie `colgroup`.

---

# Detailprüfung: `tbody`

## WHATWG-Abschnitt

**§4.9.5 The `tbody` element**

## Semantik

`tbody` repräsentiert einen Block von Zeilen, die den Datenkörper der übergeordneten Tabelle bilden.

## Content Categories

Keine.

## Context

Als Kind von `table`:

- nach `caption`,
- nach `colgroup`,
- nach `thead`,
- und nur unter den von WHATWG definierten Bedingungen, insbesondere nicht neben direkten `tr`-Kindern in der dafür ausgeschlossenen Konstellation.

## Content Model

- null oder mehr `tr`
- script-supporting elements

## Tag Omission

Der End-Tag kann unter den von WHATWG definierten Bedingungen entfallen, insbesondere wenn unmittelbar ein weiterer Tabellenbereich wie `tbody`, `tfoot` oder das Ende des Parent-Kontexts folgt.

## Content Attributes

- Global Attributes

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

## Sanitization

- Default

## DOM Interface

`HTMLTableSectionElement`

Das Interface wird ebenfalls für `thead` und `tfoot` verwendet.

Wesentliche Operationen sind:

- `rows`
- `insertRow()`
- `deleteRow()`

`rows` liefert die `tr`-Elemente des jeweiligen Tabellenbereichs.

---

# Detailprüfung: `thead`

## WHATWG-Abschnitt

**§4.9.6 The `thead` element**

## Semantik

`thead` repräsentiert den Block von Zeilen, die die Spaltenbezeichnungen bzw. Header und gegebenenfalls zusätzliche nicht-headerbezogene Zellen des Tabellenkopfs enthalten.

## Content Categories

Keine.

## Context

Als Kind von `table`:

- nach `caption` und `colgroup`,
- vor `tbody`, `tfoot` und direkten `tr`,
- höchstens ein `thead` als Kind derselben Tabelle.

## Content Model

- null oder mehr `tr`
- script-supporting elements

## Tag Omission

Der End-Tag kann entfallen, wenn `thead` unmittelbar von `tbody` oder `tfoot` gefolgt wird.

## Content Attributes

- Global Attributes

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

## Sanitization

- Default

## DOM Interface

`HTMLTableSectionElement`

---

# Detailprüfung: `tfoot`

## WHATWG-Abschnitt

**§4.9.7 The `tfoot` element**

## Semantik

`tfoot` repräsentiert den Block von Zeilen, die die Spaltensummen bzw. Tabellen-Footer für die übergeordnete Tabelle darstellen.

## Content Categories

Keine.

## Context

Als Kind von `table`:

- nach `caption`,
- `colgroup`,
- `thead`,
- `tbody`,
- `tr`,
- höchstens ein `tfoot`.

## Content Model

- null oder mehr `tr`
- script-supporting elements

## Tag Omission

Der End-Tag kann entfallen, wenn im Parent kein weiterer Inhalt folgt.

## Content Attributes

- Global Attributes

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

## Sanitization

- Default

## DOM Interface

`HTMLTableSectionElement`

---

# Detailprüfung: `tr`

## WHATWG-Abschnitt

**§4.9.8 The `tr` element**

## Semantik

`tr` repräsentiert eine Zeile von Zellen in einer Tabelle.

## Content Categories

Keine.

## Context

`tr` kann verwendet werden:

- als Kind von `thead`,
- als Kind von `tbody`,
- als Kind von `tfoot`,
- unter den speziellen Bedingungen auch direkt als Kind von `table`.

Bei direkter Verwendung unter `table` gelten die von WHATWG festgelegten Strukturbedingungen. Insbesondere darf diese Form nicht mit einer vorhandenen `tbody`-Struktur vermischt werden, die den direkten `tr`-Kindern widerspricht.

## Content Model

- null oder mehr `td`
- `th`
- script-supporting elements

## Tag Omission

Der End-Tag kann entfallen:

- wenn unmittelbar ein weiterer `tr` folgt,
- oder wenn im Parent kein weiterer Inhalt vorhanden ist.

## Content Attributes

- Global Attributes

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

## Sanitization

- Default

## DOM Interface

`HTMLTableRowElement`

Wesentliche Mitglieder:

- `rowIndex`
- `sectionRowIndex`
- `cells`
- `insertCell()`
- `deleteCell()`

`rowIndex` bezeichnet die Position der Zeile in der `rows`-Liste der Tabelle und liefert `-1`, wenn das Element nicht Teil einer Tabelle ist.

`sectionRowIndex` bezeichnet die Position innerhalb des Tabellenbereichs und liefert `-1`, wenn das Element nicht Teil eines Tabellenbereichs ist.

---

# Detailprüfung: `td`

## WHATWG-Abschnitt

**§4.9.9 The `td` element**

## Semantik

`td` repräsentiert eine Datenzelle einer Tabelle.

## Content Categories

Keine.

## Context

Als Kind von `tr`.

## Content Model

- Flow Content

## Tag Omission

Der End-Tag kann entfallen:

- wenn unmittelbar ein weiteres `td` oder `th` folgt,
- oder wenn im Parent kein weiterer Inhalt vorhanden ist.

## Content Attributes

- Global Attributes
- `colspan`
- `rowspan`
- `headers`

### `colspan`

Gibt an, über wie viele Spalten sich die Zelle erstreckt.

Der konforme Wert ist eine gültige positive Zahl bis einschließlich 1000.

### `rowspan`

Gibt an, über wie viele Zeilen sich die Zelle erstreckt.

Der konforme Wert ist eine gültige nicht-negative Zahl bis einschließlich 65534.

Der Wert `0` hat eine besondere Bedeutung: Die Zelle erstreckt sich über alle verbleibenden Zeilen der jeweiligen Zeilengruppe.

### `headers`

Ordnet die Zelle anhand von IDs Header-Zellen zu.

Die `headers`-Beziehung ist Teil des Tabellenmodells.

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

User Agents können in nicht-visuellen Umgebungen oder wenn eine zweidimensionale Darstellung ungeeignet ist, Kontextinformationen zur Zelle bereitstellen.

Dazu können insbesondere:

- Position der Zelle im Tabellenmodell,
- zugehörige Header-Zellen

gehören.

## Sanitization

- Default
- `colspan`
- `headers`
- `rowspan`

## DOM Interface

`HTMLTableCellElement`

Wesentliche Mitglieder:

- `colSpan`
- `rowSpan`
- `headers`
- `cellIndex`

Das Interface wird ebenfalls für `th` verwendet.

---

# Detailprüfung: `th`

## WHATWG-Abschnitt

**§4.9.10 The `th` element**

## Semantik

`th` repräsentiert eine Header-Zelle in einer Tabelle.

## Content Categories

Keine.

## Context

Als Kind von `tr`.

## Content Model

Flow Content, jedoch ohne Nachfahren aus folgenden Gruppen:

- `header`
- `footer`
- Sectioning Content
- Heading Content

## Tag Omission

Der End-Tag kann entfallen:

- wenn unmittelbar ein `td` oder `th` folgt,
- oder wenn im Parent kein weiterer Inhalt vorhanden ist.

## Content Attributes

- Global Attributes
- `colspan`
- `rowspan`
- `headers`
- `scope`
- `abbr`

### `colspan`

Anzahl der Spalten, über die sich die Header-Zelle erstreckt.

Gültiger positiver Wert bis einschließlich 1000.

### `rowspan`

Anzahl der Zeilen, über die sich die Header-Zelle erstreckt.

Gültiger nicht-negativer Wert bis einschließlich 65534.

`0` bedeutet: alle verbleibenden Zeilen der jeweiligen Zeilengruppe.

### `headers`

Verknüpft die Zelle explizit mit Header-Zellen über deren IDs.

### `scope`

Definiert den Bereich, auf den sich die Header-Zelle bezieht.

`scope` ist ein enumeriertes Attribut mit folgenden Zuständen:

| Keyword | Zustand | Bedeutung |
|---|---|---|
| `row` | Row | Header gilt für nachfolgende Zellen derselben Zeile bzw. Zeilen |
| `col` | Column | Header gilt für nachfolgende Zellen derselben Spalte bzw. Spalten |
| `rowgroup` | Row Group | Header gilt für die verbleibenden Zellen der Zeilengruppe |
| `colgroup` | Column Group | Header gilt für die verbleibenden Zellen der Spaltengruppe |

Missing value default und invalid value default sind beide der **Auto State**.

Im Auto State wird die Zuordnung anhand des Tabellenkontexts bestimmt.

Für `rowgroup` und `colgroup` bestehen zusätzliche Konformitätsregeln:

- `rowgroup` darf nicht verwendet werden, wenn die Header-Zelle nicht in einer Zeilengruppe verankert ist.
- `colgroup` darf nicht verwendet werden, wenn die Header-Zelle nicht in einer Spaltengruppe verankert ist.

### `abbr`

`abbr` ist eine alternative Bezeichnung für die Header-Zelle.

Der Wert soll als alternative Bezeichnung verwendet werden, wenn die Header-Zelle in anderen Kontexten referenziert wird, beispielsweise bei der Ausgabe der auf eine Datenzelle angewendeten Header.

## Accessibility

WHATWG weist eigene Accessibility Considerations für Autoren und Implementierer aus.

Die `th`-Struktur ist zentral für die semantische Zuordnung von Headern und Datenzellen.

## Sanitization

- Default
- `abbr`
- `colspan`
- `headers`
- `rowspan`
- `scope`

## DOM Interface

`HTMLTableCellElement`

`th` verwendet dasselbe DOM Interface wie `td`.

`scope` und `abbr` sind im Interface vorhanden, sind jedoch laut WHATWG nur für `th` konform.

---

# Gemeinsame Attribute von `td` und `th`

## WHATWG-Abschnitt

**§4.9.11 Attributes common to `td` and `th` elements**

Die beiden Elemente teilen drei zentrale Tabellenmodellattribute:

- `colspan`
- `rowspan`
- `headers`

## `colspan`

Der Wert muss eine gültige positive Ganzzahl bis einschließlich 1000 sein.

Die Zahl bezeichnet die Anzahl der Spalten, die von der Zelle überspannt werden.

## `rowspan`

Der Wert muss eine gültige nicht-negative Ganzzahl bis einschließlich 65534 sein.

Der Sonderwert `0` bedeutet, dass die Zelle alle verbleibenden Zeilen der jeweiligen Zeilengruppe überspannt.

## Überlappungen

`colspan` und `rowspan` dürfen nicht dazu verwendet werden, Zellen im Tabellenmodell überlappen zu lassen.

Überlappende Zellen führen zu einem **table model error**.

## `headers`

`headers` stellt eine explizite Zuordnung von Daten- bzw. Header-Zellen über ID-Werte her.

Die detaillierte Verarbeitung dieser Beziehung erfolgt im Abschnitt **4.9.12.2 Forming relationships between data cells and header cells**.

---

# Tabellenmodell

## Fachliche Rolle

Das **table model** ist ein eigenständiges normatives Konzept innerhalb von §4.9.

Es ist nicht selbst ein HTML-Element.

Das Tabellenmodell beschreibt unter anderem:

- Tabellen,
- Slots,
- Zellen,
- Zeilen,
- Spalten,
- Zeilengruppen,
- Spaltengruppen,
- Caption-Zuordnung,
- räumliche Ausdehnung der Zellen,
- Header-Beziehungen.

Eine Tabelle besitzt ein Raster aus Slots.

Jede Zelle wird auf eine bestimmte Position im Raster verankert und besitzt eine Breite und Höhe.

Die Zellen müssen das Raster vollständig und ohne Überlappung abdecken.

---

# Table model errors

Ein **table model error** liegt vor, wenn die durch `table` und seine Nachfahren repräsentierten Daten das Tabellenmodell verletzen.

WHATWG stellt ausdrücklich fest:

> Documents must not have table model errors.

Für ZE-WebLab ist daher zwischen:

1. syntaktischer Existenz eines `table`-Elements,
2. struktureller Konformität seiner Kinder,
3. Gültigkeit des resultierenden Tabellenmodells

zu unterscheiden.

---

# Processing Model

## WHATWG-Abschnitt

**§4.9.12 Processing model**

Der Processing-Model-Abschnitt ist kein Elementinventar.

Er definiert die Verarbeitung des Tabelleninhalts durch User Agents.

Er umfasst:

- **4.9.12.1 Forming a table**
- **4.9.12.2 Forming relationships between data cells and header cells**

---

# Forming a table

## §4.9.12.1

Der Algorithmus bestimmt unter anderem:

- Tabellenbreite,
- Tabellenhöhe,
- Positionen der Spalten,
- Positionen der Zeilen,
- Zeilengruppen,
- Spaltengruppen,
- Zellpositionen,
- Zellbreiten,
- Zellhöhen,
- Table-model-Fehler.

Zu Beginn werden Breite und Höhe des Tabellenrasters auf null gesetzt.

Ein leerer Tabelleninhalt ergibt entsprechend eine leere Tabelle.

Die erste `caption` wird der Tabelle zugeordnet.

Danach wird der Tabelleninhalt in der durch das Modell vorgesehenen Reihenfolge verarbeitet.

Relevante Strukturkomponenten sind:

- `colgroup`
- `thead`
- `tbody`
- `tfoot`
- `tr`

Andere Elemente werden in diesem Verarbeitungsschritt entsprechend dem Algorithmus übersprungen bzw. nicht als strukturbildende Tabellenkomponenten behandelt.

---

# Verarbeitung von `colgroup` und `col`

Bei `colgroup` mit `col`-Kindern wird die Anzahl der Spalten anhand der jeweiligen `span`-Werte bestimmt.

Für `col` gilt:

- fehlt `span`, wird effektiv eine Spalte angenommen,
- ungültige oder nullwertige Werte werden entsprechend dem Processing Model behandelt,
- Werte oberhalb 1000 werden für die Verarbeitung auf 1000 begrenzt.

Die Spalten werden anschließend einer Spaltengruppe zugeordnet.

Bei einem `colgroup` ohne `col`-Kinder wird dessen eigenes `span`-Attribut zur Bestimmung der Spaltenanzahl verwendet.

---

# Verarbeitung von Zeilengruppen

`thead`, `tbody` und `tfoot` bilden Zeilengruppen.

Der Processing Model berücksichtigt ihre Position und ihre Beziehung zu den einzelnen `tr`.

`tfoot` besitzt dabei eine besondere Verarbeitung im Algorithmus: Es existiert eine Liste der noch ausstehenden `tfoot`-Elemente.

Die konkrete Reihenfolge der Verarbeitung im Algorithmus darf nicht mit der bloßen Quellreihenfolge der Elemente gleichgesetzt werden.

---

# Verarbeitung von Zellen

Beim Verarbeiten einer `tr` werden dessen `td`- und `th`-Kinder als Zellen verarbeitet.

Für jede Zelle werden unter anderem bestimmt:

- Startposition,
- `colspan`,
- `rowspan`,
- Breite,
- Höhe,
- Zelltyp.

Ein `th` wird als Header-Zelle behandelt.

Ein `td` wird als Datenzelle behandelt.

Wenn eine neu erzeugte Zelle bereits belegte Slots abdecken würde, entsteht ein **table model error**.

---

# Downward-growing cells

Das Tabellenmodell kennt Zellen, die aufgrund ihrer `rowspan`-Ausdehnung nach unten wachsen.

Der Algorithmus führt hierfür eine Liste von Zellen, die weiter nach unten ausgedehnt werden müssen.

Nach Verarbeitung eines entsprechenden Tabellenbereichs werden diese Zellen auf die nächsten Slots erweitert.

Diese Verarbeitung ist Teil des normativen Tabellenmodells und keine zusätzliche HTML-Elementdefinition.

---

# Beziehungen zwischen Daten- und Header-Zellen

## §4.9.12.2

Jede Zelle kann null oder mehr Header-Zellen zugeordnet bekommen.

Der Algorithmus arbeitet mit einer **header list**.

Für eine Principal Cell werden zunächst ihre Koordinaten im Tabellenmodell bestimmt.

## Explizite `headers`-Zuordnung

Wenn `headers` vorhanden ist:

1. Der Attributwert wird an ASCII Whitespace aufgeteilt.
2. Daraus entsteht eine Liste von ID-Tokens.
3. Für jeden Token wird das erste Element im Dokument mit entsprechender ID betrachtet.
4. Nur eine Zelle derselben Tabelle wird als Header-Zuordnung aufgenommen.
5. Die Principal Cell selbst wird nicht als ihre eigene Header-Zelle aufgenommen.

Damit ist `headers` keine bloße Zeichenkette ohne Verarbeitung, sondern Teil des normativen Header-Zuordnungsalgorithmus.

---

# Automatische Header-Zuordnung

Wenn `headers` nicht vorhanden ist, bestimmt WHATWG die Header-Beziehungen anhand der räumlichen Lage im Tabellenmodell.

Der Algorithmus berücksichtigt unter anderem:

- Position,
- Breite,
- Höhe,
- Header-Zellstatus,
- Zeilen- und Spaltengruppen,
- `scope`,
- Datenzellen,
- Headerblöcke.

Die resultierende Header-Liste kann dadurch automatisch ermittelt werden.

---

# Header-Zelltypen

WHATWG unterscheidet für die Verarbeitung insbesondere:

- Column Header
- Row Header
- Column Group Header
- Row Group Header

## Column Header

Eine Header-Zelle ist insbesondere dann Column Header, wenn:

- `scope` im Column State ist,

oder:

- `scope` im Auto State ist,
- und sich in den von der Header-Zelle abgedeckten vertikalen Slots keine Datenzellen befinden.

## Row Header

Eine Header-Zelle ist insbesondere dann Row Header, wenn:

- `scope` im Row State ist,

oder:

- `scope` im Auto State ist,
- die Zelle kein Column Header ist,
- und sich in den von ihr abgedeckten horizontalen Slots keine Datenzellen befinden.

## Column Group Header

Eine Header-Zelle ist Column Group Header, wenn `scope` im Column Group State ist.

## Row Group Header

Eine Header-Zelle ist Row Group Header, wenn `scope` im Row Group State ist.

---

# Leere Zellen

WHATWG definiert eine Zelle als **empty cell**, wenn:

- sie keine Elemente enthält,
- und ihr gegebenenfalls vorhandener Textinhalt ausschließlich aus ASCII Whitespace besteht.

Diese Definition ist Teil des Tabellenverarbeitungsmodells.

---

# Accessibility

## WHATWG-Ebene

Für die Elemente des Tabellenmodells stellt WHATWG jeweils eigene Accessibility Considerations für Autoren und Implementierer bereit.

Die HTML-Spezifikation selbst verweist hierfür auf die einschlägigen Accessibility-Spezifikationen.

## Fachlich belegbare Punkte aus §4.9

Aus dem Abschnitt lassen sich insbesondere folgende Anforderungen bzw Empfehlungen ableiten:

- Tabellen sind für tabellarische Daten bestimmt.
- Layout-Tabellen sind nicht konform.
- Tabellen können für Nutzer von Accessibility-Tools schwer verständlich sein.
- User Agents sollen Zellen klar voneinander abgrenzen, sofern die Tabelle nicht als Layout-Tabelle klassifiziert wurde.
- Komplexe Tabellen sollten Informationen bereitstellen, die ihre Struktur und Interpretation verständlich machen.
- Header-Beziehungen sind für die Navigation und Interpretation von Tabellen relevant.
- `th`, `scope` und `headers` sind Bestandteile des semantischen Tabellenmodells.
- Nicht-visuelle User Agents können Zellkontext anhand der Tabellenstruktur und der zugeordneten Header bereitstellen.
- `abbr` kann für die Ausgabe von Header-Bezeichnungen verwendet werden.

Nicht aus §4.9 selbst abzuleiten sind konkrete Aussagen über das Verhalten eines bestimmten Screenreaders oder einer bestimmten Browser-/Assistive-Technology-Kombination.

---

# Sanitization

WHATWG weist für die Tabellen-Elemente explizit Sanitization-Informationen aus.

## `table`

- Default

## `caption`

- Default

## `colgroup`

- Default
- `span`

## `col`

- Default
- `span`

## `tbody`

- Default

## `thead`

- Default

## `tfoot`

- Default

## `tr`

- Default

## `td`

- Default
- `colspan`
- `headers`
- `rowspan`

## `th`

- Default
- `abbr`
- `colspan`
- `headers`
- `rowspan`
- `scope`

Damit ist Sanitization als eigene Referenzdimension zu behandeln und nicht mit Content Model oder Konformität gleichzusetzen.

---

# DOM Interfaces

## `HTMLTableElement`

Für `table`.

Wesentliche Tabellenverwaltungs-APIs:

- `caption`
- `createCaption()`
- `deleteCaption()`
- `tHead`
- `createTHead()`
- `deleteTHead()`
- `tFoot`
- `createTFoot()`
- `deleteTFoot()`
- `tBodies`
- `createTBody()`
- `rows`
- `insertRow()`
- `deleteRow()`

## `HTMLTableCaptionElement`

Für `caption`.

## `HTMLTableColElement`

Für `colgroup` und `col`.

## `HTMLTableSectionElement`

Für:

- `tbody`
- `thead`
- `tfoot`

Wesentliche APIs:

- `rows`
- `insertRow()`
- `deleteRow()`

## `HTMLTableRowElement`

Für `tr`.

Wesentliche APIs:

- `rowIndex`
- `sectionRowIndex`
- `cells`
- `insertCell()`
- `deleteCell()`

## `HTMLTableCellElement`

Für:

- `td`
- `th`

Wesentliche Mitglieder:

- `colSpan`
- `rowSpan`
- `headers`
- `cellIndex`
- `scope`
- `abbr`

`scope` und `abbr` sind nur für `th` konform.

---

# DOM-Sonderregeln

## `HTMLTableElement`

Die WHATWG-Spezifikation definiert für die Tabellen-API konkrete DOM-Operationen.

Beispiele:

- `createCaption()` stellt sicher, dass eine `caption` existiert.
- `deleteCaption()` entfernt die erste `caption`.
- `createTHead()` stellt sicher, dass ein `thead` existiert.
- `deleteTHead()` entfernt den ersten `thead`.
- `createTFoot()` stellt sicher, dass ein `tfoot` existiert.
- `deleteTFoot()` entfernt den ersten `tfoot`.
- `createTBody()` erzeugt und fügt einen `tbody` ein.
- `insertRow()` erzeugt eine `tr` und bei Bedarf einen `tbody`.
- `deleteRow()` entfernt eine bestimmte Tabellenzeile.

Für ungültige Indizes können `IndexSizeError`-DOMExceptions ausgelöst werden.

Bei `tHead` und `tFoot` bestehen zusätzliche Typprüfungen; ein nicht passendes Element kann beim Setzen eine `HierarchyRequestError`-DOMException auslösen.

---

# Normative Sonderregeln

## Tabellen sind Datenstrukturen

Die zentrale normative Zweckbestimmung von `table` ist die Repräsentation mehrdimensionaler Daten.

Die Verwendung als Layout-Hilfsmittel ist nicht konform.

## Tabellenmodell

Die Struktur des HTML-Quelltexts allein ist nicht die vollständige semantische Repräsentation.

Das WHATWG-Tabellenmodell bildet daraus:

- Slots,
- Zellen,
- Zeilen,
- Spalten,
- Gruppen,
- Header-Beziehungen.

## Keine Überlappung

Zellen dürfen im resultierenden Tabellenmodell nicht überlappen.

`colspan` und `rowspan` müssen so verwendet werden, dass keine überlappenden Zellbereiche entstehen.

## Vollständige Abdeckung

Die Zellen einer konformen Tabelle müssen das Tabellenraster vollständig abdecken.

## `colgroup` und `col`

`col` darf nur innerhalb eines `colgroup` ohne `span` verwendet werden.

Wenn `colgroup` selbst `span` verwendet, ist dessen Content Model `Nothing`.

## `thead`

Pro `table` darf höchstens ein `thead` als Kind vorhanden sein.

## `tfoot`

Pro `table` darf höchstens ein `tfoot` als Kind vorhanden sein.

## Direkte `tr`-Kinder

Direkte `tr`-Kinder von `table` sind unter bestimmten, ausdrücklich eingeschränkten Bedingungen erlaubt.

Sie dürfen nicht mit einer Struktur vermischt werden, die `tbody`-Kinder auf eine Weise verwendet, die den von WHATWG festgelegten Kontextregeln widerspricht.

## `scope`

`scope=rowgroup` und `scope=colgroup` unterliegen zusätzlichen strukturellen Konformitätsregeln.

## `abbr`

`abbr` ist kein allgemeines Abkürzungsattribut für beliebige Tabellenzellen. Es ist für `th` vorgesehen und dient als alternative Bezeichnung des Header-Inhalts in bestimmten Referenzierungskontexten.

---

# Querverweise

## Beziehungen innerhalb von §4.9

Die Elemente bilden eine hierarchische Tabellenstruktur:

`table`

→ `caption`

→ `colgroup`

→ `col`

→ `thead`

→ `tbody`

→ `tfoot`

→ `tr`

→ `td` / `th`

Diese Darstellung ist eine fachliche Strukturübersicht und keine Aussage, dass jedes Element unter jedem der dargestellten Elemente beliebig verschachtelt werden darf.

## Beziehungen zu anderen HTML-Konzepten

### `caption` und `figure`

WHATWG behandelt den Fall, dass eine Tabelle innerhalb eines `figure` steht und eine `figcaption` bereits den Titel bzw. die Beschreibung übernimmt.

### `details`

Bei komplexen Tabellen kann `details` innerhalb einer `caption` verwendet werden, um zusätzliche Erklärungen optional zugänglich zu machen.

### `figure` / `figcaption`

Eine Beschreibung kann neben einer Tabelle oder über die `figcaption` eines umgebenden `figure` bereitgestellt werden.

### Global Attributes

Alle Tabellen-Elemente akzeptieren die jeweils für HTML-Elemente geltenden Global Attributes, soweit keine speziellere Regel entgegensteht.

### `template`

`template` ist im Content Model von `table`, `colgroup` und den Tabellenbereichen als script-supporting bzw. strukturell unterstützendes Konzept relevant. Es wird deshalb nicht als Tabellen-Element inventarisiert.

### DOM

Die Tabellen-Interfaces bauen auf `HTMLElement` auf und verwenden gemeinsame DOM-Strukturen wie `HTMLCollection` und `DOMException`.

---

# Konformität und Status

## WHATWG-Definition

Die folgenden Elemente sind in §4.9 der aktuellen WHATWG HTML Living Standard definiert:

- `table`
- `caption`
- `colgroup`
- `col`
- `tbody`
- `thead`
- `tfoot`
- `tr`
- `td`
- `th`

## Konforme Verwendung

Die Tatsache, dass ein Element im WHATWG-Standard definiert ist, bedeutet nicht, dass jede mögliche Verwendung konform ist.

Beispiele:

- `table` für Layoutzwecke ist nicht konform.
- `col` außerhalb eines geeigneten `colgroup` ist nicht konform.
- `colgroup` mit `span` und gleichzeitigem `col`-Content ist nicht konform.
- `scope=rowgroup` ohne geeignete Zeilengruppe ist nicht konform.
- `scope=colgroup` ohne geeignete Spaltengruppe ist nicht konform.
- Tabellenmodellfehler sind nicht zulässig.

## Browser-Support

Browser-Support ist eine separate Rechercheebene.

Die in der WHATWG-Dokumentation eingeblendeten Kompatibilitätsinformationen werden nicht als WHATWG-Status in die ZE-WebLab-Referenz übernommen.

---

# Status / V1

| Feature | WHATWG definiert | Konforme Verwendung kontextabhängig | V1-Status |
|---|---|---|---|
| `table` | Ja | Ja | Referenziert |
| `caption` | Ja | Ja | Referenziert |
| `colgroup` | Ja | Ja | Referenziert |
| `col` | Ja | Ja | Referenziert |
| `tbody` | Ja | Ja | Referenziert |
| `thead` | Ja | Ja | Referenziert |
| `tfoot` | Ja | Ja | Referenziert |
| `tr` | Ja | Ja | Referenziert |
| `td` | Ja | Ja | Referenziert |
| `th` | Ja | Ja | Referenziert |
| `colspan` | Ja | Ja | Referenziert |
| `rowspan` | Ja | Ja | Referenziert |
| `headers` | Ja | Ja | Referenziert |
| `scope` | Ja | Ja | Referenziert |
| `abbr` | Ja | Ja | Referenziert |
| Table model | Ja | Ja | Referenziert |
| Header-cell assignment | Ja | Ja | Referenziert |
| Processing model | Ja | Implementierungs-/Verarbeitungsmodell | Referenziert |

---

# Fachliche Abgrenzung

## HTML-Elementinventar

Das Elementinventar von §4.9 umfasst zehn HTML-Elemente:

1. `table`
2. `caption`
3. `colgroup`
4. `col`
5. `tbody`
6. `thead`
7. `tfoot`
8. `tr`
9. `td`
10. `th`

## Attribute

Folgende elementbezogene Attribute werden in §4.9 ausdrücklich behandelt:

- `span`
- `colspan`
- `rowspan`
- `headers`
- `scope`
- `abbr`

Die Global Attributes werden nicht erneut als eigenes Attributinventar dieser Datei erfasst.

## Konzepte

Separat vom Elementinventar stehen:

- Table model
- Table model error
- Slots
- Cells
- Rows
- Columns
- Row groups
- Column groups
- Header cells
- Data cells
- Header assignment algorithm
- Processing model
- Table description techniques
- Table design techniques

Diese Konzepte dürfen in der zentralen Matrix nicht als zusätzliche HTML-Tags gezählt werden.

---

# Beispiele und normative Bedeutung

§4.9.13 enthält nicht-normative Beispiele.

Die Beispiele illustrieren unter anderem:

- mehrdimensionale Datentabellen,
- `caption`,
- `thead`,
- `tbody`,
- `th`,
- `td`,
- `rowspan`,
- `colspan`,
- `scope`,
- `headers`,
- komplexere Header-Strukturen,
- Tabellenbeschreibungen.

Die Beispiele sind keine zusätzlichen Konformitätsregeln. Maßgeblich bleiben die normativen Definitionen und Algorithmen der vorangehenden Unterabschnitte.

---

# Prüfzusammenfassung

## Elemente geprüft

- [x] `table`
- [x] `caption`
- [x] `colgroup`
- [x] `col`
- [x] `tbody`
- [x] `thead`
- [x] `tfoot`
- [x] `tr`
- [x] `td`
- [x] `th`

## Strukturinformationen geprüft

- [x] Content Categories
- [x] Contexts
- [x] Content Models
- [x] Tag Omission
- [x] Content Attributes
- [x] Accessibility-Verweise
- [x] Sanitization
- [x] DOM Interfaces

## Gemeinsame Tabellenattribute geprüft

- [x] `colspan`
- [x] `rowspan`
- [x] `headers`

## Header-spezifische Attribute geprüft

- [x] `scope`
- [x] `abbr`

## Normative Unterkonzepte geprüft

- [x] Table model
- [x] Table model errors
- [x] Forming a table
- [x] Forming relationships between data cells and header cells
- [x] Header cell classification
- [x] Downward-growing cells
- [x] Slots
- [x] Row groups
- [x] Column groups
- [x] Tabellenbeschreibung
- [x] Tabellendesign
- [x] Nicht-normative Beispiele

---

# Offene Punkte

Für die WHATWG-basierte Elementreferenz von §4.9 bestehen nach der durchgeführten Primärquellenprüfung keine offenen Punkte hinsichtlich des Elementinventars oder der Struktur des Abschnitts.

Nicht Bestandteil des Abschlusses dieser Datei sind:

1. eine vollständige Browser-Kompatibilitätsmatrix,
2. eine detaillierte Untersuchung einzelner Screenreader,
3. eine vollständige ARIA-Referenz,
4. eine vollständige AT-/Browser-Interoperabilitätsanalyse,
5. eine historische Entwicklung der Tabellen-Spezifikation,
6. eine vollständige CSS-Tabellenreferenz.

Diese Themen gehören zu separaten Rechercheebenen und werden nicht als WHATWG-Elementstatus ausgegeben.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG – HTML Living Standard**

Abschnitt:

- §4.9 Tabular data
- §4.9.1 The `table` element
- §4.9.1.1 Techniques for describing tables
- §4.9.1.2 Techniques for table design
- §4.9.2 The `caption` element
- §4.9.3 The `colgroup` element
- §4.9.4 The `col` element
- §4.9.5 The `tbody` element
- §4.9.6 The `thead` element
- §4.9.7 The `tfoot` element
- §4.9.8 The `tr` element
- §4.9.9 The `td` element
- §4.9.10 The `th` element
- §4.9.11 Attributes common to `td` and `th` elements
- §4.9.12 Processing model
- §4.9.12.1 Forming a table
- §4.9.12.2 Forming relationships between data cells and header cells
- §4.9.13 Examples

**Quellenstand der Recherche:** WHATWG HTML Living Standard, aktueller recherchierter Stand vom 11. August 2026.

## Externe Quellen

Für die fachlichen Aussagen dieser Datei wurden keine externen Quellen als normative Ersatzquelle für WHATWG verwendet.

Die in der WHATWG-Spezifikation referenzierten Accessibility Considerations verweisen auf die einschlägigen Accessibility-Spezifikationen. Diese Verweise wurden als Quellenbeziehungen dokumentiert, ohne deren vollständigen Inhalt hier als WHATWG-Inhalt auszugeben.

---

# QS-Abgrenzung für die zentrale Vollständigkeitsmatrix

Für `docs/content-analysis/html/completeness-matrix.md` sind für §4.9 mindestens folgende Feature-Ebenen unterscheidbar:

## Element-Features

- `table`
- `caption`
- `colgroup`
- `col`
- `tbody`
- `thead`
- `tfoot`
- `tr`
- `td`
- `th`

## Attribut-Features

- `span`
- `colspan`
- `rowspan`
- `headers`
- `scope`
- `abbr`

## Konzept-/Processing-Features

- Table model
- Table model errors
- Forming a table
- Forming relationships between data cells and header cells
- Header-cell assignment
- Header cell classification
- Table description techniques
- Table design techniques

Diese Ebenen sind getrennt zu führen.

Insbesondere darf `Table model`, `Processing model` oder der Header-Zuordnungsalgorithmus nicht als zusätzliches HTML-Element in der Elementinventarliste erscheinen.

---

# Abschlussstatus

**§4.9 Tabular data ist für die HTML-Referenz von ZE-WebLab vollständig geprüft.**
