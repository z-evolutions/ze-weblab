# ZE-WebLab – HTML-Referenz: Common Microsyntaxes

## Arbeitsstand / Quellenstand

- **Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien
- **Feature-Familie:** Common Microsyntaxes
- **Feature-Typ:** Normative Concept / Parsing Concept / Attribute Value Model / Data Type
- **Zieldatei:** `docs/html/27-common-microsyntaxes.md`
- **Normative Primärquelle:** WHATWG HTML Living Standard
- **WHATWG-Hauptabschnitt:** §2.3 Common microsyntaxes
- **Geprüfter WHATWG-Stand:** 11. August 2026
- **Prüfstatus:** vollständig recherchiert für §2.3 und §2.3.1–§2.3.11
- **Browser-Kompatibilität:** nicht Bestandteil dieser Datei
- **V1-Status:** projektspezifisch und nicht mit dem WHATWG-Status gleichzusetzen

### Quellenabgrenzung

Das ZE-WebLab-Repository beantwortet die Frage, welche Informationen im Projekt bereits dokumentiert sind.

Der WHATWG HTML Living Standard beantwortet die Frage, welche gemeinsamen Syntax-, Werte- und Parsingregeln HTML normativ definiert.

Diese Datei dokumentiert die **gemeinsamen Microsyntaxes von HTML**. Sie ist keine erneute Elementreferenz.

Die konkreten Attribute und Elemente, die eine bestimmte Microsyntax verwenden, bleiben in ihren jeweiligen Element- beziehungsweise Feature-Familien dokumentiert.

### Abgrenzung zu anderen ZE-WebLab-Dateien

Die vorhandenen Feature-Familien werden nicht ersetzt:

- `13-global-attributes.md` behandelt die Global-Attributes-Familie.
- `14-content-categories.md` behandelt Content Categories.
- `15-content-models.md` behandelt Content Models.
- `16-link-types.md` behandelt Link Types.
- `17-custom-elements.md` behandelt Custom Elements.
- `18-contexts.md` behandelt HTML-Kontexte.
- `19-dom-interfaces-and-apis.md` behandelt DOM Interfaces und APIs.
- `20-sanitization.md` behandelt Sanitization.
- `21-parsing.md` behandelt Parsing und Tree Construction.
- `22-svg-mathml-integration.md` behandelt HTML/SVG-/MathML-Integration.
- `23-microdata.md` behandelt Microdata.
- `24-user-interaction.md` behandelt User Interaction.
- `25-urls.md` behandelt die HTML-spezifische URL-Systematik.
- `26-fetching-resources.md` behandelt Fetching Resources.

Diese Datei behandelt dagegen die **wiederverwendbaren Syntax- und Werteformate**, die von zahlreichen HTML-Features verwendet werden.

---

## Einordnung

Common Microsyntaxes sind in HTML definierte gemeinsame Syntax- und Parsingregeln für Attributwerte und andere Datenwerte.

Sie beschreiben unter anderem:

- wie Boolean Attributes interpretiert werden,
- wie enumerierte Attribute in Zustände überführt werden,
- wie Integer und Floating-Point-Werte geparst werden,
- wie Prozent- und Längenwerte verarbeitet werden,
- wie Datums- und Zeitwerte aufgebaut und geparst werden,
- wie Legacy Colors verarbeitet werden,
- wie Tokenmengen strukturiert sind,
- wie Referenzen auf Elemente syntaktisch aufgebaut sind,
- wie Media Query Lists als HTML-Werte verwendet werden,
- wie interne eindeutige Werte erzeugt werden.

Die Microsyntax ist deshalb eine **Infrastrukturebene** zwischen dem Markup beziehungsweise Attributwert und dem jeweiligen übergeordneten HTML-Feature.

### Microsyntax ist kein HTML-Element

Eine Microsyntax ist:

- kein HTML-Element,
- keine Content Category,
- kein Content Model,
- kein Link Type,
- kein Custom Element,
- kein DOM Interface.

Sie ist eine normative Syntax- beziehungsweise Parsingdefinition.

### Microsyntax ist nicht dasselbe wie Parsing

Common Microsyntaxes und HTML Parsing müssen getrennt werden.

HTML Parsing beschreibt insbesondere:

- Tokenization,
- Tree Construction,
- Insertion Modes,
- Foreign Content,
- DOM-Erzeugung.

Common Microsyntaxes beschreiben dagegen die Interpretation bestimmter bereits vorliegender Werte.

Beispiel:

```html
<input disabled>
```

Das HTML-Parsing erzeugt das Attribut.

Die Boolean-Attribute-Regel bestimmt anschließend die normative Bedeutung seiner Anwesenheit.

Ebenso:

```html
<input tabindex="-1">
```

Der HTML-Parser erzeugt das Attribut und dessen Stringwert.

Die Integer-Microsyntax bestimmt, ob der Wert als gültiger Integer interpretiert werden kann.

---

# WHATWG-Struktur

Der aktuelle WHATWG HTML Living Standard führt unter §2.3 folgende Unterabschnitte:

1. §2.3.1 Common parser idioms
2. §2.3.2 Boolean attributes
3. §2.3.3 Keywords and enumerated attributes
4. §2.3.4 Numbers
   1. §2.3.4.1 Signed integers
   2. §2.3.4.2 Non-negative integers
   3. §2.3.4.3 Floating-point numbers
   4. §2.3.4.4 Percentages and lengths
   5. §2.3.4.5 Nonzero percentages and lengths
   6. §2.3.4.6 Lists of floating-point numbers
   7. §2.3.4.7 Lists of dimensions
5. §2.3.5 Dates and times
   1. §2.3.5.1 Months
   2. §2.3.5.2 Dates
   3. §2.3.5.3 Yearless dates
   4. §2.3.5.4 Times
   5. §2.3.5.5 Local dates and times
   6. §2.3.5.6 Time zones
   7. §2.3.5.7 Global dates and times
   8. §2.3.5.8 Weeks
   9. §2.3.5.9 Durations
   10. §2.3.5.10 Vaguer moments in time
6. §2.3.6 Legacy colors
7. §2.3.7 Space-separated tokens
8. §2.3.8 Comma-separated tokens
9. §2.3.9 References
10. §2.3.10 Media queries
11. §2.3.11 Unique internal values

Die Spezifikation beschreibt damit sowohl Syntaxdefinitionen als auch zugehörige Parsingalgorithmen.

---

# Inventar

