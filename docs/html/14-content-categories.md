# ZE-WebLab – HTML-Referenz: Content Categories

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab  
**Datei:** `docs/html/14-content-categories.md`  
**Rechercheebene:** Zweite Rechercheebene – übergreifende HTML-Konzepte  
**Feature-Typ:** Content Category / Feature Family  
**Primärquelle:** WHATWG HTML Living Standard  
**Geprüfter Spezifikationsstand:** aktueller Living-Standard-Stand der Recherche, August 2026  
**Status:** vollständig recherchiert für die in diesem Dokument abgegrenzte Content-Category-Systematik

Diese Datei dokumentiert die übergreifende Content-Category-Systematik des
aktuellen WHATWG HTML Living Standard.

Content Categories werden hier als eigenständige normative Konzepte
behandelt.

Sie sind insbesondere relevant für:

- Content Models
- Contexts
- Konformitätsanforderungen
- Elementbeziehungen
- Form-Control-Infrastruktur
- Custom Elements
- Querverweise zwischen HTML-Features

Content Categories sind **keine HTML-Elemente**.

### Normative Primärquelle

Die maßgeblichen Definitionen befinden sich im WHATWG-Bereich:

`3.2.5.2 Kinds of content`

mit den Unterabschnitten:

- `3.2.5.2.1 Metadata content`
- `3.2.5.2.2 Flow content`
- `3.2.5.2.3 Sectioning content`
- `3.2.5.2.4 Heading content`
- `3.2.5.2.5 Phrasing content`
- `3.2.5.2.6 Embedded content`
- `3.2.5.2.7 Interactive content`
- `3.2.5.2.8 Palpable content`
- `3.2.5.2.9 Script-supporting elements`

Ergänzend relevant sind:

- `3.2.5 Content models`
- `3.2.5.1 The "nothing" content model`
- `3.2.5.3 Transparent content models`
- `3.2.5.4 Paragraphs`
- `3.2.6 Global attributes`
- `3.2.9 Requirements related to ARIA and to platform accessibility APIs`
- `4.10.2 Categories` für Form-bezogene Kategorien
- `4.13 Custom elements` für form-associated custom elements
- die jeweiligen Elementdefinitionen

### Quellenabgrenzung

WHATWG beantwortet:

> Welche Content Categories definiert der HTML Living Standard und welche
> normative Bedeutung besitzen sie?

Das ZE-WebLab-Repository beantwortet:

> Welche dieser Konzepte wurden in der bestehenden ersten Rechercheebene
> bereits elementbezogen dokumentiert?

Diese beiden Aussagen werden getrennt behandelt.

Eine Kategorie gilt daher nicht automatisch als vollständig dokumentiert,
nur weil sie in einer oder mehreren Elementdateien erwähnt wird.

Ebenso bedeutet das Fehlen einer Kategorie in einer ersten-Ebene-Datei nicht,
dass die Kategorie im WHATWG-Standard nicht existiert.

### Browser-Kompatibilität

Browser-Kompatibilität ist nicht Bestandteil der WHATWG-Statusbewertung.

Diese Datei enthält deshalb keine Browser-Support-Bewertung.

---

## Einordnung

### Grundprinzip

WHATWG definiert Content Categories als Gruppen von Elementen mit ähnlichen
Eigenschaften.

Ein Element kann:

- keiner Kategorie,
- genau einer Kategorie,
- mehreren Kategorien

angehören.

Die Kategorien sind deshalb keine exklusive Klassifikation.

Ein einzelnes Element kann beispielsweise gleichzeitig:

- Flow Content,
- Phrasing Content,
- Embedded Content,
- Interactive Content
- und Palpable Content

sein.

Welche Kategorien gelten, kann außerdem von Attributen oder Zuständen des
Elements abhängen.

Beispiele:

- `a` ist nur mit vorhandenem `href` Interactive Content.
- `audio` ist mit vorhandenem `controls` Interactive Content.
- `input` ist abhängig vom `type`-State Interactive Content.
- `img` ist abhängig von `usemap` oder `controls` Interactive Content.
- `video` ist mit vorhandenem `controls` Interactive Content.
- `area` ist Flow Content, wenn es Nachkomme eines `map`-Elements ist.

### Content Category ist kein Content Model

Diese Begriffe sind strikt zu unterscheiden.

**Content Category**

klassifiziert Elemente.

Beispiel:

`p` ist Flow Content und Palpable Content.

**Content Model**

beschreibt, welche Inhalte ein Element enthalten darf.

Beispiel:

Das Content Model von `p` ist Phrasing Content.

**Context**

beschreibt, wo ein Element verwendet werden darf.

Beispiel:

`p` darf dort verwendet werden, wo Flow Content erwartet wird.

### Content Category ist kein DOM Interface

Beispiel:

- `article` ist ein HTML-Element.
- `article` gehört zu Flow Content und Sectioning Content.
- `HTMLArticleElement` ist kein eigenes WHATWG-DOM-Interface; das Element
  verwendet `HTMLElement`.

Die Kategoriezugehörigkeit ist daher unabhängig von der JavaScript-
Interface-Hierarchie.

### Content Category ist kein Parsing Model

Content Categories beschreiben die fachliche Klassifikation von Elementen.

Parsing-Regeln können diese Klassifikation verwenden oder auf sie
verweisen, sind aber selbst keine Content Categories.

---

# WHATWG-Struktur

## Allgemeine Kategorien

Der aktuelle WHATWG-Standard definiert folgende breite Kategorien:

1. Metadata content
2. Flow content
3. Sectioning content
4. Heading content
5. Phrasing content
6. Embedded content
7. Interactive content

Zusätzlich definiert WHATWG:

8. Palpable content
9. Script-supporting elements

Diese neun Kategorien gehören zum allgemeinen Content-Category-System.

WHATWG weist außerdem ausdrücklich darauf hin, dass weitere Kategorien an
anderen Stellen der Spezifikation für spezielle Zwecke definiert werden.

Insbesondere gilt dies für die Form-Control-Infrastruktur.

## Kategoriebeziehungen

Die allgemeinen Kategorien stehen in folgenden Beziehungen:

- Sectioning Content ist Flow Content.
- Heading Content ist Flow Content.
- Phrasing Content ist Flow Content.
- Embedded Content ist Phrasing Content und damit Flow Content.
- Interactive Content kann gleichzeitig Flow Content und/oder Phrasing
  Content sein.
