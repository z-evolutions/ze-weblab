# ZE-WebLab – HTML-Referenz: Sections

## Arbeitsstand

- Themenblock: **03 – Sections**
- WHATWG-Hauptabschnitt: **§4.3 Sections**
- Bearbeitete HTML-Elemente:
  - `body`
  - `article`
  - `section`
  - `nav`
  - `aside`
  - `h1`
  - `h2`
  - `h3`
  - `h4`
  - `h5`
  - `h6`
  - `hgroup`
  - `header`
  - `footer`
  - `address`
- Zusätzlich geprüfte WHATWG-Konzeptabschnitte:
  - §4.3.11 Headings and outlines
  - §4.3.11.1 Heading levels & offsets
  - §4.3.11.2 Sample outlines
  - §4.3.11.3 Exposing outlines to users
  - §4.3.12 Usage summary
  - §4.3.12.1 Article or section?
- Recherchebasis: aktuelle WHATWG HTML Living Standard.
- Arbeitsziel: fachlich belastbare Referenzierung der Elementdefinitionen und der zugehörigen normativen Sectioning-/Heading-Konzepte.
- Browser-Kompatibilität wird nicht als WHATWG-Status geführt.
- Die in der WHATWG-Seite eingeblendeten MDN-Supportdaten werden deshalb nicht als Bestandteil des Statusmodells übernommen.

## Quellenstand

Primärquelle:

- WHATWG HTML Living Standard
- Abschnitt: `4.3 Sections`
- URL: https://html.spec.whatwg.org/multipage/sections.html
- Zum Recherchezeitpunkt angezeigter Stand: **Living Standard — Last Updated 11 August 2026**

Die WHATWG-Seite umfasst unter §4.3 die zehn Elementdefinitionen bzw. Elementfamilien und anschließend die eigenständigen Konzepte zu Überschriften, Outlines und zur Nutzung von `article` bzw. `section`.

Die Elementinventarliste und die Konzeptfamilien werden in dieser Datei bewusst getrennt behandelt.

---

# WHATWG-Struktur

## §4.3 Sections

Der aktuelle WHATWG-Abschnitt ist strukturiert als:

1. §4.3.1 The `body` element
2. §4.3.2 The `article` element
3. §4.3.3 The `section` element
4. §4.3.4 The `nav` element
5. §4.3.5 The `aside` element
6. §4.3.6 The `h1`, `h2`, `h3`, `h4`, `h5`, and `h6` elements
7. §4.3.7 The `hgroup` element
8. §4.3.8 The `header` element
9. §4.3.9 The `footer` element
10. §4.3.10 The `address` element
11. §4.3.11 Headings and outlines
12. §4.3.11.1 Heading levels & offsets
13. §4.3.11.2 Sample outlines
14. §4.3.11.3 Exposing outlines to users
15. §4.3.12 Usage summary
16. §4.3.12.1 Article or section?

Die Punkte ab §4.3.11 sind keine zusätzlichen HTML-Elemente.

Sie werden daher in ZE-WebLab als Konzept-/Querverweisfamilien und nicht als zusätzliche Elementinventareinträge geführt.

---

# Inventar

| Feature | WHATWG-Abschnitt | Feature-Typ | Content Categories | Context | Content Model | Tag Omission | Content Attributes | DOM Interface | Sanitization | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| `body` | §4.3.1 | HTML-Element | keine | Als zweites Element in `html` | Flow content | Start- und Endtag unter bestimmten Bedingungen auslassbar | Global Attributes + Window-reflecting Event Handler Content Attributes | `HTMLBodyElement` | Default | Im WHATWG-Standard definiert |
| `article` | §4.3.2 | HTML-Element | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `section` | §4.3.3 | HTML-Element | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `nav` | §4.3.4 | HTML-Element | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `aside` | §4.3.5 | HTML-Element | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `h1`–`h6` | §4.3.6 | HTML-Elementfamilie | Flow, Heading, Palpable | Als Kind von `hgroup` oder wo Heading Content erwartet wird | Phrasing content | keine Auslassung | Global Attributes | `HTMLHeadingElement` | Default | Im WHATWG-Standard definiert |
| `hgroup` | §4.3.7 | HTML-Element | Flow, Heading, Palpable | Wo Heading Content erwartet wird | Struktur aus `p`-Elementen, anschließend einem `h1`–`h6`, anschließend optionalen `p`-Elementen und ggf. Script-supporting Elements | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `header` | §4.3.8 | HTML-Element | Flow, Palpable | Wo Flow Content erwartet wird | Flow content ohne `header`-/`footer`-Nachfahren | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `footer` | §4.3.9 | HTML-Element | Flow, Palpable | Wo Flow Content erwartet wird | Flow content ohne `header`-/`footer`-Nachfahren | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |
| `address` | §4.3.10 | HTML-Element | Flow, Palpable | Wo Flow Content erwartet wird | Flow content ohne Heading Content, Sectioning Content, `header`, `footer` oder `address` als Nachfahren | keine Auslassung | Global Attributes | `HTMLElement` | Default | Im WHATWG-Standard definiert |

---

# Detailprüfung: `body`

## WHATWG-Definition

Das `body`-Element repräsentiert den Inhalt des Dokuments.

In konformen Dokumenten gibt es nur ein `body`-Element.

Das DOM stellt über `document.body` einen direkten Zugriff auf das `body`-Element bereit.

## Content Categories

WHATWG weist für `body` keine Content Category aus.

Damit ist `body` insbesondere nicht als Sectioning Content, Heading Content oder Palpable Content klassifiziert.

## Context

Das `body`-Element kann als zweites Element eines `html`-Elements verwendet werden.

Die konkrete Dokumentstruktur ist damit an die Definition des Document Element und des `html`-Elements gekoppelt.

## Content Model

Das Content Model ist:

- Flow content.

Damit kann der Dokumentkörper grundsätzlich Flow Content aufnehmen.

## Tag Omission

Für `body` gelten besondere Regeln zur Auslassung.

### Starttag

Der Starttag kann ausgelassen werden, wenn:

- das Element leer ist, oder
- das erste Element innerhalb des `body` weder ASCII-Whitespace noch ein Kommentar ist,

wobei die Auslassung nicht greift, wenn das erste Element innerhalb von `body` eines der folgenden Elemente ist:

- `meta`
- `noscript`
- `link`
- `script`
- `style`
- `template`

### Endtag

Der Endtag kann ausgelassen werden, wenn das `body`-Element nicht unmittelbar von einem Kommentar gefolgt wird.

Diese Regeln gelten für die HTML-Syntax (`text/html`).

## Content Attributes

Neben den Global Attributes besitzt `body` die für das Element relevanten Window-reflecting Event Handler Content Attributes.

WHATWG führt unter anderem folgende Event Handler für `body` auf:

- `onafterprint`
- `onbeforeprint`
- `onbeforeunload`
- `onhashchange`
- `onlanguagechange`
- `onmessage`
- `onmessageerror`
- `onoffline`
- `ononline`
- `onpageswap`
- `onpagehide`
- `onpagereveal`
- `onpageshow`
- `onpopstate`
- `onrejectionhandled`
- `onstorage`
- `onunhandledrejection`
- `onunload`

Diese Event Handler sind nicht als eigenständige HTML-Elemente zu inventarisieren.

## Besondere Event-Handler-Regel

Das `body`-Element exponiert bestimmte Event Handler des `Window`-Objekts.

