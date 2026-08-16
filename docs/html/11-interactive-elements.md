# ZE-WebLab – HTML-Referenz: Interactive elements

## Arbeitsstand / Quellenstand

- **Projekt:** ZE-WebLab
- **Datei:** `docs/html/11-interactive-elements.md`
- **Themenbereich:** HTML Interactive elements
- **WHATWG-Hauptabschnitt:** §4.11 Interactive elements
- **Recherchetyp:** WHATWG-Primärquellenrecherche
- **Prüfstand:** 2026-08-16
- **Spezifikationsstand der recherchierten WHATWG-Seite:** Living Standard, zuletzt aktualisiert am 2026-08-11
- **Primärquelle:** WHATWG HTML Living Standard, §4.11 Interactive elements
- **Browser-Support:** Nicht Bestandteil des WHATWG-Statusmodells dieser Datei
- **Accessibility:** Nur die in bzw. über die WHATWG-Spezifikation referenzierten Informationen werden hier dokumentiert; eine vollständige Accessibility-Analyse erfolgt auf der dafür vorgesehenen späteren Ebene.

Diese Datei behandelt den WHATWG-Abschnitt §4.11 vollständig.

Dabei wird zwischen tatsächlichen HTML-Elementen und den in §4.11 beschriebenen Konzepten unterschieden.

Der Abschnitt enthält insbesondere:

- das Element `details`
- das Element `summary`
- das Konzept der Commands
- das Element `dialog`
- das Dialog-Light-Dismiss-Verarbeitungsmodell

Die Unterabschnitte zu Commands definieren keine neuen HTML-Elemente. Sie beschreiben vielmehr ein abstraktes Command-Modell und legen fest, unter welchen Bedingungen bereits existierende Elemente Commands definieren.

Daher werden `a`, `button`, `input`, `option` und `legend` in dieser Datei nicht nochmals als neue HTML-Elemente inventarisiert. Ihre Rolle im Command-Modell wird jedoch vollständig dokumentiert.

---

## WHATWG-Struktur

Der aktuelle WHATWG-Abschnitt §4.11 ist wie folgt aufgebaut:

### 4.11 Interactive elements

1. **4.11.1 The `details` element**
2. **4.11.2 The `summary` element**
3. **4.11.3 Commands**
   1. **4.11.3.1 Facets**
   2. **4.11.3.2 Using the `a` element to define a command**
   3. **4.11.3.3 Using the `button` element to define a command**
   4. **4.11.3.4 Using the `input` element to define a command**
   5. **4.11.3.5 Using the `option` element to define a command**
   6. **4.11.3.6 Using the `accesskey` attribute on a `legend` element to define a command**
   7. **4.11.3.7 Using the `accesskey` attribute to define a command on other elements**
4. **4.11.4 The `dialog` element**
5. **4.11.5 Dialog light dismiss**

Damit ist §4.11 nicht lediglich eine Sammlung von drei interaktiven Elementen. Er enthält zusätzlich ein eigenes abstraktes Command-Modell sowie normative Verarbeitungsmodelle für Dialoge.

---

## Inventar

### Elementinventar

| Feature | Feature-Typ | WHATWG-Abschnitt | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|---|
| `details` | HTML-Element | §4.11.1 | Flow, Interactive, Palpable | Wo Flow Content erwartet wird | Ein `summary`-Element, gefolgt von Flow Content | Keine Auslassung | Global Attributes, `name`, `open` | Uncategorized | `HTMLDetailsElement` | Im WHATWG-Standard definiert |
| `summary` | HTML-Element | §4.11.2 | Keine | Als erstes Kind eines `details`-Elements | Phrasing Content, optional mit Heading Content vermischt | Keine Auslassung | Global Attributes | Uncategorized | `HTMLElement` | Im WHATWG-Standard definiert |
| `dialog` | HTML-Element | §4.11.4 | Flow | Wo Flow Content erwartet wird | Flow Content | Keine Auslassung | Global Attributes, `closedby`, `open` | Uncategorized | `HTMLDialogElement` | Im WHATWG-Standard definiert |

### Konzeptinventar

| Feature | Feature-Typ | WHATWG-Abschnitt | Bedeutung |
|---|---|---|---|
| Commands | abstraktes HTML-Konzept | §4.11.3 | Abstraktion hinter bestimmten Menüpunkten, Buttons und Links |
| Command Facets | Unterkonzept | §4.11.3.1 | Label, Access Key, Hidden State, Disabled State und Action |
| Command über `a` | Verarbeitungs-/Definitionsregel | §4.11.3.2 | Ein `a` mit `href` definiert einen Command |
| Command über `button` | Verarbeitungs-/Definitionsregel | §4.11.3.3 | Ein `button` definiert immer einen Command |
| Command über `input` | Verarbeitungs-/Definitionsregel | §4.11.3.4 | Bestimmte `input`-States definieren einen Command |
| Command über `option` | Verarbeitungs-/Definitionsregel | §4.11.3.5 | Bestimmte `option`-Elemente innerhalb eines `select` definieren einen Command |
| Command über `legend` + `accesskey` | Verarbeitungsregel | §4.11.3.6 | Ein `legend` kann einen Command über Access-Key-Delegation definieren |
| Command über `accesskey` | Verarbeitungsregel | §4.11.3.7 | Ein Element mit zugewiesenem Access Key kann einen Command definieren |
| Dialog light dismiss | Verarbeitungsmodell | §4.11.5 | Normatives Verhalten zum Schließen eines Dialogs durch Interaktion außerhalb des Dialogs |

---

# Detailprüfung: `details`

## WHATWG-Zuordnung

- **Element:** `details`
- **Abschnitt:** §4.11.1 The `details` element
- **Feature-Typ:** HTML-Element
- **Definition:** Disclosure Widget

Das `details`-Element repräsentiert ein Disclosure Widget, über das der Benutzer zusätzliche Informationen oder Controls erhalten kann.

Die Spezifikation grenzt `details` ausdrücklich von anderen Interaktionsmustern ab.

Ein `details`-Element darf insbesondere nicht missbräuchlich eingesetzt werden, um andere Control-Typen zu simulieren.

Beispiele für ausdrücklich nicht passende Verwendungen sind:

- Tab Widgets
- Menu Widgets

Das Element ist außerdem nicht für Fußnoten vorgesehen.

---

## Content Categories

`details` gehört zu folgenden Content Categories:

- Flow Content
- Interactive Content
- Palpable Content

Damit ist `details` insbesondere selbst Interactive Content.

---

## Context

Das `details`-Element darf dort verwendet werden, wo Flow Content erwartet wird.

---

## Content Model

Das Content Model lautet:

1. ein `summary`-Element
2. danach Flow Content

Die Spezifikation beschreibt das Modell als:

```text
One summary element followed by flow content.
```

Das `summary`-Element bildet dabei die spezielle Zusammenfassung bzw. Legende des Disclosure Widgets.

Der übrige Inhalt repräsentiert die zusätzlichen Informationen oder Controls.

### Bedeutung des ersten `summary`

Das erste `summary`-Element-Kind von `details` repräsentiert die Zusammenfassung bzw. Legende.

Existiert kein `summary`-Element-Kind, soll der User Agent eine eigene Legende bereitstellen.

Die Spezifikation nennt als mögliches Beispiel eine automatisch bereitgestellte Beschriftung wie `Details`.

Für die Konformitätsprüfung ist entscheidend, dass das Content Model ein `summary` als erstes Element vorsieht.

---

## Tag Omission

Für `details` gilt:

- Start-Tag darf nicht ausgelassen werden.
- End-Tag darf nicht ausgelassen werden.

Damit gilt:

```html
<details>
  ...
</details>
```

als vollständige erforderliche Markup-Struktur.

---

## Content Attributes

`details` besitzt zusätzlich zu den Global Attributes:

- `name`
- `open`

### `name`

`name` benennt die Gruppe verwandter `details`-Elemente.

Mehrere `details`-Elemente mit demselben nichtleeren `name` innerhalb desselben Trees bilden eine gemeinsame Details Name Group.

Diese Gruppe ist exklusiv:

- höchstens ein Element der Gruppe kann gleichzeitig geöffnet sein
- das Öffnen eines Gruppenmitglieds schließt gegebenenfalls ein anderes geöffnetes Gruppenmitglied

Wenn `name` angegeben wird, darf sein Wert nicht leer sein.

Die Spezifikation enthält zusätzlich Regeln für die Struktur solcher Gruppen.

Ein Dokument darf insbesondere nicht mehr als ein geöffnetes `details`-Element derselben Details Name Group enthalten.

Ebenso darf ein `details`-Element nicht Nachfahre eines anderen `details`-Elements derselben Details Name Group sein.

Die Spezifikation empfiehlt außerdem, zusammengehörige Elemente einer solchen Gruppe räumlich zusammenzuhalten, beispielsweise innerhalb eines `section`- oder `article`-Elements.