- Metadata Content kann abhängig vom konkreten Element zusätzlich Flow
  Content sein.
- Metadata Content kann abhängig vom konkreten Element zusätzlich Phrasing
  Content sein.
- Embedded Content kann abhängig vom konkreten Element zusätzlich
  Interactive Content sein.

Diese Beziehungen stellen Klassifikationsbeziehungen dar.

Sie sind keine JavaScript-Vererbungsbeziehungen.

---

# Inventar

## Allgemeine Content Categories

| ID | Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| CC-001 | Metadata content | Content Category | §3.2.5.2.1 | vollständig elementbezogen verteilt, nicht als eigenständiges Kategoriensystem | eigenständig |
| CC-002 | Flow content | Content Category | §3.2.5.2.2 | umfangreich elementbezogen verteilt | eigenständig |
| CC-003 | Sectioning content | Content Category | §3.2.5.2.3 | in `03-sections.md` und weiteren Elementdateien erwähnt | eigenständig |
| CC-004 | Heading content | Content Category | §3.2.5.2.4 | in Elementdateien erwähnt | eigenständig |
| CC-005 | Phrasing content | Content Category | §3.2.5.2.5 | insbesondere in `05-text-level-semantics.md` und vielen Elementdateien | eigenständig |
| CC-006 | Embedded content | Content Category | §3.2.5.2.6 | umfangreich in `08-embedded-content.md` und weiteren Dateien | eigenständig |
| CC-007 | Interactive content | Content Category | §3.2.5.2.7 | insbesondere in `11-interactive-elements.md` und `10-forms.md` | eigenständig |
| CC-008 | Palpable content | Content Category | §3.2.5.2.8 | elementbezogen erwähnt | eigenständig |
| CC-009 | Script-supporting elements | Content Category | §3.2.5.2.9 | insbesondere in `12-scripting.md` erwähnt | eigenständig |

## Form-bezogene Kategorien

WHATWG definiert in §4.10.2 weitere Kategorien für Form-associated
elements.

| ID | Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| CC-010 | Form-associated elements | Feature Category | §4.10.2 | umfangreich in `10-forms.md` | eigenständig, Form-Infrastruktur |
| CC-011 | Listed elements | Feature Category | §4.10.2 | in `10-forms.md` | eigenständig, Form-Infrastruktur |
| CC-012 | Submittable elements | Feature Category | §4.10.2 | in `10-forms.md` | eigenständig, Form-Infrastruktur |
| CC-013 | Resettable elements | Feature Category | §4.10.2 | in `10-forms.md` | eigenständig, Form-Infrastruktur |
| CC-014 | Autocapitalize-and-autocorrect-inheriting elements | Feature Category | §4.10.2 | in `10-forms.md` | eigenständig, Form-Infrastruktur |
| CC-015 | Labelable elements | Feature Category | §4.10.2 | in `10-forms.md` | eigenständig, Form-Infrastruktur |

---

# Begriffsdefinitionen

## Metadata content

Metadata Content ist Inhalt, der:

- die Präsentation oder das Verhalten des übrigen Inhalts vorbereitet,
- Beziehungen des Dokuments zu anderen Dokumenten herstellt,
- oder sonstige Informationen außerhalb des eigentlichen Dokumentinhalts
  vermittelt.

Zu den HTML-Elementen dieser Kategorie gehören insbesondere:

- `base`
- `link`
- `meta`
- `noscript`
- `script`
- `style`
- `template`
- `title`

Die konkrete Kategoriezugehörigkeit einzelner Elemente ist anhand der
jeweiligen WHATWG-Elementdefinition zu prüfen.

### Namespace-Regel

WHATWG berücksichtigt außerdem Elemente anderer Namespaces, deren Semantik
primär auf Metadaten ausgerichtet ist.

Die Kategorie ist deshalb nicht auf HTML-Namespace-Elemente als solche
beschränkt.

### Abgrenzung zu `head`

Metadata Content ist nicht identisch mit:

> „Elemente, die im `head` stehen.“

Das `head`-Element besitzt ein eigenes Content Model und einen eigenen
Context.

Die Kategorieklassifikation und der zulässige Verwendungskontext sind
unterschiedliche normative Ebenen.

---

## Flow content

Flow Content ist die zentrale allgemeine Inhaltskategorie für Inhalte in
Dokumenten und Anwendungen.

WHATWG beschreibt die meisten Elemente, die im Body von Dokumenten und
Anwendungen verwendet werden, als Flow Content.

Die Kategorie umfasst unter anderem:

- `a`
- `abbr`
- `address`
- `area` unter den definierten Bedingungen
- `article`
- `aside`
- `audio`
- `b`
- `bdi`
- `bdo`
- `blockquote`
- `br`
- `button`
- `canvas`
- `cite`
- `code`
- `data`
- `datalist`
- `del`
- `details`
- `dfn`
- `dialog`
- `div`
- `dl`
- `em`
- `embed`
- `fieldset`
- `figure`
- `footer`
- `form`
- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `header`
- `hgroup`
- `hr`
- `i`
- `iframe`
- `img`
- `input`
- `ins`
- `kbd`
- `label`
- `link` unter den definierten Bedingungen
- `main`
- `map`
- `mark`
- MathML `math`
- `menu`
- `meta` unter den definierten Bedingungen
- `meter`
- `nav`
- `noscript`
- `object`
- `ol`
- `output`
- `p`
- `picture`
- `pre`
- `progress`
- `q`
- `ruby`
- `s`
- `samp`
- `script`
- `search`
- `section`
- `select`
- `slot`
- `small`
- `span`
- `strong`
- `sub`
- `sup`
- SVG `svg`
- `table`
- `template`
- `textarea`
- `time`
- `u`
- `ul`
- `var`
- `video`
- `wbr`
- autonome Custom Elements
- Text

Die vollständige aktuelle Elementzuordnung ist in den WHATWG-
Elementdefinitionen zu prüfen.

### Bedingte Kategoriezugehörigkeit

Flow Content ist nicht immer allein vom lokalen Elementnamen abhängig.

Beispiele:

- `area` ist Flow Content, wenn es Nachkomme eines `map`-Elements ist.
- `meta` kann bei vorhandenem `itemprop` Flow Content sein.
- `link` kann unter den für das Element definierten Bedingungen Flow Content
  sein.
- `main` besitzt eigene Bedingungen für die zulässige Verwendung.

### Bedeutung für Content Models

