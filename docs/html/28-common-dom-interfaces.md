# ZE-WebLab – HTML-Referenz: Common DOM Interfaces

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab  
**Datei:** `docs/html/28-common-dom-interfaces.md`  
**Rechercheebene:** Zweite Rechercheebene – übergreifende HTML-Konzepte und Feature-Familien  
**Feature-Familie:** Common DOM Interfaces  
**Feature-Typ:** DOM Interface / IDL Processing Model / Reflection / Collection API  
**Normative Primärquelle:** WHATWG HTML Living Standard  
**Geprüfter WHATWG-Stand:** 11. August 2026  
**WHATWG-Hauptbereich:** §2.6 „Common DOM interfaces“  
**Prüfstatus:** vollständig recherchiert für §2.6 und die Unterabschnitte §2.6.1–§2.6.5  
**Browser-Kompatibilität:** nicht Bestandteil dieser Datei  
**V1-Status:** projektspezifisch und nicht mit dem WHATWG-Status gleichzusetzen

Diese Datei dokumentiert die von HTML gemeinsam definierten DOM-/IDL-Mechanismen des WHATWG-Bereichs §2.6.

Im Mittelpunkt stehen:

- Reflection zwischen Content Attributes und IDL Attributes
- Reflection über Web-IDL Extended Attributes
- typisierte Reflection-Regeln
- Collections
- `HTMLAllCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`
- `DOMStringList`
- die Beziehung dieser Mechanismen zu HTML-DOM-Interfaces

Diese Datei ist **keine vollständige Dokumentation des WHATWG DOM Standards** und auch keine erneute vollständige Dokumentation aller HTML-DOM-Interfaces.

---

## Quellenabgrenzung

### WHATWG HTML

Der WHATWG HTML Living Standard definiert in §2.6 gemeinsame DOM-/IDL-Mechanismen, die von zahlreichen HTML-Features wiederverwendet werden.

Der Bereich umfasst aktuell:

- §2.6.1 Reflecting content attributes in IDL attributes
- §2.6.2 Using `reflect` via IDL extended attributes
- §2.6.3 Using `reflect` in specifications
- §2.6.4 Collections
  - §2.6.4.1 `HTMLAllCollection`
  - §2.6.4.1.1 `[[Call]]`
  - §2.6.4.2 `HTMLFormControlsCollection`
  - §2.6.4.3 `HTMLOptionsCollection`
- §2.6.5 `DOMStringList`

### DOM Standard

Allgemeine DOM-Grundlagen bleiben dem WHATWG DOM Standard zugeordnet.

Dazu gehören insbesondere:

- `Node`
- `Element`
- `Document`
- `DocumentFragment`
- DOM Attributes
- DOM Trees
- Namespaces
- grundlegende DOM-Manipulation
- `HTMLCollection`
- `NodeList`
- Events
- Mutation Observer

Diese Konzepte werden hier nur insoweit behandelt, wie HTML §2.6 darauf aufbaut oder sie für die dokumentierten HTML-spezifischen Mechanismen benötigt.

### Web IDL

Die Web IDL-Syntax und die allgemeine Semantik von Web-IDL-Typen und Extended Attributes werden durch den WHATWG Web IDL Standard definiert.

Diese Datei dokumentiert ausschließlich die HTML-spezifische Verwendung innerhalb von §2.6.

---

## Abgrenzung zu `19-dom-interfaces-and-apis.md`

`19-dom-interfaces-and-apis.md` behandelt die übergreifende HTML-DOM-/API-Ebene.

Diese Datei behandelt dagegen die **spezifische gemeinsame Infrastruktur aus §2.6**.

Die Ebenen sind daher zu unterscheiden:

```text
HTML-Element
    │
    ├── Content Attribute
    │
    └── HTML-DOM-Interface
             │
             └── IDL Attribute
                       │
                       └── Reflection
```

Beispiel:

```html
<img src="image.png">
```

Das `src` Content Attribute ist Bestandteil des HTML-Markups.

Das zugehörige DOM-Interface kann eine IDL-Eigenschaft bereitstellen, deren Verhalten durch Reflection oder durch ein spezielles URL-Processing Model definiert wird.

Die Reflection-Regeln selbst sind ein gemeinsames Infrastrukturkonzept und deshalb kein eigenes HTML-Element.

---

## Abgrenzung zu `27-common-microsyntaxes.md`

`27-common-microsyntaxes.md` behandelt gemeinsame HTML-Syntax- und Parsingregeln wie:

- Boolean Attributes
- Enumerated Attributes
- Integer
- Non-negative Integer
- Floating-Point Numbers
- Datums-/Zeitwerte
- Tokenlisten
- Referenzen
- Media Query Lists

Diese Datei baut teilweise auf diesen Microsyntaxes auf.

Beispielsweise kann eine reflektierende IDL-Eigenschaft ein Content Attribute spiegeln, dessen Wert als:

- Boolean Attribute
- Enumerated Attribute
- Integer
- URL
- Tokenliste

definiert ist.

Damit gilt:

**Microsyntax ≠ Reflection**

Die Microsyntax beschreibt die Interpretation eines Attributwertes.

Reflection beschreibt die Beziehung zwischen Content Attribute und IDL Attribute.

---

# Einordnung

## Common DOM Interfaces als Infrastruktur

HTML verwendet zahlreiche DOM-Interfaces und IDL-Mitglieder.

Dabei müssen drei Ebenen unterschieden werden:

1. Content Attribute im HTML-Markup
2. IDL Attribute beziehungsweise Methoden im DOM
3. normative Processing Models, die die Beziehung zwischen beiden bestimmen

Beispiel:

```html
<input disabled>
```

und:

```js
input.disabled
```

Die HTML-Spezifikation definiert nicht lediglich zwei unabhängige Werte.

Sie definiert eine Beziehung zwischen:

- dem Content Attribute `disabled`
- dem IDL Attribute `disabled`
- dem Boolean-State
- den jeweiligen Getter-/Setter-Regeln

Diese Beziehung wird durch Reflection beziehungsweise spezielle Reflection-Regeln beschrieben.

---

# WHATWG-Struktur

## §2.6 Common DOM interfaces

Der aktuelle WHATWG-Bereich ist in folgende Unterabschnitte gegliedert:

### §2.6.1 Reflecting content attributes in IDL attributes

Behandelt:

- reflected targets
- reflected IDL attributes
- reflected content attribute names
- Getter
- Setter
- Entfernen von Content Attributes
- Reflection für unterschiedliche IDL-Typen
- Enumerated Attributes
- URLs
- Boolean Attributes
- Integer
- Non-negative Integer
- Floating-Point Numbers
- `DOMTokenList`
- Element-Referenzen
- Listen von Element-Referenzen

### §2.6.2 Using `reflect` via IDL extended attributes

Behandelt die Web-IDL Extended Attributes:

- `[Reflect]`
- `[ReflectSetter]`
- `[ReflectURL]`
- `[ReflectNonNegative]`
- `[ReflectPositive]`
- `[ReflectPositiveWithFallback]`

Diese Extended Attributes erlauben Spezifikationen, standardisierte Reflection-Semantik direkt an IDL-Mitgliedern zu deklarieren.

### §2.6.3 Using `reflect` in specifications

Dieser Unterabschnitt beschreibt, wie Reflection in Spezifikationen verwendet und formuliert wird.

Er stellt damit eine normative Spezifikationskonvention beziehungsweise gemeinsame Definitionsebene dar.

### §2.6.4 Collections

Behandelt die HTML-spezifische Collection-Infrastruktur.

Dazu gehören:

- `HTMLAllCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`

### §2.6.5 `DOMStringList`

Behandelt die `DOMStringList`-Schnittstelle.

---

# Inventar

| ID | Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Abdeckungsstatus | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|---|
| DOM-001 | Reflection | Processing Model / DOM Infrastructure | §2.6.1 | elementbezogen vielfach vorhanden | teilweise | eigenständig |
| DOM-002 | Reflected Target | DOM Infrastructure | §2.6.1 | nicht als gemeinsames Konzept | neu | eigenständig |
| DOM-003 | Reflected IDL Attribute | IDL Processing Model | §2.6.1 | teilweise über Elementdefinitionen | teilweise | eigenständig |
| DOM-004 | Reflected Content Attribute Name | IDL Processing Model | §2.6.1 | elementbezogen | teilweise | eigenständig |
| DOM-005 | DOMString Reflection | IDL Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-006 | Nullable DOMString Reflection | IDL Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-007 | URL Reflection | IDL / URL Integration | §2.6.1 | teilweise in URL-Datei und Elementdefinitionen | teilweise | eigenständig |
| DOM-008 | Boolean Reflection | IDL Processing Model | §2.6.1 | teilweise über Microsyntaxes | teilweise | eigenständig |
| DOM-009 | Integer Reflection | IDL Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-010 | Unsigned Integer Reflection | IDL Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-011 | Floating-Point Reflection | IDL Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-012 | `DOMTokenList` Reflection | DOM Interface / Reflection | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-013 | Element-reference Reflection | DOM Interface / Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-014 | Element-list Reflection | DOM Interface / Processing Model | §2.6.1 | teilweise | teilweise | eigenständig |
| DOM-015 | `[Reflect]` | Web IDL Integration | §2.6.2 | elementbezogen | teilweise | eigenständig |
| DOM-016 | `[ReflectSetter]` | Web IDL Integration | §2.6.2 | elementbezogen | teilweise | eigenständig |
| DOM-017 | `[ReflectURL]` | Web IDL / URL Integration | §2.6.2 | elementbezogen | teilweise | eigenständig |
| DOM-018 | `[ReflectNonNegative]` | Web IDL / Numeric Reflection | §2.6.2 | elementbezogen | teilweise | eigenständig |
| DOM-019 | `[ReflectPositive]` | Web IDL / Numeric Reflection | §2.6.2 | elementbezogen | teilweise | eigenständig |
| DOM-020 | `[ReflectPositiveWithFallback]` | Web IDL / Numeric Reflection | §2.6.2 | elementbezogen | teilweise | eigenständig |
| DOM-021 | Specification use of reflection | Normative Concept | §2.6.3 | nicht als eigenes Konzept | neu | eigenständig |
| DOM-022 | `HTMLAllCollection` | DOM Interface | §2.6.4.1 | elementbezogene DOM-Nutzung | teilweise | eigenständig |
| DOM-023 | `HTMLAllCollection.[[Call]]` | DOM Processing Model | §2.6.4.1.1 | nicht als gemeinsames Konzept | neu | eigenständig |
| DOM-024 | `HTMLFormControlsCollection` | DOM Interface | §2.6.4.2 | Form-Dokumentation vorhanden | teilweise | eigenständig |
| DOM-025 | `HTMLFormControlsCollection.namedItem()` | DOM API | §2.6.4.2 | elementbezogen | teilweise | eigenständig |
| DOM-026 | `HTMLOptionsCollection` | DOM Interface | §2.6.4.3 | Form-Dokumentation vorhanden | teilweise | eigenständig |
| DOM-027 | `HTMLOptionsCollection.length` | DOM API | §2.6.4.3 | elementbezogen | teilweise | eigenständig |
| DOM-028 | `HTMLOptionsCollection.add()` | DOM API | §2.6.4.3 | elementbezogen | teilweise | eigenständig |
| DOM-029 | `HTMLOptionsCollection.remove()` | DOM API | §2.6.4.3 | elementbezogen | teilweise | eigenständig |
| DOM-030 | `DOMStringList` | DOM Interface | §2.6.5 | teilweise über DOM-Nutzung | teilweise | eigenständig |

---

# Begriffsdefinitionen

## Content Attribute

Ein Content Attribute ist ein Attribut eines HTML-Elements im Markup-/DOM-Attributmodell.

Beispiel:

```html
<input disabled>
```

`disabled` ist hier ein Content Attribute.

---

## IDL Attribute

Ein IDL Attribute ist ein durch Web IDL beschriebenes Interface-Mitglied.

Beispiel:

```js
input.disabled
```

Das IDL Attribute ist nicht einfach dasselbe Objekt wie das Content Attribute.

Es kann jedoch durch Reflection mit diesem verbunden sein.

---

## Reflection

Reflection bezeichnet die standardisierte Beziehung zwischen einem Content Attribute und einem IDL Attribute.

Bei einfacher Reflection gilt vereinfacht:

```text
Content Attribute
       ↕
   IDL Attribute
```

Die genaue Richtung und Verarbeitung hängt vom Reflection-Typ ab.

---

## Reflected Target

Ein reflected target ist das Objekt, auf dessen Content-Attribute- oder internes Attributmodell sich eine reflektierende IDL-Eigenschaft bezieht.

