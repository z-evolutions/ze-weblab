# ZE-WebLab – HTML-Referenz: User Interaction

## Arbeitsstand / Quellenstand

- **Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien
- **Feature-Familie:** User Interaction
- **Feature-Typ:** Normative Concept / Processing Model / API / DOM Interface / Attribute Family
- **Zieldatei:** `docs/html/24-user-interaction.md`
- **Normative Primärquelle:** WHATWG HTML Living Standard
- **WHATWG-Hauptabschnitt:** §6 User interaction
- **WHATWG-Stand der Detailrecherche:** 11. August 2026
- **Projektbestand:** ZE-WebLab `docs/html/01-document-element.md` bis `docs/html/23-microdata.md`
- **Prüfstatus:** vollständig recherchiert für §6.1–§6.10 innerhalb der abgegrenzten Feature-Familie
- **Browser-Kompatibilität:** nicht Bestandteil dieser Datei
- **V1-Status:** projektspezifisch und nicht mit dem WHATWG-Status gleichzusetzen

### Quellenabgrenzung

Das ZE-WebLab-Repository beantwortet die Frage, welche Inhalte im Projekt bereits dokumentiert sind.

Der WHATWG HTML Living Standard beantwortet die Frage, welche Regeln, Konzepte, APIs, Interfaces und Konformitätsanforderungen der aktuelle HTML-Standard definiert.

Diese Datei dokumentiert die übergreifenden User-Interaction-Konzepte des HTML-Standards und ist keine erneute Elementreferenz.

### Abgrenzung zu anderen ZE-WebLab-Dateien

Bereits behandelte oder eigenständige Feature-Familien:

- `13-global-attributes.md` behandelt die Global-Attribute-Familie.
- `14-content-categories.md` behandelt Content Categories.
- `15-content-models.md` behandelt Content Models.
- `16-link-types.md` behandelt Link Types.
- `17-apis-dom-interfaces.md` behandelt die übergreifende DOM-/API-Ebene.
- `18-processing-models.md` behandelt übergreifende Processing Models.
- `19-parsing.md` behandelt Parsing.
- `20-sanitization.md` behandelt Sanitization.
- `21-custom-elements.md` behandelt Custom Elements.
- `22-svg-mathml-integration.md` behandelt HTML/SVG-/MathML-Integration.
- `23-microdata.md` behandelt Microdata.

Diese Datei verbindet die für User Interaction relevanten Regeln und verweist auf diese Feature-Familien, ersetzt sie aber nicht.

---

## Einordnung

§6 des WHATWG HTML Living Standard beschreibt normative Mechanismen, mit denen HTML-Dokumente auf Benutzerinteraktion, Fokus, Sichtbarkeit, Aktivierung, Bearbeitung und bestimmte Interaktionszustände reagieren.

Die aktuelle Struktur von §6 umfasst:

1. §6.1 The `hidden` attribute
2. §6.2 Page visibility
3. §6.3 Inert subtrees
4. §6.4 Tracking user activation
5. §6.5 Activation behavior of elements
6. §6.6 Focus
7. §6.7 Assigning keyboard shortcuts
8. §6.8 Editing
9. §6.9 Find-in-page
10. §6.10 Close requests and close watchers
11. §6.11 Drag and drop

Für diese Datei werden §6.1 bis §6.10 behandelt.

§6.11 `Drag and drop` wird als eigenständige Feature-Familie abgegrenzt, weil der Abschnitt ein eigenes Datenmodell, Drag-and-Drop-Processing, Drag Data Store, Events und zugehörige APIs enthält.

---

# WHATWG-Struktur

## §6.1 The `hidden` attribute

Behandelte Unterkonzepte:

- `hidden`
- Hidden state
- Hidden Until Found state
- Not Hidden state
- Missing Value Default
- Invalid Value Default
- Empty Value Default
- ancestor revealing algorithm
- `beforematch`
- Beziehung zu Find-in-page
- Beziehung zu Fragment Navigation
- `HTMLElement.hidden`

## §6.2 Page visibility

Behandelte Unterkonzepte:

- system visibility state
- `Document` visibility state
- `visible`
- `hidden`
- visibility state update
- `visibilitychange`
- `VisibilityStateEntry`
- Beziehung zu Performance-Timing
- Beziehung zu anderen Spezifikationen

## §6.3 Inert subtrees

Behandelte Unterkonzepte:

- inert node
- inert subtree
- Modal-Dialog-Inertness
- top layer
- `inert`
- Auswirkungen auf Hit Testing
- Auswirkungen auf Text Selection
- Auswirkungen auf Editing
- Auswirkungen auf Find-in-page
- Auswirkungen auf Fokus
- Auswirkungen auf Accessibility Exposure

## §6.4 Tracking user activation

Behandelte Unterkonzepte:

- user activation
- sticky activation
- transient activation
- last activation timestamp
- last history-action activation timestamp
- activation notification
- consumption of activation
- APIs gated by user activation
- `UserActivation`
- `navigator.userActivation`
- user-agent automation

## §6.5 Activation behavior of elements

Behandelte Unterkonzepte:

- activation behavior
- click activation
- synthetic activation
- `HTMLElement.click()`
- click-in-progress flag
- `ToggleEvent`
- `CommandEvent`
- Beziehung zwischen Benutzeraktion und DOM-Event-Verarbeitung

## §6.6 Focus

Behandelte Unterkonzepte:

- system focus
- user attention
- focused area
- focusable area
- DOM anchor
- focus target
- sequential focus navigation
- `tabindex`
- focus processing
- focus management APIs
- `autofocus`
- Shadow DOM focus delegation
- `DocumentOrShadowRoot.activeElement`
- `Document.hasFocus()`
- `Window.focus()`
- `HTMLElement.focus()`
- `HTMLElement.blur()`

## §6.7 Assigning keyboard shortcuts

Behandelte Unterkonzepte:

- `accesskey`
- access key tokens
- access key assignment
- user-agent selection of actual shortcut
- keyboard shortcut processing model

## §6.8 Editing

Behandelte Unterkonzepte:

- `contenteditable`
- editing host
- plaintext-only editing
- `Document.designMode`
- editing APIs
- spelling and grammar checking
- `spellcheck`
- writing suggestions
- `writingsuggestions`
- autocapitalization
- `autocapitalize`
- autocorrection
- `autocorrect`
- input modalities
- `inputmode`
- `enterkeyhint`
- `ElementContentEditable`

## §6.9 Find-in-page

Behandelte Unterkonzepte:

- find-in-page
- find-in-page interface
- search matches
- active match
- interaction with `details`
- interaction with `hidden=until-found`
- ancestor revealing
- interaction with selection

## §6.10 Close requests and close watchers

Behandelte Unterkonzepte:

- close request
- close request processing
- fallback action
- history-action activation
- close watcher manager
- close watcher groups
- close watcher
- `CloseWatcher`
- `requestClose()`
- `close()`
- `destroy()`
- `cancel`
- `close`
- anti-abuse restrictions

---

# Inventar

