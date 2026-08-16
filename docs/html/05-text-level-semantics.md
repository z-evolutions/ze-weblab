# ZE-WebLab – HTML-Referenz: Text-level semantics

## Arbeitsstand

**Datei:** `docs/html/05-text-level-semantics.md`

**Themenbereich:** WHATWG HTML Living Standard – §4.5 Text-level semantics

**Recherche-/Dokumentationsstand:** 16.08.2026

**Geprüfter WHATWG-Spezifikationsstand:** Living Standard, zuletzt aktualisiert am 11.08.2026.

**Primärquelle:** WHATWG HTML Living Standard, Abschnitt 4.5 „Text-level semantics“.

**Status der Recherche:** abgeschlossen.

Diese Datei dokumentiert den WHATWG-Abschnitt §4.5 als fachliche Referenz für ZE-WebLab. Die Elementinventarisierung wird von allgemeinen Konzepten, globalen Attributen, APIs und externen Accessibility-Spezifikationen getrennt gehalten.

Browser-Kompatibilität wird nicht als WHATWG-Status interpretiert. Die im WHATWG-Dokument eingeblendeten MDN-Supportinformationen sind deshalb für die Statusbewertung dieser Datei nicht maßgeblich.

---

## Quellenstand

### Primärquelle

WHATWG HTML Living Standard:

- Abschnitt 4.5 „Text-level semantics“
- Unterabschnitte 4.5.1 bis 4.5.29
- Elementdefinitionen einschließlich Kategorien, Contexts, Content Models, Tag Omission, Content Attributes, Accessibility Considerations, Sanitization und DOM Interface
- normative Anforderungen innerhalb der jeweiligen Elementdefinitionen
- nichtnormativer Usage Summary in §4.5.29

Die aktuelle WHATWG-Seite weist für den recherchierten Stand „Living Standard — Last Updated 11 August 2026“ aus.

### Externe Quellen

Die WHATWG-Elementdefinitionen verweisen für Accessibility auf:

- ARIA in HTML für Autoranforderungen
- HTML Accessibility API Mappings (HTML-AAM) für Implementierungsanforderungen

Diese externen Spezifikationen werden hier nicht als Ersatz für die WHATWG-Elementdefinitionen verwendet.

Detaillierte Accessibility-Rollen, States, Properties und Plattform-Mappings gehören in die separate Accessibility-Recherche.

### Fachliche Ableitung

Die Zusammenfassung von Content Categories, Contexts, Content Models und DOM Interfaces in dieser Datei ist eine strukturierte Dokumentation der jeweiligen WHATWG-Angaben.

Wo die WHATWG-Definition auf „prose“, einen Algorithmus oder eine externe Spezifikation verweist, wird dies ausdrücklich kenntlich gemacht.

---

# 1. WHATWG-Struktur

Der recherchierte Abschnitt §4.5 enthält folgende Unterabschnitte:

1. §4.5.1 The `a` element
2. §4.5.2 The `em` element
3. §4.5.3 The `strong` element
4. §4.5.4 The `small` element
5. §4.5.5 The `s` element
6. §4.5.6 The `cite` element
7. §4.5.7 The `q` element
8. §4.5.8 The `dfn` element
9. §4.5.9 The `abbr` element
10. §4.5.10 The `ruby` element
11. §4.5.11 The `rt` element
12. §4.5.12 The `rp` element
13. §4.5.13 The `data` element
14. §4.5.14 The `time` element
15. §4.5.15 The `code` element
16. §4.5.16 The `var` element
17. §4.5.17 The `samp` element
18. §4.5.18 The `kbd` element
19. §4.5.19 The `sub` and `sup` elements
20. §4.5.20 The `i` element
21. §4.5.21 The `b` element
22. §4.5.22 The `u` element
23. §4.5.23 The `mark` element
24. §4.5.24 The `bdi` element
25. §4.5.25 The `bdo` element
26. §4.5.26 The `span` element
27. §4.5.27 The `br` element
28. §4.5.28 The `wbr` element
29. §4.5.29 Usage summary

Damit umfasst das Elementinventar dieses Themenblocks 30 HTML-Elementnamen:

- `a`
- `em`
- `strong`
- `small`
- `s`
- `cite`
- `q`
- `dfn`
- `abbr`
- `ruby`
- `rt`
- `rp`
- `data`
- `time`
- `code`
- `var`
- `samp`
- `kbd`
- `sub`
- `sup`
- `i`
- `b`
- `u`
- `mark`
- `bdi`
- `bdo`
- `span`
- `br`
- `wbr`

`sub` und `sup` werden in der WHATWG gemeinsam definiert und deshalb als gemeinsame Elementfamilie dokumentiert.

§4.5.29 ist kein weiteres Element. Es handelt sich um eine nichtnormative Übersicht der vorgesehenen Verwendung der Elemente.

---

# 2. Inventar

