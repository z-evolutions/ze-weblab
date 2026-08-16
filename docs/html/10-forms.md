# ZE-WebLab – HTML-Referenz: Forms

## Arbeitsstand / Quellenstand

**Dokument:** `docs/html/10-forms.md`

**Themenbereich:** WHATWG HTML Living Standard – §4.10 Forms

**Recherchebasis:** aktuelle WHATWG HTML Living Standard.

**Geprüfter Spezifikationsstand:** Living Standard, Stand der Recherche August 2026.

**Primärquelle:** WHATWG HTML Living Standard, §4.10 „Forms“.

**Status der Recherche:** abgeschlossen.

Diese Datei dokumentiert §4.10 der WHATWG-Spezifikation auf Feature-Ebene.

Dabei werden bewusst getrennt:

- HTML-Elemente
- `input`-States des `type`-Attributs
- elementbezogene Attribute
- gemeinsame Form-Control-Attribute
- DOM Interfaces
- Form-Control-Infrastruktur
- Constraint Validation
- Form Submission
- APIs
- normative Processing Models
- Accessibility-Informationen
- Sanitization-Informationen

Die Unterabschnitte der WHATWG-Spezifikation werden nicht automatisch als zusätzliche HTML-Elemente gezählt.

Insbesondere sind beispielsweise:

- `input`-States keine zusätzlichen HTML-Elemente
- Constraint Validation keine HTML-Elemente
- Form Submission kein HTML-Element
- Form-Control-Infrastruktur kein HTML-Element
- Autofill kein HTML-Element
- Text-Control-Selection-APIs keine HTML-Elemente
- `SubmitEvent` und `FormDataEvent` keine HTML-Elemente

---

## WHATWG-Struktur

Der aktuelle WHATWG-Bereich §4.10 ist wie folgt gegliedert:

### 4.10.1 Introduction

- 4.10.1.1 Writing a form's user interface
- 4.10.1.2 Implementing the server-side processing for a form
- 4.10.1.3 Configuring a form to communicate with the server
- 4.10.1.4 Client-side form validation
- 4.10.1.5 Enabling client-side automatic filling of form controls
- 4.10.1.6 Improving the user experience on mobile devices
- 4.10.1.7 The difference between the field type, the autofill field name, and the input modality
- 4.10.1.8 Date, time, and number formats

### 4.10.2 Categories

- Form-associated elements
- Listed elements
- Submittable elements
- Resettable elements
- Autocapitalize-and-autocorrect-inheriting elements
- Labelable elements

### 4.10.3–4.10.17 Elementdefinitionen

- 4.10.3 `form`
- 4.10.4 `label`
- 4.10.5 `input`
- 4.10.6 `button`
- 4.10.7 `select`
- 4.10.8 `datalist`
- 4.10.9 `optgroup`
- 4.10.10 `option`
- 4.10.11 `textarea`
- 4.10.12 `output`
- 4.10.13 `progress`
- 4.10.14 `meter`
- 4.10.15 `fieldset`
- 4.10.16 `legend`
- 4.10.17 `selectedcontent`

### 4.10.18 Form control infrastructure

- 4.10.18.1 A form control's value
- 4.10.18.2 Mutability
- 4.10.18.3 Association of controls and forms

### 4.10.19 Attributes common to form controls

- `name`
- `dirname`
- `maxlength`
- `minlength`
- `disabled`
- Form submission attributes
- `autocomplete`
- Autofill processing model

### 4.10.20 APIs for the text control selections

### 4.10.21 Constraints

- Definitions
- Constraint validation
- Constraint validation API
- Security

### 4.10.22 Form submission

- Introduction
- Implicit submission
- Form submission algorithm
- Constructing the entry list
- Selecting a form submission encoding
- Converting an entry list to name-value pairs
- URL-encoded form data
- Multipart form data
- Plain text form data
- `SubmitEvent`
- `FormDataEvent`

### 4.10.23 Resetting a form

Die WHATWG-Struktur bestätigt damit, dass §4.10 wesentlich mehr als eine reine Elementliste enthält.

---

# Inventar

## HTML-Elemente

| Feature | WHATWG-Abschnitt | Feature-Typ | Status |
|---|---|---|---|
| `form` | §4.10.3 | HTML-Element | im WHATWG-Standard definiert |
| `label` | §4.10.4 | HTML-Element | im WHATWG-Standard definiert |
| `input` | §4.10.5 | HTML-Element | im WHATWG-Standard definiert |
| `button` | §4.10.6 | HTML-Element | im WHATWG-Standard definiert |
| `select` | §4.10.7 | HTML-Element | im WHATWG-Standard definiert |
| `datalist` | §4.10.8 | HTML-Element | im WHATWG-Standard definiert |
| `optgroup` | §4.10.9 | HTML-Element | im WHATWG-Standard definiert |
| `option` | §4.10.10 | HTML-Element | im WHATWG-Standard definiert |
| `textarea` | §4.10.11 | HTML-Element | im WHATWG-Standard definiert |
| `output` | §4.10.12 | HTML-Element | im WHATWG-Standard definiert |
| `progress` | §4.10.13 | HTML-Element | im WHATWG-Standard definiert |
| `meter` | §4.10.14 | HTML-Element | im WHATWG-Standard definiert |
| `fieldset` | §4.10.15 | HTML-Element | im WHATWG-Standard definiert |
| `legend` | §4.10.16 | HTML-Element | im WHATWG-Standard definiert |
| `selectedcontent` | §4.10.17 | HTML-Element | im WHATWG-Standard definiert |

## `input`-States

`input` bleibt ein einziges HTML-Element. Die folgenden Zustände werden deshalb nicht als zusätzliche Elemente gezählt.

| `type` | WHATWG-State |
|---|---|
| `hidden` | Hidden state |
| `text` | Text state |
| `search` | Search state |
| `tel` | Telephone state |
| `url` | URL state |
| `email` | Email state |
| `password` | Password state |
| `date` | Date state |
| `month` | Month state |
| `week` | Week state |
| `time` | Time state |
| `datetime-local` | Local Date and Time state |
| `number` | Number state |
| `range` | Range state |
| `color` | Color state |
| `checkbox` | Checkbox state |
| `radio` | Radio Button state |
| `file` | File Upload state |
| `submit` | Submit Button state |
| `image` | Image Button state |
| `reset` | Reset Button state |
| `button` | Button state |

---

# 4.10.1 Introduction

Die WHATWG beschreibt ein Formular als Bestandteil einer Webseite, der Form Controls enthält.

Typische Form Controls umfassen unter anderem:

- Text Controls
- Buttons
- Checkboxes
- Range Controls
- Color Picker
- weitere Eingabe- und Auswahlkontrollen

Formulare können Benutzerdaten aufnehmen und diese zur weiteren Verarbeitung übermitteln.

Clientseitiges Scripting ist für grundlegende Formularübermittlung nicht grundsätzlich erforderlich. Die HTML-Formularinfrastruktur stellt jedoch APIs bereit, mit denen Skripte Formularinteraktionen erweitern können.

Die Einleitung unterscheidet insbesondere zwischen:

1. Aufbau der Benutzeroberfläche
2. serverseitiger Verarbeitung
3. Konfiguration der Kommunikation zwischen Benutzeroberfläche und Server
4. clientseitiger Validierung
5. automatischer Befüllung
6. mobiler Nutzung
7. Feldtyp, Autofill Field Name und Input Modality
8. standardisierten Datums-, Zeit- und Zahlenformaten

Diese Unterabschnitte sind konzeptionelle bzw. normative Infrastruktur und keine zusätzlichen HTML-Elemente.

---

# 4.10.2 Categories

Die Form-Elemente besitzen zusätzlich zu den allgemeinen Content Categories spezielle Formular-Kategorien.

## Form-associated elements

Die WHATWG führt folgende Elemente als form-associated elements:

- `button`
- `fieldset`
- `input`
- `object`
- `output`
- `select`
- `textarea`
- `img`
- form-associated custom elements

Die Liste ist für die Formularinfrastruktur relevant.

Wichtig:

`object` und `img` werden dadurch nicht zu Form-Elementen im Sinne dieses Dokumentinventars. Sie sind lediglich in die Form-associated-Infrastruktur einbezogen.

## Listed elements

Listed elements erscheinen in den APIs:

- `form.elements`
- `fieldset.elements`

Listed elements besitzen außerdem das `form`-Content-Attribut sowie das entsprechende `form`-IDL-Attribut.

WHATWG-Liste:

- `button`
- `fieldset`
- `input`
- `object`
- `output`
- `select`
- `textarea`
- form-associated custom elements

Image Buttons werden in bestimmten historischen API-Zusammenhängen speziell behandelt.

## Submittable elements

Submittable elements können zur Entry List einer Form Submission beitragen.

WHATWG-Liste:

- `button`
- `input`
- `select`
- `textarea`
- form-associated custom elements

Ob ein bestimmtes Element tatsächlich einen erfolgreichen Submission-Eintrag erzeugt, hängt von seinem Zustand und weiteren Bedingungen ab.