Flow Content wird in zahlreichen Content Models verwendet.

Beispiel:

`body` erlaubt Flow Content.

Dadurch wird die Kategorie zu einem zentralen Bindeglied zwischen
Elementdefinitionen und Content Models.

---

## Sectioning content

Sectioning Content bezeichnet Elemente, die einen eigenen Abschnitt der
Dokumentstruktur erzeugen.

WHATWG nennt:

- `article`
- `aside`
- `nav`
- `section`

### Normative Bedeutung

Sectioning Content ist insbesondere für die Definition des Geltungsbereichs
von `header` und `footer` relevant.

Die Kategorie ist nicht identisch mit:

- jedem Element, das visuell einen Abschnitt darstellt,
- `div`,
- einer CSS-Box,
- einem beliebigen Container.

`div` ist beispielsweise Flow Content, aber kein Sectioning Content.

### Beziehung zur Dokumentstruktur

Sectioning Content steht in engem Zusammenhang mit der Dokumentstruktur und
den Regeln für Überschriften.

Die Kategorie ist deshalb insbesondere mit folgenden Konzepten zu
verknüpfen:

- Heading Content
- `h1` bis `h6`
- `hgroup`
- Sectioning roots
- `header`
- `footer`

Diese Konzepte sind jedoch nicht untereinander synonym.

---

## Heading content

Heading Content ist die Kategorie für Inhalte, die als Überschrift einer
Section dienen.

WHATWG nennt:

- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `hgroup`, wenn die dafür definierten Bedingungen erfüllt sind

### `hgroup`

`hgroup` ist insbesondere deshalb relevant, weil seine Kategoriezugehörigkeit
von seinem Inhalt abhängt.

Ein `hgroup` mit einem geeigneten Heading-Nachkommen kann Heading Content
sein.

Es darf daher nicht pauschal allein anhand des Elementnamens als Heading
Content klassifiziert werden.

### Abgrenzung

Heading Content ist nicht identisch mit:

- sichtbarem Text in großer Schrift,
- CSS-Überschriften,
- ARIA-Heading-Rollen,
- jeder visuellen Überschrift.

Die Kategorie ist Bestandteil des HTML-Dokumentmodells.

---

## Phrasing content

Phrasing Content umfasst den Text des Dokuments sowie Elemente, die diesen
Text auf der Ebene einzelner Absätze bzw. Textsequenzen markieren.

Phrasing Content umfasst unter anderem:

- `a`
- `abbr`
- `area` unter den definierten Bedingungen
- `audio`
- `b`
- `bdi`
- `bdo`
- `br`
- `button`
- `canvas`
- `cite`
- `code`
- `data`
- `datalist`
- `del`
- `dfn`
- `em`
- `embed`
- `i`
- `iframe`
- `img`
- `input`
- `ins`
- `kbd`
- `label`
- `link` unter den definierten Bedingungen
- `map`
- `mark`
- MathML `math`
- `meta` unter den definierten Bedingungen
- `meter`
- `noscript`
- `object`
- `output`
- `picture`
- `progress`
- `q`
- `ruby`
- `samp`
- `script`
- `select`
- `selectedcontent` unter den definierten Bedingungen
- `slot`
- `small`
- `span`
- `strong`
- `sub`
- `sup`
- SVG `svg`
- `template`
- `textarea`
- `time`
- `u`
- `var`
- `video`
- `wbr`
- autonome Custom Elements
- Text

### Text als Content Category

Text ist im Zusammenhang mit den Content Models von besonderer Bedeutung.

Text Nodes können Phrasing Content darstellen.

Inter-element Whitespace wird für bestimmte Content-Model-Prüfungen
gesondert berücksichtigt.

### Beziehung zu Flow Content

Phrasing Content ist eine Untergruppe von Flow Content.

Die Beziehung lautet konzeptionell:

Phrasing Content → Flow Content

Dies ist keine DOM-Vererbung.

---

## Embedded content

Embedded Content umfasst Elemente, die:

- eine externe Ressource einbetten,
- eine andere Ressource als Bestandteil des Dokuments darstellen,
- oder Inhalte eines anderen Vokabulars integrieren.

WHATWG nennt:

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

### Namespace-Bezug

SVG und MathML sind für diese Kategorie besonders relevant.

Sie werden dadurch nicht zu HTML-Elementen.

Beispielsweise ist:

`svg`

ein SVG-Element.

Es kann aber im HTML-Content-Category-System als Embedded Content
klassifiziert werden.

Ebenso ist:

`math`

ein MathML-Element.

Die Kategoriezuordnung darf deshalb nicht mit der Namespace-Zugehörigkeit
verwechselt werden.

### Fallback Content

Einige Embedded-Content-Elemente besitzen Fallback Content.

Ob Fallback Content vorgesehen ist und welche Regeln gelten, wird durch die
jeweilige Elementdefinition bestimmt.

Die Kategorie Embedded Content selbst definiert kein einheitliches
Fallback-Verhalten für alle Elemente.

### Beziehung zu Phrasing Content

Embedded Content ist eine Form von Phrasing Content.

Damit ist Embedded Content zugleich Flow Content.

---

## Interactive content

Interactive Content ist Inhalt, der ausdrücklich für Benutzerinteraktion
vorgesehen ist.

WHATWG definiert die Kategorie insbesondere für:

- `a`, wenn `href` vorhanden ist
- `audio`, wenn `controls` vorhanden ist
- `button`
- `details`
- `embed`
- `iframe`
- `img`, wenn `usemap` oder `controls` vorhanden ist
- `input`, wenn `type` nicht im Hidden State ist
- `label`
- `select`
- `textarea`
- `video`, wenn `controls` vorhanden sind

### Attribut- und zustandsabhängige Kategorien

Interactive Content ist eine wichtige Kategorie, weil sie zeigt, dass
Content Categories dynamisch von der Elementkonfiguration abhängen können.

Beispiel:

`a` ohne `href` ist nicht aufgrund des Elementnamens automatisch
Interactive Content.

Dagegen ist:

`a href="/example"`

Interactive Content.

Ebenso:

`input type="hidden"`

ist nicht Interactive Content.

Andere `input`-States können Interactive Content sein.

### Keine Gleichsetzung mit Focusability

Interactive Content bedeutet nicht schlicht:

> „Das Element kann fokussiert werden.“

Focusability, Aktivierbarkeit, Tastaturbedienbarkeit und Interactive
Content sind getrennte normative Konzepte.