| ID | Feature | Feature-Typ | WHATWG | Status |
|---|---|---|---|---|
| UI-001 | `hidden` | Attribute / Processing Model | §6.1 | im WHATWG definiert |
| UI-002 | Hidden Until Found | Attribute State / Processing Model | §6.1 | im WHATWG definiert |
| UI-003 | Ancestor Revealing | Processing Model | §6.1 | normativer Algorithmus |
| UI-004 | Page visibility | Processing Model / DOM | §6.2 | im WHATWG definiert |
| UI-005 | `VisibilityStateEntry` | DOM/API | §6.2.1 | Interface |
| UI-006 | Inert subtrees | Processing Model | §6.3 | im WHATWG definiert |
| UI-007 | `inert` | Global Attribute / Processing Model | §6.3.2 | im WHATWG definiert |
| UI-008 | Modal-dialog inertness | Processing Model | §6.3.1 | normatives Konzept |
| UI-009 | User activation | Processing Model | §6.4 | normatives Konzept |
| UI-010 | Sticky activation | State Model | §6.4.1 | normatives Konzept |
| UI-011 | Transient activation | State Model | §6.4.1 | normatives Konzept |
| UI-012 | User activation consumption | Processing Model | §6.4.2 | normativer Algorithmus |
| UI-013 | UserActivation-gated APIs | API Integration | §6.4.3 | normatives Querschnittskonzept |
| UI-014 | `UserActivation` | DOM/API | §6.4.4 | Interface |
| UI-015 | Activation behavior | Processing Model | §6.5 | normatives Konzept |
| UI-016 | `HTMLElement.click()` | DOM API | §6.5 | API |
| UI-017 | `ToggleEvent` | DOM Interface | §6.5.1 | Interface |
| UI-018 | `CommandEvent` | DOM Interface | §6.5.2 | Interface |
| UI-019 | Focus model | Processing Model | §6.6 | normatives Konzept |
| UI-020 | Focusable area | Processing Model | §6.6.2 | normatives Konzept |
| UI-021 | `tabindex` | Attribute / Focus | §6.6.3 | im WHATWG definiert |
| UI-022 | Sequential focus navigation | Processing Model | §6.6.5 | normatives Konzept |
| UI-023 | Focus management APIs | DOM/API | §6.6.6 | API |
| UI-024 | `autofocus` | Attribute / Processing Model | §6.6.7 | im WHATWG definiert |
| UI-025 | Keyboard shortcuts | Processing Model | §6.7 | normatives Konzept |
| UI-026 | `accesskey` | Attribute / Processing Model | §6.7.2 | im WHATWG definiert |
| UI-027 | Editing hosts | Processing Model | §6.8 | normatives Konzept |
| UI-028 | `contenteditable` | Attribute / Editing | §6.8.1 | im WHATWG definiert |
| UI-029 | `designMode` | DOM/API | §6.8.2 | DOM-Konzept |
| UI-030 | Editing APIs | API | §6.8.4 | API-/externes Konzept |
| UI-031 | `spellcheck` | Attribute / Processing Model | §6.8.5 | im WHATWG definiert |
| UI-032 | Writing suggestions | Attribute / Processing Model | §6.8.6 | im WHATWG definiert |
| UI-033 | `writingsuggestions` | Attribute | §6.8.6 | im WHATWG definiert |
| UI-034 | Autocapitalization | Attribute / Processing Model | §6.8.7 | im WHATWG definiert |
| UI-035 | `autocapitalize` | Attribute | §6.8.7 | im WHATWG definiert |
| UI-036 | Autocorrection | Attribute / Processing Model | §6.8.8 | im WHATWG definiert |
| UI-037 | `autocorrect` | Attribute | §6.8.8 | im WHATWG definiert |
| UI-038 | Input modalities | Attribute / Processing Model | §6.8.9 | normatives Konzept |
| UI-039 | `inputmode` | Attribute | §6.8.9 | im WHATWG definiert |
| UI-040 | `enterkeyhint` | Attribute | §6.8.10 | im WHATWG definiert |
| UI-041 | `ElementContentEditable` | DOM Interface | §6.8.1 | Interface |
| UI-042 | Find-in-page | Processing Model | §6.9 | normatives Konzept |
| UI-043 | Hidden/Details find-in-page interaction | Processing Model | §6.9.2 | normativer Integrationsmechanismus |
| UI-044 | Find-in-page selection interaction | Processing Model | §6.9.3 | normatives Konzept |
| UI-045 | Close request | Processing Model | §6.10.1 | normatives Konzept |
| UI-046 | Close watcher infrastructure | Processing Model | §6.10.2 | normatives Konzept |
| UI-047 | `CloseWatcher` | DOM/API | §6.10.3 | Interface |
| UI-048 | `cancel` / `close` | Events | §6.10.3 | Event-Verarbeitung |

---

# Begriffsdefinitionen

## User Interaction

User Interaction bezeichnet in dieser Datei die normativen HTML-Mechanismen, die das Verhalten eines Dokuments beziehungsweise seiner DOM-Struktur im Zusammenhang mit Benutzerinteraktion definieren.

Dazu gehören insbesondere:

- Sichtbarkeit
- Inertness
- Benutzeraktivierung
- Aktivierungsverhalten
- Fokus
- Tastaturkürzel
- Editing
- Find-in-page
- Close Requests

Der Begriff ist damit breiter als ein einzelnes Event oder ein einzelnes Attribut.

## User Activation

User Activation bezeichnet einen vom HTML-Standard modellierten Interaktionszustand eines `Window`.

Er dient unter anderem dazu, bestimmte APIs an eine tatsächliche Benutzerinteraktion zu koppeln.

## Sticky Activation

Sticky Activation beschreibt einen dauerhaften Aktivierungszustand.

Nachdem ein entsprechendes `Window` eine erste relevante Aktivierung erhalten hat, bleibt der Zustand aktiv.

## Transient Activation

Transient Activation bezeichnet einen zeitlich begrenzten Aktivierungszustand.

Er steht insbesondere für APIs zur Verfügung, deren Nutzung eine kürzlich erfolgte Benutzerinteraktion voraussetzt.

## Focus

Focus bezeichnet im HTML-Standard das normative Modell dafür, welches fokussierbare Gebiet beziehungsweise welches Navigable aktuell Ziel der Tastaturinteraktion ist.

## Focusable Area

Eine Focusable Area ist ein vom HTML-Standard definiertes Gebiet, das Ziel von Fokus werden kann.

Es muss nicht zwingend exakt einem HTML-Element entsprechen.

Eine Focusable Area besitzt einen DOM Anchor.

## Activation Behavior

Activation Behavior ist das Verhalten, das ein Element bei einer Benutzeraktivierung ausführt.

Im HTML-Standard ist die Aktivierung eng mit dem `click`-Ereignis verbunden.

## Editing Host

Ein Editing Host ist ein Bereich, in dem Bearbeitung durch den Benutzer nach dem Editing-Modell möglich ist.

`contenteditable` und `designMode` sind zentrale Mechanismen dafür.

## Inert

Ein Node ist inert, wenn Benutzerinteraktionen mit diesem Node nach dem Inertness-Modell eingeschränkt beziehungsweise unterbunden werden.

Inertness betrifft nicht nur Sichtbarkeit.

---

# Normative Regeln

## `hidden`

Das `hidden`-Attribut ist ein enumeriertes Attribut.

Aktuelle Zustände:

- Hidden
- Hidden Until Found
- Not Hidden

Keywords:

- `hidden`
- `until-found`

Das Fehlen des Attributes führt zum Not Hidden State.

Ein ungültiger oder leerer Wert führt zum Hidden State.