Wenn eine Überschrift für eine solche Gruppe sinnvoll ist, soll diese am Anfang des umgebenden Containers stehen.

### `open`

`open` ist ein Boolean Attribute.

Ist `open` vorhanden:

- werden die Zusammenfassung und die zusätzlichen Informationen angezeigt.

Ist `open` nicht vorhanden:

- wird nur die Zusammenfassung angezeigt.

Das Attribut stellt damit den sichtbaren geöffnet/geschlossen-Zustand des Disclosure Widgets dar.

---

## `open` und Benutzerinteraktion

Der User Agent soll dem Benutzer ermöglichen, den zusätzlichen Inhalt ein- und auszublenden.

Beim Öffnen wird das `open`-Attribut gesetzt.

Beim Schließen wird das `open`-Attribut entfernt.

Das kann insbesondere über die Aktivierungslogik des passenden `summary`-Elements erfolgen.

Wenn kein passendes `summary` vorhanden ist, kann der User Agent eine andere Benutzeroberfläche bereitstellen.

---

## Details Name Group

Eine Details Name Group umfasst die anderen `details`-Elemente, die:

- sich im selben Tree befinden
- ein `name`-Attribut besitzen
- ein nichtleeres `name`-Attribut besitzen
- denselben `name`-Wert besitzen

Die Gruppierung ist damit nicht einfach eine CSS- oder JavaScript-Konvention, sondern Bestandteil des normativen HTML-Verhaltens.

### Exklusivität

Wenn ein Element einer solchen Gruppe geöffnet wird, wird ein anderes geöffnetes Gruppenmitglied geschlossen.

Der User Agent entfernt hierzu das `open`-Attribut des anderen Elements.

Dadurch verändert sich der tatsächlich vorhandene Markup-Zustand.

Autoren dürfen deshalb kein Markup erzeugen, das dauerhaft mehrere gleichzeitig geöffnete Mitglieder derselben exklusiven Gruppe vorgibt.

Auch Script darf keine Elemente in einer Weise hinzufügen, durch die eine solche Gruppe mehrere gleichzeitig geöffnete Mitglieder erhält.

---

## Details Toggle Processing

Jedes `details`-Element besitzt einen internen Details Toggle Task Tracker.

Dieser wird für die Verarbeitung von Zustandsänderungen des `open`-Attributs verwendet.

Wenn sich das Vorhandensein des `open`-Attributs ändert, werden Details Notification Task Steps ausgelöst.

Der resultierende `toggle`-Event verwendet `ToggleEvent`.

Die Zustände werden als:

- `closed`
- `open`

modelliert.

Bei mehrfachen schnellen Änderungen können die zugehörigen Tasks zusammengeführt werden.

Dadurch wird verhindert, dass für jede einzelne schnelle Zustandsänderung zwingend ein separates Ereignis ausgelöst wird.

---

## Normative Exklusivitätsverarbeitung

Beim Setzen des `open`-Attributs wird bei einem `details`-Element mit nichtleerem `name` geprüft, ob andere Mitglieder derselben Details Name Group geöffnet sind.

Ist ein anderes Gruppenmitglied geöffnet:

- wird dessen `open`-Attribut entfernt
- die Verarbeitung beendet sich für diesen Schritt

Beim Einfügen eines `details`-Elements wird ebenfalls die Exklusivität geprüft.

Damit gilt die Exklusivität nicht nur für Benutzerinteraktion, sondern auch für programmatische und parserbedingte Änderungen am DOM.

---

## Accessibility-Aspekte

Die WHATWG-Sektion enthält für `details` separate Accessibility Considerations:

- For authors
- For implementers

Die Spezifikation weist insbesondere darauf hin, dass das Gruppieren verwandter `details`-Elemente für zugängliche Benutzeroberflächen relevant sein kann.

Visuelles und programmatisches Gruppieren zusammengehöriger Elemente kann Benutzern helfen, die Beziehung zwischen den einzelnen Elementen zu verstehen.

Die WHATWG-Spezifikation liefert in diesem Abschnitt keine vollständige Accessibility-Rollen-/States-/Properties-Matrix.

Daher werden hier keine zusätzlichen ARIA-Zuordnungen erfunden.

Eine vertiefte Accessibility-Prüfung gehört in die dafür vorgesehene separate Referenzebene.

---

## Sanitization

Die aktuelle WHATWG-Definition weist für `details`:

- Sanitization: `Uncategorized`

aus.

Diese Angabe ist nicht mit einer Aussage gleichzusetzen, dass das Element grundsätzlich unsicher oder unsanitized sei.

Für die ZE-WebLab-Referenz bedeutet die Angabe lediglich:

- Die WHATWG-Spezifikation klassifiziert `details` an dieser Stelle als `Uncategorized`.
- Eine zusätzliche, elementeigene Sanitization-Regel wird in diesem Elementabschnitt nicht als eigene Kategorie ausgewiesen.

---

## DOM Interface

Das DOM Interface ist:

```webidl
[Exposed=Window]
interface HTMLDetailsElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, Reflect] attribute DOMString name;
  [CEReactions, Reflect] attribute boolean open;
};
```

Damit besitzt `details` ein eigenes Interface:

```text
HTMLDetailsElement
```

Die beiden wesentlichen reflektierten Attribute sind:

- `name`
- `open`

---

## Fachliche Beispiele

### Einfaches Disclosure Widget

```html
<details>
  <summary>Weitere Informationen</summary>
  <p>Zusätzliche Informationen werden hier angezeigt.</p>
</details>
```

### Standardmäßig geöffnet

```html
<details open>
  <summary>Weitere Informationen</summary>
  <p>Dieser Inhalt ist zunächst sichtbar.</p>
</details>
```

### Exklusive Gruppe

```html
<section>
  <details name="characteristics">
    <summary>Material</summary>
    <p>Massives Eichenholz.</p>
  </details>

  <details name="characteristics">
    <summary>Größe</summary>
    <p>45 cm × 35 cm.</p>
  </details>

  <details name="characteristics">
    <summary>Farbe</summary>
    <p>Naturholz oder schwarze Beize.</p>
  </details>
</section>
```

Hier bilden die drei `details`-Elemente aufgrund desselben nichtleeren `name`-Werts eine Details Name Group.

---

# Detailprüfung: `summary`

## WHATWG-Zuordnung

- **Element:** `summary`
- **Abschnitt:** §4.11.2 The `summary` element
- **Feature-Typ:** HTML-Element
- **DOM Interface:** `HTMLElement`

`summary` repräsentiert eine Zusammenfassung, Beschriftung oder Legende für den übrigen Inhalt seines übergeordneten `details`-Elements.

---

## Content Categories

Die WHATWG-Spezifikation weist für `summary` keine Content Categories aus.

Daher wird für die ZE-WebLab-Matrix ausdrücklich festgehalten:

```text
Content Categories: None
```

Dies ist nicht dasselbe wie eine fehlende Recherche.

---

## Context

`summary` darf verwendet werden:

- als erstes Kind eines `details`-Elements.

Der Kontext ist damit wesentlich restriktiver als beim `details`-Element.

---

## Content Model

Das Content Model lautet:

- Phrasing Content
- optional vermischt mit Heading Content

Die Spezifikation erlaubt damit insbesondere Heading Content innerhalb des `summary`-Content-Modells, ohne das Element selbst als Heading Content Element zu klassifizieren.

---

## Tag Omission

Für `summary` gilt:

- Start-Tag darf nicht ausgelassen werden.
- End-Tag darf nicht ausgelassen werden.

---

## Content Attributes

`summary` besitzt keine eigenen elementbezogenen Content Attributes.

Es gelten:

- Global Attributes

---

## Definition eines gültigen Summary für `details`

Nicht jedes beliebige `summary`-Element innerhalb eines `details`-Elements wird automatisch als dessen funktionales Summary behandelt.

Die Spezifikation definiert hierfür eine konkrete Prüfung.

Ein `summary` ist Summary für sein Parent-`details`, wenn:

1. das `summary` einen Parent besitzt,
2. dieser Parent ein `details`-Element ist,
3. das `summary` das erste `summary`-Element-Kind dieses `details`-Elements ist.

Erst dann erfüllt das Element die spezifizierte Summary-Rolle innerhalb dieses `details`.

---

## Aktivierungsverhalten

Das Aktivierungsverhalten des funktionalen `summary` ist:

1. Prüfen, ob das `summary` tatsächlich das Summary seines Parent-`details` ist.
2. Wenn nicht, keine weitere Aktion.
3. Das Parent-`details` bestimmen.
4. Ist `open` vorhanden, wird es entfernt.
5. Ist `open` nicht vorhanden, wird es auf den leeren String gesetzt.
6. Dadurch wird die Details Notification Task-Verarbeitung ausgelöst.