## Resettable elements

Resettable elements können vom Reset einer Form betroffen sein.

WHATWG-Liste:

- `input`
- `output`
- `select`
- `textarea`
- form-associated custom elements

## Autocapitalize-and-autocorrect-inheriting elements

Die WHATWG definiert eine Kategorie für Elemente, die `autocapitalize` und `autocorrect` vom Form Owner erben können.

Dazu gehören:

- `button`
- `fieldset`
- `input`
- `output`
- `select`
- `textarea`

## Labelable elements

Labelable elements können mit einem `label`-Element verbunden werden.

WHATWG-Liste:

- `button`
- `input`, sofern nicht im Hidden State
- `meter`
- `output`
- `progress`
- `select`
- `textarea`
- form-associated custom elements

Damit ist insbesondere festzuhalten:

> `input type="hidden"` ist kein labelable `input`.

---

# Detailprüfung: `form`

## WHATWG-Abschnitt

§4.10.3 – The `form` element

## Bedeutung

Das `form`-Element repräsentiert eine Formularstruktur und stellt den Rahmen für Form Controls und Formularübermittlung bereit.

Die WHATWG-Definition beschreibt das Element als eine Beziehung zu den form-associated elements, von denen einige bearbeitbare Werte repräsentieren können, die bei einer Form Submission verarbeitet werden.

## Content Categories

`form` ist:

- Flow content
- Palpable content

## Context

`form` kann verwendet werden:

- wo Flow Content erwartet wird.

## Content Model

Das Content Model ist:

- Flow content
- jedoch ohne `form`-Element-Nachkommen.

Ein `form` darf daher nicht ein weiteres `form`-Element enthalten.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Neben Global Attributes:

- `accept-charset`
- `action`
- `autocomplete`
- `enctype`
- `method`
- `name`
- `novalidate`
- `target`
- `rel`

## `accept-charset`

Der aktuelle WHATWG-Standard beschränkt `accept-charset` auf eine ASCII-case-insensitive Übereinstimmung mit `UTF-8`.

Damit ist die aktuelle Spezifikation gegenüber älteren HTML-Dokumentationen nicht als allgemeine Liste beliebiger Zeichencodierungen zu interpretieren.

## `action`

`action` bestimmt die URL, die für die Formularübermittlung verwendet wird.

Das Attribut gehört außerdem zur Gruppe der navigating URL attributes und ist in der Sanitization-Angabe entsprechend einzuordnen.

## `autocomplete`

`autocomplete` steuert die Standardeinstellung für Autofill-Verhalten der Form Controls.

Für `form` sind insbesondere die Zustände:

- `on`
- `off`

definiert.

Der fehlende Wert und ein ungültiger Wert führen zum On State.

## `enctype`

Bestimmt den Encoding Type für die Form Submission.

Die konkrete Verarbeitung wird in §4.10.22 beschrieben.

## `method`

Bestimmt die Variante der Form Submission.

Die eigentliche Übermittlungsverarbeitung ist Bestandteil des Form Submission Processing Models.

## `name`

`name` repräsentiert den Namen der Form innerhalb der `forms`-Collection.

Der Wert darf nicht leer sein.

Zusätzliche Anforderungen betreffen die Eindeutigkeit innerhalb der betreffenden `forms`-Collection.

## `novalidate`

`novalidate` deaktiviert die Constraint Validation für eine Form Submission.

Es handelt sich um ein Boolean Attribute.

## `target`

`target` bestimmt den Navigable, der für die Form Submission verwendet wird.

## `rel`

`rel` auf `form` steuert die Link-Arten, die durch das Formular erzeugt werden.

Die WHATWG führt für `form` als unterstützte Token insbesondere:

- `noreferrer`
- `noopener`
- `opener`

auf.

Die tatsächlich unterstützten Token müssen auf diejenigen beschränkt bleiben, für die der User Agent das entsprechende Processing Model implementiert.

## Accessibility

Die WHATWG führt für `form` eigene Accessibility Considerations für Autoren und Implementierer.

Die semantische Funktion des Elements ist von einer bloßen visuellen Gruppierung zu unterscheiden.

Die konkrete Accessibility-Ausgestaltung wird zusätzlich durch die einschlägigen Accessibility-Spezifikationen vertieft.

## Sanitization

WHATWG kennzeichnet `action` als navigating URL attribute.

Für die ZE-WebLab-Referenz wird deshalb festgehalten:

- `action` besitzt eine Sanitization-Relevanz.
- Die Sanitization-Information ist getrennt vom allgemeinen Content-Attribute-Inventar zu führen.

## DOM Interface

`form` verwendet:

`HTMLFormElement`

Die WHATWG definiert unter anderem APIs für:

- `elements`
- `length`
- indizierten Zugriff
- named access
- `autocomplete`
- Formularname
- weitere Formularoperationen

### `form.elements`

`form.elements` liefert eine `HTMLFormControlsCollection`.

Die Collection enthält die Listed Elements, deren Form Owner das betreffende `form` ist.

Image Buttons werden in dieser Collection aus historischen Gründen ausgeschlossen.

### `form.length`

`length` entspricht der Anzahl der Controls in der Collection.

Auch hier werden Image Buttons aus historischen Gründen nicht berücksichtigt.

### Named access

Ein Form kann über Namen bzw. IDs auf Form Controls zugreifen.

Die WHATWG definiert hierfür auch eine Past Names Map.

Diese dient dazu, bestimmte frühere Namen von Controls für den Zugriff verfügbar zu halten, selbst wenn sich `id` oder `name` später ändern.

Dies ist eine DOM-/API-Regel und kein zusätzliches HTML-Element.

---

# Detailprüfung: `label`

## WHATWG-Abschnitt

§4.10.4 – The `label` element

## Bedeutung

`label` repräsentiert eine Beschriftung für ein Labelable Element.

Die Verbindung kann insbesondere erfolgen:

- implizit durch ein Control innerhalb des `label`
- explizit über das `for`-Attribut.

## Content Categories

`label` ist:

- Flow content
- Phrasing content
- Interactive content
- Palpable content

## Context

Wo Flow Content oder Phrasing Content erwartet wird.

## Content Model

Phrasing Content, jedoch darf kein weiterer `label`-Nachkomme enthalten sein.

Außerdem gelten Einschränkungen hinsichtlich bestimmter interaktiver Inhalte.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Neben Global Attributes:

- `for`

## `for`

`for` ordnet das Label einem Labelable Element zu.

Der Wert wird als ID-Referenz verwendet.

Die explizite Zuordnung ist besonders relevant, wenn das Control nicht als Nachkomme des `label` eingebettet ist.

## DOM Interface

`HTMLLabelElement`

Relevante API-Eigenschaften umfassen insbesondere:

- `htmlFor`
- `control`

`control` referenziert das zugeordnete Labelable Element, sofern eine entsprechende Zuordnung besteht.

## Accessibility

Die `label`-Semantik ist zentral für die zugängliche Benennung von Form Controls.

Die WHATWG stellt hierzu Accessibility Considerations bereit.

Für ZE-WebLab gilt:

- `label` ist nicht nur eine visuelle Beschriftung.
- Die semantische Verbindung zum Control ist separat zu dokumentieren.
- Konkrete Accessibility-Mappings sind in der Accessibility-Ebene weiter zu vertiefen.

---

# Detailprüfung: `input`

## WHATWG-Abschnitt

§4.10.5 – The `input` element

## Bedeutung

`input` repräsentiert ein typisiertes Datenfeld.

Das `type`-Attribut bestimmt den Datentyp und den zugehörigen Control-Typ.

`input` besitzt damit ein gemeinsames Elementmodell mit stark zustandsabhängiger Semantik.

## Content Categories

Die genaue Kategorisierung hängt vom State ab.

`input` ist grundsätzlich ein:

- Flow content
- Phrasing content
- bestimmte States sind Interactive Content
- bestimmte States sind Listed
- bestimmte States sind Labelable
- bestimmte States sind Submittable

Der Hidden State ist insbesondere nicht labelable.

## Context

Wo Phrasing Content erwartet wird.

## Content Model

`input` ist ein Void Element.

Es besitzt kein eigenes normales Content Model.

## Tag Omission

Keine End Tag.

## Zentrale Attribute

Global Attributes sowie insbesondere:

- `accept`
- `alt`
- `autocomplete`
- `capture`
- `checked`
- `dirname`
- `disabled`
- `form`
- `formaction`
- `formenctype`
- `formmethod`
- `formnovalidate`
- `formtarget`
- `height`
- `list`
- `max`
- `maxlength`
- `min`
- `minlength`
- `multiple`
- `name`
- `pattern`
- `placeholder`
- `popovertarget`
- `popovertargetaction`
- `readonly`
- `required`
- `size`
- `src`
- `step`
- `type`
- `value`
- `width`

Die Zulässigkeit und Bedeutung vieler dieser Attribute ist state-dependent.

---

# `input` – Zustandsmodell

## Hidden State – `type="hidden"`