| Element | WHATWG-Abschnitt | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|
| `a` | §4.5.1 | Flow, Phrasing, bei `href` Interactive, Palpable | Wo Phrasing Content erwartet wird | Transparent; Einschränkungen für interaktiven Inhalt, `a` und `tabindex` | keine Auslassung | Global; `href`, `target`, `download`, `ping`, `rel`, `hreflang`, `type`, `referrerpolicy` | Default; URL-bezogene Sonderbehandlung | `HTMLAnchorElement` | definiert |
| `em` | §4.5.2 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `strong` | §4.5.3 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `small` | §4.5.4 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `s` | §4.5.5 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `cite` | §4.5.6 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `q` | §4.5.7 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global; `cite` | Default | `HTMLQuoteElement` | definiert |
| `dfn` | §4.5.8 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content, mit Regeln zur definierenden Terminologie | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `abbr` | §4.5.9 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content; keine `dfn`-Nachfahren | keine Auslassung | Global; `title` mit spezieller Semantik | Default | `HTMLElement` | definiert |
| `ruby` | §4.5.10 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | spezielles Ruby-Modell gemäß Prosa | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `rt` | §4.5.11 | keine | Als Kind eines `ruby`-Elements | Phrasing Content | Endtag unter definierten Bedingungen auslassbar | Global | Default | `HTMLElement` | definiert |
| `rp` | §4.5.12 | keine | Als Kind von `ruby`, unmittelbar vor/nach `rt` | Text | Endtag unter definierten Bedingungen auslassbar | Global | Default | `HTMLElement` | definiert |
| `data` | §4.5.13 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global; `value` | Default; `value` | `HTMLDataElement` | definiert |
| `time` | §4.5.14 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | mit `datetime`: Phrasing Content; ohne `datetime`: Text mit weiteren Anforderungen | keine Auslassung | Global; `datetime` | Default; `datetime` | `HTMLTimeElement` | definiert |
| `code` | §4.5.15 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `var` | §4.5.16 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `samp` | §4.5.17 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `kbd` | §4.5.18 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `sub` | §4.5.19 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `sup` | §4.5.19 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `i` | §4.5.20 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `b` | §4.5.21 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `u` | §4.5.22 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `mark` | §4.5.23 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLElement` | definiert |
| `bdi` | §4.5.24 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global; `dir` mit spezieller Semantik | Default | `HTMLElement` | definiert |
| `bdo` | §4.5.25 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global; `dir` mit spezieller Semantik | Default | `HTMLElement` | definiert |
| `span` | §4.5.26 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet wird | Phrasing Content | keine Auslassung | Global | Default | `HTMLSpanElement` | definiert |
| `br` | §4.5.27 | Flow, Phrasing | Wo Phrasing Content erwartet wird | Nothing | kein Endtag | Global | Default | `HTMLBRElement` | definiert |
| `wbr` | §4.5.28 | Flow, Phrasing | Wo Phrasing Content erwartet wird | Nothing | kein Endtag | Global | Default | `HTMLElement` | definiert |

Die Tabelle ist eine strukturierte Zusammenfassung der jeweiligen WHATWG-Elementdefinitionen. Bei Elementen mit speziellen Prosa-Regeln ist das vereinfachte Tabellenfeld nicht als Ersatz für die nachfolgenden Detailprüfungen zu verstehen.

---

# 3. Detailprüfung: `a`

## WHATWG

**Abschnitt:** §4.5.1 The `a` element

## Content Categories

`a` ist:

- Flow Content
- Phrasing Content
- Palpable Content
- zusätzlich Interactive Content, wenn das Element ein `href`-Attribut besitzt

Die Interactive-Content-Zugehörigkeit ist damit vom Vorhandensein von `href` abhängig.

## Context

Das Element darf verwendet werden, wenn Phrasing Content erwartet wird.

## Content Model

Das Content Model ist transparent.

Es gelten jedoch zusätzliche Einschränkungen:

- Es darf keinen interaktiven Inhalt als Nachfahren geben.
- Es darf kein `a`-Element als Nachfahre geben.
- Es darf keinen Nachfahren geben, auf dem das `tabindex`-Attribut angegeben ist.

Das transparente Modell bedeutet nicht, dass beliebiger Inhalt ohne weitere Einschränkungen erlaubt ist.

## Tag Omission

Weder Starttag noch Endtag dürfen ausgelassen werden.

## Content Attributes

Neben den Global Attributes sind vorgesehen:

- `href` – Adresse des Hyperlinks
- `target` – Navigable für die Navigation des Hyperlinks
- `download` – Download statt Navigation und optionaler Dateiname
- `ping` – URLs, an die beim Folgen des Hyperlinks Ping-Anfragen gesendet werden
- `rel` – Beziehung zwischen Ausgangsort und Zielressource
- `hreflang` – Sprache der verknüpften Ressource
- `type` – Hinweis auf den Typ der referenzierten Ressource
- `referrerpolicy` – Referrer Policy für durch das Element initiierte Fetches

## Normative Abhängigkeit von `href`

Mit `href` stellt `a` einen Hyperlink dar.

Ohne `href` stellt `a` einen Platzhalter für einen möglichen Link dar und besteht semantisch aus seinem Inhalt.

Die Attribute

- `target`
- `download`
- `ping`
- `rel`
- `hreflang`
- `type`
- `referrerpolicy`

müssen weggelassen werden, wenn `href` nicht vorhanden ist.

Für `itemprop` gilt eine zusätzliche Regel: Wird `itemprop` auf `a` verwendet, muss auch `href` angegeben sein.

## Semantische Funktion

Mit `href` repräsentiert `a` einen Hyperlink, einen sogenannten Hypertext Anchor, der durch seinen Inhalt beschriftet ist.

Ohne `href` ist `a` kein Hyperlink.

Das Element kann aufgrund seines transparenten Content Models große Inhaltsbereiche umfassen, sofern die Beschränkungen bezüglich interaktiven Inhalts eingehalten werden.

## Accessibility

Die WHATWG-Definition verweist für die Accessibility-Betrachtung auf externe Autor- und Implementierungsregeln.

Für ZE-WebLab wird deshalb hier keine eigenständige Rollen-/State-/Property-Tabelle erfunden.

Die Accessibility-Ebene ist separat zu vertiefen.

## Sanitization

Die WHATWG-Definition ordnet `a` der **Default**-Sanitization zu.

Zusätzlich werden `href`, `hreflang` und `type` als relevante Attribute genannt; `href` gehört dabei zu den navigating URL attributes.

## DOM Interface

```text
HTMLAnchorElement : HTMLElement
```

Die WHATWG-Definition enthält insbesondere:

- `download`
- `ping`
- `rel`
- `relList`
- `text`
- `referrerPolicy`

sowie die von HyperlinkElementUtils beziehungsweise HTMLHyperlinkElementUtils bereitgestellten Eigenschaften.

Die `text`-IDL-Eigenschaft entspricht dem descendant text content.

Der Setter ersetzt den Inhalt des Elements durch den angegebenen String.

---

# 4. Detailprüfung: `em`

## WHATWG

**Abschnitt:** §4.5.2 The `em` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung von Start- oder Endtag.

## Content Attributes

Nur Global Attributes.

## Semantik

`em` repräsentiert **Stress Emphasis** des Inhalts.

Die Intensität der Stress Emphasis wird durch die Anzahl der verschachtelten `em`-Vorfahren bestimmt.

Die Platzierung der Stress Emphasis kann die Bedeutung eines Satzes verändern. Die konkrete sprachliche Verwendung hängt von der jeweiligen Sprache ab.

`em` ist deshalb nicht lediglich ein typografisches „kursiv“.

## Accessibility

WHATWG verweist auf die entsprechenden Accessibility Considerations für Autoren und Implementierer.

Eine konkrete ARIA-Rollenabbildung wird hier nicht erfunden.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 5. Detailprüfung: `strong`

## WHATWG

**Abschnitt:** §4.5.3 The `strong` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`strong` repräsentiert eine hohe **Wichtigkeit, Ernsthaftigkeit oder Dringlichkeit** seines Inhalts.

Die WHATWG-Beschreibung behandelt `strong` nicht als reine Darstellung von Fettschrift.

Verschachtelung kann zur Kennzeichnung zunehmender Wichtigkeit verwendet werden.

## Abgrenzung

`strong` ist insbesondere nicht mit `b` gleichzusetzen:

- `strong` → Importance
- `b` → Aufmerksamkeit für einen utilitaristischen Zweck ohne zusätzliche Wichtigkeitssemantik

Für Stress Emphasis ist `em` vorgesehen.

## Accessibility

WHATWG verweist auf die einschlägigen Accessibility-Regeln.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 6. Detailprüfung: `small`

## WHATWG

**Abschnitt:** §4.5.4 The `small` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`small` repräsentiert **Side Comments**, beispielsweise:

- Kleingedrucktes
- Copyright-Hinweise
- rechtliche Hinweise
- ähnliche ergänzende Informationen

Die WHATWG-Definition stellt klar, dass `small` nicht ausschließlich über eine kleinere Schriftgröße definiert wird.

## Abgrenzung

Die Verwendung von `small` für bloße visuelle Größenänderung ist keine semantische Definition des Elements.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 7. Detailprüfung: `s`

## WHATWG

**Abschnitt:** §4.5.5 The `s` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`s` repräsentiert Inhalt, der **nicht mehr korrekt oder nicht mehr relevant** ist.

## Abgrenzung zu `del`

`s` ist ausdrücklich nicht das Element für Dokumentänderungen.

Wenn Inhalt als aus einem Dokument entfernt markiert werden soll, ist `del` aus §4.7 vorgesehen.

Damit gilt:

- `s` → nicht mehr zutreffender bzw. nicht mehr relevanter Inhalt
- `del` → dokumentierte Änderung bzw. Entfernung

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 8. Detailprüfung: `cite`

## WHATWG

**Abschnitt:** §4.5.6 The `cite` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`cite` repräsentiert den **Titel eines Werkes**.

Die WHATWG-Definition nennt unter anderem:

- Bücher
- wissenschaftliche Arbeiten
- Essays
- Gedichte
- Partituren
- Lieder
- Drehbücher
- Filme
- Fernsehsendungen
- Spiele
- Skulpturen
- Gemälde
- Theaterproduktionen
- Opern
- Musicals
- Ausstellungen
- juristische Fallberichte
- Computerprogramme

Ein Werk kann dabei gerade zitiert oder ausführlich referenziert werden oder lediglich beiläufig erwähnt werden.

## Nicht für Personennamen

Der Name einer Person ist kein Werktitel.

`cite` darf deshalb nicht einfach zur Markierung von Personennamen verwendet werden.

## Interpunktion

Wenn ein Werktitel konventionell durch Interpunktion vom umgebenden Text getrennt wird, gehört diese Interpunktion nicht zum Titel und damit nicht in das `cite`-Element.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 9. Detailprüfung: `q`

## WHATWG

**Abschnitt:** §4.5.7 The `q` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Global Attributes sowie:

- `cite` – Link zur Quelle des Zitats bzw. zu weiteren Informationen über das Zitat

## Semantik

`q` repräsentiert Phrasing Content, der aus einer anderen Quelle zitiert wird.

## Zitierzeichen

Die WHATWG-Definition behandelt die für das Zitat vorgesehenen Anführungszeichen als Rendering-Verantwortung des User Agents.

Anführungszeichen, die das Zitat selbst darstellen sollen, dürfen deshalb nicht zusätzlich unmittelbar vor, nach oder innerhalb des `q`-Elements in den Inhalt geschrieben werden.

## Verwendung

`q` ist für tatsächliche Zitate vorgesehen.

Es ist nicht als generisches Element für:

- Sarkasmus
- beliebige Hervorhebung
- typografische Anführungszeichen
- Text, der nur zufällig in Anführungszeichen steht

definiert.

Die Verwendung von `q` für Zitate ist optional; ein explizit mit Interpunktion markiertes Zitat ohne `q` kann ebenfalls korrekt sein.

## Sanitization

Default.

## DOM Interface

`HTMLQuoteElement`.

---

# 10. Detailprüfung: `dfn`

## WHATWG

**Abschnitt:** §4.5.8 The `dfn` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

Die WHATWG-Definition enthält zusätzliche Regeln dafür, wie der definierte Begriff und seine umgebende Definition bestimmt werden.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`dfn` markiert die **defining instance** eines Begriffes.

Das Element ist damit nicht einfach ein allgemeines „Glossar-Element“.

Die Definition eines Begriffes wird durch den Kontext des umgebenden Absatzes beziehungsweise des einschlägigen Abschnitts bestimmt.

## Verknüpfung mit `abbr`

Ein definierter Begriff kann beispielsweise mit `dfn` und einer darin enthaltenen `abbr`-Markierung kombiniert werden.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 11. Detailprüfung: `abbr`

## WHATWG

**Abschnitt:** §4.5.9 The `abbr` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

Zusätzlich darf es keine `dfn`-Nachfahren enthalten.

## Tag Omission

Keine Auslassung.

## Content Attributes

Global Attributes.

Zusätzlich besitzt `title` eine besondere Semantik:

`title` kann die vollständige Bezeichnung beziehungsweise Expansion der Abkürzung enthalten.

Wenn `title` verwendet wird, muss sein Wert die Expansion der Abkürzung und nichts anderes enthalten.

## Semantik

`abbr` repräsentiert eine Abkürzung oder ein Akronym, optional mit Expansion.

Die WHATWG-Definition erlaubt auch `abbr` ohne Expansion.

## Pluralbildung

Wenn eine Abkürzung pluralisiert wird, muss die grammatische Zahl der Expansion mit dem Inhalt des `abbr`-Elements übereinstimmen.

## Accessibility

Die konkrete Interpretation von Abkürzungen und Expansionen kann für assistive Technologien relevant sein. WHATWG verweist für die konkrete Accessibility-Ebene auf die einschlägigen Accessibility-Spezifikationen.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 12. Detailprüfung: `ruby`

## WHATWG

**Abschnitt:** §4.5.10 The `ruby` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Das Content Model wird in der WHATWG-Definition über eine ausführliche Prosa-/Strukturdefinition beschrieben.

Es ist nicht angemessen, das Modell lediglich als „beliebiger Phrasing Content“ zu verkürzen.

`ruby` besteht aus einem oder mehreren strukturierten Sequenztypen, die Basistexte und Ruby-Annotationen miteinander verknüpfen.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`ruby` ermöglicht die Kennzeichnung von Phrasing Content mit **Ruby-Anmerkungen**.

Ruby-Anmerkungen sind kurze Textabschnitte, die zusammen mit einem Basistext dargestellt werden.

Der hauptsächliche Anwendungsfall ist die ostasiatische Typografie, beispielsweise:

- Aussprachehinweise
- Furigana
- zusätzliche Annotationen
- Übersetzungs- oder Bedeutungsinformationen

## Ruby-Segmentmodell

Die WHATWG-Definition beschreibt Ruby nicht nur als einfache Kombination aus:

```html
<ruby>Basis<rt>Annotation</rt></ruby>
```

Vielmehr werden:

- Base Text Segments
- Annotation Segments
- Zuordnungen zwischen beiden
- DOM Ranges

konzeptionell unterschieden.

Ein Annotation Segment besteht aus einem DOM Range, der genau ein `rt`-Element umfasst.

Die Ruby-Repräsentation ergibt sich aus den Basissegmenten und deren Zuordnung zu Annotationen.

## Verschachtelte Ruby-Strukturen

Die Spezifikation erlaubt auch verschachtelte Ruby-Konstruktionen.

Dadurch können beispielsweise mehrere Annotationsebenen für denselben Basistext ausgedrückt werden.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 13. Detailprüfung: `rt`

## WHATWG

**Abschnitt:** §4.5.11 The `rt` element

## Content Categories

Keine.

## Context

Als Kind eines `ruby`-Elements.

## Content Model

Phrasing Content.

## Tag Omission

Der Endtag darf ausgelassen werden, wenn:

- das `rt`-Element unmittelbar von einem weiteren `rt`-Element gefolgt wird,
- es unmittelbar von einem `rp`-Element gefolgt wird,
- oder kein weiterer Inhalt im Elternelement vorhanden ist.

Der Starttag ist nicht auslassbar.

## Content Attributes

Nur Global Attributes.

## Semantik

`rt` markiert den Ruby-Textbestandteil einer Ruby-Annotation.

Als Kind von `ruby` repräsentiert `rt` nicht selbstständig einen eigenen sichtbaren Inhalt im semantischen Ruby-Modell, sondern wird von `ruby` zur Bestimmung der Annotation verwendet.

Ein `rt`, das nicht Kind eines `ruby`-Elements ist, repräsentiert dasselbe wie seine Kinder.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 14. Detailprüfung: `rp`

## WHATWG

**Abschnitt:** §4.5.12 The `rp` element

## Content Categories

Keine.

## Context

Als Kind eines `ruby`-Elements und zwar unmittelbar vor oder unmittelbar nach einem `rt`-Element.

## Content Model

Text.

## Tag Omission

Der Endtag darf ausgelassen werden, wenn:

- unmittelbar ein `rt` folgt,
- unmittelbar ein weiteres `rp` folgt,
- oder kein weiterer Inhalt im Elternelement vorhanden ist.

## Content Attributes

Nur Global Attributes.

## Semantik

`rp` stellt Klammern oder anderen Inhalt bereit, der von User Agents ohne Ruby-Unterstützung dargestellt werden kann.

Innerhalb eines `ruby`-Elements repräsentiert `rp` nichts.

Außerhalb eines `ruby`-Elements repräsentiert `rp` seine Kinder.

## Fallback-Funktion

Ein typisches Muster ist:

```html
<ruby>
  漢
  <rp>（</rp>
  <rt>かん</rt>
  <rp>）</rp>
