# ZE-WebLab – HTML-Referenz: Edits

## Arbeitsstand / Quellenstand

**WHATWG-Bereich:** §4.7 „Edits“  
**Primärquelle:** WHATWG HTML Living Standard  
**Recherche-/Quellenstand:** 11. August 2026  
**Status:** fachliche Detailprüfung für §4.7 abgeschlossen.

Diese Datei dokumentiert die HTML-Elemente und die fachlich relevanten Unterkonzepte aus WHATWG §4.7. Sie ist keine Kopie der Spezifikation. Normative Anforderungen werden zusammengefasst; Beispiele und Hinweise dienen der Lern- und Referenzfunktion von ZE-WebLab.

Die Primärquelle für diesen Themenblock ist die aktuelle WHATWG HTML Living Standard, §4.7 „Edits“.

> **Abgrenzung:** Browser-Kompatibilität wird nicht als WHATWG-Konformitätsstatus behandelt. Die WHATWG-Seite blendet teilweise Informationen zur Browserunterstützung ein; diese gehören in eine separate Kompatibilitätsebene und werden in dieser Datei nicht als Status der HTML-Definition übernommen.

> **Abgrenzung der Informationsebenen:** `ins` und `del` sind HTML-Elemente. `cite` und `datetime` sind elementbezogene Content Attributes. `HTMLModElement` ist ein DOM-Interface. Die Abschnitte zu Paragraphen, Listen und Tabellen sind keine zusätzlichen HTML-Elemente und werden deshalb als normative bzw. informative Querverweis-/Verwendungsregeln dokumentiert.

---

## 1. WHATWG-Struktur

WHATWG §4.7 „Edits“ besteht aktuell aus folgenden Unterabschnitten:

| WHATWG | Abschnitt | Typ |
|---|---|---|
| 4.7 | Edits | Element-/Konzeptfamilie |
| 4.7.1 | The `ins` element | HTML-Element |
| 4.7.2 | The `del` element | HTML-Element |
| 4.7.3 | Attributes common to `ins` and `del` elements | Attribut-/DOM-Konzept |
| 4.7.4 | Edits and paragraphs | nicht-normativer Verwendungsabschnitt |
| 4.7.5 | Edits and lists | nicht-normativer Verwendungsabschnitt |
| 4.7.6 | Edits and tables | nicht-normativer Verwendungsabschnitt |

Der Abschnitt beginnt mit der gemeinsamen Aussage, dass `ins` und `del` Änderungen an einem Dokument repräsentieren.

Dabei ist fachlich zwischen zwei Änderungsarten zu unterscheiden:

- `ins` repräsentiert eine **Hinzufügung** zum Dokument.
- `del` repräsentiert eine **Entfernung** aus dem Dokument.

Die drei Abschnitte 4.7.4 bis 4.7.6 definieren keine weiteren HTML-Elemente. Sie erläutern vielmehr die Verwendung von `ins` und `del` im Zusammenhang mit Paragraphen, Listen und Tabellen.

Quelle: WHATWG HTML Living Standard, §4.7.

---

## 2. Vollständigkeitskontrolle

WHATWG §4.7 definiert in seinem Elementinventar genau zwei HTML-Elemente:

| WHATWG | Element | Feature-Typ |
|---|---|---|
| 4.7.1 | `ins` | HTML-Element |
| 4.7.2 | `del` | HTML-Element |

Zusätzlich behandelt §4.7:

- zwei gemeinsame Content Attributes: `cite` und `datetime`
- das gemeinsame DOM-Interface `HTMLModElement`
- Regeln zur Verwendung von Änderungen mit Paragraphen
- Regeln zur Darstellung von Änderungen innerhalb von Listen
- Regeln zur Darstellung von Änderungen innerhalb von Tabellen

Diese Unterkonzepte werden nicht als zusätzliche Elemente gezählt.

**Elementinventar des Bereichs: 2**

---

## 3. Elementinventar – strukturelle Eigenschaften

| Element | Content Categories | Kontext | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface |
|---|---|---|---|---|---|---|---|
| `ins` | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Transparent | Keine Auslassung | Global Attributes, `cite`, `datetime` | Default mit `cite`, `datetime` | `HTMLModElement` |
| `del` | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Transparent | Keine Auslassung | Global Attributes, `cite`, `datetime` | Default mit `cite`, `datetime` | `HTMLModElement` |

Die Angaben entsprechen den aktuellen Elementdefinitionen in §4.7.1 und §4.7.2.

Besonders wichtig:

- Beide Elemente sind gleichzeitig Flow Content, Phrasing Content und Palpable Content.
- Beide dürfen dort verwendet werden, wo Phrasing Content erwartet wird.
- Beide besitzen ein transparentes Content Model.
- Bei beiden sind weder Start- noch Endtag auslassbar.
- Beide besitzen dieselben zusätzlichen Content Attributes.
- Beide verwenden dasselbe DOM-Interface `HTMLModElement`.
- Die semantische Bedeutung der beiden Elemente ist jedoch unterschiedlich.

Quelle: WHATWG HTML Living Standard, §4.7.1 und §4.7.2.

---

# 4. Detailprüfung: `ins`

## 4.1 Grundbedeutung

Das `ins`-Element repräsentiert eine **Hinzufügung zum Dokument**.

Es wird verwendet, wenn ein Teil des Dokuments als eingefügter bzw. hinzugefügter Inhalt gekennzeichnet werden soll.

Die Semantik ist damit eine Änderungssemantik und nicht lediglich eine visuelle Hervorhebung.

Ein User Agent kann eine solche Änderung beispielsweise visuell kennzeichnen, die WHATWG-Semantik selbst besteht jedoch in der Kennzeichnung der Hinzufügung.

Quelle: WHATWG §4.7.1.

---

## 4.2 Content Categories

`ins` gehört zu folgenden Content Categories:

- Flow content
- Phrasing content
- Palpable content

Die Mehrfachzugehörigkeit ist für die Konformitätsprüfung relevant.

Insbesondere bedeutet die Zugehörigkeit zu Phrasing Content, dass `ins` dort verwendet werden kann, wo Phrasing Content erwartet wird.

Die Zugehörigkeit zu Flow Content bedeutet zugleich, dass das Element nicht ausschließlich auf kleine Textfragmente beschränkt ist.

Quelle: WHATWG §4.7.1.

---

## 4.3 Context

Der von WHATWG angegebene Kontext lautet:

> Wo Phrasing Content erwartet wird.

Damit ist der Verwendungskontext nicht identisch mit der Aussage, dass der Inhalt selbst zwingend nur aus einfachem Text bestehen darf.

Da das Content Model transparent ist, hängt die konkrete zulässige Struktur zusätzlich vom Kontext ab, in dem `ins` eingesetzt wird.

Quelle: WHATWG §4.7.1.

---

## 4.4 Content Model

Das Content Model von `ins` ist:

**Transparent**

Transparent bedeutet hier nicht, dass beliebige Inhalte unabhängig vom Elternkontext erlaubt wären.

Vielmehr wird die Zulässigkeit des Inhalts über die transparenten Content-Model-Regeln in Verbindung mit dem umgebenden Kontext bestimmt.