Repräsentiert einen Wert, der nicht als Benutzer-Control angezeigt wird.

Besonderheiten:

- nicht labelable
- keine normale Benutzerinteraktion
- kann submittable sein
- dient insbesondere zur Übermittlung eines zusätzlichen Wertes

Bestimmte interaktive oder UI-bezogene Attribute sind in diesem State nicht sinnvoll bzw. nicht zulässig.

Der Hidden State ist daher nicht mit einem unsichtbar gemachten normalen Text Control gleichzusetzen.

---

## Text State – `type="text"`

Repräsentiert Text ohne Zeilenumbrüche.

Typischer Control-Typ:

- Text Control

Relevante Attribute umfassen insbesondere:

- `maxlength`
- `minlength`
- `pattern`
- `placeholder`
- `readonly`
- `required`
- `size`
- `list`
- `autocomplete`

Der Text State ist grundsätzlich ein typisches labelable, listed und submittable Form Control.

---

## Search State – `type="search"`

Repräsentiert Text ohne Zeilenumbrüche mit Search-Control-Semantik.

Das State-Modell ist eng mit dem Text State verwandt.

Der Unterschied liegt insbesondere in der vorgesehenen Semantik und Benutzerinteraktion für Suchfelder.

---

## Telephone State – `type="tel"`

Repräsentiert Telefonnummern.

Die WHATWG behandelt Telefonnummern als Text und schreibt kein allgemeines internationales Telefonnummernformat vor.

Der State ist insbesondere relevant für:

- Eingabemodalität
- mobile Tastaturen
- Autofill
- Textverarbeitung

---

## URL State – `type="url"`

Repräsentiert eine absolute URL.

Die Eingabe unterliegt URL-bezogenen Validierungsregeln.

Relevante Attribute umfassen unter anderem:

- `maxlength`
- `minlength`
- `pattern`
- `placeholder`
- `readonly`
- `required`
- `size`
- `list`
- `autocomplete`

---

## Email State – `type="email"`

Repräsentiert:

- eine E-Mail-Adresse
- oder bei `multiple` eine Liste von E-Mail-Adressen.

Der State besitzt eigene Syntax- und Constraint-Validation-Regeln.

Relevante Attribute:

- `multiple`
- `maxlength`
- `minlength`
- `pattern`
- `placeholder`
- `readonly`
- `required`
- `size`
- `list`
- `autocomplete`

---

## Password State – `type="password"`

Repräsentiert Text ohne Zeilenumbrüche, wobei die Benutzereingabe typischerweise verborgen dargestellt wird.

Das Element bleibt ein Datenfeld und ist nicht mit einer kryptografischen Speicherung gleichzusetzen.

Relevante Attribute umfassen insbesondere:

- `maxlength`
- `minlength`
- `pattern`
- `placeholder`
- `readonly`
- `required`
- `size`
- `autocomplete`

---

## Date State – `type="date"`

Repräsentiert ein Datum:

- Jahr
- Monat
- Tag

ohne Zeitzone.

Die zugrunde liegende Datumssemantik folgt den WHATWG-Date-and-Time-Microsyntaxes.

Das sichtbare UI darf lokalisiert sein; der zugrunde liegende Wert ist jedoch standardisiert.

---

## Month State – `type="month"`

Repräsentiert:

- Jahr
- Monat

ohne konkreten Tag.

---

## Week State – `type="week"`

Repräsentiert eine Kalenderwoche mit Jahr.

Die WHATWG definiert hierfür eine standardisierte Wochenrepräsentation.

---

## Time State – `type="time"`

Repräsentiert eine Uhrzeit ohne Zeitzone.

Die unterstützte Genauigkeit und Schrittweite werden über die entsprechenden Form-Control-Regeln bestimmt.

---

## Local Date and Time State – `type="datetime-local"`

Repräsentiert eine lokale Kombination aus:

- Datum
- Uhrzeit

ohne Zeitzoneninformation.

Der State ist deshalb nicht dasselbe wie eine globale Zeitangabe.

---

## Number State – `type="number"`

Repräsentiert eine Zahl.

Die WHATWG definiert dafür eine numerische Eingabe mit:

- `min`
- `max`
- `step`

und den zugehörigen Constraint-Validation-Regeln.

Das sichtbare UI kann beispielsweise Spinner oder andere numerische Controls verwenden; die konkrete Darstellung ist nicht die eigentliche HTML-Semantik.

---

## Range State – `type="range"`

Repräsentiert eine Zahl innerhalb eines Wertebereichs.

Der Wertebereich wird insbesondere über:

- `min`
- `max`
- `step`

bestimmt.

Das Control ist für die Auswahl eines Wertes innerhalb eines Bereichs vorgesehen.

---

## Color State – `type="color"`

Repräsentiert eine Farbe.

Der Wert folgt den von der WHATWG definierten Farbregeln.

Der sichtbare Color Picker ist User-Agent-UI und nicht selbst Teil des HTML-Elementinventars.

---

## Checkbox State – `type="checkbox"`

Repräsentiert eine boolesche Auswahl.

Relevantes Attribut:

- `checked`

Eine Checkbox kann:

- ausgewählt
- nicht ausgewählt

sein.

Zusätzlich besitzt der Zustand die für Form Submission und Constraint Validation relevanten Regeln.

---

## Radio Button State – `type="radio"`

Repräsentiert eine Auswahl innerhalb einer Gruppe.

Radio Buttons werden anhand ihres `name`-Wertes gruppiert.

Die WHATWG definiert hierfür eigene Regeln zur Gruppe und zur Auswahl.

`checked` bestimmt den initialen bzw. deklarativen Auswahlzustand.

---

## File Upload State – `type="file"`

Repräsentiert ein Control zur Auswahl von Dateien.

Relevante Attribute:

- `accept`
- `capture`
- `multiple`

Die Auswahl selbst erfolgt über die User-Agent- bzw. Betriebssystemumgebung.

`accept` dient als Hinweis bzw. Einschränkung für die Auswahl geeigneter Dateitypen.

Die resultierenden Dateien werden nicht als gewöhnliche Stringwerte behandelt, sondern über die Datei-/Formularinfrastruktur repräsentiert.

---

## Submit Button State – `type="submit"`

Repräsentiert einen Submit Button.

Beim Aktivieren kann dadurch eine Form Submission ausgelöst werden.

State-spezifische Submission-Attribute:

- `formaction`
- `formenctype`
- `formmethod`
- `formnovalidate`
- `formtarget`

Diese überschreiben bzw. ergänzen die entsprechenden Einstellungen der Form für die jeweilige Submission.

---

## Image Button State – `type="image"`

Repräsentiert einen grafischen Submit Button.

Relevante Attribute:

- `src`
- `alt`
- `width`
- `height`

Bei Submission können zusätzlich Koordinaten des aktivierten Image Buttons Teil der Entry List werden.

Image Buttons besitzen außerdem historische Sonderregeln bei bestimmten Form-Control-Collections.

---

## Reset Button State – `type="reset"`

Repräsentiert einen Button zum Zurücksetzen der Form Controls.

Das Aktivieren löst den Form Reset Mechanismus aus.

---

## Button State – `type="button"`

Repräsentiert einen generischen Button ohne die implizite Submit- oder Reset-Funktion der entsprechenden States.

Die Interaktion kann über Script oder andere Mechanismen erweitert werden.

---

# Input-spezifische Unterkonzepte

## 4.10.5.2 Localization

Die WHATWG weist ausdrücklich darauf hin, dass die Darstellung von Form Controls lokalisiert sein kann.

Insbesondere betrifft dies:

- Datumsdarstellungen
- Zeitdarstellungen
- Zahlen
- Eingabemethoden
- Benutzeroberfläche

Die interne HTML-Wertrepräsentation ist davon zu unterscheiden.

---

# 4.10.5.3 Common `input` element attributes

## `maxlength`

Begrenzt die maximale Länge einer Benutzereingabe bei den dafür geeigneten Input States.

Die Länge wird auf Basis der von der Spezifikation definierten String-/Code-Unit-Regeln bestimmt.

## `minlength`

Definiert eine Mindestlänge für die Constraint Validation.

## `size`

Bestimmt bei den dafür vorgesehenen Text Controls die sichtbare Größe.

## `readonly`

Macht ein Control nicht editierbar, ohne es dadurch automatisch aus allen Form-APIs zu entfernen.

Die genaue Wirkung ist state-dependent.

## `required`

Kennzeichnet ein Control als verpflichtend.

Die Constraint Validation entscheidet anhand des jeweiligen States, wie `required` angewendet wird.

## `multiple`

Erlaubt bei den dafür vorgesehenen States mehrere Werte.

Besonders relevant:

- `email`
- `file`

## `pattern`

Definiert ein reguläres Muster für die Eingabe.

Die aktuelle WHATWG-Spezifikation verwendet hierfür die spezifizierte JavaScript-Regular-Expression-Semantik und die entsprechenden Constraint-Validation-Regeln.

## `min` und `max`

Definieren bei numerischen bzw. zeitbezogenen States untere und obere Grenzen.