Der Hidden State bedeutet, dass der User Agent das Element nicht rendern soll.

Der Hidden Until Found State unterscheidet sich davon insbesondere dadurch, dass der Inhalt für Find-in-page und Fragment Navigation zugänglich bleibt.

Wenn eine Suche oder Fragment Navigation einen verborgenen Zielbereich erreichen muss, kann der User Agent den Bereich über den Ancestor Revealing Algorithmus offenlegen.

## `hidden` und Aktivität

`hidden` entfernt einen Bereich nicht aus dem DOM.

Elemente innerhalb eines Hidden-Bereichs bleiben grundsätzlich aktiv.

Insbesondere können:

- Scripts weiterhin ausgeführt werden
- Form Controls weiterhin funktionieren
- Form Controls weiterhin an Submission beteiligt sein

`hidden` ist deshalb kein allgemeiner Mechanismus zum Deaktivieren eines DOM-Subtrees.

## `hidden` und Accessibility

Der Hidden State ist nicht lediglich eine visuelle Präsentationsoption.

Ein Bereich, der mit `hidden` verborgen wird, ist grundsätzlich auch nicht für die normale Benutzerwahrnehmung beziehungsweise Accessibility-Interaktion bestimmt.

`hidden` darf deshalb nicht mit einer rein visuellen CSS-Ausblendung gleichgesetzt werden.

## `inert`

`inert` ist ein Boolean Attribute.

Wenn das Attribut gesetzt ist, wird das Element und der relevante Flat-Tree-Teil seines Subtrees inert.

Inertness wirkt insbesondere auf:

- Hit Testing
- Text Selection
- Editing
- Find-in-page
- Focus
- Accessibility Exposure
- Commands beziehungsweise Interaktion

Ein inert Node ist nicht einfach dasselbe wie ein verborgenes Element.

## Modal Dialogs

Ein Modal Dialog kann die übrigen Bereiche des Dokuments inert machen.

Der Mechanismus ist mit dem Top Layer und dem Modal-Verhalten des `dialog`-Elements verbunden.

Die Modalität eines Dialogs ist deshalb nicht nur ein CSS- oder Rendering-Zustand.

## User Activation

User Activation besitzt ein normatives Zustandsmodell.

Relevant sind insbesondere:

- sticky activation
- transient activation
- last activation timestamp
- last history-action activation timestamp

Bestimmte APIs dürfen nur bei entsprechender User Activation ausgeführt werden.

## Aktivierungsverbrauch

Transient Activation kann durch API-Verarbeitung konsumiert werden.

Dadurch wird verhindert, dass eine einzelne Benutzeraktion unbegrenzt viele activation-gated Operationen auslöst.

## Activation Behavior

Elemente können ein eigenes Activation Behavior besitzen.

Die Benutzeraktivierung eines solchen Elements führt zu einem `click`-bezogenen Aktivierungsablauf.

`HTMLElement.click()` erzeugt eine programmatisch ausgelöste Aktivierung beziehungsweise ein synthetisches `click`-Ereignis.

Das erzeugte Event besitzt nicht den Charakter eines echten Benutzerereignisses.

## Focus

Der Fokusmechanismus unterscheidet unter anderem:

- system focus
- user attention
- focused area
- focusable area
- sequentially focusable
- DOM anchor

Ein Element kann nur unter den jeweils normativ definierten Bedingungen eine Focusable Area darstellen.

Unter anderem spielen folgende Faktoren eine Rolle:

- `tabindex`
- Disabled State
- Inertness
- Rendering
- Shadow DOM
- Focus Delegation

## `tabindex`

`tabindex` beeinflusst die Fokusierbarkeit und die sequenzielle Fokusnavigation.

Die bloße Existenz eines `tabindex`-Attributes bedeutet nicht, dass jeder Wert dieselbe Fokuswirkung besitzt.

Das WHATWG-Modell unterscheidet insbesondere:

- negativen Wert
- Wert `0`
- positiven Wert

Die tatsächliche Sequential Focus Navigation wird durch das vollständige Fokusmodell bestimmt.

## `autofocus`

`autofocus` ist ein Boolean Attribute.

Es kennzeichnet ein Element als Kandidaten für automatisches Fokussieren.

Die tatsächliche Fokussierung unterliegt dem Autofocus- und Focus-Processing-Model.

Autofocus ist daher nicht gleichbedeutend mit der simplen Anweisung:

> Dieses Element erhält immer sofort den Fokus.

## Keyboard Shortcuts

`accesskey` ermöglicht es Autoren, einen Hinweis auf ein gewünschtes Tastaturkürzel bereitzustellen.

Der konkrete Shortcut wird nicht ausschließlich durch den Autor bestimmt.

Der User Agent kann:

- Tokens auswerten
- geeignete Tokens auswählen
- Modifier Keys berücksichtigen
- plattformspezifische Regeln anwenden

## Editing

`contenteditable` ist ein enumeriertes Attribut.

Aktuelle Zustände:

- True
- False
- Plaintext-Only
- Inherit

Keywords:

- `true`
- `false`
- `plaintext-only`

Der Missing Value Default und Invalid Value Default sind Inherit.

Der Empty Value Default ist True.

`plaintext-only` schränkt die Bearbeitung auf Rohtext ohne Rich-Text-Formatierung ein.

## `designMode`

`designMode` ist ein DOM-/Document-Konzept für die Bearbeitbarkeit eines gesamten Dokuments.

Es gehört damit zur Editing-API-Ebene und ist kein HTML-Element.

## Spelling und Grammar Checking

`spellcheck` steuert einen Hinweis beziehungsweise Zustand für Rechtschreib- und Grammatikprüfung.

Das Vorhandensein des Attributes bedeutet nicht, dass ein User Agent zwingend eine konkrete Prüfsoftware oder ein bestimmtes Wörterbuch verwenden muss.

Das Feature ist ein User-Agent-Verhaltenshinweis innerhalb des Editing-Modells.

## Writing Suggestions

`writingsuggestions` gehört zum Editing- und Input-Modality-Modell.

Es steuert, ob der User Agent Schreibvorschläge für entsprechende bearbeitbare Inhalte anbieten soll beziehungsweise darf.

## Autocapitalization

`autocapitalize` definiert Hinweise für die automatische Großschreibung.

Definierte Zustände umfassen:

- Default
- None
- Sentences
- Words
- Characters

Bekannte Keywords umfassen:

- `off`
- `none`
- `on`
- `sentences`
- `words`
- `characters`

Autocapitalization ist eine Eingabehilfe und keine Validierungsregel.

## Autocorrection

`autocorrect` steuert die Autokorrektur-Unterstützung im Editing-/Input-Kontext.

Definierte Keywords:

- `on`
- `off`

Das Feature kann durch den Kontext beeinflusst werden, beispielsweise durch:

- Form Owner
- Editing Host
- Elementtyp
- Input Type

## `inputmode`

`inputmode` ist ein enumeriertes Attribut.

Definierte Keywords:

- `none`
- `text`
- `tel`
- `url`
- `email`
- `numeric`
- `decimal`
- `search`

Das Attribut bestimmt die gewünschte Eingabemodalität.

Es ist keine Validierungsregel.

Insbesondere bestimmt `inputmode="numeric"` nicht automatisch, dass nur numerische Daten gültig sind.

## `enterkeyhint`