Das ist insbesondere für die Verwendung von `ins` um Paragraphen bzw. andere nicht-Phrasing-Elemente relevant.

Die Paragraphen-Regeln in §4.7.4 zeigen ausdrücklich, dass `ins` Paragraphing nicht verändert.

Quelle: WHATWG §4.7.1 und §4.7.4.

---

## 4.5 Tag Omission

Für `ins` gilt:

- Starttag darf nicht ausgelassen werden.
- Endtag darf nicht ausgelassen werden.

Damit besitzt `ins` keine Tag-Omission-Regel.

Quelle: WHATWG §4.7.1.

---

## 4.6 Content Attributes

`ins` besitzt:

- Global Attributes
- `cite`
- `datetime`

Die beiden zusätzlichen Attribute sind gemeinsame Attribute von `ins` und `del`.

### `cite`

`cite` kann die URL eines Dokuments angeben, das die Änderung erklärt.

### `datetime`

`datetime` kann Datum und optional Uhrzeit der Änderung angeben.

Die Attribute werden ausführlich in §4.7.3 behandelt.

Quelle: WHATWG §4.7.1 und §4.7.3.

---

## 4.7 Semantische Verwendung

`ins` sollte verwendet werden, wenn eine Änderung als **hinzugefügter Inhalt** dokumentiert werden soll.

Beispielsweise kann ein neu hinzugefügter Absatz als solcher gekennzeichnet werden:

```html
<ins>
  <p>Dies ist ein neu eingefügter Absatz.</p>
</ins>
```

Die Spezifikation zeigt außerdem, dass `ins` auch Phrasing Content umfassen kann:

```html
<ins>
  Apples are <em>tasty</em>.
</ins>
```

Dabei ist entscheidend, dass die semantische Bedeutung „hinzugefügt“ lautet und nicht etwa „besonders wichtig“ oder „hervorgehoben“.

Quelle: WHATWG §4.7.1.

---

## 4.8 Paragraphen und `ins`

`ins` beeinflusst die Paragraphing-Struktur nicht.

Das führt zu einem wichtigen Sonderfall:

Ein `ins`-Element kann bei impliziten Paragraphen mehrere inhaltliche Bereiche übergreifen.

WHATWG weist ausdrücklich darauf hin, dass `ins` nicht über implizierte Paragraphengrenzen hinweg verwendet werden sollte.

Die Spezifikation bezeichnet entsprechende Konstruktionen als schlechte Form und empfiehlt eine Struktur, bei der Paragraphen explizit mit `p` ausgezeichnet werden.

Beispiel einer problematischen Struktur:

```html
<ins>
  <p>Dies ist ein eingefügter Absatz.</p>
  Dies ist ein weiterer Absatz, dessen erster Teil ebenfalls eingefügt wurde.
</ins>
```

Das `ins`-Element umschließt hier sowohl einen expliziten Paragraphen als auch weiteren Inhalt, der zu einem weiteren impliziten Paragraphen gehören kann.

Besser ist eine getrennte Kennzeichnung:

```html
<ins>
  <p>Dies ist ein eingefügter Absatz.</p>
</ins>

<ins>
  Dies ist ein weiterer eingefügter Absatz.
</ins>
```

Die Empfehlung ist nicht damit zu verwechseln, dass `ins` selbst eine Paragraphing-Grenze erzeugen würde. Das tut es nicht.

Quelle: WHATWG §4.7.1 und §4.7.4.

---

## 4.9 Accessibility

Die aktuelle WHATWG-Definition enthält für `ins` einen Abschnitt **Accessibility considerations**.

WHATWG verweist dort auf getrennte Accessibility-Regeln für:

- Autoren
- Implementierer

Die eigentliche Accessibility-Ausarbeitung wird damit nicht vollständig innerhalb der Elementdefinition dupliziert.

Für ZE-WebLab wird deshalb an dieser Stelle keine eigenständige Rollen- oder API-Zuordnung erfunden.

**Dokumentationsstatus:**

- WHATWG liefert Accessibility Considerations.
- Die detaillierte Accessibility-Auswertung gehört in die separate Accessibility-Referenz.
- Die vorliegende Datei übernimmt keine nicht belegte zusätzliche Rolle.

Quelle: WHATWG §4.7.1, Abschnitt „Accessibility considerations“.

---

## 4.10 Sanitization

Für `ins` ist in der WHATWG-Definition angegeben:

**Default** mit den Attributen:

- `cite`
- `datetime`

Damit gehört `ins` zum Default-Sanitization-Modell mit einer expliziten Berücksichtigung dieser beiden Content Attributes.

Sanitization ist dabei als eigene Informationsebene zu behandeln.

Sie ist nicht gleichbedeutend mit:

- HTML-Konformität
- Browserunterstützung
- Accessibility
- DOM-Semantik

Quelle: WHATWG §4.7.1.

---

## 4.11 DOM Interface

`ins` verwendet das Interface:

**`HTMLModElement`**

Damit besitzt `ins` kein ausschließlich für dieses Element definiertes separates DOM-Interface.

Das gemeinsame Interface wird in §4.7.3 genauer beschrieben.

Quelle: WHATWG §4.7.1 und §4.7.3.

---

# 5. Detailprüfung: `del`

## 5.1 Grundbedeutung

Das `del`-Element repräsentiert eine **Entfernung aus dem Dokument**.

Es wird verwendet, wenn Inhalt als aus dem Dokument entfernt gekennzeichnet werden soll.

Damit ist `del` semantisch etwas anderes als das Text-Level-Element `s`.

Die Unterscheidung ist für ZE-WebLab ausdrücklich relevant:

- `s` kennzeichnet Inhalt, der nicht mehr korrekt oder relevant ist.
- `del` kennzeichnet eine Änderung, bei der Inhalt aus dem Dokument entfernt wurde.

`del` gehört daher zu §4.7 „Edits“.

Quelle: WHATWG §4.7.2.

---

## 5.2 Content Categories

`del` gehört zu folgenden Content Categories:

- Flow content
- Phrasing content
- Palpable content

Wie bei `ins` ist die Zugehörigkeit zu mehreren Content Categories gleichzeitig möglich.

Quelle: WHATWG §4.7.2.

---

## 5.3 Context

Der Kontext lautet:

**Wo Phrasing Content erwartet wird.**

Die konkrete Verwendung wird zusätzlich durch das transparente Content Model bestimmt.

Quelle: WHATWG §4.7.2.

---

## 5.4 Content Model

Das Content Model von `del` ist:

**Transparent**

Die Zulässigkeit der konkreten Nachfahren hängt daher vom umgebenden Kontext und den transparenten Content-Model-Regeln ab.

Auch bei `del` gilt, dass das Element Paragraphing nicht selbst verändert.

Quelle: WHATWG §4.7.2 und §4.7.4.

---

## 5.5 Tag Omission

Für `del` gilt:

- Starttag darf nicht ausgelassen werden.
- Endtag darf nicht ausgelassen werden.

Es gibt somit keine Tag-Omission-Regel.

Quelle: WHATWG §4.7.2.

---

## 5.6 Content Attributes