| ID | Feature | Feature-Typ | WHATWG | Status |
|---|---|---|---|---|
| MICRO-001 | Common parser idioms | Parsing Concept | §2.3.1 | im WHATWG definiert |
| MICRO-002 | Boolean Attributes | Attribute Value Model | §2.3.2 | normative Definition |
| MICRO-003 | Enumerated Attributes | Attribute Value Model / State Model | §2.3.3 | normative Definition |
| MICRO-004 | Signed integers | Data Type / Parsing Concept | §2.3.4.1 | normative Definition |
| MICRO-005 | Non-negative integers | Data Type / Parsing Concept | §2.3.4.2 | normative Definition |
| MICRO-006 | Floating-point numbers | Data Type / Parsing Concept | §2.3.4.3 | normative Definition |
| MICRO-007 | Percentages and lengths | Data Type / Parsing Concept | §2.3.4.4 | normative Definition |
| MICRO-008 | Nonzero percentages and lengths | Data Type / Parsing Concept | §2.3.4.5 | normative Definition |
| MICRO-009 | Lists of floating-point numbers | Data Type / Parsing Concept | §2.3.4.6 | normative Definition |
| MICRO-010 | Lists of dimensions | Data Type / Parsing Concept | §2.3.4.7 | normative Definition |
| MICRO-011 | Months | Date/Time Syntax | §2.3.5.1 | normative Definition |
| MICRO-012 | Dates | Date/Time Syntax | §2.3.5.2 | normative Definition |
| MICRO-013 | Yearless dates | Date/Time Syntax | §2.3.5.3 | normative Definition |
| MICRO-014 | Times | Date/Time Syntax | §2.3.5.4 | normative Definition |
| MICRO-015 | Local dates and times | Date/Time Syntax | §2.3.5.5 | normative Definition |
| MICRO-016 | Time zones | Date/Time Syntax | §2.3.5.6 | normative Definition |
| MICRO-017 | Global dates and times | Date/Time Syntax | §2.3.5.7 | normative Definition |
| MICRO-018 | Weeks | Date/Time Syntax | §2.3.5.8 | normative Definition |
| MICRO-019 | Durations | Date/Time Syntax | §2.3.5.9 | normative Definition |
| MICRO-020 | Vaguer moments in time | Date/Time Syntax | §2.3.5.10 | normative Definition |
| MICRO-021 | Legacy colors | Legacy Syntax / Parsing Concept | §2.3.6 | normative Definition |
| MICRO-022 | Space-separated tokens | Token Syntax | §2.3.7 | normative Definition |
| MICRO-023 | Comma-separated tokens | Token Syntax | §2.3.8 | normative Definition |
| MICRO-024 | Hash-name references | Reference Syntax / Parsing Concept | §2.3.9 | normative Definition |
| MICRO-025 | Media query lists | External Syntax Integration | §2.3.10 | normative Definition |
| MICRO-026 | Unique internal values | Internal Value Model | §2.3.11 | normative Definition |

---

# Begriffsdefinitionen

## Common Microsyntax

Eine Common Microsyntax ist eine von HTML definierte Syntax beziehungsweise ein Parsingmodell, das an mehreren Stellen der Spezifikation wiederverwendet werden kann.

Die Definition enthält typischerweise:

- zulässige Zeichenfolgen,
- Zustände,
- Parsingregeln,
- Fehlerbehandlung,
- gegebenenfalls Konformitätsanforderungen.

## Parser

Ein Parser verarbeitet eine Zeichenfolge nach einem definierten Algorithmus und erzeugt daraus einen semantischen Wert oder einen Fehler.

## Valid String

Ein valid string ist eine Zeichenfolge, die die für die jeweilige Microsyntax definierten syntaktischen Anforderungen erfüllt.

Die Validität eines Strings ist nicht automatisch identisch mit der erfolgreichen Interpretation durch einen beliebigen Browser oder eine beliebige Programmbibliothek.

## Parsing Error

Ein Parsingalgorithmus kann bei einer nicht passenden Eingabe mit einem Fehler beziehungsweise einem definierten Fehlschlag enden.

Das Verhalten muss anhand des jeweiligen HTML-Algorithmus bestimmt werden.

---

# Common Parser Idioms

## §2.3.1

Einige Microsyntax-Parser verwenden ein gemeinsames algorithmisches Muster.

Dabei existieren insbesondere:

- `input` – die zu verarbeitende Zeichenfolge
- `position` – eine Position innerhalb der Zeichenfolge

Die Parser bewegen `position` schrittweise durch `input`.

Typische Hilfsoperationen umfassen:

- ASCII-Whitespace überspringen,
- Code-Point-Sequenzen sammeln,
- Zeichen vergleichen,
- Sequenzen interpretieren,
- bei Fehlern abbrechen.

### Normative Bedeutung

Diese Parser-Idiome sind keine eigene Datenstruktur und keine API.

Sie bilden ein gemeinsames Beschreibungsmuster für die in §2.3 definierten Algorithmen.

### Fehlerbehandlung

Die jeweilige Microsyntax definiert selbst, wann ein Parser:

- erfolgreich einen Wert liefert,
- einen Fehler liefert,
- `nothing` zurückgibt,
- einen Default-Zustand verwendet.

Daher darf nicht aus einem allgemeinen Parsermuster auf ein einheitliches Fehlerverhalten aller Microsyntaxes geschlossen werden.

---

# Boolean Attributes

## §2.3.2

Ein Boolean Attribute verwendet die **Anwesenheit des Attributes** als semantisches Signal.

### True

Ist das Attribut vorhanden, repräsentiert es grundsätzlich den True-Zustand.

### False

Ist das Attribut nicht vorhanden, repräsentiert es den False-Zustand.

### Zulässige Markupwerte

Ist ein Boolean Attribute vorhanden, muss sein Wert entweder:

- der leere String sein,
- oder ein ASCII-case-insensitiver Match des kanonischen Attributnamens ohne führenden oder nachfolgenden Whitespace.

Beispiele:

```html
<input disabled>
<input disabled="">
<input disabled="disabled">
```

Diese Formen repräsentieren den gesetzten Zustand des Boolean Attributes.

### Nicht zulässig

Folgende Schreibweise darf nicht als allgemeiner Wahrheitswert interpretiert werden:

```html
<input disabled="true">
<input disabled="false">
```

Insbesondere bedeutet:

```html
disabled="false"
```

nicht „disabled ist false“.

Ein Boolean Attribute wird zur Darstellung des False-Zustands weggelassen.

### Wichtige Konsequenz

Boolean Attributes sind keine String-Boolean-Konvention.

Nicht:

```text
"true"  → true
"false" → false
```

sondern:

```text
Attribut vorhanden → true
Attribut nicht vorhanden → false
```

Die konkrete HTML-Definition eines einzelnen Boolean Attributes bleibt maßgeblich.

### Querverweise

Relevante Beispiele aus dem Projekt:

- `autofocus`
- `headingreset`
- `inert`
- `itemscope`
- `disabled`
- `checked`
- `multiple`
- `required`

Die konkrete Semantik bleibt in den jeweiligen Feature- und Elementdefinitionen dokumentiert.

---

# Keywords and Enumerated Attributes

## §2.3.3

Enumerated Attributes besitzen eine endliche Menge definierter Zustände.

Dabei werden drei Ebenen unterschieden:

1. Content-Attribute-Wert
2. Keyword-/State-Mapping
3. resultierender Zustand

### Zustandsbestimmung

Die allgemeine Reihenfolge ist:

1. Prüfen, ob das Attribut fehlt.
2. Falls definiert, den Missing Value Default verwenden.
3. Keyword-Matching durchführen.
4. Falls definiert, den Empty Value Default berücksichtigen.
5. Falls definiert, den Invalid Value Default verwenden.
6. Andernfalls liegt kein definierter Zustand vor.

### Missing Value Default

Der Missing Value Default definiert den Zustand, wenn das Attribut nicht angegeben wurde.

### Empty Value Default

Der Empty Value Default definiert den Zustand für einen leeren Attributwert, soweit die jeweilige Attributdefinition einen solchen Zustand vorsieht.

### Invalid Value Default

Der Invalid Value Default definiert den Zustand für einen nicht passenden beziehungsweise ungültigen Wert, soweit vorhanden.

### Canonical Keyword

Ein Zustand kann ein kanonisches Keyword besitzen.

Das ist insbesondere für Reflection relevant.

Das kanonische Keyword muss nicht zwingend identisch mit jedem Keyword sein, das denselben Zustand repräsentiert.

### Konformität

Für Autoren gelten die jeweils definierten conforming keywords.

Ein beliebiger String ist daher nicht automatisch ein zulässiger enumerierter Attributwert.

### Beispiele

Zu den im ZE-WebLab dokumentierten enumerierten Attributen gehören unter anderem:

- `hidden`
- `contenteditable`
- `spellcheck`
- `autocapitalize`
- `autocorrect`
- `inputmode`
- `enterkeyhint`
- `translate`
- `dir`
- `draggable`
- `popover`
- `writingsuggestions`

Die konkrete Zustandsdefinition bleibt jeweils Bestandteil des zugehörigen Features.