Die entsprechenden Event Handler werden auf `body` gespiegelt.

Für bestimmte Ereignisse ersetzt die Window-reflecting Body-Element-Event-Handler-Menge die generischen Event Handler mit gleichnamigen Event Handlern.

Dies ist eine spezielle Beziehung zwischen `body`, `Window` und dem HTML-Event-Handler-Modell.

## Accessibility

WHATWG verweist für Accessibility auf getrennte Accessibility Considerations für Autoren und Implementierer.

Diese Datei übernimmt daraus keine darüber hinausgehenden Aussagen, die nicht Bestandteil der HTML-Elementdefinition selbst sind.

Für ZE-WebLab ist deshalb festzuhalten:

- Accessibility ist eine eigene Informationsgruppe.
- Die bloße Existenz eines `body`-Elements stellt keine eigenständige WAI-ARIA-Rolle dar.
- Weitergehende Accessibility-Regeln sind über die einschlägigen Accessibility-Spezifikationen separat zu prüfen.

## Sanitization

WHATWG weist für `body` den Sanitization-Zustand:

- **Default**

aus.

## DOM Interface

Das DOM Interface ist:

```webidl
[Exposed=Window]
interface HTMLBodyElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};

HTMLBodyElement includes WindowEventHandlers;
```

Die obsolete Members sind für das aktuelle konforme API-Modell nicht als neue HTML-Features zu inventarisieren.

## Normative Sonderregeln

Wesentliche Sonderregel des `body`-Elements ist die Verbindung mit dem `Window`-Event-Handler-Modell.

Außerdem ist in konformen Dokumenten nur ein `body`-Element vorgesehen.

---

# Detailprüfung: `article`

## WHATWG-Definition

`article` repräsentiert eine vollständige bzw. in sich geschlossene Komposition innerhalb eines Dokuments, einer Seite, einer Anwendung oder einer Website.

Sie soll grundsätzlich unabhängig verbreitbar oder wiederverwendbar sein können.

WHATWG nennt als Beispiele unter anderem:

- Forenbeitrag
- Magazin- oder Zeitungsartikel
- Blogeintrag
- Nutzerkommentar
- interaktives Widget
- sonstige eigenständige Inhalte

## Content Categories

`article` gehört zu:

- Flow content
- Sectioning content
- Palpable content

## Context

`article` kann dort verwendet werden, wo Sectioning Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content.

## Tag Omission

Für `article` können weder Starttag noch Endtag ausgelassen werden.

## Content Attributes

Es gelten:

- Global Attributes

Weitere elementbezogene Content Attributes definiert §4.3.2 nicht.

## Verschachtelte `article`-Elemente

Verschachtelte `article`-Elemente repräsentieren grundsätzlich Artikel bzw. eigenständige Einheiten, die inhaltlich mit dem äußeren `article` zusammenhängen.

Ein typischer Fall ist:

- äußerer `article`: Blogeintrag
- innere `article`-Elemente: Kommentare

## Author Information

Mit einem `article` verbundene Autoreninformationen beziehen sich nicht automatisch auf verschachtelte `article`-Elemente.

Für ein inneres `article` muss die jeweilige Information eigenständig betrachtet werden.

## Syndication / Wiederverwendung

Wenn Inhalte zur Syndizierung bestimmt sind, entspricht die Semantik von `article` konzeptionell dem Zweck eines eigenständig verteilbaren Eintrags.

## Accessibility

WHATWG verweist auf Accessibility Considerations für Autoren und Implementierer.

Die Elementdefinition selbst begründet keine zusätzliche, hier separat zu inventarisierende Accessibility-Featurefamilie.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`article` verwendet:

- `HTMLElement`

Es gibt für `article` kein eigenes spezialisiertes DOM-Interface.

---

# Detailprüfung: `section`

## WHATWG-Definition

`section` repräsentiert einen generischen Abschnitt eines Dokuments oder einer Anwendung.

Ein Abschnitt ist dabei eine thematische Gruppierung von Inhalt, typischerweise mit einer Überschrift.

Beispiele sind:

- Kapitel
- einzelne Seiten innerhalb eines Tab-Dialogs
- nummerierte Abschnitte einer Arbeit
- thematische Bereiche einer Startseite

## Content Categories

`section` gehört zu:

- Flow content
- Sectioning content
- Palpable content

## Context

`section` kann dort verwendet werden, wo Sectioning Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content.

## Tag Omission

Für `section` sind weder Starttag noch Endtag auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

Weitere elementbezogene Content Attributes definiert §4.3.3 nicht.

## Semantischer Zweck

`section` ist kein generischer Container.

Wenn ein Element lediglich benötigt wird für:

- Styling
- Scripting
- technische Gruppierung ohne eigene semantische Sektion

soll stattdessen ein geeigneter generischer Container wie `div` geprüft werden.

Die WHATWG-Beschreibung verbindet `section` mit einer tatsächlichen Dokumentstruktur.

Als praktische Regel wird angegeben, dass `section` nur dann passend ist, wenn sein Inhalt in der Dokumentstruktur bzw. im Outline explizit als Abschnitt erscheinen soll.

## Verhältnis zu `article`

WHATWG empfiehlt, `article` anstelle von `section` zu verwenden, wenn die Inhalte sinnvollerweise syndiziert bzw. als eigenständige Komposition behandelt werden können.

`section` ist dagegen die generische semantische Einheit für einen thematischen Abschnitt.

## Accessibility

WHATWG stellt eigene Accessibility Considerations für Autoren und Implementierer bereit.

Für die ZE-WebLab-Referenz ist insbesondere festzuhalten:

- `section` ist Sectioning Content.
- Die Verwendung ist semantisch und nicht lediglich visuell.
- Eine Section sollte eine tatsächliche thematische Einheit darstellen.
- Die Accessibility-Auswirkungen der konkreten Überschriftenstruktur sind gemeinsam mit dem Heading-/Outline-Modell zu betrachten.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`section` verwendet:

- `HTMLElement`

---

# Detailprüfung: `nav`

## WHATWG-Definition

`nav` repräsentiert einen Abschnitt einer Seite, der Links zu anderen Seiten oder zu Teilen innerhalb derselben Seite enthält.

Es handelt sich um einen Abschnitt mit Navigationslinks.

## Content Categories

`nav` gehört zu:

- Flow content
- Sectioning content
- Palpable content

## Context

`nav` kann dort verwendet werden, wo Sectioning Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content.

## Tag Omission

Weder Starttag noch Endtag sind auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

Keine zusätzlichen elementbezogenen Content Attributes werden in §4.3.4 definiert.

## Umfang der Navigation

Nicht jede Linkgruppe einer Seite muss in `nav` eingeschlossen werden.

Das Element ist insbesondere für wichtige bzw. größere Navigationsblöcke vorgesehen.

Ein kurzer Linkblock im Footer, beispielsweise mit:

- Impressum
- Nutzungsbedingungen
- Startseite
- Copyright

muss nicht zusätzlich mit `nav` ausgezeichnet werden.

## Accessibility-Bezug

User Agents, insbesondere assistive Technologien, können `nav` verwenden, um Navigationsinformationen zu identifizieren.

Dadurch kann Navigation beispielsweise:

- beim initialen Rendering übersprungen werden,
- gezielt verfügbar gemacht werden,
- als Navigationsbereich erkannt werden.

## `nav` benötigt keine Liste

Das Content Model ist nicht auf `ul` oder andere Listen beschränkt.