`enterkeyhint` ist ein enumeriertes Attribut.

Definierte Keywords:

- `enter`
- `done`
- `go`
- `next`
- `previous`
- `search`
- `send`

Das Attribut beschreibt, welche Aktion beziehungsweise welches Symbol für die Enter-Taste einer virtuellen Tastatur angezeigt werden soll.

## Find-in-page

Find-in-page ist ein User-Agent-Mechanismus zur Suche innerhalb des Seiteninhalts.

Der HTML-Standard beschreibt insbesondere:

- Query
- Matches
- Active Match
- Sichtbarmachung des aktiven Matches
- Interaktion mit `details`
- Interaktion mit `hidden=until-found`
- Interaktion mit Selection

Find-in-page ist nicht selbst ein HTML-Element.

## Close Requests

Ein Close Request beschreibt den Wunsch des Benutzers, eine aktuell angezeigte UI-Komponente zu schließen.

Beispiele können sein:

- Escape-Taste
- Zurück-Geste
- Plattform-spezifische Back-Aktion
- Assistive-Technology-Geste
- Game-Controller-Back-Aktion

Der konkrete Auslöser ist User-Agent- beziehungsweise plattformspezifisch.

## Close Watchers

Close Watchers ermöglichen es Webseiten, auf Close Requests zu reagieren.

Der Mechanismus besitzt bewusst Anti-Abuse-Regeln.

Insbesondere begrenzt der Close Watcher Manager die Anzahl unabhängig gruppierter Close Watchers abhängig von Benutzeraktivierung und History-Action Activation.

---

# Attribute

## Übersicht

Für diese Feature-Familie sind insbesondere folgende HTML-Attribute relevant:

| Attribut | Hauptbereich |
|---|---|
| `hidden` | Visibility / Find-in-page |
| `inert` | Inertness |
| `tabindex` | Focus |
| `autofocus` | Focus |
| `accesskey` | Keyboard Shortcuts |
| `contenteditable` | Editing |
| `spellcheck` | Editing |
| `writingsuggestions` | Editing |
| `autocapitalize` | Editing / Input |
| `autocorrect` | Editing / Input |
| `inputmode` | Input Modality |
| `enterkeyhint` | Input Modality |

Diese Attribute gehören teilweise gleichzeitig zu anderen Feature-Familien.

Insbesondere sind mehrere davon bereits in `13-global-attributes.md` als Global Attributes erfasst.

Die erneute Nennung hier ist eine fachliche Querverbindung und keine zusätzliche Attributdefinition.

---

# Content Categories

Die User-Interaction-Mechanismen definieren keine eigene Content Category im Sinne des allgemeinen HTML-Content-Category-Modells.

Relevante Beziehungen bestehen dennoch:

- `hidden` kann auf HTML-Elemente unabhängig von deren Content Category angewendet werden.
- `inert` kann auf HTML-Elemente und deren relevante Subtrees wirken.
- Fokusierbarkeit hängt von Elementtyp, Attributen und Processing Rules ab.
- Editing kann für unterschiedliche Elementtypen beziehungsweise Editing Hosts relevant sein.

Content Categories werden in `14-content-categories.md` behandelt.

---

# Context

User Interaction ist stark kontextabhängig.

Relevante Kontextdimensionen sind unter anderem:

- Dokument
- Window
- Navigable
- Top-Level Traversable
- Dialog
- Popover
- Shadow Tree
- Editing Host
- Form Owner
- Focus Scope
- Top Layer
- Flat Tree

Insbesondere bei Fokus, Autofocus, Inertness und User Activation kann derselbe DOM-Knoten je nach Kontext unterschiedlich verarbeitet werden.

---

# Content Model

User Interaction besitzt kein eigenes allgemeines Content Model.

Stattdessen greifen die beschriebenen Mechanismen auf die Content Models und Elementdefinitionen anderer Bereiche zurück.

Beispiele:

- `hidden` kann Elemente unabhängig von deren konkretem Content Model betreffen.
- `inert` betrifft DOM-Subtrees.
- `contenteditable` betrifft Editing Hosts.
- Focus Processing berücksichtigt Elementtyp und Rendering.
- Find-in-page verarbeitet vorhandenen Dokumentinhalt.

Content Models sind daher eine separate Informationsebene.

---

# Processing Models

## Hidden State

Das Processing Model von `hidden` unterscheidet insbesondere:

- Hidden
- Hidden Until Found
- Not Hidden

Beim Hidden Until Found State existiert ein spezieller Offenlegungsmechanismus.

## Ancestor Revealing Algorithm

Der Ancestor Revealing Algorithm verarbeitet unter anderem:

- `hidden=until-found`
- geschlossene `details`
- Zielknoten einer Suche oder Fragmentnavigation

Der Algorithmus kann:

- `beforematch` auslösen
- `hidden` entfernen
- `details` öffnen

Der Ablauf erfolgt entlang des Flat Tree.

## Visibility Processing

Beim Wechsel des System Visibility State wird der Visibility State betroffener Documents aktualisiert.

Dabei werden unter anderem:

- Visibility State
- Visibility State Entries
- `visibilitychange`

aktualisiert beziehungsweise ausgelöst.

## Inertness Processing

Inertness wird nicht lediglich durch einen CSS-Wert definiert.

Die Verarbeitung beeinflusst mehrere Interaktionssysteme:

- Pointer-/Hit Testing
- Selection
- Editing
- Find-in-page
- Focus
- Accessibility Exposure

## User Activation Processing

Das User-Activation-Modell verwendet Zeitstempel und Zustände.

Wesentliche Vorgänge sind:

- Activation Notification
- Sticky Activation
- Transient Activation
- Consumption
- History-Action Activation

## Activation Processing

Bei Elementaktivierung wird ein Aktivierungsablauf ausgeführt.

`click()` verwendet dabei ein Click-in-Progress-Flag, um rekursive beziehungsweise doppelte Aktivierungsverarbeitung zu vermeiden.

## Focus Processing

Die Fokusverarbeitung umfasst unter anderem:

1. Ermittlung einer Focusable Area
2. Berücksichtigung von Shadow DOM
3. Berücksichtigung von Inertness
4. Berücksichtigung von Disabled State
5. Berücksichtigung von Rendering
6. Ermittlung des Fokusziels
7. Fokuswechsel
8. Aktualisierung von `activeElement`

## Sequential Focus Navigation

Die sequenzielle Fokusnavigation ist ein eigenes Processing Model.

`tabindex` liefert dafür einen wichtigen Input, ersetzt aber nicht die vollständige Navigation Rules.

## Editing Processing

Editing berücksichtigt insbesondere:

- Editing Host
- `contenteditable`
- `designMode`
- Vererbung des Editierstatus
- Plaintext-Only
- Input Modality
- Spellchecking
- Writing Suggestions
- Autocapitalization
- Autocorrection

## Find-in-page Processing

Find-in-page arbeitet mit:

- Suchquery
- Matches
- Active Match
- Scroll-to-match
- Hidden Until Found
- `details`
- Selection

Die Offenlegung von `hidden=until-found` wird dabei über das bestehende Ancestor Revealing Model integriert.

## Close Request Processing

Close Requests werden zunächst vom User Agent verarbeitet.

Die Verarbeitung berücksichtigt unter anderem:

- Fullscreen
- relevante UI-Zustände
- Close Watchers
- History Action Activation
- Fallback Action