---

# Numbers

## §2.3.4

HTML definiert mehrere numerische Microsyntaxes.

Dabei ist insbesondere zwischen folgenden Typen zu unterscheiden:

- signed integer
- non-negative integer
- floating-point number
- percentage
- length
- nonzero percentage
- nonzero length
- list of floating-point numbers
- list of dimensions

Diese Typen dürfen nicht pauschal als „Zahl“ behandelt werden.

---

## Signed Integers

### §2.3.4.1

Ein gültiger Integer besteht aus:

- einer oder mehreren ASCII-Ziffern,
- optional mit einem führenden `-`.

Beispiele:

```text
0
1
42
-1
-42
```

Ein führendes `+` gehört nicht zur allgemeinen gültigen Integer-Syntax.

### Parsing

Der Parser:

1. beginnt am Anfang der Eingabe,
2. verarbeitet gegebenenfalls das Minuszeichen,
3. sammelt eine Sequenz von ASCII-Ziffern,
4. interpretiert diese als Dezimalzahl,
5. liefert den resultierenden Integer oder einen Fehler.

### Whitespace

Das konkrete Parsing berücksichtigt die in der Spezifikation definierten Whitespace-Regeln.

Eine Anwendung darf daher nicht eigenständig eine abweichende Integer-Syntax annehmen.

---

## Non-negative Integers

### §2.3.4.2

Ein non-negative integer ist ein Integer ohne negativen Wert.

Die zulässige Syntax und der Parsingalgorithmus bauen auf der entsprechenden HTML-Definition auf.

Typische Anwendungen sind Attribute, bei denen negative Werte semantisch nicht zulässig sind.

### Abgrenzung

Ein gültiger Integer ist nicht automatisch ein gültiger non-negative integer.

Beispiel:

```text
-1
```

kann syntaktisch ein Integer sein, ist aber kein non-negative integer.

---

## Floating-Point Numbers

### §2.3.4.3

HTML definiert eine eigene Microsyntax für Floating-Point-Zahlen.

Sie kann unter anderem enthalten:

- Ganzzahlanteile,
- Dezimalpunkt,
- Bruchteile,
- Exponenten,
- negative Werte.

Beispiele für typische gültige Formen:

```text
0
1
1.5
-1.5
0.25
1e3
1.5e-2
```

Die exakte Konformität richtet sich nach dem HTML-Parser und nicht nach einer beliebigen Programmiersprache.

### Besonderheit des Pluszeichens

Ein führendes `+` kann vom Parsingalgorithmus verarbeitet werden, ist aber für die Authoring-Konformität nicht in derselben Weise zulässig wie die konformen Formen.

Daher darf:

```text
+1
```

nicht einfach als vollständig konforme HTML-Zahl behandelt werden.

### Parsing

Der Parser arbeitet unter anderem mit:

- `value`
- `divisor`
- `exponent`
- `position`

und verarbeitet Ganzzahl-, Bruch- und Exponentenanteile.

---

# Percentages and Lengths

## §2.3.4.4

HTML definiert eine gemeinsame Syntax für Werte, die entweder:

- eine Zahl,
- einen Prozentwert,
- oder einen relativen Wert

repräsentieren können.

Die Syntax verwendet insbesondere:

- numerische Werte,
- `%`,
- `*`.

### Prozentwerte

Ein Prozentwert wird durch das Prozentzeichen gekennzeichnet:

```text
50%
100%
0%
```

### Relative Werte

In den entsprechenden HTML-Microsyntaxes kann `*` einen relativen Wert kennzeichnen.

### Parsing

Die Spezifikation definiert einen Parser, der unter anderem:

1. Whitespace überspringt,
2. den numerischen Anteil bestimmt,
3. einen optionalen Bruchteil verarbeitet,
4. anschließend die Einheit bestimmt,
5. das Ergebnis als Wert mit Einheit zurückgibt.

---

# Nonzero Percentages and Lengths

## §2.3.4.5

Die Nonzero-Variante verwendet dieselbe grundlegende Wertsystematik, verlangt aber einen von Null verschiedenen Wert, soweit die jeweilige Syntax dies definiert.

Damit sind:

```text
0%
```

und:

```text
0
```

nicht automatisch gültige Werte für eine Microsyntax, die ausdrücklich einen nonzero percentage oder nonzero length verlangt.

---

# Lists of Floating-Point Numbers

## §2.3.4.6

HTML definiert auch Listen von Floating-Point-Zahlen.

Dabei werden einzelne Werte innerhalb einer definierten Zeichenfolgenstruktur verarbeitet.

Die genaue Trennung und Whitespace-Behandlung richtet sich nach dem jeweiligen Parser.

Beispielhafte Werte:

```text
1 2 3
1.5 2.5 3.5
```

Eine solche Liste ist nicht dasselbe wie eine allgemeine durch Leerzeichen getrennte Tokenliste.

Die Elemente der Liste werden numerisch interpretiert.

---

# Lists of Dimensions

## §2.3.4.7

Eine Liste von Dimensionswerten verwendet die numerische Parsinglogik zusammen mit den dafür definierten Einheiten.

Der Parser unterscheidet insbesondere numerische Werte und deren Einheiten.

Die Spezifikation beschreibt auch die Verarbeitung von:

- Ganzzahlanteilen,
- Bruchteilen,
- Prozentwerten,
- relativen Werten.

Diese Syntax ist deshalb von der allgemeinen Token-Syntax getrennt zu behandeln.

---

# Dates and Times

## §2.3.5

HTML definiert eine umfangreiche Gruppe von Datum-/Zeit-Microsyntaxes.

Diese Syntaxen sind zwar teilweise an ISO 8601 angelehnt, aber **nicht einfach mit einer allgemeinen ISO-8601-Parserbibliothek gleichzusetzen**.

WHATWG definiert die HTML-spezifischen Gültigkeits- und Parsingregeln ausdrücklich.

Die Gruppe umfasst:

- Months
- Dates
- Yearless dates
- Times
- Local dates and times
- Time zones
- Global dates and times
- Weeks
- Durations
- Vaguer moments in time

Die Datumsregeln verwenden den proleptischen Gregorianischen Kalender.

---

# Months

## §2.3.5.1

Ein gültiger Month-Wert repräsentiert:

- ein Jahr,
- einen Monat.

Das Jahr muss mindestens vier Ziffern besitzen und größer als 0 sein.

Die Monatskomponente liegt im Bereich:

```text
01–12
```

Die Grundstruktur ist:

```text
YYYY-MM
```

Beispiel:

```text
2026-08
```

Ein Monat ist dabei ein eigenständiger Datentyp und nicht lediglich ein beliebiger String mit diesem Erscheinungsbild.

---

# Dates

## §2.3.5.2

Ein gültiges Datum repräsentiert:

- Jahr,
- Monat,
- Tag.

Die Grundstruktur ist:

```text
YYYY-MM-DD
```

Beispiel:

```text
2026-08-16
```

### Kalenderregeln

Die Anzahl der Tage eines Monats wird anhand der Gregorianischen Kalenderregeln bestimmt.

Dabei gelten insbesondere:

- 31 Tage für bestimmte Monate,
- 30 Tage für bestimmte Monate,
- 28 beziehungsweise 29 Tage für Februar.

Schaltjahre werden nach den definierten Gregorianischen Regeln bestimmt.

Ein syntaktisch ähnlich aussehender, aber kalendarisch ungültiger Wert ist daher kein gültiges Datum.

---

# Yearless Dates

## §2.3.5.3

Eine yearless date repräsentiert:

- Monat,
- Tag,

aber kein Jahr.

Grundstruktur:

```text
MM-DD
```

Beispiel:

```text
08-16
```

Diese Syntax ist insbesondere dann relevant, wenn ein wiederkehrender Tag unabhängig von einem bestimmten Jahr ausgedrückt werden soll.