`del` besitzt:

- Global Attributes
- `cite`
- `datetime`

Diese Attribute werden gemeinsam mit `ins` in §4.7.3 definiert.

Quelle: WHATWG §4.7.2 und §4.7.3.

---

## 5.7 Semantische Verwendung

`del` kennzeichnet entfernten Inhalt.

Ein typischer Anwendungsfall ist eine Liste von Aufgaben, bei der erledigte bzw. entfernte Einträge weiterhin als Teil der dokumentierten Änderungshistorie markiert werden:

```html
<ul>
  <li>Spülmaschine ausräumen</li>
  <li>
    <del datetime="2009-10-11T01:25-07:00">
      Vorlesungen herunterladen
    </del>
  </li>
  <li>Drucker kaufen</li>
</ul>
```

Die Semantik lautet dabei nicht lediglich „durchgestrichener Text“.

Die visuelle Darstellung ist eine getrennte Rendering-Ebene.

Quelle: WHATWG §4.7.2.

---

## 5.8 Paragraphen und `del`

Wie `ins` beeinflusst `del` die Paragraphing-Struktur nicht.

Daher können insbesondere bei impliziten Paragraphen Situationen entstehen, in denen ein `del`-Element über mehrere inhaltliche Bereiche reicht.

WHATWG empfiehlt, solche Konstruktionen zu vermeiden und Paragraphen explizit mit `p` zu markieren.

Besonders wichtig ist die Regel, dass derselbe `del`-Bereich nicht einfach das Ende eines Paragraphen und den Anfang des unmittelbar folgenden Paragraphen markieren kann.

Dafür sollen getrennte `p`-Elemente und getrennte `del`-Elemente verwendet werden.

Beispiel:

```html
<p>
  Dies ist der erste Absatz.
  <del>Dieser Satz wurde gelöscht.</del>
</p>

<p>
  <del>Dieser Satz wurde ebenfalls gelöscht.</del>
  Dieser Satz blieb bestehen.
</p>
```

Quelle: WHATWG §4.7.2 und §4.7.4.

---

## 5.9 Accessibility

Die aktuelle WHATWG-Definition enthält für `del` ebenfalls Accessibility Considerations für:

- Autoren
- Implementierer

Eine vollständige Accessibility-Referenz wird daraus nicht innerhalb dieser Datei abgeleitet.

Die detaillierte Accessibility-Auswertung bleibt eine separate Rechercheebene.

Quelle: WHATWG §4.7.2.

---

## 5.10 Sanitization

Für `del` ist angegeben:

**Default** mit:

- `cite`
- `datetime`

Damit besitzt `del` dasselbe Sanitization-Grundmodell wie `ins`.

Quelle: WHATWG §4.7.2.

---

## 5.11 DOM Interface

`del` verwendet:

**`HTMLModElement`**

Das Interface ist gemeinsam mit `ins` definiert.

Quelle: WHATWG §4.7.2 und §4.7.3.

---

# 6. Gemeinsame Attribute

## 6.1 Überblick

`ins` und `del` besitzen dieselben zusätzlichen Content Attributes:

| Attribut | Element | Zweck |
|---|---|---|
| `cite` | `ins`, `del` | Quelle bzw. Dokument, das die Änderung erklärt |
| `datetime` | `ins`, `del` | Datum und optional Uhrzeit der Änderung |

Daneben gelten die Global Attributes.

Die beiden Attribute bilden eine eigene Attributebene und werden deshalb nicht als eigenständige HTML-Elemente inventarisiert.

---

# 7. Das `cite`-Attribut

## 7.1 Zweck

Das `cite`-Attribut kann die URL eines Dokuments angeben, das die Änderung erklärt.

Die Spezifikation nennt als Beispiel ein längeres Dokument wie ein Sitzungsprotokoll.

Bei einem langen Quelldokument wird empfohlen, einen URL-Fragmentteil zu verwenden, der direkt auf die relevante Stelle des Dokuments verweist.

---

## 7.2 Konformitätsregel

Wenn `cite` vorhanden ist, muss sein Wert eine **gültige URL** sein, die die Änderung erklärt.

Die URL darf von Leerraum umgeben sein.

Zur Bestimmung des entsprechenden Ziels wird der Wert relativ zum Node Document des Elements geparst.

---

## 7.3 Zweck für User Agents

User Agents können Benutzern ermöglichen, einem solchen Citation Link zu folgen.

Die Spezifikation stellt jedoch heraus, dass das Attribut primär für private bzw. maschinenbezogene Zwecke gedacht ist, beispielsweise für serverseitige Systeme, die Änderungen statistisch erfassen.

Es ist daher nicht als primärer sichtbarer Quellenhinweis für Leser gedacht.

---

## 7.4 Sanitization

`cite` wird bei `ins` und `del` explizit im Sanitization-Modell berücksichtigt.

---

## 7.5 DOM-Bezug

Das `cite`-Attribut wird im gemeinsamen `HTMLModElement`-Interface als:

```webidl
[CEReactions, ReflectURL] attribute USVString cite;
```

abgebildet.

Damit wird das Content Attribute als URL-bezogenes reflektiertes IDL-Attribut repräsentiert.

Quelle: WHATWG §4.7.3.

---

# 8. Das `datetime`-Attribut

## 8.1 Zweck

`datetime` kann Datum und Uhrzeit der Änderung angeben.

Das Attribut ist optional.

---

## 8.2 Zulässiger Wert

Wenn `datetime` vorhanden ist, muss sein Wert ein:

**valid date string with optional time**

sein.

Damit ist nicht beliebiger Text zulässig.

---

## 8.3 Verarbeitung

User Agents müssen den Wert gemäß dem WHATWG-Algorithmus zum Parsen von Datum-/Zeit-Strings verarbeiten.

Wenn das Ergebnis weder ein gültiges `date` noch ein gültiges `global date and time` ergibt, besitzt die Änderung keinen zugeordneten Timestamp.

In diesem Fall ist der Attributwert nicht konform.

---

## 8.4 Globale Datums-/Zeitangabe

Wenn der Wert eine globale Datums-/Zeitangabe enthält, sollen User Agents die zugehörige Zeitzonenoffset-Information verwenden, um zu bestimmen, in welcher Zeitzone die Zeit dargestellt werden soll.

---

## 8.5 Sichtbarkeit

Der Wert von `datetime` kann Benutzern angezeigt werden.

Sein primärer Zweck ist jedoch ebenfalls die maschinenbezogene Verarbeitung der Änderungsinformation.

---

## 8.6 Sanitization

`datetime` wird bei `ins` und `del` ausdrücklich im Sanitization-Modell berücksichtigt.

---

## 8.7 DOM-Bezug

Das Attribut wird im gemeinsamen Interface als:

```webidl
[CEReactions, Reflect] attribute DOMString dateTime;
```

repräsentiert.

Dabei ist zu beachten:

- Content Attribute: `datetime`
- IDL-Attribut: `dateTime`

Quelle: WHATWG §4.7.3.

---

# 9. DOM Interfaces

## 9.1 Gemeinsames Interface

Sowohl `ins` als auch `del` müssen das Interface:

**`HTMLModElement`**

implementieren.

Die aktuelle WHATWG-Definition lautet sinngemäß:

```webidl
[Exposed=Window]
interface HTMLModElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, ReflectURL] attribute USVString cite;
  [CEReactions, Reflect] attribute DOMString dateTime;
};
```

Damit ergibt sich folgende Zuordnung:

| HTML-Element | DOM Interface |
|---|---|
| `ins` | `HTMLModElement` |
| `del` | `HTMLModElement` |

---

## 9.2 `cite` im DOM

Das Content Attribute:

```html
cite
```

wird als:

```text
cite
```

im IDL repräsentiert.

Es ist URL-bezogen.

---

## 9.3 `datetime` im DOM

Das Content Attribute:

```html
datetime
```

wird im IDL als:

```text
dateTime
```

repräsentiert.

Das ist die übliche Unterscheidung zwischen HTML-Content-Attribute und IDL-Attributname.

---

## 9.4 Vererbung

`HTMLModElement` erbt von:

**`HTMLElement`**

Damit stehen neben den spezifischen Mitgliedern des Änderungs-Interfaces die allgemeinen HTMLElement-Funktionalitäten zur Verfügung.

Quelle: WHATWG §4.7.3 und DOM-bezogene Definitionen.

---

# 10. Edits und Paragraphen

## 10.1 Status des Abschnitts

WHATWG §4.7.4 ist ausdrücklich als:

**non-normative**

gekennzeichnet.

Der Abschnitt erläutert also die Verwendung und die Auswirkungen der Paragraphing-Regeln; er führt nicht eine zusätzliche Elementdefinition ein.

---

## 10.2 `ins` und `del` beeinflussen Paragraphing nicht

Die zentrale Aussage lautet:

`ins` und `del` beeinflussen die Paragraphing-Struktur nicht.

Dadurch können bei impliziten Paragraphen Situationen entstehen, in denen ein `ins` oder `del` mehrere inhaltliche Bereiche umfasst.

---

## 10.3 Explizite Paragraphen

Die Spezifikation zeigt, dass `p`-Elemente verwendet werden können, um Paragraphen explizit zu markieren.

Dadurch wird die Änderungsmarkierung wesentlich eindeutiger.

Beispiel:

```html
<section>
  <p>
    Dies ist der erste Absatz.
    <del>Dieser Satz wurde entfernt.</del>
  </p>
  <p>
    <del>Dieser Satz wurde ebenfalls entfernt.</del>
    Dieser Satz blieb erhalten.
  </p>
</section>
```

---

## 10.4 Problematische implizite Paragraphengrenzen

Problematisch ist insbesondere eine Struktur, bei der `ins` oder `del` über die Grenze mehrerer impliziter Paragraphen hinweg verwendet wird.

Beispielsweise kann ein `ins` ein vollständiges `p`-Element und anschließend weiteren Phrasing Content umfassen.

Die Spezifikation bezeichnet entsprechende Konstruktionen als verwirrend bzw. schlechte Praxis.

---

## 10.5 Keine gemeinsame Markierung zweier direkt aufeinanderfolgender Paragraphen

Eine besonders wichtige Regel betrifft den Übergang zwischen zwei direkt aufeinanderfolgenden Paragraphen.

Es ist nicht möglich, das Ende des ersten und den Anfang des zweiten Paragraphen mit demselben `ins`- oder `del`-Element in der gewünschten Weise zu markieren.

Stattdessen müssen getrennte Paragraphen und Änderungsmarkierungen verwendet werden.

Beispiel:

```html
<p>
  Der erste Paragraph.
  <del>Dieser Satz wurde gelöscht.</del>
</p>

<p>
  <del>Dieser Satz wurde ebenfalls gelöscht.</del>
  Dieser Teil blieb bestehen.
</p>
```

---

## 10.6 Empfehlung der Spezifikation

WHATWG empfiehlt ausdrücklich, Paragraphen immer mit `p` zu markieren, anstatt `ins` oder `del` über implizite Paragraphengrenzen hinweg zu führen.

Diese Empfehlung ist für ZE-WebLab als praktische Conformance-/Authoring-Regel relevant.

---

# 11. Edits und Listen

## 11.1 Status des Abschnitts

WHATWG §4.7.5 ist:

**non-normative**

Der Abschnitt beschreibt die praktische Modellierung von Änderungen innerhalb von Listen.

---

## 11.2 `ol` und `ul` erlauben `ins`/`del` nicht direkt als Kinder

Die Content Models von:

- `ol`
- `ul`

erlauben `ins` und `del` nicht als direkte Kinder.

Damit ist beispielsweise folgende Struktur nicht die von WHATWG vorgesehene Methode:

```html
<ul>
  <del>
    <li>Eintrag</li>
  </del>
</ul>
```

Der Grund liegt im Content Model der Listen.

---

## 11.3 Listen repräsentieren weiterhin alle Items

Listen repräsentieren ihre Items weiterhin vollständig.

Das gilt auch für Items, die ansonsten als gelöscht markiert werden könnten.

Ein gelöschtes Listenelement verschwindet also durch die Verwendung von `del` nicht aus dem strukturellen Listenmodell.

---

## 11.4 Ein eingefügtes oder gelöschtes Item

Um ein eingefügtes oder gelöschtes Item zu markieren, kann `ins` bzw. `del` um den **Inhalt des `li`-Elements** gelegt werden.

Beispiel:

```html
<ul>
  <li>
    <ins>Neu eingefügter Eintrag</ins>
  </li>
  <li>
    <del>Entfernter Eintrag</del>
  </li>
</ul>
```

Das `li` bleibt das List Item.

`ins` bzw. `del` kennzeichnet die Änderung innerhalb des Items.

---

## 11.5 Ersetzung eines List Items

Wenn ein Item durch ein anderes ersetzt wurde, kann dasselbe `li` mehrere Änderungsbereiche enthalten:

- ein oder mehrere `del`
- gefolgt von einem oder mehreren `ins`

Beispiel:

```html
<li>
  <del>Alter Wert</del>
  <ins>Neuer Wert</ins>
</li>
```

Damit wird die Ersetzung innerhalb desselben List Items dokumentiert.

---

## 11.6 Verschachtelte Änderungen

WHATWG zeigt auch Fälle, in denen `del` und `ins` verschachtelt werden können, um mehrere historische Änderungen an einem Listeneintrag darzustellen.

Beispielsweise:

```html
<li>
  <del datetime="2008-03-01T20:22Z">
    <ins datetime="2008-02-14T12:02Z">
      Früher eingefügter Eintrag
    </ins>
  </del>
</li>
```

Damit kann die Historie eines Eintrags differenzierter dargestellt werden.

---

## 11.7 Nummerierung

Bei geänderten Listen wird die Nummerierung der List Items nicht so behandelt, als würden `ins` und `del` die historische Entwicklung der Liste rückwirkend in die Listenpositionen einrechnen.

Die Liste repräsentiert weiterhin ihre Items.

Die Änderungsmarkierung dokumentiert den Änderungszustand.

Quelle: WHATWG §4.7.5.

---

# 12. Edits und Tabellen

