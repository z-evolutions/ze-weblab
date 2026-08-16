# ZE-WebLab – HTML-Referenz: Microdata

## Arbeitsstand / Quellenstand

Projekt: ZE-WebLab

Datei: `docs/html/23-microdata.md`

Themenbereich: Microdata

Feature-Typ: Normatives HTML-Konzept / Feature-Familie / globale Attribute / Datenmodell / Verarbeitung

WHATWG-Bereich: §5 Microdata

Geprüfter WHATWG-Stand: HTML Living Standard, 11. August 2026

Repository-Stand: Der zum Prüfzeitpunkt über die öffentliche GitHub-Verzeichnisansicht abrufbare `main`-Stand enthält die erste Rechercheebene `01`–`12` sowie `README.md`. Eine bereits vorhandene `23-microdata.md` konnte im öffentlich abrufbaren Stand nicht bestätigt werden und wird deshalb als neue zweite-Ebenen-Datei behandelt.

Diese Datei dokumentiert Microdata als übergreifendes HTML-Konzept. Microdata wird ausdrücklich nicht als HTML-Elementinventar behandelt.

Microdata verwendet vorhandene HTML-Elemente und vier globale HTML-Attribute:

- `itemscope`
- `itemtype`
- `itemid`
- `itemref`

sowie das globale Attribut:

- `itemprop`

Die Attribute sind Bestandteil des WHATWG-Global-Attributes-Systems. Ihre konkrete normative Bedeutung ergibt sich aus §5 Microdata.

Microdata ist von den HTML-Content-Categories, Content Models und Link Types zu unterscheiden. Die Microdata-Systematik erzeugt keine neuen HTML-Elemente.

Browser-Kompatibilität ist nicht Bestandteil der WHATWG-Statusbewertung dieser Datei.

---

## Einordnung

Microdata ist ein in HTML integriertes Modell zur Annotation von Dokumentinhalten mit maschinenlesbaren Name-Value-Pairs.

Das Modell besteht aus:

- Items
- Item Types
- optionalen globalen Identifikatoren
- Properties
- Property Values
- Beziehungen zwischen Items
- optionalen Referenzen über `itemref`

Die zentrale Modellstruktur ist:

```text
Item
├── Item Types
├── Global Identifier
└── Properties
    ├── Property Name
    └── Property Value
        ├── String
        └── Item
```

Ein Item ist damit kein HTML-Elementtyp. Ein Item wird durch ein HTML-Element erzeugt, auf dem `itemscope` angegeben ist.

Ein Property ist ebenfalls kein HTML-Element. Eine Property wird durch `itemprop` auf einem HTML-Element beschrieben.

Ein Item Type ist kein HTML-Element, keine Content Category und kein WHATWG-Status. Es ist ein für das jeweilige Vokabular definierter URL-basierter Typbezeichner.

Microdata stellt somit eine zusätzliche semantische Annotationsebene über dem bestehenden HTML-Dokument dar.

---

## WHATWG-Struktur

Der aktuelle WHATWG-Bereich ist:

### §5 Microdata

#### §5.1 Introduction

- §5.1.1 Overview
- §5.1.2 The basic syntax
- §5.1.3 Typed items
- §5.1.4 Global identifiers for items
- §5.1.5 Selecting names when defining vocabularies

#### §5.2 Encoding microdata

- §5.2.1 The microdata model
- §5.2.2 Items
- §5.2.3 Names: the `itemprop` attribute
- §5.2.4 Values
- §5.2.5 Associating names with items
- §5.2.6 Microdata and other namespaces

#### §5.3 Sample microdata vocabularies

- §5.3.1 vCard
- §5.3.1.1 Conversion to vCard
- §5.3.1.2 Examples
- §5.3.2 vEvent
- §5.3.2.1 Conversion to iCalendar
- §5.3.2.2 Examples
- §5.3.3 Licensing works
- §5.3.3.1 Examples

#### §5.4 Converting HTML to other formats

- §5.4.1 JSON

Diese Unterabschnitte bilden die fachliche Grundlage dieser Datei.

---

## Inventar

| Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Abdeckungsstatus | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| Microdata | Normative Concept / Feature Family | §5 | elementbezogene Erwähnungen möglich | neu als übergreifendes Konzept | vollständig relevant |
| `itemscope` | Global Attribute / Microdata Feature | §5.2.2 | teilweise über einzelne Elemente | nur elementbezogen bzw. global erwähnt | vollständig relevant |
| `itemtype` | Global Attribute / Microdata Feature | §5.2.2 | teilweise | nur elementbezogen bzw. global erwähnt | vollständig relevant |
| `itemid` | Global Attribute / Microdata Feature | §5.2.2 | teilweise | nur elementbezogen bzw. global erwähnt | vollständig relevant |
| `itemref` | Global Attribute / Microdata Feature | §5.2.2 | teilweise | nur elementbezogen bzw. global erwähnt | vollständig relevant |
| `itemprop` | Global Attribute / Microdata Feature | §5.2.3 | teilweise | nur elementbezogen bzw. global erwähnt | vollständig relevant |
| Item | Microdata Data Model | §5.2.1–§5.2.5 | nicht als eigenes Featuremodell | nicht übergreifend dokumentiert | vollständig relevant |
| Item Type | Microdata Data Model | §5.1.3 / §5.2.2 | nicht als eigenes Featuremodell | nicht übergreifend dokumentiert | vollständig relevant |
| Property | Microdata Data Model | §5.2.1 / §5.2.3 | nicht als eigenes Featuremodell | nicht übergreifend dokumentiert | vollständig relevant |
| Property Value | Microdata Data Model | §5.2.1 / §5.2.4 | elementbezogene Wertattribute können vorhanden sein | nur indirekt | vollständig relevant |
| Global Identifier | Microdata Data Model | §5.1.4 / §5.2.2 | nicht als Microdata-Systematik | neu | vollständig relevant |
| `itemref`-Zuordnung | Processing Model | §5.2.5 | nicht übergreifend | neu | vollständig relevant |
| Microdata Errors | Conformance / Processing Concept | §5.2.5 | nicht übergreifend | neu | vollständig relevant |
| HTML/Namespace-Abgrenzung | Integration Rule | §5.2.6 | SVG/MathML ggf. separat behandelt | Microdata-Bezug neu | relevant |
| vCard Vocabulary | Sample Vocabulary | §5.3.1 | nicht übergreifend | neu | relevant |
| vCard Conversion | Processing Model / API-nahe Verarbeitung | §5.3.1.1 | nicht übergreifend | neu | relevant |
| vEvent Vocabulary | Sample Vocabulary | §5.3.2 | nicht übergreifend | neu | relevant |
| iCalendar Conversion | Processing Model | §5.3.2.1 | nicht übergreifend | neu | relevant |
| Licensing Works Vocabulary | Sample Vocabulary | §5.3.3 | nicht übergreifend | neu | relevant |
| JSON Conversion | Conversion Algorithm | §5.4.1 | nicht übergreifend | neu | vollständig relevant |

---

## Begriffsdefinitionen

### Microdata

Microdata ist ein HTML-Feature zur Annotation von Dokumentinhalten mit maschinenlesbaren Name-Value-Pairs.

Die semantische Bedeutung der Property-Namen und Item Types wird durch das verwendete Vokabular bestimmt.