Die Gültigkeit des Tages hängt weiterhin vom angegebenen Monat ab.

---

# Times

## §2.3.5.4

Eine gültige Zeit repräsentiert:

- Stunde,
- Minute,
- Sekunde,
- optional einen Bruchteil der Sekunde.

Grundstruktur:

```text
HH:MM
HH:MM:SS
HH:MM:SS.s
```

Die Spezifikation definiert den zulässigen Wertebereich der einzelnen Komponenten.

Insbesondere wird zwischen:

- Stunde,
- Minute,
- Sekunde,
- fractional seconds

unterschieden.

Eine Zeitzone ist Bestandteil einer Time-Syntax nicht automatisch.

---

# Local Dates and Times

## §2.3.5.5

Ein local date and time besteht aus:

- einem Datum,
- einer Zeit,
- ohne Zeitzone.

Zulässige Trennung:

```text
YYYY-MM-DDTHH:MM
```

oder entsprechend der definierten Variante mit einem einzelnen Leerzeichen.

Die normalisierte Form verwendet `T`.

Beispiel:

```text
2026-08-16T14:30
```

### Keine Zeitzone

Ein local date and time enthält selbst keine Zeitzoneninformation.

Es darf daher nicht automatisch als UTC interpretiert werden.

---

# Time Zones

## §2.3.5.6

Ein time-zone offset besteht aus:

- Vorzeichen,
- Stunden,
- Minuten.

Alternativ kann `Z` für UTC verwendet werden.

Beispiele:

```text
Z
+01:00
-05:00
+0130
```

Die WHATWG-Syntax definiert die zulässigen Bereiche ausdrücklich.

Dabei sind auch Offsets zulässig, die über den heute praktisch verwendeten Zeitzonenbereich hinausgehen.

Die syntaktische Zulässigkeit eines Offsets ist deshalb nicht identisch mit der Aussage, dass eine reale Zeitzone genau diesen Offset aktuell verwendet.

---

# Global Dates and Times

## §2.3.5.7

Ein global date and time kombiniert:

- Datum,
- Zeit,
- Zeitzonenoffset.

Beispiel:

```text
2026-08-16T14:30:00Z
```

oder mit einem expliziten Offset:

```text
2026-08-16T14:30:00+02:00
```

### Ergebnis

Beim Parsing wird der lokale Zeitpunkt unter Berücksichtigung des Offsets in einen Zeitpunkt in UTC überführt.

Die zugehörige Offsetinformation kann für Roundtripping beziehungsweise Darstellung erhalten bleiben.

### Konformität

Ein global date and time ist nicht bloß ein beliebiger ISO-8601-String.

Maßgeblich sind die von HTML definierten Regeln.

---

# Weeks

## §2.3.5.8

HTML definiert eine Week-Syntax.

Grundstruktur:

```text
YYYY-Www
```

Beispiel:

```text
2026-W33
```

Dabei bestehen:

- eine Week-Year-Nummer,
- eine Week-Nummer.

### Wochenjahr

Das Week-Year ist nicht immer identisch mit dem Gregorianischen Kalenderjahr des entsprechenden Tages.

Die erste Woche eines Week-Years ist die Woche, die den ersten Donnerstag des entsprechenden Gregorianischen Jahres enthält.

Ein Jahr kann nach den definierten Regeln 52 oder 53 Wochen besitzen.

---

# Durations

## §2.3.5.9

Eine Duration repräsentiert eine bestimmte Anzahl von Sekunden.

HTML definiert dabei zwei relevante Schreibweisenfamilien:

1. ISO-ähnliche Duration-Syntax
2. menschenlesbare Duration-Komponenten

### ISO-ähnliche Form

Beispiel:

```text
P3D
PT2H30M
PT45S
P1DT2H
```

### Menschenlesbare Komponenten

Die alternative Syntax kann Einheiten wie:

```text
w
d
h
m
s
```

verwenden.

Beispiel:

```text
2h 30m
```

### Monate und Jahre

Eine Duration im Sinne dieses HTML-Modells muss eine bestimmte Anzahl von Sekunden repräsentieren.

Monate und Jahre sind deshalb als tatsächliche Durationseinheiten nicht eindeutig in Sekunden umrechenbar.

Der Parser kann solche Einheiten im Rahmen des definierten Parsingmodells berücksichtigen, verwirft aber Ergebnisse, die eine nicht zulässige Duration mit Monaten beziehungsweise Jahren ergeben.

### Ergebnis

Eine gültige HTML-Duration repräsentiert letztlich eine konkrete Anzahl von Sekunden.

---

# Vaguer Moments in Time

## §2.3.5.10

Diese Microsyntax akzeptiert einen eingeschränkteren beziehungsweise allgemeineren Zeitpunktstyp.

Ein gültiger Wert kann insbesondere sein:

- ein Datum,
- eine globale Datums-/Zeitangabe.

Der Parser kann entsprechend einen:

- Date-Wert,
- Time-Wert,
- Global-Date-and-Time-Wert

oder keinen Wert liefern.

Diese Syntax ist deshalb nicht mit einer vollständigen ISO-8601-Datumszeit gleichzusetzen.

---

# Legacy Colors

## §2.3.6

HTML enthält Parsingregeln für bestimmte obsolete Legacy-Attribute, die Farbangaben nach historischen HTML-Regeln verarbeiten.

### Status

Die Legacy Color Syntax ist ein **historisches/obsoletes Verarbeitungskonzept**.

Sie ist deshalb nicht als modernes allgemeines CSS-Farbmodell zu dokumentieren.

### Parsing

Der Algorithmus behandelt unter anderem:

- leere Eingaben,
- führenden und nachfolgenden ASCII-Whitespace,
- den Sonderwert `transparent`,
- benannte Farben,
- kurze Hexfarben,
- nicht-hexadezimale Zeichen,
- Unicode-Codepoints außerhalb des Basic Multilingual Plane,
- Begrenzung auf 128 Codepoints,
- Zerlegung in drei Farbkomponenten.

### Externe CSS-Beziehung

Die resultierende Farbe wird in Beziehung zu den CSS-Farbdefinitionen gesetzt.

HTML definiert jedoch für diesen Legacy-Bereich ein eigenes Parsingverfahren.

### Abgrenzung

Diese Datei behandelt nicht:

- das moderne CSS Color Model,
- CSS Color 4,
- vollständige CSS-Farbsyntax.

---

# Space-Separated Tokens

## §2.3.7

Ein Set of space-separated tokens besteht aus:

- null oder mehr Wörtern,
- getrennt durch einen oder mehrere ASCII-Whitespace-Zeichen.

Ein Token selbst besteht aus mindestens einem Zeichen, das kein ASCII-Whitespace ist.

Beispiel:

```text
alpha beta gamma
```

führt zu den Tokens:

```text
alpha
beta
gamma
```

### Führender und nachfolgender Whitespace

Führender und nachfolgender ASCII-Whitespace kann Bestandteil der äußeren Zeichenfolge sein, ohne Teil eines Tokens zu werden.

### Unique Tokens

Die Spezifikation unterscheidet insbesondere:

- unordered set of unique space-separated tokens
- ordered set of unique space-separated tokens

### Ordered

Bei einer ordered token set ist die Reihenfolge semantisch relevant.

### Unordered

Bei einer unordered token set ist die Reihenfolge nicht semantisch relevant.

### Zulässige Tokenwerte

Ein konkretes Feature kann zusätzlich eine Menge erlaubter Tokens definieren.

Dann gilt:

- bekannte Tokens sind konform,
- nicht definierte Tokens sind nicht konform.

Die allgemeine Microsyntax selbst definiert jedoch nicht automatisch die erlaubten Wörter jedes einzelnen Attributes.

### Vergleich