Ein `nav`-Element kann beispielsweise Navigation in Fließtext enthalten.

## Mehrere `nav`-Elemente

Eine Seite kann mehrere `nav`-Elemente besitzen.

Beispiele:

- Hauptnavigation der Website
- sekundäre Navigation innerhalb eines Artikels
- Navigation innerhalb einer Anwendung

Die einzelnen Navigationsbereiche können unterschiedliche semantische Aufgaben haben.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`nav` verwendet:

- `HTMLElement`

---

# Detailprüfung: `aside`

## WHATWG-Definition

`aside` repräsentiert einen Abschnitt eines Dokuments, dessen Inhalt tangential mit dem Inhalt um den Abschnitt herum verbunden ist und der als eigenständige Einheit betrachtet werden kann.

Die konkrete Beziehung hängt vom Kontext ab.

## Content Categories

`aside` gehört zu:

- Flow content
- Sectioning content
- Palpable content

## Context

`aside` kann dort verwendet werden, wo Sectioning Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content.

## Tag Omission

Weder Starttag noch Endtag sind auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

Keine zusätzlichen elementbezogenen Content Attributes werden in §4.3.5 definiert.

## Kontextabhängige Bedeutung

Ein `aside` innerhalb eines `article` kann sich speziell auf diesen Artikel beziehen.

Ein `aside` außerhalb des Artikels kann dagegen mit der übergeordneten Seite verbunden sein.

Beispielsweise:

- Blogroll auf Seitenebene → tangential zur gesamten Seite
- zusätzlicher Kommentarhinweis innerhalb eines Blogartikels → tangential zum Artikel

Die semantische Beziehung wird daher nicht ausschließlich durch das Element selbst, sondern auch durch seine Position im Dokument bestimmt.

## Typische Einsatzbereiche

WHATWG nennt unter anderem:

- Sidebars
- Blogrolls
- verwandte Inhalte
- zusätzliche Informationen
- ergänzende Inhalte

## Accessibility

WHATWG stellt Accessibility Considerations für Autoren und Implementierer bereit.

Für ZE-WebLab ist insbesondere relevant, dass `aside` Sectioning Content darstellt und daher in der Dokumentstruktur berücksichtigt wird.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`aside` verwendet:

- `HTMLElement`

---

# Detailprüfung: `h1`–`h6`

## Elementfamilie

WHATWG behandelt `h1`, `h2`, `h3`, `h4`, `h5` und `h6` gemeinsam.

Die Elemente repräsentieren Überschriften für ihre jeweiligen Sections.

## Content Categories

Die Heading-Elemente gehören zu:

- Flow content
- Heading content
- Palpable content

## Context

Sie können verwendet werden:

- als Kind eines `hgroup`-Elements
- dort, wo Heading Content erwartet wird.

## Content Model

Das Content Model ist:

- Phrasing content.

## Tag Omission

Für `h1` bis `h6` sind weder Starttag noch Endtag auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

Die Überschriftselemente besitzen in §4.3.6 keine zusätzlichen elementbezogenen Content Attributes.

## DOM Interface

Alle sechs Elemente verwenden:

```webidl
[Exposed=Window]
interface HTMLHeadingElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

## Heading Level

Die Nummer des Elements entspricht grundsätzlich seinem Heading Level:

| Element | Basis-Level |
|---|---:|
| `h1` | 1 |
| `h2` | 2 |
| `h3` | 3 |
| `h4` | 4 |
| `h5` | 5 |
| `h6` | 6 |

Die tatsächliche berechnete Heading-Ebene kann durch das WHATWG-Modell für `headingoffset` beeinflusst werden.

## Semantische Beziehung zu Sections

WHATWG beschreibt zwei grundsätzlich gleichwertige Formen:

1. Verschachtelte Überschriften ohne explizite `section`-Elemente.
2. Überschriften innerhalb expliziter `section`-Elemente.

Beide können dieselbe Dokumentstruktur ausdrücken.

Die Wahl zwischen diesen Formen kann eine Frage der gewünschten Authoring-Struktur und der zusätzlichen Styling-Hooks sein.

---

# Detailprüfung: `hgroup`

## WHATWG-Definition

`hgroup` repräsentiert eine Überschrift zusammen mit zugehörigem Inhalt.

Es kann verwendet werden, um eine `h1`–`h6`-Überschrift mit einem oder mehreren `p`-Elementen zu gruppieren, die beispielsweise darstellen:

- Subheading
- alternativen Titel
- Tagline

## Content Categories

`hgroup` gehört zu:

- Flow content
- Heading content
- Palpable content

## Context

`hgroup` kann dort verwendet werden, wo Heading Content erwartet wird.

## Content Model

Das Content Model ist präzise strukturiert:

1. null oder mehr `p`-Elemente,
2. danach genau ein `h1`, `h2`, `h3`, `h4`, `h5` oder `h6`,
3. danach null oder mehr `p`-Elemente,
4. wobei Script-supporting Elements entsprechend dem definierten Modell optional eingestreut werden können.

Damit ist beispielsweise eine Überschrift mit Untertitel oder Tagline ausdrückbar.

## Tag Omission

Weder Starttag noch Endtag sind auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`hgroup` verwendet:

- `HTMLElement`

## Heading-Zusammenhang

`hgroup` ist Teil des Heading Content und wird deshalb bei der Betrachtung von Überschriften und Dokumentstrukturen gemeinsam mit `h1`–`h6` betrachtet.

---

# Detailprüfung: `header`

## WHATWG-Definition

`header` repräsentiert eine Gruppe einleitender oder navigationsbezogener Hilfsmittel.

Typische Inhalte können sein:

- Überschrift
- `hgroup`
- Inhaltsverzeichnis
- Suchformular
- relevante Logos
- weitere einleitende oder navigationsbezogene Inhalte

Eine Überschrift ist üblich, aber nicht zwingend.

## Content Categories

`header` gehört zu:

- Flow content
- Palpable content

`header` ist **kein Sectioning Content**.

## Context

`header` kann dort verwendet werden, wo Flow Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content,
- jedoch ohne `header`- oder `footer`-Elemente als Nachfahren.

Damit ist insbesondere keine beliebige Rekursion von `header` innerhalb von `header` vorgesehen.

## Tag Omission

Weder Starttag noch Endtag sind auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

## Verhältnis zu Sections

`header` erzeugt keine neue Section.

Es ist deshalb nicht selbst Bestandteil des Sectioning-Algorithmus.

Eine Überschrift innerhalb eines `header` kann dennoch eine Überschrift des umgebenden Abschnitts sein.

## Outline-Verhalten

`header` nimmt nicht selbst am Outline-Modell teil.

Eine nachfolgende Überschrift kann daher weiterhin Teil der Section sein, die durch die entsprechende Überschrift innerhalb des `header` begonnen wurde.

## Accessibility

WHATWG unterscheidet bei `header` die Accessibility-Betrachtung abhängig davon, ob ein Sectioning-Content-Ancestor vorhanden ist.

Die konkrete Accessibility-Semantik ist deshalb kontextabhängig.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`header` verwendet:

- `HTMLElement`

---

# Detailprüfung: `footer`

## WHATWG-Definition

`footer` repräsentiert den Footer seines nächsten Sectioning-Content-Vorfahren.

Existiert kein solcher Vorfahr, bezieht sich der Footer auf das `body`-Element bzw. auf die Seite insgesamt.

Typische Inhalte können sein:

- Autorinformationen
- Links zu verwandten Dokumenten
- Copyright-Informationen
- weitere Informationen über den jeweiligen Abschnitt

## Content Categories

`footer` gehört zu:

- Flow content
- Palpable content

`footer` ist kein Sectioning Content.

## Context

`footer` kann dort verwendet werden, wo Flow Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content,
- ohne `header`- oder `footer`-Elemente als Nachfahren.

## Tag Omission

Weder Starttag noch Endtag sind auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

## Beziehung zum nächstgelegenen Abschnitt

Ein `footer` gehört semantisch zu seinem nächsten Sectioning-Content-Vorfahren.

Wenn kein solcher Vorfahr existiert, bezieht er sich auf das `body` bzw. die gesamte Seite.

## Footer ist nicht zwingend am Ende

WHATWG stellt ausdrücklich fest, dass ein Footer nicht zwingend am Ende des Abschnitts stehen muss.

Das Ende ist allerdings der typische Einsatzort.

## Footer ist kein Sectioning Content

`footer` führt keine neue Section ein.

Das ist wichtig für die Trennung von:

- Abschnittsbildung
- Abschnitts-Metadaten

## Ganze Sections im Footer

Wenn ein `footer` vollständige Sections enthält, können diese beispielsweise darstellen:

- Anhänge
- Indizes
- ausführliche Kolophone
- umfangreiche Lizenzvereinbarungen

## Accessibility

WHATWG unterscheidet die Accessibility-Betrachtung danach, ob ein Sectioning-Content-Ancestor vorhanden ist.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`footer` verwendet:

- `HTMLElement`

---

# Detailprüfung: `address`

## WHATWG-Definition

`address` repräsentiert Kontaktinformationen für den nächsten `article`- oder `body`-Vorfahren.

Wenn der relevante Vorfahr `body` ist, beziehen sich die Kontaktinformationen auf das Dokument als Ganzes.

## Content Categories

`address` gehört zu:

- Flow content
- Palpable content

## Context

`address` kann dort verwendet werden, wo Flow Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content

mit folgenden Einschränkungen:

- keine Heading-Content-Nachfahren
- keine Sectioning-Content-Nachfahren
- keine `header`-Nachfahren
- keine `footer`-Nachfahren
- keine `address`-Nachfahren

## Tag Omission

Weder Starttag noch Endtag sind auslassbar.

## Content Attributes

Es gelten:

- Global Attributes

## Semantik: Kontaktinformation

`address` ist nicht das allgemeine HTML-Element für beliebige Adressen.

Insbesondere darf eine gewöhnliche Postanschrift nicht allein deshalb mit `address` ausgezeichnet werden.

`address` ist für relevante Kontaktinformationen bestimmt.

## Nicht-konforme Verwendung

Eine beliebige Information wie:

- Änderungsdatum
- allgemeiner Dokumenttext
- sonstige Nicht-Kontaktinformation

gehört nicht in `address`.

## Typische Einbettung

`address` wird häufig innerhalb eines `footer` verwendet.

Beispiel:

```html
<footer>
  <address>
    For more details, contact
    <a href="mailto:js@example.com">John Smith</a>.
  </address>
  <p><small>© copyright 2038 Example Corp.</small></p>