WHATWG definiert das allgemeine Microdata-Modell und einige Beispielvokabulare. WHATWG definiert nicht automatisch ein universelles Vokabular für sämtliche möglichen Anwendungen.

---

### Item

Ein Item ist eine Gruppe aus Name-Value-Pairs.

Ein Item kann besitzen:

- einen oder mehrere Item Types
- einen globalen Identifier, sofern das verwendete Vokabular globale Identifier unterstützt
- eine Liste von Properties

Der Wert einer Property kann entweder:

- ein String
- oder selbst ein Item

sein.

Items können dadurch verschachtelte Datenstrukturen bilden.

---

### Top-Level Item

Ein Item ist ein Top-Level Item, wenn das Element, das dieses Item erzeugt, kein `itemprop`-Attribut besitzt.

Top-Level Items stehen damit nicht selbst als Property Value eines anderen Items.

---

### Typed Item

Ein Item ist ein Typed Item, wenn:

- es einen Item Type besitzt
- oder es der Wert einer Property eines Typed Items ist.

Bei einem verschachtelten Item können die relevanten Typen aus dem übergeordneten Typed Item abgeleitet werden, wenn das verschachtelte Item selbst keine Item Types besitzt.

---

### Item Type

Ein Item Type identifiziert den Typ eines Items.

Item Types sind URL-basierte Identifikatoren.

`itemtype` enthält eine ungeordnete Menge eindeutiger, durch ASCII-Whitespace getrennter Tokens.

Jedes Token muss:

- eine gültige URL sein
- eine absolute URL sein
- in einer anwendbaren Spezifikation als Item Type definiert sein
- zu einem Vokabular gehören, das mit den anderen angegebenen Item Types kompatibel ist.

Alle Item Types eines Items müssen dasselbe Vokabular verwenden.

Item Types sind für User Agents grundsätzlich opaque identifiers.

Ein User Agent darf einen unbekannten Item Type nicht einfach dereferenzieren oder aus dessen URL-Struktur ableiten, wie das Item zu verarbeiten ist.

---

### Vocabulary

Ein Vokabular definiert die Bedeutung von:

- Item Types
- Property Names
- zulässigen Property Values
- gegebenenfalls globalen Identifikatoren
- weiteren Regeln für die Verarbeitung dieser Daten.

Ein Vokabular kann durch eine externe Spezifikation definiert werden.

WHATWG definiert das allgemeine Microdata-Modell und einige Beispielvokabulare. Ein allgemeiner Microdata-Eintrag wird nicht allein durch das Vorhandensein von `itemscope` automatisch Teil eines bestimmten externen Vokabulars.

---

### Property

Eine Property ist ein Name innerhalb eines Items.

Ein HTML-Element mit `itemprop` kann eine oder mehrere Properties zu einem oder mehreren Items hinzufügen.

Property-Namen werden durch ASCII-Whitespace getrennt.

---

### Property Name

Property Names sind die Tokens des `itemprop`-Attributs.

Die Tokens werden aus dem Attributwert durch Aufteilung an ASCII-Whitespace gewonnen.

Doppelte Property-Namen werden entfernt, wobei das erste Auftreten erhalten bleibt.

Innerhalb eines Items sind unterschiedliche Property-Namen grundsätzlich ungeordnet.

Mehrere Properties desselben Namens besitzen dagegen eine definierte Reihenfolge.

---

### Property Value

Der Wert einer Property wird anhand des Elements bestimmt, auf dem `itemprop` angegeben ist.

Der Wert kann insbesondere sein:

- ein verschachteltes Item
- der Wert eines `meta`-Attributs
- eine URL
- der Wert eines `data`-Elements
- der Wert eines `meter`-Elements
- der Datums-/Zeitwert eines `time`-Elements
- der Textinhalt des Elements.

---

### Global Identifier

Ein globaler Identifier identifiziert ein Item über das Dokument hinaus.

Er wird mit `itemid` angegeben.

Ein `itemid` ist nur unter bestimmten Voraussetzungen zulässig:

- `itemscope` muss vorhanden sein
- `itemtype` muss vorhanden sein
- das Vokabular muss globale Identifier für Items unterstützen.

Die konkrete Bedeutung des globalen Identifikators wird durch das verwendete Vokabular definiert.

---

### Property Association

Die Zuordnung von Properties zu Items erfolgt grundsätzlich über die DOM-Struktur.

Zusätzlich kann `itemref` verwendet werden, um weitere Elemente außerhalb der direkten Kindstruktur in die Property-Suche einzubeziehen.

---

## Microdata-Attribute

## `itemscope`

### Feature-Typ

Global Attribute / Microdata Item Creation

### WHATWG-Zuordnung

§5.2.2 Items

### Bedeutung

`itemscope` erzeugt auf dem betreffenden HTML-Element ein neues Microdata Item.

Das Item besteht aus einer Gruppe von Name-Value-Pairs.

### Syntax

`itemscope` ist ein Boolean Attribute.

Beispiele:

```html
<div itemscope>
</div>
```

```html
<section itemscope>
  <h2 itemprop="name">Beispiel</h2>
</section>
```

### Geltungsbereich

`itemscope` kann auf jedem HTML-Element angegeben werden.

Das bedeutet nicht, dass `itemscope` auf Elementen anderer Namespaces automatisch Microdata-Verarbeitung auslöst.

### Konformität

Ein Element mit `itemscope` erzeugt ein Item.

Die weitere Interpretation hängt insbesondere davon ab, ob zusätzlich:

- `itemtype`
- `itemid`
- `itemref`
- `itemprop`

angegeben sind.

---

## `itemtype`

### Feature-Typ

Global Attribute / Microdata Item Type

### WHATWG-Zuordnung

§5.2.2 Items

### Bedeutung

`itemtype` gibt die Item Types eines Items an.

### Voraussetzungen

`itemtype` darf nur auf einem Element mit `itemscope` angegeben werden.

### Syntax

Der Wert ist eine ungeordnete Menge eindeutiger, durch ASCII-Whitespace getrennter Tokens.

Jedes Token muss eine gültige absolute URL sein.

Alle Item Types müssen:

- in anwendbaren Spezifikationen definiert sein
- dasselbe Vokabular verwenden.

Beispiel:

```html
<div
  itemscope
  itemtype="https://example.com/vocabulary/Person">
</div>
```

Mehrere kompatible Typen können angegeben werden:

```html
<div
  itemscope
  itemtype="https://example.com/vocabulary/Person https://example.com/vocabulary/Employee">
</div>
```

### Normative Einschränkung

Mehrere Item Types dürfen nicht einfach aus unterschiedlichen Vokabularen kombiniert werden.

Das Vokabular bestimmt die Bedeutung der zulässigen Property Names.

### Opaque Identifier

Item Types sind opaque identifiers.

User Agents dürfen unbekannte Item Types nicht anhand ihrer URL-Struktur interpretieren.

---

## `itemid`

### Feature-Typ

Global Attribute / Microdata Global Identifier

### WHATWG-Zuordnung

§5.1.4 / §5.2.2

### Bedeutung

`itemid` gibt den globalen Identifier eines Items an.

### Voraussetzungen

`itemid` darf nur verwendet werden, wenn:

- `itemscope` vorhanden ist
- `itemtype` vorhanden ist
- das referenzierte Vokabular globale Identifier unterstützt.

### Syntax

Der Wert muss eine gültige URL sein, die optional von Leerraum umgeben sein darf.

Beispiel:

```html
<div
  itemscope
  itemtype="https://example.com/vocabulary/Person"
  itemid="https://example.com/person/123">
</div>
```

### Auflösung

Der globale Identifier wird relativ zum Node Document des Elements aufgelöst.

Fehlt `itemid` oder schlägt die URL-Interpretation fehl, besitzt das Item keinen globalen Identifier.

### Bedeutung

Die konkrete Semantik eines globalen Identifikators ist Sache des verwendeten Vokabulars.

---

## `itemref`

### Feature-Typ

Global Attribute / Property Association Syntax

### WHATWG-Zuordnung

§5.2.2 / §5.2.5

### Bedeutung

`itemref` erlaubt es, zusätzliche Elemente zu referenzieren, die bei der Ermittlung der Properties eines Items berücksichtigt werden.

Dies ist insbesondere relevant, wenn die zu annotierenden Informationen nicht bequem innerhalb der DOM-Kindstruktur des Items liegen.

### Syntax

Der Wert besteht aus einer ungeordneten Menge eindeutiger, durch ASCII-Whitespace getrennte Tokens.

Jedes Token ist die ID eines Elements im selben Tree.

### Voraussetzung

`itemref` darf nur auf einem Element mit `itemscope` angegeben werden.

### Beispiel

```html
<div itemscope itemref="additional-data">
  <span itemprop="name">Sascha</span>
</div>

<div id="additional-data">
  <span itemprop="role">Developer</span>
</div>
```

### Datenmodell

`itemref` selbst ist kein Bestandteil des eigentlichen Microdata-Datenmodells.

Es ist ein syntaktisches Hilfsmittel zur Property-Zuordnung.

---

## `itemprop`

### Feature-Typ

Global Attribute / Microdata Property

### WHATWG-Zuordnung

§5.2.3

### Bedeutung

`itemprop` definiert die Property Names, die das betreffende Element zu einem oder mehreren Items beiträgt.

### Geltungsbereich

`itemprop` kann auf jedem HTML-Element angegeben werden, sofern dadurch tatsächlich Properties zu Items hinzugefügt werden.

### Syntax

Der Wert besteht aus einer ungeordneten Menge eindeutiger, durch ASCII-Whitespace getrennter Tokens.

Beispiel:

```html
<span itemprop="name">Sascha</span>
```

Mehrere Properties können gemeinsam angegeben werden:

```html
<span itemprop="name nickname">Sascha</span>
```

### Property-Namen bei Typed Items

Wenn das Item Typed Item ist, muss jeder Property Name durch die Spezifikation des relevanten Vokabulars zugelassen sein.

Alternativ können gültige absolute URLs als Property Names verwendet werden, wenn sie entsprechend definiert oder als proprietäre Property Names verwendet werden.

### Untyped Items

Bei untypisierten Items können proprietäre Property Names als Tokens verwendet werden, die weder `.` noch `:` enthalten.

### URL Property Names

Absolute URLs können als Property Names verwendet werden.

Dadurch können Property Names global eindeutig gemacht werden.

---

## Content Categories

Microdata ist keine Content Category.

Die Microdata-Attribute ändern die Content Category eines Elements nicht allgemein.

Allerdings kann die Anwesenheit bestimmter Attribute bei einzelnen Elementdefinitionen Einfluss auf deren Kategorie oder Context haben.

Ein besonders relevantes WHATWG-Beispiel ist `meta`:

- `meta` gehört grundsätzlich zu Metadata Content.
- Bei Verwendung von `itemprop` kann `meta` unter den von WHATWG definierten Bedingungen zusätzlich als Flow Content und Phrasing Content eingeordnet werden.

Diese elementbezogene Kategorisierung ist von der Microdata-Datenmodellierung zu unterscheiden.

Microdata selbst ist keine Kategorie wie:

- Flow Content
- Phrasing Content
- Metadata Content
- Embedded Content
- Interactive Content
- Sectioning Content.

---

## Context

Microdata besitzt kein eigenes universelles Content-Model-Context-System.

Die zulässige Verwendung eines Elements wird weiterhin durch die jeweilige Elementdefinition bestimmt.

Die Microdata-Attribute sind globale HTML-Attribute und können deshalb auf HTML-Elementen in unterschiedlichen Contexts vorkommen.

Für Microdata relevant ist insbesondere:

- `itemscope` erzeugt ein Item
- `itemprop` ordnet Properties zu
- `itemtype` typisiert das Item
- `itemid` identifiziert das Item global
- `itemref` erweitert die Property-Suche.

Der Context eines konkreten HTML-Elements bleibt davon getrennt.

---

## Content Model

Microdata definiert kein neues Content Model für HTML-Elemente.

Die vorhandenen Content Models der verwendeten HTML-Elemente bleiben bestehen.

Ein Microdata Item kann beispielsweise auf:

```html
<div itemscope>
```

oder:

```html
<article itemscope>
```

oder:

```html
<span itemscope>
```

gebildet werden.

Welche Inhalte innerhalb dieser Elemente zulässig sind, ergibt sich weiterhin aus dem Content Model des jeweiligen HTML-Elements.

Microdata ist daher kein Ersatz für das WHATWG-Content-Model-System.

---

## Verarbeitung des Microdata-Modells

## Grundmodell

Das Microdata-Modell besteht aus Gruppen von Name-Value-Pairs.

Jedes Item kann besitzen:

- Item Types
- Global Identifier
- Properties.

Jede Property besitzt:

- einen Namen
- einen oder mehrere Werte.

Ein Wert ist entweder:

- ein String
- oder ein Item.

---

## Erzeugung eines Items

Ein HTML-Element mit `itemscope` erzeugt ein Item.

Beispiel:

```html
<div itemscope>
</div>
```

Ohne weitere Attribute handelt es sich um ein Item ohne Item Type.

---

## Verschachtelte Items

Ein Element kann gleichzeitig:

- `itemscope`
- `itemprop`

besitzen.

In diesem Fall erzeugt das Element ein neues Item und dieses Item wird gleichzeitig als Property Value des übergeordneten Items verwendet.

Beispiel:

```html
<div itemscope>
  <span itemprop="name">Amanda</span>

  <div itemprop="band" itemscope>
    <span itemprop="name">Jazz Band</span>
    <span itemprop="size">12</span>
  </div>
</div>
```

Das äußere Item besitzt:

- `name`
- `band`

Das `band`-Property besitzt als Wert ein weiteres Item.

Das innere Item besitzt:

- `name`
- `size`.

---

## Top-Level Items

Ein Item ist ein Top-Level Item, wenn das Element, das es erzeugt, kein `itemprop` besitzt.

Beispiel:

```html
<div itemscope>
  <span itemprop="name">Amanda</span>
</div>
```

Das `div` erzeugt ein Top-Level Item.

---

## Mehrere Properties mit gleichem Namen

Ein Item darf mehrere Properties mit demselben Namen besitzen.

Beispiel:

```html
<div itemscope>
  <span itemprop="flavor">Lemon sorbet</span>
  <span itemprop="flavor">Apricot sorbet</span>
</div>
```

Das Item besitzt zwei Werte für `flavor`.

Die Reihenfolge gleicher Property Names ist relevant.

Die Reihenfolge unterschiedlicher Property Names ist dagegen grundsätzlich nicht semantisch relevant.

---

## Mehrere Property Names auf einem Element

Ein einzelnes Element kann mehrere Property Names angeben:

```html
<span itemprop="favorite-color favorite-fruit">
  orange
</span>
```

Das Element fügt damit mehrere Properties mit demselben Wert hinzu.

---

## Associating Names with Items

WHATWG definiert einen Algorithmus zur Ermittlung der Properties eines Items.

Vereinfacht besteht die Verarbeitung aus folgenden Schritten:

1. Das Ausgangselement wird als `root` festgelegt.
2. Eine Memory-Liste wird angelegt.
3. Die Kind-Elemente werden zur Verarbeitung vorgemerkt.
4. Falls `itemref` vorhanden ist, werden die referenzierten Elemente ebenfalls zur Verarbeitung vorgemerkt.
5. Die vorgemerkten Elemente werden verarbeitet.
6. Elemente mit `itemscope` werden nicht rekursiv über ihre Kinder als Properties des übergeordneten Items durchsucht.
7. Elemente mit `itemprop` und mindestens einem Property Name werden als Properties erfasst.
8. Die Ergebnisse werden in Tree Order sortiert.

Die normative Verarbeitung darf nicht durch eine bloße vereinfachte DOM-Abfrage ersetzt werden, wenn Konformität oder User-Agent-Verarbeitung geprüft wird.

---

## Microdata Errors

WHATWG definiert Microdata Errors im Rahmen des Algorithmus zur Ermittlung der Properties.

Ein relevanter Fall entsteht beispielsweise, wenn während der Property-Ermittlung ein Element erneut in der bereits besuchten Struktur auftaucht.

Ein Dokument darf keine Items enthalten, bei denen der Property-Ermittlungsalgorithmus Microdata Errors feststellt.

---

## `itemref` und Zyklen

Die durch verschachtelte Items gebildete Struktur kann als Graph betrachtet werden.

WHATWG fordert, dass `itemref`-Beziehungen keine Zyklen erzeugen, die über Property Values zwischen Items entstehen.

Das bedeutet insbesondere:

```text
Item A
  └── Property → Item B
                   └── Property → Item A
```

ist als zyklische Item-Struktur problematisch und fällt unter die normativen Microdata-Regeln.

---

## Unzugeordnete `itemprop`

Ein Element mit `itemprop` muss tatsächlich als Property eines Items gefunden werden können.

Ein `itemprop`, das zu keinem Item gehört, ist nicht konform.

Damit reicht es nicht aus, `itemprop` isoliert irgendwo im Dokument anzugeben.

---

## Werte

Die Property Values werden nach WHATWG abhängig vom Elementtyp bestimmt.

### Verschachteltes Item

Wenn das Element selbst `itemscope` besitzt:

```html
<div itemprop="author" itemscope>
</div>
```

ist der Property Value das von diesem Element erzeugte Item.

---

### `meta`

Bei `meta` wird der Wert aus dem `content`-Attribut gewonnen.

Beispiel:

```html
<meta itemprop="description" content="Beschreibung">
```

Der Property Value ist:

```text
Beschreibung
```

Fehlt `content`, ist der Wert der leere String.

---

### URL-basierte Elemente

Bei folgenden Elementen wird der Property Value aus einem URL-Attribut bestimmt:

- `a`
- `area`
- `audio`
- `embed`
- `iframe`
- `img`
- `link`
- `object`
- `source`
- `track`
- `video`

Bei diesen Elementen werden die entsprechenden URL-Attribute verarbeitet.

Dazu gehören insbesondere:

- `href`
- `src`
- `data`

je nach Element.

---

### `data`

Bei:

```html
<data itemprop="product-id" value="9678AOU879">
  The Instigator 2000
</data>
```

ist der Property Value der Wert des `value`-Attributs.

---

### `meter`

Bei `meter` wird der Wert des `value`-Attributs als Property Value verwendet.

---

### `time`

Bei `time` wird der nach WHATWG bestimmte Datums-/Zeitwert des Elements als Property Value verwendet.

Beispiel:

```html
<time
  itemprop="birthday"
  datetime="2009-05-10">
  May 10th 2009
</time>
```

Der menschenlesbare Text und der maschinenlesbare Datumswert können damit getrennt dargestellt werden.

---

### Sonstige Elemente

Bei sonstigen Elementen ist der Property Value der Descendant Text Content des Elements.

Beispiel:

```html
<span itemprop="name">Sascha</span>
```

liefert den Textinhalt als Property Value.

---

## URL Property Elements

WHATWG definiert eine Gruppe von URL Property Elements.

Dazu gehören:

- `a`
- `area`
- `audio`
- `embed`
- `iframe`
- `img`
- `link`
- `object`
- `source`
- `track`
- `video`

Wenn die Definition einer Property verlangt, dass deren Wert eine absolute URL ist, muss dafür ein entsprechendes URL Property Element verwendet werden.

Es genügt nicht, dass ein beliebiger Text zufällig wie eine URL aussieht.

Die URL-Regel hängt von der Definition des Property Values im verwendeten Vokabular ab.

---

## Property Names und Vokabulare

Bei einem Typed Item bestimmt das verwendete Vokabular, welche Property Names zulässig sind.

Ein Vokabular kann Property Names als einfache Wörter definieren.

Ein Vokabular kann außerdem URL-basierte Property Names verwenden.

Beispiel:

```html
<span itemprop="name">
  Hedral
</span>
```

oder:

```html
<span itemprop="https://example.com/color">
  black
</span>
```

Die URL-Variante kann für global eindeutige Property Names verwendet werden.

---

## Vokabularregeln

Microdata selbst definiert nicht die Semantik beliebiger Property Names.

Ein Vokabular muss definieren:

- welche Item Types existieren
- welche Property Names existieren
- welche Property Values zulässig sind
- wie Items interpretiert werden
- gegebenenfalls ob globale Identifier unterstützt werden
- gegebenenfalls Konvertierungsregeln.

Autoren sollen bestehende Vokabulare wiederverwenden, wenn dies sinnvoll ist.

---

## HTML- und andere Namespaces

## HTML Namespace

Die Microdata-Attribute sind im WHATWG-Standard für HTML-Elemente definiert.

Microdata-Verarbeitung findet daher nicht automatisch statt, nur weil ein Element in einem anderen Namespace ein Attribut mit demselben lokalen Namen besitzt.

---

## SVG

Ein Beispiel:

```html
<p itemscope></p>
```

erzeugt ein Microdata Item.

Dagegen:

```html
<svg itemscope></svg>
```

erzeugt aufgrund des SVG-Namespaces kein Microdata Item.

Das Attribut ist dort nicht automatisch ein Microdata-Attribut.

Diese Regel ist besonders wichtig für die Trennung zwischen:

- HTML
- SVG
- MathML.

Microdata darf daher nicht als namespaceübergreifendes Attributsystem verstanden werden.

---

## MathML

Für MathML gilt dieselbe grundlegende Abgrenzung.

Die Microdata-Attribute sind als Microdata-Features für HTML-Elemente definiert.

Ein gleichnamiges Attribut auf einem Element eines anderen Namespace wird dadurch nicht automatisch zu einem Microdata-Feature.

---

## DOM Interfaces / APIs

## Aktueller WHATWG-Stand

Microdata ist im aktuellen WHATWG-Standard primär als HTML-Datenmodell und Verarbeitungsmodell dokumentiert.

Die Microdata-Spezifikation ist dabei nicht mit einer eigenständigen aktuellen `HTMLPropertiesCollection`-API gleichzusetzen.