Close Watchers dürfen den Schließvorgang unter bestimmten Bedingungen abbrechen.

---

# DOM Interfaces / APIs

## `Document`

Im Bereich User Interaction sind insbesondere folgende Konzepte relevant:

- `Document.visibilityState`
- `Document.hidden`
- `Document.hasFocus()`
- `DocumentOrShadowRoot.activeElement`

## `VisibilityStateEntry`

`VisibilityStateEntry` erweitert `PerformanceEntry`.

Relevante exponierte Informationen:

- `name`
- `entryType`
- `startTime`
- `duration`

Das Interface repräsentiert Visibility-State-Änderungen innerhalb des Performance-Modells.

## `UserActivation`

Das WHATWG-Modell definiert das Interface `UserActivation`.

Relevante IDL-Eigenschaften:

- `hasBeenActive`
- `isActive`

`hasBeenActive` repräsentiert Sticky Activation.

`isActive` repräsentiert Transient Activation.

## `navigator.userActivation`

Das UserActivation-Modell ist über den Navigator-Kontext zugänglich.

Die API darf nicht mit einem beliebigen DOM-Event verwechselt werden.

## `HTMLElement.click()`

`click()` löst den definierten programmatischen Aktivierungsmechanismus aus.

Bei einem deaktivierten Form Control wird die Aktivierung nicht durchgeführt.

Das Click-in-Progress-Flag verhindert verschachtelte beziehungsweise rekursive `click()`-Verarbeitung.

## `HTMLElement.focus()`

`focus()` verschiebt den Fokus auf das Element.

Relevante Optionen umfassen:

- `preventScroll`
- `focusVisible`

Mit `preventScroll` kann das automatische Scrollen zum fokussierten Element unterdrückt werden.

## `HTMLElement.blur()`

`blur()` entfernt den Fokus vom betreffenden Element beziehungsweise führt die entsprechende Fokusverarbeitung aus.

Der Einsatz zum bloßen Unterdrücken einer sichtbaren Fokusmarkierung ist nicht als allgemeine Accessibility-Lösung vorgesehen.

## `Document.hasFocus()`

`Document.hasFocus()` liefert einen Boolean, der angibt, ob der Document-Kontext nach dem definierten Fokusmodell fokussiert ist.

## `Window.focus()`

`Window.focus()` versucht, den Fokus auf das entsprechende Window beziehungsweise Navigable zu setzen.

Die konkrete Wirksamkeit kann von User-Agent- und Plattformregeln abhängen.

## `ElementContentEditable`

`ElementContentEditable` ist ein DOM Interface Mixin.

Es stellt unter anderem bereit:

- `contentEditable`
- `enterKeyHint`
- `isContentEditable`
- `inputMode`

## `CloseWatcher`

`CloseWatcher` ist ein Window-exponiertes Interface.

IDL-Konzeptuell umfasst es:

- Konstruktor
- `requestClose()`
- `close()`
- `destroy()`
- `oncancel`
- `onclose`

Der Konstruktor kann ein `AbortSignal` über `CloseWatcherOptions` erhalten.

### `requestClose()`

`requestClose()` verhält sich wie eine Close Request an den betreffenden Close Watcher.

Der Mechanismus erlaubt insbesondere:

1. `cancel` Event
2. Prüfung von `preventDefault()`
3. gegebenenfalls `close` Event
4. Deaktivierung des Close Watchers

### `close()`

`close()` führt die Close-Verarbeitung unmittelbar aus und überspringt die normale Cancel-Entscheidung.

### `destroy()`

`destroy()` deaktiviert den Close Watcher.

Danach nimmt er nicht mehr an Close Requests teil.

---

# Events

## `visibilitychange`

Bei einer Änderung des Document Visibility State wird ein `visibilitychange` Event ausgelöst.

Das Event wird auf dem betreffenden `Document` ausgelöst und ist Bestandteil des Page-Visibility-Modells.

## `beforematch`

`beforematch` ist mit dem Ancestor Revealing Algorithm verbunden.

Es wird ausgelöst, bevor ein `hidden=until-found`-Bereich im Rahmen der Offenlegung sichtbar gemacht wird.

## `click`

`click` ist das zentrale Event des Activation Behavior.

Nicht jede Auslösung eines `click`-Events entspricht jedoch einer echten Benutzerinteraktion.

Insbesondere ist ein programmatisch erzeugtes `click()`-Ergebnis kein Trusted User Input.

## `toggle`

Das `toggle`-Event kann unter anderem im Zusammenhang mit `details` und anderen Toggle-Mechanismen auftreten.

Im User-Interaction-Kontext ist insbesondere die Interaktion mit Find-in-page relevant.

## `cancel` und `close`

`CloseWatcher` definiert:

- `cancel`
- `close`

`cancel` ermöglicht die Verhinderung eines Schließvorgangs, soweit das konkrete Close-Processing dies erlaubt.

`close` signalisiert den tatsächlich ausgeführten Schließvorgang.

---

# Accessibility

Accessibility-relevante Aussagen müssen von den normativen HTML-Regeln getrennt betrachtet werden.

Der HTML-Standard definiert im User-Interaction-Kontext jedoch konkrete Verhaltensregeln mit unmittelbaren Accessibility-Auswirkungen.

## Inertness

Inert Nodes werden grundsätzlich nicht normal für Accessibility APIs beziehungsweise assistive technologies exponiert.

Daher kann `inert` Inhalte für Nutzer assistiver Technologien ebenso unzugänglich machen wie für direkte Interaktion.

## `hidden`

Der Hidden State ist nicht lediglich eine visuelle Darstellung.

Autoren dürfen `hidden` nicht verwenden, wenn Inhalte lediglich für eine bestimmte Präsentationsform verborgen werden sollen.

## Fokus

Ein korrekter Fokuszustand ist ein wesentlicher Bestandteil der Tastaturbedienbarkeit.

Die Fokusregeln berücksichtigen insbesondere:

- Inertness
- Disabled State
- Rendering
- Shadow DOM
- Sequential Focus Navigation

## `blur()`

Der Standard warnt ausdrücklich davor, `blur()` lediglich zum Entfernen eines Fokusindikators einzusetzen.

Wenn der Fokusindikator visuell angepasst wird, muss weiterhin eine verständliche Fokusdarstellung vorhanden sein.

## `inputmode`

`inputmode` ist keine Validierungsregel.

Accessibility- und Usability-Entscheidungen dürfen daher nicht daraus ableiten, dass ein bestimmtes Eingabeformat technisch erzwungen wird.

---

# Sanitization

Die User-Interaction-Features definieren keine allgemeine Sanitization-Policy.

Insbesondere sind:

- `hidden`
- `inert`
- `tabindex`
- `autofocus`
- `accesskey`
- `contenteditable`
- `spellcheck`
- `inputmode`
- `enterkeyhint`

keine Sanitization-Mechanismen.

Sanitization wird als eigenständige Feature-Familie in `20-sanitization.md` behandelt.

Für User Interaction relevante DOM- oder Event-Verarbeitung darf daher nicht mit HTML Sanitization gleichgesetzt werden.

---

# Konformitätsregeln

## `hidden`

Autoren dürfen `hidden` nicht verwenden, um Inhalte nur aus einer bestimmten Präsentationsform zu entfernen.