Typischerweise ist dies ein Element.

HTML definiert auch Reflection für `ElementInternals`.

---

## Reflected Content Attribute Name

Der reflected content attribute name ist der Name des Content Attributes, das durch das IDL Attribute reflektiert wird.

Er ist typischerweise der lokale Name des HTML-Attributes.

---

## Canonical Keyword

Bei enumerierten Attributen kann ein Zustand ein kanonisches Keyword besitzen.

Wenn ein IDL Attribute auf bekannte Werte beschränkt ist, kann der Getter den kanonischen Keyword-Wert zurückgeben.

Damit muss der vom Getter zurückgegebene String nicht zwingend identisch mit der ursprünglich geschriebenen Schreibweise sein.

---

# Normative Regeln

## Grundprinzip der Reflection

Reflection ist keine pauschale Stringkopie.

Die konkrete Reflection hängt vom Typ des IDL Attributes und von der Definition des Content Attributes ab.

Beispielsweise unterscheiden sich:

- Boolean Reflection
- Enumerated Reflection
- URL Reflection
- Integer Reflection
- Floating-Point Reflection
- `DOMTokenList` Reflection
- Element Reference Reflection

---

# §2.6.1 Reflection

## Reflected Target

WHATWG definiert ein reflected target als:

- ein Element
- oder ein `ElementInternals`-Objekt

Das reflected target stellt die Grundlage für die Reflection-Algorithmen bereit.

Für ein Element werden insbesondere folgende Operationen definiert:

- get the element
- get the content attribute
- set the content attribute
- delete the content attribute

---

## Get the Element

Für ein Element als reflected target liefert die Operation:

```text
das Element selbst
```

Bei `ElementInternals` liefert sie das zugehörige target element.

---

## Get the Content Attribute

Für ein Element wird das Content Attribute anhand von:

- Namespace
- Local Name

ermittelt.

Existiert das Attribut nicht, wird `null` geliefert.

Existiert es, wird sein Attributwert zurückgegeben.

---

## Set the Content Attribute

Beim Setzen wird der entsprechende DOM-Attributmechanismus verwendet.

Konzeptionell:

```text
IDL Setter
    ↓
set content attribute
    ↓
DOM Attribute
```

Die konkrete DOM-Operation stammt aus dem DOM-Modell.

---

## Delete the Content Attribute

Beim Löschen wird das entsprechende Content Attribute entfernt.

Das ist insbesondere für:

- nullable IDL Attributes
- Boolean IDL Attributes
- bestimmte Reflection-Semantiken

relevant.

---

# DOMString Reflection

Für ein IDL Attribute vom Typ `DOMString` gelten grundsätzlich Reflection-Regeln.

Vereinfacht:

```text
Content Attribute vorhanden
        ↓
Content-Attributwert
        ↓
IDL Getter
```

Fehlt das Content Attribute, liefert der Getter bei gewöhnlicher `DOMString`-Reflection grundsätzlich den leeren String.

Der Setter schreibt den gegebenen Wert als Content Attribute.

---

## Enumerated Attribute und `DOMString`

Bei einem reflektierenden `DOMString`-IDL-Attribut kann die Reflection zusätzlich auf bekannte Zustände eines enumerierten Attributes beschränkt sein.

Wenn das IDL Attribute als:

```text
limited to only known values
```

definiert ist, berücksichtigt der Getter die Zustände des enumerierten Attributes.

Dabei kann der Getter:

- einen kanonischen Keyword-Wert
- oder den leeren String

zurückgeben.

Dadurch kann sich der Getter-Ausgabewert vom ursprünglichen Content-Attribut-String unterscheiden.

---

# Nullable DOMString Reflection

Bei einem IDL Attribute vom Typ:

```webidl
DOMString?
```

kann der Getter `null` liefern.

Die Reflection berücksichtigt:

- fehlendes Content Attribute
- enumerierte Zustände
- Zustände ohne zugeordnetes Keyword
- tatsächliche Attributwerte

Beim Setter gilt:

```text
null
 ↓
Content Attribute löschen
```

Ein Nicht-`null`-Wert wird als Content Attribute gesetzt.

---

# URL Reflection

Bestimmte IDL Attributes vom Typ `USVString` werden als URL behandelt.

Hier ist die Reflection nicht lediglich eine direkte Stringkopie.

Der Getter kann:

1. den Content-Attributwert lesen,
2. ihn als URL verarbeiten,
3. die URL relativ zur relevanten Document Base URL auflösen,
4. die URL serialisieren,
5. bei einem Fehler auf den ursprünglichen Wert zurückfallen.

Vereinfacht:

```text
Content Attribute
       ↓
URL Parsing
       ↓
Document Base URL
       ↓
URL Serialization
       ↓
IDL Getter
```

Damit steht URL Reflection in direkter Beziehung zu:

- `25-urls.md`
- URL Parsing
- Document Base URL
- URL Serialization

---

## URL Reflection und Fehler

Kann der Wert nicht erfolgreich als URL verarbeitet werden, wird nicht automatisch ein anderer semantischer Wert erfunden.

Die spezifikationsgemäße Fehlerbehandlung des jeweiligen Reflection-Modells ist maßgeblich.

---

# Boolean Reflection

Bei einem IDL Attribute vom Typ:

```webidl
boolean
```

gilt die Presence-Semantik.

Fehlt das Content Attribute:

```text
false
```

Ist das Content Attribute vorhanden:

```text
true
```

Der konkrete Stringwert des Attributes ist für den Boolean-Getter nicht maßgeblich.

Beispiel:

```html
<input disabled="false">
```

Das Content Attribute ist vorhanden.

Daher liefert:

```js
input.disabled
```

den Wert:

```text
true
```

Die Boolean-Microsyntax wird in `27-common-microsyntaxes.md` behandelt.

---

# Integer Reflection

HTML kann IDL Attributes definieren, die einen Integer aus einem Content Attribute reflektieren.

Die Reflection verwendet die HTML-Integer-Parsingregeln.

Dabei können unter anderem berücksichtigt werden:

- signed integers
- non-negative integers
- Wertebereiche des Web-IDL-Typs
- Default Values
- negative Werte
- ungültige Werte

Die Reflection ist deshalb nicht gleichbedeutend mit:

```js
Number(attributeValue)
```

---

## Nicht-negative Integer

Bei einer Reflection, die nur nicht-negative Werte zulässt, wird die entsprechende HTML-Microsyntax verwendet.