Die Art des Tokenvergleichs wird jeweils durch die konkrete Attribut- oder Featuredefinition bestimmt.

Mögliche Regeln können insbesondere Case-Sensitivity oder Case-Insensitivity betreffen.

---

# Comma-Separated Tokens

## §2.3.8

Eine comma-separated token set besteht aus Tokens, die durch einzelne Kommas getrennt werden.

Beispiel:

```text
alpha,beta,gamma
```

### Whitespace

Whitespace kann um die einzelnen Tokens herum auftreten.

Beispiel:

```text
alpha, beta, gamma
```

### Leere Tokens

Im Gegensatz zur Space-Separated-Token-Syntax kann ein comma-separated token set auch leere Tokens enthalten.

Beispiel:

```text
a,,b
```

ergibt:

```text
a
""
b
```

### Komma innerhalb eines Tokens

Ein Komma selbst gehört nicht zum Token.

### Konkrete Einschränkungen

Ein Feature kann zusätzliche Anforderungen für seine Tokens definieren.

Die allgemeine Microsyntax schreibt nicht vor, dass alle comma-separated token sets dieselben zulässigen Werte besitzen.

---

# References

## §2.3.9

HTML definiert eine Hash-Name-Reference-Syntax für Referenzen auf bestimmte Elemente.

Ein Hash-Name-Reference beginnt mit:

```text
#
```

gefolgt von einem Namen.

### Referenzauflösung

Die Parsingregeln suchen im jeweiligen Scope nach dem ersten passenden Element in Tree Order.

Dabei wird insbesondere ein Element berücksichtigt, dessen:

- `id`
- oder `name`

dem Referenzwert entspricht.

### `name` und `id`

Ein wichtiger normativer Unterschied ist:

- Für die Ermittlung einer gültigen Hash-Name-Reference ist insbesondere das `name`-Attribut maßgeblich.
- Das Parsing kann `id` berücksichtigen, um ein Ziel aufzulösen.
- Eine Referenz, die ausschließlich über `id` aufgelöst wird, ist nach der Definition nicht automatisch eine gültige Hash-Name-Reference.

### Tree Order

Wenn mehrere passende Elemente vorhanden sind, wird das erste passende Element in Tree Order ausgewählt.

### Kein universeller URL-Parser

Eine Hash-Name-Reference ist nicht dasselbe wie eine vollständige URL.

Sie ist eine HTML-spezifische Referenzsyntax.

---

# Media Queries

## §2.3.10

HTML definiert für entsprechende Stellen eine Microsyntax für gültige Media Query Lists.

Die eigentliche Syntax wird durch die Media Queries-Spezifikation definiert.

### HTML-Verwendung

HTML prüft beziehungsweise verwendet einen Wert als Media Query List.

Beispiel:

```html
<link rel="stylesheet" media="screen and (min-width: 800px)" href="style.css">
```

### Empty Value

Eine leere Zeichenfolge beziehungsweise eine Zeichenfolge, die nur aus ASCII-Whitespace besteht, gilt als Media Query List, die mit der Benutzerumgebung matcht.

### Externe normative Quelle

Die konkrete Grammatik der Media Queries wird nicht vollständig durch HTML neu definiert.

HTML verweist hierfür auf die zuständige CSS-Spezifikation.

### Abgrenzung

Diese Datei dokumentiert daher:

- die HTML-Integration,
- die Konformitätsregel,
- die Matching-Bedeutung innerhalb von HTML.

Sie dokumentiert nicht die vollständige Media Queries-Spezifikation.

---

# Unique Internal Values

## §2.3.11

Ein Unique Internal Value ist ein interner Wert mit besonderen Eigenschaften.

Er ist:

- serialisierbar,
- nach Wert vergleichbar,
- niemals für Script exponiert.

### Erzeugung

Zur Erzeugung eines neuen Unique Internal Value wird ein Wert zurückgegeben, der zuvor noch nicht durch diesen Algorithmus zurückgegeben wurde.

### Zweck

Unique Internal Values können intern verwendet werden, wenn eine Implementierung beziehungsweise ein Algorithmus einen eindeutigen Wert benötigt, der nicht durch Script beobachtbar sein darf.

### Keine öffentliche API

Ein Unique Internal Value ist:

- kein DOM Interface,
- kein JavaScript-Objekt,
- kein HTML-Attributwert,
- kein öffentliches Web-API-Token.

Es ist ein normatives internes Konzept.

---

# Attribute

Common Microsyntaxes sind keine eigene Attributfamilie im Sinne eines festen Attributinventars.

Vielmehr liefern sie Wertmodelle für zahlreiche Attribute.

## Boolean Attribute

Beispiele aus dem ZE-WebLab-Bestand:

- `autofocus`
- `hidden` ist **nicht** Boolean, sondern enumeriert
- `inert`
- `itemscope`
- `headingreset`
- `disabled`
- `checked`
- `multiple`
- `required`

Die konkrete Einordnung ist immer anhand der jeweiligen WHATWG-Definition vorzunehmen.

## Enumerated Attributes

Beispiele:

- `hidden`
- `contenteditable`
- `spellcheck`
- `autocapitalize`
- `autocorrect`
- `inputmode`
- `enterkeyhint`
- `translate`
- `dir`
- `draggable`
- `popover`
- `writingsuggestions`

Die gemeinsame Zustandslogik wird in §2.3.3 definiert.

## Integer Attributes

Beispiele können unter anderem sein:

- `tabindex`
- `start`
- `rowspan`
- `colspan`
- weitere elementbezogene Integer-Attribute.

Das konkrete Attribut kann zusätzlich eigene Wertebereiche oder Sonderregeln definieren.

## Floating-Point Values

Floating-Point-Microsyntaxes werden dort eingesetzt, wo HTML numerische Werte mit entsprechender Genauigkeit benötigt.

Die konkrete Verwendung ist featureabhängig.

## Token Attributes

Beispiele:

- `class` verwendet DOM-seitig eine Tokenliste, ist aber nicht allein aufgrund dieser Verwendung ein in HTML definiertes Global Attribute.
- `accesskey` verwendet eine geordnete Menge eindeutiger Tokens.
- `itemprop` verwendet ein Microdata-spezifisches Tokenmodell.
- `rel` verwendet Link-Type-Tokens.

Diese Attribute dürfen deshalb nicht zu einer einzigen semantischen Attributfamilie zusammengefasst werden.

---

# Content Categories

Common Microsyntaxes definieren keine eigene Content Category.

Die Microsyntax kann aber von Attributen verwendet werden, die auf Elementen verschiedener Content Categories vorkommen.

Beispiele:

- Flow Content
- Phrasing Content
- Metadata Content
- Interactive Content
- Form-associated Elemente
- Embedded Content

Die Content Category eines Elements bleibt eine separate Informationsebene.

Querverweis:

`14-content-categories.md`

---

# Context

Common Microsyntaxes besitzen grundsätzlich keinen eigenen HTML Context.

Ein Context kann jedoch bestimmen:

- welches Attribut überhaupt verwendet wird,
- welche Tokens erlaubt sind,
- welche Default-Zustände gelten,
- wie ein geparster Wert anschließend verarbeitet wird.

Beispiel:

Ein enumeriertes Attribut kann dieselbe allgemeine Zustandslogik wie ein anderes Attribut verwenden, aber vollständig andere Keywords und Zustände besitzen.

Daher gilt:

**Gemeinsame Microsyntax ≠ gemeinsamer semantischer Kontext.**

---

# Content Model

Common Microsyntaxes definieren kein Content Model.

Sie beziehen sich auf:

- Attributwerte,
- Datenwerte,
- Referenzwerte,
- interne Werte.

Das Content Model eines HTML-Elements bleibt in den Elementdefinitionen beziehungsweise in `15-content-models.md` dokumentiert.

