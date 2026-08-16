# ZE-WebLab – HTML-Referenz: HTML Sanitization

## Arbeitsstand / Quellenstand

- Rechercheebene: 2 – übergreifende HTML-Konzepte und Feature-Familien
- Feature-Familie: HTML Sanitization
- Feature-Typ: API / DOM-Verarbeitung / Processing Model / Security Feature
- Zieldatei: `docs/html/20-sanitization.md`
- Normative Primärquelle: WHATWG HTML Living Standard
- Maßgeblicher WHATWG-Bereich: §8.6 HTML sanitization
- Verwandter WHATWG-Bereich: §8.5 DOM parsing and serialization APIs
- WHATWG-Stand der Recherche: 11. August 2026
- Projektquelle: öffentliches ZE-WebLab-Repository
- Browser-Kompatibilität: nicht Bestandteil der normativen Statusbewertung
- V1-Status: projektspezifisch; nicht mit WHATWG-Status gleichzusetzen
- Prüfstatus: vollständig recherchiert für den abgegrenzten Sanitization-Bereich

### Quellenabgrenzung

Die WHATWG HTML Living Standard ist die normative Primärquelle für:

- Definition der HTML-Sanitization
- `Sanitizer`
- `SanitizerConfig`
- Sanitizer-Konfigurationen
- Safe- und Unsafe-Verarbeitung
- Sanitization-Algorithmen
- Sanitization-Kategorien
- Integration in HTML-Parsing
- Integration in DOM-Insertion-APIs
- Verarbeitung von Elementen
- Verarbeitung von Attributen
- Verarbeitung von Processing Instructions
- Behandlung von Kommentaren
- Behandlung von Custom Data Attributes
- Behandlung von `javascript:`-URLs
- Entfernung unsicherer Elemente und Attribute
- normative Sicherheitsregeln

Das ZE-WebLab-Repository ist die maßgebliche Quelle für die Feststellung, welche Aspekte bereits im Projekt dokumentiert sind.

Diese Datei behandelt keine vollständige allgemeine Security-Referenz des Webplattform-Stacks.

Insbesondere werden nicht automatisch sämtliche XSS-, CSP-, Trusted-Types-, DOM-Clobbering- oder Server-Side-Security-Konzepte zu Sanitization-Features erklärt.

### Abgrenzung zu anderen ZE-WebLab-Dateien

Die Sanitization-Systematik ist von folgenden Themen zu unterscheiden:

- `13-global-attributes.md` behandelt Global Attributes.
- `14-content-categories.md` behandelt Content Categories.
- `15-content-models.md` behandelt Content Models.
- `16-link-types.md` behandelt Link Types.
- `17-custom-elements.md` behandelt Custom Elements.
- `18-contexts.md` behandelt Contexts.
- `19-dom-interfaces-and-apis.md` behandelt die übergreifende DOM-/API-Ebene.
- `21-parsing.md` behandelt das allgemeine HTML-Parsing.
- `22-svg-mathml-integration.md` behandelt die HTML/SVG-/MathML-Integration.
- `23-microdata.md` behandelt Microdata.

Sanitization ist keine Elementliste und keine eigene Content Category.

---

## Einordnung

HTML Sanitization ist die normative Verarbeitung von HTML-Inhalten, bei der ein aus HTML erzeugter DOM-Baum anhand einer Sanitizer-Konfiguration gefiltert wird.

Die aktuelle WHATWG-Systematik stellt hierfür eine native Sanitizer-API bereit.

Das zentrale Objekt ist:

`Sanitizer`

Die Sanitizer-API ist insbesondere dafür vorgesehen, HTML-Strings in einen DOM-Baum zu überführen und diesen Baum anhand einer Konfiguration zu filtern.

Die WHATWG unterscheidet dabei ausdrücklich zwischen:

- sicheren Sanitization-Methoden
- unsicheren Sanitization-/Parsing-Methoden

Die sicheren Methoden sind darauf ausgelegt, keine Markup-Strukturen zu erzeugen, die Script-Ausführung ermöglichen.

Die Unsafe-Methoden besitzen dagegen keine entsprechende Sicherheitsgarantie durch einen eingebauten sicheren Basisschutz.

### Sanitization ist kein HTML-Element

`Sanitizer` ist:

- kein HTML-Element
- keine Content Category
- kein Content Model
- kein Link Type
- kein Custom Element
- kein natives HTML-Tag

`Sanitizer` ist ein DOM-/API-Konzept.

### Sanitization ist auch kein allgemeiner XSS-Status

Die WHATWG-Sanitization-Systematik enthält Sicherheitsregeln gegen bestimmte scriptfähige oder potentiell gefährliche HTML-Strukturen.

Daraus folgt nicht, dass jede Anwendungssicherheitsproblematik durch die Sanitizer API gelöst wird.

Die WHATWG behandelt ausdrücklich auch Grenzen der Sanitizer API, darunter:

- serverseitig reflektiertes oder gespeichertes XSS
- DOM Clobbering
- XSS durch Script Gadgets
- Mutation XSS

Diese Bereiche sind teilweise nicht-normative Security Considerations und dürfen nicht mit den normativen Sanitization-Regeln gleichgesetzt werden.

---

## WHATWG-Struktur

Der maßgebliche Bereich ist:

- §8.6 HTML sanitization

### Unterabschnitte

#### §8.6.1 Introduction

Nicht-normativer Einführungsteil.

Behandelt insbesondere:

- Zweck der HTML Sanitization
- Verarbeitung untrusted HTML
- DOM-basierte XSS-Risiken
- Safe und Unsafe APIs

#### §8.6.1.1 Safe and unsafe

Behandelt die grundsätzliche Unterscheidung zwischen:

- sicheren Methoden
- unsicheren Methoden

#### §8.6.2 The `Sanitizer` interface

Normativer API-Bereich für:

- `Sanitizer`
- Konstruktor
- Konfigurationsabfrage
- Allow-/Remove-Methoden
- Kommentarverarbeitung
- Data-Attribute-Verarbeitung
- `removeUnsafe()`