</footer>
```

## Kontaktinformationen eines Nodes

WHATWG definiert zusätzlich ein Modell dafür, welche `address`-Elemente die Kontaktinformationen eines Nodes bilden.

Für ein `article` bzw. `body` werden die relevanten `address`-Elemente anhand der Vorfahrbeziehungen bestimmt.

Für einen Node innerhalb eines `article` oder `body` gelten die Kontaktinformationen des nächsten entsprechenden `article`- oder `body`-Vorfahren.

User Agents dürfen diese Kontaktinformationen Nutzern zugänglich machen oder beispielsweise für Indexierungszwecke verwenden.

## Accessibility

WHATWG verweist auf die einschlägigen Accessibility Considerations.

Die besondere Bedeutung des Elements liegt in der semantischen Auszeichnung von Kontaktinformationen.

## Sanitization

Sanitization:

- **Default**

## DOM Interface

`address` verwendet:

- `HTMLElement`

---

# Headings and outlines

## §4.3.11

Der Abschnitt "Headings and outlines" ist ein eigenständiges Konzept und kein zusätzliches HTML-Element.

Er definiert insbesondere:

- Heading Levels
- Heading-Struktur
- Outline
- Beziehungen zwischen Überschriften und Sections
- Anforderungen an Heading Levels
- Empfehlungen zur Darstellung von Outlines

## Heading Level

`h1`–`h6` besitzen eine Heading Level.

Diese wird über das WHATWG-Modell zur Ermittlung der berechneten Heading-Ebene bestimmt.

Die niedrigere Heading Level entspricht einer geringeren Anzahl übergeordneter Sections.

## Outline

Die Outline eines Dokuments besteht aus den Überschriften des Dokuments in Tree Order.

Die Outline kann beispielsweise zur Erzeugung eines Inhaltsverzeichnisses verwendet werden.

Bei einem interaktiven Inhaltsverzeichnis sollen Einträge zur jeweiligen Überschrift führen.

## Mindestanforderung für Level 1

Wenn ein Dokument eine oder mehrere Überschriften besitzt, soll sich innerhalb der Outline mindestens eine Überschrift mit Heading Level 1 befinden.

## Aufeinanderfolgende Überschriften

Jede Überschrift nach einer vorhergehenden Überschrift `lead` in der Outline muss eine Heading Level besitzen, die:

- kleiner,
- gleich,
- oder höchstens um 1 größer

als die Heading Level von `lead` ist.

Ein Sprung beispielsweise von Level 1 direkt zu Level 3 ist damit nach der beschriebenen Konformitätsregel problematisch.

Beispiel für eine nicht-konforme Struktur:

```html
<body>
  <h1>Apples</h1>
  <p>Apples are fruit.</p>

  <section>
    <h3>Taste</h3>
    <p>They taste lovely.</p>
  </section>
</body>
```

Konform wäre beispielsweise:

```html
<body>
  <h1>Apples</h1>
  <p>Apples are fruit.</p>

  <section>
    <h2>Taste</h2>
    <p>They taste lovely.</p>
  </section>
</body>
```

---

# Heading levels & offsets

## §4.3.11.1

Die aktuelle WHATWG-Spezifikation definiert zusätzlich:

- `headingoffset`
- `headingreset`

Diese sind keine eigenständigen HTML-Elemente.

Sie gehören in ZE-WebLab deshalb zur Attribut-/Konzept-Ebene.

## `headingoffset`

`headingoffset` erlaubt es, die Heading Levels für Nachfahren zu verschieben.

Der Attributwert muss eine gültige nicht-negative Ganzzahl zwischen:

- `0`
- und `8`

einschließlich sein.

## `headingreset`

`headingreset` ist ein Boolean Attribute.

Es verhindert, dass die Berechnung des Heading Offsets über das Element mit diesem Attribut hinaus fortgesetzt wird.

## Berechnung der Heading Level

Die Ausgangsebene wird anhand des lokalen Namens bestimmt:

| Element | Ausgangsebene |
|---|---:|
| `h1` | 1 |
| `h2` | 2 |
| `h3` | 3 |
| `h4` | 4 |
| `h5` | 5 |
| `h6` | 6 |

Danach wird der berechnete Heading Offset hinzuaddiert.

Wenn das Ergebnis größer als 9 ist, wird es auf 9 begrenzt.

## Berechnung des Heading Offset

Für die Berechnung wird von dem jeweiligen Element ausgehend die Ancestor-Kette betrachtet.

Für jedes HTML-Element mit `headingoffset` wird dessen Wert als nicht-negative Ganzzahl verarbeitet.

Der Offset wird addiert.

Wenn ein Element `headingreset` besitzt, wird die Offset-Suche dort beendet.

Das Modell berücksichtigt auch den Übergang über Shadow Roots zum jeweiligen Host.

## Beispiel

```html
<body>
  <main>
    <h1>This is a heading level 1</h1>

    <article headingoffset="1">
      <h1>This is a heading level 2</h1>

      <section headingoffset="1">
        <h1>This is a heading level 3</h1>

        <dialog headingreset>
          <h1>This is a heading level 1</h1>
        </dialog>
      </section>
    </article>

    <h1 aria-level="2">This is a heading level 2</h1>
  </main>