Das kann zu speziellen Getter-Fallbacks führen.

Beispielsweise kann ein IDL Attribute bei fehlendem oder ungültigem Wert einen definierten Default oder einen speziellen Fallback-Wert liefern.

---

## `long`

Bei `long`-IDL-Attributen wird ein gültiger Integer-Wert nur dann übernommen, wenn er innerhalb des gültigen `long`-Bereichs liegt.

Außerhalb dieses Bereichs greift die definierte Reflection-Fallbacklogik.

---

# Unsigned Integer Reflection

Für `unsigned long`-basierte Reflection existieren zusätzliche Optionen.

WHATWG unterscheidet insbesondere:

- nur positive Zahlen
- nur positive Zahlen mit Fallback
- Clamping auf einen Bereich
- Default Value

Damit kann das Getter-Verhalten wesentlich komplexer sein als eine reine Typkonvertierung.

---

## `[ReflectNonNegative]`

`[ReflectNonNegative]` ist eine HTML-spezifische Web-IDL Extended Attribute.

Es wird verwendet, um eine numerische Reflection auf nicht-negative Werte auszurichten.

Das Extended Attribute darf nur bei den dafür vorgesehenen IDL-Typen verwendet werden.

---

## `[ReflectPositive]`

`[ReflectPositive]` beschreibt Reflection für Werte, die positiv sein müssen.

Insbesondere kann das Getter-/Setter-Verhalten Werte unterhalb der erlaubten Untergrenze speziell behandeln.

---

## `[ReflectPositiveWithFallback]`

`[ReflectPositiveWithFallback]` erweitert dieses Modell um ein definiertes Fallback-Verhalten.

Es ist deshalb von `[ReflectPositive]` zu unterscheiden.

---

# Floating-Point Reflection

HTML kann IDL Attributes vom Typ:

```webidl
double
```

über Content Attributes reflektieren.

Dabei werden die HTML-Floating-Point-Parsingregeln verwendet.

Die Reflection kann zusätzlich auf positive Werte beschränkt sein.

---

## `NaN` und `Infinity`

Die Web-IDL-Semantik des Typs `double` ist zu berücksichtigen.

Insbesondere können `NaN` und unendliche Werte bei Setter-Verarbeitung zu Exceptions führen.

Die konkrete Verarbeitung ergibt sich aus dem Zusammenspiel von:

- HTML Reflection
- Web IDL
- Floating-Point Parsing

---

# `DOMTokenList` Reflection

Ein IDL Attribute vom Typ:

```webidl
DOMTokenList
```

kann ein Content Attribute reflektieren, dessen Wert aus Tokens besteht.

Der Getter liefert ein `DOMTokenList`-Objekt.

Dieses Objekt steht in Beziehung zum zugrunde liegenden Content Attribute.

Vereinfacht:

```text
Content Attribute
     ↓
ASCII-/Token-Verarbeitung
     ↓
DOMTokenList
```

Das bedeutet nicht, dass `DOMTokenList` selbst ein HTML-Element oder eine Content Category wäre.

---

# Element-Referenz-Reflection

HTML definiert Reflection für IDL Attributes, deren Werte Elemente referenzieren.

Dabei kann der IDL-Typ beispielsweise ein:

```webidl
Element?
```

oder ein Interface sein, das von `Element` erbt.

Die Reflection kann einen Elementverweis anhand des Wertes eines Content Attributes auflösen.

---

## Auflösung über `id`

Ein typisches Modell ist:

```text
Content Attribute
      ↓
ID-Wert
      ↓
Element im relevanten Root
      ↓
passendes Element
```

Das relevante Element muss unter anderem:

- im passenden Tree-/Root-Kontext liegen,
- die passende ID besitzen,
- den geforderten Interface-Typ implementieren.

---

## Explizit gesetztes Element

Die Reflection kann zusätzlich einen explizit gesetzten Elementverweis unterstützen.

Damit kann ein IDL Setter direkt ein Element zuweisen, anstatt ausschließlich anhand eines ID-Strings aufzulösen.

Beim Setzen auf `null` wird der explizite Verweis entfernt und das entsprechende Content Attribute gelöscht.

---

# Element-Listen-Reflection

HTML definiert auch Reflection für IDL Attributes, deren Typ eine Liste von Elementen beziehungsweise eine `FrozenArray` von Elementen sein kann.

Dabei können zwei Fälle unterschieden werden:

1. explizit gesetzte Elemente
2. Auflösung aus einer durch ASCII-Whitespace getrennten ID-Liste

---

## Auflösung einer ID-Liste

Vereinfacht:

```text
Content Attribute
       ↓
ASCII-Whitespace Split
       ↓
ID Tokens
       ↓
Element Resolution
       ↓
Element List
       ↓
FrozenArray
```

Die Suche berücksichtigt dabei den relevanten Tree-/Root-Kontext.

---

## Caching

Für bestimmte Element-Listen-Reflection definiert WHATWG zwischengespeicherte Ergebnisse.

Das dient unter anderem dazu, die Identität des zurückgegebenen `FrozenArray`-Objekts zu erhalten.

Die Reflection ist daher nicht zwingend mit einer einfachen Neuerzeugung eines Arrays bei jedem Getter-Aufruf gleichzusetzen.

---

# §2.6.2 Using `reflect` via IDL Extended Attributes

HTML definiert mehrere Web-IDL Extended Attributes für Reflection.

## `[Reflect]`

```webidl
[Reflect]
attribute DOMString foo;
```

bedeutet grundsätzlich, dass das IDL Attribute das gleichnamige Content Attribute reflektiert.

Wird kein Name angegeben, wird der IDL-Name nach den definierten Regeln als Content-Attributname verwendet.

---

## `[ReflectSetter]`

`[ReflectSetter]` definiert Reflection insbesondere für den Setter.

Es unterscheidet sich damit von `[Reflect]`, das die allgemeine Reflection-Semantik beschreibt.

---

## `[ReflectURL]`

`[ReflectURL]` ist für `USVString`-IDL-Attribute vorgesehen.

Es aktiviert URL-bezogene Reflection.

Der reflektierte Wert kann dabei relativ zur relevanten Document Base URL verarbeitet werden.

---

## `[ReflectNonNegative]`

`[ReflectNonNegative]` ist für numerische Reflection mit einer Nicht-Negativ-Beschränkung vorgesehen.

---

## `[ReflectPositive]`