## 12.1 Status des Abschnitts

WHATWG §4.7.6 ist:

**non-normative**

Der Abschnitt erläutert die Schwierigkeiten bei der Kennzeichnung von Änderungen innerhalb des Tabellenmodells.

---

## 12.2 Tabellenmodell

Die HTML-Tabellenelemente besitzen komplexe Content Models.

Insbesondere die Elemente des Tabellenmodells erlauben `ins` und `del` nicht beliebig an jeder strukturell naheliegenden Position.

Dadurch ist die Markierung von Tabellenänderungen schwieriger als bei normalem Phrasing Content.

---

## 12.3 Hinzufügen einer vollständigen Zeile

Wenn eine komplette Tabellenzeile hinzugefügt wurde, kann der Inhalt jeder einzelnen Zelle mit `ins` markiert werden.

Beispiel:

```html
<table>
  <thead>
    <tr>
      <th>Spiel</th>
      <th>Publisher</th>
      <th>Bewertung</th>
  <tbody>
    <tr>
      <td>Diablo 2</td>
      <td>Blizzard</td>
      <td>8/10</td>
    <tr>
      <td>Portal</td>
      <td>Valve</td>
      <td>10/10</td>
    <tr>
      <td><ins>Portal 2</ins></td>
      <td><ins>Valve</ins></td>
      <td><ins>10/10</ins></td>
</table>
```

Die `tr`-Struktur selbst wird nicht mit `ins` umschlossen.

Stattdessen werden die Inhalte der jeweiligen Zellen markiert.

---

## 12.4 Entfernen einer vollständigen Spalte

Wenn eine komplette Spalte entfernt wurde, kann der Inhalt der betreffenden Zellen mit `del` markiert werden.

Beispiel:

```html
<table>
  <thead>
    <tr>
      <th>Spielname</th>
      <th>Publisher</th>
      <th>
        <del
          cite="/edits/r192"
          datetime="2011-05-02 14:23Z"
        >Bewertung</del>
  <tbody>
    <tr>
      <td>Diablo 2</td>
      <td>Blizzard</td>
      <td>
        <del
          cite="/edits/r192"
          datetime="2011-05-02 14:23Z"
        >8/10</del>
    <tr>
      <td>Portal</td>
      <td>Valve</td>
      <td>
        <del
          cite="/edits/r192"
          datetime="2011-05-02 14:23Z"
        >10/10</del>
    <tr>
      <td>Portal 2</td>
      <td>Valve</td>
      <td>
        <del
          cite="/edits/r192"
          datetime="2011-05-02 14:23Z"
        >10/10</del>
</table>
```

Das Beispiel zeigt gleichzeitig die Kombination von:

- `del`
- `cite`
- `datetime`

zur Dokumentation einer Tabellenänderung.

---

## 12.5 Komplexere Tabellenänderungen

WHATWG weist darauf hin, dass es grundsätzlich keinen guten Weg gibt, wesentlich kompliziertere Tabellenänderungen mit `ins` und `del` auszudrücken.

Als Beispiel wird eine Änderung genannt, bei der eine Tabellenzelle entfernt wird und die nachfolgenden Zellen dadurch nach oben oder links verschoben werden.

Die einfache Markierung einzelner Zellinhalte bildet solche strukturellen Veränderungen nicht vollständig ab.

---

## 12.6 Dokumentationsregel für ZE-WebLab

Für ZE-WebLab ist deshalb zwischen:

1. Änderung des Inhalts einer Zelle,
2. Hinzufügen einer Zeile,
3. Entfernen einer Zeile,
4. Hinzufügen einer Spalte,
5. Entfernen einer Spalte,
6. struktureller Änderung des Tabellenrasters

zu unterscheiden.

WHATWG liefert in §4.7.6 konkrete Muster insbesondere für vollständige Zeilen und Spalten.

Für komplexere Tabellenstrukturänderungen darf aus §4.7.6 keine zusätzliche, nicht belegte allgemeine Änderungsnotation abgeleitet werden.

Quelle: WHATWG §4.7.6.

---

# 13. `ins` versus `del`

Die zentrale fachliche Gegenüberstellung lautet:

| Element | Semantik |
|---|---|
| `ins` | Hinzufügung zum Dokument |
| `del` | Entfernung aus dem Dokument |

Beide teilen:

- Content Categories
- Kontext
- transparentes Content Model
- Tag-Omission-Verhalten
- `cite`
- `datetime`
- Sanitization-Grundmodell
- DOM Interface `HTMLModElement`

Sie unterscheiden sich jedoch in der Änderungssemantik.

---

## 13.1 `ins` ist keine Hervorhebung

`ins` bedeutet nicht:

- wichtig
- hervorgehoben
- fett
- neu aus Sicht des Benutzers ohne Dokumenthistorie

Die Semantik lautet konkret:

**Der Inhalt wurde dem Dokument hinzugefügt.**

---

## 13.2 `del` ist kein allgemeines Durchstreichen

`del` bedeutet nicht lediglich:

- Text soll durchgestrichen dargestellt werden
- Text ist weniger wichtig
- Text ist veraltet

Die Semantik lautet:

**Der Inhalt wurde aus dem Dokument entfernt.**

---

## 13.3 `s` versus `del`

Für ZE-WebLab muss diese Unterscheidung explizit erhalten bleiben:

| Element | Bedeutung |
|---|---|
| `s` | Inhalt ist nicht mehr korrekt oder nicht mehr relevant |
| `del` | Inhalt wurde als Änderung aus dem Dokument entfernt |

`del` gehört zu §4.7.

`s` gehört zu §4.5 „Text-level semantics“.

---

## 13.4 `ins`/`del` versus CSS

Die HTML-Elemente liefern semantische Änderungsinformationen.

CSS kann die Darstellung verändern.

Eine Darstellung wie:

```css
del {
  text-decoration: line-through;
}
```

ist keine vollständige Definition der Semantik von `del`.

Ebenso ist eine grüne Hervorhebung von `ins` keine Voraussetzung für die Bedeutung des Elements.

Die semantische Ebene und die Präsentationsebene bleiben getrennt.

---

# 14. Gemeinsame Regeln für Änderungsmetadaten

## 14.1 Änderungsquelle

`cite` kann angeben, wo die Änderung erklärt wird.

Es ist damit möglich, eine Änderung mit einem externen Änderungsdokument zu verknüpfen.

Die Spezifikation sieht auch die Möglichkeit eines URL-Fragments vor, um bei langen Dokumenten auf den konkreten relevanten Abschnitt zu verweisen.

---

## 14.2 Änderungszeitpunkt

`datetime` kann den Zeitpunkt der Änderung dokumentieren.

Der Wert ist kein beliebiger beschreibender Text.

Er muss dem von WHATWG definierten Format für einen gültigen Datumsstring mit optionaler Zeit entsprechen.

---

## 14.3 Kombination

`cite` und `datetime` können gemeinsam verwendet werden:

```html
<del
  cite="/edits/r192"
  datetime="2011-05-02 14:23Z"
>
  Entfernte Information
</del>
```

Damit können sowohl Änderungsquelle als auch Änderungszeitpunkt angegeben werden.