</body>
```

Das Beispiel demonstriert die Berechnungsmechanik und ist laut WHATWG nicht als allgemeine Best-Practice-Struktur zu verstehen.

---

# Sample outlines

## §4.3.11.2

WHATWG enthält Beispiele für die resultierende Outline verschiedener Dokumentstrukturen.

Ein Dokument kann Überschriften verwenden:

- direkt aufeinanderfolgend,
- innerhalb von `section`,
- innerhalb von `article`,
- innerhalb von `header`,
- innerhalb von `hgroup`.

## Explizite und implizite Struktur

Folgende Strukturen können hinsichtlich der Überschriftenstruktur äquivalent sein:

```html
<h1>Let's call it a draw(ing surface)</h1>
<h2>Diving in</h2>
<h2>Simple shapes</h2>
<h2>Canvas coordinates</h2>
<h3>Canvas coordinates diagram</h3>
<h2>Paths</h2>
```

und:

```html
<h1>Let's call it a draw(ing surface)</h1>

<section>
  <h2>Diving in</h2>
</section>

<section>
  <h2>Simple shapes</h2>
</section>

<section>
  <h2>Canvas coordinates</h2>

  <section>
    <h3>Canvas coordinates diagram</h3>
  </section>
</section>

<section>
  <h2>Paths</h2>
</section>
```

Die erste Variante ist kürzer.

Die zweite Variante bietet zusätzliche explizite Sectioning-Strukturen und damit weitere Styling- und Strukturierungsmöglichkeiten.

## Mehrere Top-Level-Überschriften

Ein Dokument kann mehrere `h1`-Überschriften besitzen.

Beispiel:

```html
<h1>Apples</h1>
<p>Pomaceous.</p>

<h1>Bananas</h1>
<p>Edible.</p>

<h1>Carambola</h1>
<p>Star.</p>
```

Die resultierende Outline kann mehrere Top-Level-Einträge enthalten.

## `title` ist keine Heading

Das `title`-Element ist keine Heading.

Sein Text gehört daher nicht zur Heading-Struktur der Dokument-Outline.

## `header` verändert die Outline nicht

`header`-Elemente beeinflussen die Outline nicht selbst.

Eine Überschrift innerhalb eines `header` kann dennoch Teil der Outline sein.

Beispiel:

```html
<h1>Ray's blog</h1>

<article>
  <header>
    <nav>
      <a href="?t=-1d">Yesterday</a>
      <a href="?t=-7d">Last week</a>
      <a href="?t=-1m">Last month</a>
    </nav>

    <h2>We're adopting a child!</h2>
  </header>

  <p>As of today, Janine and I have signed the papers.</p>
</article>
```

Die Outline enthält hier:

1. `Ray's blog`
2. `We're adopting a child!`

## Dokument ohne Heading Level 1

Ein Dokument kann technisch konform sein, obwohl keine Heading Level 1 vorhanden ist.

WHATWG ermutigt eine solche Struktur jedoch nicht.

Beispielsweise:

```html
<section>
  <h2>Apples</h2>
  <p>Pomaceous.</p>
</section>

<section>
  <h2>Bananas</h2>
  <p>Edible.</p>
</section>
```

Die Struktur ist konform, aber nicht empfohlen, weil keine Heading Level 1 vorhanden ist.

## Erste Heading mit Level ungleich 1

Auch eine erste Heading mit einem anderen Level kann konform sein.

Beispielsweise:

```html
<h2>A plea from our caretakers</h2>
<p>Please, we beg of you, send help!</p>

<h1>Feathers</h1>
<p>Epidermal growths.</p>
```

Auch dies wird von WHATWG nicht als bevorzugte Struktur dargestellt.

---

# Exposing outlines to users

## §4.3.11.3

User Agents werden ermutigt, Dokument-Outlines Nutzern zugänglich zu machen.

Das unterstützt insbesondere:

- Navigation
- Orientierung
- nicht-visuelle Nutzung
- Screenreader-Nutzung

WHATWG nennt als mögliches Interaktionsmodell beispielsweise Tastaturnavigation zwischen Überschriften.

Das konkrete UI-Verhalten ist dabei nicht als verpflichtendes Browser-UI vorgegeben.

---

# Usage summary

## §4.3.12

Der WHATWG-Abschnitt "Usage summary" ist ausdrücklich **nicht normativ**.

Er fasst die primären Verwendungszwecke der Sectioning-Elemente zusammen.

## Zusammenfassung der Elementzwecke

| Element | Zweck |
|---|---|
| `body` | Inhalt des Dokuments |
| `article` | vollständige bzw. eigenständige Komposition, die grundsätzlich unabhängig verteilt oder wiederverwendet werden kann |
| `section` | generischer thematischer Abschnitt |
| `nav` | wichtiger Navigationsbereich |
| `aside` | tangential mit dem umgebenden Inhalt verbundener Abschnitt |
| `h1`–`h6` | Überschriften für Sections |
| `hgroup` | Überschrift zusammen mit zugehörigem Subheading-/Titel-/Tagline-Inhalt |
| `header` | einleitende oder navigationsbezogene Hilfsmittel |
| `footer` | Footer des nächstgelegenen Sectioning-Content-Elements bzw. des Dokuments |
| `address` | Kontaktinformationen des nächsten `article`- oder `body`-Vorfahren |

---

# Article or section?

## §4.3.12.1

WHATWG behandelt ausdrücklich die Frage, wann `article` und wann `section` verwendet werden sollte.

## `article`

`article` ist geeignet, wenn der Inhalt eine:

- vollständige,
- eigenständige,
- in sich geschlossene

Komposition darstellt.

Ein wesentlicher Gesichtspunkt ist, ob die Einheit grundsätzlich unabhängig verteilt oder wiederverwendet werden könnte.

Typische Beispiele:

- Blogartikel
- Forenbeitrag
- Kommentar
- eigenständige Nachricht
- Widget
- eigenständiger Inhalt

## `section`

`section` ist geeignet, wenn der Inhalt einen:

- thematischen Abschnitt
- innerhalb einer größeren Komposition

darstellt.

Die Section muss nicht unabhängig verteilt werden können.

## Entscheidungsregel für ZE-WebLab

Für die praktische Referenzierung kann folgende WHATWG-orientierte Unterscheidung verwendet werden:

> Ist der Inhalt selbst eine eigenständige Komposition, ist `article` zu prüfen.