`[ReflectPositive]` ist für numerische Reflection mit einer Positiv-Beschränkung vorgesehen.

---

## `[ReflectPositiveWithFallback]`

`[ReflectPositiveWithFallback]` beschreibt positive numerische Reflection mit einem zusätzlichen Fallback-Modell.

---

## Einschränkungen

Die genannten primären Reflection Extended Attributes:

- werden auf IDL Interface Members verwendet,
- sind auf Interface-Attribute bezogen,
- dürfen nicht beliebig kombiniert werden,
- folgen den jeweils in HTML definierten Typanforderungen.

Die allgemeine Definition der Extended-Attribute-Syntax gehört zu Web IDL.

---

# §2.6.3 Using `reflect` in specifications

Dieser Abschnitt ist anders einzuordnen als ein gewöhnliches DOM API.

Er beschreibt, wie Spezifikationen die gemeinsame Reflection-Infrastruktur verwenden.

Damit wird vermieden, dass jede einzelne HTML-Featuredefinition eigene, voneinander abweichende Getter-/Setter-Algorithmen für dieselbe Reflection-Semantik formuliert.

Die gemeinsame Reflection-Infrastruktur dient damit als:

- normative Abstraktion,
- Wiederverwendungsmechanismus,
- Konsistenzmechanismus.

---

## Normative Bedeutung

Wenn eine HTML-Definition beispielsweise ein IDL Attribute als reflektierend definiert, muss die zugehörige Reflection nach den gemeinsamen Regeln interpretiert werden.

Daraus folgt:

**Reflection ist Bestandteil der normativen DOM-/IDL-Semantik.**

Sie ist nicht lediglich eine Dokumentationskonvention.

---

# §2.6.4 Collections

HTML definiert mehrere spezialisierte Collection-Interfaces.

Diese sind nicht mit einer beliebigen JavaScript-Array-Struktur gleichzusetzen.

Zu den relevanten Interfaces gehören:

- `HTMLAllCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`

---

## Collection ist kein HTML-Element

Eine Collection ist:

- kein HTML-Element,
- keine Content Category,
- kein Content Model,
- kein Link Type,
- kein Custom Element.

Sie ist ein DOM-/API-Konzept.

---

# `HTMLAllCollection`

## Definition

`HTMLAllCollection` ist eine historische HTML-DOM-Schnittstelle.

Sie wird durch das spezielle `document.all`-Verhalten exponiert.

Sie ist deshalb nicht mit einer gewöhnlichen `HTMLCollection` gleichzusetzen.

---

## Historische Besonderheiten

`HTMLAllCollection` besitzt besondere Legacy-Semantik.

Dazu gehören unter anderem:

- spezielle Namenssuche,
- besondere `[[Call]]`-Semantik,
- Legacy-kompatibles Verhalten bei booleschen Kontexten,
- besondere Web-Kompatibilitätsregeln.

Diese Eigenschaften dürfen nicht als allgemeines Modell für moderne DOM-Collections interpretiert werden.

---

## `document.all`

`document.all` ist ein historisch bedingtes HTML-DOM-Feature.

Es ist kein HTML-Element.

Es liefert eine `HTMLAllCollection`.

Die Existenz dieses Interfaces ist daher als DOM-/Legacy-Feature zu dokumentieren.

---

# `HTMLAllCollection.[[Call]]`

## §2.6.4.1.1

`HTMLAllCollection` besitzt ein spezielles internes `[[Call]]`-Verhalten.

Dadurch kann das Objekt in einer aufrufbaren Form verwendet werden.

Historisch können dadurch Konstrukte wie:

```js
document.all("example")
```

Elemente anhand eines Namens beziehungsweise einer ID suchen.

Das ist kein gewöhnliches Muster für HTML-DOM-Collections.

---

## Legacy-Semantik

Die spezielle Call-Semantik von `HTMLAllCollection` ist eine Legacy-/Kompatibilitätsfunktion.

Sie darf nicht mit einer normalen JavaScript-Funktion gleichgesetzt werden.

Insbesondere ist die besondere Wahrheit-/Falschheitssemantik von `document.all` kein allgemeines Verhalten von:

- `HTMLCollection`
- `NodeList`
- DOM-Objekten
- HTML-DOM-Interfaces

---

# `HTMLFormControlsCollection`

## Definition

`HTMLFormControlsCollection` ist eine spezialisierte Collection für Form Controls.

Sie steht insbesondere mit:

```html
<form>
```

und dessen zugehörigen Form Controls in Beziehung.

Das Interface erweitert die Collection-Funktionalität um eine namensbezogene Suche.

---

## `namedItem()`

`HTMLFormControlsCollection` stellt `namedItem()` bereit.

Die Suche kann sich auf:

- `id`
- `name`

beziehen.

Die konkrete Auswahl und Rückgabe richtet sich nach den normativen Regeln der HTML-Spezifikation.

---

## `RadioNodeList`

Bei bestimmten namensbezogenen Suchvorgängen kann eine `RadioNodeList` zurückgegeben werden.

Damit kann eine Gruppe von Radio- beziehungsweise gleichnamigen Form Controls repräsentiert werden.

Dies ist ein DOM/API-Konzept und kein neues HTML-Element.

---

# `HTMLOptionsCollection`

## Definition

`HTMLOptionsCollection` ist eine spezialisierte Collection für die Optionen eines `select`-Elements.

Sie steht insbesondere mit:

- `option`
- `optgroup`
- `select`

in Beziehung.

---

## `length`

Die Collection besitzt eine `length`-Eigenschaft.

Diese repräsentiert die Anzahl der Optionen innerhalb der entsprechenden Collection.

Die Eigenschaft kann nicht lediglich als statische JavaScript-Array-Länge betrachtet werden, weil die Collection live mit dem DOM-Modell verbunden ist.

---

## `length` Setter

Das Setzen der `length`-Eigenschaft kann die Menge der Optionen verändern.

Die konkrete Verarbeitung ist in HTML definiert.

Damit kann:

```js
select.options.length = 0;
```

eine DOM-Veränderung bewirken.

---

## `add()`

`HTMLOptionsCollection` stellt eine `add()`-Methode bereit.

Sie dient dem Einfügen einer Option beziehungsweise eines `optgroup`-Elements in die Collection.

Die Methode besitzt definierte Einschränkungen hinsichtlich:

- Elementtyp
- Position
- Referenzknoten
- Hierarchie

---