Damit ist die Benutzerinteraktion mit dem Disclosure Widget direkt mit dem `open`-Zustand von `details` verbunden.

---

## Accessibility-Aspekte

Die WHATWG-Spezifikation weist für `summary` eigene Accessibility Considerations aus:

- For authors
- For implementers

Der Abschnitt definiert jedoch keine vollständige externe Accessibility-Mapping-Tabelle.

Daher wird in dieser Datei keine zusätzliche ARIA-Rolle oder Accessibility-API-Zuordnung als WHATWG-Fakt ergänzt.

---

## Sanitization

Die WHATWG-Spezifikation weist für `summary`:

- Sanitization: `Uncategorized`

aus.

Es wird an dieser Stelle keine zusätzliche elementeigene Sanitization-Regel als eigener Verarbeitungsmechanismus definiert.

---

## DOM Interface

`summary` verwendet:

```text
HTMLElement
```

Es besitzt in §4.11 kein eigenes spezifiziertes DOM-Interface.

---

## Fachliches Beispiel

```html
<details>
  <summary>Versandinformationen</summary>
  <p>Der Versand erfolgt innerhalb von zwei Werktagen.</p>
</details>
```

Das `summary` ist hier das erste Element-Kind des `details` und damit dessen funktionales Summary.

---

# Commands

## Einordnung

§4.11.3 definiert das Konzept der Commands.

Commands sind keine neuen HTML-Elemente.

Sie sind eine Abstraktion hinter:

- Menu Items
- Buttons
- Links

Die Spezifikation ermöglicht damit, dass verschiedene Teile einer Benutzeroberfläche auf dieselbe Art von auslösbarer Aktion Bezug nehmen können.

Für die ZE-WebLab-Inventarisierung ist deshalb wichtig:

> `command` ist in §4.11.3 ein Feature-/Konzeptbereich und kein zusätzliches HTML-Element.

---

## Command Facets

Ein Command besitzt folgende Facets:

1. Label
2. Access Key
3. Hidden State
4. Disabled State
5. Action

Diese fünf Facets bilden das zentrale Modell des Command-Konzepts.

---

## Label

Das Label ist der für den Benutzer sichtbare Name des Commands.

Wie dieses Label bestimmt wird, hängt vom Element ab, das den Command definiert.

---

## Access Key

Der Access Key ist eine vom User Agent ausgewählte Tastenkombination, durch die der Command ausgelöst werden kann.

Ein Command muss nicht zwingend einen Access Key besitzen.

---

## Hidden State

Der Hidden State gibt an, ob der Command verborgen ist.

Ein sichtbarer Command kann vom User Agent beispielsweise in Menüs exponiert werden.

Die WHATWG-Spezifikation beschreibt insbesondere die Bedingungen, unter denen User Agents Commands exponieren dürfen.

Dazu gehört:

- Hidden State ist nicht gesetzt.
- Das Element befindet sich in einem Dokument mit Browsing Context.
- Weder das Element noch einer seiner Vorfahren besitzt das `hidden`-Attribut.

User Agents werden insbesondere für Commands mit Access Keys dazu ermutigt, diese sichtbar bzw. auffindbar zu machen.

---

## Disabled State

Der Disabled State beschreibt, ob ein Command relevant und auslösbar ist.

Wie der Disabled State bestimmt wird, hängt vom definierenden Element ab.

Typische Faktoren sind:

- `inert`
- der eigene Disabled State eines Form Controls
- der Disabled State eines umgebenden `select`

---

## Action

Die Action beschreibt die eigentliche Wirkung des Commands.

Die WHATWG-Spezifikation nennt als mögliche Formen unter anderem:

- einen Script-basierten Event Handler
- Navigation zu einer URL
- Form Submission

Die konkrete Action ist vom jeweiligen Element abhängig.

---

# Commands: `a`

## WHATWG-Abschnitt

§4.11.3.2 – Using the `a` element to define a command

Ein `a`-Element mit `href` definiert einen Command.

`a` wird dadurch nicht zu einem neuen Elementtyp.

---

## Command Facets von `a`

### Label

Das Label ist der Descendant Text Content des Elements.

### Access Key

Der Access Key entspricht dem dem Element zugewiesenen Access Key, sofern vorhanden.

### Hidden State

Der Hidden State ist `true`, wenn das Element ein `hidden`-Attribut besitzt.

Andernfalls ist er `false`.

### Disabled State

Der Disabled State ist `true`, wenn:

- das Element selbst inert ist,
- oder einer seiner Vorfahren inert ist.

Andernfalls ist er `false`.

### Action

Die Action besteht darin, ein `click`-Event am Element auszulösen.

---

# Commands: `button`

## WHATWG-Abschnitt

§4.11.3.3 – Using the `button` element to define a command

Ein `button`-Element definiert immer einen Command.

Auch hier entsteht kein neues Elementinventar.

---

## Command Facets von `button`

Label, Access Key, Hidden State und Action werden nach den Regeln für `a` bestimmt.

Der Disabled State unterscheidet sich:

Er ist `true`, wenn:

- das Element selbst inert ist,
- ein Vorfahr inert ist,
- oder der Disabled State des Buttons gesetzt ist.

---

## Beziehung zum aktuellen Button-Modell

Die aktuelle WHATWG-Spezifikation behandelt `command` und `commandfor` zusätzlich direkt beim `button`-Element.

Dabei kann ein Button ein Ziel-Element über `commandfor` adressieren.

Das konkrete Attribut- und Aktivierungsmodell des Buttons gehört primär in die Form-Control-Dokumentation.

Für §4.11 ist relevant, dass ein Button im Command-Modell als Command-Quelle fungiert und Dialoge über die vorgesehenen Dialog-Command-Zustände adressieren kann.

---

# Commands: `input`

## WHATWG-Abschnitt

§4.11.3.4 – Using the `input` element to define a command

Ein `input`-Element definiert einen Command, wenn sein `type`-Attribut in einem der folgenden States ist:

- Submit Button
- Reset Button
- Image Button
- Button
- Radio Button
- Checkbox

---

## Label-Bestimmung

Für Submit Button, Reset Button, Image Button und Button wird das Label aus dem `value`-Attribut bzw. einer User-Agent-/Locale-abhängigen Button-Beschriftung bestimmt.

Für Radio Button und Checkbox gilt eine andere Label-Bestimmung.

Wenn das Element ein gelabeltes Control ist, wird der Descendant Text Content des ersten passenden `label`-Elements in Tree Order verwendet.

Andernfalls kann der `value`-Wert verwendet werden.

Wenn auch dieser fehlt, ist das Label der leere String.

---

## Sonderfall Image Button

Die Spezifikation weist ausdrücklich darauf hin, dass ein `value`-Attribut bei einem `input` im Image Button State selbst nicht konform ist.

Es kann jedoch trotzdem bei der Label-Bestimmung berücksichtigt werden, wenn das `alt`-Attribut fehlt.

Diese Regel ist für die Trennung zwischen Konformitätsprüfung und tatsächlichem User-Agent-Verhalten relevant.

---

## Weitere Command Facets

### Access Key

Der dem Element zugewiesene Access Key.

### Hidden State

`true`, wenn das Element `hidden` besitzt.

### Disabled State

`true`, wenn:

- das Element inert ist,
- ein Vorfahr inert ist,
- oder der eigene Disabled State gesetzt ist.

### Action

Die Action besteht darin, ein `click`-Event am Element auszulösen.

---

# Commands: `option`

## WHATWG-Abschnitt

§4.11.3.5 – Using the `option` element to define a command

Ein `option`-Element definiert einen Command, wenn:

- es einen `select`-Ancestor besitzt,
- und entweder kein `value`-Attribut besitzt,
- oder sein `value`-Attribut nicht leer ist.

---

## Label

Das Label ist:

1. der Wert des `label`-Attributs, wenn vorhanden,
2. andernfalls der Descendant Text Content des `option`-Elements,
3. wobei ASCII Whitespace entfernt und zusammengefasst wird.

---

## Access Key

Der Access Key entspricht dem zugewiesenen Access Key des Elements.

---

## Hidden State

Der Hidden State ist `true`, wenn das Element `hidden` besitzt.

---

## Disabled State

Der Disabled State ist `true`, wenn:

- das `option` selbst disabled ist,
- das nächste übergeordnete `select` disabled ist,
- das Element oder einer seiner Vorfahren inert ist.

---

## Action

Die Action hängt vom `multiple`-Zustand des zugehörigen `select` ab.

Wenn das nächste übergeordnete `select` das `multiple`-Attribut besitzt:

- die Option wird getoggelt.

Andernfalls:

- die Option wird ausgewählt.

---

# Commands: `legend` und `accesskey`

## WHATWG-Abschnitt

§4.11.3.6 – Using the `accesskey` attribute on a `legend` element to define a command

Ein `legend`-Element definiert einen Command, wenn alle folgenden Bedingungen erfüllt sind:

1. Es besitzt einen zugewiesenen Access Key.
2. Es ist Kind eines `fieldset`.
3. Sein Parent besitzt einen Descendant, der einen Command definiert.
4. Dieser Delegatee ist weder ein `label`- noch ein `legend`-Element.

Das betreffende Element wird als Access-Key-Delegatee des `legend` bezeichnet.

---

## Command Facets

### Label

Das Label ist der Descendant Text Content des `legend`.

### Access Key

Der Access Key ist der zugewiesene Access Key des `legend`.

### Hidden State

Der Hidden State wird vom Access-Key-Delegatee übernommen.

### Disabled State

Der Disabled State wird vom Access-Key-Delegatee übernommen.

### Action

Die Action wird vom Access-Key-Delegatee übernommen.

Damit delegiert das `legend` nicht nur den Zugriff, sondern übernimmt die relevanten Command-Facets des Ziel-Controls.

---

## Beispiel

```html
<fieldset>
  <legend accesskey="p">
    <label>
      Anzahl Pizzen:
      <input
        name="pizza"
        type="number"
        step="1"
        value="1"
        min="0">
    </label>
  </legend>

  <label>
    <input name="pizza-cheese" type="checkbox" checked>
    Käse
  </label>

  <label>
    <input name="pizza-ham" type="checkbox" checked>
    Schinken
  </label>

  <label>
    <input name="pizza-pineapple" type="checkbox">
    Ananas
  </label>
</fieldset>
```

Hier kann der Access Key des `legend` an das relevante Control delegiert werden.

---

# Commands über `accesskey` auf anderen Elementen

## WHATWG-Abschnitt

§4.11.3.7 – Using the `accesskey` attribute to define a command on other elements

Ein Element mit einem zugewiesenen Access Key definiert grundsätzlich einen Command.

Allerdings gilt die Regel aus §4.11.3.7 nur dann, wenn kein früherer, elementspezifischer Command-Abschnitt bereits definiert, wie dieses Element einen Command erzeugt.

Damit haben die spezifischeren Regeln Vorrang.

---

## Label

Ist das Element ein gelabeltes Control:

- wird der Descendant Text Content des ersten passenden `label`-Elements verwendet.

Andernfalls:

- wird der Descendant Text Content des Elements verwendet.

---

## Access Key

Der Access Key ist der dem Element zugewiesene Access Key.

---

## Hidden State

`true`, wenn das Element ein `hidden`-Attribut besitzt.

---

## Disabled State

`true`, wenn:

- das Element inert ist,
- oder ein Vorfahr inert ist.

---

## Action

Die Action besteht aus:

1. Ausführen der Focusing Steps für das Element.
2. Auslösen eines `click`-Events am Element.

---

# Detailprüfung: `dialog`

## WHATWG-Zuordnung

- **Element:** `dialog`
- **Abschnitt:** §4.11.4 The `dialog` element
- **Feature-Typ:** HTML-Element
- **Content Category:** Flow Content
- **DOM Interface:** `HTMLDialogElement`

Das `dialog`-Element repräsentiert einen vorübergehenden Teil einer Anwendung in Form eines kleinen Fensters bzw. Dialogfensters.

Es dient dazu:

- eine Aufgabe mit dem Benutzer durchzuführen,
- Informationen einzuholen,
- oder eine transitorische Interaktion abzubilden.

Die Spezifikation betont insbesondere bei modalen Dialogen die Erwartung, dass sie sich für Benutzer möglichst vertraut wie Dialoge in anderen Anwendungssystemen verhalten.

---

## Abgrenzung

`dialog` darf nicht missbräuchlich verwendet werden, um andere Control-Typen darzustellen.

Die Spezifikation nennt ausdrücklich:

- Context Menus
- Tooltips
- Popup Listboxes

als Beispiele für Dinge, die keine Dialog Boxes sind.

---

## Content Categories

`dialog` gehört zu:

- Flow Content

Weitere Content Categories werden für das Element in §4.11.4 nicht ausgewiesen.

---

## Context

`dialog` darf dort verwendet werden, wo Flow Content erwartet wird.

---

## Content Model

Das Content Model lautet:

- Flow Content

Es gibt für `dialog` in §4.11 keine spezielle Einschränkung auf bestimmte Kind-Elemente.

---

## Tag Omission

Für `dialog` gilt:

- Start-Tag darf nicht ausgelassen werden.
- End-Tag darf nicht ausgelassen werden.

---

## Content Attributes

Zusätzlich zu den Global Attributes besitzt `dialog`:

- `closedby`
- `open`

---

## `open`

`open` ist ein Boolean Attribute.

Wenn es vorhanden ist:

- ist der Dialog aktiv,
- und der Benutzer kann mit ihm interagieren.

Ein `dialog` ohne `open` soll dem Benutzer nicht angezeigt werden.

Die Spezifikation erlaubt, diese Sichtbarkeitsanforderung über die Rendering-Schicht umzusetzen.

---

## Manuelles Entfernen von `open`

Die Spezifikation weist ausdrücklich auf Konsequenzen des manuellen Entfernens von `open` hin.

Das Entfernen kann den Dialog zwar normalerweise aus der Anzeige entfernen, führt aber nicht zum vollständigen normalen Dialog-Close-Verhalten.

Insbesondere:

- das `close`-Event wird nicht ausgelöst,
- `close()` und Close Requests können anschließend nicht mehr auf dieselbe Weise schließen,
- bei einem modal geöffneten Dialog kann das Dokument weiterhin blockiert sein.

Daher empfiehlt die Spezifikation, zum eigentlichen Schließen vorzugsweise:

- `requestClose()`
- oder `close()`

zu verwenden.

Zum rein visuellen Verbergen kann die `hidden`-Eigenschaft verwendet werden.

---

## `closedby`

`closedby` ist ein Enumerated Attribute.

Die spezifizierten Keywords und States sind:

| Keyword | State | Bedeutung |
|---|---|---|
| `any` | Any | Close Requests oder Klicks außerhalb schließen den Dialog |
| `closerequest` | Close Request | Close Requests schließen den Dialog |
| `none` | None | Keine Benutzeraktion schließt den Dialog automatisch |

Zusätzlich existiert der Auto State.

### Missing Value Default

Der Missing Value Default ist:

- Auto

### Invalid Value Default

Der Invalid Value Default ist ebenfalls:

- Auto

### Auto State

Im Auto State hängt das effektive Verhalten davon ab, wie der Dialog geöffnet wurde.

Wurde der Dialog mit `showModal()` geöffnet:

- verhält sich Auto wie Close Request.

Wurde er nicht modal geöffnet:

- verhält sich Auto wie None.

---

## `closedby` und Light Dismiss

`closedby="any"` ermöglicht das Dialog Light Dismiss.

Das bedeutet:

- ein Klick außerhalb des Dialogs kann den Dialog schließen.

Dies wird in §4.11.5 gesondert verarbeitet.

---

## `tabindex`

Die Spezifikation enthält für `dialog` eine ausdrückliche Konformitätsregel:

> Das `tabindex`-Attribut darf nicht auf `dialog`-Elementen angegeben werden.

Dies ist von der allgemeinen Frage der Fokussierbarkeit zu unterscheiden.

Das Dialog-Focusing-Modell sorgt selbst dafür, einen geeigneten Fokus-Kandidaten zu bestimmen.

---

# Dialog-Fokus

Ein wichtiger Bestandteil des `dialog`-Modells ist die Fokussteuerung.

Die Spezifikation definiert Dialog Focusing Steps.

Dabei wird grundsätzlich versucht, einen sinnvollen Fokus-Kandidaten zu bestimmen.

Die Reihenfolge umfasst insbesondere:

1. Prüfen, ob Fokus auf den Dialog bzw. dessen Kontext zulässig ist.
2. Wenn `autofocus` auf dem Dialog selbst vorhanden ist, wird der Dialog als Control gewählt.
3. Andernfalls wird ein Focus Delegate des Dialogs gesucht.
4. Wenn kein solcher Control gefunden wird, wird der Dialog selbst als Control verwendet.
5. Die Focusing Steps werden auf den ermittelten Control angewendet.

---

## Empfehlung zur Verwendung von `autofocus`

Die WHATWG-Spezifikation empfiehlt Autoren ausdrücklich, die erwartete initiale Interaktion eines Dialogs zu berücksichtigen.

Wenn ein bestimmtes Nachfahren-Element unmittelbar nach dem Öffnen bedient werden soll, sollte dieses Element `autofocus` verwenden.

Wenn kein solches Nachfahren-Element vorhanden ist, kann `autofocus` am `dialog` selbst verwendet werden.

Dies ist eine Autorenempfehlung und keine Aussage darüber, dass jedes Dialog-Markup zwingend `autofocus` enthalten muss.

---

## Scrollbare Dialoge