---

# 15. Normative Sonderregeln

## 15.1 Beide Elemente repräsentieren Dokumentänderungen

Die gemeinsame Oberdefinition von §4.7 ordnet `ins` und `del` der Darstellung von Dokumentänderungen zu.

---

## 15.2 `ins` repräsentiert Hinzufügungen

`ins` repräsentiert eine Addition zum Dokument.

---

## 15.3 `del` repräsentiert Entfernungen

`del` repräsentiert eine Entfernung aus dem Dokument.

---

## 15.4 Transparentes Content Model

Beide Elemente besitzen ein transparentes Content Model.

Das bedeutet, dass die zulässige Struktur vom umgebenden Kontext abhängt.

---

## 15.5 Keine Tag-Auslassung

Weder bei `ins` noch bei `del` ist ein Start- oder Endtag auslassbar.

---

## 15.6 `cite`

Wenn `cite` vorhanden ist:

- muss es eine gültige URL sein,
- muss die URL die Änderung erklären,
- wird die URL relativ zum Node Document des Elements verarbeitet.

---

## 15.7 `datetime`

Wenn `datetime` vorhanden ist:

- muss es ein gültiger Datumsstring mit optionaler Zeit sein,
- wird es nach dem WHATWG-Datum-/Zeit-Parsing verarbeitet,
- kann daraus ein Änderungszeitpunkt bestimmt werden.

Ein nicht erfolgreich parsebarer Wert ist nicht konform und führt nicht zu einem gültigen Änderungs-Timestamp.

---

## 15.8 Paragraphing

`ins` und `del` verändern das Paragraphing nicht.

Daraus folgen die besonderen Empfehlungen aus §4.7.4.

---

## 15.9 Listen

`ins` und `del` dürfen nicht direkt als Kinder von `ol` oder `ul` verwendet werden.

Die Änderungsmarkierung erfolgt innerhalb von `li`.

---

## 15.10 Tabellen

Die Tabellenstruktur verhindert eine beliebige Umhüllung von Tabellenzeilen oder Tabellenzellen mit `ins` bzw. `del`.

Änderungen werden deshalb insbesondere durch Markierung der Zellinhalte ausgedrückt.

---

# 16. Accessibility

## 16.1 WHATWG-Quelle

Die Elementdefinitionen von `ins` und `del` enthalten jeweils einen Abschnitt:

**Accessibility considerations**

Dort wird zwischen Hinweisen für:

- Autoren
- Implementierer

unterschieden.

WHATWG verweist hierfür auf die einschlägigen Accessibility-Spezifikationen.

---

## 16.2 Dokumentationsgrenze

Diese Datei behauptet deshalb nicht, dass die reine HTML-Elementdefinition eine vollständige Accessibility-Referenz darstellt.

Insbesondere werden hier nicht ohne zusätzliche Primärquellen erfunden:

- konkrete ARIA-Rollen,
- Accessibility-API-Mappings,
- Screenreader-Ausgaben,
- herstellerspezifische Interpretationen,
- browserabhängige Accessibility-Verhalten.

---

## 16.3 ZE-WebLab-Status

Für die V1-Referenz wird festgehalten:

- Accessibility Considerations sind in WHATWG vorhanden.
- Eine vertiefte Accessibility-Zuordnung ist eine separate Rechercheebene.
- Browser- und Screenreader-Verhalten wird nicht als WHATWG-Status übernommen.

Quelle: WHATWG §4.7.1 und §4.7.2.

---

# 17. Sanitization

## 17.1 `ins`

WHATWG gibt für `ins` an:

**Default mit `cite` und `datetime`.**

---

## 17.2 `del`

WHATWG gibt für `del` an:

**Default mit `cite` und `datetime`.**

---

## 17.3 Gemeinsames Modell

Damit besitzen beide Elemente dasselbe Sanitization-Grundmodell.

| Element | Sanitization |
|---|---|
| `ins` | Default mit `cite`, `datetime` |
| `del` | Default mit `cite`, `datetime` |

---

## 17.4 Abgrenzung

Sanitization ist nicht dasselbe wie:

- Conformance
- Parsing
- DOM-Semantik
- Accessibility
- Browser-Kompatibilität

Die Sanitization-Information wird deshalb als eigene Referenzdimension geführt.

Quelle: WHATWG §4.7.1 und §4.7.2.

---

# 18. DOM-Interface-Matrix

| HTML-Element | Interface | Spezifische IDL-Mitglieder |
|---|---|---|
| `ins` | `HTMLModElement` | `cite`, `dateTime` |
| `del` | `HTMLModElement` | `cite`, `dateTime` |

Das gemeinsame Interface erbt von `HTMLElement`.

### `HTMLModElement`

Das Interface besitzt:

```webidl
[Exposed=Window]
interface HTMLModElement : HTMLElement {
  [HTMLConstructor] constructor();

  [CEReactions, ReflectURL] attribute USVString cite;
  [CEReactions, Reflect] attribute DOMString dateTime;
};
```

Die konkrete IDL-Ausgestaltung gehört zur DOM-/IDL-Ebene und darf nicht mit der HTML-Elementsemantik vermischt werden.

Quelle: WHATWG §4.7.3.

---

# 19. Querverweise

| Thema | Beziehung zu §4.7 |
|---|---|
| Global Attributes | Beide Elemente akzeptieren Global Attributes |
| Content Categories | `ins` und `del` sind Flow, Phrasing und Palpable Content |
| Transparent Content Model | Bestimmt die zulässige Nachfahrenstruktur |
| Paragraphing | `ins` und `del` beeinflussen Paragraphing nicht |
| `p` | Relevant für die empfohlene explizite Paragraphenstruktur |
| `ol` / `ul` | Relevanz für Änderungen an Listen |
| `li` | Änderungsmarkierungen innerhalb von List Items |
| Tabellenmodell | Relevanz für Änderungen an Tabellen |
| `td` / `th` | Änderungsmarkierungen innerhalb von Tabellenzellen |
| `s` | Semantischer Vergleich mit `del` |
| `cite` | Content Attribute zur Änderungsquelle |
| `datetime` | Content Attribute zum Änderungszeitpunkt |
| DOM | `HTMLModElement` |
| URL-Infrastruktur | Verarbeitung des `cite`-Wertes |
| Datum-/Zeit-Infrastruktur | Verarbeitung von `datetime` |
| Accessibility | WHATWG Accessibility Considerations und externe Accessibility-Spezifikationen |

---

# 20. Beziehung zu anderen HTML-Elementen

## 20.1 `s`

Die wichtigste semantische Abgrenzung innerhalb der Text-Level-Semantik:

```text
s   → nicht mehr korrekt oder relevant
del → als Dokumentänderung entfernt
```

Das bedeutet:

`del` sollte nicht lediglich deshalb eingesetzt werden, weil ein Text heute nicht mehr aktuell ist.

---

## 20.2 `ins` und `p`

`ins` kann `p`-Elemente umfassen, weil sein Content Model transparent ist und es als Flow Content verwendet werden kann.

Das bedeutet jedoch nicht, dass `ins` selbst Paragraphing erzeugt.