## `step`

Definiert die Schrittweite für die dafür vorgesehenen Input States.

Dabei wird eine sogenannte Step Base und das entsprechende Stepping-Konzept berücksichtigt.

## `list`

Referenziert ein `datalist`-Element.

Die ID-Referenz verbindet das Input Control mit einer Liste vorgeschlagener Werte.

## `placeholder`

Stellt einen Hinweis auf den erwarteten Eingabewert bereit.

`placeholder` ist keine echte Beschriftung des Controls und ersetzt deshalb kein `label`.

---

# 4.10.5.4 Common `input` element APIs

Das DOM Interface von `input` ist:

`HTMLInputElement`

Je nach State stehen unter anderem APIs für folgende Konzepte zur Verfügung:

- Wert
- Default Value
- Checked State
- Default Checked State
- Selection
- Files
- Validity
- Form Association
- Labels
- Type
- List
- Dimensions bei Image Buttons

Die genaue Bedeutung einzelner IDL-Attribute hängt vom jeweiligen Input State ab.

---

# 4.10.5.5 Common event behaviors

Form Controls besitzen standardisierte Interaktions- und Event-Regeln.

Dazu gehören insbesondere:

- `input`
- `change`
- `invalid`
- `beforeinput` im Rahmen der allgemeinen DOM-/Input-Infrastruktur
- Aktivierungsverhalten
- Fokusverhalten

Die konkrete Event-Semantik ist von der jeweiligen Control-Art abhängig.

---

# Detailprüfung: `button`

## WHATWG-Abschnitt

§4.10.6 – The `button` element

## Content Categories

`button` ist:

- Flow content
- Phrasing content
- Interactive content
- Palpable content
- Listed
- Labelable
- Submittable
- Autocapitalize-and-autocorrect inheriting
- Form-associated

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content, jedoch dürfen bestimmte interaktive Elemente nicht verschachtelt werden.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Neben Global Attributes:

- `command`
- `commandfor`
- `disabled`
- `form`
- `formaction`
- `formenctype`
- `formmethod`
- `formnovalidate`
- `formtarget`
- `name`
- `popovertarget`
- `popovertargetaction`
- `type`
- `value`

## `type`

Der Button-Typ bestimmt insbesondere:

- Submit
- Reset
- Button

Fehlt `type`, greift der in der Spezifikation definierte Default.

## Submission Attributes

Nur Submit Buttons dürfen die Submit-spezifischen Attribute verwenden:

- `formaction`
- `formenctype`
- `formmethod`
- `formnovalidate`
- `formtarget`

## DOM Interface

`HTMLButtonElement`

## Accessibility

`button` ist ein interaktives, labelbares Form-associated Element.

Die zugängliche Beschriftung ergibt sich aus seinem Inhalt bzw. der einschlägigen Accessibility-Semantik.

---

# Detailprüfung: `select`

## WHATWG-Abschnitt

§4.10.7 – The `select` element

## Bedeutung

`select` repräsentiert ein Control zur Auswahl von Optionen.

Die aktuelle Spezifikation unterstützt dabei verschiedene Darstellungs- und Auswahlmodelle.

## Content Categories

Je nach Definition insbesondere:

- Flow content
- Phrasing content
- Interactive content
- Listed
- Labelable
- Submittable
- Resettable
- Autocapitalize-and-autocorrect inheriting
- Form-associated

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Die aktuelle Spezifikation definiert ein strukturiertes Content Model, das insbesondere `option`, `optgroup`, `hr`, script-supporting content und unter bestimmten Bedingungen `button` bzw. `div` berücksichtigt.

Das genaue Modell hängt vom Select-Modus ab.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Unter anderem:

- `autocomplete`
- `disabled`
- `form`
- `multiple`
- `name`
- `required`
- `size`

## `multiple`

Erlaubt die Auswahl mehrerer Werte.

## `required`

Kennzeichnet die Auswahl als erforderlich.

## `size`

Definiert die Anzahl der Optionen, die angezeigt werden sollen.

Die Spezifikation verlangt hierfür einen gültigen positiven Wert.

## DOM Interface

`HTMLSelectElement`

Relevante APIs umfassen:

- `autocomplete`
- `disabled`
- `form`
- `labels`
- `length`
- `multiple`
- `name`
- `options`
- `selectedIndex`
- `selectedOptions`
- `size`
- `value`
- `validity`
- `willValidate`

---

# Detailprüfung: `datalist`

## WHATWG-Abschnitt

§4.10.8 – The `datalist` element

## Bedeutung

`datalist` repräsentiert eine Menge von Optionen, die einem anderen Form Control als Vorschläge bereitgestellt werden können.

Es handelt sich nicht selbst um das Eingabe-Control.

Typischer Zusammenhang:

`input[list]` → `datalist#id`

## Content Categories

`datalist` ist:

- Flow content
- Phrasing content
- Palpable content

## Context

Wo Flow Content oder Phrasing Content erwartet wird.

## Content Model

Zero or more `option`-Elemente bzw. die von der Spezifikation zugelassenen unterstützenden Inhalte.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Global Attributes.

Es besitzt kein eigenes `list`-Attribut zur Auswahl eines Ziel-Controls.

## DOM Interface

`HTMLDataListElement`

Die `options`-Collection stellt die zugehörigen Options bereit.

## Accessibility

`datalist` stellt Vorschlagsdaten bereit und ist nicht mit einem sichtbaren Dropdown-Element gleichzusetzen.

Die konkrete Darstellung der Vorschläge ist User-Agent-Verhalten.

---

# Detailprüfung: `optgroup`

## WHATWG-Abschnitt

§4.10.9 – The `optgroup` element

## Bedeutung

`optgroup` gruppiert Optionen innerhalb eines `select`.

## Content Categories

Keine allgemeinen Content Categories wie bei Flow-/Phrasing-Elementen.

## Context

Innerhalb von `select`.

## Content Model

`option`-Elemente sowie gemäß aktuellem Select-Content-Model die von der Spezifikation zugelassenen Inhalte.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Global Attributes sowie:

- `disabled`
- `label`

## `disabled`

Deaktiviert die Gruppe und damit die darin enthaltenen Optionen für die entsprechende Interaktion.

## `label`

Definiert die sichtbare bzw. semantische Gruppenbezeichnung.

## DOM Interface

`HTMLOptGroupElement`

---

# Detailprüfung: `option`

## WHATWG-Abschnitt

§4.10.10 – The `option` element

## Bedeutung

`option` repräsentiert eine einzelne Auswahlmöglichkeit.

## Context

Typischerweise innerhalb von:

- `select`
- `optgroup`
- `datalist`

Das konkrete zulässige Umfeld hängt vom jeweiligen Content Model ab.

## Content Model

Text bzw. die von der aktuellen Select-/Datalist-Infrastruktur zugelassenen Inhalte.

Die aktuelle Spezifikation berücksichtigt außerdem das `selectedcontent`-Modell bei bestimmten Select-Darstellungen.

## Tag Omission

Die WHATWG definiert für `option` besondere Tag-Omission-Regeln.

Die End Tag kann unter den spezifizierten Bedingungen weggelassen werden.

## Content Attributes

Unter anderem:

- `disabled`
- `label`
- `selected`
- `value`

## `disabled`

Macht die Option nicht auswählbar.

## `label`

Definiert eine alternative Beschriftung für die Option.

Fehlt `label`, wird der entsprechende Textinhalt für die Darstellung verwendet.

## `selected`

Definiert den initialen bzw. Default-Auswahlzustand.

Der aktuelle ausgewählte Zustand und der Default-Zustand sind konzeptionell zu unterscheiden.

## `value`

Definiert den Wert, der bei der Form Submission verwendet werden kann.

Fehlt `value`, wird die entsprechende textuelle Repräsentation nach den WHATWG-Regeln herangezogen.

## DOM Interface

`HTMLOptionElement`

Relevante Eigenschaften:

- `disabled`
- `form`
- `label`
- `defaultSelected`
- `selected`
- `text`
- `value`

---

# Detailprüfung: `textarea`

## WHATWG-Abschnitt

§4.10.11 – The `textarea` element

## Bedeutung

`textarea` repräsentiert ein mehrzeiliges Text Control.

## Content Categories

- Flow content
- Phrasing content
- Interactive content
- Listed
- Labelable
- Submittable
- Resettable
- Autocapitalize-and-autocorrect inheriting
- Form-associated
- Palpable content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Raw text.

Das bedeutet insbesondere, dass der Inhalt nicht wie normales HTML-Markup interpretiert wird.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Neben Global Attributes:

- `autocomplete`
- `cols`
- `dirname`
- `disabled`
- `form`
- `maxlength`
- `minlength`
- `name`
- `placeholder`
- `readonly`
- `required`
- `rows`
- `wrap`

## `cols`

Definiert die sichtbare Breite in Zeichen.

## `rows`

Definiert die sichtbare Höhe in Zeilen.

## `wrap`

Steuert das Wrapping-Verhalten bei der Submission.

## `placeholder`