Insbesondere ist `hidden` nicht als Ersatz für ein UI-Tab- oder Overflow-Modell gedacht.

## Referenzen auf Hidden Content

Nicht verborgene Elemente sollen nicht über normale Hyperlinks auf verborgene Elemente verweisen.

Ebenso sollen bestimmte `for`-Referenzen nicht von nicht verborgenen Controls auf verborgene Ziele zeigen.

Es gibt jedoch ausdrücklich zulässige technische Referenzen, beispielsweise bestimmte Accessibility-Referenzen oder interne Verarbeitung.

## `inert`

Autoren sollen keine Inhalte inert machen, die für das Verständnis oder die Bedienung des nicht inaktiven Teils der Seite erforderlich sind.

Ein inert Bereich sollte normalerweise auch visuell als nicht aktiv erkennbar sein.

## `accesskey`

Die Verwendung von `accesskey` darf nicht als Garantie für eine bestimmte Tastenkombination verstanden werden.

Die konkrete Kombination wird vom User Agent beziehungsweise der Plattform bestimmt.

## `autofocus`

`autofocus` muss im Kontext des vollständigen Fokus- und Autofocus-Modells bewertet werden.

Es ist keine Garantie dafür, dass ein Element unter allen Umständen Fokus erhält.

## `contenteditable`

`contenteditable` bestimmt Editierbarkeit.

Es stellt jedoch kein vollständiges Rich-Text-Editor-Framework bereit.

Komplexe Editor-Funktionen erfordern zusätzliche DOM-/Editing-APIs.

## `inputmode`

`inputmode` liefert einen Input-Hint.

Es ersetzt weder:

- serverseitige Validierung
- Client-seitige Validierung
- `type`
- `pattern`
- sonstige Form Constraints

## `enterkeyhint`

`enterkeyhint` beeinflusst die Darstellung beziehungsweise Semantik der Enter-Aktion einer virtuellen Tastatur.

Es stellt keine eigene Form Submission Rule dar.

## Close Watchers

Close Watchers unterliegen Anti-Abuse-Regeln.

Ein Dokument darf den Close-Mechanismus nicht unbegrenzt blockieren.

Die Fähigkeit, Close Requests zu verhindern, wird insbesondere mit User Activation und History-Action Activation gekoppelt.

---

# Status / V1

## WHATWG-Status

Die hier dokumentierten Konzepte sind Bestandteil der aktuellen WHATWG HTML Living Standard.

Dazu zählen sowohl:

- Attribute
- DOM Interfaces
- APIs
- Zustandsmodelle
- Processing Models
- normative Algorithmen
- Event-Verarbeitung
- Konformitätsanforderungen

## Nicht als HTML-Elemente definierte Konzepte

Folgende Einträge sind ausdrücklich keine HTML-Elemente:

- User Activation
- Sticky Activation
- Transient Activation
- Focusable Area
- Activation Behavior
- Find-in-page
- Close Request
- Close Watcher
- Page Visibility Processing
- Inertness Model
- Sequential Focus Navigation

## V1

Die V1-Zuordnung des ZE-WebLab ist eine projektspezifische Klassifikation.

Sie darf nicht mit dem WHATWG-Status gleichgesetzt werden.

Für diese Datei gilt daher:

- **WHATWG:** definiert
- **ZE-WebLab-V1:** Feature-Familie der Rechercheebene 2
- **Browser-Support:** separat zu recherchieren

---

# Querverweise

## Global Attributes

Direkter Bezug zu:

- `hidden`
- `inert`
- `tabindex`
- `autofocus`
- `accesskey`
- `contenteditable`
- `spellcheck`
- `writingsuggestions`
- `autocapitalize`
- `autocorrect`
- `inputmode`
- `enterkeyhint`

Siehe:

`docs/html/13-global-attributes.md`

## Content Categories

Die User-Interaction-Features operieren auf Elementen und DOM-Strukturen, verwenden aber kein eigenes Content-Category-System.

Siehe:

`docs/html/14-content-categories.md`

## Content Models

User Interaction kann auf DOM-Subtrees und Elementinhalte wirken, definiert aber kein neues allgemeines Content Model.

Siehe:

`docs/html/15-content-models.md`

## Link Types

User Interaction und Link Processing überschneiden sich insbesondere bei:

- Fragment Navigation
- Find-in-page
- Aktivierung von Links
- User Activation

Die Link-Type-Systematik bleibt in:

`docs/html/16-link-types.md`

## DOM Interfaces / APIs

User Interaction verwendet zahlreiche DOM Interfaces.

Siehe:

`docs/html/17-apis-dom-interfaces.md`

## Processing Models

Die hier beschriebenen Algorithmen sind zugleich konkrete Beispiele für die übergreifende Processing-Model-Ebene.

Siehe:

`docs/html/18-processing-models.md`

## Parsing

Parsing ist für die hier beschriebenen Zustände nicht die zentrale Definitionsquelle.

Spezielle Parsing-Interaktionen werden separat behandelt.

Siehe:

`docs/html/19-parsing.md`

## Sanitization

User Interaction definiert keine allgemeine Sanitization.

Siehe:

`docs/html/20-sanitization.md`

## Custom Elements

User Interaction kann auch bei Custom Elements relevant sein.

Insbesondere können:

- Fokus
- Aktivierung
- `inert`
- globale Attribute
- Editing

auf Custom Elements beziehungsweise deren DOM-Strukturen wirken.

Siehe:

`docs/html/21-custom-elements.md`

## SVG und MathML

Die in §6 beschriebenen Interaktionsmodelle können mit Elementen anderer Namespaces interagieren.

Die Namespace- und Foreign-Content-Regeln sind jedoch separat definiert.

Siehe:

`docs/html/22-svg-mathml-integration.md`

## Microdata

Microdata verwendet mehrere Global Attributes, insbesondere:

- `itemscope`
- `itemtype`
- `itemid`
- `itemprop`
- `itemref`

Diese Attribute gehören funktional zum Microdata-Modell.

Siehe:

`docs/html/23-microdata.md`

---

# Feature-Abgrenzung

## Bereits anderweitig vollständig als eigene Familie behandelt

Nicht erneut als eigenständige User-Interaction-Features zu modellieren sind:

- Global-Attribute-Inventar
- Content Categories
- Content Models
- Link Types
- allgemeines DOM-API-Inventar
- allgemeine Processing Models
- Parsing
- Sanitization
- Custom Elements
- SVG-/MathML-Integration
- Microdata

Diese Datei dokumentiert lediglich deren User-Interaction-Beziehungen.

## Nicht Bestandteil dieser Datei

### Drag and drop

WHATWG §6.11 `Drag and drop` wird nicht in diese Datei aufgenommen.

Der Bereich besitzt ein eigenständiges:

- Drag-and-Drop-Modell
- Drag Data Store
- DataTransfer-Modell
- Event-Modell
- Processing Model
- DOM/API-Modell

Das Feature sollte als eigenständige spätere Feature-Familie recherchiert werden.

### Fullscreen

Fullscreen ist eine separate Spezifikation.

§6 verweist auf Fullscreen insbesondere im Zusammenhang mit Close Requests.

Fullscreen wird deshalb nicht als HTML-User-Interaction-Feature in diese Datei integriert.

### Pointer Events

Pointer Events sind in einer separaten Spezifikation definiert.