Die Spezifikation weist zusätzlich auf die Benutzerfreundlichkeit großer Dialoge hin.

Autoren sollten vermeiden, den Dialog selbst unnötig scrollbar zu machen.

Insbesondere große direkte Textmengen als direkte Kinder des Dialogs können dazu führen, dass der Dialog selbst überläuft.

Ein inneres Element kann stattdessen als scrollbarer Container dienen.

---

# DOM Interface von `dialog`

Das aktuelle Interface lautet:

```webidl
[Exposed=Window]
interface HTMLDialogElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, Reflect] attribute boolean open;
  attribute DOMString returnValue;
  [CEReactions, ReflectSetter] attribute DOMString closedBy;
  [CEReactions] undefined show();
  [CEReactions] undefined showModal();
  [CEReactions] undefined close(optional DOMString returnValue);
  [CEReactions] undefined requestClose(optional DOMString returnValue);
};
```

Damit besitzt `dialog` folgende wesentliche DOM-Schnittstelle:

- `open`
- `returnValue`
- `closedBy`
- `show()`
- `showModal()`
- `close()`
- `requestClose()`

---

# `show()`

`show()` zeigt den Dialog nicht modal an.

Das Verfahren prüft zunächst den aktuellen Zustand des Dialogs.

Ein bereits geöffneter nichtmodaler Dialog kann nicht einfach nochmals geöffnet werden.

Bei bereits geöffnetem Zustand kann eine `InvalidStateError`-Exception auftreten, abhängig vom konkreten Zustand der Spezifikation.

Vor dem Öffnen wird ein cancelbares `beforetoggle`-Event mit:

- `oldState = "closed"`
- `newState = "open"`

ausgelöst.

Wird dieses Event abgebrochen, wird das Öffnen nicht fortgesetzt.

Danach:

- wird ein Dialog Toggle Event Task eingeplant,
- `open` gesetzt,
- das zuvor fokussierte Element gespeichert,
- gegebenenfalls relevante Popover-Zustände verarbeitet,
- die Dialog Focusing Steps ausgeführt.

---

# `showModal()`

`showModal()` öffnet den Dialog als modalen Dialog.

Der Dialog wird dadurch:

- modal,
- in die Top Layer eingebracht,
- und das Dokument wird durch den modalen Dialog blockiert.

Der Fokus wird anschließend entsprechend den Dialog Focusing Steps behandelt.

Die Spezifikation beschreibt dabei insbesondere:

- den Wechsel in den Modalzustand,
- die Dokument-Blockierung,
- die Top Layer,
- die Speicherung des zuvor fokussierten Elements,
- die Fokusinitialisierung.

---

## Modalität und Inertheit

Wenn ein Dialog modal geöffnet wird, wird das betreffende Dokument entsprechend dem Dialogmodell blockiert.

Der fokussierte Bereich des Dokuments wird dabei inert, soweit er nicht zum Dialog gehört.

Dadurch wird die Interaktion mit dem restlichen Dokument während des modalen Dialogs eingeschränkt.

---

# `close()`

`close()` schließt den Dialog.

Optional kann ein Return Value angegeben werden.

Wenn ein Wert übergeben wird:

- wird dieser als `returnValue` des Dialogs gesetzt.

Das eigentliche Close-Verfahren umfasst unter anderem:

1. Prüfung, ob der Dialog geöffnet ist.
2. Auslösen eines `beforetoggle`-Events.
3. Einplanen eines Dialog Toggle Events.
4. Entfernen von `open`.
5. Entfernen des Dialogs aus der Top Layer, wenn er modal war.
6. Beenden des Modalzustands.
7. Aktualisieren des Return Values.
8. Wiederherstellung des vorherigen Fokus, soweit erforderlich.
9. Auslösen eines `close`-Events.

---

# `requestClose()`

`requestClose()` repräsentiert einen Close Request.

Die Methode führt nicht einfach unmittelbar dieselbe Operation wie `close()` aus.

Stattdessen wird zunächst das Request-Close-Verfahren verwendet.

Dieses ermöglicht insbesondere:

- Auslösen eines `cancel`-Events,
- Abbrechen des Close-Vorgangs über `preventDefault()`,
- anschließendes Schließen, wenn der Close Request nicht abgebrochen wurde.

Damit ist `requestClose()` für Benutzer- bzw. UI-vermittelte Schließvorgänge besonders relevant.

---

## Unterschied `close()` und `requestClose()`

| Methode | Bedeutung |
|---|---|
| `close()` | Schließt den Dialog direkt über das Close-Verfahren |
| `requestClose()` | Fordert das Schließen an und durchläuft das Cancel-/Close-Request-Modell |

Die Spezifikation weist ausdrücklich darauf hin, dass `requestClose()` als Hilfsfunktion verwendet werden kann, um Schließlogik über `cancel`- und `close`-Events zu zentralisieren.

`requestClose()` ignoriert dabei das `closedby`-Attribut.

Auch bei `closedby="none"` führt ein expliziter `requestClose()`-Aufruf das Request-Close-Verfahren aus.

---

# Dialog Return Value

`HTMLDialogElement.returnValue` repräsentiert den Return Value des Dialogs.

Die Eigenschaft:

- kann gelesen werden,
- kann gesetzt werden,
- wird beim Schließen durch einen übergebenen Return Value aktualisiert.

Ein klassisches Anwendungsmodell ist die Verwendung von Dialog-Formularen mit unterschiedlichen Button-Werten.

---

# Dialog Events

Das Dialogmodell verwendet insbesondere:

- `beforetoggle`
- `toggle`
- `cancel`
- `close`

Diese Events haben unterschiedliche Rollen.

## `beforetoggle`

Wird vor dem eigentlichen Öffnen oder Schließen verwendet.

Beim Öffnen:

- `oldState = "closed"`
- `newState = "open"`

Beim Schließen:

- `oldState = "open"`
- `newState = "closed"`

Bei Dialogen kann zusätzlich die `source`-Information des auslösenden Elements beteiligt sein.

---

## `toggle`

Das `toggle`-Event wird über einen Toggle Task ausgeliefert.

Wie beim `details`-Element existiert ein Dialog Toggle Task Tracker.

Schnelle Zustandsänderungen können dadurch zusammengeführt werden.

---

## `cancel`

`cancel` ist für Close Requests relevant.

Wird das Event mit `preventDefault()` abgebrochen:

- wird der Close-Vorgang verhindert.

---

## `close`

Das `close`-Event wird nach dem eigentlichen Schließen des Dialogs ausgelöst.

Es ist damit vom `beforetoggle`- und `cancel`-Verhalten zu unterscheiden.

---

# Dialog Internal State

Das WHATWG-Verarbeitungsmodell definiert mehrere interne Zustände und Hilfsdaten für Dialoge.

Dazu gehören insbesondere:

- Dialog Toggle Task Tracker
- Close Watcher
- Request-Close Return Value
- Request-Close Source Element
- Enable-Close-Watcher-for-Request-Close Boolean
- Is-Modal Boolean
- Previously Focused Element
- Open Dialogs List

Diese sind keine HTML-Attribute und keine zusätzlichen HTML-Elemente.

Sie gehören zur normativen Implementierungs- und Verarbeitungsbeschreibung des `dialog`-Elements.

---

# Dialog Setup und Cleanup

Beim Einfügen eines `dialog`-Elements prüft die Spezifikation unter anderem:

- ob das Dokument vollständig aktiv ist,
- ob das Dialogelement `open` besitzt,
- ob es verbunden ist.

Bei einem geöffneten und verbundenen Dialog werden die Dialog Setup Steps ausgeführt.

Dabei wird:

- der Dialog in die Open Dialogs List aufgenommen,
- ein Close Watcher eingerichtet.

Beim Entfernen eines geöffneten Dialogs werden die Cleanup Steps ausgeführt.

Dabei:

- wird der Dialog aus der Open Dialogs List entfernt,
- ein vorhandener Close Watcher zerstört.

Wenn sich der Dialog in der Top Layer befindet, wird er ebenfalls aus dieser entfernt.

---

# Dialog Close Watcher

Der Dialog verwendet einen Close Watcher, um Close Requests zu verarbeiten.

Der Close Watcher ist insbesondere für:

- `cancel`
- Close Requests
- Light Dismiss
- andere Benutzerinitiierte Schließvorgänge

relevant.

Der Close Watcher wird während der Dialog Setup Steps eingerichtet.

Beim Cleanup wird er wieder zerstört.

---

# Commands und `dialog`

Das Dialogmodell ist direkt mit dem Command-Modell aus §4.11.3 verbunden.

Für `dialog` werden gültige Command States definiert.

Die Dialog-Command-Zustände umfassen:

- Close
- Request Close
- Show Modal

Diese entsprechen den in der aktuellen HTML-Spezifikation für `command` vorgesehenen Zuständen.

---

## Dialog Command: Close