## `remove()`

`HTMLOptionsCollection` stellt außerdem `remove()` bereit.

Die Methode kann eine Option anhand ihrer Position aus der Collection entfernen.

Das Verhalten steht in direktem Zusammenhang mit der zugrunde liegenden DOM-Struktur des `select`-Elements.

---

# §2.6.5 `DOMStringList`

## Definition

`DOMStringList` ist eine DOM-Schnittstelle zur Darstellung einer Liste von Strings.

Sie ist von anderen Collection-Typen zu unterscheiden.

Eine `DOMStringList` enthält keine DOM-Elemente.

---

## Eigenschaften

Das Interface stellt insbesondere Methoden beziehungsweise Eigenschaften bereit, um:

- die Länge der Liste zu bestimmen,
- auf Einträge anhand eines Index zuzugreifen,
- zu prüfen, ob ein String enthalten ist.

---

## `length`

`length` liefert die Anzahl der Einträge der Liste.

---

## `item()`

`item(index)` liefert den String an der entsprechenden Position, sofern ein entsprechender Eintrag vorhanden ist.

Bei einem ungültigen Index gilt die für das Interface definierte Rückgabesemantik.

---

## `contains()`

`contains(string)` prüft, ob der angegebene String in der Liste vorhanden ist.

Die Operation ist eine Listenabfrage und keine DOM-Elementsuche.

---

# Detailprüfung: Reflection-Typen

| Reflection-Typ | Content Attribute | IDL-Typ / Modell | Zentrale Verarbeitung |
|---|---|---|---|
| String Reflection | Textwert | `DOMString` | direkter Wert |
| Nullable String Reflection | Textwert | `DOMString?` | `null` bei fehlendem Wert |
| URL Reflection | URL-Attribut | `USVString` | URL Parsing und Serialization |
| Boolean Reflection | Boolean Attribute | `boolean` | Anwesenheit |
| Enumerated Reflection | Enumerated Attribute | `DOMString` / `DOMString?` | State-/Keyword-Mapping |
| Integer Reflection | Integer-Attribut | `long` | Integer Parsing |
| Non-negative Reflection | Non-negative Integer | `long` / unsigned Typen | Wertebereich |
| Positive Reflection | Positive Integer | numerischer IDL-Typ | Positivitätsprüfung |
| Floating-Point Reflection | Floating-Point Value | `double` | Floating-Point Parsing |
| Token Reflection | Token Attribute | `DOMTokenList` | Tokenmodell |
| Element Reflection | ID-Referenz | `Element?` bzw. Interface | Elementauflösung |
| Element-List Reflection | ID-Token-Liste | `FrozenArray<T>?` | Mehrfachauflösung |

---

# Attribute

## Reflection und Content Attributes

Die folgenden Attributeigenschaften sind voneinander zu unterscheiden:

```text
Content Attribute
    ↓
HTML Attributwert
    ↓
Reflection / Processing
    ↓
IDL Attribute
```

Nicht jedes Content Attribute besitzt automatisch ein reflektierendes IDL Attribute.

Ebenso kann ein IDL Attribute:

- ein Content Attribute reflektieren,
- einen verarbeiteten Zustand liefern,
- einen internen Slot exponieren,
- ein eigenes API-Modell besitzen.

---

# Content Categories

Content Categories sind für §2.6 nicht das zentrale Informationsmodell.

DOM Interfaces und Reflection besitzen keine eigene Content Category.

Beispiele:

- `HTMLInputElement` ist ein DOM Interface.
- `HTMLFormControlsCollection` ist ein DOM Interface.
- Reflection ist ein Processing Model.
- `DOMStringList` ist ein DOM Interface.

Keine dieser Kategorien ist eine Content Category.

---

# Context

Contexts sind für die Collection- und Reflection-Infrastruktur grundsätzlich keine eigenständige Dimension.

Die konkreten Elementkontexte bestimmen jedoch, welche Content Attributes und welche IDL Interfaces vorhanden sind.

Beispiel:

```text
<select>
   ↓
HTMLSelectElement
   ↓
options
   ↓
HTMLOptionsCollection
```

Der Kontext des `select`-Elements ist daher für die Entstehung des konkreten API-Zusammenhangs relevant.

---

# Content Model

Reflection, DOM Interfaces und Collections besitzen kein HTML Content Model.

Ein Content Model gehört zur Definition eines HTML-Elements.

Beispielsweise:

```text
select
    → HTML-Element
    → eigenes Content Model
    → HTMLSelectElement
    → HTMLOptionsCollection
```

Das Content Model des `select`-Elements darf daher nicht mit dem API-Modell von `HTMLOptionsCollection` vermischt werden.

---

# Processing Models

## Reflection Processing

Reflection ist ein normatives Processing Model.

Es bestimmt:

- wie der Getter arbeitet,
- wie der Setter arbeitet,
- wann Attribute gelöscht werden,
- wie Werte geparst werden,
- welche Defaults gelten,
- wie URLs behandelt werden,
- wie Elementreferenzen aufgelöst werden.

---

## Attribute Changes

Bei Elementen können Attributänderungen dazu führen, dass reflektierende IDL-Zustände neu bestimmt werden.

Das ist insbesondere relevant bei:

- Enumerated Attributes
- URL Reflection
- Element References
- Element Lists
- `DOMTokenList`

---

## Live Collections

Bestimmte HTML Collections sind live.

Das bedeutet, dass Änderungen am zugrunde liegenden DOM die Collection beeinflussen können.

Beispiel:

```text
DOM
 │
 ├── option
 ├── option
 └── option
       ↓
HTMLOptionsCollection
```

Wird ein `option`-Element eingefügt oder entfernt, kann sich die Collection entsprechend ändern.

---

# DOM Interfaces / APIs

## `HTMLAllCollection`

Legacy-Collection für `document.all`.

Besondere Eigenschaften:

- namensbezogene Suche
- spezielle Call-Semantik
- Legacy-Web-Kompatibilität

---

## `HTMLFormControlsCollection`

Spezialisierte Collection für Form Controls.

Besondere API:

- `namedItem()`

Zusammenhang:

```text
HTMLFormElement
      ↓
elements
      ↓
HTMLFormControlsCollection
```

---

## `HTMLOptionsCollection`

Spezialisierte Collection für `select`-Optionen.

Wichtige API-Mitglieder:

- `length`
- `add()`
- `remove()`
- `selectedIndex`-bezogene Zusammenhänge je nach übergeordnetem Interface