Definiert einen Hinweistext.

## `readonly`

Verhindert die Bearbeitung durch den Benutzer.

## `required`

Macht die Eingabe verpflichtend.

## DOM Interface

`HTMLTextAreaElement`

Relevante APIs:

- `value`
- `defaultValue`
- `textLength`
- `selectionStart`
- `selectionEnd`
- `selectionDirection`
- `setRangeText()`
- `setSelectionRange()`
- `validity`
- `willValidate`
- `labels`
- `form`

---

# Detailprüfung: `output`

## WHATWG-Abschnitt

§4.10.12 – The `output` element

## Bedeutung

`output` repräsentiert das Ergebnis einer Berechnung oder einer anderen Benutzerinteraktion.

## Content Categories

- Flow content
- Phrasing content
- Labelable
- Listed
- Resettable
- Form-associated
- Palpable

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Neben Global Attributes:

- `for`
- `form`
- `name`

## `for`

Referenziert die Controls, aus denen das Ergebnis abgeleitet wurde.

Die Referenz ist eine space-separated list of IDs.

## `form`

Kann den Form Owner explizit bestimmen.

## `name`

Bestimmt den Namen des Outputs innerhalb der Form-Infrastruktur.

## DOM Interface

`HTMLOutputElement`

Relevante APIs:

- `htmlFor`
- `form`
- `name`
- `value`
- `defaultValue`
- `willValidate`
- `validity`
- `labels`

`output` ist resettable, aber nicht submittable im selben Sinn wie klassische Eingabe-Controls.

---

# Detailprüfung: `progress`

## WHATWG-Abschnitt

§4.10.13 – The `progress` element

## Bedeutung

`progress` repräsentiert den Fortschritt bei einer Aufgabe.

## Content Categories

- Flow content
- Phrasing content
- Labelable
- Palpable

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Global Attributes sowie:

- `value`
- `max`

## Determinate und indeterminate

Ist `value` vorhanden, repräsentiert das Element einen bestimmten Fortschritt.

Fehlt `value`, kann der Fortschritt als nicht bestimmbar bzw. indeterminate dargestellt werden.

## `max`

Definiert den maximalen Fortschrittswert.

Der Wert muss die WHATWG-Anforderungen für einen gültigen positiven Wert erfüllen.

## `value`

Definiert den aktuellen Fortschritt.

## DOM Interface

`HTMLProgressElement`

Relevante APIs:

- `max`
- `position`
- `value`
- `labels`

`position` kann insbesondere bei indeterminate Progress einen speziellen Wert liefern.

## Accessibility

`progress` besitzt eine eigene semantische Bedeutung für Fortschrittsanzeigen.

Die konkrete Accessibility-Mapping-Ebene wird zusätzlich durch die Accessibility-Spezifikationen bestimmt.

---

# Detailprüfung: `meter`

## WHATWG-Abschnitt

§4.10.14 – The `meter` element

## Bedeutung

`meter` repräsentiert eine skalare Messung innerhalb eines bekannten Bereichs.

Es ist nicht als generischer Fortschrittsbalken gedacht.

## Content Categories

- Flow content
- Phrasing content
- Labelable
- Palpable

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Global Attributes sowie:

- `value`
- `min`
- `max`
- `low`
- `high`
- `optimum`

## `min` / `max`

Definieren den Messbereich.

## `value`

Definiert den aktuellen Messwert.

## `low`

Definiert den unteren Bereich.

## `high`

Definiert den oberen Bereich.

## `optimum`

Definiert den optimalen Wert bzw. Bereich.

Die WHATWG definiert anhand dieser Werte die semantische Einordnung der Messung.

## DOM Interface

`HTMLMeterElement`

Relevante APIs:

- `value`
- `min`
- `max`
- `low`
- `high`
- `optimum`
- `labels`

---

# Detailprüfung: `fieldset`

## WHATWG-Abschnitt

§4.10.15 – The `fieldset` element

## Bedeutung

`fieldset` gruppiert zusammengehörige Form Controls.

## Content Categories

- Flow content
- Listed
- Form-associated
- Palpable

## Context

Wo Flow Content erwartet wird.

## Content Model

Flow Content, wobei ein `legend` unter den spezifizierten Bedingungen am Anfang auftreten kann.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Global Attributes sowie:

- `disabled`
- `form`
- `name`

## `disabled`

Deaktiviert die enthaltenen Form Controls gemäß der Fieldset-Disabled-Infrastruktur.

Ein `legend` besitzt dabei eine besondere Stellung.

## `form`

Kann den Form Owner explizit festlegen.

## `name`

Definiert den Namen des Fieldsets.

## DOM Interface

`HTMLFieldSetElement`

Relevante APIs:

- `disabled`
- `form`
- `name`
- `elements`
- `type`
- `willValidate`
- `validity`
- `validationMessage`

---

# Detailprüfung: `legend`

## WHATWG-Abschnitt

§4.10.16 – The `legend` element

## Bedeutung

`legend` repräsentiert die Beschriftung einer `fieldset`-Gruppe.

## Content Categories

- Flow content
- Palpable content

## Context

Als erster Nachkomme eines `fieldset` bzw. in den von der Spezifikation vorgesehenen Kontexten.

## Content Model

Flow Content.

## Tag Omission

Keine der beiden Tags ist auslassbar.

## Content Attributes

Global Attributes.

## Accessibility

`legend` ist für die semantische Gruppierung und Benennung von Form Controls relevant.

Die konkrete Accessibility-Auswertung erfolgt zusätzlich über die einschlägigen Accessibility-Mappings.

---

# Detailprüfung: `selectedcontent`

## WHATWG-Abschnitt

§4.10.17 – The `selectedcontent` element

## Bedeutung

`selectedcontent` gehört zur aktuellen Select-Control-Infrastruktur.

Es ermöglicht die deklarative Darstellung des Inhalts der aktuell ausgewählten `option` in den dafür vorgesehenen Select-Konfigurationen.

## Einordnung

`selectedcontent` ist ein eigenständiges HTML-Element im WHATWG-Standard.

Es darf deshalb im Elementinventar geführt werden.

Es ist jedoch kein klassisches Form Control und nicht selbst das auswählende Control.

## Content Model

Die Zulässigkeit und Beziehung zu `select` und `option` sind durch das aktuelle Select-Content-Model bestimmt.

## Normative Besonderheit

Die Verwendung ist eng mit dem modernen Select-Rendering- und Content-Modell verbunden.

Die Regeln dürfen deshalb nicht aus älteren HTML-Referenzen übernommen werden, die `selectedcontent` noch nicht enthalten.

## DOM Interface

Die DOM-Semantik ist entsprechend der WHATWG-Elementdefinition zu dokumentieren.

`selectedcontent` wird nicht mit `HTMLSelectElement` gleichgesetzt.

---

# Gemeinsame Attribute der Form Controls

## `name`

`name` ist zentral für:

- Form Submission
- Form-Control-Identität
- `form.elements`
- Named Access
- bestimmte Autofill- und Submission-Prozesse

Ein Control ohne geeigneten `name`-Wert kann trotz vorhandener Benutzerinteraktion nicht automatisch denselben Submission-Eintrag erzeugen wie ein benanntes Control.

## `dirname`

`dirname` ermöglicht die Übermittlung der Text-Richtung eines Controls zusammen mit seinem Wert.

Es ist für geeignete Text Controls relevant.

Die Richtung wird als zusätzlicher Submission-Eintrag verarbeitet.

## `maxlength`

Begrenzt die maximale Eingabelänge.

Neben der Autorenanforderung besitzt das Attribut eine Rolle in der Constraint Validation.

## `minlength`

Definiert eine Mindestlänge.

Eine zu kurze Benutzereingabe kann dadurch einen `tooShort`-Constraint verursachen.

## `disabled`

`disabled` deaktiviert ein Form Control.

Ein disabled Control:

- ist nicht normal interaktiv
- nimmt nicht normal an der Submission teil
- wird bei der Constraint Validation entsprechend behandelt
- kann über Fieldset-Infrastruktur indirekt disabled werden

## Form Submission Attributes

Elemente wie `button` und `input` können Submission-Eigenschaften lokal überschreiben:

- `formaction`
- `formenctype`
- `formmethod`
- `formnovalidate`
- `formtarget`

Diese Attribute sind state-dependent.

---

# `autocomplete` und Autofill

## Grundprinzip

`autocomplete` steuert Hinweise für die automatische Befüllung von Form Controls.

Die WHATWG unterscheidet dabei:

- Autofill Field Name
- Field Type
- Input Modality

Diese drei Konzepte sind nicht identisch.

## Autofill Field Name

Beschreibt, welche Art von Information ein Control erwartet.

Dazu gehören die von der Spezifikation definierten Autofill Tokens und deren strukturierte Syntax.

## `autocomplete="on"`

Aktiviert bzw. erlaubt Autofill entsprechend dem jeweiligen Control.

## `autocomplete="off"`

Signalisiert, dass Autofill nicht verwendet werden soll.