---

## Palpable content

Palpable Content beschreibt Inhalte, die ein Element als nicht leer
erscheinen lassen.

WHATWG nennt dabei insbesondere:

- nichtleeren Text,
- hörbaren Inhalt,
- sichtbaren Inhalt,
- interaktive Inhalte.

### Allgemeine Anforderung

Als allgemeine Regel gilt:

Elemente, deren Content Model Flow Content oder Phrasing Content erlaubt,
sollten mindestens einen Palpable-Content-Knoten enthalten, der nicht mit
`hidden` ausgeblendet ist.

Diese Regel ist ausdrücklich keine ausnahmslose harte Konformitätsregel.

WHATWG nennt legitime Fälle, in denen ein Element leer sein kann, etwa:

- Platzhalter, die später durch Script befüllt werden,
- Template-Inhalte,
- andere situationsabhängig legitime leere Strukturen.

### Palpable Content

Die Kategorie umfasst unter anderem:

- `a`
- `abbr`
- `address`
- `article`
- `aside`
- `b`
- `bdi`
- `bdo`
- `blockquote`
- `button`
- `canvas`
- `cite`
- `code`
- `data`
- `del`
- `details`
- `dfn`
- `div`
- `em`
- `embed`
- `fieldset`
- `figure`
- `footer`
- `form`
- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `header`
- `hgroup`
- `i`
- `iframe`
- `img`
- `ins`
- `kbd`
- `label`
- `main`
- `map`
- `mark`
- MathML `math`
- `meter`
- `nav`
- `object`
- `output`
- `p`
- `picture`
- `pre`
- `progress`
- `q`
- `ruby`
- `s`
- `samp`
- `search`
- `section`
- `select`
- `small`
- `span`
- `strong`
- `sub`
- `sup`
- SVG `svg`
- `table`
- `textarea`
- `time`
- `u`
- `var`
- `video`
- autonome Custom Elements
- nicht ausschließlich aus Inter-element Whitespace bestehender Text

Zusätzlich existieren bedingte Fälle.

### Bedingte Palpability

Die Palpable-Content-Zugehörigkeit ist bei einigen Features abhängig von
Attributen oder Inhalt.

Beispiele:

- `audio` ist Palpable Content, wenn `controls` vorhanden ist.
- `input` ist Palpable Content, wenn der `type`-State nicht Hidden ist.
- `dl` ist Palpable Content, wenn seine Kinder mindestens eine Name-Value-
  Gruppe enthalten.
- `menu` ist Palpable Content, wenn mindestens ein `li` enthalten ist.
- `ol` ist Palpable Content, wenn mindestens ein `li` enthalten ist.
- `ul` ist Palpable Content, wenn mindestens ein `li` enthalten ist.
- Text ist Palpable Content, sofern er nicht lediglich Inter-element
  Whitespace ist.

---

## Script-supporting elements

Script-supporting elements sind Elemente, die selbst nichts repräsentieren
und insbesondere nicht als eigener sichtbarer Inhalt dargestellt werden,
aber Scripts unterstützen.

WHATWG nennt:

- `script`
- `template`

### Abgrenzung

Script-supporting elements sind nicht gleichbedeutend mit:

- allen Elementen, die JavaScript manipulieren kann,
- allen Elementen mit DOM APIs,
- allen Elementen mit Event Handlern,
- allen Elementen, die Script auslösen können.

Die Kategorie ist eine spezifische Content-Model-Klassifikation.

---

# Form-spezifische Content Categories

Die Form-Infrastruktur verwendet zusätzliche Kategorien.

Diese Kategorien gehören nicht zur Liste der neun allgemeinen Kategorien,
sind aber Bestandteil der übergreifenden HTML-Klassifikation.

Die normative Quelle ist:

`§4.10.2 Categories`

---

## Form-associated elements

Form-associated elements sind Elemente, die einen `form owner` besitzen
können.

WHATWG nennt aktuell:

- `button`
- `fieldset`
- `input`
- `object`
- `output`
- `select`
- `textarea`
- `img`
- form-associated custom elements

### Besonderheit von `img`

`img` ist Form-associated Content, obwohl es kein gewöhnliches
Form-Control-Modell wie `input` besitzt.

Die Form-associated-Kategorie darf deshalb nicht mit:

- Form Control
- Submittable Element
- Listed Element
- Labelable Element

gleichgesetzt werden.

### Custom Elements

Form-associated custom elements können ebenfalls Form-associated Elements
sein.

Damit ist die Kategorie nicht auf native HTML-Elemente beschränkt.

---

## Listed elements

Listed Elements sind Form-associated Elements, die in den entsprechenden
Form-Collections gelistet werden.

WHATWG nennt:

- `button`
- `fieldset`
- `input`
- `object`
- `output`
- `select`
- `textarea`
- form-associated custom elements

Listed Elements sind insbesondere für die Form-DOM-API relevant.

Dazu gehören unter anderem Beziehungen zu:

- `HTMLFormElement.elements`
- `HTMLFieldSetElement.elements`

### Abgrenzung

Nicht jedes Form-associated Element ist Listed.

Insbesondere `img` ist Form-associated, aber nicht Listed.

---

## Submittable elements

Submittable Elements sind Elemente, die bei der Konstruktion der Entry List
einer Form berücksichtigt werden können.

WHATWG nennt:

- `button`
- `input`
- `select`
- `textarea`
- form-associated custom elements

### Normative Bedeutung

Submittable bedeutet nicht:

> „Das Element wird immer übertragen.“

Ob ein Element tatsächlich einen Eintrag zur Form Submission beiträgt,
hängt von seinem jeweiligen Zustand und den Regeln zur Konstruktion der
Entry List ab.

Beispielsweise können bestimmte Zustände eines Form Controls von der
Submission ausgeschlossen sein.

### Abgrenzung

Submittable ist nicht identisch mit:

- Listed
- Labelable
- Resettable
- Interactive Content

---

## Resettable elements

Resettable Elements sind Elemente, die von einem Reset einer Form betroffen
sein können.

WHATWG nennt:

- `input`
- `output`
- `select`
- `textarea`
- form-associated custom elements

### Normative Bedeutung

Ein Reset führt bei den entsprechenden Elementen die jeweils definierten
Reset-Schritte aus.

Die Kategorie beschreibt daher eine Beziehung zur Form-Reset-Verarbeitung.

Sie ist keine allgemeine Aussage darüber, dass ein Element einen
„Reset-Button“ besitzt.