---

# Processing Models

## Allgemeine Beziehung

Eine Microsyntax besteht nicht immer nur aus einer Validierungsregel.

Sie kann einen vollständigen Parsingalgorithmus enthalten.

Dabei können folgende Ergebnisse entstehen:

- semantischer Wert,
- Zustand,
- Fehler,
- `nothing`,
- internes Objekt.

## Parser und Konformität

Es muss zwischen zwei Fragen unterschieden werden:

1. Ist ein Attributwert für Autoren konform?
2. Wie wird ein vorhandener Wert vom User Agent geparst?

Diese Fragen können unterschiedliche Regeln besitzen.

Das gilt insbesondere für:

- enumerierte Attribute,
- numerische Werte,
- Legacy Colors,
- Datums-/Zeitwerte.

## Parsingalgorithmus

Ein HTML-Microsyntax-Parser kann:

- Whitespace überspringen,
- Zeichen sammeln,
- Werte konvertieren,
- Bereiche prüfen,
- Sonderfälle behandeln,
- bei Fehler abbrechen.

Die konkrete Reihenfolge ist normativ.

Eine Implementierung darf deshalb nicht einfach einen beliebigen Standardparser einsetzen, wenn dessen Fehlerbehandlung von HTML abweicht.

---

# DOM Interfaces / APIs

Common Microsyntaxes definieren grundsätzlich keine eigenen DOM Interfaces.

Sie beeinflussen aber DOM APIs mittelbar.

Beispiele:

```text
Content Attribute
       ↓
Microsyntax
       ↓
HTML State / Value
       ↓
IDL Reflection oder DOM Processing
```

Beispiel für ein enumeriertes Attribut:

```text
contenteditable
      ↓
Enumerated Attribute Parsing
      ↓
ContentEditable State
      ↓
ElementContentEditable API
```

Beispiel für einen Integer:

```text
tabindex="-1"
      ↓
Integer Parsing
      ↓
tabIndex / Focus Processing
```

Die konkrete IDL-Semantik bleibt in der DOM-/API-Dokumentation beziehungsweise im jeweiligen HTML-Feature.

Querverweis:

`19-dom-interfaces-and-apis.md`

---

# Accessibility

Common Microsyntaxes selbst definieren keine allgemeine Accessibility-Semantik.

Die Accessibility-Bedeutung entsteht vielmehr durch das Feature, das eine Microsyntax verwendet.

Beispiele:

- `tabindex` → Fokusmodell und Accessibility
- `hidden` → Visibility und Accessibility Exposure
- `aria-*` → ARIA-Spezifikation
- `lang` → Sprache und Accessibility
- `dir` → Schreibrichtung und Textverarbeitung

Daher darf aus der Tatsache, dass eine Microsyntax einen Wert korrekt parst, keine Accessibility-Bedeutung abgeleitet werden.

Für Accessibility relevante Aussagen müssen aus der jeweiligen Featuredefinition beziehungsweise der zuständigen Accessibility-Spezifikation stammen.

---

# Sanitization

Common Microsyntaxes sind keine Sanitization-Familie.

Das Parsen eines Wertes bedeutet nicht automatisch, dass der Wert sicher oder sanitisiert ist.

Beispiele:

- Ein gültiger URL-Wert ist nicht automatisch sicher.
- Ein gültiger Token ist nicht automatisch sicher.
- Ein gültiger String ist nicht automatisch sanitisiert.
- Eine gültige Farbe ist nicht automatisch eine Sicherheitsprüfung.

Sanitization bleibt deshalb eine separate Dimension.

Querverweis:

`20-sanitization.md`

---

# Konformitätsregeln

## Allgemeines

Konformität muss auf Feature-Ebene geprüft werden.

Die allgemeine Microsyntax definiert ein Wertmodell, aber das konkrete Feature kann zusätzliche Anforderungen stellen.

Beispiel:

Eine allgemeine Tokenliste kann syntaktisch korrekt sein, während ein bestimmtes Attribut nur eine Teilmenge bestimmter Tokens zulässt.

## Boolean Attributes

Bei Boolean Attributes:

- Attribut vorhanden → True-Zustand
- Attribut nicht vorhanden → False-Zustand

`true` und `false` sind keine generischen Boolean-Attribute-Werte.

## Enumerated Attributes

Bei enumerierten Attributen:

- konforme Keywords,
- Missing Value Default,
- Empty Value Default,
- Invalid Value Default

müssen getrennt betrachtet werden.

## Zahlen

Bei numerischen Werten müssen insbesondere unterschieden werden:

- signed integer,
- non-negative integer,
- floating-point number,
- percentage,
- length,
- nonzero value,
- list of numbers.

## Datum/Zeit

Datum-/Zeitwerte müssen nach den HTML-spezifischen Regeln geprüft werden.

Eine allgemeine ISO-8601-Konformität reicht nicht als Ersatz für die WHATWG-Regeln.

## Token

Bei Tokenlisten müssen unter anderem berücksichtigt werden:

- Whitespace,
- Separator,
- Duplikate,
- Reihenfolge,
- erlaubte Tokenwerte,
- Vergleichsregeln.

## References

Bei Hash-Name-References muss zwischen:

- syntaktischer Referenz,
- gültiger Referenz,
- tatsächlicher Zielauflösung

unterschieden werden.

---

# Querverweise

## Microsyntax ↔ Global Attributes

`13-global-attributes.md`

Viele Global Attributes verwenden die in §2.3 definierten Wertmodelle.

Beispiele:

- `autofocus`
- `contenteditable`
- `hidden`
- `inert`
- `inputmode`
- `tabindex`

Die Global-Attribute-Datei dokumentiert die konkrete Attributsemantik.

Diese Datei dokumentiert die gemeinsame Syntax- und Parsinginfrastruktur.

## Microsyntax ↔ Content Categories

`14-content-categories.md`

Keine direkte Identität.

Content Categories beschreiben Elementklassifikationen.

Microsyntaxes beschreiben Wertformate.

## Microsyntax ↔ Content Models

`15-content-models.md`

Keine direkte Identität.

Content Models beschreiben zulässigen Inhalt.

Microsyntaxes beschreiben Werte und Syntax.

## Microsyntax ↔ Link Types

`16-link-types.md`

Link Types verwenden insbesondere Token- beziehungsweise Keyword-Systeme.

Die konkrete Semantik der Link Types wird dort dokumentiert.

## Microsyntax ↔ DOM

`19-dom-interfaces-and-apis.md`

DOM Interfaces können Werte aus Microsyntaxes reflektieren oder verarbeitete Zustände exponieren.

## Microsyntax ↔ Parsing

`21-parsing.md`

HTML Parsing und Microsyntax Parsing sind unterschiedliche Ebenen.

```text
HTML source
    ↓
HTML tokenizer / tree construction
    ↓
DOM / content attributes
    ↓
Microsyntax parsing
    ↓
semantic state / value
```

## Microsyntax ↔ Microdata

`23-microdata.md`

Microdata verwendet mehrere Token- und URL-bezogene Wertmodelle.

Die Microdata-Semantik bleibt dort dokumentiert.

## Microsyntax ↔ URLs

`25-urls.md`

URL-Syntax ist eine eigene Infrastruktur.

Ein URL-Attribut kann gleichzeitig eine HTML-Microsyntax und den WHATWG URL Standard verwenden.

Diese Ebenen dürfen nicht vermischt werden.

## Microsyntax ↔ Fetching

`26-fetching-resources.md`

Fetch-bezogene Attribute verwenden verschiedene Wertmodelle.

Das Microsyntax-Modell beschreibt den Attributwert.

Das Fetching-Modell beschreibt dessen anschließende Verarbeitung.

---

# Detailprüfung

## MICRO-001 – Common parser idioms

### WHATWG

§2.3.1