---

## `DOMStringList`

String-Liste mit:

- `length`
- `item()`
- `contains()`

Sie repräsentiert keine DOM-Elemente.

---

# Accessibility

§2.6 ist primär eine DOM-/IDL-Infrastrukturebene.

Die Reflection-Mechanismen selbst definieren keine eigenständige Accessibility-Semantik.

Accessibility-relevante Bedeutung entsteht durch die Features, die diese DOM-/IDL-Mechanismen verwenden.

Beispiele:

- Form Controls
- Fokus
- interaktive Elemente
- Sprache
- semantische Attribute

Die Accessibility-Bedeutung eines konkreten Attributes oder Elements ist daher weiterhin in der jeweiligen Element-/Featuredefinition beziehungsweise in den maßgeblichen Accessibility-Spezifikationen zu prüfen.

Es darf nicht aus der Existenz einer Reflection-API eine eigene Accessibility-Anforderung abgeleitet werden.

---

# Sanitization

Reflection ist nicht mit Sanitization gleichzusetzen.

Ein reflektierendes IDL Attribute beschreibt die Beziehung zwischen:

- Content Attribute
- DOM-/IDL-Wert

Es ist kein Sanitization-Mechanismus.

Beispiel:

```text
Attribute Reflection
        ≠
Sanitization
```

Die Sanitization-Klassifikation eines konkreten HTML-Elements oder Attributes wird in der jeweiligen Featuredefinition beziehungsweise in `20-sanitization.md` behandelt.

---

# Konformitätsregeln

## Reflection

Die Verwendung von Reflection muss der jeweiligen IDL-/HTML-Definition entsprechen.

Nicht jede beliebige JavaScript-Eigenschaft ist automatisch eine HTML-Reflection.

---

## Extended Attributes

Die Reflection Extended Attributes dürfen nur entsprechend ihrer WHATWG-/Web-IDL-Definition verwendet werden.

Insbesondere sind die zulässigen Kombinationen und IDL-Typen zu beachten.

---

## Legacy Interfaces

`HTMLAllCollection` und `document.all` besitzen historische Sonderregeln.

Diese dürfen nicht als allgemeine Empfehlung für neue APIs verstanden werden.

---

## Collections

Eine Collection darf nicht automatisch wie ein Array behandelt werden.

Insbesondere unterscheiden sich:

- Live Collections
- statische Arrays
- `NodeList`
- `HTMLCollection`
- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`
- `DOMStringList`

---

# Status / V1

## WHATWG-Status

| Feature | WHATWG-Status |
|---|---|
| Reflection | im HTML Living Standard definiert |
| Reflected Target | normative HTML-Infrastruktur |
| Reflected IDL Attribute | normative HTML-/IDL-Infrastruktur |
| URL Reflection | normative HTML-/IDL-Infrastruktur |
| Boolean Reflection | normative HTML-/IDL-Infrastruktur |
| Numeric Reflection | normative HTML-/IDL-Infrastruktur |
| Element Reflection | normative HTML-/DOM-Infrastruktur |
| `[Reflect]` | normative Web-IDL-/HTML-Integration |
| `[ReflectSetter]` | normative Web-IDL-/HTML-Integration |
| `[ReflectURL]` | normative Web-IDL-/HTML-Integration |
| `[ReflectNonNegative]` | normative Web-IDL-/HTML-Integration |
| `[ReflectPositive]` | normative Web-IDL-/HTML-Integration |
| `[ReflectPositiveWithFallback]` | normative Web-IDL-/HTML-Integration |
| `HTMLAllCollection` | im HTML Living Standard definiert |
| `HTMLFormControlsCollection` | im HTML Living Standard definiert |
| `HTMLOptionsCollection` | im HTML Living Standard definiert |
| `DOMStringList` | im HTML Living Standard definiert |

## Obsolete / Legacy

`HTMLAllCollection` und insbesondere `document.all` besitzen Legacy-Semantik.

Das bedeutet nicht, dass sie aus der WHATWG-Spezifikation verschwunden sind.

Für die Projektstatusbewertung ist daher zwischen:

- aktuell normativ definiert
- historisch/Legacy-Semantik
- obsolete API-Mitglieder

zu unterscheiden.

## V1

Die V1-Einstufung ist eine ZE-WebLab-Projektentscheidung.

Sie darf nicht mit dem WHATWG-Status gleichgesetzt werden.

---

# Querverweise

## Reflection ↔ Common Microsyntaxes

Reflection verwendet unter anderem:

- Boolean Attribute Parsing
- Enumerated Attribute States
- Integer Parsing
- Non-negative Integer Parsing
- Floating-Point Parsing
- Tokenlisten

Siehe:

`docs/html/27-common-microsyntaxes.md`

---

## Reflection ↔ URLs

URL Reflection verwendet:

- URL Parsing
- Document Base URL
- URL Serialization
- Character Encoding

Siehe:

`docs/html/25-urls.md`

---

## Reflection ↔ DOM Interfaces

Reflection wird innerhalb konkreter HTML-DOM-Interfaces verwendet.

Siehe:

`docs/html/19-dom-interfaces-and-apis.md`

---

## Collections ↔ Forms

`HTMLFormControlsCollection` steht insbesondere mit:

- `form`
- `fieldset`
- Form Controls
- `RadioNodeList`

in Beziehung.

---

## Collections ↔ `select`

`HTMLOptionsCollection` steht insbesondere mit:

- `select`
- `option`
- `optgroup`

in Beziehung.

---

## Reflection ↔ Global Attributes

Viele Global Attributes besitzen entsprechende IDL-Mitglieder.

Beispiele:

- `hidden`
- `inert`
- `autofocus`
- `contenteditable`
- `lang`
- `dir`
- `translate`
- `popover`

Die gemeinsame Reflection-Infrastruktur erklärt dabei nicht die vollständige Semantik des jeweiligen Attributes.

---

## Reflection ↔ Custom Elements

Custom Elements verwenden ebenfalls HTML-DOM-/IDL-Mechanismen.

Insbesondere sind relevant:

- HTMLElement
- reflected attributes
- custom element reactions
- `ElementInternals`

Reflection darf deshalb nicht ausschließlich auf native HTML-Elemente beschränkt betrachtet werden.

---

## Reflection ↔ HTML/SVG/MathML

Einige gemeinsame HTML-DOM-Mechanismen betreffen Interfaces beziehungsweise Elementtypen, die mit:

- HTML
- SVG
- MathML

zusammenarbeiten.

Dies gilt insbesondere für gemeinsame IDL-/Reflection-Infrastrukturen.

Die jeweilige Namespace-Semantik bleibt jedoch maßgeblich.

---

# Detailprüfung

## Reflection auf Content Attributes

Die normative Grundstruktur lässt sich vereinfacht so darstellen:

```text
Content Attribute
       │
       ├── lesen
       │
       ▼