> Ist der Inhalt ein thematischer Abschnitt einer übergeordneten Komposition, ist `section` zu prüfen.

> Wird lediglich ein generischer Container für Styling oder Scripting benötigt, ist `section` nicht das geeignete Element; stattdessen ist ein generischer Container wie `div` zu prüfen.

Diese Formulierung ist eine fachliche Ableitung aus den WHATWG-Beschreibungen und keine zusätzliche normative Definition.

---

# Content Categories

## Überblick

Die Sectioning-Elemente dieses Themenblocks lassen sich nicht auf eine einzige Kategorie reduzieren.

### Sectioning Content

Zu Sectioning Content gehören:

- `article`
- `section`
- `nav`
- `aside`

### Heading Content

Zu Heading Content gehören:

- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `hgroup`

### Flow Content ohne Sectioning Content

Folgende Elemente dieses Blocks sind Flow Content, aber kein Sectioning Content:

- `body`
- `header`
- `footer`
- `address`

### Palpable Content

WHATWG klassifiziert als Palpable Content:

- `article`
- `section`
- `nav`
- `aside`
- `h1`–`h6`
- `hgroup`
- `header`
- `footer`
- `address`

`body` wird in §4.3.1 dagegen mit keiner Content Category aufgeführt.

---

# Contexts

## Übersicht

| Element | Context |
|---|---|
| `body` | Als zweites Element in `html` |
| `article` | Wo Sectioning Content erwartet wird |
| `section` | Wo Sectioning Content erwartet wird |
| `nav` | Wo Sectioning Content erwartet wird |
| `aside` | Wo Sectioning Content erwartet wird |
| `h1`–`h6` | Als Kind von `hgroup` oder wo Heading Content erwartet wird |
| `hgroup` | Wo Heading Content erwartet wird |
| `header` | Wo Flow Content erwartet wird |
| `footer` | Wo Flow Content erwartet wird |
| `address` | Wo Flow Content erwartet wird |

Contexts dürfen nicht mit Content Models verwechselt werden.

Der Context beschreibt, wo ein Element eingesetzt werden darf.

Das Content Model beschreibt, welchen Inhalt das Element enthalten darf.

---

# Content Models

## Übersicht

| Element | Content Model |
|---|---|
| `body` | Flow content |
| `article` | Flow content |
| `section` | Flow content |
| `nav` | Flow content |
| `aside` | Flow content |
| `h1`–`h6` | Phrasing content |
| `hgroup` | `p`* → `h1`–`h6` → `p`*, mit Script-supporting Elements gemäß Modell |
| `header` | Flow content ohne `header`-/`footer`-Nachfahren |
| `footer` | Flow content ohne `header`-/`footer`-Nachfahren |
| `address` | Flow content ohne Heading Content, Sectioning Content, `header`, `footer` oder `address` als Nachfahren |

---

# Tag Omission

## Übersicht

| Element | Tag-Omission-Regel |
|---|---|
| `body` | Start- und Endtag unter definierten Bedingungen auslassbar |
| `article` | keine Auslassung |
| `section` | keine Auslassung |
| `nav` | keine Auslassung |
| `aside` | keine Auslassung |
| `h1`–`h6` | keine Auslassung |
| `hgroup` | keine Auslassung |
| `header` | keine Auslassung |
| `footer` | keine Auslassung |
| `address` | keine Auslassung |

Die `body`-Regel ist damit eine echte Sonderregel innerhalb dieses Themenblocks.

---

# Content Attributes

## Elementbezogene Attribute

Für die meisten Elemente dieses Themenblocks definiert §4.3 keine zusätzlichen elementbezogenen Content Attributes.

Es gelten:

- Global Attributes

### `body`

`body` besitzt zusätzlich die im Abschnitt beschriebenen Event Handler, die mit dem `Window`-Event-Handler-Modell verbunden sind.

### `h1`–`h6`

Die Heading-Berechnung ist zusätzlich mit den Konzepten:

- `headingoffset`
- `headingreset`

verbunden.

Diese Attribute gehören in der ZE-WebLab-Gesamtstruktur zur separaten Attribut-Ebene und nicht zur HTML-Elementinventarliste.

---

# Accessibility

## WHATWG-Ebene

Die Elementdefinitionen enthalten Accessibility Considerations für Autoren und Implementierer.

Für ZE-WebLab wird daraus keine pauschale Browser- oder Screenreader-Kompatibilitätsaussage abgeleitet.

## Sectioning Content

Die Elemente:

- `article`
- `section`
- `nav`
- `aside`

erzeugen Sectioning-Strukturen.

Das ist für die semantische Dokumentstruktur und damit auch für assistive Technologien relevant.

## Navigation

`nav` kann User Agents und assistiven Technologien helfen, wichtige Navigationsbereiche zu erkennen.

## Überschriften

`h1`–`h6` repräsentieren Überschriften.

Eine logisch strukturierte Heading-Hierarchie ist für die Navigation in Dokumenten relevant.

WHATWG ermutigt User Agents ausdrücklich dazu, Outlines für Nutzer zugänglich zu machen.

## `header` und `footer`

`header` und `footer` sind keine Sectioning-Elemente.

Sie erzeugen daher selbst keine neue Section.

Ihre Accessibility-Betrachtung hängt insbesondere bei `header` und `footer` davon ab, ob sie innerhalb eines Sectioning-Content-Kontexts liegen.

## `address`

`address` dient der semantischen Kennzeichnung von Kontaktinformationen.

Es darf nicht als generisches Element für beliebige Adressen oder beliebige Metadaten missbraucht werden.

## Weiterführende Accessibility-Recherche

Die HTML-Spezifikation verweist für detaillierte Accessibility Considerations auf die einschlägigen Accessibility-Spezifikationen.

Deren vollständige Prüfung gehört in ZE-WebLab zur separaten Accessibility-Rechercheebene.

---

# Sanitization

## Elementzustände

WHATWG weist für die Elemente dieses Blocks jeweils den Sanitization-Zustand:

- **Default**

aus.

Dies gilt für:

- `body`
- `article`
- `section`
- `nav`
- `aside`
- `h1`–`h6`
- `hgroup`
- `header`
- `footer`
- `address`

Sanitization ist dabei eine eigenständige Informationsebene.

Sie darf nicht mit:

- Content Model
- Tag Omission
- Accessibility
- Browser-Support

vermischt werden.

---

# DOM Interfaces

## `body`

```webidl
[Exposed=Window]
interface HTMLBodyElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};

HTMLBodyElement includes WindowEventHandlers;
```

## `article`

- `HTMLElement`

## `section`

- `HTMLElement`

## `nav`

- `HTMLElement`

## `aside`

- `HTMLElement`

## `h1`–`h6`

```webidl
[Exposed=Window]
interface HTMLHeadingElement : HTMLElement {
  [HTMLConstructor] constructor();

  // also has obsolete members
};
```

## `hgroup`

- `HTMLElement`

## `header`

- `HTMLElement`

## `footer`

- `HTMLElement`

## `address`

- `HTMLElement`

## Einordnung

Nur `body` und die gemeinsame Heading-Elementfamilie besitzen in diesem Block spezialisierte DOM Interfaces.

Die übrigen Elemente verwenden direkt `HTMLElement`.

DOM Interfaces sind keine zusätzlichen HTML-Elemente und werden deshalb nicht als separate Feature-Einträge im Elementinventar gezählt.

---

# Normative Sonderregeln