Wenn der Command den Close State besitzt und der Ziel-Dialog `open` ist:

- wird der Dialog geschlossen.

Ein optionaler Wert des auslösenden Elements kann dabei als Return Value berücksichtigt werden.

---

## Dialog Command: Request Close

Wenn der Command den Request Close State besitzt und der Ziel-Dialog `open` ist:

- wird ein Close Request ausgelöst.

Damit durchläuft die Aktion das `cancel`-/Close-Request-Modell.

---

## Dialog Command: Show Modal

Wenn der Command den Show Modal State besitzt und der Ziel-Dialog nicht geöffnet ist:

- wird der Dialog modal angezeigt.

---

## Beispiel mit `commandfor`

```html
<button
  type="button"
  commandfor="the-dialog"
  command="show-modal">
  Löschen
</button>

<dialog id="the-dialog">
  <form action="/delete" method="POST">
    <button type="submit">
      Löschen
    </button>

    <button
      commandfor="the-dialog"
      command="close">
      Abbrechen
    </button>
  </form>
</dialog>
```

Hier ist:

- `commandfor` das Ziel des Commands,
- `command="show-modal"` die Aktion zum modalen Öffnen,
- `command="close"` die Aktion zum Schließen.

Die Attribute selbst gehören zur Attribut-/Form-Control-Ebene und werden dort detaillierter inventarisiert.

§4.11 beschreibt hier die Interaktion zwischen Command- und Dialogmodell.

---

# Accessibility

## Grundsatz

Die WHATWG-Spezifikation weist für die drei Elemente:

- `details`
- `summary`
- `dialog`

jeweils Accessibility Considerations für:

- Autoren
- Implementierer

aus.

Die konkrete Accessibility-Ebene darf nicht mit der Content-Category-Ebene verwechselt werden.

---

## `details`

Für `details` hebt die Spezifikation insbesondere die Gruppierung verwandter Elemente hervor.

Bei einer Gruppe mit `name` kann eine gemeinsame äußere Struktur die Beziehung der Elemente für Benutzer besser verständlich machen.

Die WHATWG-Spezifikation empfiehlt, zusammengehörige Elemente möglichst zusammenzuhalten.

---

## `summary`

Das `summary` bildet die funktionale Beschriftung bzw. Legende des `details`-Elements, sofern es das erste `summary`-Kind ist.

Die korrekte Platzierung als erstes `summary`-Element ist deshalb nicht lediglich eine semantische Konvention, sondern Teil der funktionalen Definition.

---

## `dialog`

Für Dialoge ist die Fokusführung besonders relevant.

Die WHATWG-Spezifikation definiert eigene Dialog Focusing Steps und empfiehlt Autoren, die erwartete initiale Interaktion explizit über `autofocus` zu berücksichtigen.

Bei modalen Dialogen ist außerdem die Blockierung des restlichen Dokuments Bestandteil des Verarbeitungsmodells.

---

## Keine erfundenen ARIA-Zuordnungen

Diese Datei übernimmt keine nicht aus der Primärquelle belegten:

- ARIA Roles
- ARIA States
- ARIA Properties
- Accessibility Tree Mapping Details
- Plattform-spezifischen Accessibility API Mappings

Eine solche Zuordnung muss gegebenenfalls in der späteren Accessibility-Referenz auf Basis der einschlägigen Accessibility-Spezifikationen recherchiert werden.

---

# Sanitization

## `details`

WHATWG-Klassifikation:

```text
Uncategorized
```

## `summary`

WHATWG-Klassifikation:

```text
Uncategorized
```

## `dialog`

WHATWG-Klassifikation:

```text
Uncategorized
```

Damit weist die aktuelle WHATWG-Darstellung für die drei in §4.11 definierten Elemente keine jeweils eigene spezialisierte Sanitization-Kategorie aus.

Diese Angabe darf nicht als allgemeine Sicherheitsbewertung des Elements interpretiert werden.

Sanitization ist eine eigenständige Spezifikationsebene.

---

# DOM Interfaces

## `details`

```webidl
[Exposed=Window]
interface HTMLDetailsElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, Reflect] attribute DOMString name;
  [CEReactions, Reflect] attribute boolean open;
};
```

---

## `summary`

```text
HTMLElement
```

`summary` besitzt kein eigenes spezialisiertes DOM Interface innerhalb dieses Abschnitts.

---

## `dialog`

```webidl
[Exposed=Window]
interface HTMLDialogElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, Reflect] attribute boolean open;
  attribute DOMString returnValue;
  [CEReactions, ReflectSetter] attribute DOMString closedBy;
  [CEReactions] undefined show();
  [CEReactions] undefined showModal();
  [CEReactions] undefined close(optional DOMString returnValue);
  [CEReactions] undefined requestClose(optional DOMString returnValue);
};
```

---

# Normative Sonderregeln

## `details`

Für `details` sind insbesondere folgende normative Regeln relevant:

- Das Element ist ein Disclosure Widget.
- Es darf nicht zur Simulation anderer Interaktionsmuster missbraucht werden.
- `summary` ist das vorgesehene Summary-/Legend-Element.
- Das erste `summary`-Element hat die spezielle funktionale Bedeutung.
- `open` ist ein Boolean Attribute.
- `name` darf bei Verwendung nicht leer sein.
- Gleichnamige `details`-Elemente können eine exklusive Details Name Group bilden.
- Innerhalb einer Gruppe darf nicht mehr als ein Element geöffnet sein.
- Script darf keine Gruppe mit mehreren geöffneten Mitgliedern erzeugen.
- Ein `details` darf nicht Nachfahre eines anderen `details` derselben Name Group sein.
- Das Öffnen eines Gruppenmitglieds kann das Schließen eines anderen bewirken.
- Zustandsänderungen werden über Toggle Task-Verarbeitung und `toggle`-Events verarbeitet.

---

## `summary`

- `summary` ist nur als erstes Kind eines `details`-Elements als dessen Summary definiert.
- Ein späteres `summary`-Element erhält nicht automatisch dieselbe funktionale Bedeutung.
- Die Aktivierung eines gültigen Summary toggelt `open` am Parent-`details`.
- Die Änderung löst die zugehörige Details Notification Task-Verarbeitung aus.

---

## `dialog`

- `dialog` ist ein eigenes HTML-Element.
- `dialog` ist Flow Content.
- Das Content Model ist Flow Content.
- Start- und End-Tag dürfen nicht ausgelassen werden.
- `open` ist ein Boolean Attribute.
- `closedby` ist ein Enumerated Attribute.
- `tabindex` darf nicht auf `dialog` angegeben werden.
- `show()` öffnet nicht modal.
- `showModal()` öffnet modal.
- `close()` schließt direkt über das Close-Verfahren.
- `requestClose()` verwendet das Close-Request-Modell.
- Close Requests können über `cancel` verhindert werden.
- Modal geöffnete Dialoge blockieren den relevanten Dokumentbereich.
- Modal geöffnete Dialoge werden in der Top Layer verarbeitet.
- Der zuvor fokussierte Control kann beim Schließen wieder fokussiert werden.
- Dialoge besitzen einen internen Close Watcher.
- Dialoge besitzen einen Open Dialogs List-Zustand auf Dokumentebene.
- Dialoge können über Commands geöffnet oder geschlossen werden.
- `closedby` beeinflusst automatisch ausgelöste Close-Verfahren.
- `requestClose()` ignoriert `closedby`.
- Light Dismiss ist ein eigenes Verarbeitungsmodell und nicht identisch mit `requestClose()` oder `close()`.

---

# Dialog Light Dismiss

## WHATWG-Abschnitt

§4.11.5 – Dialog light dismiss

Light Dismiss bedeutet, dass ein Klick außerhalb eines `dialog`-Elements den Dialog schließen kann, wenn dessen effektiver `closedby`-Zustand `Any` ist.

Das ist zusätzlich zu den normalen Close Requests.

---

## Voraussetzung

Light Dismiss ist insbesondere relevant für:

```text
closedby = Any
```

Das entspricht dem Keyword:

```html
closedby="any"
```

---

## Verarbeitung

Die Light-Dismiss-Verarbeitung arbeitet mit Pointer Events.

Die Spezifikation prüft unter anderem:

- ob das Event vertrauenswürdig ist,
- welches Dokument betroffen ist,
- ob offene Dialoge vorhanden sind,
- welcher Dialog dem Pointer-Ziel am nächsten liegt,
- welcher Dialog der oberste offene Dialog ist,
- ob der effektive `closedby`-Zustand `Any` ist.

---

## Pointer Down / Pointer Up

Die Light-Dismiss-Verarbeitung berücksichtigt die Beziehung zwischen:

- `pointerdown`
- `pointerup`

Dazu speichert das Dokument das Dialog Pointerdown Target.

Beim `pointerup` wird geprüft, ob das Ziel mit dem beim `pointerdown` ermittelten Ziel übereinstimmt.