---

## Autocapitalize-and-autocorrect-inheriting elements

Diese Kategorie beschreibt Elemente, die die Attribute:

- `autocapitalize`
- `autocorrect`

von ihrem Form Owner erben.

WHATWG nennt:

- `button`
- `fieldset`
- `input`
- `output`
- `select`
- `textarea`

### Bedeutung

Die Kategorie ist ausschließlich für die entsprechenden
Autocapitalize-/Autocorrect-Inheritance-Regeln relevant.

Sie ist keine allgemeine Kategorie für alle Form Controls.

---

## Labelable elements

Labelable Elements sind Elemente, die mit einem `label`-Element verbunden
werden können.

WHATWG nennt:

- `button`
- `input`, sofern der `type`-State nicht Hidden ist
- `meter`
- `output`
- `progress`
- `select`
- `textarea`
- form-associated custom elements

### Besonderheit von `input`

`input` ist nur dann Labelable, wenn es nicht im Hidden State ist.

Damit ist die Kategorie wiederum zustandsabhängig.

### `meter` und `progress`

`meter` und `progress` sind Labelable, obwohl sie nicht Form-associated
Elements sind.

Dies zeigt, dass:

> Labelable Elements

keine Untermenge von:

> Form-associated Elements

sein müssen.

---

# Beziehungen zwischen Kategorien

## Allgemeines Beziehungsmodell

Die Kategorien lassen sich vereinfacht wie folgt darstellen:

Metadata Content

→ kann je nach Element zusätzlich Flow Content sein

Flow Content

→ enthält Sectioning Content  
→ enthält Heading Content  
→ enthält Phrasing Content  
→ enthält Embedded Content

Phrasing Content

→ enthält Embedded Content

Interactive Content

→ kann zugleich Flow Content und/oder Phrasing Content sein

Palpable Content

→ überschneidet sich mit mehreren anderen Kategorien

Script-supporting elements

→ werden unabhängig von den allgemeinen Kategorien für bestimmte
Content Models klassifiziert

Diese Darstellung ist bewusst keine vollständige mathematische
Mengenbeschreibung.

Die konkrete Elementzugehörigkeit ist immer anhand der WHATWG-
Elementdefinition zu prüfen.

---

# Detailprüfung

## `a`

`a` ist:

- Flow Content
- Phrasing Content
- Interactive Content, wenn `href` vorhanden ist
- Palpable Content

Die Interactive-Content-Zugehörigkeit ist daher zustandsabhängig.

---

## `audio`

`audio` ist:

- Flow Content
- Phrasing Content
- Embedded Content
- Interactive Content, wenn `controls` vorhanden ist
- Palpable Content, wenn `controls` vorhanden ist

Damit bestehen mehrere attributabhängige Kategoriezuordnungen.

---

## `button`

`button` ist:

- Flow Content
- Phrasing Content
- Interactive Content
- Listed Element
- Labelable Element
- Submittable Element
- Form-associated Element
- Autocapitalize-and-autocorrect-inheriting Element
- Palpable Content

---

## `img`

`img` ist:

- Flow Content
- Phrasing Content
- Embedded Content
- Form-associated Element
- Palpable Content

`img` ist Interactive Content, wenn:

- `usemap`
- oder `controls`

unter den definierten Bedingungen vorhanden ist.

`img` ist dagegen nicht automatisch:

- Listed Element
- Submittable Element
- Resettable Element
- Labelable Element

---

## `input`

`input` ist:

- Flow Content
- Phrasing Content
- Form-associated Element
- Listed Element
- Labelable Element, wenn nicht Hidden State
- Submittable Element
- Resettable Element
- Autocapitalize-and-autocorrect-inheriting Element
- Interactive Content, wenn nicht Hidden State
- Palpable Content, wenn nicht Hidden State

Die genaue Kategoriezugehörigkeit hängt damit wesentlich vom `type`-
Zustand ab.

---

## `object`

`object` ist:

- Flow Content
- Phrasing Content
- Embedded Content
- Listed Element
- Form-associated Element
- Palpable Content

Interactive Content ist abhängig von den für das Element definierten
Bedingungen.

---

## `script`

`script` ist:

- Metadata Content unter den entsprechenden Bedingungen
- Flow Content unter den entsprechenden Bedingungen
- Phrasing Content unter den entsprechenden Bedingungen
- Script-supporting Element

Die genaue Einordnung hängt vom Verwendungskontext und den jeweiligen
Elementregeln ab.

---

## `template`

`template` ist Script-supporting Content.

Der Inhalt eines `template`-Elements wird nicht als normaler unmittelbarer
Dokumentinhalt in den aktiven DOM-Baum eingesetzt.

Das Template-Modell besitzt deshalb eigene Regeln und darf nicht einfach
mit einem gewöhnlichen Flow-Content-Container gleichgesetzt werden.

---

# Attribute

Content Categories können von Attributen und Zuständen abhängig sein.

Besonders relevant sind:

| Element | Attribut / Zustand | Kategorieauswirkung |
|---|---|---|
| `a` | `href` | Interactive Content |
| `audio` | `controls` | Interactive Content und Palpable Content |
| `img` | `usemap` / `controls` | Interactive Content |
| `input` | `type` | beeinflusst Interactive, Labelable und Palpable sowie Form-Kategorien |
| `video` | `controls` | Interactive Content |
| `meta` | `itemprop` | zusätzliche Flow-/Phrasing-Zuordnung |
| `link` | Verwendung / Attribute | Kategoriezuordnung kann kontextabhängig sein |
| `area` | Zugehörigkeit zu `map` | Flow-/Phrasing-Zuordnung |

### Grundregel

Ein Attribut darf nicht allein deshalb als Global Attribute oder
Content Attribute dokumentiert werden, weil es eine Kategoriezuordnung
beeinflusst.

Die Attributdefinition gehört zur entsprechenden Attribut- bzw.
Elementdefinition.

Die Kategorie dokumentiert lediglich die daraus resultierende
Klassifikation.

---

# Content Categories und Context

Content Categories und Context sind unterschiedliche Informationsdimensionen.

## Content Category

Beantwortet:

> Welche Klassifikation besitzt dieses Element?

## Context

Beantwortet:

> Unter welchen Bedingungen darf dieses Element verwendet werden?

Beispiel:

`p`:

- Kategorie: Flow Content, Palpable Content
- Context: dort, wo Flow Content erwartet wird
- Content Model: Phrasing Content