</ruby>
```

Bei Ruby-Unterstützung wird `rp` nicht als Bestandteil der Ruby-Repräsentation verwendet.

Bei fehlender Ruby-Unterstützung kann der Inhalt von `rp` zur Darstellung der Annotation in einer Fallback-Form dienen.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 15. Detailprüfung: `data`

## WHATWG

**Abschnitt:** §4.5.13 The `data` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Global Attributes sowie:

- `value` – maschinenlesbarer Wert

`value` muss vorhanden sein.

## Semantik

`data` repräsentiert seinen sichtbaren Inhalt zusammen mit einer maschinenlesbaren Form dieses Inhalts.

Der maschinenlesbare Wert wird durch `value` bereitgestellt.

## Normative `value`-Regel

Das `value`-Attribut muss eine maschinenlesbare Repräsentation des Inhalts enthalten.

## Abgrenzung zu `time`

Wenn der maschinenlesbare Wert datums- oder zeitbezogen ist, soll das speziellere `time`-Element verwendet werden.

## Einsatz mit Microdata und Microformats

`data` kann mit Microformats oder den Microdata-Attributen von HTML kombiniert werden.

Damit können:

- menschenlesbarer Inhalt für die Darstellung
- maschinenlesbarer Wert für Datenverarbeitung

parallel bereitgestellt werden.

## Sanitization

Default mit `value` als speziell genanntem Attribut.

## DOM Interface

`HTMLDataElement`.

IDL:

```text
attribute DOMString value;
```

---

# 16. Detailprüfung: `time`

## WHATWG

**Abschnitt:** §4.5.14 The `time` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Wenn `datetime` vorhanden ist:

- Phrasing Content

Wenn `datetime` nicht vorhanden ist:

- Text
- zusätzlich müssen die in der WHATWG-Definition beschriebenen Anforderungen erfüllt sein

## Tag Omission

Keine Auslassung.

## Content Attributes

Global Attributes sowie:

- `datetime` – maschinenlesbarer Wert

## Semantik

`time` repräsentiert seinen Inhalt zusammen mit einer maschinenlesbaren Repräsentation eines:

- Datums
- Zeitpunkts
- Zeitbereichs beziehungsweise entsprechenden Datums-/Zeitwerts
- Zeitzonen-Offsets
- Zeitdauer

Die konkrete zulässige Syntax ist in der WHATWG-Definition über die verschiedenen Datums-/Zeit-String-Grammatiken festgelegt.

## `datetime`

Wenn `datetime` vorhanden ist, muss dessen Wert eine gültige maschinenlesbare Repräsentation des dargestellten Inhalts sein.

Wenn `datetime` nicht vorhanden ist, wird der Datetime-Wert aus dem Child Text Content des Elements bestimmt.

## Keine Element-Nachfahren ohne `datetime`

Ein `time`-Element ohne `datetime` darf keine Element-Nachfahren besitzen.

Das Content Model „Text“ ist deshalb nicht lediglich eine verkürzte Darstellung, sondern eine normative Einschränkung.

## Datetime Value

Der Datetime-Wert eines `time`-Elements ist:

1. der Wert von `datetime`, wenn das Attribut vorhanden ist,
2. andernfalls der Child Text Content des Elements.

Dieser Wert muss einer der in der Spezifikation beschriebenen gültigen syntaktischen Formen entsprechen.

## Sanitization

Default mit `datetime`.

## DOM Interface

`HTMLTimeElement`.

IDL:

```text
attribute DOMString dateTime;
```

---

# 17. Detailprüfung: `code`

## WHATWG

**Abschnitt:** §4.5.15 The `code` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`code` repräsentiert einen **Fragment von Computer Code**.

Der Begriff ist nicht auf eine bestimmte Programmiersprache beschränkt.

Beispiele umfassen:

- Programmnamen
- Methoden
- Variablen
- Schlüsselwörter
- syntaktische Fragmente
- Codefragmente innerhalb von Prosa

## Kombination mit `pre`

Für Block-Code kann `pre` mit `code` kombiniert werden.

Beispielsweise:

```html
<pre><code class="language-pascal">var i: Integer;
begin
  i := 1;