### Bedeutung

Gemeinsames Beschreibungsmuster für Parseralgorithmen.

### Status

Normativ als Bestandteil der Spezifikationsalgorithmen.

### Zweite-Ebene-Relevanz

Eigenständiges Unterkonzept von Common Microsyntaxes.

---

## MICRO-002 – Boolean Attributes

### WHATWG

§2.3.2

### Bedeutung

Anwesenheitsbasierte Boolean-Semantik.

### Konformität

Vorhandener Wert muss leer oder kanonisch case-insensitiv sein.

`true` und `false` sind keine generischen zulässigen Werte.

### Status

Normativ.

---

## MICRO-003 – Enumerated Attributes

### WHATWG

§2.3.3

### Bedeutung

Mapping von Attributwerten auf definierte Zustände.

### Zustandsparameter

- Missing Value Default
- Empty Value Default
- Invalid Value Default
- Keyword/State Mapping
- Canonical Keyword

### Status

Normativ.

---

## MICRO-004 – Signed integers

### WHATWG

§2.3.4.1

### Bedeutung

Ganzzahlen mit optionalem negativem Vorzeichen.

### Status

Normativ.

---

## MICRO-005 – Non-negative integers

### WHATWG

§2.3.4.2

### Bedeutung

Ganzzahlen ohne negative Werte.

### Status

Normativ.

---

## MICRO-006 – Floating-point numbers

### WHATWG

§2.3.4.3

### Bedeutung

HTML-definierte Syntax und Parsingregeln für Fließkommazahlen.

### Status

Normativ.

---

## MICRO-007 – Percentages and lengths

### WHATWG

§2.3.4.4

### Bedeutung

Numerische Werte mit Prozent- beziehungsweise relativer Einheit.

### Status

Normativ.

---

## MICRO-008 – Nonzero percentages and lengths

### WHATWG

§2.3.4.5

### Bedeutung

Nicht-null Prozent-/Längenwerte.

### Status

Normativ.

---

## MICRO-009 – Lists of floating-point numbers

### WHATWG

§2.3.4.6

### Bedeutung

Listen numerischer Fließkommawerte.

### Status

Normativ.

---

## MICRO-010 – Lists of dimensions

### WHATWG

§2.3.4.7

### Bedeutung

Listen von Dimensionswerten.

### Status

Normativ.

---

## MICRO-011 – Months

### WHATWG

§2.3.5.1

### Bedeutung

Jahr-Monat-Werte nach HTML-Datumssyntax.

### Status

Normativ.

---

## MICRO-012 – Dates

### WHATWG

§2.3.5.2

### Bedeutung

Proleptische Gregorianische Kalenderdaten.

### Status

Normativ.

---

## MICRO-013 – Yearless dates

### WHATWG

§2.3.5.3

### Bedeutung

Monat-Tag-Werte ohne Jahr.

### Status

Normativ.

---

## MICRO-014 – Times

### WHATWG

§2.3.5.4

### Bedeutung

Zeitwerte mit Stunde, Minute, Sekunde und optionalem Sekundenbruchteil.

### Status

Normativ.

---

## MICRO-015 – Local dates and times

### WHATWG

§2.3.5.5

### Bedeutung

Datum und Zeit ohne Zeitzone.

### Status

Normativ.

---

## MICRO-016 – Time zones

### WHATWG

§2.3.5.6

### Bedeutung

Zeit-Offset beziehungsweise UTC-Kennung.

### Status

Normativ.

---

## MICRO-017 – Global dates and times

### WHATWG

§2.3.5.7

### Bedeutung

Datum, Zeit und Zeitzonenoffset.

### Status

Normativ.

---

## MICRO-018 – Weeks

### WHATWG

§2.3.5.8

### Bedeutung

Week-Year und Week Number.

### Status

Normativ.

---

## MICRO-019 – Durations

### WHATWG

§2.3.5.9

### Bedeutung

Dauerwerte, die eine konkrete Anzahl von Sekunden repräsentieren.

### Status

Normativ.

---

## MICRO-020 – Vaguer moments in time

### WHATWG

§2.3.5.10

### Bedeutung

Allgemeinere Datum-/Zeitangabe mit optionalen Komponenten.

### Status

Normativ.

---

## MICRO-021 – Legacy colors

### WHATWG

§2.3.6

### Bedeutung

Historische HTML-Farbsyntax.

### Status

Obsoletes beziehungsweise Legacy-Verarbeitungskonzept.

### Abgrenzung

Nicht mit dem modernen CSS Color Model gleichsetzen.

---

## MICRO-022 – Space-separated tokens

### WHATWG

§2.3.7

### Bedeutung

Tokenmengen mit ASCII-Whitespace als Separator.

### Status

Normativ.

---

## MICRO-023 – Comma-separated tokens

### WHATWG

§2.3.8

### Bedeutung

Tokenmengen mit Komma als Separator.

### Status

Normativ.

---

## MICRO-024 – Hash-name references

### WHATWG

§2.3.9

### Bedeutung

Referenzsyntax für bestimmte Elementtypen.

### Status

Normativ.

---

## MICRO-025 – Media query lists

### WHATWG

§2.3.10

### Bedeutung

HTML-Integration der Media Query List Syntax.

### Status

Normative HTML-Integration einer extern definierten Syntax.

---

## MICRO-026 – Unique internal values

### WHATWG

§2.3.11

### Bedeutung

Eindeutige interne Werte, die nicht an Script exponiert werden.

### Status

Normatives internes Konzept.

---

# Status / V1

## WHATWG-Status

Die in dieser Datei dokumentierten Common Microsyntaxes sind Bestandteil des aktuellen WHATWG HTML Living Standard.

Die einzelnen Bereiche haben unterschiedliche fachliche Eigenschaften:

| Bereich | WHATWG-Status |
|---|---|
| Common parser idioms | normative Verarbeitungsdefinition |
| Boolean Attributes | normative Definition |
| Enumerated Attributes | normative Definition |
| Numbers | normative Syntax und Parsingregeln |
| Dates and times | normative Syntax und Parsingregeln |
| Legacy colors | obsolete/legacy normative Verarbeitung |
| Space-separated tokens | normative Syntax |
| Comma-separated tokens | normative Syntax |
| References | normative Syntax und Parsing |
| Media queries | normative HTML-Integration |
| Unique internal values | normatives internes Konzept |

## Browser-Kompatibilität

Browser-Kompatibilität ist kein Bestandteil des WHATWG-Status.

Diese Datei macht keine Aussagen darüber, ob ein bestimmter Browser ein Feature unterstützt.

## ZE-WebLab-V1

Die V1-Einstufung ist projektspezifisch.

Für diese Datei gilt:

**V1-Ebene: übergreifende HTML-Infrastruktur / gemeinsame Syntaxmodelle**

### Begründung

Common Microsyntaxes werden von zahlreichen HTML-Features wiederverwendet und sind deshalb nicht sinnvoll ausschließlich in einzelnen Elementreferenzen dokumentierbar.

---

# Erste-Ebene-Abdeckung

## Allgemeine Abdeckung

Die erste Rechercheebene verwendet zahlreiche Microsyntaxes indirekt.

Dort werden Attribute und Elemente jeweils in ihrem konkreten Kontext beschrieben.

Diese Datei dokumentiert dagegen die gemeinsame Infrastruktur.

### Beispiele

```text
Elementdefinition
    ↓
Attribut
    ↓
gemeinsames Wertmodell
    ↓
Microsyntax
```

### Boolean Attributes

Die erste Ebene verwendet Boolean Attributes unter anderem bei:

- `disabled`
- `checked`
- `required`
- `multiple`
- `autofocus`
- `inert`
- `itemscope`

Die allgemeine Boolean-Attribute-Regel wird erst hier als eigenständige Feature-Familie zentral dokumentiert.