Nur wenn die relevanten Ziele übereinstimmen, wird die weitere Light-Dismiss-Verarbeitung durchgeführt.

---

## Oberster Dialog

Es wird der letzte Dialog der Open Dialogs List als oberster Dialog betrachtet.

Wenn der Klick innerhalb dieses obersten Dialogs erfolgt:

- findet kein Light Dismiss statt.

Wenn der Klick außerhalb liegt:

- und der effektive `closedby`-State `Any` ist,
- wird ein Close Request ausgelöst.

Damit ist Light Dismiss kein unmittelbares Entfernen des `open`-Attributs.

Stattdessen wird der normale Close-Request-Mechanismus verwendet.

---

# Modal Dialog und Backdrop

Bei modal angezeigten Dialogen wird die Top Layer verwendet.

Pointer Events können dabei den Dialog selbst als Event Target aufweisen, wenn sie visuell dessen `::backdrop` treffen.

Die Spezifikation berücksichtigt deshalb die geometrische Prüfung der Pointer-Koordinaten.

Ist ein Pointer Event auf dem Backdrop eines modalen Dialogs angekommen, muss festgestellt werden, ob die Koordinaten außerhalb der tatsächlichen Dialoggrenzen liegen.

Diese Prüfung ist Teil der Bestimmung des nächstgelegenen angeklickten Dialogs.

---

# `closedby` und effektiver Zustand

Der tatsächlich wirksame Close-Mechanismus wird nicht ausschließlich aus dem rohen Attributwert gelesen.

Die Spezifikation definiert einen berechneten `closedby`-State.

Für den Auto State gilt:

- modal → Close Request
- nicht modal → None

Für explizite States gilt:

- `any` → Any
- `closerequest` → Close Request
- `none` → None

Damit ist insbesondere wichtig:

```html
<dialog closedby="any">
```

nicht gleichbedeutend mit einem simplen JavaScript-Click-Outside-Handler.

Das Verhalten ist Bestandteil des normativen Dialog-Verarbeitungsmodells.

---

# Querverweise

## `details` ↔ `summary`

`details` und `summary` bilden eine eng gekoppelte Elementbeziehung.

`summary` ist das funktionale Disclosure-Label, wenn es:

- ein `details`-Parent besitzt,
- und das erste `summary`-Element-Kind dieses Parents ist.

Die Aktivierung von `summary` verändert `open` des `details`.

---

## `details` ↔ `toggle`

Das `open`-Attribut von `details` ist mit Toggle Event Processing verbunden.

Änderungen werden nicht nur als statische Attributänderungen behandelt.

Die Spezifikation definiert eigene Task- und Event-Schritte.

---

## `dialog` ↔ Focus

Das Dialogmodell ist direkt mit den HTML Focus/Focusing Steps verbunden.

Insbesondere relevant sind:

- zuvor fokussiertes Element
- `autofocus`
- Focus Delegate
- Focusing Steps

---

## `dialog` ↔ Top Layer

Modal geöffnete Dialoge werden in die Top Layer aufgenommen.

Beim Schließen wird ein modal geöffneter Dialog aus der Top Layer entfernt.

---

## `dialog` ↔ Inert

Ein modal geöffneter Dialog beeinflusst die Interaktion mit dem restlichen Dokument.

Der fokussierte Bereich außerhalb des Dialogs wird entsprechend dem Modalitätsmodell inert.

---

## `dialog` ↔ `closedby`

`closedby` steuert die erlaubten automatischen Benutzeraktionen zum Schließen.

Die effektive Interpretation hängt bei Auto vom Modalzustand ab.

---

## `dialog` ↔ Commands

`dialog` definiert gültige Command-Zustände für:

- Close
- Request Close
- Show Modal

Damit verbindet §4.11.4 das Dialogmodell direkt mit §4.11.3.

---

## `dialog` ↔ `commandfor`

Ein `button` kann mit `commandfor` einen Ziel-Dialog adressieren.

Die eigentliche Definition von `commandfor` und die vollständige Button-Attributprüfung gehören zur Button-/Form-Control-Ebene.

§4.11 verwendet diese Mechanismen für das Dialog-Command-Modell.

---

## `dialog` ↔ `cancel`

Close Requests führen über den Close Watcher zum `cancel`-Verhalten.

Wird `cancel` verhindert:

```javascript
event.preventDefault();
```

wird der Close-Vorgang nicht fortgesetzt.

---

## `dialog` ↔ `close`

Das `close`-Event wird nach dem tatsächlichen Schließen des Dialogs ausgelöst.

Es ist damit von:

- `beforetoggle`
- `toggle`
- `cancel`

zu unterscheiden.

---

# Elemente versus Konzepte

Für die Vollständigkeitsmatrix ist folgende Trennung verbindlich.

## Tatsächliche HTML-Elemente dieses Abschnitts

```text
details
summary
dialog
```

## Keine zusätzlichen HTML-Elemente

Folgende Begriffe sind trotz ihrer Behandlung in §4.11 keine neuen Elemente:

```text
Commands
Command Facets
Dialog light dismiss
Details Name Group
Dialog Close Watcher
Dialog Toggle Task Tracker
Open Dialogs List
Dialog Focusing Steps
```

Ebenso werden die bereits an anderer Stelle inventarisierten Elemente:

```text
a
button
input
option
legend
```

nicht nochmals als neue HTML-Elemente gezählt.

Ihre Command-Bedeutung wird hier lediglich als Querverweis-/Konzeptinformation dokumentiert.

---

# Content Categories – Zusammenfassung

| Element | Content Categories |
|---|---|
| `details` | Flow, Interactive, Palpable |
| `summary` | None |
| `dialog` | Flow |

Die Kategoriezuordnung ist unabhängig von der Frage, ob ein Element in einem bestimmten Kontext verwendet werden darf.

---

# Context – Zusammenfassung

| Element | Context |
|---|---|
| `details` | Wo Flow Content erwartet wird |
| `summary` | Als erstes Kind eines `details` |
| `dialog` | Wo Flow Content erwartet wird |

---

# Content Model – Zusammenfassung

| Element | Content Model |
|---|---|
| `details` | Ein `summary`, gefolgt von Flow Content |
| `summary` | Phrasing Content, optional mit Heading Content vermischt |
| `dialog` | Flow Content |

---

# Tag Omission – Zusammenfassung

| Element | Start-Tag | End-Tag |
|---|---|---|
| `details` | nicht auslassbar | nicht auslassbar |
| `summary` | nicht auslassbar | nicht auslassbar |
| `dialog` | nicht auslassbar | nicht auslassbar |

---

# Content Attributes – Zusammenfassung

| Element | Eigene Content Attributes |
|---|---|
| `details` | `name`, `open` |
| `summary` | keine |
| `dialog` | `closedby`, `open` |

Zusätzlich gelten jeweils die Global Attributes.

---

# DOM Interface – Zusammenfassung

| Element | DOM Interface |
|---|---|
| `details` | `HTMLDetailsElement` |
| `summary` | `HTMLElement` |
| `dialog` | `HTMLDialogElement` |

---

# Sanitization – Zusammenfassung

| Element | WHATWG-Sanitization-Klassifikation |
|---|---|
| `details` | Uncategorized |
| `summary` | Uncategorized |
| `dialog` | Uncategorized |

---

# Konformitätsrelevante Unterschiede

## `details`

Ein `details`-Element kann im WHATWG-Standard definiert sein, ohne dass jede denkbare Verwendung als Disclosure Widget konform wäre.

Insbesondere darf es nicht als Ersatz für andere Interaktionsmuster missbraucht werden.

## `summary`

Ein `summary` ist nicht allein aufgrund seines Namens das funktionale Summary eines beliebigen Parents.

Die spezielle Funktion entsteht nur bei:

- Parent = `details`
- erstes `summary`-Element-Kind

## `dialog`

Ein `dialog` ist nicht generell ein beliebiges Popup.

Die Spezifikation grenzt Dialoge insbesondere von:

- Context Menus
- Tooltips
- Popup Listboxes

ab.

---

# Status / V1

## WHATWG-Status

Die drei Elemente sind im aktuellen WHATWG HTML Living Standard definiert:

- `details`
- `summary`
- `dialog`

Die Command-Semantik und Dialog-Light-Dismiss-Verarbeitung sind ebenfalls Bestandteil des aktuellen Standards.

---

## Konformitätsstatus

Der Begriff:

```text
im WHATWG-Standard definiert
```

bedeutet nicht automatisch:

```text
jede konkrete Verwendung ist konform
```

Beispiele:

- `details` ist definiert, darf aber nicht als beliebiger Ersatz für Tabs oder Menüs missbraucht werden.
- `dialog` ist definiert, darf aber nicht zur Darstellung eines Tooltips verwendet werden.
- `summary` ist definiert, erhält seine spezielle funktionale Bedeutung jedoch nur in der dafür spezifizierten Position innerhalb von `details`.
- `details`-Name-Groups unterliegen eigenen Konformitätsregeln.
- `tabindex` darf nicht auf `dialog` angegeben werden.