## `body`

- In konformen Dokumenten gibt es nur ein `body`.
- `body` ist das zweite Element innerhalb von `html`.
- Start- und Endtag besitzen spezielle Auslassungsregeln.
- Das Element ist mit dem `WindowEventHandlers`-Modell verbunden.

## `article`

- Repräsentiert eine eigenständige bzw. unabhängig verteilbare Komposition.
- Verschachtelte `article`-Elemente können eigenständige Untereinheiten wie Kommentare darstellen.
- Autoreninformationen des äußeren `article` gelten nicht automatisch für verschachtelte `article`-Elemente.

## `section`

- Repräsentiert einen thematischen Abschnitt.
- Ist kein generischer Container.
- Für reine Styling-/Scripting-Zwecke ist ein generischer Container wie `div` geeigneter.
- `article` ist vorzuziehen, wenn die Inhalte eigenständig syndizierbar bzw. wiederverwendbar sind.

## `nav`

- Nicht jede Linkgruppe muss in `nav` stehen.
- Das Element ist für wichtige Navigationsblöcke gedacht.
- `nav` muss keine Liste enthalten.

## `aside`

- Die Bedeutung hängt vom umgebenden Kontext ab.
- Innerhalb eines `article` kann `aside` auf diesen Artikel bezogen sein.
- Auf Seitenebene kann `aside` tangentiale Inhalte zur gesamten Seite enthalten.

## `h1`–`h6`

- Die Elementnummer entspricht der Basis-Heading-Level.
- Die berechnete Heading Level kann durch `headingoffset` beeinflusst werden.
- `h1`–`h6` gehören zu Heading Content.
- Sie repräsentieren Überschriften der jeweiligen Sections.

## `hgroup`

- Muss ein Heading-Element enthalten.
- `p`-Elemente können davor und danach verwendet werden.
- Dient insbesondere zur Gruppierung von Überschrift und Subheading/Tagline/alternativem Titel.

## `header`

- Ist kein Sectioning Content.
- Erzeugt keine eigene Section.
- Darf keine `header`-/`footer`-Nachfahren besitzen.

## `footer`

- Gehört zum nächsten Sectioning-Content-Vorfahren oder zum `body`.
- Erzeugt selbst keine Section.
- Darf keine `header`-/`footer`-Nachfahren besitzen.
- Muss nicht am Ende des Abschnitts stehen.

## `address`

- Dient ausschließlich relevanter Kontaktinformation.
- Ist kein allgemeines Postaladdress-Element.
- Darf keine Heading-/Sectioning-Content-Nachfahren und keine `header`-, `footer`- oder `address`-Nachfahren besitzen.

---

# Querverweise

## Document Element

`body` steht unmittelbar in Beziehung zum `html`-Element aus:

- §4.1 The document element

## Document Metadata

Das `title`-Element aus §4.2 ist keine Heading und beeinflusst deshalb die Heading-Outline nicht.

## Grouping Content

Für `section` und `article` ist die Abgrenzung zu generischen Containern wie `div` relevant.

## Text-level Semantics

Heading-Inhalte können Phrasing Content enthalten.

## Links

`nav` wird häufig zusammen mit:

- `a`
- Listen
- anderen Linkmechanismen

verwendet.

`nav` selbst ist jedoch nicht auf ein bestimmtes Linkelement beschränkt.

## Embedded Content

`header`, `footer`, `article` und `section` können Embedded Content als Teil ihres Flow Contents enthalten.

## Forms

Ein `header` kann beispielsweise ein Suchformular enthalten.

## Interactive Elements

Ein `article` kann interaktive Widgets enthalten.

## Accessibility

Sectioning und Heading-Strukturen stehen in unmittelbarer Beziehung zu Accessibility APIs und assistiven Technologien.

## Global Attributes

Die in §4.3 aufgeführten Elemente übernehmen grundsätzlich die Global Attributes, soweit die jeweilige Definition keine speziellere Einschränkung nennt.

---

# Abgrenzung: Sectioning Content vs. Heading Content

Eine zentrale fachliche Unterscheidung für ZE-WebLab ist:

| Konzept | Elemente |
|---|---|
| Sectioning Content | `article`, `section`, `nav`, `aside` |
| Heading Content | `h1`–`h6`, `hgroup` |

`header` und `footer` gehören dagegen nicht zu Sectioning Content.

Damit ist insbesondere folgende Aussage falsch:

> "Jedes semantische Abschnittselement erzeugt automatisch eine Section."

Für den aktuellen WHATWG-Stand müssen mindestens die jeweiligen Content Categories unterschieden werden.

---

# Abgrenzung: `article` vs. `section`

| Kriterium | `article` | `section` |
|---|---|---|
| Eigenständige Komposition | Ja, zentraler Zweck | Nicht erforderlich |
| Syndizierbarkeit/Wiederverwendung | Wesentlicher Anwendungsfall | Nicht zentral |
| Thematischer Abschnitt | Möglich, wenn eigenständig | Zentraler Zweck |
| Sectioning Content | Ja | Ja |
| Flow Content | Ja | Ja |
| Palpable Content | Ja | Ja |
| Content Model | Flow content | Flow content |
| Generischer Styling-Container | Nein | Nein |

Diese Tabelle ist eine fachliche Verdichtung der WHATWG-Definitionen und keine eigenständige normative Spezifikation.

---

# Abgrenzung: `header` vs. `footer`

| Merkmal | `header` | `footer` |
|---|---|---|
| Sectioning Content | Nein | Nein |
| Flow Content | Ja | Ja |
| Palpable Content | Ja | Ja |
| Typischer Zweck | Einleitung / Navigation | Abschlussinformationen |
| Erzeugt Section | Nein | Nein |
| Global Attributes | Ja | Ja |
| DOM Interface | `HTMLElement` | `HTMLElement` |

Beide Elemente sind Struktur-/Metadatencontainer und keine Sectioning-Elemente.

---

# Abgrenzung: `aside` vs. `section`

`section` repräsentiert eine thematische Gruppierung des eigentlichen Inhalts.

`aside` repräsentiert dagegen einen Inhalt, der mit dem umgebenden Inhalt tangential verbunden ist.

Daraus folgt:

- Hauptthematischer Abschnitt → `section`
- eigenständige Komposition → `article`
- tangentialer Zusatzinhalt → `aside`

Die konkrete Wahl muss anhand der tatsächlichen Semantik des Inhalts erfolgen.

---

# Abgrenzung: `nav` vs. beliebige Linkgruppe

Eine Linkgruppe ist nicht automatisch ein Navigationsabschnitt.

`nav` ist insbesondere für wichtige Navigationsblöcke vorgesehen.

Beispiele für typische `nav`-Bereiche:

- Hauptnavigation
- Seiten-/Abschnittsnavigation
- größere Navigationsbereiche einer Webanwendung

Ein kleiner Linkblock im Footer benötigt dagegen nicht zwingend `nav`.

---

# Abgrenzung: `address` vs. Postadresse

`address` ist nicht das generische Element für eine postalische Adresse.

Die relevante Frage lautet:

> Handelt es sich um Kontaktinformationen des entsprechenden `article`- oder `body`-Kontexts?

Wenn nicht, ist `address` nicht automatisch das richtige Element.

---

# Status / V1

## WHATWG-Status

Alle in diesem Dokument untersuchten Elemente sind Bestandteil der aktuellen WHATWG HTML Living Standard:

- `body`
- `article`
- `section`
- `nav`
- `aside`
- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `hgroup`
- `header`
- `footer`
- `address`

## Konformität

"Im WHATWG-Standard definiert" bedeutet nicht automatisch:

> Jede beliebige Verwendung des Elements ist konform.

Die Konformität hängt unter anderem ab von:

- Context
- Content Model
- Content Attributes
- konkreter Semantik
- speziellen normativen Regeln
- Heading-/Section-Struktur

## Browser-Support

Browser-Support ist nicht Bestandteil dieses Statusmodells.

Die in der WHATWG-Webdarstellung eingeblendeten MDN-Kompatibilitätsinformationen werden nicht als WHATWG-Status übernommen.

## V1-Kategorisierung

| Feature | WHATWG definiert | Konformitätsregeln vorhanden | V1-Referenz |
|---|---|---|---|
| `body` | Ja | Ja | Ja |
| `article` | Ja | Ja | Ja |
| `section` | Ja | Ja | Ja |
| `nav` | Ja | Ja | Ja |
| `aside` | Ja | Ja | Ja |
| `h1`–`h6` | Ja | Ja | Ja |
| `hgroup` | Ja | Ja | Ja |
| `header` | Ja | Ja | Ja |
| `footer` | Ja | Ja | Ja |
| `address` | Ja | Ja | Ja |

V1 bedeutet hier die Aufnahme in die ZE-WebLab-Referenz und nicht eine Aussage über Browserimplementierung.

---

# Offene Punkte

## Keine offenen Punkte hinsichtlich des HTML-Elementinventars

Der WHATWG-Abschnitt §4.3 definiert die für diesen Themenblock relevanten Elemente eindeutig.

Das Inventar ist:

- `body`
- `article`
- `section`
- `nav`
- `aside`
- `h1`
- `h2`
- `h3`
- `h4`
- `h5`
- `h6`
- `hgroup`
- `header`
- `footer`
- `address`

## Separat weiterzuführende Rechercheebenen

Nicht als offene Punkte dieses Themenblocks, sondern als separate Arbeitsebenen zu behandeln sind:

1. vollständiges Global-Attribute-Inventar
2. vollständige Accessibility-Vertiefung
3. Browser-Kompatibilität
4. detaillierte Accessibility API Mappings
5. allgemeine Content-Categories-Referenz
6. allgemeine Heading-/Outline-API- und DOM-Referenz
7. Shadow-DOM-/Heading-Offset-Interaktionen in der übergeordneten API-Dokumentation

Diese Punkte stellen keine Lücken in der §4.3-Elementrecherche dar.

---

# QS-Prüfung

## Elemente

- [x] `body`
- [x] `article`
- [x] `section`
- [x] `nav`
- [x] `aside`
- [x] `h1`
- [x] `h2`
- [x] `h3`
- [x] `h4`
- [x] `h5`
- [x] `h6`
- [x] `hgroup`
- [x] `header`
- [x] `footer`
- [x] `address`

## WHATWG-Unterabschnitte

- [x] §4.3.1 `body`
- [x] §4.3.2 `article`
- [x] §4.3.3 `section`
- [x] §4.3.4 `nav`
- [x] §4.3.5 `aside`
- [x] §4.3.6 `h1`–`h6`
- [x] §4.3.7 `hgroup`
- [x] §4.3.8 `header`
- [x] §4.3.9 `footer`
- [x] §4.3.10 `address`
- [x] §4.3.11 Headings and outlines
- [x] §4.3.11.1 Heading levels & offsets
- [x] §4.3.11.2 Sample outlines
- [x] §4.3.11.3 Exposing outlines to users
- [x] §4.3.12 Usage summary
- [x] §4.3.12.1 Article or section?

## Fachliche Informationsgruppen

- [x] Content Categories
- [x] Context
- [x] Content Model
- [x] Tag Omission
- [x] Content Attributes
- [x] Accessibility
- [x] Sanitization
- [x] DOM Interface
- [x] normative Sonderregeln
- [x] Querverweise
- [x] Status
- [x] offene Punkte

---

# Quellen / Referenzen

## Primärquelle

WHATWG, **HTML Living Standard**, §4.3 Sections:

https://html.spec.whatwg.org/multipage/sections.html

Direkt geprüfte Unterabschnitte:

- https://html.spec.whatwg.org/multipage/sections.html#the-body-element
- https://html.spec.whatwg.org/multipage/sections.html#the-article-element
- https://html.spec.whatwg.org/multipage/sections.html#the-section-element
- https://html.spec.whatwg.org/multipage/sections.html#the-nav-element
- https://html.spec.whatwg.org/multipage/sections.html#the-aside-element
- https://html.spec.whatwg.org/multipage/sections.html#the-h1,-h2,-h3,-h4,-h5,-and-h6-elements
- https://html.spec.whatwg.org/multipage/sections.html#the-hgroup-element
- https://html.spec.whatwg.org/multipage/sections.html#the-header-element
- https://html.spec.whatwg.org/multipage/sections.html#the-footer-element
- https://html.spec.whatwg.org/multipage/sections.html#the-address-element
- https://html.spec.whatwg.org/multipage/sections.html#headings-and-outlines
- https://html.spec.whatwg.org/multipage/sections.html#heading-levels-and-offsets
- https://html.spec.whatwg.org/multipage/sections.html#sample-outlines
- https://html.spec.whatwg.org/multipage/sections.html#exposing-outlines-to-users
- https://html.spec.whatwg.org/multipage/sections.html#usage-summary
- https://html.spec.whatwg.org/multipage/sections.html#article-or-section

## Verwendete externe Quelle

Für die fachliche Elementrecherche wurde keine externe Quelle als Primärgrundlage benötigt.

Die in der WHATWG-Seite eingeblendeten MDN-Verweise und Browser-Support-Daten wurden nicht als Grundlage für den WHATWG-Status übernommen.

## Quellenstatus

- Primärquelle: WHATWG HTML Living Standard
- Externe Quellen: nicht erforderlich
- Fachliche Ableitungen: als solche kenntlich gemacht
- Browser-Kompatibilität: bewusst nicht Bestandteil dieser Datei

---

# Abschlussbewertung

Der Themenblock **§4.3 Sections** ist für die Elementebene vollständig erfasst.

Die zentralen Trennungen für ZE-WebLab sind:

- Sectioning Content ist nicht dasselbe wie Heading Content.
- `header` und `footer` sind keine Sectioning-Elemente.
- `body` ist kein gewöhnliches Sectioning-Element.
- `article` und `section` haben unterschiedliche semantische Zwecke.
- `nav` ist für wichtige Navigationsbereiche vorgesehen und nicht für jede Linkgruppe erforderlich.
- `aside` ist kontextabhängig tangential.
- `h1`–`h6` bilden eine gemeinsame Heading-Elementfamilie.
- `hgroup` ist ein Heading-Grouping-Element und besitzt ein spezifisches Content Model.
- `address` bezeichnet Kontaktinformationen und nicht beliebige Adressen.
- Headings and outlines sind eine eigenständige Konzeptfamilie und keine zusätzlichen HTML-Elemente.
- `headingoffset` und `headingreset` gehören zur Attribut-/Konzept-Ebene und nicht zum Elementinventar.
- DOM Interfaces und Sanitization sind eigenständige Informationsgruppen.
- Browser-Support bleibt von WHATWG-Definition und Konformitätsstatus getrennt.