### Enumerated Attributes

Die erste Ebene enthält zahlreiche enumerierte Attribute.

Beispiele:

- `type`
- `method`
- `target`
- `rel`
- `contenteditable`
- `hidden`
- `dir`
- `translate`
- `loading`

Die konkrete Zustandssemantik bleibt beim jeweiligen Feature.

Diese Datei dokumentiert die gemeinsame WHATWG-Mechanik.

### Numerische Werte

Numerische Microsyntaxes werden unter anderem bei:

- `tabindex`
- `start`
- `width`
- `height`
- Tabellenattributen
- Medienattributen

verwendet.

Die konkrete Zulässigkeit und der Wertebereich sind jeweils element- beziehungsweise attributspezifisch.

### Datum/Zeit

Datum-/Zeit-Microsyntaxes sind insbesondere für:

- `time`
- `datetime`
- Form Controls
- andere zeitbezogene HTML-Werte

relevant.

Die Element- und Formdefinitionen bleiben die konkrete normative Quelle für die jeweilige Verwendung.

### Token

Token-Microsyntaxes sind unter anderem relevant für:

- `rel`
- `class`
- `accesskey`
- Microdata
- verschiedene Listen- und Keywordmodelle.

Die konkrete Semantik wird nicht allein durch die allgemeine Token-Syntax bestimmt.

---

# Offene Punkte

## Repository-Bestandsprüfung

Die RAW-Datei:

`docs/html/27-common-microsyntaxes.md`

ist zum Zeitpunkt dieser Erstellung noch nicht Bestandteil des Repository-Bestands.

Sie ist daher eine neue Recherchedatei.

Die vorhandenen Dateien `25-urls.md` und `26-fetching-resources.md` wurden als aktuelle RAW-Dateien geprüft.

## Externe Spezifikationen

Für einzelne Microsyntaxes verweist HTML auf externe normative Standards.

Relevant sind insbesondere:

- WHATWG URL Standard für URL-Verarbeitung
- CSS Media Queries für Media Query Lists
- CSS Color für die resultierende Farbdarstellung
- ISO 8601 als Hintergrund beziehungsweise Referenz für bestimmte Datum-/Zeitformate

Die externen Spezifikationen ersetzen jedoch nicht die HTML-spezifischen Konformitäts- und Parsingregeln.

## Keine vollständige externe Spezifikationsreferenz

Diese Datei ist keine vollständige Dokumentation:

- des URL Standards,
- des CSS Media Queries Standards,
- des CSS Color Standards,
- von ISO 8601.

Dokumentiert wird ausschließlich die HTML-seitige Verwendung beziehungsweise Definition.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard**

Relevanter Bereich:

- §2.3 Common microsyntaxes
- §2.3.1 Common parser idioms
- §2.3.2 Boolean attributes
- §2.3.3 Keywords and enumerated attributes
- §2.3.4 Numbers
- §2.3.4.1 Signed integers
- §2.3.4.2 Non-negative integers
- §2.3.4.3 Floating-point numbers
- §2.3.4.4 Percentages and lengths
- §2.3.4.5 Nonzero percentages and lengths
- §2.3.4.6 Lists of floating-point numbers
- §2.3.4.7 Lists of dimensions
- §2.3.5 Dates and times
- §2.3.5.1 Months
- §2.3.5.2 Dates
- §2.3.5.3 Yearless dates
- §2.3.5.4 Times
- §2.3.5.5 Local dates and times
- §2.3.5.6 Time zones
- §2.3.5.7 Global dates and times
- §2.3.5.8 Weeks
- §2.3.5.9 Durations
- §2.3.5.10 Vaguer moments in time
- §2.3.6 Legacy colors
- §2.3.7 Space-separated tokens
- §2.3.8 Comma-separated tokens
- §2.3.9 References
- §2.3.10 Media queries
- §2.3.11 Unique internal values

**Geprüfter Stand:** 11. August 2026

## ZE-WebLab-Projektquellen

Relevante vorhandene Dateien:

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
- `docs/html/18-contexts.md`
- `docs/html/19-dom-interfaces-and-apis.md`
- `docs/html/20-sanitization.md`
- `docs/html/21-parsing.md`
- `docs/html/22-svg-mathml-integration.md`
- `docs/html/23-microdata.md`
- `docs/html/24-user-interaction.md`
- `docs/html/25-urls.md`
- `docs/html/26-fetching-resources.md`

## Fachliche Abgrenzung

Die folgende Trennung bleibt verbindlich:

```text
Element
    ↓
Attribut
    ↓
Microsyntax
    ↓
geparster Zustand / Wert
    ↓
Feature-spezifisches Processing Model
    ↓
DOM / API / User-Agent-Verarbeitung
```

Daraus folgt:

- Eine Microsyntax ist kein Element.
- Eine Microsyntax ist kein Attribut.
- Ein Attribut ist nicht automatisch eine eigene Microsyntax.
- Ein geparster Wert ist nicht automatisch ein DOM Interface.
- Ein Parsingergebnis ist nicht automatisch eine Accessibility-Aussage.
- Eine syntaktisch gültige Eingabe ist nicht automatisch sicher.
- Browser-Kompatibilität ist kein WHATWG-Status.

---

# Prüfstatus

| Prüfbereich | Status |
|---|---|
| §2.3 Common microsyntaxes | vollständig geprüft |
| §2.3.1 Common parser idioms | vollständig geprüft |
| §2.3.2 Boolean attributes | vollständig geprüft |
| §2.3.3 Enumerated attributes | vollständig geprüft |
| §2.3.4 Numbers | vollständig geprüft |
| §2.3.4.1 Signed integers | vollständig geprüft |
| §2.3.4.2 Non-negative integers | vollständig geprüft |
| §2.3.4.3 Floating-point numbers | vollständig geprüft |
| §2.3.4.4 Percentages and lengths | vollständig geprüft |
| §2.3.4.5 Nonzero percentages and lengths | vollständig geprüft |
| §2.3.4.6 Lists of floating-point numbers | vollständig geprüft |
| §2.3.4.7 Lists of dimensions | vollständig geprüft |
| §2.3.5 Dates and times | vollständig geprüft |
| §2.3.5.1 Months | vollständig geprüft |
| §2.3.5.2 Dates | vollständig geprüft |
| §2.3.5.3 Yearless dates | vollständig geprüft |
| §2.3.5.4 Times | vollständig geprüft |
| §2.3.5.5 Local dates and times | vollständig geprüft |
| §2.3.5.6 Time zones | vollständig geprüft |
| §2.3.5.7 Global dates and times | vollständig geprüft |
| §2.3.5.8 Weeks | vollständig geprüft |
| §2.3.5.9 Durations | vollständig geprüft |
| §2.3.5.10 Vaguer moments in time | vollständig geprüft |
| §2.3.6 Legacy colors | vollständig geprüft |
| §2.3.7 Space-separated tokens | vollständig geprüft |
| §2.3.8 Comma-separated tokens | vollständig geprüft |
| §2.3.9 References | vollständig geprüft |
| §2.3.10 Media queries | vollständig geprüft |
| §2.3.11 Unique internal values | vollständig geprüft |
| Erste-Ebene-Abgrenzung | geprüft |
| Global-Attributes-Abgrenzung | geprüft |
| URL-Abgrenzung | geprüft |
| Fetch-Abgrenzung | geprüft |
| DOM/API-Abgrenzung | geprüft |
| Parsing-Abgrenzung | geprüft |
| Sanitization-Abgrenzung | geprüft |
| Accessibility-Abgrenzung | geprüft |
| Browser-Kompatibilität | bewusst nicht Bestandteil |
| Repository-Zielpfad | geprüft |
| `27-common-microsyntaxes.md` als vorhandener Bestand | nicht vorhanden / neue Datei |