Damit bilden:

- Category
- Context
- Content Model

drei unterschiedliche normative Aussagen.

---

# Content Categories und Content Models

Content Models referenzieren Content Categories.

Beispiel:

Ein Content Model kann lauten:

`Flow content`

oder:

`Phrasing content`

Damit ist nicht gemeint, dass Flow Content selbst ein Element wäre.

Die Content-Model-Prüfung muss vielmehr feststellen, ob die tatsächlichen
Kindknoten zu der angegebenen Kategorie gehören.

### Beispiel

Wenn ein Element als Content Model:

`Phrasing content`

besitzt, können dort grundsätzlich nur Inhalte eingesetzt werden, die
unter die entsprechende Phrasing-Content-Klassifikation fallen, soweit
keine zusätzlichen Bedingungen gelten.

### Sonderfälle

Content Models können zusätzlich:

- konkrete Elemente,
- Text,
- Script-supporting elements,
- transparente Inhalte,
- Ausschlüsse,
- Zustandsbedingungen

verwenden.

Deshalb darf ein Content Model nicht ausschließlich als einfache
Kategorieprüfung implementiert werden.

---

# Transparent content models

Transparent ist keine Content Category.

Transparent ist eine Eigenschaft eines Content Models.

Ein transparentes Content Model übernimmt die zulässigen Inhalte aus dem
Kontext, in dem das betreffende Element verwendet wird, unter Anwendung
der zusätzlichen Regeln des Elements.

Beispiele für Elemente mit transparenten Content Models finden sich unter
anderem bei:

- `a`
- `del`
- `ins`
- `object`

Die konkrete Transparenzregel ist jeweils der Elementdefinition zu
entnehmen.

### Wichtige Abgrenzung

Nicht:

`transparent` = Content Category

sondern:

`transparent` = Content-Model-Eigenschaft.

---

# Processing Models

Content Categories sind keine Processing Models.

Sie können jedoch indirekt in Processing Rules verwendet werden.

Beispiele für Verbindungen:

- Form-associated categories → Form Owner Processing
- Submittable Elements → Form Submission
- Resettable Elements → Form Reset
- Interactive Content → Interaktionsbezogene normative Regeln
- Embedded Content → Ressourcen- und Fallback-Verarbeitung
- Script-supporting Elements → Script-/Template-Verarbeitung

Die jeweilige Processing Rule ist daher nicht Bestandteil der Kategorie-
Definition selbst.

---

# DOM Interfaces / APIs

Content Categories besitzen keine eigene DOM-Interface-Hierarchie.

Ein Element erhält sein DOM Interface entsprechend seiner
Elementdefinition.

Beispiele:

- `button` → `HTMLButtonElement`
- `input` → `HTMLInputElement`
- `img` → `HTMLImageElement`
- `audio` → `HTMLAudioElement`
- `video` → `HTMLVideoElement`
- `object` → `HTMLObjectElement`
- `form` → `HTMLFormElement`

Mehrere Elemente derselben Content Category können unterschiedliche
Interfaces besitzen.

Umgekehrt können mehrere Elemente dasselbe Interface oder eine gemeinsame
Interface-Basis verwenden.

### Form-Kategorien und APIs

Die Form-spezifischen Kategorien stehen in engem Zusammenhang mit APIs wie:

- `HTMLFormElement.elements`
- `HTMLFieldSetElement.elements`
- `HTMLFormElement.submit()`
- `HTMLFormElement.requestSubmit()`
- `HTMLFormElement.reset()`
- `HTMLInputElement`
- `HTMLSelectElement`
- `HTMLTextAreaElement`

Diese APIs sind jedoch keine Content Categories.

---

# Accessibility

## WHATWG-Abgrenzung

Content Categories sind keine Accessibility-Rollen.

Eine Kategorie wie:

`Interactive content`

ist nicht identisch mit einer ARIA-Rolle.

Ebenso ist:

`Heading content`

nicht automatisch identisch mit:

`role="heading"`

### Accessibility API

Die aktuelle HTML-Spezifikation besitzt einen eigenen Bereich für:

`3.2.9 Requirements related to ARIA and to platform accessibility APIs`

Die Accessibility-Semantik eines Elements muss daher von der
Content-Category-Klassifikation getrennt betrachtet werden.

### Palpable Content

Palpable Content besitzt eine offensichtliche Beziehung zur
Benutzbarkeit und Wahrnehmbarkeit von Inhalten.

Die Kategorie ist dennoch keine Accessibility-Rolle und keine
vollständige Accessibility-Anforderung.

### Externe Accessibility-Spezifikationen

ARIA- und Platform-Accessibility-API-Mappings können für eine vollständige
Accessibility-Referenz zusätzliche normative Quellen erfordern.

Solche Quellen werden nicht stillschweigend als Teil der WHATWG-
Content-Category-Definition behandelt.

---

# Sanitization

Content Categories sind nicht mit Sanitization-Kategorien gleichzusetzen.

Die Content-Category-Systematik beantwortet insbesondere:

- Welche Elemente gehören zu welcher Kategorie?
- Welche Inhalte sind in Content Models zulässig?
- Welche Elemente besitzen bestimmte gemeinsame Eigenschaften?

Sanitization beantwortet dagegen Sicherheits- bzw.
Bereinigungsfragen.

### Konsequenz für ZE-WebLab

Eine Aussage wie:

> „Flow Content ist sicher.“

ist keine normative WHATWG-Aussage.

Ebenso bedeutet eine Kategoriezugehörigkeit nicht automatisch:

- sichere HTML-Eingabe,
- sichere URL,
- sichere Script-Ausführung,
- sichere DOM-Injektion.

Sanitization wird deshalb als separate Informationsdimension behandelt.

---

# Konformitätsregeln

## Kategoriezugehörigkeit

Die Kategoriezugehörigkeit eines Elements ist entsprechend der jeweiligen
WHATWG-Definition zu bestimmen.

Wenn eine Kategorie von einem Attribut oder Zustand abhängt, darf das
Element nicht ohne Berücksichtigung dieses Zustands klassifiziert werden.

## Content Models

Eine Content-Model-Anforderung, die eine Content Category referenziert,
muss anhand der tatsächlichen Kategoriezugehörigkeit der Inhalte geprüft
werden.

## Palpable Content

Die Palpable-Content-Anforderung ist als allgemeine Autorregel zu
verstehen und besitzt ausdrücklich legitime Ausnahmen.