Historische HTML-Versionen und ältere Spezifikationsstände enthielten eine `HTMLPropertiesCollection`-/`PropertyNodeList`-basierte DOM-API.

Diese historische API darf nicht ohne aktuellen WHATWG-Nachweis als Bestandteil des aktuellen Living Standards dokumentiert werden.

Für die aktuelle Referenz ist deshalb zwischen:

- aktuellen Microdata-Content-Attributen
- aktuellem Microdata-Datenmodell
- aktuellen User-Agent-Verarbeitungsalgorithmen
- historischen Microdata-DOM-APIs

zu unterscheiden.

### Normativer DOM-Bezug

Die Microdata-Verarbeitung arbeitet mit DOM-Konzepten wie:

- Elementen
- Trees
- IDs
- Tree Order
- Descendant Text Content
- Node Document.

Diese DOM-Konzepte stammen teilweise aus den allgemeinen DOM-/HTML-Regeln und werden von Microdata verwendet.

---

## IDL-Bezug

Die Attribute `itemscope`, `itemtype`, `itemid`, `itemref` und `itemprop` gehören zum globalen HTML-Attributsystem.

Ihre Existenz als Content Attributes ist daher von den konkreten HTML-Element-Interfaces unabhängig.

Ein Element erhält durch `itemscope` kein neues spezielles HTML-Element-Interface.

Beispielsweise bleibt ein:

```html
<div itemscope>
```

ein `HTMLDivElement`.

`itemscope` macht daraus kein `HTMLMicrodataElement`.

---

## API / Verarbeitung

Microdata enthält normative User-Agent-Verarbeitungsalgorithmen.

Dazu gehören insbesondere:

- Ermittlung der Properties eines Items
- Ermittlung von Property Values
- Verarbeitung von `itemref`
- Erkennung von Microdata Errors
- Konvertierung von Microdata in JSON
- Konvertierung bestimmter Beispielvokabulare in andere Formate.

Diese Algorithmen sind keine HTML-Elemente und werden deshalb als Processing Models dokumentiert.

---

## Processing Models

## Property-Ermittlung

Der Algorithmus zur Ermittlung der Properties eines Items ist ein zentrales Microdata Processing Model.

Er arbeitet DOM-basiert und berücksichtigt:

- das Root-Element
- Kind-Elemente
- `itemscope`
- `itemprop`
- `itemref`
- Tree Order
- bereits besuchte Elemente.

---

## Property Value Processing

Die Bestimmung des Wertes eines Properties hängt vom konkreten HTML-Element ab.

Die WHATWG-Regeln bilden deshalb eine definierte Prioritätsreihenfolge:

1. `itemscope`
2. `meta`
3. URL-basierte Elemente
4. `object`
5. `data`
6. `meter`
7. `time`
8. sonstiger Descendant Text Content.

Diese Reihenfolge ist normativ relevant.

---

## JSON Conversion

WHATWG definiert in §5.4.1 einen Algorithmus zur Umwandlung von HTML-Microdata in JSON.

Das Ergebnis eines Items kann insbesondere enthalten:

```json
{
  "type": [
    "https://example.com/Person"
  ],
  "id": "https://example.com/person/123",
  "properties": {
    "name": [
      "Sascha"
    ]
  }
}
```

Die konkrete JSON-Struktur wird durch den WHATWG-Algorithmus bestimmt.

Wichtig ist insbesondere:

- `type` enthält die Item Types
- `id` enthält gegebenenfalls den globalen Identifier
- `properties` enthält die Properties des Items
- Property Values können Strings oder verschachtelte JSON-Objekte sein.

Bei zyklischen Item-Beziehungen behandelt der JSON-Konvertierungsalgorithmus die Rekursion ausdrücklich und kann für bereits besuchte Items den Wert `ERROR` erzeugen.

Die JSON-Konvertierung ist ein WHATWG-definierter Verarbeitungsschritt und nicht mit einem allgemeinen, externen JSON-LD-Konverter gleichzusetzen.

---

## vCard

WHATWG enthält ein Beispielvokabular für vCard.

Der Item Type ist:

```text
http://microformats.org/profile/hcard
```

Das Vokabular basiert auf dem vCard-Format und verweist für die fachliche Interpretation auf RFC 6350.

Das Beispielvokabular definiert unter anderem:

- `kind`
- `fn`
- `n`
- `nickname`
- `photo`
- `bday`
- `anniversary`
- `sex`
- `gender-identity`
- `adr`
- `tel`
- `email`
- `impp`
- `lang`
- `tz`
- `geo`
- `title`
- `role`
- `logo`
- `agent`
- `sound`
- `uid`
- `url`.

Die vollständigen Property-Regeln gehören zum WHATWG-Beispielvokabular und sind nicht mit dem allgemeinen Microdata-Modell gleichzusetzen.

---

## vCard Conversion

WHATWG definiert einen User-Agent-Algorithmus zur Konvertierung eines vCard-Microdata-Items in vCard-Daten.

Der Algorithmus:

- sucht Items mit dem vCard Item Type
- wählt das erste passende vCard Item
- erzeugt vCard-Zeilen
- verarbeitet definierte Properties
- berücksichtigt verschachtelte Items
- berücksichtigt bestimmte Property- und Parameterregeln.

Das Ergebnis ist vCard 4.0.

Die Konvertierungsregeln sind spezifisch für das WHATWG-Beispielvokabular.

---

## vEvent

WHATWG enthält außerdem ein Beispielvokabular für Events.

Der Item Type ist:

```text
http://microformats.org/profile/hcalendar#vevent
```

Das Vokabular basiert auf iCalendar.

Zu den definierten Properties gehören unter anderem:

- `attach`
- `categories`
- `class`
- `comment`
- `description`
- `dtend`
- `dtstart`
- `duration`
- `location`
- `organizer`
- `priority`
- `resources`
- `rdate`
- `recurrence-id`
- `sequence`
- `status`
- `summary`
- `transp`
- `uid`
- `url`.

Die genaue Zulässigkeit, Kardinalität und Werteform ergibt sich aus der jeweiligen Vokabulardefinition.

---

## iCalendar Conversion

WHATWG definiert einen Algorithmus zur Konvertierung eines passenden vEvent-Items in iCalendar-Daten.

Dabei werden unter anderem:

- Item Properties
- Datumswerte
- Date-Time-Werte
- verschachtelte Werte
- iCalendar-Namen
- Parameter
- Escape-Regeln
- Zeilenlängen

verarbeitet.

Der Algorithmus kann ungültige iCalendar-Ausgabe erzeugen, wenn die Eingabedaten nicht den Konformitätsregeln des entsprechenden Vokabulars entsprechen.

Die Konvertierung ist deshalb nicht als allgemeine Garantie zu verstehen, dass beliebiges Microdata automatisch gültiges iCalendar erzeugt.

---

## Licensing Works

WHATWG enthält außerdem das Beispielvokabular:

```text
http://n.whatwg.org/work
```

Es beschreibt Werke, beispielsweise:

- Artikel
- Bilder
- Videos
- Songs.

Definierte Properties umfassen:

- `work`
- `title`
- `author`
- `license`.

`work` muss als absolute URL angegeben werden.

`author` kann insbesondere Text oder ein vCard-Item sein.

`license` muss eine absolute URL sein.