#### §8.6.3 Sanitizer configuration

Definiert:

- `SanitizerConfig`
- `SanitizerElementNamespace`
- `SanitizerElementNamespaceWithAttributes`
- `SanitizerAttributeNamespace`
- `SanitizerProcessingInstruction`
- zugehörige Typdefinitionen

#### §8.6.3.1 Configuration invariants

Nicht-normativer Erläuterungsbereich zu den Konfigurationsinvarianten.

Die eigentliche normative Gültigkeitsprüfung der Konfiguration wird durch die zugehörigen Algorithmen definiert.

#### §8.6.4 Sanitization algorithms

Definiert unter anderem:

- Setzen und Filtern von HTML
- Ermittlung des Sanitizers aus Optionen
- Sanitization eines Nodes
- innere Sanitization-Schritte
- `javascript:`-URL-Erkennung
- Entfernung von Elementen
- Entfernung von Attributen
- Entfernung unsicherer Inhalte
- Kanonisierung
- Konfigurationsvalidierung

#### §8.6.5 Sanitization constants

Definiert die Sanitization-Kategorien:

- `Default`
- `Unsafe`
- `Uncategorized`

Außerdem wird die eingebaute sichere Basiskonfiguration beschrieben.

#### §8.6.6 Security considerations

Nicht-normativer Sicherheitsbereich.

Unterabschnitte:

- §8.6.6.1 Server-side reflected and stored XSS
- §8.6.6.2 DOM clobbering
- §8.6.6.3 XSS with script gadgets
- §8.6.6.4 Mutation XSS

---

## Inventar