end.</code></pre>
```

Die `class`-Angabe kann dabei die verwendete Sprache kennzeichnen.

Die Semantik der konkreten Klassenwerte ist nicht Bestandteil der `code`-Elementdefinition.

## Abgrenzung

`code` kennzeichnet Code.

Für Variablen ist `var` vorgesehen.

Für Computer-Ausgabe ist `samp` vorgesehen.

Für Benutzereingaben ist `kbd` vorgesehen.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 18. Detailprüfung: `var`

## WHATWG

**Abschnitt:** §4.5.16 The `var` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`var` repräsentiert eine Variable.

Das kann beispielsweise sein:

- eine mathematische Variable
- eine Variable in einem Programm
- ein Bezeichner für eine Konstante
- ein Symbol für eine physikalische Größe
- ein Funktionsparameter
- ein Platzhalterbegriff in Prosa

## Mathematik

Für komplexere mathematische Ausdrücke ist MathML geeigneter.

`var` kann jedoch weiterhin zur Kennzeichnung einzelner Variablen verwendet werden, auch innerhalb beziehungsweise in Verbindung mit MathML.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 19. Detailprüfung: `samp`

## WHATWG

**Abschnitt:** §4.5.17 The `samp` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`samp` repräsentiert **Computer Output**.

Es kann insbesondere verwendet werden, um Text zu kennzeichnen, den ein Computersystem ausgegeben hat.

## Verhältnis zu `kbd`

Die WHATWG-Definition unterscheidet:

- `kbd` → User Input
- `samp` → System-/Computer-Output

Diese Elemente können verschachtelt werden, um die Beziehung zwischen Benutzereingabe und angezeigtem beziehungsweise zurückgegebenem Systeminhalt präzise darzustellen.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 20. Detailprüfung: `kbd`

## WHATWG

**Abschnitt:** §4.5.18 The `kbd` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`kbd` repräsentiert **User Input**.

Der typische Anwendungsfall ist Tastatureingabe, aber das Konzept ist nicht ausschließlich auf Tastaturereignisse beschränkt.

Auch andere Eingabeformen können repräsentiert werden.

## Verschachtelung mit `samp`

Wenn `kbd` innerhalb von `samp` verschachtelt ist, repräsentiert es Benutzereingabe so, wie sie vom System wiedergegeben wurde.

## Verschachtelung mit `samp` als Kind

Wenn `kbd` ein `samp` enthält, kann damit eine Eingabe repräsentiert werden, die auf einer vom System angezeigten Ausgabe basiert, beispielsweise die Auswahl eines Menüeintrags.

## Verschachteltes `kbd`

Wenn `kbd` innerhalb eines weiteren `kbd`-Elements liegt, kann das innere Element eine einzelne Taste beziehungsweise eine einzelne Eingabeeinheit darstellen.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 21. Detailprüfung: `sub` und `sup`

## WHATWG

**Abschnitt:** §4.5.19 The `sub` and `sup` elements

Die WHATWG definiert beide Elemente gemeinsam.

---

## `sub`

### Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

### Context

Wo Phrasing Content erwartet wird.

### Content Model

Phrasing Content.

### Tag Omission

Keine Auslassung.

### Content Attributes

Nur Global Attributes.

### Semantik

`sub` repräsentiert einen **Subscript**.

Es kann beispielsweise verwendet werden für:

- chemische Formeln
- tiefgestellte Bestandteile von Variablen
- typografische Konventionen

### Mathematik

Die WHATWG empfiehlt für mathematische Ausdrücke grundsätzlich MathML, erlaubt aber die Verwendung von `sub`, wenn keine detaillierte mathematische Markupstruktur benötigt wird.

---

## `sup`

### Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

### Context

Wo Phrasing Content erwartet wird.

### Content Model

Phrasing Content.

### Tag Omission

Keine Auslassung.

### Content Attributes

Nur Global Attributes.

### Semantik

`sup` repräsentiert einen **Superscript**.

Beispiele umfassen:

- Hochzahlen
- Exponenten
- typografische Abkürzungen
- andere in der Spezifikation beschriebene Hochstellungen

Auch hier wird für komplexere Mathematik MathML empfohlen.

## Sanitization

Für beide Elemente: Default.

## DOM Interface

Für beide: `HTMLElement`.

---

# 22. Detailprüfung: `i`

## WHATWG

**Abschnitt:** §4.5.20 The `i` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`i` repräsentiert einen Textabschnitt in:

- einer alternativen Stimme oder Stimmung
- einer vom normalen Prosatext abgesetzten Qualität
- einer taxonomischen Bezeichnung
- einem technischen Begriff
- einer idiomatischen Wendung aus einer anderen Sprache
- einer Transliteration
- einem Gedanken
- einem Schiffsnamen in westlichen Texten

## Sprache

Bei Begriffen in einer anderen Sprache als der Hauptsprache soll `lang` verwendet werden.

## Abgrenzung

`i` bedeutet nicht „kursiv“.

Die visuelle Darstellung ist nicht durch die semantische Definition garantiert.

Für andere Bedeutungen sind insbesondere zu prüfen:

- `em` für Stress Emphasis
- `dfn` für die definierende Instanz
- `b` für utilitaristische Aufmerksamkeit
- andere spezifischere Elemente

## `class`

`class` kann genutzt werden, um den Grund für die Verwendung von `i` zu kennzeichnen.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 23. Detailprüfung: `b`

## WHATWG

**Abschnitt:** §4.5.21 The `b` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`b` repräsentiert einen Textabschnitt, auf den aus **utilitaristischen Gründen Aufmerksamkeit gelenkt** wird, ohne zusätzliche Wichtigkeit oder eine alternative Stimme/Stimmung auszudrücken.

Beispiele:

- Schlüsselwörter in einer Zusammenfassung
- Produktnamen in einer Rezension
- handlungsrelevante Wörter in textbasierten interaktiven Anwendungen
- Lead-/Lede-Text eines Artikels

## Abgrenzung

`b` ist kein generisches „bold“-Element.

Insbesondere:

- Überschriften → `h1`–`h6`
- Stress Emphasis → `em`
- Importance → `strong`
- Highlighting → `mark`

## Letztes Mittel

Die WHATWG empfiehlt, `b` als letztes Mittel einzusetzen, wenn kein semantisch passenderes Element vorhanden ist.

## Darstellung

Die Spezifikation definiert keine zwingende Fettdarstellung.

Stylesheets können die Darstellung verändern.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 24. Detailprüfung: `u`

## WHATWG

**Abschnitt:** §4.5.22 The `u` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`u` repräsentiert einen Textabschnitt mit einer **nicht artikulierten, aber ausdrücklich dargestellten nichttextuellen Annotation**.

Die WHATWG nennt unter anderem:

- Kennzeichnung eines Eigennamens in chinesischer Typografie
- Kennzeichnung eines falsch geschriebenen Wortes

## Abgrenzung

Je nach Kontext können andere Elemente geeigneter sein:

- `em` → Stress Emphasis
- `b` oder `mark` → Aufmerksamkeit beziehungsweise Hervorhebung
- `cite` → Werktitel
- `ruby` → explizite Textannotation
- `i` → technische Begriffe, Taxonomie, Transliteration, Gedanken, Schiffsnamen

## Visuelle Mehrdeutigkeit

Die Standardsichtbarkeit von `u` kann mit der konventionellen Darstellung von Hyperlinks kollidieren.

Deshalb empfiehlt die WHATWG, `u` dort zu vermeiden, wo die Darstellung mit einem Hyperlink verwechselt werden könnte.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 25. Detailprüfung: `mark`

## WHATWG

**Abschnitt:** §4.5.23 The `mark` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`mark` repräsentiert einen Textabschnitt, der für Referenzzwecke markiert oder hervorgehoben wurde, weil er in einem anderen Kontext relevant ist.

## Zitatkontext

Innerhalb eines Zitats oder eines anderen referenzierten Textblocks kann `mark` anzeigen, dass die Hervorhebung nicht ursprünglich vom Autor des zitierten Textes stammt, sondern nachträglich zur Aufmerksamkeit auf eine relevante Stelle hinzugefügt wurde.

## Haupttext

Im Haupttext kann `mark` einen Abschnitt markieren, der aufgrund seiner Relevanz für die aktuelle Aktivität des Benutzers hervorgehoben wird.

Ein typischer Fall ist die Hervorhebung von Suchtreffern.

## Abgrenzung zu `strong`

- `strong` → Wichtigkeit
- `mark` → Relevanz beziehungsweise Hervorhebung in einem anderen Kontext

Die beiden Semantiken sind nicht austauschbar.

## Abgrenzung zu `u`

Wenn eine Markierung eine explizite Annotation wie eine Rechtschreibmarkierung darstellt, kann `u` geeigneter sein.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 26. Detailprüfung: `bdi`

## WHATWG

**Abschnitt:** §4.5.24 The `bdi` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Global Attributes.

`dir` besitzt auf `bdi` besondere Semantik.

## Semantik

`bdi` repräsentiert einen Textabschnitt, der für die Zwecke der bidirektionalen Textformatierung von seiner Umgebung **isoliert** werden soll.

Das Element ist insbesondere nützlich bei Inhalten unbekannter oder variabler Schreibrichtung, beispielsweise:

- Benutzernamen
- nutzergenerierte Inhalte
- gemischte Schreibsysteme

## `dir`-Default

Bei `bdi` verhält sich `dir` besonders:

Der Default ist `auto`.

Anders als bei vielen anderen Elementen wird die Richtung nicht einfach vom Elternelement geerbt.

Die Richtung wird aus dem Inhalt beziehungsweise der Auto-Directionality bestimmt.

## Rendering

Die WHATWG definiert für `bdi` zusätzliche Rendering-Anforderungen im Zusammenhang mit dem bidirektionalen Algorithmus.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 27. Detailprüfung: `bdo`

## WHATWG

**Abschnitt:** §4.5.25 The `bdo` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Global Attributes.

`dir` besitzt besondere Semantik.

## Semantik

`bdo` repräsentiert einen Textabschnitt, dessen **bidirektionale Textformatierung ausdrücklich gesteuert** wird.

Im Unterschied zu `bdi` geht es nicht um Isolation eines unbekannten Inhalts, sondern um die explizite Richtung des Textes.

## `dir`

Für `bdo` ist `dir` für die Festlegung der Text-Richtung maßgeblich.

Die WHATWG behandelt `bdo` zusammen mit den bidirektionalen Rendering-Regeln.

## Rendering

Die Definition enthält Anforderungen im Zusammenhang mit dem Unicode Bidirectional Algorithm.

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 28. Detailprüfung: `span`

## WHATWG

**Abschnitt:** §4.5.26 The `span` element

## Content Categories

- Flow Content
- Phrasing Content
- Palpable Content

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Phrasing Content.

## Tag Omission

Keine Auslassung.

## Content Attributes

Nur Global Attributes.

## Semantik

`span` besitzt **keine eigene Bedeutung**.

Es repräsentiert seine Kinder.

Sein Nutzen entsteht insbesondere durch Kombination mit Global Attributes wie:

- `class`
- `lang`
- `dir`
- `id`
- weiteren Global Attributes

## Typische Verwendung

`span` kann als semantisch neutrales oder technisch unterstützendes Inline-Element eingesetzt werden.

Die WHATWG nennt beispielsweise die Kombination mit `class` zur Kennzeichnung von:

- Schlüsselwörtern
- Identifiern
- Typen
- anderen Teilen eines Codefragments

Die konkrete Bedeutung der `class`-Werte stammt dabei nicht aus der `span`-Definition.

## Abgrenzung

`span` ist kein Ersatz für vorhandene semantische Elemente.

Wenn eine spezifische HTML-Semantik existiert, ist das spezifische Element grundsätzlich vorzuziehen.

## Sanitization

Default.

## DOM Interface

`HTMLSpanElement`.

---

# 29. Detailprüfung: `br`

## WHATWG

**Abschnitt:** §4.5.27 The `br` element

## Content Categories

- Flow Content
- Phrasing Content

`br` ist nicht als Palpable Content angegeben.

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Nothing.

Das Element ist ein Void Element.

## Tag Omission

Es gibt keinen Endtag.

## Content Attributes

Nur Global Attributes.

## Semantik

`br` repräsentiert einen **Zeilenumbruch**.

## Inhaltliche Zeilenumbrüche

`br` darf nur für Zeilenumbrüche verwendet werden, die tatsächlich Teil des Inhalts sind.

Die WHATWG nennt als typische Beispiele:

- Gedichte
- Adressen

## Kein Layout-Ersatz

`br` darf nicht als allgemeines Layoutwerkzeug verwendet werden.

Insbesondere darf es nicht eingesetzt werden, um thematische Gruppen innerhalb eines Absatzes voneinander zu trennen.

Für solche Strukturen sind geeignete HTML-Elemente zu verwenden.

## Einzelnes `br` in einem Absatz

Wenn ein Absatz ausschließlich aus einem einzelnen `br` besteht, repräsentiert er eine Platzhalter-Leerzeile, beispielsweise innerhalb eines Templates.

Solche Leerzeilen dürfen nicht ausschließlich für Präsentationszwecke verwendet werden.

## Textinhalt

In einem `br` kann kein sinnvoller Inhalt enthalten sein.

Inhalte innerhalb von `br`-Elementen dürfen nicht als Teil des umgebenden Textes betrachtet werden.

## Bidirektionale Darstellung

Die WHATWG definiert zusätzliche Rendering-Anforderungen für `br` im Zusammenhang mit dem bidirektionalen Algorithmus.

## Sanitization

Default.

## DOM Interface

`HTMLBRElement`.

Die WHATWG-Definition weist außerdem auf obsolete Members des Interfaces hin. Diese gehören nicht zur normalen aktuellen Elementfunktion und werden nicht als aktuelle Content Attributes inventarisiert.

---

# 30. Detailprüfung: `wbr`

## WHATWG

**Abschnitt:** §4.5.28 The `wbr` element

## Content Categories

- Flow Content
- Phrasing Content

`wbr` ist nicht als Palpable Content angegeben.

## Context

Wo Phrasing Content erwartet wird.

## Content Model

Nothing.

Das Element ist ein Void Element.

## Tag Omission

Es gibt keinen Endtag.

## Content Attributes

Nur Global Attributes.

## Semantik

`wbr` repräsentiert eine **Möglichkeit für einen Zeilenumbruch**.

Es signalisiert damit eine Stelle, an der ein User Agent den Text bei Bedarf umbrechen kann.

## Unterschied zu `br`

- `br` → tatsächlicher inhaltlicher Zeilenumbruch
- `wbr` → mögliche Umbruchstelle

`wbr` erzwingt keinen Zeilenumbruch.

## Typische Verwendung

Die WHATWG zeigt insbesondere lange Zeichenfolgen beziehungsweise Wörter, die ohne mögliche Umbruchstelle schlecht umbrechbar wären.

Beispiel:

```html
www.simply<wbr>orange<wbr>juice.com
```

## Sanitization

Default.

## DOM Interface

`HTMLElement`.

---

# 31. Gemeinsame Merkmale

## 31.1 Phrasing Content

Der überwiegende Teil der Elemente in §4.5 ist Phrasing Content.

Das betrifft insbesondere:

- `a`
- `em`
- `strong`
- `small`
- `s`
- `cite`
- `q`
- `dfn`
- `abbr`
- `ruby`
- `data`
- `time`
- `code`
- `var`
- `samp`
- `kbd`
- `sub`
- `sup`
- `i`
- `b`
- `u`
- `mark`
- `bdi`
- `bdo`
- `span`

`rt` ist dagegen nicht selbst als Content Category eingestuft, obwohl sein Content Model Phrasing Content ist.

`rp` besitzt ebenfalls keine Content Category und hat als Content Model Text.

`br` und `wbr` sind Flow + Phrasing, aber nicht Palpable.

## 31.2 Palpable Content

Die meisten eigenständigen textsemantischen Elemente sind zusätzlich Palpable Content.

Ausnahmen beziehungsweise Besonderheiten sind insbesondere:

- `rt`
- `rp`
- `br`
- `wbr`

Diese dürfen daher nicht einfach aus der allgemeinen Kategorie „Text-level semantics“ heraus als identisch klassifiziert werden.

---

# 32. Content Models

## Standardfall

Bei vielen Elementen lautet das Content Model:

> Phrasing Content.

Dazu gehören beispielsweise:

- `em`
- `strong`
- `small`
- `s`
- `cite`
- `q`
- `code`
- `var`
- `samp`
- `kbd`
- `sub`
- `sup`
- `i`
- `b`
- `u`
- `mark`
- `bdi`
- `bdo`
- `span`

## Besondere Modelle

### `a`

Transparent, jedoch mit zusätzlichen Einschränkungen hinsichtlich:

- Interactive Content
- verschachtelter `a`-Elemente
- `tabindex`

### `abbr`

Phrasing Content, aber ohne `dfn`-Nachfahren.

### `ruby`

Spezialmodell gemäß Prosa.

### `rt`

Phrasing Content.

### `rp`

Text.

### `data`

Phrasing Content.

### `time`

Mit `datetime`:

- Phrasing Content

Ohne `datetime`:

- Text mit zusätzlichen syntaktischen Anforderungen.

### `br`

Nothing.

### `wbr`

Nothing.

---

# 33. Tag-Omission

## Keine auslassbaren Tags

Bei folgenden Elementen sind weder Start- noch Endtag auslassbar:

- `a`
- `em`
- `strong`
- `small`
- `s`
- `cite`
- `q`
- `dfn`
- `abbr`
- `ruby`
- `data`
- `time`
- `code`
- `var`
- `samp`
- `kbd`
- `sub`
- `sup`
- `i`
- `b`
- `u`
- `mark`
- `bdi`
- `bdo`
- `span`

## `rt`

Der Endtag darf unter den von der WHATWG genannten Nachfolgebedingungen ausgelassen werden.

## `rp`

Der Endtag darf unter den von der WHATWG genannten Nachfolgebedingungen ausgelassen werden.

## Void Elements

`br` und `wbr` besitzen keinen Endtag.

---

# 34. Elementbezogene Attribute

Die folgenden Elemente besitzen im recherchierten §4.5 zusätzliche elementbezogene Content Attributes:

| Element | zusätzliches Attribut | Funktion |
|---|---|---|
| `a` | `href` | Adresse des Hyperlinks |
| `a` | `target` | Ziel-Navigable |
| `a` | `download` | Downloadverhalten |
| `a` | `ping` | Ping-URLs |
| `a` | `rel` | Beziehung zur Zielressource |
| `a` | `hreflang` | Sprache der Zielressource |
| `a` | `type` | Hinweis auf Ressourcentyp |
| `a` | `referrerpolicy` | Referrer Policy |
| `q` | `cite` | Quelle des Zitats |
| `abbr` | `title` | Expansion der Abkürzung; spezielle Semantik |
| `data` | `value` | Maschinenlesbarer Wert |
| `time` | `datetime` | Maschinenlesbarer Datums-/Zeitwert |

Alle übrigen in diesem Themenblock definierten Elemente besitzen in ihrer Elementdefinition ausschließlich Global Attributes.

Dabei ist wichtig:

**Global Attributes sind keine elementbezogenen Content Attributes.**

Die Auflistung der Global Attributes gehört in die separate Attribut-Ebene der ZE-WebLab-Referenz.

---

# 35. Sanitization

Die WHATWG-Elementdefinitionen enthalten für die Elemente in §4.5 jeweils Sanitization-Angaben.

## Default

Für nahezu alle Elemente dieses Abschnitts gilt:

> Sanitization: Default.

Dies betrifft insbesondere:

- `em`
- `strong`
- `small`
- `s`
- `cite`
- `q`
- `dfn`
- `abbr`
- `ruby`
- `rt`
- `rp`
- `code`
- `var`
- `samp`
- `kbd`
- `sub`
- `sup`
- `i`
- `b`
- `u`
- `mark`
- `bdi`
- `bdo`
- `span`
- `br`
- `wbr`

## Sonderfälle

### `a`

Die Definition nennt Default-Sanitization mit:

- `href`
- `hreflang`
- `type`

und `href` als navigating URL attribute.

### `data`

Default-Sanitization mit `value`.

### `time`

Default-Sanitization mit `datetime`.

Damit sind die URL-/Datenwert-bezogenen Attribute nicht mit den übrigen Global Attributes gleichzusetzen.

---

# 36. DOM Interfaces

## Spezifische Interfaces

### `a`

```text
HTMLAnchorElement
```

### `q`

```text
HTMLQuoteElement
```

### `data`

```text
HTMLDataElement
```

### `time`

```text
HTMLTimeElement
```

### `span`

```text
HTMLSpanElement
```

### `br`

```text
HTMLBRElement
```

## `HTMLElement`

Die folgenden Elemente verwenden das allgemeine `HTMLElement`-Interface:

- `em`
- `strong`
- `small`
- `s`
- `cite`
- `dfn`
- `abbr`
- `ruby`
- `rt`
- `rp`
- `code`
- `var`
- `samp`
- `kbd`
- `sub`
- `sup`
- `i`
- `b`
- `u`
- `mark`
- `bdi`
- `bdo`
- `wbr`

## Keine falsche Interface-Zählung

Die speziellen DOM Interfaces stellen keine zusätzlichen HTML-Elemente dar.

Sie sind API-/DOM-Ebene und deshalb von der Elementinventarliste getrennt zu halten.

---

# 37. Normative Sonderregeln

## 37.1 `a` ohne `href`

Ein `a` ohne `href` ist kein Hyperlink.

Es repräsentiert einen Platzhalter.

Die für Hyperlinks relevanten Attribute müssen in diesem Fall weggelassen werden.

## 37.2 `a` und interaktiver Inhalt

Das transparente Content Model von `a` wird durch die Regel eingeschränkt, dass kein Interactive Content, kein weiteres `a` und kein Nachfahre mit `tabindex` enthalten sein darf.

## 37.3 `em` und Stresshierarchie

Verschachtelte `em`-Elemente erhöhen die Ebene der Stress Emphasis.

## 37.4 `s` ist nicht `del`

` s` kennzeichnet nicht mehr korrekten beziehungsweise nicht mehr relevanten Inhalt.

Dokumentänderungen werden durch `del` aus §4.7 modelliert.

## 37.5 `q` und Anführungszeichen

Quotation Punctuation für den Inhalt von `q` wird nicht als normaler Text innerhalb des Elements eingefügt.

## 37.6 `cite` und Personennamen

`cite` ist für Werktitel vorgesehen, nicht für Personennamen.

## 37.7 `abbr` und `title`

Wenn `title` bei `abbr` verwendet wird, muss es die Expansion der Abkürzung enthalten und darf keine zusätzlichen Informationen enthalten.

## 37.8 `ruby`

Das Ruby-Modell ist strukturell und nicht durch eine einfache Regel „Text + `rt`“ erschöpfend beschrieben.

## 37.9 `rt`

`rt` ist als Annotationselement auf das Ruby-Modell bezogen.

Außerhalb eines `ruby`-Elements besitzt es eine andere, durch die Spezifikation definierte Repräsentation.

## 37.10 `rp`

`rp` dient als Fallback-Markup für User Agents ohne Ruby-Unterstützung.

Innerhalb von `ruby` repräsentiert es selbst nichts.

## 37.11 `data`

`value` ist verpflichtend.

Der Wert muss eine maschinenlesbare Repräsentation des sichtbaren Inhalts darstellen.

## 37.12 `time`

Ohne `datetime` darf `time` keine Element-Nachfahren besitzen.

Der Text muss dann selbst eine zulässige Datums-/Zeitdarstellung bilden.

## 37.13 `b`

`b` darf nicht als allgemeines Ersatzmittel für `strong`, `em`, `mark` oder Überschriften verwendet werden.

## 37.14 `i`

`i` ist nicht semantisch gleichbedeutend mit „kursiv“.

## 37.15 `u`

`u` ist nicht das HTML-Element für Hyperlink-Darstellung.

## 37.16 `bdi`

`bdi` isoliert bidirektionalen Text von seiner Umgebung.

`dir` besitzt auf `bdi` besondere Auto-Semantik.

## 37.17 `bdo`

`bdo` wird zur expliziten Steuerung der bidirektionalen Textformatierung verwendet.

## 37.18 `br`

`br` ist ausschließlich für inhaltliche Zeilenumbrüche vorgesehen.

Es ist kein generisches CSS-/Layout-Element.

## 37.19 `wbr`

`wbr` bietet nur eine mögliche Umbruchstelle.

Es entspricht nicht `br`.

---

# 38. Accessibility

## WHATWG-Ebene

Die Elementdefinitionen enthalten jeweils einen Abschnitt:

> Accessibility considerations

Die WHATWG verweist dort für Autoren und Implementierer auf einschlägige externe Accessibility-Regeln.

Für die HTML-Referenz bedeutet das:

- Accessibility ist Bestandteil der Elementprüfung.
- Die vollständige Accessibility-Semantik wird aber nicht allein aus der HTML-Elementdefinition abgeleitet.
- ARIA-Rollen und States/Properties gehören in eine separate Accessibility-Ebene.

## Autorensicht

Die WHATWG verweist auf Anforderungen für Autoren, insbesondere hinsichtlich:

- sinnvoller Verwendung semantischer Elemente
- Vermeidung ungeeigneter Ersatzkonstruktionen
- korrekter Bedeutung von Textsemantik

## Implementierungssicht

Für Implementierer verweist WHATWG auf HTML Accessibility API Mappings.

Die konkrete Plattformabbildung wird daher nicht als Bestandteil dieser Datei erfunden.

## Besonders relevante Accessibility-Themen in §4.5

Folgende Elemente besitzen semantisch relevante Eigenschaften, die bei einer späteren Accessibility-Vertiefung besonders berücksichtigt werden sollten:

- `a`
- `em`
- `strong`
- `abbr`
- `q`
- `ruby`
- `rt`
- `time`
- `bdi`
- `bdo`
- `br`

Die bloße CSS-Darstellung darf dabei nicht mit der HTML-Semantik gleichgesetzt werden.

---

# 39. Bidirektionaler Text

§4.5 enthält mehrere Elemente, die unmittelbar mit bidirektionalem Text zusammenhängen.

## `bdi`

Isolation eines Textabschnitts von seiner Umgebung.

Besonders wichtig für:

- unbekannte Benutzereingaben
- Benutzernamen
- gemischte Schreibrichtungen

## `bdo`

Explizite bidirektionale Formatierung.

## `br`

Die WHATWG definiert auch Rendering-Anforderungen für `br` im Zusammenhang mit dem bidirektionalen Algorithmus.

## `dir`

`dir` ist ein Global Attribute und wird deshalb nicht als eigenständiges Elementinventar geführt.

Für `bdi` und `bdo` besitzt `dir` jedoch elementbezogene Sondersemantik.

---

# 40. Machine-readable content

Mehrere Elemente aus §4.5 kombinieren menschenlesbaren Inhalt mit maschinenlesbarer Information.

## `data`

```html
<data value="...">sichtbarer Inhalt</data>
```

`value` stellt die maschinenlesbare Repräsentation bereit.

## `time`

```html
<time datetime="...">sichtbarer Datums-/Zeittext</time>
```

`datetime` stellt die maschinenlesbare Datums-/Zeitrepräsentation bereit.

## Abgrenzung

`data` ist das allgemeinere Element für maschinenlesbare Werte.

`time` ist das spezialisierte Element für Datums-/Zeitinformationen.

---

# 41. Textsemantik und Darstellung

Ein zentraler Punkt des Abschnitts ist die Trennung zwischen:

1. semantischer Bedeutung
2. visueller Darstellung

Insbesondere darf nicht aus der üblichen Browserdarstellung geschlossen werden, dass dies die normative Bedeutung eines Elements sei.

Beispiele:

| Element | Semantik | Nicht bloß |
|---|---|---|
| `em` | Stress Emphasis | kursiv |
| `strong` | Importance | fett |
| `i` | alternative voice/mood bzw. abgesetzte Textqualität | kursiv |
| `b` | Aufmerksamkeit für utilitaristische Zwecke | fett |
| `u` | unartikulierte explizite Annotation | Unterstreichung |
| `mark` | relevante Hervorhebung | gelber Hintergrund |
| `s` | nicht mehr korrekt/relevant | Durchstreichung |
| `cite` | Werktitel | kursiver Titel |
| `small` | Side Comment | kleine Schrift |

Die CSS-Darstellung kann abweichend gestaltet werden.

---

# 42. Abgrenzung der Computertext-Elemente

§4.5 enthält mehrere Elemente, die im Kontext von Software, Computern und technischen Texten verwendet werden.

## `code`

Computer Code.

## `var`

Variable.

## `samp`

Computer-/Systemausgabe.

## `kbd`

Benutzereingabe.

Diese vier Elemente haben unterschiedliche Semantiken und sollten nicht allein aufgrund einer gemeinsamen visuellen Darstellung als austauschbar betrachtet werden.

---

# 43. Abgrenzung der Hervorhebungselemente

## `em`

Stress Emphasis.

## `strong`

Importance.

## `b`

Aufmerksamkeit ohne zusätzliche Importance und ohne alternative Voice/Mood.

## `mark`

Relevanz beziehungsweise Hervorhebung in einem anderen Kontext.

## `u`

Explizite, nicht artikulierte Annotation.

## `s`

Nicht mehr korrekter beziehungsweise nicht mehr relevanter Inhalt.

Diese sechs Elemente erfüllen unterschiedliche semantische Funktionen.

---

# 44. Ruby-Unterfamilie

Die Elemente

- `ruby`
- `rt`
- `rp`

bilden innerhalb von §4.5 eine zusammenhängende Feature-Familie.

## Rollen

### `ruby`

Container und semantische Repräsentation der Ruby-Struktur.

### `rt`

Ruby-Annotation.

### `rp`

Fallback-Markup für nicht Ruby-fähige User Agents.

## Inventarregel

Alle drei sind eigenständige HTML-Elemente und deshalb im Elementinventar enthalten.

Die zugrunde liegende Ruby-Segment- und Annotation-Logik ist jedoch ein Unterkonzept der Ruby-Verarbeitung und kein weiteres Elementinventar.

---

# 45. Querverweise

## §4.4 Grouping Content

Text-level semantics werden häufig innerhalb von Grouping-Content-Elementen verwendet.

Insbesondere relevant:

- `p`
- `pre`
- `blockquote`
- `li`
- `dt`
- `dd`

Die Elemente aus §4.5 bleiben dabei eigenständige Text-level-Semantics-Features.

## §4.6 Links

`a` besitzt eine direkte Beziehung zum Link-Konzept aus §4.6.

Die vollständige Hyperlink-Verarbeitung gehört jedoch in:

`docs/html/06-links.md`

Diese Datei wiederholt deshalb nicht die komplette Link-API- und Processing-Model-Dokumentation.

## §4.7 Edits

`del` und `ins` gehören zum folgenden Themenblock Edits.

Besonders relevant ist die normative Abgrenzung:

- `s` → nicht mehr korrekt/relevant
- `del` → dokumentierte Entfernung/Änderung

## Forms

`kbd` kann in Dokumentation von Benutzereingaben relevant sein, ist aber kein Form-Control.

## MathML

`sub`, `sup` und `var` können bei mathematischen Inhalten verwendet werden.

Für komplexe mathematische Ausdrücke verweist WHATWG auf MathML.

## SVG / MathML Integration

Die genannten HTML-Elemente bleiben HTML-Elemente.

Die Integration fremder Vokabulare wird separat dokumentiert.

---

# 46. `span` als semantisch neutrales Element

`span` ist innerhalb dieses Themenblocks besonders wichtig, weil es kein eigenes Vokabularsemantik-Label besitzt.

Die Definition lautet sinngemäß:

- `span` bedeutet für sich selbst nichts
- es repräsentiert seine Kinder
- seine Funktion entsteht typischerweise durch Global Attributes

Typische Attribute:

- `class`
- `id`
- `lang`
- `dir`
- `title`
- `data-*`

Die konkreten Bedeutungen von Klassen, IDs und Data Attributes gehören nicht zur `span`-Definition.

---

# 47. `a` als Sonderfall des transparenten Content Models

`a` unterscheidet sich strukturell stark von den meisten anderen Elementen dieses Abschnitts.

Die meisten Text-level-Elemente besitzen:

> Phrasing Content

als Content Model.

`a` besitzt dagegen:

> Transparent

mit zusätzlichen Verboten.

Das erlaubt beispielsweise, einen größeren Abschnitt innerhalb eines Links zu kapseln, sofern keine verbotenen interaktiven Nachfahren vorhanden sind.

Damit kann `a` auch Inhaltsstrukturen umfassen, die über reinen Inline-Text hinausgehen.

---

# 48. Status / V1

## WHATWG-Definition

Alle in diesem Dokument inventarisierten Elemente sind im recherchierten WHATWG HTML Living Standard definiert.

Damit ist für die Elementebene festzustellen:

**WHATWG-Status: definiert.**

## Konforme Verwendung

„Definiert“ bedeutet nicht automatisch:

> Jede denkbare Verwendung ist konform.

Die Konformität hängt jeweils von:

- Context
- Content Model
- Content Attributes
- zusätzlichen normativen Regeln
- gegebenenfalls Attributzuständen
- weiteren Querverweisen

ab.

Beispiele:

- `a` ohne `href` ist weiterhin ein definiertes Element, aber kein Hyperlink.
- `a` darf keine verbotenen interaktiven Nachfahren enthalten.
- `abbr[title]` muss die spezifischen `title`-Regeln beachten.
- `data` benötigt `value`.
- `time` besitzt unterschiedliche Regeln mit und ohne `datetime`.
- `br` darf nicht als allgemeines Layoutwerkzeug missbraucht werden.

## Browser-Support

Browser-Support ist kein Bestandteil dieses WHATWG-Statusfeldes.

Die WHATWG-Seite enthält zwar eingeblendete MDN-Kompatibilitätsinformationen, diese werden hier nicht als Status übernommen.

## V1-Einordnung

Für die ZE-WebLab-V1-Referenz:

| Ebene | Status |
|---|---|
| HTML-Elemente | WHATWG-definiert |
| Content Categories | aus WHATWG geprüft |
| Context | aus WHATWG geprüft |
| Content Model | aus WHATWG geprüft |
| Tag Omission | aus WHATWG geprüft |
| Elementbezogene Attribute | aus WHATWG geprüft |
| Sanitization | aus WHATWG geprüft |
| DOM Interface | aus WHATWG geprüft |
| Accessibility | WHATWG-Verweise geprüft; Detailmapping separat |
| Browser-Kompatibilität | nicht Bestandteil des WHATWG-Status |
| Global Attributes | separate Referenzfamilie |
| Link Types | separate Referenzfamilie |
| APIs | separate Ebene |

---

# 49. Offene Punkte

Nach der Prüfung von §4.5 bestehen keine offenen Punkte hinsichtlich des grundlegenden Elementinventars.

Für die Gesamtprojektstruktur bleiben jedoch bewusst separate Rechercheebenen bestehen.

## Accessibility-Vertiefung

Die Elementdefinitionen verweisen auf externe Accessibility-Spezifikationen.

Eine vollständige Dokumentation von:

- ARIA Roles
- States
- Properties
- Accessibility Tree
- Plattform-API-Mappings

ist deshalb nicht Bestandteil dieser Datei.

## Browser-Kompatibilität

Nicht Bestandteil dieser WHATWG-Referenz.

Eine spätere Browser-Kompatibilitätsrecherche ist separat durchzuführen.

## Global Attributes

Global Attributes werden nicht pro Element vollständig dupliziert.

Sie werden in der dafür vorgesehenen separaten Attribut-Ebene inventarisiert.

## Link Types

Die Link Types von `a` gehören zur separaten Link-Feature-Familie.

## Datums-/Zeit-Syntaxen

`time` verweist auf zahlreiche normative Datums-/Zeit-Stringdefinitionen.

Diese werden hier nicht als eigene HTML-Elemente oder Attribute gezählt.

## Ruby Processing

Das Ruby-Segmentmodell ist ein Unterkonzept der `ruby`-Definition und kein zusätzliches Elementinventar.

---

# 50. Usage Summary

Der WHATWG-Abschnitt §4.5.29 ist ausdrücklich **nichtnormativ**.

Die Übersicht ordnet die Elemente nach ihrem hauptsächlichen Zweck.

| Element | Hauptzweck |
|---|---|
| `a` | Hyperlinks |
| `em` | Stress Emphasis |
| `strong` | Importance |
| `small` | Side Comments |
| `s` | Inaccurate / no longer relevant text |
| `cite` | Titles of works |
| `q` | Quotations |
| `dfn` | Defining instance |
| `abbr` | Abbreviations |
| `ruby` / `rt` / `rp` | Ruby annotations |
| `data` | Machine-readable equivalent |
| `time` | Machine-readable date/time equivalent |
| `code` | Computer code |
| `var` | Variables |
| `samp` | Computer output |
| `kbd` | User input |
| `sub` | Subscripts |
| `sup` | Superscripts |
| `i` | Alternative voice / offset text |
| `b` | Keywords / attention for utilitarian purposes |
| `u` | Annotations |
| `mark` | Highlighting |
| `bdi` | Text directionality isolation |
| `bdo` | Text directionality formatting |
| `span` | Other / generic inline grouping |
| `br` | Line break |
| `wbr` | Line-breaking opportunity |

Diese Tabelle ist eine zusammenfassende Zweckübersicht und ersetzt nicht die normativen Elementdefinitionen.

---

# 51. QS-Prüfung

## Elementinventar

- [x] `a`
- [x] `em`
- [x] `strong`
- [x] `small`
- [x] `s`
- [x] `cite`
- [x] `q`
- [x] `dfn`
- [x] `abbr`
- [x] `ruby`
- [x] `rt`
- [x] `rp`
- [x] `data`
- [x] `time`
- [x] `code`
- [x] `var`
- [x] `samp`
- [x] `kbd`
- [x] `sub`
- [x] `sup`
- [x] `i`
- [x] `b`
- [x] `u`
- [x] `mark`
- [x] `bdi`
- [x] `bdo`
- [x] `span`
- [x] `br`
- [x] `wbr`

## WHATWG-Unterabschnitte

- [x] §4.5.1 `a`
- [x] §4.5.2 `em`
- [x] §4.5.3 `strong`
- [x] §4.5.4 `small`
- [x] §4.5.5 `s`
- [x] §4.5.6 `cite`
- [x] §4.5.7 `q`
- [x] §4.5.8 `dfn`
- [x] §4.5.9 `abbr`
- [x] §4.5.10 `ruby`
- [x] §4.5.11 `rt`
- [x] §4.5.12 `rp`
- [x] §4.5.13 `data`
- [x] §4.5.14 `time`
- [x] §4.5.15 `code`
- [x] §4.5.16 `var`
- [x] §4.5.17 `samp`
- [x] §4.5.18 `kbd`
- [x] §4.5.19 `sub` / `sup`
- [x] §4.5.20 `i`
- [x] §4.5.21 `b`
- [x] §4.5.22 `u`
- [x] §4.5.23 `mark`
- [x] §4.5.24 `bdi`
- [x] §4.5.25 `bdo`
- [x] §4.5.26 `span`
- [x] §4.5.27 `br`
- [x] §4.5.28 `wbr`
- [x] §4.5.29 Usage summary

## Fachliche Prüffelder

- [x] Content Categories
- [x] Contexts
- [x] Content Models
- [x] Tag Omission
- [x] Content Attributes
- [x] Global Attributes als separate Ebene berücksichtigt
- [x] Accessibility Considerations
- [x] Sanitization
- [x] DOM Interfaces
- [x] normative Sonderregeln
- [x] relevante Querverweise
- [x] Abgrenzung zu Browser-Support
- [x] Abgrenzung zu APIs
- [x] Abgrenzung zu externen Accessibility-Spezifikationen
- [x] Abgrenzung von Unterkonzepten zu Elementen

---

# 52. Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard**

Abschnitt:

**§4.5 Text-level semantics**

Recherchierte Unterabschnitte:

- §4.5.1 The `a` element
- §4.5.2 The `em` element
- §4.5.3 The `strong` element
- §4.5.4 The `small` element
- §4.5.5 The `s` element
- §4.5.6 The `cite` element
- §4.5.7 The `q` element
- §4.5.8 The `dfn` element
- §4.5.9 The `abbr` element
- §4.5.10 The `ruby` element
- §4.5.11 The `rt` element
- §4.5.12 The `rp` element
- §4.5.13 The `data` element
- §4.5.14 The `time` element
- §4.5.15 The `code` element
- §4.5.16 The `var` element
- §4.5.17 The `samp` element
- §4.5.18 The `kbd` element
- §4.5.19 The `sub` and `sup` elements
- §4.5.20 The `i` element
- §4.5.21 The `b` element
- §4.5.22 The `u` element
- §4.5.23 The `mark` element
- §4.5.24 The `bdi` element
- §4.5.25 The `bdo` element
- §4.5.26 The `span` element
- §4.5.27 The `br` element
- §4.5.28 The `wbr` element
- §4.5.29 Usage summary

**Spezifikationsstand der Recherche:** 11.08.2026.

## Ergänzende normative Querverweise

Für die in den Elementdefinitionen referenzierten Bereiche sind insbesondere relevant:

- WHATWG HTML – Global Attributes
- WHATWG HTML – Content Categories
- WHATWG HTML – Content Models
- WHATWG HTML – Sanitization
- WHATWG HTML – DOM Interfaces
- WHATWG HTML – Links
- WHATWG HTML – Edits
- WHATWG HTML – Bidirectional Text / `dir`
- WHATWG HTML – Datums- und Zeitwerte
- WHATWG HTML – Microdata
- WHATWG HTML – HTML/SVG/MathML Integration
- DOM Standard
- HTML Accessibility API Mappings
- ARIA in HTML
- MathML

Diese Querverweise werden nicht als zusätzliche Elemente des §4.5-Inventars gezählt.

---

# 53. Abschlussbewertung

Der WHATWG-Abschnitt §4.5 „Text-level semantics“ ist für ZE-WebLab als **abgeschlossen recherchiert** einzustufen.

Das Elementinventar wurde vollständig gegen die aktuelle Abschnittsstruktur geprüft.

Insbesondere wurden die folgenden Ebenen getrennt gehalten:

- HTML-Elemente
- Content Categories
- Contexts
- Content Models
- Tag Omission
- Content Attributes
- Global Attributes
- Accessibility
- Sanitization
- DOM Interfaces
- normative Sonderregeln
- Querverweise
- externe Accessibility-Spezifikationen
- Browser-Kompatibilität

Die Elemente `sub` und `sup` wurden als gemeinsame WHATWG-Definitionsfamilie dokumentiert.

`ruby`, `rt` und `rp` wurden als zusammengehörige Ruby-Featurefamilie dokumentiert, ohne das Ruby-Segmentmodell fälschlich als zusätzliche HTML-Elemente zu inventarisieren.

§4.5.29 wurde als nichtnormative Usage Summary behandelt und nicht als zusätzliches Element oder Feature interpretiert.

Damit ist `docs/html/05-text-level-semantics.md` für den aktuellen WHATWG-Recherchestand vollständig dokumentiert.