Dieses Vokabular dient insbesondere dazu, Lizenzinformationen über Werke maschinenlesbar zu annotieren.

---

## Accessibility

Microdata ist ein maschinenlesbares Annotationssystem.

Es ersetzt keine Accessibility-Semantik.

Die Verwendung von Microdata erzeugt nicht automatisch eine ARIA-Rolle und darf nicht als Ersatz für semantische HTML-Elemente oder die einschlägigen Accessibility-Spezifikationen verstanden werden.

Für Accessibility gelten weiterhin:

- die Semantik des verwendeten HTML-Elements
- die WHATWG Accessibility Considerations
- gegebenenfalls ARIA in HTML
- gegebenenfalls HTML Accessibility API Mappings.

Wenn ein Element beispielsweise durch Microdata mit `itemprop` versehen wird, ändert dies nicht automatisch seine zugrunde liegende Accessibility-Semantik.

Microdata und Accessibility sind daher getrennte Informationsdimensionen.

---

## Sanitization

Microdata ist kein eigenständiger Sanitization-Modus.

Die Sanitization-Regeln des verwendeten HTML-Elements und die allgemeine WHATWG-Sanitization-Systematik bleiben maßgeblich.

Die Anwesenheit von:

- `itemscope`
- `itemtype`
- `itemid`
- `itemref`
- `itemprop`

ist nicht als eigenständige Sanitization-Kategorie zu behandeln.

Bei der Dokumentation einzelner HTML-Elemente muss die jeweilige Element-Sanitization weiterhin aus der Elementdefinition übernommen werden.

---

## Konformitätsregeln

### `itemscope`

`itemscope` ist ein Boolean Attribute.

Ein Element mit `itemscope` erzeugt ein Item.

---

### `itemtype`

`itemtype`:

- benötigt `itemscope`
- muss eine nichtleere Tokenmenge enthalten
- verwendet gültige absolute URLs
- darf nur Item Types aus demselben Vokabular kombinieren.

---

### `itemid`

`itemid`:

- benötigt `itemscope`
- benötigt `itemtype`
- setzt ein Vokabular voraus, das globale Identifier unterstützt
- muss eine gültige URL enthalten.

---

### `itemref`

`itemref`:

- benötigt `itemscope`
- referenziert IDs
- verwendet Elemente desselben Trees
- darf keine ungültigen oder doppelten Tokenformen verwenden.

---

### `itemprop`

`itemprop`:

- muss mindestens einen Property Name enthalten
- verwendet eindeutige, durch ASCII-Whitespace getrennte Tokens
- muss im jeweiligen Item-Kontext zulässige Property Names verwenden.

---

### Microdata Errors

Die durch den Property-Ermittlungsalgorithmus erkannten Microdata Errors sind konformitätsrelevant.

---

### Zyklische Item-Strukturen

Die durch `itemref` und verschachtelte Items entstehende Item-Struktur darf keine unzulässigen Zyklen enthalten.

---

### Unzugeordnete Properties

Ein `itemprop` darf nicht auf einem Element verwendet werden, das keiner Property eines Items zugeordnet werden kann.

---

## Normative Sonderregeln

### Microdata ist an HTML-Elemente gebunden

Die Microdata-Attribute sind keine beliebigen namespaceunabhängigen Attribute.

Ihre normative Microdata-Bedeutung gilt für HTML-Elemente.

---

### `itemref` gehört nicht zum Datenmodell

`itemref` ist eine syntaktische Hilfskonstruktion.

Das eigentliche Datenmodell besteht aus:

- Items
- Types
- Identifiers
- Properties
- Values.

---

### Mehrere Item Types

Mehrere Item Types sind möglich, aber nur innerhalb desselben Vokabulars.

Das ist eine zentrale Konformitätsregel.

---

### Item Types sind opaque

Aus der URL eines Item Types darf ein User Agent nicht eigenständig eine Semantik ableiten.

---

### URL-Property-Regel

Ein Property Value, der laut Vokabular eine absolute URL sein muss, muss über ein geeignetes URL Property Element angegeben werden.

Ein bloßer String, der zufällig wie eine URL aussieht, genügt dafür nicht.

---

### Property-Reihenfolge

Unterschiedliche Property Names sind ungeordnet.

Mehrere Werte desselben Property Names besitzen dagegen eine definierte Reihenfolge.

---

### `meta` mit `itemprop`

`meta` kann mit `itemprop` zur Bereitstellung maschinenlesbarer Werte verwendet werden.

Das kann gleichzeitig die Content-Category-Einstufung des Elements beeinflussen.

Die Microdata-Funktion und die Elementkategorie müssen getrennt dokumentiert werden.

---

## Querverweise

### Element ↔ Microdata Attribute

Viele HTML-Elemente können Microdata-Attribute tragen.

Besonders häufig sind:

- `article`
- `div`
- `span`
- `section`
- `meta`
- `data`
- `meter`
- `time`
- `a`
- `img`
- `link`
- `object`
- `audio`
- `video`
- `source`.

Die konkrete Zulässigkeit der Attribute ergibt sich aus dem globalen Attributsystem bzw. den Microdata-Regeln.

---

### Microdata ↔ Global Attributes

Microdata nutzt das globale Attributsystem.

Die relevanten Microdata-Attribute sind:

- `itemid`
- `itemprop`
- `itemref`
- `itemscope`
- `itemtype`.

---

### Microdata ↔ Content Categories

Microdata ist keine Content Category.

Einzelne Attribute können jedoch bei konkreten Elementen Einfluss auf deren Kategorien oder zulässige Contexts haben.

---

### Microdata ↔ Content Models

Microdata definiert kein neues Content Model.

Das Content Model des jeweiligen HTML-Elements bleibt maßgeblich.

---

### Microdata ↔ DOM

Microdata verwendet DOM-Strukturen zur Ermittlung von:

- Items
- Properties
- Referenzen
- Tree Order
- Text Values
- IDs.

---

### Microdata ↔ URLs

URL-Werte werden über die WHATWG-URL-Verarbeitungsregeln bestimmt.

Das betrifft insbesondere:

- `itemtype`
- `itemid`
- URL Property Values
- URL Property Names.

---

### Microdata ↔ `meta`

`meta` ist besonders relevant für maschinenlesbare String Values:

```html
<meta itemprop="description" content="...">
```

---

### Microdata ↔ `time`

`time` ermöglicht die Trennung von:

- menschenlesbarer Darstellung
- maschinenlesbarem Datums-/Zeitwert.

---

### Microdata ↔ `data`

`data` ermöglicht die Trennung zwischen:

- sichtbarem Text
- maschinenlesbarem `value`.

---

### Microdata ↔ SVG

Microdata-Verarbeitung wird nicht automatisch auf SVG-Elemente übertragen.

Ein gleichnamiges Attribut im SVG-Namespace ist kein Microdata-Feature.

---

### Microdata ↔ MathML

Für MathML gilt dieselbe Namespace-Abgrenzung.

---

### Microdata ↔ JSON

WHATWG definiert einen eigenen Microdata-to-JSON-Konvertierungsalgorithmus.

Dieser ist nicht mit JSON-LD gleichzusetzen.

---

### Microdata ↔ vCard

Das WHATWG-vCard-Beispielvokabular basiert auf Microdata und definiert zusätzlich eine Konvertierung in vCard.

---

### Microdata ↔ iCalendar