Die tatsächliche Browserentscheidung kann von weiteren Faktoren abhängen.

## Autofill ist kein Element

Autofill ist eine Feature-/Processing-Ebene.

Es wird daher nicht als HTML-Element inventarisiert.

---

# Form Control Infrastructure

# 4.10.18.1 A form control's value

Form Controls besitzen einen Wert, der sich von:

- Attributwerten
- Default Value
- aktuellem Benutzerwert
- Submission Value

unterscheiden kann.

Das ist besonders wichtig für:

- `input`
- `textarea`
- `select`
- `output`

Die Spezifikation unterscheidet verschiedene interne Wertzustände.

Der aktuelle Wert darf daher nicht pauschal mit dem ursprünglichen HTML-Attributwert gleichgesetzt werden.

---

# 4.10.18.2 Mutability

Die WHATWG definiert, wann ein Form Control mutierbar bzw. editierbar ist.

Dabei spielen insbesondere folgende Faktoren eine Rolle:

- Control State
- `readonly`
- `disabled`
- interne Control-Eigenschaften

Nicht jedes Control, das einen Wert besitzt, ist für Benutzer editierbar.

---

# 4.10.18.3 Association of controls and forms

Jedes form-associated element kann einen Form Owner besitzen.

Der Form Owner kann:

- implizit aus der Dokumentstruktur entstehen
- explizit über das `form`-Attribut bestimmt werden

Das ermöglicht auch die Zuordnung von Controls, die nicht physisch innerhalb des `form`-Elements liegen.

Diese Association ist ein internes DOM-/Processing-Konzept und kein zusätzliches HTML-Element.

---

# Constraint Validation

# 4.10.21.1 Definitions

Constraint Validation bezeichnet das standardisierte Modell zur Prüfung, ob Form Controls die für sie geltenden Eingabebedingungen erfüllen.

Relevante Konzepte sind unter anderem:

- candidate for constraint validation
- barred from constraint validation
- validity state
- validation message
- suffering from a particular validity error

---

# 4.10.21.2 Constraint validation

Ein Control kann verschiedene Validity States besitzen.

Relevante Zustände des `ValidityState`-Modells umfassen insbesondere:

- `valueMissing`
- `typeMismatch`
- `patternMismatch`
- `tooLong`
- `tooShort`
- `rangeUnderflow`
- `rangeOverflow`
- `stepMismatch`
- `badInput`
- `customError`
- `valid`

Welche Zustände tatsächlich relevant sind, hängt vom jeweiligen Control und State ab.

## `required`

Kann `valueMissing` auslösen.

## Typprüfung

Beispiele:

- URL Controls
- Email Controls

können type-spezifische Fehler erzeugen.

## `pattern`

Kann `patternMismatch` auslösen.

## Längenbeschränkungen

`maxlength` und `minlength` können zu Längen-Constraints führen.

## Bereichsconstraints

`min` und `max` können:

- `rangeUnderflow`
- `rangeOverflow`

auslösen.

## Schrittweite

`step` kann zu `stepMismatch` führen.

## `badInput`

Bestimmte numerische bzw. spezialisierte Controls können einen ungültigen Benutzereingabestatus besitzen, der als `badInput` behandelt wird.

---

# 4.10.21.3 Constraint Validation API

Die Constraint Validation API stellt unter anderem bereit:

- `checkValidity()`
- `reportValidity()`
- `setCustomValidity()`
- `validity`
- `validationMessage`
- `willValidate`

Bei Forms zusätzlich:

- `checkValidity()`
- `reportValidity()`
- `requestSubmit()`

## `checkValidity()`

Prüft die Gültigkeit.

Bei ungültigen Controls kann das entsprechende Event-Modell ausgelöst werden.

## `reportValidity()`

Führt die Validitätsprüfung einschließlich der vorgesehenen Benutzerbenachrichtigung durch.

## `setCustomValidity()`

Ermöglicht das Setzen einer eigenen Validierungsfehlermeldung.

Ein nichtleerer Custom-Error-String macht das Control invalid.

---

# 4.10.21.4 Security

Constraint Validation ist keine Sicherheitsgrenze.

Server müssen Form Submission Daten weiterhin validieren.

Clientseitige Constraint Validation darf deshalb nicht als Vertrauensgrenze betrachtet werden.

---

# Form Submission

# 4.10.22.1 Introduction

Form Submission beschreibt den Prozess, durch den Daten eines Formulars an ein Ziel übermittelt werden.

Die Verarbeitung umfasst unter anderem:

1. Ermittlung des Submitters
2. Prüfung der Submission-Bedingungen
3. Constraint Validation
4. Ermittlung des Form Owners
5. Ermittlung der Submission Attributes
6. Aufbau der Entry List
7. Wahl des Encodings
8. Erzeugung der eigentlichen Request-Daten
9. Navigation bzw. Fetch-/Submission-Verarbeitung

---

# 4.10.22.2 Implicit submission

Die WHATWG definiert Regeln für implizite Submission.

Dies betrifft insbesondere Situationen, in denen ein Benutzer beispielsweise aus einem Text Control heraus eine Submission auslöst, ohne explizit einen Submit Button anzuklicken.

Das Verhalten hängt unter anderem von den vorhandenen Submit Buttons und der Form-Struktur ab.

Implicit Submission ist ein Processing Model und kein zusätzliches HTML-Element.

---

# 4.10.22.3 Form submission algorithm

Der Form Submission Algorithmus verarbeitet unter anderem:

- Submitter
- Form Owner
- Submission Attributes
- Validierung
- Entry List
- Encoding
- Ziel-Navigable

Die konkrete algorithmische Verarbeitung ist Teil der normativen WHATWG-Spezifikation.

---

# 4.10.22.4 Constructing the entry list

Die Entry List ist die zentrale abstrakte Datenstruktur der Form Submission.

Ein Eintrag kann insbesondere repräsentieren:

- String
- Datei
- weitere von der Submission-Infrastruktur definierte Werte

Nicht jedes Form Control erzeugt automatisch einen Eintrag.

Relevante Faktoren:

- Control muss submittable sein
- Control darf nicht disabled sein
- Control benötigt bei entsprechenden Controls einen gültigen Namen
- aktueller State muss Submission unterstützen
- bestimmte Controls erzeugen zusätzliche Einträge

## Checkbox

Nur eine erfolgreiche Auswahl kann einen entsprechenden Wert beitragen.

## Radio

Der ausgewählte Radio Button trägt den Wert bei.

## File

File Controls können File Entries erzeugen.

## Image Button

Image Buttons können zusätzliche Koordinateninformationen erzeugen.

## `dirname`

Kann einen zusätzlichen Richtungseintrag erzeugen.

---

# 4.10.22.5 Selecting a form submission encoding

Die Submission verwendet abhängig von den Form-Einstellungen einen Encoding Type.

Relevante Werte umfassen insbesondere:

- `application/x-www-form-urlencoded`
- `multipart/form-data`
- `text/plain`

Die Auswahl hängt von `enctype` bzw. den entsprechenden Submitter-Attributen ab.

---

# 4.10.22.6 Converting an entry list to a list of name-value pairs

Die Entry List wird entsprechend dem gewählten Submission-Verfahren in Name-Value-Paare bzw. die jeweils erforderliche Datenrepräsentation überführt.

Dabei werden unter anderem:

- Namen
- Stringwerte
- File Values
- Encoding
- Reihenfolge

berücksichtigt.

---

# 4.10.22.7 URL-encoded form data

`application/x-www-form-urlencoded` serialisiert die Formdaten in der dafür definierten URL-Encoded-Repräsentation.

Besondere Regeln betreffen:

- Byte-/Zeichenkodierung
- Prozentkodierung
- Trennung der Name-Value-Paare
- Sonderzeichen
- Leerzeichen

Die konkrete Serialisierung ist normativ durch die WHATWG definiert.

---

# 4.10.22.8 Multipart form data

`multipart/form-data` wird insbesondere bei Dateiübertragungen verwendet.

Die Formdaten werden als Multipart-Struktur mit einzelnen Parts übertragen.

Dabei können einzelne Parts unter anderem:

- Namen
- Dateinamen
- MIME-Typen
- Binärdaten

enthalten.

Die genaue Formatierung folgt dem normativen Submission-Modell.

---

# 4.10.22.9 Plain text form data

`text/plain` stellt eine einfache textuelle Submission-Repräsentation bereit.

Die Formdaten werden dabei entsprechend dem von der WHATWG definierten Plain-Text-Form-Data-Verfahren serialisiert.

---

# `SubmitEvent`

`SubmitEvent` ist ein DOM Event Interface und kein HTML-Element.

Es stellt im Submission-Kontext insbesondere den Submitter zur Verfügung.

Damit kann Script unterscheiden, welches konkrete Control die Submission ausgelöst hat.

---

# `FormDataEvent`

`FormDataEvent` ist ebenfalls ein DOM Event Interface und kein HTML-Element.

Es wird im Zusammenhang mit der Erstellung von Form Data verwendet und stellt die entsprechende `FormData`-Repräsentation bereit.