§6 verwendet Pointer-/Hit-Testing-Konzepte, definiert aber nicht das vollständige Pointer-Events-Modell.

### Selection API

Selection ist ein extern beziehungsweise separat spezifiziertes DOM-Feature.

HTML referenziert Selection insbesondere bei Editing, Focus und Find-in-page.

### UI Events

UI Events definieren Ereignisse wie `click`, `keydown` und verwandte Event-Verarbeitung.

Die HTML-Activation-Regeln referenzieren diese Mechanismen, ersetzen aber nicht die UI-Events-Spezifikation.

---

# Detailprüfung

## UI-001 – `hidden`

- **Feature-Typ:** Attribute / Processing Model
- **WHATWG:** §6.1
- **Global Attribute:** Ja
- **Wertmodell:** Enumerated Attribute
- **States:** Hidden, Hidden Until Found, Not Hidden
- **DOM:** `HTMLElement.hidden`
- **Querverweise:** Find-in-page, Fragment Navigation, `details`, Rendering

### Prüfstatus

Vollständig geprüft.

---

## UI-002 – Hidden Until Found

- **Feature-Typ:** Attribute State / Processing Model
- **WHATWG:** §6.1
- **Keyword:** `until-found`
- **Funktion:** Inhalt bleibt für Find-in-page und Fragment Navigation auffindbar.
- **Verarbeitung:** Ancestor Revealing Algorithm
- **Event:** `beforematch`

### Prüfstatus

Vollständig geprüft.

---

## UI-004 – Page visibility

- **Feature-Typ:** Processing Model / DOM
- **WHATWG:** §6.2
- **Document State:** `visible` / `hidden`
- **DOM:** `Document.visibilityState`, `Document.hidden`
- **Event:** `visibilitychange`

### Prüfstatus

Vollständig geprüft.

---

## UI-005 – `VisibilityStateEntry`

- **Feature-Typ:** DOM Interface
- **WHATWG:** §6.2.1
- **Basiskonzept:** Performance Entry
- **Werte:** Visibility State und Timestamp
- **IDL:** `name`, `entryType`, `startTime`, `duration`

### Prüfstatus

Vollständig geprüft.

---

## UI-006 – Inert subtrees

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.3
- **Wirkung:** Interaktion mit einem Node beziehungsweise Subtree wird eingeschränkt.
- **Betroffene Systeme:** Hit Testing, Selection, Editing, Find-in-page, Focus, Accessibility

### Prüfstatus

Vollständig geprüft.

---

## UI-007 – `inert`

- **Feature-Typ:** Global Attribute / Processing Model
- **WHATWG:** §6.3.2
- **Wertmodell:** Boolean Attribute
- **Wirkung:** Element und relevante Flat-Tree-Descendants werden inert.

### Prüfstatus

Vollständig geprüft.

---

## UI-009 – User Activation

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.4
- **States:** Sticky Activation, Transient Activation
- **Zweck:** Missbrauchsschutz für bestimmte APIs

### Prüfstatus

Vollständig geprüft.

---

## UI-014 – `UserActivation`

- **Feature-Typ:** DOM Interface
- **WHATWG:** §6.4.4
- **IDL:** `hasBeenActive`, `isActive`

### Prüfstatus

Vollständig geprüft.

---

## UI-015 – Activation behavior

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.5
- **Zentraler Mechanismus:** `click`
- **API-Bezug:** `HTMLElement.click()`

### Prüfstatus

Vollständig geprüft.

---

## UI-017 – `ToggleEvent`

- **Feature-Typ:** DOM Interface
- **WHATWG:** §6.5.1
- **Bezug:** Toggle-basierte Interaktionsmechanismen

### Prüfstatus

Vollständig geprüft.

---

## UI-018 – `CommandEvent`

- **Feature-Typ:** DOM Interface
- **WHATWG:** §6.5.2
- **Bezug:** Command-/Activation-Modell

### Prüfstatus

Vollständig geprüft.

---

## UI-019 – Focus

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.6
- **Kernkonzepte:** Focusable Area, Focus Target, DOM Anchor
- **Querverweise:** `tabindex`, `autofocus`, Shadow DOM, Inertness

### Prüfstatus

Vollständig geprüft.

---

## UI-021 – `tabindex`

- **Feature-Typ:** Attribute / Focus
- **WHATWG:** §6.6.3
- **Wirkung:** Fokusierbarkeit und Sequential Focus Navigation

### Prüfstatus

Vollständig geprüft.

---

## UI-023 – Focus management APIs

- **Feature-Typ:** DOM/API
- **WHATWG:** §6.6.6
- **APIs:** `focus()`, `blur()`, `activeElement`, `hasFocus()`, `Window.focus()`

### Prüfstatus

Vollständig geprüft.

---

## UI-024 – `autofocus`

- **Feature-Typ:** Attribute / Processing Model
- **WHATWG:** §6.6.7
- **Wertmodell:** Boolean Attribute
- **Bezug:** Autofocus Candidate / Focus Processing

### Prüfstatus

Vollständig geprüft.

---

## UI-026 – `accesskey`

- **Feature-Typ:** Attribute / Processing Model
- **WHATWG:** §6.7.2
- **Wertmodell:** whitespace-separierte Ein-Zeichen-Tokens
- **Processing:** User-Agent-Auswahl

### Prüfstatus

Vollständig geprüft.

---

## UI-028 – `contenteditable`

- **Feature-Typ:** Attribute / Editing
- **WHATWG:** §6.8.1
- **States:** True, False, Plaintext-Only, Inherit
- **DOM:** `ElementContentEditable`

### Prüfstatus

Vollständig geprüft.

---

## UI-029 – `designMode`

- **Feature-Typ:** DOM/API
- **WHATWG:** §6.8.2
- **Scope:** gesamtes Document

### Prüfstatus

Vollständig geprüft.

---

## UI-031 – `spellcheck`

- **Feature-Typ:** Attribute / Editing
- **WHATWG:** §6.8.5
- **Zweck:** Rechtschreib- und Grammatikprüfung

### Prüfstatus

Vollständig geprüft.

---

## UI-033 – `writingsuggestions`

- **Feature-Typ:** Attribute / Editing
- **WHATWG:** §6.8.6
- **Zweck:** Schreibvorschläge

### Prüfstatus

Vollständig geprüft.

---

## UI-035 – `autocapitalize`

- **Feature-Typ:** Attribute / Input Modality
- **WHATWG:** §6.8.7
- **States:** Default, None, Sentences, Words, Characters

### Prüfstatus

Vollständig geprüft.

---

## UI-037 – `autocorrect`

- **Feature-Typ:** Attribute / Input Modality
- **WHATWG:** §6.8.8
- **States:** On, Off

### Prüfstatus

Vollständig geprüft.

---

## UI-039 – `inputmode`

- **Feature-Typ:** Attribute / Input Modality
- **WHATWG:** §6.8.9
- **Keywords:** `none`, `text`, `tel`, `url`, `email`, `numeric`, `decimal`, `search`

### Prüfstatus

Vollständig geprüft.

---

## UI-040 – `enterkeyhint`

- **Feature-Typ:** Attribute / Input Modality
- **WHATWG:** §6.8.10
- **Keywords:** `enter`, `done`, `go`, `next`, `previous`, `search`, `send`

### Prüfstatus

Vollständig geprüft.

---