---

## 20.3 `del` und `li`

Bei Listen wird `del` innerhalb des `li`-Inhalts verwendet.

Das `li` bleibt der strukturelle Listeneintrag.

---

## 20.4 `ins` und `li`

Analog wird `ins` innerhalb eines `li` verwendet, wenn ein Listeneintrag als hinzugefügt gekennzeichnet werden soll.

---

## 20.5 `ins`/`del` und Tabellenzellen

Bei Tabellen wird die Änderungsmarkierung typischerweise innerhalb von `td` bzw. `th` vorgenommen.

Die Tabellenstruktur selbst wird dadurch nicht durch ein zusätzliches `ins` oder `del` umschlossen.

---

# 21. Beispiele für konforme Änderungsmodelle

## 21.1 Hinzugefügter Absatz

```html
<ins>
  <p>Dieser Absatz wurde neu hinzugefügt.</p>
</ins>
```

---

## 21.2 Entfernte Passage

```html
<p>
  Ein Teil des Dokuments
  <del>ist entfernt worden.</del>
</p>
```

---

## 21.3 Hinzufügung mit Quelle und Zeitpunkt

```html
<ins
  cite="/edits/42"
  datetime="2026-08-11T10:30Z"
>
  Neuer Inhalt
</ins>
```

---

## 21.4 Entfernung mit Quelle und Zeitpunkt

```html
<del
  cite="/edits/43"
  datetime="2026-08-11T11:00Z"
>
  Entfernte Information
</del>
```

---

## 21.5 Ersetzter Listeneintrag

```html
<ul>
  <li>
    <del>Alter Eintrag</del>
    <ins>Neuer Eintrag</ins>
  </li>
</ul>
```

---

## 21.6 Historische Änderung innerhalb eines List Items

```html
<ul>
  <li>
    <del datetime="2026-08-11T11:00Z">
      <ins datetime="2026-08-10T09:00Z">
        Zwischenstand
      </ins>
    </del>
  </li>
</ul>
```

---

## 21.7 Hinzugefügte Tabellenzeile

```html
<table>
  <tbody>
    <tr>
      <td>Bestehender Inhalt</td>
      <td>Bestehender Inhalt</td>
    <tr>
      <td><ins>Neue Zeile</ins></td>
      <td><ins>Neue Daten</ins></td>
  </tbody>
</table>
```

Die Änderungsmarkierung liegt in den Zellinhalten, nicht um dem `tr`.

---

# 22. Typische Fehlinterpretationen

## 22.1 „`ins` bedeutet grüner Text“

Falsch.

`ins` bezeichnet eine Hinzufügung semantisch. Eine grüne Darstellung ist lediglich eine mögliche Präsentation.

---

## 22.2 „`del` bedeutet durchgestrichener Text“

Zu kurz gegriffen.

Die Semantik von `del` ist die Kennzeichnung einer Entfernung aus dem Dokument.

Eine Durchstreichung kann eine Darstellung dieser Information sein.

---

## 22.3 „`del` ist dasselbe wie `s`“

Falsch.

`s` und `del` besitzen unterschiedliche Semantik.

---

## 22.4 „`ins` und `del` erzeugen Paragraphen“

Falsch.

Beide beeinflussen Paragraphing nicht.

---

## 22.5 „`ins` kann direkt um `li` gelegt werden“

Bei einem `ul` oder `ol` ist das nicht die vorgesehene Struktur, weil deren Content Model `ins` bzw. `del` nicht als direkte Kinder zulässt.

Stattdessen wird `ins` bzw. `del` um den Inhalt des `li` gelegt.

---

## 22.6 „Eine komplette Tabellenzeile kann einfach in `ins` eingeschlossen werden“

Die Tabellen-Content-Models erlauben diese allgemeine Umhüllung nicht.

WHATWG zeigt deshalb die Markierung der einzelnen Zellinhalte.

---

## 22.7 „`datetime` ist beliebiger Datums-Text“

Falsch.

Wenn `datetime` vorhanden ist, muss der Wert ein gültiger Date String mit optionaler Zeit sein.

---

## 22.8 „`cite` ist ein sichtbarer Quellenhinweis“

Nicht zwingend.

Das `cite`-Attribut liefert eine URL zur Erklärung der Änderung und ist laut Spezifikation primär für private bzw. maschinenbezogene Zwecke gedacht.

---

# 23. Status / V1

## 23.1 WHATWG-Definitionsstatus

Die beiden Elemente sind im aktuellen WHATWG HTML Living Standard definiert:

- `ins`
- `del`

Beide sind Bestandteil von §4.7 „Edits“.

---

## 23.2 V1-Referenzstatus

Für ZE-WebLab V1 werden aufgenommen:

| Feature | V1 |
|---|---|
| `ins` | aufgenommen |
| `del` | aufgenommen |
| `cite` | als elementbezogenes Attribut dokumentiert |
| `datetime` | als elementbezogenes Attribut dokumentiert |
| `HTMLModElement` | als DOM-Interface dokumentiert |
| Paragraphenregeln | als Konzept-/Verwendungsbereich dokumentiert |
| Listenregeln | als Konzept-/Verwendungsbereich dokumentiert |
| Tabellenregeln | als Konzept-/Verwendungsbereich dokumentiert |

---

## 23.3 Bedeutung des Status

„Im WHATWG-Standard definiert“ bedeutet nicht automatisch:

- jede konkrete Verwendung ist konform,
- jede Attributkombination ist gültig,
- jede Verschachtelung ist zulässig,
- jede Browserimplementierung verhält sich identisch.

Die Konformität hängt unter anderem von:

- Kontext,
- Content Model,
- Content Attributes,
- URL-/Datumswerten,
- Paragraphing,
- Listenstruktur,
- Tabellenstruktur

ab.

---

## 23.4 Browser-Kompatibilität

Browser-Kompatibilität ist nicht Bestandteil des WHATWG-V1-Status.

Die aktuelle WHATWG-Darstellung enthält zwar eingeblendete Informationen zur Browserunterstützung, diese werden nicht in den Status dieser Referenz übernommen.

Browser-Support wird später als separate Rechercheebene dokumentiert.

---

# 24. Prüfmatrix

| Prüfbereich | `ins` | `del` | Status |
|---|---|---|---|
| Elementdefinition | geprüft | geprüft | abgeschlossen |
| Content Categories | geprüft | geprüft | abgeschlossen |
| Context | geprüft | geprüft | abgeschlossen |
| Content Model | geprüft | geprüft | abgeschlossen |
| Tag Omission | geprüft | geprüft | abgeschlossen |
| Global Attributes | geprüft | geprüft | abgeschlossen |
| `cite` | geprüft | geprüft | abgeschlossen |
| `datetime` | geprüft | geprüft | abgeschlossen |
| Accessibility | WHATWG-Verweis geprüft | WHATWG-Verweis geprüft | abgeschlossen auf WHATWG-Ebene |
| Sanitization | geprüft | geprüft | abgeschlossen |
| DOM Interface | `HTMLModElement` | `HTMLModElement` | abgeschlossen |
| Paragraphen | geprüft | geprüft | abgeschlossen |
| Listen | geprüft | geprüft | abgeschlossen |
| Tabellen | geprüft | geprüft | abgeschlossen |
| normative Sonderregeln | geprüft | geprüft | abgeschlossen |
| Querverweise | geprüft | geprüft | abgeschlossen |
| Browser-Support | bewusst getrennt | bewusst getrennt | nicht Bestandteil |
| vertiefte Accessibility-Mappings | separate Ebene | separate Ebene | nicht Bestandteil |