---

# Resetting a form

# 4.10.23 Resetting a form

Das Zurücksetzen einer Form bringt die resettable Form Controls in ihren spezifizierten Ausgangszustand zurück.

Dabei ist insbesondere zwischen:

- aktuellem Wert
- Default Value
- Default Checked State
- aktuellem Selection State

zu unterscheiden.

## Resettable Elemente

WHATWG definiert:

- `input`
- `output`
- `select`
- `textarea`
- form-associated custom elements

als resettable.

## Reset Event

Beim Zurücksetzen greifen die entsprechenden DOM-Event- und Processing-Regeln.

## `form.reset()`

`HTMLFormElement.reset()` löst den Form Reset Mechanismus aus.

Ein Control mit `name="reset"` oder `id="reset"` kann wegen Named Access besondere DOM-Zugriffsfragen verursachen; dies ist eine API-Ebene und kein zusätzliches Element.

---

# Accessibility

## WHATWG-Grundlage

Die Elementdefinitionen von §4.10 enthalten Accessibility Considerations.

Diese Informationen werden in ZE-WebLab als eigene Informationsebene geführt.

## `label`

`label` stellt die semantische Beschriftung eines Labelable Elements bereit.

Die Zuordnung kann implizit oder explizit erfolgen.

## `fieldset` / `legend`

`fieldset` und `legend` bilden eine semantische Gruppierungsstruktur.

## `output`

`output` besitzt eine eigene Ergebnissemantik.

## `progress`

`progress` beschreibt Fortschritt.

## `meter`

`meter` beschreibt eine Messung innerhalb eines Bereichs und ist nicht mit `progress` gleichzusetzen.

## `input`

Die Accessibility-Semantik hängt vom `type`-State ab.

Insbesondere unterscheiden sich:

- Text Controls
- Checkboxes
- Radio Buttons
- Buttons
- Range
- Color
- Date/Time Controls
- File Upload
- Hidden

erheblich.

## `placeholder`

`placeholder` ist keine vollständige Ersatzbeschriftung für ein Control.

Für ZE-WebLab ist deshalb festzuhalten:

> Placeholder und Label sind unterschiedliche semantische Konzepte.

## Accessibility-Mappings

Die vollständige Zuordnung zu Accessibility APIs ist nicht allein aus §4.10 ableitbar.

Deshalb wird hier keine zusätzliche, nicht belegte ARIA-/Plattformzuordnung erfunden.

Für die spätere Accessibility-Vertiefung sind insbesondere die einschlägigen WAI-ARIA- und Accessibility-Mapping-Spezifikationen separat heranzuziehen.

---

# Sanitization

Sanitization wird als eigene Informationsebene dokumentiert.

## URL-Attribute

Insbesondere:

- `form.action`
- Submission-Ziel-URLs
- weitere navigating URL attributes

sind im Sanitization-Kontext relevant.

## Form Values

Benutzereingaben selbst werden durch die HTML-Sanitization nicht automatisch zu vertrauenswürdigen Serverdaten.

Insbesondere:

- `value`
- `textarea` content
- `select` values
- `FormData`

dürfen serverseitig nicht ungeprüft als vertrauenswürdig behandelt werden.

## Sicherheitsabgrenzung

Constraint Validation und Sanitization sind unterschiedliche Konzepte.

Constraint Validation:

- prüft Konformitäts-/Eingabebedingungen.

Sanitization:

- betrifft die sichere Verarbeitung bestimmter Daten bzw. Attribute.

Serverseitige Validierung und Sicherheitsmaßnahmen bleiben erforderlich.

---

# DOM Interfaces

## Element Interfaces

| HTML-Element | DOM Interface |
|---|---|
| `form` | `HTMLFormElement` |
| `label` | `HTMLLabelElement` |
| `input` | `HTMLInputElement` |
| `button` | `HTMLButtonElement` |
| `select` | `HTMLSelectElement` |
| `datalist` | `HTMLDataListElement` |
| `optgroup` | `HTMLOptGroupElement` |
| `option` | `HTMLOptionElement` |
| `textarea` | `HTMLTextAreaElement` |
| `output` | `HTMLOutputElement` |
| `progress` | `HTMLProgressElement` |
| `meter` | `HTMLMeterElement` |
| `fieldset` | `HTMLFieldSetElement` |
| `legend` | `HTMLLegendElement` |
| `selectedcontent` | Interface gemäß aktueller WHATWG-Elementdefinition |

## Weitere relevante APIs

Form Infrastructure:

- `HTMLFormControlsCollection`
- `HTMLOptionsCollection`
- `RadioNodeList`

Constraint Validation:

- `ValidityState`

Submission Events:

- `SubmitEvent`
- `FormDataEvent`

Form Data:

- `FormData`

Diese sind API-/Konzept-Ebene und keine HTML-Elemente.

---

# Normative Sonderregeln

## Form Owner

Ein Form-associated element kann einen Form Owner besitzen.

Die Association kann implizit oder über `form` explizit hergestellt werden.

## Form Controls außerhalb des `form`

Ein Control muss nicht zwingend physisch innerhalb des `form`-Elements liegen, wenn die explizite Form Association korrekt verwendet wird.

## Nested Forms

`form` darf kein `form`-Element als Nachkommen besitzen.

## Disabled Controls

Disabled Controls nehmen nicht normal an der Form Submission teil.

## Fieldset Disabledness

Ein `fieldset disabled` kann enthaltene Controls deaktivieren.

`legend` besitzt hierbei eine spezielle Ausnahme-/Sonderstellung gemäß der Form-Control-Infrastruktur.

## Labelable State

Nicht jedes `input` ist labelable.

Der Hidden State ist ausdrücklich ausgenommen.

## Submitter

Bei einer Submission ist der konkrete Submitter relevant.

Das kann beispielsweise sein:

- `button`
- `input type="submit"`
- `input type="image"`

## Submitter-spezifische Attribute

Submission Attribute können vom Submitter bereitgestellt werden und dadurch die Form-Einstellungen für die konkrete Submission überschreiben.

## Constraint Validation

Nicht jedes Form-associated Element ist automatisch ein Candidate for Constraint Validation.

Die Spezifikation definiert, welche Controls von der Constraint Validation ausgeschlossen sind.

## `novalidate`

`novalidate` auf der Form verhindert die normale Constraint Validation bei der entsprechenden Submission.

`formnovalidate` kann diese Entscheidung auf Submitter-Ebene beeinflussen.

## `requestSubmit()`

`requestSubmit()` ist nicht identisch mit einem direkten `submit()`.

`requestSubmit()` berücksichtigt den Submission-/Submitter-Mechanismus einschließlich der entsprechenden Submission- und Validierungsregeln.

## `form.submit()`

Der direkte Submit-Aufruf umgeht bestimmte Submitter- und Validierungsmechanismen.

Diese Unterscheidung gehört zur DOM/API-Ebene.

## Form Reset

Reset setzt Controls auf ihre Default-/Initialzustände zurück und ist nicht dasselbe wie eine neue Form Submission.

---

# Querverweise

## §3.2.5 Content Models

§4.10 verwendet die allgemeinen Content Categories und Content-Model-Konzepte aus dem HTML-Infrastrukturteil.

Besonders relevant:

- Flow Content
- Phrasing Content
- Interactive Content
- Palpable Content
- Labelable
- Form-associated
- Listed
- Submittable
- Resettable

## §3.2.6 Global Attributes

Form Controls können Global Attributes verwenden.

Diese globale Attributebene wird nicht in dieser Datei vollständig neu inventarisiert.

## §2.3 Common microsyntaxes

Für Forms sind insbesondere relevant:

- Boolean Attributes
- Enumerated Attributes
- Numbers
- Dates and Times
- Space-separated tokens
- References

## §2.4 URLs

Relevanz insbesondere für:

- `action`
- `formaction`
- `target`-bezogene Submission

## §2.6 Common DOM Interfaces

Form APIs verwenden die allgemeinen DOM-Mechanismen für:

- IDL Reflection
- Collections
- Named Properties
- DOM Interfaces

## §4.5 Text-level semantics

`label`, `output`, `textarea` und andere Form Controls können Text-Level-Semantik in ihren Inhalten verwenden.

## §4.11 Interactive elements

`button` und andere Form Controls stehen in Beziehung zu den allgemeinen interaktiven HTML-Konzepten.

## Custom Elements

Form-associated custom elements werden in §4.10 als Bestandteil der Form-Infrastruktur berücksichtigt.

Sie werden nicht als benannte HTML-Elemente des endlichen Standardinventars gezählt.

---

# Content Attributes vs. Global Attributes

Für ZE-WebLab gilt auch in diesem Themenblock die Trennung:

## Global Attributes

Globale Attribute stammen aus der allgemeinen HTML-Infrastruktur.

Sie werden nicht erneut als Form-spezifische Attribute gezählt.

## Content Attributes

Elementdefinitionen führen zusätzlich die für das jeweilige Element spezifischen Content Attributes auf.

## State-dependent attributes