| ID | Feature | Feature-Typ | WHATWG-Bereich | Erste-Ebene-Abdeckung | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|
| SAN-001 | HTML Sanitization | Normatives Konzept | §8.6 | teilweise elementbezogen | vollständig relevant |
| SAN-002 | Safe Sanitization | Processing Model / API | §8.6.1.1, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-003 | Unsafe Sanitization | Processing Model / API | §8.6.1.1, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-004 | `Sanitizer` | DOM Interface / API | §8.6.2 | nicht vollständig | vollständig relevant |
| SAN-005 | `SanitizerConfig` | API-Dictionary | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-006 | `SanitizerElementNamespace` | API-Dictionary | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-007 | `SanitizerElementNamespaceWithAttributes` | API-Dictionary | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-008 | `SanitizerAttributeNamespace` | API-Dictionary | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-009 | `SanitizerProcessingInstruction` | API-Dictionary | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-010 | `SanitizerElement` | API-Typ | §8.6.3 | nicht vollständig | relevant |
| SAN-011 | `SanitizerElementWithAttributes` | API-Typ | §8.6.3 | nicht vollständig | relevant |
| SAN-012 | `SanitizerAttribute` | API-Typ | §8.6.3 | nicht vollständig | relevant |
| SAN-013 | `SanitizerPI` | API-Typ | §8.6.3 | nicht vollständig | relevant |
| SAN-014 | `elements` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-015 | `removeElements` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-016 | `replaceWithChildrenElements` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-017 | `processingInstructions` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | relevant |
| SAN-018 | `removeProcessingInstructions` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | relevant |
| SAN-019 | `attributes` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-020 | `removeAttributes` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-021 | `comments` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | relevant |
| SAN-022 | `dataAttributes` | Sanitizer-Konfiguration | §8.6.3 | nicht vollständig | vollständig relevant |
| SAN-023 | `Sanitizer.prototype.get()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-024 | `allowElement()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-025 | `removeElement()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-026 | `replaceElementWithChildren()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-027 | `allowProcessingInstruction()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-028 | `removeProcessingInstruction()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-029 | `allowAttribute()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-030 | `removeAttribute()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-031 | `setComments()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-032 | `setDataAttributes()` | API | §8.6.2 | nicht vollständig | relevant |
| SAN-033 | `removeUnsafe()` | API / Processing Model | §8.6.2, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-034 | `Element.setHTML()` | DOM API | §8.5.2, §8.6.4 | elementbezogen teilweise | vollständig relevant |
| SAN-035 | `ShadowRoot.setHTML()` | DOM API | §8.5.2, §8.6.4 | nicht vollständig | relevant |
| SAN-036 | `Document.parseHTML()` | DOM API | §8.5.2, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-037 | `Element.setHTMLUnsafe()` | DOM API | §8.5.2, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-038 | `ShadowRoot.setHTMLUnsafe()` | DOM API | §8.5.2, §8.6.4 | nicht vollständig | relevant |
| SAN-039 | `Document.parseHTMLUnsafe()` | DOM API | §8.5.2, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-040 | Sanitization Category `Default` | Normatives Konzept | §8.6.5 | nicht vollständig | vollständig relevant |
| SAN-041 | Sanitization Category `Unsafe` | Normatives Konzept | §8.6.5 | nicht vollständig | vollständig relevant |
| SAN-042 | Sanitization Category `Uncategorized` | Normatives Konzept | §8.6.5 | nicht vollständig | vollständig relevant |
| SAN-043 | Built-in Safe Baseline Configuration | Normatives Konzept | §8.6.5 | nicht vollständig | vollständig relevant |
| SAN-044 | Built-in Safe Default Configuration | Normatives Konzept | §8.6.5 | nicht vollständig | vollständig relevant |
| SAN-045 | Event Handler Content Attributes | Sanitization Rule | §8.6.4, §8.6.5 | teilweise elementbezogen | vollständig relevant |
| SAN-046 | `javascript:` URL Sanitization | Processing Rule | §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-047 | Template Contents Sanitization | Processing Rule | §8.6.4 | nicht vollständig | relevant |
| SAN-048 | Shadow Root Sanitization | Processing Rule | §8.6.4 | nicht vollständig | relevant |
| SAN-049 | SVG Sanitization Integration | Integration Feature | §8.6.4, §8.6.5 | teilweise | relevant |
| SAN-050 | MathML Sanitization Integration | Integration Feature | §8.6.5 | teilweise | relevant |
| SAN-051 | Configuration Canonicalization | Processing Model | §8.6.3, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-052 | Configuration Validation | Processing Model | §8.6.3, §8.6.4 | nicht vollständig | vollständig relevant |
| SAN-053 | Sanitizer Element Namespaces | Integration Feature | §8.6.3 | nicht vollständig | relevant |
| SAN-054 | Sanitizer Attribute Namespaces | Integration Feature | §8.6.3 | nicht vollständig | relevant |
| SAN-055 | Mutation XSS Boundary | Security Concept | §8.6.6.4 | nicht vollständig | relevant |

---

## Begriffsdefinitionen

### HTML Sanitization

HTML Sanitization bezeichnet die normative Verarbeitung eines HTML-basierten DOM-Baums, bei der Elemente, Attribute, Processing Instructions und gegebenenfalls Kommentare anhand einer Sanitizer-Konfiguration gefiltert werden.

Die Sanitization erfolgt auf einem DOM-/Node-Baum und ist mit dem HTML-Parsing verknüpft.

### Sanitizer

`Sanitizer` ist das zentrale DOM-Interface der Sanitizer API.

Ein `Sanitizer` besitzt eine zugehörige `SanitizerConfig`.

Die Konfiguration kann:

- abgefragt
- verändert
- für Allow-Listen verwendet
- für Remove-Listen verwendet
- für sichere Verarbeitung erweitert
- für unsichere Verarbeitung eingesetzt

werden.

### SanitizerConfig

`SanitizerConfig` ist das Dictionary, das die Filterregeln für einen `Sanitizer` beschreibt.

Die Konfiguration unterscheidet insbesondere:

- Elemente
- Attribute
- Processing Instructions
- Kommentare
- Custom Data Attributes
- Ersetzen von Elementen durch deren Kinder

### Safe

Eine Sanitization-Verarbeitung ist im Sinne der WHATWG sicher, wenn sie die vorgesehenen Schutzregeln gegen scriptfähiges Markup anwendet.

Die sicheren Methoden entfernen unsichere Inhalte unabhängig davon, ob eine Benutzerkonfiguration versucht, diese Inhalte zu erlauben.

### Unsafe

`Unsafe` bezeichnet in der Sanitization-Systematik eine Kategorie von Elementen, die XSS ermöglichen können.

Elemente mit dieser Kategorie werden von sicheren Sanitization-Methoden entfernt.

### Default

`Default` bezeichnet eine Sanitization-Kategorie für Elemente, die Bestandteil der eingebauten sicheren Standardkonfiguration sind.

### Uncategorized

`Uncategorized` bezeichnet Elemente, die weder standardmäßig entfernt noch standardmäßig in die Safe-Konfiguration aufgenommen werden.

Sie können dennoch explizit in einer Sanitizer-Konfiguration berücksichtigt werden.

### `replaceWithChildrenElements`

Diese Konfiguration bezeichnet Elemente, die selbst entfernt werden, deren Kinder jedoch erhalten bleiben.

Die Kinder werden vor der Entfernung des Elements rekursiv sanitisiert.

Bestimmte Elemente dürfen aus normativen Gründen nicht über diese Mechanik ersetzt werden.

---

## Normative Regeln

### Grundprinzip

Die Sanitizer API verarbeitet HTML nicht ausschließlich als Zeichenkette.

Der vorgesehene Ablauf ist grundsätzlich:

1. HTML wird durch den HTML-Parser verarbeitet.
2. Es entsteht ein DOM-/Node-Baum.
3. Der Sanitizer filtert diesen Baum.
4. Das Ergebnis wird in den vorgesehenen DOM-Kontext eingesetzt oder als Document zurückgegeben.

Damit ist die Sanitization eng mit dem HTML-Parsing verbunden.

### Safe- und Unsafe-Verarbeitung

Die WHATWG unterscheidet zwischen sicheren und unsicheren Methoden.

Zu den sicheren Methoden gehören:

- `Element.setHTML()`
- `ShadowRoot.setHTML()`
- `Document.parseHTML()`

Zu den Unsafe-Methoden gehören:

- `Element.setHTMLUnsafe()`
- `ShadowRoot.setHTMLUnsafe()`
- `Document.parseHTMLUnsafe()`

Die Unsafe-Methoden besitzen keine automatische Sicherheitsgarantie vergleichbar mit den Safe-Methoden.

Bei Unsafe-Methoden kann jedoch eine `Sanitizer`-Konfiguration angegeben werden.

### `Element.setHTML()`

`Element.setHTML()`:

1. verwendet den HTML-Parser,
2. verwendet das Element als Parsing-Kontext,
3. ermittelt einen Sanitizer,
4. erzeugt einen Fragmentbaum,
5. sanitisiert den Fragmentbaum,
6. ersetzt den bisherigen Inhalt des Elements durch das Ergebnis.

Die Sanitization ist Bestandteil des normativen Verarbeitungsmodells.

### `ShadowRoot.setHTML()`

`ShadowRoot.setHTML()` arbeitet analog zur sicheren Element-Variante.

Der Host des Shadow Roots stellt den Parsing-Kontext bereit.

Auch hier wird der erzeugte Fragmentbaum vor der Einfügung sanitisiert.

### `Document.parseHTML()`

`Document.parseHTML()`:

- parst den angegebenen HTML-String,
- erzeugt ein neues `Document`,
- wendet Sanitization an,
- entfernt unsichere Inhalte.

Das Ergebnis ist ein sanitisiertes Dokument.

### `Element.setHTMLUnsafe()`

`Element.setHTMLUnsafe()` parst HTML und ersetzt die Children des Elements.

Die Methode führt nicht automatisch die sichere Entfernung potentiell gefährlicher Elemente und Attribute durch.

Eine explizite `sanitizer`-Option kann verwendet werden.

Wenn `runScripts` aktiviert ist, wird die Verarbeitung mit dem entsprechenden Script-Verarbeitungsmodus durchgeführt.

### `ShadowRoot.setHTMLUnsafe()`

`ShadowRoot.setHTMLUnsafe()` ist die entsprechende Unsafe-Variante für einen Shadow Root.

Der Host des Shadow Roots stellt den Parsing-Kontext bereit.

### `Document.parseHTMLUnsafe()`

`Document.parseHTMLUnsafe()` erzeugt ein neues `Document`.

Die Methode entfernt unsichere Elemente und Attribute nicht automatisch.

Bei Verwendung einer Sanitizer-Konfiguration kann jedoch eine Sanitization durchgeführt werden.

Script-Elemente werden beim Parsing nicht unmittelbar ausgeführt.

---

## `Sanitizer` Interface

### Interface

Das WHATWG-Interface umfasst:

- `constructor()`
- `get()`
- `allowElement()`
- `removeElement()`
- `replaceElementWithChildren()`
- `allowProcessingInstruction()`
- `removeProcessingInstruction()`
- `allowAttribute()`
- `removeAttribute()`
- `setComments()`
- `setDataAttributes()`
- `removeUnsafe()`

### Konstruktor

Der Konstruktor akzeptiert:

- eine `SanitizerConfig`
- das Preset `"default"`

Der Default-Konstruktor verwendet die eingebaute sichere Standardkonfiguration.

### `get()`

`get()` liefert eine Kopie der Konfiguration des Sanitizers.

Die zurückgegebene Konfiguration kann verändert und anschließend für einen neuen `Sanitizer` verwendet werden.

### `allowElement()`

`allowElement()` stellt sicher, dass ein angegebenes Element in der Sanitizer-Konfiguration erlaubt wird.

Das Element wird dabei kanonisiert.

### `removeElement()`

`removeElement()` stellt sicher, dass ein angegebenes Element blockiert wird.

Bei Allow-Listen kann ein Element aus der Allow-Liste entfernt werden.

Bei Remove-Listen wird es gegebenenfalls hinzugefügt.

### `replaceElementWithChildren()`

`replaceElementWithChildren()` konfiguriert ein Element so, dass:

- das Element selbst entfernt wird,
- seine Kinder erhalten bleiben,
- die Kinder vorher sanitisiert werden.

Die Konfiguration darf bestimmte nicht ersetzbare Elemente nicht enthalten.

### `allowProcessingInstruction()`

Erlaubt eine Processing Instruction.

Die Angabe wird zunächst kanonisiert.

### `removeProcessingInstruction()`

Entfernt eine Processing Instruction aus der Allow-Liste beziehungsweise fügt sie der Remove-Liste hinzu.

### `allowAttribute()`

Erlaubt ein Attribut global.

Dabei wird zwischen:

- lokalem Namen
- Namespace

unterschieden.

### `removeAttribute()`

Entfernt ein Attribut aus einer Allow-Liste beziehungsweise fügt es einer Remove-Liste hinzu.

Die Operation berücksichtigt auch elementbezogene Attributlisten.

### `setComments()`

Bestimmt, ob Kommentare erhalten bleiben.

Die Safe-Default-Konfiguration deaktiviert Kommentare.

### `setDataAttributes()`

Bestimmt, ob Custom Data Attributes erlaubt werden.

Die Einstellung ist an die Verwendung einer Attribut-Allow-Liste gebunden.

### `removeUnsafe()`

`removeUnsafe()` erweitert beziehungsweise verändert die Konfiguration so, dass die als `Unsafe` definierten Inhalte entfernt werden.

Zusätzlich werden Event Handler Content Attributes berücksichtigt.

---

## SanitizerConfig

Die aktuelle `SanitizerConfig` enthält insbesondere:

- `elements`
- `removeElements`
- `replaceWithChildrenElements`
- `processingInstructions`
- `removeProcessingInstructions`
- `attributes`
- `removeAttributes`
- `comments`
- `dataAttributes`

### `elements`

`elements` ist eine globale Element-Allow-Liste.

Wenn `elements` vorhanden ist, dürfen grundsätzlich nur dort enthaltene Elemente verbleiben.

Elementbezogene Attributregeln können Bestandteil eines Eintrags sein.

### `removeElements`

`removeElements` ist eine globale Element-Remove-Liste.

Die Verwendung von `elements` und `removeElements` gleichzeitig als globale Listen ist nicht zulässig.

### `replaceWithChildrenElements`

Diese Liste enthält Elemente, die entfernt und durch ihre sanitisierten Kinder ersetzt werden.

Ein Element darf nicht gleichzeitig:

- erlaubt
- entfernt
- durch seine Kinder ersetzt

werden.

### `processingInstructions`

Allow-Liste für Processing Instructions.

### `removeProcessingInstructions`

Remove-Liste für Processing Instructions.

### `attributes`

Globale Attribut-Allow-Liste.

### `removeAttributes`

Globale Attribut-Remove-Liste.

### `comments`

Boolean-Einstellung für die Erhaltung von Kommentaren.

### `dataAttributes`

Boolean-Einstellung für Custom Data Attributes.

`dataAttributes` ist konzeptionell eine Erweiterung der globalen Attribut-Allow-Liste.

---

## Konfigurationsinvarianten

Eine gültige Sanitizer-Konfiguration muss die normativen Konsistenzbedingungen erfüllen.

### Globale Elementlisten

Es darf nicht gleichzeitig geben:

- `elements`
- `removeElements`

Wenn beide fehlen, entspricht dies der Verwendung einer leeren `removeElements`-Liste.

### Globale Attributlisten

Es darf nicht gleichzeitig geben:

- `attributes`
- `removeAttributes`

Wenn beide fehlen, entspricht dies der Verwendung einer leeren `removeAttributes`-Liste.

### Processing Instructions

Es darf nicht gleichzeitig geben:

- `processingInstructions`
- `removeProcessingInstructions`

### `dataAttributes`

`dataAttributes` darf nur in dem Konfigurationsmodell verwendet werden, das eine globale Attribut-Allow-Liste verwendet.

### Doppelte Elemente

Globale Elementlisten dürfen keine widersprüchlichen oder doppelten Einträge enthalten.

Insbesondere dürfen Elemente nicht gleichzeitig in:

- `elements`
- `removeElements`
- `replaceWithChildrenElements`

vorkommen.

### Doppelte Attribute

Globale Attributlisten dürfen keine widersprüchlichen oder doppelten Einträge enthalten.

### Lokale Attributlisten

Elementeinträge können lokale:

- `attributes`
- `removeAttributes`

besitzen.

Die Kombination muss den normativen Konsistenzbedingungen entsprechen.

### Nicht ersetzbare Elemente

Bestimmte Elemente dürfen nicht in `replaceWithChildrenElements` erscheinen.

Der Grund ist, dass das Ersetzen dieser Elemente durch ihre Kinder zu Problemen bei der Struktur und erneuten Interpretation des resultierenden Baums führen kann.

---

## Detailprüfung

### Elementverarbeitung

Bei der Sanitization werden Elemente anhand ihrer:

- Local Name
- Namespace

identifiziert.

Die Sanitizer-Konfiguration arbeitet deshalb nicht ausschließlich mit HTML-Local-Names.

Namespace-Information ist insbesondere für SVG und MathML relevant.

### Verarbeitung von Templates

Wenn ein HTML-`template`-Element sanitisiert wird, werden auch dessen Template Contents rekursiv verarbeitet.

Die Sanitization bezieht sich damit nicht nur auf die unmittelbaren Children des `template`-Elements.

### Verarbeitung von Shadow Roots

Wenn ein sanitisiertes Element ein Shadow Host ist, wird auch der zugehörige Shadow Root rekursiv sanitisiert.

### Kommentarverarbeitung

Kommentare werden abhängig von `configuration.comments` verarbeitet.

Wenn Kommentare nicht erlaubt sind, werden sie entfernt.

### Processing Instructions

Processing Instructions werden abhängig von:

- `processingInstructions`
- `removeProcessingInstructions`

gefiltert.

### Attribute

Attribute werden anhand ihrer:

- Local Name
- Namespace

identifiziert.

Ein Attribut kann global oder elementbezogen erlaubt beziehungsweise entfernt werden.

### `javascript:`-URLs

Die Sanitization besitzt eine eigene Prüfung auf `javascript:`-URLs.

Hierzu wird der Attributwert durch den WHATWG Basic URL Parser verarbeitet.

Wenn das resultierende URL-Schema `javascript` ist, wird das Attribut unter den entsprechenden Sanitization-Bedingungen entfernt.

Dies ist eine normative Processing Rule und darf nicht als bloße Browser-Empfehlung verstanden werden.

### Animating URL Attributes

Die Sanitization berücksichtigt außerdem bestimmte animierende URL-Attribute.

Die normative Regel kann dazu führen, dass entsprechende Attribute entfernt werden, wenn deren Werte als URL-bezogene Animationsmechanismen verarbeitet werden.

Die genaue Liste ist Bestandteil der WHATWG-Sanitization-Algorithmen und darf nicht durch eine frei erfundene oder veraltete Liste ersetzt werden.

---

## Attribute

Sanitization ist unmittelbar mit der Attributverarbeitung verbunden.

Relevant sind:

- globale Attribute
- elementbezogene Attribute
- Custom Data Attributes
- Event Handler Content Attributes
- URL-Attribute
- SVG-Attribute
- MathML-Attribute

### Event Handler Content Attributes

Event Handler Content Attributes werden bei der Safe-Sanitization durch die `remove unsafe`-Verarbeitung entfernt.

Die effektive sichere Basiskonfiguration verhält sich daher so, als würden diese Attribute in der Remove-Liste stehen.

### Custom Data Attributes

Custom Data Attributes werden über `dataAttributes` gesteuert.

Die Aktivierung von `dataAttributes` erlaubt die entsprechende Klasse von `data-*`-Attributen innerhalb des vorgesehenen Konfigurationsmodells.

### Namespace-bezogene Attribute

Sanitizer-Attribute können einen Namespace besitzen.

Das ist für die Verarbeitung von:

- HTML
- SVG
- MathML

relevant.

---

## Content Categories

Sanitization ist keine Content Category.

Die Content Categories aus `14-content-categories.md` werden durch Sanitization nicht ersetzt.

Allerdings können Content Categories indirekt relevant sein, wenn die Sanitizer-Konfiguration Elementgruppen verarbeitet.

Für die Sanitizer API gilt:

- `Flow content` ist keine Sanitizer-Kategorie.
- `Phrasing content` ist keine Sanitizer-Kategorie.
- `Embedded content` ist keine Sanitizer-Kategorie.
- `Interactive content` ist keine Sanitizer-Kategorie.
- `Palpable content` ist keine Sanitizer-Kategorie.

Die Sanitizer API arbeitet stattdessen mit konkreten Elementen und Namespaces.

---

## Context

Sanitization besitzt einen direkten Bezug zum Parsing-Kontext.

Bei:

- `Element.setHTML()`
- `Element.setHTMLUnsafe()`

stellt das jeweilige Element den Parsing-Kontext bereit.

Bei:

- `ShadowRoot.setHTML()`
- `ShadowRoot.setHTMLUnsafe()`

stellt der Host des Shadow Roots den relevanten Kontext bereit.

Bei:

- `Document.parseHTML()`
- `Document.parseHTMLUnsafe()`

wird ein neues Dokument erzeugt.

Damit hängt das Ergebnis der HTML-Parsing-Phase vom jeweiligen Kontext ab.

Die Sanitization findet auf dem daraus resultierenden DOM-Baum statt.

---

## Content Model

Sanitization definiert kein eigenes Content Model.

Die Sanitizer-Konfiguration entscheidet nicht anhand von:

- Flow Content
- Phrasing Content
- Sectioning Content
- Heading Content
- Embedded Content
- Interactive Content

über die Zulässigkeit.

Stattdessen arbeitet sie mit konkreten Elementen, Attributen und Namespaces.

Daraus folgt:

`SanitizerConfig` ist kein Content Model.

Die Sanitization kann jedoch dazu führen, dass ein ursprünglich geparster Baum nach dem Entfernen von Nodes eine andere inhaltliche Struktur besitzt.

---

## Processing Models

### Gesamtverarbeitung

Das normative Sanitization-Processing Model kann vereinfacht als folgende Verarbeitungskette dargestellt werden:

1. Ermittlung des Parsing-Kontexts.
2. Ermittlung des Sanitizers.
3. Auswahl des Safe-/Unsafe-Modus.
4. HTML-Fragment- oder Dokument-Parsing.
5. Erzeugung des DOM-Baums.
6. Sanitization des erzeugten Baums.
7. Einfügen beziehungsweise Rückgabe des Ergebnisses.

Diese Darstellung ist eine fachliche Zusammenfassung der normativen Algorithmen.

### Safe-Modus

Im Safe-Modus wird zusätzlich die `remove unsafe`-Verarbeitung auf die Sanitizer-Konfiguration angewendet.

Damit werden die normativ als unsicher definierten Elemente und Attribute entfernt.

### Unsafe-Modus

Im Unsafe-Modus wird die Konfiguration nicht automatisch durch die Safe-Baseline erweitert.

Ein leerer Sanitizer kann im Unsafe-Kontext deshalb grundsätzlich alle Inhalte zulassen.

### Sanitization des Nodes

Die Sanitization durchläuft rekursiv:

- DocumentType Nodes
- Text Nodes
- Comment Nodes
- Element Nodes
- Processing Instructions

Text und DocumentType werden nicht aufgrund der normalen Element-/Attributlisten entfernt.

Kommentare und Processing Instructions werden entsprechend ihrer Konfiguration behandelt.

### Rekursive Elementverarbeitung

Die Verarbeitung eines Elements berücksichtigt:

1. Ermittlung von Name und Namespace.
2. `replaceWithChildrenElements`.
3. globale Element-Allow-/Remove-Regeln.
4. Template Contents.
5. Shadow Root.
6. Attribute.
7. rekursive Verarbeitung der Kinder.

---

## DOM Interfaces / APIs

### `Sanitizer`

Zentrales Interface der Sanitization-Feature-Familie.

### `Element.setHTML()`

Safe HTML-Insertion API.

### `ShadowRoot.setHTML()`

Safe HTML-Insertion API für Shadow Roots.

### `Document.parseHTML()`

Safe HTML-Parsing API für ein neues `Document`.

### `Element.setHTMLUnsafe()`

Unsafe HTML-Insertion API.

### `ShadowRoot.setHTMLUnsafe()`

Unsafe HTML-Insertion API für Shadow Roots.

### `Document.parseHTMLUnsafe()`

Unsafe HTML-Parsing API.

### `DOMParser`

`DOMParser` gehört zur benachbarten DOM-Parsing-API.

Die klassische `DOMParser.parseFromString()`-Systematik ist nicht identisch mit der Sanitizer API.

Insbesondere ist `DOMParser` nicht selbst das Sanitizer-Interface.

Die WHATWG weist bei der modernen HTML-Parsing-Verarbeitung auf `Document.parseHTMLUnsafe()` als moderne Alternative für HTML-Parsing hin.

### `innerHTML`

`innerHTML` gehört zur HTML-Serialization-/DOM-Insertion-Systematik.

`innerHTML` ist nicht identisch mit der Sanitizer API.

Die Sanitizer API wird insbesondere relevant, wenn HTML sicher geparst und vor der Einfügung sanitisiert werden soll.

---

## Accessibility

Die Sanitizer API definiert keine eigene Accessibility-Semantik.

Sanitization kann jedoch Accessibility-relevante Inhalte entfernen.

Beispiele können sein:

- ARIA-Attribute
- semantische Attribute
- Attribute von SVG-/MathML-Elementen
- strukturgebende Elemente

Daher ist die Sanitizer-Konfiguration fachlich von Accessibility-Anforderungen der Anwendung abhängig.

Eine Sanitizer-Konfiguration darf nicht allein deshalb als accessibility-konform bezeichnet werden, weil sie WHATWG-konform ist.

Eine Aussage über konkrete Accessibility-Anforderungen muss gegebenenfalls anhand einer externen Accessibility-Spezifikation geprüft werden.

WHATWG-Definitionen und externe Accessibility-Regeln sind dabei getrennt zu dokumentieren.

---

## Sanitization

### Sanitization Categories

Die WHATWG definiert drei Sanitization-Kategorien:

| Kategorie | Bedeutung |
|---|---|
| `Default` | Bestandteil der eingebauten sicheren Standardkonfiguration |
| `Unsafe` | Kann XSS ermöglichen und wird bei Safe-Sanitization entfernt |
| `Uncategorized` | Nicht standardmäßig entfernt und nicht standardmäßig erlaubt |

### Built-in Safe Baseline Configuration

Die sichere Basiskonfiguration enthält in `removeElements`:

- alle HTML-Elemente, die in ihren individuellen Definitionen normativ als `Unsafe` gekennzeichnet sind
- das obsolete `frame`-Element
- SVG `script`
- SVG `use`

Die `removeAttributes`-Liste der Basiskonfiguration ist leer.

Event Handler Content Attributes werden jedoch durch `removeUnsafe()` automatisch entfernt.

### Built-in Safe Default Configuration

Die eingebaute sichere Standardkonfiguration enthält:

- `comments = false`
- `dataAttributes = false`
- eine Element-Allow-Liste
- eine Attribut-Allow-Liste
- `processingInstructions` als leere Liste

Die Attribut-Allow-Liste enthält unter anderem:

- `dir`
- `lang`
- `title`

sowie eine umfangreiche Auswahl von SVG-, MathML- und CSS-bezogenen Attributen, die für die sichere Standardverarbeitung vorgesehen sind.

Die vollständige normative Liste wird von der WHATWG als Bestandteil der Built-in Safe Default Configuration definiert.

### MathML

Die Safe Default Configuration enthält eine definierte Auswahl von MathML-Elementen.

Dazu gehören unter anderem:

- `math`
- `merror`
- `mfrac`
- `mi`
- `mmultiscripts`
- `mn`
- `mo`
- `mover`
- `mpadded`
- `mphantom`
- `mprescripts`
- `mroot`
- `mrow`
- `ms`
- `mspace`
- `msqrt`
- `mstyle`
- `msub`
- `msubsup`
- `msup`
- `mtable`
- `mtd`
- `mtext`
- `mtr`
- `munder`
- `munderover`
- `semantics`

Bestimmte MathML-Attribute sind ebenfalls Bestandteil der entsprechenden sicheren Konfiguration.

### SVG

Die Safe Default Configuration enthält eine definierte Auswahl von SVG-Elementen und Attributen.

Dazu gehören beispielsweise:

- `a`
- `circle`
- `defs`
- `desc`

sowie weitere normativ definierte SVG-Elemente.

SVG `script` und SVG `use` gehören dagegen zur sicheren Baseline-Remove-Liste.

---

## Konformitätsregeln

### Konfiguration

Eine Sanitizer-Konfiguration muss die von WHATWG definierten Invarianten erfüllen.

Ungültige Konfigurationen können zu einer `TypeError`-Exception führen.

### Safe APIs

Safe APIs müssen die Safe-Sanitization-Verarbeitung durchführen.

Eine Benutzerkonfiguration darf nicht dazu führen, dass scriptfähiges Markup durch die Safe-API erhalten bleibt.

### Unsafe APIs

Unsafe APIs dürfen potentiell gefährliches Markup erhalten.

Das bedeutet nicht, dass sie grundsätzlich ohne Sanitization arbeiten müssen.

Eine explizite Sanitizer-Konfiguration kann auch bei Unsafe APIs verwendet werden.

### `runScripts`

`runScripts` darf nur in einem Unsafe-Verarbeitungskontext aktiviert werden.

Im Safe-Modus ist eine entsprechende Aktivierung nicht zulässig.

### Template Contents

Template Contents müssen entsprechend den Sanitization-Algorithmen rekursiv verarbeitet werden.

### Shadow Roots

Shadow Roots eines sanitisierten Shadow Hosts werden entsprechend den Sanitization-Algorithmen ebenfalls verarbeitet.

### Namespaces

Elemente und Attribute müssen unter Berücksichtigung ihres Namespace behandelt werden.

Ein gleicher Local Name in unterschiedlichen Namespaces ist deshalb nicht automatisch dasselbe Sanitizer-Element.

---

## Security Considerations

Der WHATWG-Abschnitt §8.6.6 ist nicht-normativ.

Er beschreibt Grenzen und Sicherheitsaspekte der Sanitizer API.

### Server-side reflected and stored XSS

Die Sanitizer API arbeitet im DOM.

Sie schützt nicht automatisch gegen:

- serverseitig reflektiertes XSS
- serverseitig gespeichertes XSS

Serverseitige Verarbeitung liegt außerhalb der eigentlichen Sanitizer API.

### DOM Clobbering

DOM Clobbering kann auftreten, wenn manipuliertes HTML DOM-Eigenschaften über Mechanismen wie `id` oder `name` beeinflusst.

Die Sanitizer API ist nicht als vollständiger Schutz gegen sämtliche Formen des DOM Clobbering definiert.

### XSS with script gadgets

Die WHATWG behandelt auch XSS-Angriffe, die über Script Gadgets erfolgen können.

Die Existenz der Sanitizer API bedeutet nicht, dass jede mögliche Anwendungsschwäche durch das Entfernen klassischer scriptfähiger Elemente beseitigt wird.

### Mutation XSS

Mutation XSS beziehungsweise mXSS kann entstehen, wenn:

1. HTML sanitisiert wird,
2. der DOM-Baum anschließend serialisiert wird,
3. die serialisierte Zeichenkette erneut geparst wird,
4. sich die Interpretation des Markups verändert.

Die WHATWG weist ausdrücklich darauf hin, dass ein sanitisiertes DOM nach der Serialisierung nicht mehr als garantiert sanitisiert betrachtet werden darf.

Wenn sanitisiertes HTML wieder als String verarbeitet werden muss, soll es bei erneuter DOM-Einfügung erneut als untrusted HTML behandelt und sanitisiert werden.

---

## Querverweise

### Sanitization ↔ Parsing

Sanitization verwendet den HTML-Parser.

Relevante Verbindung:

`HTML String → HTML Parser → DOM Tree → Sanitization → DOM insertion`

Die allgemeine Parsing-Systematik ist in `21-parsing.md` dokumentiert.

### Sanitization ↔ DOM APIs

Die Sanitizer API ist eng mit:

- `Element`
- `ShadowRoot`
- `Document`

verbunden.

Die übergreifende API-Dokumentation befindet sich in `19-dom-interfaces-and-apis.md`.

### Sanitization ↔ Global Attributes

Attribute können durch Sanitization entfernt werden.

Die vollständige Definition der Global Attributes bleibt in `13-global-attributes.md`.

### Sanitization ↔ SVG/MathML

Die Sanitizer-Konfiguration berücksichtigt Namespaces und enthält normativ definierte SVG-/MathML-Inhalte.

Die allgemeine Integrationssystematik befindet sich in `22-svg-mathml-integration.md`.

### Sanitization ↔ Custom Elements

Custom Elements sind nicht selbst Bestandteil der Sanitizer API.

Sie können jedoch als DOM-Elemente von Sanitization betroffen sein.

Die Custom-Elements-Systematik befindet sich in `17-custom-elements.md`.

### Sanitization ↔ HTML Elements

Die individuellen HTML-Elementdefinitionen können eine Sanitization Category besitzen.

Die Sanitizer-Systematik nutzt diese Information für die Safe Baseline Configuration.

### Sanitization ↔ `innerHTML`

`innerHTML` kann einen sanitisierten DOM-Baum wieder in eine Zeichenkette überführen.

Eine erneute Verarbeitung dieser Zeichenkette kann zu Mutation-XSS-Risiken führen.

---

## Status / V1

### WHATWG-Status

| Feature | WHATWG-Status |
|---|---|
| HTML Sanitization | im Living Standard definiert |
| `Sanitizer` | normative API |
| `SanitizerConfig` | normative API-Datenstruktur |
| Safe Sanitization | normatives Processing Model |
| Unsafe Sanitization | normatives Processing Model |
| Sanitization Categories | normative Definition |
| `Element.setHTML()` | normative DOM API |
| `ShadowRoot.setHTML()` | normative DOM API |
| `Document.parseHTML()` | normative DOM API |
| `Element.setHTMLUnsafe()` | normative DOM API |
| `ShadowRoot.setHTMLUnsafe()` | normative DOM API |
| `Document.parseHTMLUnsafe()` | normative DOM API |

### WHATWG-Status und Browser-Support

Browser-Kompatibilität ist nicht Bestandteil dieser Statusbewertung.

Insbesondere bedeutet:

- „im WHATWG Living Standard definiert“

nicht automatisch:

- „in allen Browsern implementiert“.

Browser-Support ist als separate Rechercheebene zu behandeln.

### V1-Einstufung

Die Zuordnung zu einer ZE-WebLab-V1-Kategorie ist projektspezifisch.

Für diese Datei gilt:

- WHATWG-Status: normatives HTML-/DOM-/API-Konzept
- ZE-WebLab-Ebene: Rechercheebene 2
- Feature-Typ: API / Processing Model / Security Feature
- V1-Zuordnung: projektspezifisch

Die V1-Einstufung darf nicht als WHATWG-Status interpretiert werden.

---

## Offene Punkte

Zum Zeitpunkt der Recherche wurden keine grundlegenden offenen Punkte innerhalb des abgegrenzten §8.6-Bereichs festgestellt.

Folgende Punkte bleiben bewusst als Abgrenzungen bestehen:

1. Die vollständige browserseitige Implementierungs- und Kompatibilitätslage gehört nicht in diese WHATWG-Statusdokumentation.
2. Externe Accessibility-Anforderungen werden nicht aus der Sanitizer API abgeleitet.
3. Allgemeine Anwendungssicherheit ist nicht mit HTML Sanitization gleichzusetzen.
4. CSP und Trusted Types sind eigenständige Webplattform-/Security-Konzepte und werden nicht als Bestandteile der Sanitizer API behandelt.
5. Server-seitige XSS-Verarbeitung liegt außerhalb der Sanitizer API.
6. Eine vollständige Liste aller als `Unsafe` oder `Default` klassifizierten Elemente wird nicht redundant aus den individuellen Elementdateien kopiert; die normative Quelle bleibt die jeweilige WHATWG-Elementdefinition und die Built-in Sanitizer Configuration.
7. SVG- und MathML-spezifische Einzelregeln werden hier nur insoweit behandelt, wie sie für die Sanitizer API relevant sind; die vollständige Integrationssystematik bleibt in `22-svg-mathml-integration.md`.

---

## Prüfstatus

### Geprüfte normative Bereiche

- §8.5 DOM parsing and serialization APIs
- §8.5.2 HTML parsing methods
- §8.6 HTML sanitization
- §8.6.1 Introduction
- §8.6.1.1 Safe and unsafe
- §8.6.2 The `Sanitizer` interface
- §8.6.3 Sanitizer configuration
- §8.6.3.1 Configuration invariants
- §8.6.4 Sanitization algorithms
- §8.6.5 Sanitization constants
- §8.6.6 Security considerations
- §8.6.6.1 Server-side reflected and stored XSS
- §8.6.6.2 DOM clobbering
- §8.6.6.3 XSS with script gadgets
- §8.6.6.4 Mutation XSS

### Geprüfte Querverbindungen

- DOM
- HTML Parsing
- Dynamic Markup Insertion
- HTML Elements
- Global Attributes
- SVG
- MathML
- Shadow DOM
- Custom Elements
- HTML Serialization

### Ergebnis

Der abgegrenzte Sanitization-Bereich ist für die Rechercheebene 2 vollständig geprüft.

Die Datei behandelt HTML Sanitization als eigenständige Feature-Familie und zählt weder `Sanitizer` noch die zugehörigen APIs, Konfigurationen oder Processing Models als HTML-Elemente.

---

## Quellen / Referenzen

### Primärquelle

WHATWG HTML Living Standard

Maßgeblicher Bereich:

- §8.6 HTML sanitization
- §8.6.1 Introduction
- §8.6.1.1 Safe and unsafe
- §8.6.2 The `Sanitizer` interface
- §8.6.3 Sanitizer configuration
- §8.6.3.1 Configuration invariants
- §8.6.4 Sanitization algorithms
- §8.6.5 Sanitization constants
- §8.6.6 Security considerations

### Verwandte Primärbereiche

- §8.5 DOM parsing and serialization APIs
- §8.5.2 HTML parsing methods
- §4 The elements of HTML
- §4.13 Custom elements
- §13 The HTML syntax

### Projektquelle

ZE-WebLab GitHub Repository:

- `docs/html/13-global-attributes.md`
- `docs/html/14-content-categories.md`
- `docs/html/15-content-models.md`
- `docs/html/17-custom-elements.md`
- `docs/html/18-contexts.md`
- `docs/html/19-dom-interfaces-and-apis.md`
- `docs/html/21-parsing.md`
- `docs/html/22-svg-mathml-integration.md`
- `docs/html/23-microdata.md`

### Quellenstatus

- WHATWG: normative Primärquelle
- ZE-WebLab: Projekt-/Bestandsquelle
- externe Quellen: für die normative Definition dieser Datei nicht erforderlich
- Browser-Kompatibilität: bewusst nicht Bestandteil dieser Datei