Sie darf nicht als universelles:

> „Jedes Flow-Element muss sichtbaren Inhalt besitzen.“

modelliert werden.

## Form Categories

Form-spezifische Kategorien sind für die jeweils definierten Form-
Processing-Modelle relevant.

Insbesondere dürfen:

- Form-associated
- Listed
- Submittable
- Resettable
- Labelable

nicht synonym verwendet werden.

---

# Querverweise

## Element ↔ Content Category

Jedes Element der ersten Rechercheebene kann eine oder mehrere
Kategoriezuordnungen besitzen.

Die Elementdateien dokumentieren die Zuordnung elementbezogen.

Diese Datei dokumentiert die Kategorie als übergreifendes Feature.

---

## Content Category ↔ Content Model

Content Models referenzieren Content Categories.

Dies ist eine der wichtigsten Beziehungen der zweiten Rechercheebene.

---

## Content Category ↔ Context

Context bestimmt den zulässigen Einsatzort.

Category und Context müssen getrennt dokumentiert werden.

---

## Content Category ↔ Attribute

Einige Kategoriezuordnungen hängen von Attributen oder Zuständen ab.

Wichtige Beispiele:

- `a` + `href`
- `audio` + `controls`
- `video` + `controls`
- `img` + `usemap`
- `input` + `type`
- `meta` + `itemprop`

---

## Content Category ↔ Form Infrastructure

Form-spezifische Kategorien stehen in Beziehung zu:

- Form Owner
- Form Controls
- Form Collections
- Form Submission
- Form Reset
- Label Association
- Autofill
- Autocapitalize
- Autocorrect

---

## Content Category ↔ Custom Elements

Autonome Custom Elements gehören zu Flow Content und können Palpable
Content sein.

Form-associated custom elements können zusätzlich in die Form-spezifischen
Kategorien fallen.

Damit ist die Content-Category-Systematik ausdrücklich nicht auf eine
endliche Liste nativer HTML-Elemente beschränkt.

---

## Content Category ↔ SVG

SVG-Elemente werden nicht zu HTML-Elementen, nur weil sie im HTML-Content-
Category-System als Embedded Content oder Phrasing Content berücksichtigt
werden.

`svg` ist ein SVG-Element und zugleich innerhalb der HTML-Kategorisierung
Embedded Content.

---

## Content Category ↔ MathML

Für MathML gilt entsprechend:

`math`

ist ein MathML-Element.

Es wird innerhalb des HTML-Content-Category-Systems als Embedded Content
und Phrasing Content berücksichtigt.

---

# Erste-Ebene-Abdeckung

## `01-document-element.md`

`html` besitzt keine Content Categories.

Die Datei dokumentiert diese Tatsache elementbezogen.

**Abdeckung:** teilweise für die übergreifende Kategorie-Systematik.

---

## `02-document-metadata.md`

Metadata Content wird umfangreich über die einzelnen Metadata-Elemente
behandelt.

Insbesondere werden dort Elemente wie:

- `head`
- `title`
- `base`
- `link`
- `meta`
- `style`

und weitere Metadaten-Features behandelt.

**Abdeckung:** umfangreich elementbezogen; keine vollständige eigenständige
Content-Category-Referenz.

---

## `03-sections.md`

Sectioning Content und Heading Content werden im Zusammenhang mit den
entsprechenden Struktur- und Heading-Elementen behandelt.

**Abdeckung:** umfangreich elementbezogen.

---

## `04-grouping-content.md`

Flow Content und Palpable Content werden über Gruppierungs- und
Container-Elemente behandelt.

**Abdeckung:** elementbezogen.

---

## `05-text-level-semantics.md`

Phrasing Content wird über die Text-Level-Elemente umfangreich berührt.

**Abdeckung:** umfangreich elementbezogen.

---

## `06-links.md`

`a` und `area` werden einschließlich ihrer Kategoriebeziehungen behandelt.

Die Datei enthält außerdem die übergreifende Link-Type-Systematik.

**Abdeckung:** Kategoriezuordnung vorhanden; Content Categories als
eigenständige Feature-Familie nicht vollständig behandelt.

---

## `07-edits.md`

`del` und `ins` besitzen Kategoriezuordnungen, die dort elementbezogen
behandelt werden.

**Abdeckung:** elementbezogen.

---

## `08-embedded-content.md`

Embedded Content wird dort besonders umfangreich behandelt.

Die Datei berücksichtigt:

- `audio`
- `canvas`
- `embed`
- `iframe`
- `img`
- `object`
- `picture`
- `svg`
- `video`
- MathML-Bezüge

**Abdeckung:** umfangreich elementbezogen; die übergreifende Kategorie-
Systematik wird durch diese Datei nicht vollständig ersetzt.

---

## `09-tabular-data.md`

Einzelne Tabellen-Elemente besitzen eigene Kategoriezuordnungen.

**Abdeckung:** elementbezogen.

---

## `10-forms.md`

Die Form-Datei behandelt die Form-Infrastruktur bereits auf Feature-Ebene.

Insbesondere werden Form-associated Elements und die zugehörigen
Form-Kategorien berücksichtigt.

**Abdeckung:** hoch.

Die vorliegende Datei dokumentiert diese Kategorien dennoch zusätzlich,
weil sie als Bestandteil der allgemeinen HTML-Kategorie-Systematik
eingeordnet und mit den anderen Kategorien verbunden werden müssen.

---

## `11-interactive-elements.md`

Interactive Content wird umfangreich über interaktive Elemente behandelt.

**Abdeckung:** umfangreich elementbezogen.

---

## `12-scripting.md`

Script-supporting elements werden im Zusammenhang mit Script- und
Template-Verarbeitung behandelt.

**Abdeckung:** umfangreich elementbezogen.

---

# Abdeckungsstatus