## UI-042 – Find-in-page

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.9
- **Bezug:** Active Match, Selection, `details`, `hidden=until-found`

### Prüfstatus

Vollständig geprüft.

---

## UI-045 – Close requests

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.10.1
- **Beispiele:** Escape, Back, Assistive Technology Dismiss, Game Controller Back
- **Querverweise:** Fullscreen, Popover, Dialog, History Action Activation

### Prüfstatus

Vollständig geprüft.

---

## UI-046 – Close watcher infrastructure

- **Feature-Typ:** Processing Model
- **WHATWG:** §6.10.2
- **Bestandteile:** Manager, Groups, Allowed Number of Groups, Close Watchers
- **Schutzmechanismus:** User-Activation-basierte Begrenzung

### Prüfstatus

Vollständig geprüft.

---

## UI-047 – `CloseWatcher`

- **Feature-Typ:** DOM/API
- **WHATWG:** §6.10.3
- **Methoden:** `requestClose()`, `close()`, `destroy()`
- **Events:** `cancel`, `close`
- **Option:** `AbortSignal`

### Prüfstatus

Vollständig geprüft.

---

# Feature-Familien außerhalb des Scopes

Die aktuelle WHATWG-Struktur enthält nach §6.10 unmittelbar:

## §6.11 Drag and drop

Dieser Bereich ist fachlich eigenständig.

Er sollte in einer separaten Datei behandelt werden.

Voraussichtliche Schwerpunkte:

- Drag and Drop
- Drag Data Store
- `DataTransfer`
- `DataTransferItem`
- `DataTransferItemList`
- Drag Events
- `dragstart`
- `drag`
- `dragenter`
- `dragover`
- `dragleave`
- `drop`
- `dragend`
- Drag Data Store Modes
- DataTransfer Types
- User-Agent-Drag-Verarbeitung

Diese Punkte werden hier nicht als Teil der abgeschlossenen §6.1–§6.10-Recherche dokumentiert.

---

# Querverweis-Matrix

| User-Interaction-Feature | Relevante andere Feature-Familie |
|---|---|
| `hidden` | Global Attributes |
| `hidden=until-found` | Find-in-page |
| `hidden=until-found` | Fragment Navigation |
| `inert` | Global Attributes |
| `inert` | Dialog |
| `inert` | Accessibility |
| User Activation | APIs |
| User Activation | Popover |
| User Activation | Fullscreen |
| Activation Behavior | DOM Events |
| Focus | `tabindex` |
| Focus | `autofocus` |
| Focus | Shadow DOM |
| Focus | Inertness |
| `accesskey` | Keyboard Interaction |
| `contenteditable` | Editing |
| `spellcheck` | Editing |
| `writingsuggestions` | Editing |
| `autocapitalize` | Input Modality |
| `autocorrect` | Input Modality |
| `inputmode` | Forms |
| `enterkeyhint` | Forms |
| Find-in-page | `hidden=until-found` |
| Find-in-page | `details` |
| Close Request | Dialog |
| Close Request | Popover |
| Close Request | Fullscreen |
| CloseWatcher | User Activation |
| CloseWatcher | History Action Activation |

---

# Offene Punkte

## Keine offenen Punkte innerhalb des abgegrenzten WHATWG-Bereichs

Für §6.1 bis §6.10 wurden die aktuellen WHATWG-Unterabschnitte geprüft.

Es verbleibt innerhalb dieser Abgrenzung kein fachlicher Punkt, der für die Referenzdokumentation als ungeklärt bezeichnet werden muss.

## Bewusst nicht abgeschlossen

### §6.11 Drag and drop

Der Abschnitt wurde als eigenständige Feature-Familie abgegrenzt und ist nicht Bestandteil dieser Datei.

### Externe Spezifikationen

Folgende externe Spezifikationsbereiche werden vom HTML-Standard referenziert, sind aber nicht vollständig in HTML definiert:

- DOM
- UI Events
- Selection
- Pointer Events
- CSS Containment
- Fullscreen
- WebDriver
- Performance Timeline
- weitere jeweils referenzierte Standards

Diese werden nur insoweit berücksichtigt, wie HTML auf sie verweist.

### Browser-Kompatibilität

Browser-Support wurde nicht als WHATWG-Status bewertet und ist nicht Bestandteil dieser Datei.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard**

Maßgeblicher Bereich:

- §6 User interaction
- §6.1 The `hidden` attribute
- §6.2 Page visibility
- §6.2.1 The `VisibilityStateEntry` interface
- §6.3 Inert subtrees
- §6.3.1 Modal dialogs and inert subtrees
- §6.3.2 The `inert` attribute
- §6.4 Tracking user activation
- §6.4.1 Data model
- §6.4.2 Processing model
- §6.4.3 APIs gated by user activation
- §6.4.4 The `UserActivation` interface
- §6.4.5 User agent automation
- §6.5 Activation behavior of elements
- §6.5.1 The `ToggleEvent` interface
- §6.5.2 The `CommandEvent` interface
- §6.6 Focus
- §6.6.1 Introduction
- §6.6.2 Data model
- §6.6.3 The `tabindex` attribute
- §6.6.4 Processing model
- §6.6.5 Sequential focus navigation
- §6.6.6 Focus management APIs
- §6.6.7 The `autofocus` attribute
- §6.7 Assigning keyboard shortcuts
- §6.7.1 Introduction
- §6.7.2 The `accesskey` attribute
- §6.7.3 Processing model
- §6.8 Editing
- §6.8.1 Making document regions editable
- §6.8.2 Making entire documents editable
- §6.8.3 Best practices for in-page editors
- §6.8.4 Editing APIs
- §6.8.5 Spelling and grammar checking
- §6.8.6 Writing suggestions
- §6.8.7 Autocapitalization
- §6.8.8 Autocorrection
- §6.8.9 Input modalities: the `inputmode` attribute
- §6.8.10 Input modalities: the `enterkeyhint` attribute
- §6.9 Find-in-page
- §6.9.1 Introduction
- §6.9.2 Interaction with `details` and `hidden=until-found`
- §6.9.3 Interaction with selection
- §6.10 Close requests and close watchers
- §6.10.1 Close requests
- §6.10.2 Close watcher infrastructure
- §6.10.3 The `CloseWatcher` interface

## Projektquelle

ZE-WebLab Repository:

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
- `docs/html/17-apis-dom-interfaces.md`
- `docs/html/18-processing-models.md`
- `docs/html/19-parsing.md`
- `docs/html/20-sanitization.md`
- `docs/html/21-custom-elements.md`
- `docs/html/22-svg-mathml-integration.md`
- `docs/html/23-microdata.md`

---

# Prüfabschluss

- **Feature-Familie:** User Interaction
- **Zieldatei:** `docs/html/24-user-interaction.md`
- **WHATWG-Hauptbereich:** §6.1–§6.10
- **Rechercheabschluss:** vollständig für den abgegrenzten Bereich
- **§6.11 Drag and drop:** bewusst separat offen
- **Elementinventar:** nicht erweitert
- **Attribute:** als Attribute dokumentiert, nicht als Elemente
- **DOM Interfaces:** getrennt von HTML-Elementen dokumentiert
- **Processing Models:** als normative Konzepte behandelt
- **Browser-Support:** nicht Bestandteil der Statusbewertung
- **V1:** getrennt vom WHATWG-Status