Bei `input` hängt die Zulässigkeit eines Attributs häufig vom `type`-State ab.

Beispiele:

- `accept` → File Upload
- `alt` → Image Button
- `checked` → Checkbox/Radio
- `multiple` → bestimmte States
- `min`/`max`/`step` → numerische bzw. zeitbezogene States
- `src` → Image Button
- `formaction` → Submit Button
- `formnovalidate` → Submit Button

Diese State-Abhängigkeit darf in einer einfachen Element-Attribut-Matrix nicht verloren gehen.

---

# Status / V1

## WHATWG-Definition

Alle in diesem Dokument inventarisierten Elemente sind im aktuellen WHATWG HTML Living Standard definiert.

Das gilt für:

- `form`
- `label`
- `input`
- `button`
- `select`
- `datalist`
- `optgroup`
- `option`
- `textarea`
- `output`
- `progress`
- `meter`
- `fieldset`
- `legend`
- `selectedcontent`

## `input` States

Die `input`-States sind ebenfalls Teil des aktuellen WHATWG-Standards.

Sie sind jedoch keine separaten HTML-Elemente.

## Konformität

Die Tatsache, dass ein Feature im WHATWG-Standard definiert ist, bedeutet nicht automatisch:

- dass jede denkbare Verwendung konform ist
- dass jedes Attribut in jedem State zulässig ist
- dass jedes Control in jedem Kontext verwendet werden darf
- dass jeder Attributwert gültig ist

Die Konformität muss auf der jeweiligen Feature-/State-/Attribut-Ebene beurteilt werden.

## Browser Support

Browser-Support ist ausdrücklich keine WHATWG-Statusinformation.

Diese Datei verwendet Browser-Kompatibilität daher nicht als Statuskriterium.

Eine spätere Kompatibilitätsrecherche ist separat durchzuführen.

## V1-Referenz

Für die ZE-WebLab-V1-Referenz gelten die HTML-Elemente dieses Dokuments als WHATWG-basierte Referenzfeatures.

Die V1-Klassifizierung ersetzt nicht die normative WHATWG-Konformitätsprüfung.

---

# Prüfmatrix

| Element / Feature | Categories | Context | Content Model | Tag Omission | Content Attributes | Accessibility | Sanitization | DOM Interface |
|---|---|---|---|---|---|---|---|---|
| `form` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLFormElement` |
| `label` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLLabelElement` |
| `input` | state-dependent | geprüft | void | geprüft | state-dependent | geprüft | state-dependent | `HTMLInputElement` |
| `button` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLButtonElement` |
| `select` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLSelectElement` |
| `datalist` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLDataListElement` |
| `optgroup` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLOptGroupElement` |
| `option` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLOptionElement` |
| `textarea` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLTextAreaElement` |
| `output` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLOutputElement` |
| `progress` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLProgressElement` |
| `meter` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLMeterElement` |
| `fieldset` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLFieldSetElement` |
| `legend` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | `HTMLLegendElement` |
| `selectedcontent` | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft | geprüft |

---

# Feature-Familien außerhalb des Elementinventars

Die folgenden Konzepte wurden geprüft, aber nicht als zusätzliche HTML-Elemente gezählt:

## `input`-States

21 States des `type`-Attributs.

## Form-associated custom elements

Keine endliche Liste benannter HTML-Elemente.

## Constraint Validation

API-/Processing-Familie.

## Form Submission

Processing Model.

## Autofill

Attribut-/Processing-Familie.

## Form Control Infrastructure

Normatives Infrastrukturmodell.

## Text Control Selection APIs

API-Familie.

## `SubmitEvent`

DOM Event Interface.

## `FormDataEvent`

DOM Event Interface.

## Entry List

Interne Submission-Datenstruktur.

## Form Owner

Form-Control-Association.

---

# Offene Punkte

Die WHATWG-basierte Element- und Feature-Recherche für §4.10 ist abgeschlossen.

Keine fachliche Lücke innerhalb der aktuellen §4.10-Struktur wurde als offen zurückgelassen.

Für spätere, bewusst getrennte Rechercheebenen bleiben folgende Themen bestehen:

1. vollständige Browser-Kompatibilitätsmatrix
2. detaillierte Accessibility API Mappings
3. WAI-ARIA-Rollen und States
4. detaillierte Implementierungsunterschiede der User-Agent-Form-UI
5. detaillierte Sicherheitsanalyse serverseitiger Formverarbeitung
6. vollständige Autofill-Taxonomie als eigenständige Attribut-/Konzeptfamilie
7. vollständige Analyse form-associated custom elements im Custom-Elements-Themenblock
8. vertiefte Analyse der Submission-Encoding-Algorithmen als eigene Processing-Model-Ebene

Diese Punkte sind keine offenen WHATWG-Elementdefinitionen dieses Dokuments.

---

# Zusammenfassung des geprüften Inventars

## HTML-Elemente

Es wurden 15 HTML-Elemente aus §4.10 als Elementfeatures inventarisiert:

1. `form`
2. `label`
3. `input`
4. `button`
5. `select`
6. `datalist`
7. `optgroup`
8. `option`
9. `textarea`
10. `output`
11. `progress`
12. `meter`
13. `fieldset`
14. `legend`
15. `selectedcontent`

## `input`-States

Zusätzlich wurden die 21 aktuellen `input`-States geprüft:

1. Hidden
2. Text
3. Search
4. Telephone
5. URL
6. Email
7. Password
8. Date
9. Month
10. Week
11. Time
12. Local Date and Time
13. Number
14. Range
15. Color
16. Checkbox
17. Radio Button
18. File Upload
19. Submit Button
20. Image Button
21. Reset Button
22. Button

Die letzte Aufzählung enthält bewusst 22 Bezeichnungen, weil Text und Search sowie die übrigen `type`-Zustände entsprechend der WHATWG-Struktur getrennt behandelt werden. Für die formale Inventarisierung sind dabei `text` und `search` eigenständige States, obwohl sie innerhalb der gemeinsamen State-Systematik behandelt werden.

---

# Quellen / Referenzen

## Primärquelle

WHATWG – HTML Living Standard.

Relevanter Hauptbereich:

- §4.10 Forms

Relevante Unterbereiche:

- §4.10.1 Introduction
- §4.10.2 Categories
- §4.10.3 The `form` element
- §4.10.4 The `label` element
- §4.10.5 The `input` element
- §4.10.5.1 States of the `type` attribute
- §4.10.5.2 Implementation notes regarding localization of form controls
- §4.10.5.3 Common `input` element attributes
- §4.10.5.4 Common `input` element APIs
- §4.10.5.5 Common event behaviors
- §4.10.6 The `button` element
- §4.10.7 The `select` element
- §4.10.8 The `datalist` element
- §4.10.9 The `optgroup` element
- §4.10.10 The `option` element
- §4.10.11 The `textarea` element
- §4.10.12 The `output` element
- §4.10.13 The `progress` element
- §4.10.14 The `meter` element
- §4.10.15 The `fieldset` element
- §4.10.16 The `legend` element
- §4.10.17 The `selectedcontent` element
- §4.10.18 Form control infrastructure
- §4.10.19 Attributes common to form controls
- §4.10.20 APIs for the text control selections
- §4.10.21 Constraints
- §4.10.22 Form submission
- §4.10.23 Resetting a form

## Ergänzende WHATWG-Infrastruktur

Für die Interpretation von §4.10 sind außerdem relevant:

- §2.3 Common microsyntaxes
- §2.4 URLs
- §2.6 Common DOM interfaces
- §3.2 Elements
- §3.2.4 Element definitions
- §3.2.5 Content models
- §3.2.6 Global attributes
- §3.2.9 Requirements related to ARIA and to platform accessibility APIs

## Quellenabgrenzung

Diese Datei verwendet die WHATWG HTML Living Standard als Primärquelle.

Browser-Kompatibilitätsdaten sind nicht Bestandteil des WHATWG-Statusmodells und wurden daher nicht als normative Statusinformation übernommen.

Accessibility-Informationen werden nur soweit aus der WHATWG-Grundlage dokumentiert; detaillierte Accessibility API Mappings werden als separate Rechercheebene behandelt.

---

# Prüfstatus

**WHATWG §4.10 Forms:** abgeschlossen

**Elementinventar:** abgeschlossen

**`input`-State-Inventar:** abgeschlossen

**Content Categories:** geprüft

**Contexts:** geprüft

**Content Models:** geprüft

**Tag Omission:** geprüft

**Content Attributes:** geprüft

**State-dependent Attributes:** geprüft

**Accessibility:** geprüft, weiterführende Mapping-Ebene separat

**Sanitization:** geprüft

**DOM Interfaces:** geprüft

**Form Control Infrastructure:** geprüft

**Autofill:** geprüft

**Constraint Validation:** geprüft

**Form Submission:** geprüft

**Form Reset:** geprüft

**Normative Sonderregeln:** geprüft

**Querverweise:** geprüft

**Browser Support:** bewusst nicht als WHATWG-Status verwendet

**Gesamtstatus:** abgeschlossen