---

## Browser-Support

Browser-Support wird bewusst nicht als WHATWG-Status in diese Datei übernommen.

Die WHATWG-Seite kann Browser-Kompatibilitätsinformationen darstellen, aber diese sind eine andere Informationsdimension als die normative HTML-Definition.

Für ZE-WebLab gilt:

```text
WHATWG-Status != Browser-Kompatibilität
```

Eine spätere Kompatibilitätsdatei kann die Implementierungsstände separat dokumentieren.

---

# V1-Referenzstatus

| Feature | V1-Status |
|---|---|
| `details` | Referenz aufgenommen |
| `summary` | Referenz aufgenommen |
| Commands | Konzept-/Querverweis aufgenommen |
| `dialog` | Referenz aufgenommen |
| Dialog light dismiss | Verarbeitungsmodell aufgenommen |
| Command Facets | Konzept aufgenommen |
| Dialog DOM API | aufgenommen |
| Details Toggle Processing | aufgenommen |
| Dialog Toggle Processing | aufgenommen |
| Dialog Close Request Processing | aufgenommen |
| Dialog Light Dismiss Processing | aufgenommen |

---

# Prüfstatus

## `details`

- [x] WHATWG-Abschnitt geprüft
- [x] Elementdefinition geprüft
- [x] Content Categories geprüft
- [x] Context geprüft
- [x] Content Model geprüft
- [x] Tag Omission geprüft
- [x] Content Attributes geprüft
- [x] `name` geprüft
- [x] `open` geprüft
- [x] Details Name Group geprüft
- [x] Exklusivitätsregeln geprüft
- [x] Toggle Processing geprüft
- [x] Accessibility-Hinweise geprüft
- [x] Sanitization geprüft
- [x] DOM Interface geprüft
- [x] normative Sonderregeln geprüft
- [x] Querverweise geprüft

## `summary`

- [x] WHATWG-Abschnitt geprüft
- [x] Elementdefinition geprüft
- [x] Content Categories geprüft
- [x] Context geprüft
- [x] Content Model geprüft
- [x] Tag Omission geprüft
- [x] Content Attributes geprüft
- [x] funktionale Summary-Bedingung geprüft
- [x] Aktivierungsverhalten geprüft
- [x] Accessibility-Hinweise geprüft
- [x] Sanitization geprüft
- [x] DOM Interface geprüft
- [x] Querverweise zu `details` geprüft

## Commands

- [x] Facets geprüft
- [x] `a` geprüft
- [x] `button` geprüft
- [x] `input` geprüft
- [x] `option` geprüft
- [x] `legend` + `accesskey` geprüft
- [x] allgemeine `accesskey`-Regel geprüft
- [x] Abgrenzung Konzept vs. Element geprüft

## `dialog`

- [x] WHATWG-Abschnitt geprüft
- [x] Elementdefinition geprüft
- [x] Content Categories geprüft
- [x] Context geprüft
- [x] Content Model geprüft
- [x] Tag Omission geprüft
- [x] `open` geprüft
- [x] `closedby` geprüft
- [x] Auto State geprüft
- [x] `show()` geprüft
- [x] `showModal()` geprüft
- [x] `close()` geprüft
- [x] `requestClose()` geprüft
- [x] `returnValue` geprüft
- [x] Dialog Focusing Steps geprüft
- [x] Modalitätsmodell geprüft
- [x] Top Layer-Beziehung geprüft
- [x] Close Watcher geprüft
- [x] Dialog Setup/Cleanup geprüft
- [x] Command Integration geprüft
- [x] Accessibility-Hinweise geprüft
- [x] Sanitization geprüft
- [x] DOM Interface geprüft
- [x] normative Sonderregeln geprüft

## Dialog Light Dismiss

- [x] `closedby="any"` geprüft
- [x] Pointerdown-/Pointerup-Modell geprüft
- [x] Open Dialogs List geprüft
- [x] Topmost Dialog geprüft
- [x] Outside-Dialog-Prüfung geprüft
- [x] Close-Request-Integration geprüft

---

# Offene Punkte

Nach der vollständigen Prüfung von §4.11 verbleiben für diese Datei keine offenen Punkte bezüglich des WHATWG-Elementinventars.

Nicht Gegenstand dieser Datei und deshalb bewusst offen für spätere Fachbereiche sind:

- vollständige Browser-Kompatibilitätsmatrix
- vollständige ARIA-/Accessibility-API-Mappings
- detaillierte Plattform-Accessibility-Implementierungen
- vollständige globale Attributreferenz
- vollständige Button-/Input-/Option-Attributreferenz außerhalb des Command-Kontexts
- vollständige Popover-Spezifikation
- vollständige Top-Layer-Spezifikation
- vollständige Pointer-Events-Spezifikation
- vollständige DOM-Spezifikation
- vollständige Web IDL-Referenz
- vollständige Rendering-Regeln

Diese Punkte sind keine Lücken in der Recherche von §4.11, sondern bewusst getrennte Referenzebenen.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard**

Abschnitt:

```text
§4.11 Interactive elements
```

Unterabschnitte:

```text
§4.11.1 The details element
§4.11.2 The summary element
§4.11.3 Commands
§4.11.3.1 Facets
§4.11.3.2 Using the a element to define a command
§4.11.3.3 Using the button element to define a command
§4.11.3.4 Using the input element to define a command
§4.11.3.5 Using the option element to define a command
§4.11.3.6 Using the accesskey attribute on a legend element to define a command
§4.11.3.7 Using the accesskey attribute to define a command on other elements
§4.11.4 The dialog element
§4.11.5 Dialog light dismiss
```

Der Abschnitt wurde gegen die aktuelle Living-Standard-Fassung geprüft.

---

# Referenzhinweise für ZE-WebLab

## Elementebene

Als eigenständige HTML-Elemente dieses Themenblocks gelten:

```text
details
summary
dialog
```

## Konzeptebene

Als separate Konzept-/Verarbeitungsebene gelten:

```text
Commands
Command Facets
Details Name Groups
Details Toggle Processing
Dialog Focusing Steps
Dialog Close Watcher
Dialog Setup/Cleanup
Dialog Toggle Processing
Dialog Close Requests
Dialog Light Dismiss
```

## Keine zusätzliche Elementzählung

Folgende bereits vorhandene HTML-Elemente werden durch das Command-Kapitel nicht nochmals als neue Elemente gezählt:

```text
a
button
input
option
legend
```

Damit bleibt die Elementinventarisierung von ZE-WebLab konsistent mit der festgelegten Methodik:

> WHATWG-Unterabschnitt != automatisch neues HTML-Element.

---

# Kurzreferenz

## `details`

```html
<details>
  <summary>Zusammenfassung</summary>
  <p>Zusätzlicher Inhalt.</p>
</details>
```

- Flow Content
- Interactive Content
- Palpable Content
- erstes `summary`, danach Flow Content
- `name`
- `open`
- `HTMLDetailsElement`

## `summary`

```html
<summary>Zusammenfassung</summary>
```

- keine Content Categories
- erstes Kind von `details`
- Phrasing Content, optional Heading Content
- keine eigenen Content Attributes
- `HTMLElement`

## `dialog`

```html
<dialog>
  <p>Dialoginhalt</p>
</dialog>
```

- Flow Content
- Flow Content als Content Model
- `closedby`
- `open`
- `show()`
- `showModal()`
- `close()`
- `requestClose()`
- `returnValue`
- `HTMLDialogElement`

---

# Abschlussbewertung

§4.11 ist für die ZE-WebLab-Referenz vollständig auf Element-, Konzept- und Verarbeitungsmodellebene erfasst.

Das Elementinventar dieses Abschnitts besteht aus:

```text
details
summary
dialog
```

Die Command-Unterabschnitte werden nicht als zusätzliche HTML-Elemente gezählt.

Die wichtigsten fachlichen Beziehungen des Abschnitts sind:

```text
details
 └── summary
      └── toggelt details[open]

details[name]
 └── Details Name Group
      └── exklusive Öffnung

dialog
 ├── open
 ├── closedby
 ├── show()
 ├── showModal()
 ├── close()
 ├── requestClose()
 ├── returnValue
 ├── Focus Processing
 ├── Top Layer
 ├── Close Watcher
 └── Light Dismiss

Commands
 ├── a
 ├── button
 ├── input
 ├── option
 ├── legend + accesskey
 └── allgemeines accesskey-Modell
```

Damit ist die Trennung zwischen:

- HTML-Elementinventar,
- Attributebene,
- Command-Konzept,
- DOM-API,
- Accessibility,
- Sanitization,
- und normativen Processing Models

gewahrt.