Das WHATWG-vEvent-Beispielvokabular basiert auf Microdata und definiert zusätzlich eine Konvertierung in iCalendar.

---

## Status / V1

### WHATWG-Status

Microdata ist im aktuellen WHATWG HTML Living Standard definiert.

Status:

**im WHATWG-Standard definiert**

Es handelt sich um ein normatives HTML-Konzept.

---

### `itemscope`

Status:

**normatives HTML-Global-Attribute / Microdata-Feature**

---

### `itemtype`

Status:

**normatives HTML-Global-Attribute / Microdata-Feature**

---

### `itemid`

Status:

**normatives HTML-Global-Attribute / Microdata-Feature**

---

### `itemref`

Status:

**normatives HTML-Global-Attribute / Microdata-Feature**

---

### `itemprop`

Status:

**normatives HTML-Global-Attribute / Microdata-Feature**

---

### Microdata Data Model

Status:

**normatives Microdata-Modell**

---

### Microdata Processing Algorithms

Status:

**normative User-Agent-Verarbeitung**

---

### Sample Vocabularies

Die in §5.3 definierten Vokabulare sind Bestandteil des WHATWG-Standards, stellen aber nicht das gesamte Microdata-Vokabularsystem dar.

Sie sind daher als:

**WHATWG-definierte Beispielvokabulare**

zu kennzeichnen.

---

### Browser-Kompatibilität

Browser-Kompatibilität wird in ZE-WebLab separat behandelt.

Sie ist nicht Bestandteil der WHATWG-Statusklassifikation.

---

### ZE-WebLab-V1

Microdata gehört fachlich in die zweite Rechercheebene.

Begründung:

- Es ist kein einzelnes HTML-Element.
- Es verwendet mehrere globale Attribute.
- Es besitzt ein eigenständiges Datenmodell.
- Es definiert normative Verarbeitungsregeln.
- Es besitzt Beziehungen zu DOM, URLs und mehreren HTML-Elementen.
- Es enthält Konformitätsregeln, die nicht auf ein einzelnes Element reduziert werden können.
- Es besitzt eigene Konvertierungsalgorithmen.

V1-Einstufung:

**Zweite Ebene – eigenständige Feature-Familie**

---

## Erste-Ebene-Abgrenzung

Microdata darf nicht als Wiederholung der Elementreferenz behandelt werden.

Die erste Ebene beschreibt beispielsweise:

- `meta`
- `data`
- `meter`
- `time`
- `a`
- `img`
- `link`
- `object`
- `audio`
- `video`.

Diese Elementdefinitionen können Microdata-Attribute erwähnen.

Die zweite Ebene beschreibt dagegen:

- das gemeinsame Microdata-Modell
- die Attributfamilie
- die Item-Struktur
- Property-Zuordnung
- Item Types
- globale Identifier
- `itemref`
- Wertbestimmung
- Konformität
- Processing Models
- Namespace-Abgrenzung
- JSON-Konvertierung
- WHATWG-Beispielvokabulare.

Eine elementbezogene Erwähnung von `itemprop` oder `itemscope` in einer Elementdatei gilt deshalb nicht als vollständige Microdata-Dokumentation.

---

## Abgrenzung zu anderen Feature-Familien

### Nicht Content Categories

Microdata ist keine Content Category.

---

### Nicht Content Model

Microdata definiert kein allgemeines Content Model.

---

### Nicht Link Type

`itemtype` ist kein Link Type.

Eine URL in `itemtype` ist ein Item Type Identifier und kein `rel`-Link-Type.

---

### Nicht Custom Element

Microdata ist unabhängig von Custom Elements.

Ein Custom Element kann grundsätzlich Microdata-Attribute verwenden, soweit es sich um ein HTML-Element handelt und die Microdata-Regeln erfüllt.

Microdata macht daraus jedoch kein Custom Element.

---

### Nicht JSON-LD

Microdata und JSON-LD sind unterschiedliche Markup-/Datenmodelle.

Die WHATWG-JSON-Konvertierung ist nicht automatisch eine JSON-LD-Konvertierung.

---

### Nicht RDF

Microdata besitzt ein eigenes Datenmodell.

Eine externe Verarbeitung kann Microdata in andere semantische Datenmodelle überführen, dies ist aber nicht automatisch Bestandteil des WHATWG-Microdata-Modells.

---

## Detailprüfung nach WHATWG-Unterabschnitten

## §5.1 Introduction

### §5.1.1 Overview

Geprüft.

Der Abschnitt beschreibt Microdata als Annotation von Inhalten mit maschinenlesbaren Name-Value-Pairs.

Status:

**geprüft**

---

### §5.1.2 The basic syntax

Geprüft.

Behandelt:

- `itemscope`
- `itemprop`
- verschachtelte Items
- URL Values
- `data`
- `meter`
- `time`
- `itemref`.

Status:

**geprüft**

---

### §5.1.3 Typed items

Geprüft.

Behandelt:

- Item Types
- Vokabulare
- `itemtype`
- mehrere kompatible Typen
- Typkontext für Property Names.

Status:

**geprüft**

---

### §5.1.4 Global identifiers for items

Geprüft.

Behandelt:

- `itemid`
- globale Identifier
- Abhängigkeit vom Vokabular
- URL-basierte Identifier.

Status:

**geprüft**

---

### §5.1.5 Selecting names when defining vocabularies

Geprüft.

Behandelt:

- URL-basierte Property Names
- einfache Property Names
- Vokabularentwurf
- globale Eindeutigkeit.

Status:

**geprüft**

---

## §5.2 Encoding microdata

### §5.2.1 The microdata model

Geprüft.

Behandelt:

- Items
- Properties
- Values
- Item Types
- globale Identifier
- Reihenfolge gleicher Property Names.

Status:

**geprüft**

---

### §5.2.2 Items

Geprüft.

Behandelt:

- `itemscope`
- `itemtype`
- `itemid`
- `itemref`
- Typed Items
- globale Identifier.

Status:

**geprüft**

---

### §5.2.3 Names: `itemprop`

Geprüft.

Behandelt:

- Property Names
- Tokenisierung
- URL Property Names
- typed/untyped Items
- Property-Reihenfolge.

Status:

**geprüft**

---

### §5.2.4 Values

Geprüft.

Behandelt:

- Item Values
- `meta`
- URL Property Elements
- `object`
- `data`
- `meter`
- `time`
- Text Values.

Status:

**geprüft**

---

### §5.2.5 Associating names with items

Geprüft.

Behandelt:

- Property-Ermittlungsalgorithmus
- `itemref`
- Memory
- Pending
- Tree Order
- Microdata Errors
- Top-Level Items
- Zyklen
- unzugeordnete `itemprop`.

Status:

**geprüft**

---

### §5.2.6 Microdata and other namespaces

Geprüft.

Behandelt:

- HTML Namespace
- SVG-Abgrenzung
- andere Namespaces.

Status:

**geprüft**

---

## §5.3 Sample microdata vocabularies

Geprüft.

Enthalten sind:

- vCard
- vEvent
- Licensing works.

Diese Vokabulare sind nicht als vollständige externe Semantikfamilien von ZE-WebLab zu behandeln, sondern als Bestandteil der WHATWG-Microdata-Dokumentation.

Status:

**geprüft**

---

## §5.3.1 vCard

Geprüft.

Status:

**geprüft**

---

## §5.3.1.1 Conversion to vCard

Geprüft.

Status:

**geprüft**

---

## §5.3.1.2 Examples

Geprüft.

Status:

**geprüft**

---

## §5.3.2 vEvent

Geprüft.

Status:

**geprüft**

---

## §5.3.2.1 Conversion to iCalendar

Geprüft.

Status:

**geprüft**

---

## §5.3.2.2 Examples

Geprüft.

Status:

**geprüft**

---

## §5.3.3 Licensing works

Geprüft.

Status:

**geprüft**

---

## §5.3.3.1 Examples

Geprüft.

Status:

**geprüft**

---

## §5.4 Converting HTML to other formats

Geprüft.

Der Abschnitt definiert Konvertierungsregeln für Microdata.

---

## §5.4.1 JSON

Geprüft.

Behandelt:

- Item Type
- Global Identifier
- Properties
- verschachtelte Items
- Rekursions-/Memory-Verarbeitung
- JSON-Struktur.

Status:

**geprüft**

---

## Accessibility

### WHATWG

Microdata besitzt keine eigenständige Accessibility-Semantik, die die Semantik des verwendeten HTML-Elements ersetzt.

Die Accessibility-Semantik bleibt an das jeweilige HTML-Element und die entsprechenden Accessibility-Regeln gebunden.

### Externe Spezifikationen

Für konkrete Accessibility-Aussagen können insbesondere folgende externe normative Quellen erforderlich sein:

- ARIA in HTML
- HTML Accessibility API Mappings

Diese Quellen sind nicht Bestandteil der Microdata-Norm selbst.

### Projektregel

Für ZE-WebLab gilt:

**Keine Accessibility-Semantik aus Microdata ableiten, wenn WHATWG bzw. die zuständige Accessibility-Spezifikation dies nicht ausdrücklich definiert.**

---

## Sanitization

### WHATWG-Bezug

Microdata ist keine eigenständige Sanitization-Kategorie.

### Projektbewertung

Für Microdata selbst:

**keine eigenständige Microdata-Sanitization-Kategorie identifiziert**

Die Sanitization-Eigenschaften des konkreten HTML-Elements bleiben maßgeblich.

### Konsequenz

Bei:

```html
<div itemscope itemtype="...">
```

ist die Sanitization-Frage nicht durch "Microdata" als Ganzes beantwortet.

Sie muss auf Ebene des konkreten Elements und der verwendeten Attribute bzw. URL-bezogenen Verarbeitung betrachtet werden.

---

## Offene Punkte

### 1. Historische Microdata-DOM-API

Historische HTML-Spezifikationsstände enthielten eine `HTMLPropertiesCollection`-basierte DOM-API.

Im aktuellen WHATWG-Microdata-Bereich ist diese historische API nicht als eigenständiger aktueller Microdata-Abschnitt vorhanden.

Sie darf daher nicht als aktuelles WHATWG-Feature dokumentiert werden.

Status:

**abgegrenzt; historische Information, nicht aktueller WHATWG-Bestand**

---

### 2. Externe Vokabulare

WHATWG definiert das Microdata-Modell, aber nicht sämtliche externen Vokabulare.

Für konkrete externe Vokabulare muss die jeweilige Vokabularquelle separat geprüft werden.

Status:

**kein offener WHATWG-Fehler; bewusst externe Abgrenzung**

---

### 3. Accessibility

Für konkrete Accessibility-Aussagen zu einzelnen Microdata-Anwendungen können externe Accessibility-Spezifikationen erforderlich sein.

Status:

**fachlich abgegrenzt; keine automatische Microdata-Accessibility-Semantik**

---

### 4. Browser-Kompatibilität

Browser-Support ist bewusst nicht Bestandteil dieser Datei.

Status:

**separate Rechercheebene**

---

## Prüfstatus

| Bereich | Status |
|---|---|
| WHATWG §5 | vollständig geprüft |
| §5.1 Introduction | vollständig geprüft |
| §5.2 Encoding microdata | vollständig geprüft |
| §5.3 Sample microdata vocabularies | vollständig geprüft |
| §5.4 Converting HTML to other formats | vollständig geprüft |
| `itemscope` | geprüft |
| `itemtype` | geprüft |
| `itemid` | geprüft |
| `itemref` | geprüft |
| `itemprop` | geprüft |
| Microdata Model | geprüft |
| Property Values | geprüft |
| Property Association | geprüft |
| Microdata Errors | geprüft |
| Namespace-Regeln | geprüft |
| JSON Conversion | geprüft |
| vCard | geprüft |
| vCard Conversion | geprüft |
| vEvent | geprüft |
| iCalendar Conversion | geprüft |
| Licensing works | geprüft |
| Accessibility | geprüft / externe Abgrenzung |
| Sanitization | geprüft / keine eigenständige Microdata-Kategorie |
| DOM/API-Abgrenzung | geprüft |
| Historische `HTMLPropertiesCollection`-API | abgegrenzt |
| Browser-Support | bewusst nicht Bestandteil |

Gesamtstatus:

**vollständig recherchiert für den aktuellen WHATWG-Bereich §5 Microdata**

---

## Quellen / Referenzen

### Primärquelle

WHATWG HTML Living Standard

Bereich:

`§5 Microdata`

Unterbereiche:

- §5.1 Introduction
- §5.2 Encoding microdata
- §5.3 Sample microdata vocabularies
- §5.4 Converting HTML to other formats

### Relevante normative Querverweise

- WHATWG HTML Standard – Global Attributes
- WHATWG HTML Standard – DOM / Elements
- WHATWG HTML Standard – Content Models
- WHATWG URL Standard
- WHATWG DOM Standard
- RFC 6350 – vCard Format Specification
- RFC 5545 – Internet Calendaring and Scheduling Core Object Specification
- BCP 47 – Language Tags
- ARIA in HTML – für externe Accessibility-Konformität, soweit erforderlich
- HTML Accessibility API Mappings – für Accessibility API Semantik, soweit erforderlich

### Projektquelle

ZE-WebLab Repository:

`z-evolutions/ze-weblab`

Projektpfad:

`docs/html/23-microdata.md`

Repository-Status zum Prüfzeitpunkt:

Die öffentlich abrufbare `docs/html`-Verzeichnisansicht des geprüften `main`-Standes bestätigte die bereits vorhandenen Dateien der ersten Rechercheebene. Eine vorhandene `23-microdata.md` konnte dort zum Prüfzeitpunkt nicht bestätigt werden.

---

## Fachliche Schlussfolgerung

Microdata ist eine eigenständige zweite-Ebenen-Feature-Familie.

Die fachliche Einheit besteht nicht aus einem einzelnen Element, sondern aus:

```text
Microdata
├── Items
│   ├── Item Types
│   ├── Global Identifiers
│   └── Properties
│       ├── Property Names
│       └── Property Values
├── Global Attributes
│   ├── itemscope
│   ├── itemtype
│   ├── itemid
│   ├── itemref
│   └── itemprop
├── Property Association
├── Value Processing
├── Microdata Errors
├── Namespace Rules
├── Sample Vocabularies
│   ├── vCard
│   ├── vEvent
│   └── Licensing works
└── Conversion
    └── JSON
```

Damit ist Microdata klar von der ersten Rechercheebene der nativen HTML-Elemente abzugrenzen.

Die Datei ist als eigenständige zweite-Ebenen-Referenz vorgesehen und darf nicht als zusätzliche Elementliste interpretiert werden.