---

# 25. Offene bzw. separat zu bearbeitende Punkte

Die Detailprüfung von WHATWG §4.7 ist abgeschlossen.

Folgende Themen gehören jedoch in eigene Referenzbereiche und sind keine offenen Lücken innerhalb der §4.7-Elementdefinitionen:

1. vollständiges globales Attributinventar,
2. vollständige elementbezogene Attributmatrix,
3. vollständige URL-Syntax und URL-Infrastruktur,
4. vollständige Datum-/Zeit-Syntax und gemeinsame Date-/Time-Infrastruktur,
5. vertiefte Accessibility-Mappings,
6. ARIA- und Accessibility-API-Auswertung,
7. Browser-Kompatibilität,
8. vollständige Tabellen-Content-Model-Referenz,
9. vollständige Listen-Content-Model-Referenz,
10. vollständige Paragraphing-/Content-Model-Referenz,
11. übergreifendes Sanitization-Modell.

Diese Punkte stellen keine fehlenden Bestandteile der §4.7-Recherche dar.

Insbesondere wurden keine zusätzlichen HTML-Elemente aus den Unterabschnitten 4.7.3 bis 4.7.6 erzeugt.

---

# 26. Recherchefazit

WHATWG §4.7 ist eine kleine, aber strukturell wichtige Elementfamilie.

Der Bereich definiert genau zwei HTML-Elemente:

- `ins`
- `del`

Beide dienen der semantischen Kennzeichnung von Dokumentänderungen.

Dabei bestehen mehrere gemeinsame Eigenschaften:

- Flow Content
- Phrasing Content
- Palpable Content
- Verwendung dort, wo Phrasing Content erwartet wird
- transparentes Content Model
- keine Tag-Auslassung
- Global Attributes
- `cite`
- `datetime`
- Sanitization Default mit `cite` und `datetime`
- DOM Interface `HTMLModElement`

Die entscheidende semantische Unterscheidung lautet:

```text
ins = Hinzufügung
del = Entfernung
```

Die beiden Elemente sind nicht bloß visuelle Werkzeuge.

---

## 26.1 Paragraphen

`ins` und `del` beeinflussen Paragraphing nicht.

Daraus entstehen besondere Fälle bei impliziten Paragraphen.

WHATWG empfiehlt deshalb, Paragraphen explizit mit `p` zu markieren und Änderungsmarkierungen nicht über implizite Paragraphengrenzen hinweg zu führen.

---

## 26.2 Listen

Bei `ol` und `ul` dürfen `ins` und `del` nicht als direkte Kinder verwendet werden.

Stattdessen werden Änderungsmarkierungen innerhalb des `li`-Inhalts eingesetzt.

Ein List Item kann beispielsweise so ersetzt werden:

```html
<li>
  <del>Alter Eintrag</del>
  <ins>Neuer Eintrag</ins>
</li>
```

---

## 26.3 Tabellen

Das Tabellenmodell erschwert die direkte Kennzeichnung struktureller Änderungen.

WHATWG zeigt deshalb insbesondere:

- Markierung der Inhalte einer hinzugefügten Zeile mit `ins`
- Markierung der Inhalte einer entfernten Spalte mit `del`

Für komplexere strukturelle Tabellenänderungen bietet §4.7.6 keine allgemeine Änderungsnotation.

---

## 26.4 Attribute

Die beiden gemeinsamen Attribute sind fachlich eigenständig zu dokumentieren:

- `cite` → URL zur Erklärung der Änderung
- `datetime` → Datum und optionaler Zeitpunkt der Änderung

Beide besitzen eigene Konformitätsregeln.

---

## 26.5 DOM

`ins` und `del` implementieren gemeinsam:

**`HTMLModElement`**

Das Interface stellt insbesondere die IDL-Eigenschaften:

- `cite`
- `dateTime`

bereit.

---

## 26.6 Abgrenzung zu §4.5

Die wichtigste Verbindung zum bereits bearbeiteten Bereich „Text-level semantics“ ist die Unterscheidung zwischen:

```text
s   → nicht mehr korrekt oder relevant
del → als Änderung entfernt
```

Damit darf `del` nicht als bloße Variante von `s` dokumentiert werden.

---

# 27. Quellen / Referenzen

## Primärquelle

- WHATWG HTML Living Standard, §4.7 „Edits“.
- WHATWG HTML Living Standard, §4.7.1 „The `ins` element“.
- WHATWG HTML Living Standard, §4.7.2 „The `del` element“.
- WHATWG HTML Living Standard, §4.7.3 „Attributes common to `ins` and `del` elements“.
- WHATWG HTML Living Standard, §4.7.4 „Edits and paragraphs“.
- WHATWG HTML Living Standard, §4.7.5 „Edits and lists“.
- WHATWG HTML Living Standard, §4.7.6 „Edits and tables“.

## Verwendete fachliche Primärinformationen

Geprüft wurden insbesondere:

- Elementdefinitionen,
- Content Categories,
- Context,
- Content Model,
- Tag-Omission-Regeln,
- Content Attributes,
- Accessibility Considerations,
- Sanitization,
- DOM Interface,
- Definition von `cite`,
- Definition von `datetime`,
- Datum-/Zeit-Parsing für `datetime`,
- URL-Verarbeitung für `cite`,
- Paragraphing-Verhalten,
- Listen-Content-Model,
- Tabellen-Content-Model,
- normative bzw. informative Verwendungsregeln.

## Externe Quellen

Für die fachlichen Aussagen dieser Datei wurden keine externen Quellen als Ersatz für die WHATWG-Primärquelle verwendet.

Die Accessibility-Abschnitte der WHATWG-Definition verweisen ihrerseits auf einschlägige externe Accessibility-Spezifikationen. Diese werden in dieser Datei nicht als vollständig recherchierte Accessibility-Referenz ausgegeben.

---

## 28. Prüfstatus

**WHATWG §4.7 – Edits: abgeschlossen**

Geprüfter Elementbestand:

- `ins`
- `del`

Geprüfte Unterkonzepte:

- gemeinsame Attribute `cite` und `datetime`
- `HTMLModElement`
- Paragraphing
- Listen
- Tabellen
- Accessibility Considerations
- Sanitization
- normative Konformitätsregeln
- Querverweise
- Status-/V1-Einordnung

**Browser-Kompatibilität:** bewusst nicht Bestandteil des WHATWG-Konformitätsstatus.

**Vertiefte Accessibility-Mappings:** separate Rechercheebene.

**Elementinventar §4.7:** vollständig mit 2 HTML-Elementen.

**Prüfstatus:** abgeschlossen auf Basis der aktuellen WHATWG HTML Living Standard, Quellenstand 11. August 2026.