| Feature-Familie | Erste Ebene | Status für zweite Ebene |
|---|---|---|
| Metadata content | verteilt über `02-document-metadata.md` | eigenständige übergreifende Dokumentation erforderlich |
| Flow content | über zahlreiche Dateien verteilt | eigenständige übergreifende Dokumentation erforderlich |
| Sectioning content | `03-sections.md` | eigenständige Kategorieebene erforderlich |
| Heading content | `03-sections.md` und Elementdefinitionen | eigenständige Kategorieebene erforderlich |
| Phrasing content | `05-text-level-semantics.md` und viele weitere | eigenständige Kategorieebene erforderlich |
| Embedded content | `08-embedded-content.md` | Kategorieebene ergänzend erforderlich |
| Interactive content | `11-interactive-elements.md`, `10-forms.md` | eigenständige Kategorieebene erforderlich |
| Palpable content | verteilt | eigenständige Kategorieebene erforderlich |
| Script-supporting elements | `12-scripting.md` | eigenständige Kategorieebene erforderlich |
| Form-associated elements | `10-forms.md` | bereits stark abgedeckt; Querverbindung erforderlich |
| Listed elements | `10-forms.md` | bereits stark abgedeckt |
| Submittable elements | `10-forms.md` | bereits stark abgedeckt |
| Resettable elements | `10-forms.md` | bereits stark abgedeckt |
| Autocapitalize-and-autocorrect inheriting | `10-forms.md` | bereits stark abgedeckt |
| Labelable elements | `10-forms.md` | bereits stark abgedeckt |

### Schlussfolgerung

Die erste Ebene enthält zahlreiche Kategorieangaben.

Sie ersetzt jedoch keine eigenständige übergreifende Content-Category-
Referenz.

Die zweite Ebene ist deshalb fachlich gerechtfertigt.

---

# Status / V1

## WHATWG-Status

Content Categories sind:

**im aktuellen WHATWG HTML Living Standard definiert.**

Sie sind normative Bestandteile des HTML-Daten- und Content-Models.

### Keine Deprecated-Kategorie

Die in dieser Datei dokumentierten aktuellen Kategorien werden nicht
aufgrund bloßer historischer Existenz als deprecated oder obsolete
klassifiziert.

### Form-spezifische Kategorien

Die Form-Kategorien sind ebenfalls aktuelle Bestandteile des Standards.

---

## ZE-WebLab-V1

Die V1-Zuordnung ist von der WHATWG-Definition getrennt.

### V1-Einstufung

| Feature | WHATWG-Status | ZE-WebLab-V1 |
|---|---|---|
| Metadata content | definiert | Referenzbestandteil |
| Flow content | definiert | Referenzbestandteil |
| Sectioning content | definiert | Referenzbestandteil |
| Heading content | definiert | Referenzbestandteil |
| Phrasing content | definiert | Referenzbestandteil |
| Embedded content | definiert | Referenzbestandteil |
| Interactive content | definiert | Referenzbestandteil |
| Palpable content | definiert | Referenzbestandteil |
| Script-supporting elements | definiert | Referenzbestandteil |
| Form-associated elements | definiert | Referenzbestandteil |
| Listed elements | definiert | Referenzbestandteil |
| Submittable elements | definiert | Referenzbestandteil |
| Resettable elements | definiert | Referenzbestandteil |
| Autocapitalize-and-autocorrect-inheriting elements | definiert | Referenzbestandteil |
| Labelable elements | definiert | Referenzbestandteil |

Die V1-Einstufung bedeutet nicht:

> WHATWG hat einen V1-Status definiert.

V1 ist eine interne ZE-WebLab-Projektebene.

---

# Offene Punkte

## 1. Vollständige elementweise Matrix

Die vollständige Zuordnung jedes einzelnen aktuellen HTML-, SVG- und
MathML-relevanten Elements zu sämtlichen Content Categories sollte bei
Bedarf zusätzlich als maschinenlesbare bzw. tabellarische
Cross-Reference-Ebene gepflegt werden.

Diese Datei dokumentiert die Feature-Familien und die normativ relevanten
Klassifikationsregeln; sie ist nicht als Ersatz für jede einzelne
Elementdatei gedacht.

**Status:** kein offener WHATWG-Punkt; mögliche spätere
Dokumentationsausweitung.

## 2. Form-associated custom elements

Die Einordnung form-associated custom elements ist mit der Custom-Elements-
und Form-Infrastruktur verknüpft.

Die vollständige normative Behandlung gehört deshalb zusätzlich in die
Custom-Elements-/Form-Feature-Familien.

**Status:** Querverweis erforderlich; kein ungeklärter WHATWG-Punkt.

## 3. Accessibility-Mappings

Content Categories allein liefern keine vollständige Accessibility-
Semantik.

Für detaillierte Rollen- und Platform-Accessibility-Mappings sind die
entsprechenden Accessibility-Regelwerke separat zu recherchieren.

**Status:** bewusst getrennte Rechercheebene.

## 4. Sanitization

Content Categories liefern keine vollständige Sanitization-Matrix.

Sanitization-Regeln müssen deshalb separat recherchiert und dokumentiert
werden.

**Status:** bewusst getrennte Rechercheebene.

## 5. Browser-Support

Browser-Support wurde nicht als Teil des WHATWG-Status bewertet.

Eine Browser-Kompatibilitätsmatrix gehört in eine separate Rechercheebene.

**Status:** bewusst ausgeschlossen.

---

# Quellen / Referenzen

## Primärquelle

WHATWG HTML Living Standard:

`https://html.spec.whatwg.org/multipage/`

### Relevante normative Bereiche

- `3.2.5 Content models`
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
- `3.2.5.3 Transparent content models`
- `3.2.5.4 Paragraphs`
- `3.2.6 Global attributes`
- `3.2.9 Requirements related to ARIA and to platform accessibility APIs`
- `4.10.2 Categories`
- `4.13 Custom elements`

## ZE-WebLab-Projektquelle

Öffentliches Repository:

`https://github.com/z-evolutions/ze-weblab`

### Geprüfte erste-Ebene-Dateien

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

## Quellenrollen

**WHATWG HTML Living Standard**

Normative Primärquelle für:

- Definitionen
- Kategoriezugehörigkeit
- Content Models
- Contexts
- Konformitätsanforderungen
- normative Sonderregeln
- DOM-/API-Beziehungen

**ZE-WebLab GitHub Repository**

Projektbestandsquelle für:

- bereits dokumentierte erste Rechercheebene
- vorhandene elementbezogene Kategorieangaben
- vorhandene Querverweise
- Abgrenzung zwischen erster und zweiter Rechercheebene

## Recherchegrundsatz

Die Aussage:

> „In der ersten Ebene erwähnt“

ist nicht gleichbedeutend mit:

> „Als übergreifende Feature-Familie vollständig dokumentiert“.

Die vorliegende Datei schließt diese Lücke für die Content-Category-
Systematik, ohne die zwölf Elementdateien als zweite Ebene zu duplizieren.