Reflection Algorithm
       │
       ▼
IDL Getter
```

und:

```text
IDL Setter
    │
    ▼
Reflection Algorithm
    │
    ▼
Content Attribute
```

Bei komplexeren Reflection-Typen kommen zusätzliche Verarbeitungsschritte hinzu.

---

## URL Reflection

```text
Content Attribute
       │
       ▼
URL Parsing
       │
       ├── Erfolg → Serialisierung
       │
       └── Fehler → definierter Fallback
```

---

## Element Reflection

```text
Content Attribute
       │
       ▼
ID / Referenz
       │
       ▼
relevanter Tree / Root
       │
       ▼
passendes Element
```

---

## Element-Listen-Reflection

```text
Content Attribute
       │
       ▼
Tokenisierung
       │
       ▼
IDs
       │
       ▼
Elemente
       │
       ▼
FrozenArray
```

---

# Normative Sonderregeln

## Reflection ist typabhängig

Es gibt kein universelles:

```text
IDL = String(Content Attribute)
```

Stattdessen muss der jeweilige Reflection-Typ geprüft werden.

---

## Getter und Setter sind nicht zwingend symmetrisch

Ein Getter kann einen verarbeiteten Wert liefern, während ein Setter einen normalisierten Wert beziehungsweise einen neuen Content-Attributwert erzeugt.

Dies gilt insbesondere für:

- Enumerated Attributes
- URLs
- numerische Werte
- Boolean Attributes
- Elementreferenzen

---

## Reflection kann interne Zustände verwenden

Nicht jedes DOM-Feature liest unmittelbar den sichtbaren Content-Attributwert.

Beispiele außerhalb der einfachen Reflection sind unter anderem:

- interne Slots
- explizite Elementreferenzen
- gecachte Elementlisten

Damit ist das DOM-/IDL-Modell nicht vollständig durch die serialisierte HTML-Quelle beschreibbar.

---

# Offene Punkte

Zum geprüften Stand des §2.6 bestehen für den abgegrenzten Themenbereich keine fachlichen offenen Punkte.

Folgende Abgrenzungen bleiben bewusst bestehen:

1. Der vollständige WHATWG DOM Standard wird nicht in diese Datei integriert.
2. Die vollständige Web-IDL-Spezifikation wird nicht erneut dokumentiert.
3. Die vollständige Semantik einzelner HTML-Elemente bleibt in den Elementreferenzen.
4. Die gemeinsame Microsyntax-Infrastruktur bleibt in `27-common-microsyntaxes.md`.
5. URL-spezifische Infrastruktur bleibt in `25-urls.md`.
6. Allgemeine HTML-DOM-/API-Inventare bleiben in `19-dom-interfaces-and-apis.md`.
7. Browser-Kompatibilität wird nicht als WHATWG-Status geführt.

---

# Prüfstatus

| Bereich | Prüfstatus |
|---|---|
| §2.6 Common DOM interfaces | geprüft |
| §2.6.1 Reflection | geprüft |
| Reflected targets | geprüft |
| DOMString Reflection | geprüft |
| Nullable DOMString Reflection | geprüft |
| URL Reflection | geprüft |
| Boolean Reflection | geprüft |
| Integer Reflection | geprüft |
| Unsigned Integer Reflection | geprüft |
| Floating-Point Reflection | geprüft |
| `DOMTokenList` Reflection | geprüft |
| Element Reflection | geprüft |
| Element-List Reflection | geprüft |
| §2.6.2 Reflection Extended Attributes | geprüft |
| `[Reflect]` | geprüft |
| `[ReflectSetter]` | geprüft |
| `[ReflectURL]` | geprüft |
| `[ReflectNonNegative]` | geprüft |
| `[ReflectPositive]` | geprüft |
| `[ReflectPositiveWithFallback]` | geprüft |
| §2.6.3 Use of `reflect` | geprüft |
| §2.6.4 Collections | geprüft |
| `HTMLAllCollection` | geprüft |
| `HTMLAllCollection.[[Call]]` | geprüft |
| `HTMLFormControlsCollection` | geprüft |
| `HTMLOptionsCollection` | geprüft |
| §2.6.5 `DOMStringList` | geprüft |
| Querverweise zu bestehenden ZE-WebLab-Dateien | geprüft |
| Accessibility | abgegrenzt |
| Sanitization | abgegrenzt |
| Browser-Kompatibilität | bewusst nicht Bestandteil |

---

# Quellen / Referenzen

## Normative Primärquelle

- WHATWG HTML Living Standard
- §2.6 Common DOM interfaces
- §2.6.1 Reflecting content attributes in IDL attributes
- §2.6.2 Using `reflect` via IDL extended attributes
- §2.6.3 Using `reflect` in specifications
- §2.6.4 Collections
- §2.6.4.1 The `HTMLAllCollection` interface
- §2.6.4.1.1 `[[Call]]`
- §2.6.4.2 The `HTMLFormControlsCollection` interface
- §2.6.4.3 The `HTMLOptionsCollection` interface
- §2.6.5 The `DOMStringList` interface

## Weitere normative Quellen

- WHATWG DOM Standard
- WHATWG Web IDL Standard
- WHATWG URL Standard
- WHATWG Infra Standard

## ZE-WebLab-Projektquellen

- `docs/html/13-global-attributes.md`
- `docs/html/19-dom-interfaces-and-apis.md`
- `docs/html/25-urls.md`
- `docs/html/26-fetching-resources.md`
- `docs/html/27-common-microsyntaxes.md`

## Quellenabgrenzung

Die normative Definition der hier dokumentierten HTML-Mechanismen stammt aus dem WHATWG HTML Living Standard.

Die genannten ZE-WebLab-Dateien dienen ausschließlich zur Bestimmung des bestehenden Projektstands und zur Abgrenzung der zweiten Rechercheebene.

Browser-Support-Daten werden nicht zur Bestimmung des WHATWG-Status verwendet.