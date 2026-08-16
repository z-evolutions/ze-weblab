# ZE-WebLab – HTML-Referenz: Embedded Content

## 1. Arbeitsstand / Quellenstand

**Themenbereich:** HTML Embedded Content

**WHATWG-Bereich:** §4.8 „Embedded content“

**Recherchegegenstand:** aktuelle WHATWG HTML Living Standard

**Geprüfter Standardstand:** 11. August 2026

**Prüfstatus:** abgeschlossen für §4.8 auf Ebene der WHATWG-Elementdefinitionen, der unmittelbar zugehörigen Unterkonzepte, Verarbeitungsmodelle und Integrationsregeln.

Die Recherche berücksichtigt insbesondere:

- §4.8.1 The `picture` element
- §4.8.2 The `source` element
- §4.8.3 The `img` element
- §4.8.4 Images
- §4.8.4.1 Introduction
- §4.8.4.1.1 Adaptive images
- §4.8.4.2 Attributes common to `source`, `img`, and `link` elements
- §4.8.4.2.1 Srcset attributes
- §4.8.4.2.2 Sizes attributes
- §4.8.4.3 Processing model
- §4.8.4.3.1 When to obtain images
- §4.8.4.3.2 Reacting to DOM mutations
- §4.8.4.3.3 The list of available images
- §4.8.4.3.4 Decoding images
- §4.8.4.3.5 Updating the image data
- §4.8.4.3.6 Preparing an image for presentation
- §4.8.4.3.7 Selecting an image source
- §4.8.4.3.8 Creating a source set from attributes
- §4.8.4.3.9 Updating the source set
- §4.8.4.3.10 Parsing a `srcset` attribute
- §4.8.4.3.11 Parsing a `sizes` attribute
- §4.8.4.3.12 Normalizing the source densities
- §4.8.4.3.13 Reacting to environment changes
- §4.8.4.4 Requirements for providing text to act as an alternative for images
- §4.8.4.4.1 General guidelines
- §4.8.4.4.2 A link or button containing nothing but the image
- §4.8.4.4.3 A phrase or paragraph with an alternative graphical representation
- §4.8.4.4.4 A short phrase or label with an alternative graphical representation
- §4.8.4.4.5 Text rendered to a graphic for typographical effect
- §4.8.4.4.6 A graphical representation of surrounding text
- §4.8.4.4.7 Ancillary images
- §4.8.4.4.8 Purely decorative images
- §4.8.4.4.9 Groups of images forming one larger picture without links
- §4.8.4.4.10 Groups of images forming one larger picture with links
- §4.8.4.4.11 A key part of the content
- §4.8.4.4.12 An image not intended for the user
- §4.8.4.4.13 Images in email or private documents
- §4.8.4.4.14 Guidance for markup generators
- §4.8.4.4.15 Guidance for conformance checkers
- §4.8.5 The `iframe` element
- §4.8.6 The `embed` element
- §4.8.7 The `object` element
- §4.8.8 The `video` element
- §4.8.9 The `audio` element
- §4.8.10 The `track` element
- §4.8.11 Media elements
- §4.8.11.1 Error codes
- §4.8.11.2 Location of the media resource
- §4.8.11.3 MIME types
- §4.8.11.4 Network states
- §4.8.11.5 Loading the media resource
- §4.8.11.6 Offsets into the media resource
- §4.8.11.7 Ready states
- §4.8.11.8 Playing the media resource
- §4.8.11.9 Seeking
- §4.8.11.10 Media resources with multiple media tracks
- §4.8.11.10.1 `AudioTrackList` and `VideoTrackList`
- §4.8.11.10.2 Declarative selection of audio and video tracks
- §4.8.11.11 Timed text tracks
- §4.8.11.11.1 Text track model
- §4.8.11.11.2 Sourcing in-band text tracks
- §4.8.11.11.3 Sourcing out-of-band text tracks
- §4.8.11.11.4 Guidelines for exposing cues
- §4.8.11.11.5 Text track API
- §4.8.11.11.6 Event handlers for text track APIs
- §4.8.11.11.7 Best practices for metadata text tracks
- §4.8.11.12 Identifying a track kind through a URL
- §4.8.11.13 User interface
- §4.8.11.14 Time ranges
- §4.8.11.15 The `TrackEvent` interface
- §4.8.11.16 Events summary
- §4.8.11.17 Security and privacy considerations
- §4.8.11.18 Best practices for authors using media elements
- §4.8.11.19 Best practices for implementers of media elements
- §4.8.12 The `map` element
- §4.8.13 The `area` element
- §4.8.14 Image maps
- §4.8.14.1 Authoring
- §4.8.14.2 Processing model
- §4.8.15 MathML
- §4.8.16 SVG
- §4.8.17 Dimension attributes

Wichtig:

§4.8 enthält sowohl konkrete HTML-Elementdefinitionen als auch eigenständige Konzept-, API-, Verarbeitungs- und Integrationsbereiche.

Für ZE-WebLab werden diese Ebenen nicht vermischt.

---

## 2. WHATWG-Struktur

Der Bereich §4.8 „Embedded content“ ist in folgende fachliche Gruppen gegliedert:

### 2.1 HTML-Elementdefinitionen

Die eigentlichen HTML-Elemente dieses Bereichs sind:

- `picture`
- `source`
- `img`
- `iframe`
- `embed`
- `object`
- `video`
- `audio`
- `track`
- `map`
- `area`

Damit werden **11 benannte HTML-Elemente** als Elementinventar geführt.

### 2.2 Bildinfrastruktur

§4.8.4 „Images“ ist kein zusätzliches Element.

Der Bereich behandelt unter anderem:

- adaptive images
- `srcset`
- `sizes`
- source sets
- image candidate strings
- resource selection
- image fetching
- image decoding
- Reaktion auf DOM-Mutationen
- Reaktion auf Änderungen der Umgebung
- alternative Texte
- Conformance-Regeln für `alt`

Diese Konzepte werden als eigene Konzept-/Verarbeitungsfamilie behandelt.

### 2.3 Media-Infrastruktur

§4.8.11 „Media elements“ ist kein zusätzliches HTML-Element.

Er beschreibt die gemeinsame Infrastruktur von:

- `audio`
- `video`

Dazu gehören unter anderem:

- `HTMLMediaElement`
- Media-Fehler
- Netzwerkzustände
- Ready States
- Laden von Media Resources
- Playback
- Seeking
- Media Tracks
- Audio Tracks
- Video Tracks
- Text Tracks
- Time Ranges
- Media Events
- Media User Interface
- Security and Privacy
- Authoring-/Implementation-Best-Practices

### 2.4 Image Maps

§4.8.14 „Image maps“ ist kein zusätzliches HTML-Element.

Es beschreibt die Beziehung zwischen:

- `img`
- `map`
- `area`
- `usemap`
- geometrischen Bereichen
- Hyperlinks
- alternativem Text
- Interaktionsverarbeitung

### 2.5 Fremdsprachenintegration

§4.8.15 und §4.8.16 behandeln:

- MathML
- SVG

Diese sind **keine HTML-Elemente** und werden daher nicht in das HTML-Elementinventar aufgenommen.

Die HTML-Spezifikation definiert hier insbesondere Integrationsregeln für die Einbettung der Fremdsprachen in HTML.

### 2.6 Dimension Attributes

§4.8.17 ist kein eigenes Element.

Es beschreibt gemeinsame Regeln für bestimmte `width`- und `height`-Attribute, insbesondere für:

- `img`
- `iframe`
- `embed`
- `object`
- `video`
- `source` unter `picture`
- `input` im Image-Button-State

---

## 3. Inventar

| Feature | WHATWG-Abschnitt | Content Categories | Context | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Status |
|---|---|---|---|---|---|---|---|---|---|
| `picture` | §4.8.1 | Flow, Phrasing, Embedded, Palpable | Wo Embedded Content erwartet wird | `source*`, danach `img`, optional Script-supporting Elements | Keine Auslassung | Global Attributes | Uncategorized | `HTMLPictureElement` | aktuell definiert |
| `source` | §4.8.2 | Keine | In `picture` vor `img`; in Media Element vor Flow/`track` | Nothing | Kein End-Tag | Global + kontextabhängig `type`, `media`, `src`, `srcset`, `sizes`, `width`, `height` | Uncategorized | `HTMLSourceElement` | aktuell definiert |
| `img` | §4.8.3 | Flow, Phrasing, Embedded, Form-associated, ggf. Interactive, Palpable | Wo Embedded Content erwartet; in `picture` nach `source` | Nothing | Kein End-Tag | Global + `alt`, `src`, `srcset`, `sizes`, `crossorigin`, `usemap`, `ismap`, `controls`, `width`, `height`, `referrerpolicy`, `decoding`, `loading`, `fetchpriority` | Uncategorized | `HTMLImageElement` | aktuell definiert |
| `iframe` | §4.8.5 | Flow, Phrasing, Embedded, Interactive, Palpable | Wo Embedded Content erwartet | Nothing | Keine Auslassung | Global + `src`, `srcdoc`, `name`, `sandbox`, `allow`, `allowfullscreen`, `width`, `height`, `referrerpolicy`, `loading` | Unsafe | `HTMLIFrameElement` | aktuell definiert |
| `embed` | §4.8.6 | Flow, Phrasing, Embedded, Interactive, Palpable | Wo Embedded Content erwartet | Nothing | Kein End-Tag | Global + `src`, `type`, `width`, `height` und weitere nicht-namespaced Attribute nach den Regeln der Definition | Unsafe | `HTMLEmbedElement` | aktuell definiert |
| `object` | §4.8.7 | Flow, Phrasing, Embedded, Listed form-associated, Palpable | Wo Embedded Content erwartet | Transparent | Keine Auslassung | Global + `data`, `type`, `name`, `form`, `width`, `height` | Unsafe | `HTMLObjectElement` | aktuell definiert |
| `video` | §4.8.8 | Flow, Phrasing, Embedded, ggf. Interactive, Palpable | Wo Embedded Content erwartet | Abhängig von `src`; `track*`, `source*`, transparent, aber keine Media-Element-Nachfahren | Keine Auslassung | Global + Media-/Video-Attribute | Uncategorized | `HTMLVideoElement` | aktuell definiert |
| `audio` | §4.8.9 | Flow, Phrasing, Embedded, ggf. Interactive und Palpable | Wo Embedded Content erwartet | Abhängig von `src`; `track*`, `source*`, transparent, aber keine Media-Element-Nachfahren | Keine Auslassung | Global + Media-Attribute | Uncategorized | `HTMLAudioElement` | aktuell definiert |
| `track` | §4.8.10 | Keine | Als Kind eines Media Elements vor Flow Content | Nothing | Kein End-Tag | Global + `kind`, `src`, `srclang`, `label`, `default` | Uncategorized | `HTMLTrackElement` | aktuell definiert |
| `map` | §4.8.12 | Flow, Phrasing, Palpable | Wo Phrasing Content erwartet | Transparent | Keine Auslassung | Global + `name` | Uncategorized | `HTMLMapElement` | aktuell definiert |
| `area` | §4.8.13 | Flow, Phrasing | Wo Phrasing Content erwartet, aber nur mit `map`-Ancestor | Nothing | Kein End-Tag | Global + Image-Map-/Hyperlink-Attribute | Uncategorized + navigating URL `href` | `HTMLAreaElement` | aktuell definiert |

---

## 4. Detailprüfung: `picture`

### 4.1 Semantische Rolle

`picture` ist ein Container für mehrere alternative Bildquellen, die gemeinsam mit einem enthaltenen `img`-Element eine deklarative Auswahl eines geeigneten Bildes ermöglichen.

Die Auswahl kann insbesondere von folgenden Faktoren abhängen:

- Pixeldichte des Displays
- Viewport-Größe
- Bildformat
- Media Query
- weitere von der Bildquellenauswahl berücksichtigte Umgebungsbedingungen

`picture` selbst stellt kein sichtbares Bild dar.

Das tatsächlich eingebettete Bild wird durch das enthaltene `img` repräsentiert.

### 4.2 Content Categories

`picture` ist:

- Flow content
- Phrasing content
- Embedded content
- Palpable content

### 4.3 Context

`picture` darf verwendet werden:

- dort, wo Embedded Content erwartet wird.

### 4.4 Content Model

Das Content Model besteht aus:

1. null oder mehr `source`-Elementen,
2. danach genau einem `img`-Element,
3. optional dazwischen bzw. entsprechend der Definition Script-supporting Elements.

Das `img`-Element bildet dabei den zentralen Darstellungs- und Fallbackpunkt.

### 4.5 Tag Omission

Weder Start- noch End-Tag dürfen ausgelassen werden.

### 4.6 Content Attributes

`picture` besitzt neben den Global Attributes keine eigenen Content Attributes.

Die eigentliche Quellenbeschreibung erfolgt über:

- `source`
- `img`

### 4.7 Normative Strukturregel

Ein `picture`-Element ist nicht mit einem `video`- oder `audio`-Element gleichzusetzen.

Insbesondere hat `source` innerhalb von `picture` eine andere Bedeutung als `source` innerhalb eines Media Elements.

Bei `picture` ist `source` Teil der Auswahl eines Bild-Source-Sets.

Das `src`-Attribut von `source` hat innerhalb von `picture` keine Bedeutung.

### 4.8 Resource Selection

Der User Agent bestimmt anhand der beteiligten `source`- und `img`-Attribute, welche Bildquelle verwendet wird.

Dabei sind insbesondere relevant:

- `srcset`
- `sizes`
- `media`
- `type`
- die Umgebung
- die unterstützten Bildformate
- die Regeln des Source-Set- und Image-Selection-Modells

### 4.9 Sanitization

WHATWG klassifiziert `picture` als:

- Uncategorized

Die Sanitization-Information ist als eigene Informationsebene zu führen.

### 4.10 DOM Interface

`picture` implementiert:

`HTMLPictureElement`

Das Interface besitzt insbesondere den HTML-Konstruktor und erbt von `HTMLElement`.

---

## 5. Detailprüfung: `source`

### 5.1 Semantische Rolle

`source` stellt eine alternative Quelle für:

- ein `img` innerhalb von `picture`
- ein Media Element (`audio` oder `video`)

bereit.

`source` repräsentiert selbst nichts.

### 5.2 Content Categories

`source` besitzt keine Content Category.

### 5.3 Context

`source` kann in zwei unterschiedlichen Kontexten auftreten:

#### Innerhalb von `picture`

Als Kind eines `picture`-Elements:

- vor dem `img`-Element.

#### Innerhalb eines Media Elements

Als Kind von:

- `audio`
- `video`

und dort vor Flow Content oder `track`-Elementen entsprechend dem Media Content Model.

### 5.4 Content Model

`source` hat das Content Model:

- Nothing

### 5.5 Tag Omission

Das End-Tag ist nicht vorhanden bzw. darf nicht angegeben werden.

### 5.6 Content Attributes

Gemeinsam:

- Global Attributes
- `type`
- `media`

Zusätzlich abhängig vom Kontext:

#### In `picture`

- `srcset`
- `sizes`
- `width`
- `height`

#### In `audio` / `video`

- `src`

`srcset` und `sizes` gehören zum Bildquellenmodell und sind für `source` im Media-Kontext nicht vorgesehen.

Umgekehrt ist `src` die Media-Resource-Adresse und nicht die Bildquelle eines `picture`-`source`.

### 5.7 `type`

Wenn vorhanden:

- muss ein gültiger MIME-Type-String sein.

Bei `picture` ermöglicht `type` dem User Agent, Quellen eines nicht unterstützten Bildformats zu überspringen.

Bei Media Resources hilft `type`, ungeeignete Ressourcen vor dem Abruf zu erkennen.

### 5.8 `media`

Wenn vorhanden:

- muss eine gültige Media-Query-Liste enthalten.

Innerhalb von `picture` wird die Umgebungsauswertung im Rahmen der Bildquellenauswahl berücksichtigt.

### 5.9 `srcset` und `sizes` in `picture`

Bei einem `source` unter `picture`:

- `srcset` muss vorhanden sein.
- `sizes` ist insbesondere erforderlich, wenn `srcset` Width Descriptors verwendet und das folgende `img` nicht Auto-Sizes erlaubt.
- `sizes` kann bei einem `img`, das Auto-Sizes erlaubt, unter den entsprechenden Bedingungen entfallen.

### 5.10 `src` im Media-Kontext

Bei `source` als Kind von `audio` oder `video`:

- `src` muss vorhanden sein.
- Der Wert muss eine gültige, nichtleere URL sein.
- `type` kann die Media-Ressource genauer beschreiben.
- `srcset` und `sizes` dürfen in diesem Kontext nicht verwendet werden.

### 5.11 DOM-Änderungen

WHATWG definiert spezielle Element-Insertion-, Moving- und Removing-Steps für `source`.

Diese stehen insbesondere mit:

- Media Resource Selection
- `picture`
- relevanten Mutationen eines `img`

in Verbindung.

Damit ist `source` nicht lediglich ein passiver Datenträger von Attributen.

### 5.12 Sanitization

Sanitization:

- Uncategorized

### 5.13 DOM Interface

`source` implementiert:

`HTMLSourceElement`

Das Interface reflektiert unter anderem:

- `src`
- `type`
- `srcset`
- `sizes`
- `media`
- `width`
- `height`

---

## 6. Detailprüfung: `img`

### 6.1 Semantische Rolle

`img` repräsentiert ein Bild.

Das eingebettete Medium wird über:

- `src`
- `srcset`
- gegebenenfalls vorherige `source`-Elemente in `picture`

bestimmt.

Der `alt`-Wert stellt den Ersatzinhalt für Nutzer bereit, die das Bild nicht verarbeiten können oder dessen Darstellung deaktiviert haben.

### 6.2 Content Categories

`img` ist:

- Flow content
- Phrasing content
- Embedded content
- Form-associated element
- Palpable content

Zusätzlich kann `img` Interactive Content sein, wenn:

- `usemap` vorhanden ist
- oder `controls` vorhanden ist

### 6.3 Context

`img` darf verwendet werden:

- dort, wo Embedded Content erwartet wird.

Zusätzlich:

- als Kind von `picture`, nach allen `source`-Elementen.

### 6.4 Content Model

`img` hat:

- Nothing

### 6.5 Tag Omission

Das End-Tag ist nicht vorhanden bzw. darf nicht angegeben werden.

### 6.6 Content Attributes

Neben den Global Attributes:

- `alt`
- `src`
- `srcset`
- `sizes`
- `crossorigin`
- `usemap`
- `ismap`
- `controls`
- `width`
- `height`
- `referrerpolicy`
- `decoding`
- `loading`
- `fetchpriority`

### 6.7 `src`

Wenn vorhanden:

- gültige nichtleere URL
- muss auf eine nichtinteraktive Bildressource verweisen
- die Ressource darf optional animiert sein
- sie darf weder paginiert noch skriptbasiert sein

Die Spezifikation nennt als mögliche Bildressourcen unter anderem:

- Bitmap-Bilder
- einzelne Vektordokumente
- animierte Bitmaps
- deklarativ animierte Vektorgrafiken

Nicht von dieser Definition umfasst sind insbesondere:

- skriptfähige SVG-Dateien
- mehrseitige PDFs
- HTML-Dokumente
- reine Textdokumente
- interaktive MNG-Ressourcen

### 6.8 `srcset`

`srcset` ist ein eigener Source-Set-Mechanismus.

Die Werte können Image Candidate Strings mit unterschiedlichen Deskriptoren enthalten.

Relevant sind insbesondere:

- Width Descriptors
- Density Descriptors
- Kandidatenauswahl
- Source Size

### 6.9 `sizes`

`sizes` bestimmt die angenommene bzw. berechnete Quellgröße für die Auswahl von Bildkandidaten.

Wenn `srcset` Width Descriptors enthält, gelten besondere Anforderungen an `sizes`.

Bei Lazy Loading kann unter den von WHATWG definierten Bedingungen auch `sizes="auto"` beziehungsweise ein entsprechender `auto`-Beginn verwendet werden.

### 6.10 `alt`

`alt` ist die zentrale alternative Textrepräsentation des Bildes.

WHATWG behandelt die Anforderungen an `alt` in einem eigenen umfangreichen Unterabschnitt.

Die konkrete Wahl des Alternativtextes hängt vom Verwendungskontext ab.

Dabei unterscheidet die Spezifikation unter anderem:

- Bilder als alleinige Inhalte eines Links oder Buttons
- Bilder als grafische Darstellung eines Textes
- Charts
- Diagramme
- Graphen
- Karten
- Illustrationen
- Icons
- Logos
- typografisch gerenderter Text
- ergänzende Bilder
- dekorative Bilder
- Bildgruppen
- zentrale Bestandteile des Inhalts
- Bilder, die nicht für den Nutzer bestimmt sind
- private Dokumente und E-Mails

### 6.11 Decorative Images

Bei rein dekorativen Bildern ist ein leerer `alt`-Wert das relevante Muster.

Ein fehlendes `alt` darf nicht pauschal als gleichwertig mit einem absichtlich leeren `alt` behandelt werden.

### 6.12 `crossorigin`

`crossorigin` ist ein CORS-Settings-Attribut.

Es beeinflusst insbesondere die Verwendung von Bildern aus anderen Origins in Verbindung mit Canvas.

### 6.13 `usemap`

`usemap` referenziert eine Image Map.

Der Wert muss den dafür vorgesehenen Hash-Name-Referenzregeln entsprechen.

Die eigentliche Image-Map-Struktur wird über:

- `map`
- `area`

gebildet.

### 6.14 `ismap`

`ismap` ist ein Boolean Attribute.

Es darf nur unter der von WHATWG vorgesehenen Beziehung zu einem `a`-Element mit `href` verwendet werden.

Es kennzeichnet ein serverseitiges Image Map.

### 6.15 `controls`

`controls` ist ein Boolean Attribute.

Bei `img` erlaubt es dem User Agent, eine Benutzeroberfläche über dem Bild bereitzustellen.

Die Spezifikation schränkt die Verwendung ein:

- `alt` muss vorhanden sein.
- `alt` darf nicht leer sein.

Die konkrete Benutzeroberfläche ist implementation-defined.

### 6.16 `referrerpolicy`

`referrerpolicy` bestimmt die Referrer Policy für Fetches, die durch das Element ausgelöst werden.

### 6.17 `decoding`

`decoding` ist ein Image Decoding Hint.

Die möglichen Zustände und Defaults werden durch die entsprechende gemeinsame Infrastruktur definiert.

WHATWG beschreibt für `img` insbesondere:

- Preferred Decoding Method
- Auto State
- Reflection des Attributes durch das DOM Interface.

### 6.18 `loading`

`loading` ist ein Lazy Loading Attribute.

Es beeinflusst, ob Bildressourcen außerhalb des Viewports verzögert geladen werden.

WHATWG definiert dafür unter anderem:

- Eager State
- Lazy State
- Lazy Load Resumption Steps

Das Attribut ist keine reine Performance-Empfehlung, sondern Teil des normativen HTML-Verarbeitungsmodells.

### 6.19 `fetchpriority`

`fetchpriority` ist ein Fetch Priority Attribute.

Es beeinflusst die Priorität der vom Element initiierten Fetches.

### 6.20 Dimension Attributes

`img` unterstützt:

- `width`
- `height`

als Dimension Attributes.

Diese können insbesondere dazu beitragen, Dimensionen beziehungsweise Seitenverhältnisse frühzeitig festzulegen und Layout Shifts zu vermeiden.

### 6.21 Image Processing

Die Verarbeitung von `img` umfasst unter anderem:

1. Ermittlung des Source Sets.
2. Auswahl geeigneter Bildkandidaten.
3. Berücksichtigung der Umgebung.
4. Abruf der Ressource.
5. Dekodierung.
6. Aktualisierung des Bildzustands.
7. Vorbereitung für die Darstellung.
8. Reaktion auf DOM-Mutationen.
9. Reaktion auf Änderungen der Umgebung.

### 6.22 `decode()`

`HTMLImageElement.decode()` ermöglicht es, die Dekodierung eines Bildes anzufordern und auf eine Promise-basierte Fertigstellung zu warten.

Bei erfolgreicher Dekodierung wird die Promise erfüllt.

Bei einem Fehler kann die Promise mit einer `EncodingError`-DOMException abgelehnt werden.

### 6.23 `complete`

`complete` zeigt an, ob das Bild vollständig verarbeitet bzw. kein weiterer Bildabruf erforderlich ist oder ein endgültiger Fehlerzustand erreicht wurde.

Der konkrete Getter ist an den Zustand der aktuellen und gegebenenfalls ausstehenden Requests gebunden.

### 6.24 `currentSrc`

`currentSrc` liefert die absolute URL der aktuell verwendeten Bildressource.

### 6.25 `naturalWidth` und `naturalHeight`

Diese liefern die dichtekorrigierten natürlichen Dimensionen des verfügbaren Bildes.

Wenn das Bild nicht verfügbar ist, wird `0` geliefert.

### 6.26 Legacy Factory Function

WHATWG definiert zusätzlich die Legacy Factory Function:

`Image(width, height)`

Sie erzeugt ein neues `HTMLImageElement` und kann die Dimensionen setzen.

### 6.27 Sanitization

Sanitization:

- Uncategorized

### 6.28 DOM Interface

`img` implementiert:

`HTMLImageElement`

Wichtige Mitglieder umfassen:

- `alt`
- `src`
- `srcset`
- `sizes`
- `crossOrigin`
- `useMap`
- `isMap`
- `controls`
- `width`
- `height`
- `naturalWidth`
- `naturalHeight`
- `complete`
- `currentSrc`
- `referrerPolicy`
- `decoding`
- `loading`
- `fetchPriority`
- `decode()`

---

## 7. Bildverarbeitung und Adaptive Images

### 7.1 Adaptive Images

Adaptive Images ermöglichen die Auswahl unterschiedlicher Ressourcen abhängig von:

- Display Density
- Viewport
- Layout
- Bildformat
- sonstigen Umweltbedingungen

Das zentrale Modell besteht aus:

- Source Set
- Source Size
- Image Candidates
- Candidate Selection

### 7.2 `srcset`-Verarbeitung

Die Spezifikation unterscheidet insbesondere:

- URL plus Density Descriptor
- URL plus Width Descriptor

Bei Width Descriptors ist die `sizes`-Information für die Auswahl relevant.

### 7.3 `sizes`-Verarbeitung

`sizes` wird als Liste von Größenbedingungen ausgewertet.

Dabei werden unter anderem:

- Media Conditions
- Length Values
- Default Source Size

berücksichtigt.

### 7.4 Source Set

Ein Source Set ist die Menge der verfügbaren Bildkandidaten.

Es kann aus:

- `img.src`
- `img.srcset`
- `source.srcset`

gebildet werden.

Innerhalb von `picture` werden die `source`-Elemente entsprechend ihrer Position und Eignung berücksichtigt.

### 7.5 Image Source Selection

Die Auswahl eines Bildkandidaten ist kein rein syntaktischer Vorgang.

Der User Agent berücksichtigt unter anderem:

- unterstützte Formate
- Media Conditions
- Device Pixel Ratio
- Source Size
- Kandidatendichten
- aktuelle Umgebung

### 7.6 DOM Mutations

Änderungen an relevanten Attributen oder an der Struktur können eine erneute Bildquellenauswahl auslösen.

Dies betrifft insbesondere:

- `src`
- `srcset`
- `sizes`
- `media`
- `type`
- Änderungen innerhalb von `picture`

### 7.7 Environment Changes

Ändert sich die Umgebung, kann eine bereits ausgewählte Bildquelle neu bewertet werden.

Relevante Änderungen können beispielsweise durch:

- Änderung des Viewports
- Änderung der Display Density
- Media-Query-Änderungen

entstehen.

---

## 8. Accessibility: Bilder

### 8.1 Grundsatz

Die Accessibility-Anforderungen für Bilder sind kontextabhängig.

Ein universeller `alt`-Text kann deshalb nicht für alle Verwendungsarten vorausgesetzt werden.

### 8.2 WHATWG-Fallgruppen

Der Standard behandelt insbesondere:

1. Link oder Button, der nur aus einem Bild besteht.
2. Phrase oder Paragraph mit grafischer Repräsentation.
3. Charts, Diagramme, Graphen, Karten und Illustrationen.
4. Kurze Labels, Icons und Logos.
5. Text, der als Grafik dargestellt wird.
6. Grafische Darstellung von umgebendem Text.
7. Ancillary Images.
8. rein dekorative Bilder.
9. Bildgruppen ohne Links.
10. Bildgruppen mit Links.
11. Bilder als zentraler Bestandteil des Inhalts.
12. Bilder, die nicht für den Nutzer bestimmt sind.
13. E-Mails oder private Dokumente mit bekanntem Empfänger.
14. Anforderungen an Markup Generatoren.
15. Anforderungen an Conformance Checker.

### 8.3 `alt` ist nicht nur eine Beschreibung

Der Alternativtext muss nicht zwingend eine visuelle Beschreibung des Bildes sein.

Er soll die für den jeweiligen Kontext relevante Funktion beziehungsweise Information des Bildes vermitteln.

### 8.4 Accessibility-Zuordnung

WHATWG verweist bei den Elementdefinitionen auf:

- Accessibility Considerations für Autoren
- Accessibility Considerations für Implementierer
- ARIA in HTML
- HTML Accessibility API Mappings

Eine vollständige Accessibility-Mapping-Matrix wird deshalb nicht innerhalb dieser Datei erfunden.

---

## 9. Detailprüfung: `iframe`

### 9.1 Semantische Rolle

`iframe` repräsentiert seinen Content Navigable.

Es erzeugt damit einen eingebetteten Browsing-/Navigationskontext.

### 9.2 Content Categories

`iframe` ist:

- Flow content
- Phrasing content
- Embedded content
- Interactive content
- Palpable content

### 9.3 Context

Wo Embedded Content erwartet wird.

### 9.4 Content Model

`iframe` hat:

- Nothing

### 9.5 Tag Omission

Keine Tag-Auslassung.

### 9.6 Content Attributes

Neben Global Attributes:

- `src`
- `srcdoc`
- `name`
- `sandbox`
- `allow`
- `allowfullscreen`
- `width`
- `height`
- `referrerpolicy`
- `loading`

### 9.7 `src`

`src` gibt die URL der Seite an, die der Content Navigable enthalten soll.

Wenn `itemprop` angegeben ist, muss auch `src` angegeben werden.

### 9.8 `srcdoc`

`srcdoc` enthält den HTML-Inhalt des eingebetteten Dokuments.

Das daraus erzeugte Dokument erhält die spezielle URL:

`about:srcdoc`

### 9.9 `sandbox`

`sandbox` steuert Einschränkungen für den eingebetteten Kontext.

Es ist ein Token-basiertes Attribut mit einer eigenen, umfangreichen Permissions-/Sandbox-Semantik.

### 9.10 `allow`

`allow` wirkt über Permissions Policy.

Es kann Features für den eingebetteten Kontext freischalten, soweit die übergeordneten Permissions-Policy-Regeln dies überhaupt zulassen.

### 9.11 `allowfullscreen`

`allowfullscreen` ist ein Boolean Attribute.

Es ermöglicht unter den definierten Bedingungen die Verwendung des Fullscreen-Features im eingebetteten Kontext.

### 9.12 Permissions Policy

`allow` und `allowfullscreen` können keine Berechtigung über eine bereits bestehende Einschränkung des Elternkontexts hinaus erteilen.

Die Attribute beeinflussen die Permissions Policy des aktiven Dokuments des Content Navigable.

Änderungen wirken insbesondere bei Navigation des Content Navigable.

### 9.13 Fallback

`iframe` besitzt keinen Fallback Content im Sinne von `object`.

Das Element erzeugt einen neuen Child Navigable.

### 9.14 Loading

`loading` ermöglicht Lazy Loading des eingebetteten Kontexts unter den dafür geltenden Regeln.

### 9.15 Sanitization

Sanitization:

- Unsafe

### 9.16 DOM Interface

`HTMLIFrameElement`

Wichtige Mitglieder:

- `src`
- `srcdoc`
- `name`
- `sandbox`
- `allow`
- `allowFullscreen`
- `width`
- `height`
- `referrerPolicy`
- `loading`
- `contentDocument`
- `contentWindow`
- `getSVGDocument()`

---

## 10. Detailprüfung: `embed`

### 10.1 Semantische Rolle

`embed` stellt einen Integrationspunkt für:

- externe Anwendungen
- interaktive Inhalte
- eingebettete Ressourcen

dar.

### 10.2 Content Categories

`embed` ist:

- Flow content
- Phrasing content
- Embedded content
- Interactive content
- Palpable content

### 10.3 Context

Wo Embedded Content erwartet wird.

### 10.4 Content Model

Nothing.

### 10.5 Tag Omission

Kein End-Tag.

### 10.6 Content Attributes

Neben Global Attributes:

- `src`
- `type`
- `width`
- `height`

sowie die von der Definition berücksichtigten sonstigen nicht-namespaced Attribute.

### 10.7 `src`

`src` gibt die URL der einzubettenden Ressource an.

Wenn `itemprop` vorhanden ist, muss `src` vorhanden sein.

### 10.8 `type`

`type` gibt gegebenenfalls den MIME-Typ an.

Der Wert muss ein gültiger MIME-Type-String sein.

Wenn sowohl `type` als auch `src` vorhanden sind, muss der angegebene Typ mit den expliziten Content-Type-Metadaten der Ressource übereinstimmen.

### 10.9 Aktivierung

Ein `embed` kann abhängig von:

- Dokumentstatus
- `src`
- `type`
- Rendering
- Media-Ancestor
- `object`-Fallback-Zustand

potenziell aktiv sein.

### 10.10 Sanitization

Sanitization:

- Unsafe

### 10.11 DOM Interface

`HTMLEmbedElement`

Wichtige Mitglieder:

- `src`
- `type`
- `width`
- `height`
- `getSVGDocument()`

---

## 11. Detailprüfung: `object`

### 11.1 Semantische Rolle

`object` kann eine externe Ressource repräsentieren.

Abhängig vom Ressourcentyp kann sie:

- als Bild behandelt werden
- einen Child Navigable darstellen
- oder auf Fallback Content zurückfallen

### 11.2 Content Categories

`object` ist:

- Flow content
- Phrasing content
- Embedded content
- Listed form-associated element
- Palpable content

### 11.3 Context

Wo Embedded Content erwartet wird.

### 11.4 Content Model

Transparent.

### 11.5 Tag Omission

Keine Tag-Auslassung.

### 11.6 Content Attributes

Neben Global Attributes:

- `data`
- `type`
- `name`
- `form`
- `width`
- `height`

### 11.7 `data`

`data` gibt die URL der Ressource an.

Das Attribut muss vorhanden sein und eine gültige nichtleere URL enthalten.

### 11.8 `type`

Wenn vorhanden:

- gültiger MIME-Type-String.

### 11.9 `name`

`name` kann den Content Navigable benennen.

### 11.10 Fallback Content

Wenn die Ressource nicht unterstützt oder nicht erfolgreich dargestellt werden kann, kann `object` seine Kinder als Fallback Content repräsentieren.

Das unterscheidet `object` wesentlich von `iframe`.

### 11.11 Dynamische Neubestimmung

WHATWG definiert ein umfangreiches Verarbeitungsmodell, das bei Änderungen unter anderem an:

- `data`
- `type`
- `classid`
- Dokumentstatus
- Renderingstatus
- Ancestor-`object`-Fallback

die Repräsentation des Elements neu bestimmen kann.

### 11.12 Form Association

`object` ist form-associated.

Das DOM Interface stellt deshalb unter anderem:

- `form`
- `willValidate`
- `validity`
- `validationMessage`
- `checkValidity()`
- `reportValidity()`
- `setCustomValidity()`

bereit.

### 11.13 Sanitization

Sanitization:

- Unsafe

### 11.14 DOM Interface

`HTMLObjectElement`

Wichtige Mitglieder:

- `data`
- `type`
- `name`
- `form`
- `width`
- `height`
- `contentDocument`
- `contentWindow`
- `getSVGDocument()`
- Constraint-Validation-API

---

## 12. Detailprüfung: `video`

### 12.1 Semantische Rolle

`video` dient zur Wiedergabe von:

- Video
- Filmen
- gegebenenfalls Audio mit visueller Wiedergabe

### 12.2 Content Categories

`video` ist:

- Flow content
- Phrasing content
- Embedded content
- Palpable content

Zusätzlich bei vorhandenem `controls`:

- Interactive content

### 12.3 Context

Wo Embedded Content erwartet wird.

### 12.4 Content Model

Wenn `src` vorhanden ist:

- null oder mehr `track`
- danach transparent
- aber keine Media-Element-Nachfahren

Wenn `src` nicht vorhanden ist:

- null oder mehr `source`
- danach null oder mehr `track`
- danach transparent
- aber keine Media-Element-Nachfahren

### 12.5 Tag Omission

Keine Tag-Auslassung.

### 12.6 Content Attributes

Neben Global Attributes:

- `src`
- `crossorigin`
- `poster`
- `preload`
- `autoplay`
- `playsinline`
- `loop`
- `muted`
- `controls`
- `loading`
- `width`
- `height`

### 12.7 `poster`

`poster` gibt eine Bildressource an, die angezeigt werden kann, wenn keine Videodaten verfügbar sind.

Die Ressource wird unter den Lazy-Loading-Regeln ebenfalls verzögert geladen, wenn `loading="lazy"` greift.

### 12.8 `playsinline`

`playsinline` ist ein Boolean Attribute.

Es dient als Hinweis, dass Video innerhalb des vorgesehenen Wiedergabebereichs abgespielt werden soll.

Das Fehlen des Attributes bedeutet nicht zwingend, dass Fullscreen-Wiedergabe erfolgen muss.

### 12.9 Fallback Content

Inhalt innerhalb von `video` kann als Legacy-Fallback für nicht unterstützende User Agents dienen.

Dieser Inhalt ist nicht als eigentliche Accessibility-Lösung gedacht.

Für Accessibility sind insbesondere:

- Captions
- Audio Descriptions
- Sign Language Tracks
- Transcripts
- `track`
- WebVTT

relevant.

### 12.10 Dimensionen

`video` unterstützt:

- `width`
- `height`

und stellt zusätzlich:

- `videoWidth`
- `videoHeight`

bereit.

### 12.11 Media Interface

`video` ist ein Media Element und erbt seine zentrale Medienfunktionalität von:

`HTMLMediaElement`

### 12.12 Sanitization

Sanitization:

- Uncategorized

### 12.13 DOM Interface

`HTMLVideoElement`

Zusätzliche Mitglieder:

- `width`
- `height`
- `videoWidth`
- `videoHeight`
- `poster`
- `playsInline`

---

## 13. Detailprüfung: `audio`

### 13.1 Semantische Rolle

`audio` repräsentiert einen:

- Sound
- Audio Stream

### 13.2 Content Categories

`audio` ist:

- Flow content
- Phrasing content
- Embedded content

Bei vorhandenem `controls`:

- Interactive content
- Palpable content

### 13.3 Context

Wo Embedded Content erwartet wird.

### 13.4 Content Model

Mit `src`:

- `track*`
- danach transparent
- keine Media-Element-Nachfahren

Ohne `src`:

- `source*`
- `track*`
- danach transparent
- keine Media-Element-Nachfahren

### 13.5 Tag Omission

Keine Tag-Auslassung.

### 13.6 Content Attributes

Neben Global Attributes:

- `src`
- `crossorigin`
- `preload`
- `autoplay`
- `loop`
- `muted`
- `controls`
- `loading`

### 13.7 Media Processing

`audio` verwendet die gemeinsame Media-Element-Infrastruktur.

Es kann unter anderem:

- Media Resources laden
- Media Provider Objects verwenden
- Playback steuern
- Seeking durchführen
- Tracks verwalten
- Events auslösen

### 13.8 Unterschied zu `video`

Beide sind Media Elements.

Der zentrale konzeptionelle Unterschied besteht darin, dass `video` einen visuellen Playback-Bereich besitzt, während `audio` keinen visuellen Videobereich für die Media-Daten bereitstellt.

### 13.9 Sanitization

Sanitization:

- Uncategorized

### 13.10 DOM Interface

`HTMLAudioElement`

Es basiert auf:

`HTMLMediaElement`

---

## 14. Detailprüfung: `track`

### 14.1 Semantische Rolle

`track` ermöglicht explizite externe zeitgesteuerte Textspuren für Media Elements.

`track` repräsentiert selbst nichts.

### 14.2 Content Categories

Keine.

### 14.3 Context

Als Kind eines Media Elements:

- vor Flow Content.

### 14.4 Content Model

Nothing.

### 14.5 Tag Omission

Kein End-Tag.

### 14.6 Content Attributes

Neben Global Attributes:

- `kind`
- `src`
- `srclang`
- `label`
- `default`

### 14.7 `kind`

`kind` ist ein enumerated attribute.

Die WHATWG-Definition umfasst unter anderem Zustände für:

- subtitles
- captions
- descriptions
- chapters
- metadata

### 14.8 Subtitles

Subtitles stellen Transkription oder Übersetzung von Dialogen bereit und sind insbesondere für Situationen gedacht, in denen Ton vorhanden, aber nicht verstanden wird.

### 14.9 Captions

Captions umfassen neben Dialogen auch:

- relevante Sound Effects
- musikalische Hinweise
- weitere relevante Audioinformationen

und sind insbesondere für Situationen relevant, in denen Audio nicht verfügbar oder nicht ausreichend wahrnehmbar ist.

### 14.10 `srclang`

`srclang` gibt die Sprache der Textspur an.

### 14.11 `label`

`label` liefert die für Nutzer sichtbare Bezeichnung der Textspur.

### 14.12 `default`

`default` ist ein Boolean Attribute und kennzeichnet eine Textspur, die verwendet werden soll, wenn keine andere Textspur geeigneter ausgewählt wird.

### 14.13 Sanitization

Sanitization:

- Uncategorized

### 14.14 DOM Interface

`HTMLTrackElement`

---

## 15. Media Elements – gemeinsame Infrastruktur

### 15.1 Abgrenzung

§4.8.11 ist keine zusätzliche HTML-Elementfamilie.

Die dort beschriebenen Media Elements sind:

- `audio`
- `video`

### 15.2 Gemeinsame Attribute

Die gemeinsame Media-Infrastruktur behandelt insbesondere:

- `src`
- `crossorigin`
- `preload`
- `autoplay`
- `loop`
- `muted`
- `controls`
- `loading`

`video` besitzt darüber hinaus eigene Attribute wie:

- `poster`
- `playsinline`
- `width`
- `height`

### 15.3 Media Provider Objects

Media Resources können über URL-basierte Ressourcen oder Media Provider Objects bereitgestellt werden.

WHATWG behandelt insbesondere:

- `MediaStream`
- `MediaSource`
- `Blob`

als mögliche Media Provider Objects.

### 15.4 `srcObject`

`srcObject` ermöglicht die Zuordnung eines Media Provider Objects zu einem Media Element.

### 15.5 `currentSrc`

`currentSrc` repräsentiert die aktuell verwendete Media Resource URL.

### 15.6 `canPlayType()`

`canPlayType(type)` liefert eine Einschätzung, ob ein User Agent eine bestimmte Media Resource wiedergeben kann.

Mögliche Ergebnisse sind:

- leerer String
- `maybe`
- `probably`

### 15.7 Error Codes

`MediaError` kennt vier standardisierte Fehlercodes:

- `MEDIA_ERR_ABORTED`
- `MEDIA_ERR_NETWORK`
- `MEDIA_ERR_DECODE`
- `MEDIA_ERR_SRC_NOT_SUPPORTED`

### 15.8 Network States

Die Media-Element-Infrastruktur besitzt Zustände für den Netzwerk-/Ladezustand.

Diese Zustände steuern unter anderem:

- Laden
- Ressourcenanforderung
- Fehler
- Leerlauf
- laufende Requests

### 15.9 Ready States

Die Media API verwendet Ready States, unter anderem:

- `HAVE_NOTHING`
- `HAVE_METADATA`
- `HAVE_CURRENT_DATA`
- `HAVE_FUTURE_DATA`
- `HAVE_ENOUGH_DATA`

Diese Zustände beschreiben, wie weit Media Data verfügbar ist.

### 15.10 Playback

Die Media-Infrastruktur behandelt:

- Play
- Pause
- Current Playback Position
- Playback Rate
- Default Playback Rate
- Volume
- Muting
- Looping
- Autoplay

### 15.11 Seeking

Seeking verändert die aktuelle Wiedergabeposition.

Die Verarbeitung berücksichtigt:

- seekable ranges
- Media Resource
- aktuelle Wiedergabeposition
- Seeking State
- entsprechende Events

### 15.12 Multiple Media Tracks

Media Resources können mehrere:

- Audio Tracks
- Video Tracks

enthalten.

Die API stellt hierfür Track-Listen bereit.

### 15.13 AudioTrackList

`AudioTrackList` repräsentiert die Audio Tracks eines Media Elements.

### 15.14 VideoTrackList

`VideoTrackList` repräsentiert die Video Tracks eines Media Elements.

### 15.15 Track Selection

Audio Tracks können aktiviert beziehungsweise deaktiviert werden.

Bei Video Tracks ist die Auswahl restriktiver:

- höchstens ein Video Track ist gleichzeitig ausgewählt.

### 15.16 Timed Text Tracks

Timed Text Tracks bilden ein eigenständiges Untermodell.

Es umfasst:

- Text Track Model
- Text Track Cues
- Text Track Modes
- in-band Tracks
- out-of-band Tracks
- Cue-Verarbeitung
- Text Track API
- Events

### 15.17 In-band Tracks

In-band Text Tracks stammen aus der Media Resource selbst.

### 15.18 Out-of-band Tracks

Out-of-band Text Tracks werden insbesondere über `track`-Elemente bereitgestellt.

### 15.19 Text Track API

Das Text Track API stellt Objekte und Methoden zur Verwaltung von:

- Text Tracks
- Cues
- Cue-Zuständen
- Track Modes

bereit.

### 15.20 Metadata Text Tracks

Metadata Tracks können maschinenlesbare beziehungsweise anwendungsbezogene zeitabhängige Informationen transportieren.

Die Spezifikation enthält dafür eigene Best Practices.

### 15.21 Track Kind Through URL

WHATWG definiert Regeln, mit denen ein Track-Typ anhand einer URL beziehungsweise entsprechender Ressourceneigenschaften bestimmt werden kann.

### 15.22 Media User Interface

User Agents können Benutzeroberflächen für:

- Playback
- Lautstärke
- Captions
- Audio Description
- weitere Media-Funktionen

bereitstellen.

Die konkrete UI ist grundsätzlich implementationsabhängig.

### 15.23 Time Ranges

Time Ranges beschreiben Bereiche innerhalb der Media Timeline.

Sie werden unter anderem für:

- buffered
- seekable
- played

verwendet.

### 15.24 `TrackEvent`

`TrackEvent` ist das Ereignisobjekt für bestimmte Track-bezogene Events.

### 15.25 Events

Die Media-Spezifikation definiert zahlreiche Events für:

- Laden
- Metadaten
- Playback
- Pause
- Seeking
- Progress
- Errors
- Tracks
- Zeitänderungen

Diese Events sind API-/Verarbeitungskonzepte und keine zusätzlichen HTML-Elemente.

### 15.26 Security and Privacy

Media kann:

- Netzwerkzugriffe
- Cross-Origin Requests
- Medieninformationen
- Timing
- Benutzerinteraktion

betreffen.

Die WHATWG-Spezifikation behandelt hierfür eigene Security- und Privacy-Aspekte.

### 15.27 Authoring Best Practices

WHATWG behandelt unter anderem:

- Ressourcenfreigabe
- Umgang mit Media Element References
- Playback Rate
- Geräte-/Ressourcenbeschränkungen
- Nutzung von `srcObject`
- Entfernung beziehungsweise Freigabe von Media Resources

### 15.28 Implementer Best Practices

Auch für User-Agent-Implementierungen bestehen eigene Empfehlungen und Anforderungen.

Diese sind nicht als zusätzliche HTML-Features zu inventarisieren.

---

## 16. Image Maps

### 16.1 Grundmodell

Eine Image Map verbindet:

- ein `img`
- ein `map`
- `area`-Elemente

mit geometrisch definierten Bereichen.

Die Bereiche können Hyperlinks repräsentieren.

### 16.2 Detailprüfung: `map`

#### Content Categories

`map` ist:

- Flow content
- Phrasing content
- Palpable content

#### Context

Wo Phrasing Content erwartet wird.

#### Content Model

Transparent.

#### Tag Omission

Keine Tag-Auslassung.

#### Content Attributes

Neben Global Attributes:

- `name`

#### `name`

`name`:

- muss vorhanden sein
- darf nicht leer sein
- darf keine ASCII Whitespace enthalten
- muss im Tree eindeutig sein

Wenn `id` ebenfalls vorhanden ist, müssen `name` und `id` denselben Wert besitzen.

#### DOM Interface

`HTMLMapElement`

Zusätzlich:

- `areas`

liefert eine `HTMLCollection` der enthaltenen `area`-Elemente.

#### Sanitization

- Uncategorized

### 16.3 Detailprüfung: `area`

#### Content Categories

`area` ist:

- Flow content
- Phrasing content

#### Context

Wo Phrasing Content erwartet wird, aber nur bei vorhandenem `map`-Ancestor.

#### Content Model

Nothing.

#### Tag Omission

Kein End-Tag.

#### Content Attributes

Neben Global Attributes:

- `alt`
- `coords`
- `shape`
- `href`
- `target`
- `download`
- `ping`
- `rel`
- `referrerpolicy`
- `hreflang`
- `type`

#### Hyperlink State

Wenn `href` vorhanden ist:

- `area` repräsentiert einen Hyperlink.
- `alt` muss vorhanden sein.

Wenn `href` fehlt:

- der Bereich ist nicht auswählbar.
- `alt` muss entfallen.

#### `shape`

`shape` ist ein enumerated attribute.

Konforme Zustände:

- `circle`
- `default`
- `poly`
- `rect`

Nicht konforme historische Synonyme umfassen unter anderem:

- `circ`
- `polygon`
- `rectangle`

Der Missing Value Default und Invalid Value Default ist:

- Rectangle State

#### `coords`

`coords` definiert die geometrischen Koordinaten.

Je nach Shape gelten unterschiedliche Anforderungen.

#### Circle

- drei Integer
- Mittelpunkt X
- Mittelpunkt Y
- Radius
- Radius nicht negativ

#### Default

- keine Koordinaten erforderlich
- gesamte Bildfläche

#### Polygon

- mindestens sechs Integer
- gerade Anzahl
- Koordinatenpaare bilden die Polygonpunkte

#### Rectangle

- genau vier Integer
- linker oberer Punkt
- rechter unterer Punkt

#### Hyperlink Attributes

Ohne `href` müssen folgende Attribute entfallen:

- `target`
- `download`
- `ping`
- `rel`
- `referrerpolicy`
- `hreflang`
- `type`

#### Sanitization

`area` ist:

- Uncategorized

mit `href` als:

- navigating URL attribute

#### DOM Interface

`HTMLAreaElement`

und Einbindung in:

- `HyperlinkElementUtils`
- `HTMLHyperlinkElementUtils`

---

## 17. Image-Map-Processing

### 17.1 Zuordnung über `usemap`

`img[usemap]` wird anhand des `usemap`-Werts einer `map` zugeordnet.

Der Wert wird als Hash-Name-Referenz verarbeitet.

### 17.2 Area Collection

Nach erfolgreicher Zuordnung werden alle `area`-Nachfahren des `map` gesammelt.

### 17.3 Textdarstellung

Wenn der User Agent die Textrepräsentation des Bildes darstellen will:

- nicht verlinkte `area`-Elemente werden entfernt.
- leere beziehungsweise fehlende `alt`-Texte werden unter den definierten Bedingungen berücksichtigt.
- verbleibende Hyperlinks werden zusammen mit dem Bildtext zugänglich gemacht.

### 17.4 Visuelle Darstellung

Wenn das Bild dargestellt und interaktiv verwendet wird:

- werden die `area`-Geometrien in Layern angeordnet.
- die Reihenfolge erfolgt in umgekehrter Tree Order.
- spätere `area`-Elemente liegen entsprechend unter den früheren.

### 17.5 Shape Processing

Für jede `area` wird:

1. der Shape State bestimmt,
2. `coords` geparst,
3. eine Mindestanzahl von Koordinaten geprüft,
4. überzählige Werte verworfen,
5. bei Rechtecken gegebenenfalls Koordinaten vertauscht,
6. bei Kreisen ein nichtpositiver Radius als leer behandelt,
7. die endgültige Geometrie erzeugt.

### 17.6 Layering

Die geometrischen Flächen können sich überlappen.

Der User Agent muss die Interaktion zunächst dem obersten passenden Bereich zuordnen.

### 17.7 Koordinatensystem

Die Koordinaten werden in CSS-Pixeln relativ zum Bild interpretiert.

Historische Besonderheiten gelten für die Skalierung des dargestellten Bildes.

Browser Zoom und CSS-/SVG-Transforms verändern die grundlegende Koordinateninterpretation nicht nach dem von WHATWG beschriebenen Modell.

### 17.8 Live Image Maps

Image Maps sind live.

Wenn der DOM verändert wird, muss der User Agent so handeln, als ob die relevanten Image-Map-Algorithmen erneut ausgeführt worden wären.

---

## 18. MathML-Integration

### 18.1 Abgrenzung

MathML ist kein HTML-Elementinventar.

§4.8.15 beschreibt die Integration von MathML in HTML.

Die Semantik der MathML-Elemente stammt aus MathML und den dafür zuständigen Spezifikationen.

### 18.2 `math`

Das MathML-`math`-Element wird für die Zwecke der HTML-Content-Models als:

- Embedded content
- Phrasing content
- Flow content
- Palpable content

behandelt.

### 18.3 HTML innerhalb von MathML

Für bestimmte MathML-Strukturen gelten spezielle Integrationsregeln.

Insbesondere können HTML-Elemente innerhalb von MathML-Kontexten auftreten, soweit die entsprechenden MathML-Regeln dies vorsehen.

### 18.4 `annotation-xml`

Wenn `annotation-xml` Elemente aus dem HTML Namespace enthält, müssen diese HTML-Elemente Flow Content sein.

### 18.5 MathML Token Elements

MathML Token Elements wie:

- `mi`
- `mo`
- `mn`
- `ms`
- `mtext`

können unter den von WHATWG definierten Bedingungen HTML-Phrasing-Content enthalten.

### 18.6 Ungültiger Text

Wenn in einem MathML-Element, dessen Content Model keinen direkten Text zulässt, Text außerhalb von Inter-Element Whitespace vorkommt, müssen User Agents für Layout und Rendering so tun, als wäre dieser Text in ein MathML-`mtext` eingeschlossen.

Der Quellinhalt bleibt dabei trotzdem nicht konform.

### 18.7 Fehlerhafte MathML-Strukturen

Wenn MathML-Inhalt nicht dem vorgesehenen Content Model entspricht, müssen User Agents für Layout und Rendering so verfahren, als wäre die fehlerhafte Struktur durch ein geeignetes `merror` ersetzt worden.

### 18.8 ZE-WebLab-Ebene

MathML:

- wird nicht als HTML-Tag gezählt.
- wird als Fremdsprachen-/Integrationsfamilie dokumentiert.
- benötigt später eine eigene MathML-Referenz, wenn die MathML-Semantik vollständig erschlossen werden soll.

---

## 19. SVG-Integration

### 19.1 Abgrenzung

SVG ist keine HTML-Elementfamilie.

§4.8.16 definiert die Integration von SVG in HTML.

Die eigentliche SVG-Semantik stammt aus SVG 2 und den dafür zuständigen Spezifikationen.

### 19.2 SVG `svg`

Das SVG-`svg`-Element zählt für HTML-Content-Model-Zwecke zu:

- Embedded content
- Phrasing content
- Flow content
- Palpable content

### 19.3 `foreignObject`

Wenn SVG `foreignObject` HTML-Namespace-Elemente enthält, müssen diese Flow Content sein.

### 19.4 SVG `title`

Für das SVG-`title`-Element innerhalb eines HTML-Dokuments gilt ein eingeschränktes Content Model.

WHATWG legt dafür fest, dass dessen Inhalt Phrasing Content ist.

### 19.5 `getSVGDocument()`

`iframe`, `embed` und `object` können über:

`getSVGDocument()`

auf ein eingebettetes SVG-Dokument zugreifen, wenn die von WHATWG beschriebenen Bedingungen erfüllt sind.

Die Methode liefert insbesondere dann ein Dokument, wenn das eingebettete Dokument im Rahmen des XML-/SVG-Ladevorgangs als `image/svg+xml` erzeugt wurde.

### 19.6 ZE-WebLab-Ebene

SVG:

- wird nicht als HTML-Element gezählt.
- wird als Integrations-/Fremdsprachenelement dokumentiert.
- muss bei einer vollständigen SVG-Referenz separat behandelt werden.

---

## 20. Dimension Attributes

### 20.1 Abgrenzung

§4.8.17 ist kein HTML-Element.

Es definiert gemeinsame Regeln für Dimension Attributes.

### 20.2 Betroffene Elemente

WHATWG behandelt insbesondere:

- `img`
- `iframe`
- `embed`
- `object`
- `video`
- `source` unter `picture`
- `input`, wenn es sich um einen Image Button handelt

### 20.3 `width`

`width` gibt die horizontale Dimension des visuellen Inhalts an.

### 20.4 `height`

`height` gibt die vertikale Dimension des visuellen Inhalts an.

### 20.5 Einheit

Die HTML-Dimension-Attribute werden in CSS-Pixeln interpretiert.

### 20.6 Zweck

Dimension Attributes ermöglichen User Agents insbesondere:

- frühzeitige Dimensionsbestimmung
- Seitenverhältnisbestimmung
- Layout-Reservierung
- stabileres Rendering

### 20.7 Source-Dimensionen

`source` kann innerhalb von `picture` ebenfalls Dimension Attributes besitzen.

Das `img`-Element kann diese Dimensionen im Rahmen des Dimension-Source-Modells berücksichtigen.

### 20.8 DOM Reflection

Die konkreten DOM-Interfaces reflektieren `width` und `height` entsprechend den jeweiligen Elementdefinitionen.

Die Typen und Reflection-Regeln unterscheiden sich je nach Element.

---

## 21. Sanitization

### 21.1 Grundsatz

Sanitization ist eine eigene Informationsebene und darf nicht mit:

- HTML-Konformität
- Browser-Support
- Sicherheitsgarantie
- Accessibility

gleichgesetzt werden.

### 21.2 Sanitization-Status der Elemente

| Element | WHATWG Sanitization |
|---|---|
| `picture` | Uncategorized |
| `source` | Uncategorized |
| `img` | Uncategorized |
| `iframe` | Unsafe |
| `embed` | Unsafe |
| `object` | Unsafe |
| `video` | Uncategorized |
| `audio` | Uncategorized |
| `track` | Uncategorized |
| `map` | Uncategorized |
| `area` | Uncategorized |

### 21.3 Navigating URL Attributes

Bei `area` wird `href` zusätzlich als:

- navigating URL attribute

geführt.

Das ist eine gesonderte Sanitization-Information.

### 21.4 Sicherheitsrelevante Interpretation

Insbesondere `iframe`, `embed` und `object` können externe oder aktive Inhalte integrieren.

Der Sanitization-Status `Unsafe` ist daher nicht mit der Aussage gleichzusetzen, dass jede Verwendung des Elements unzulässig ist.

Er gehört vielmehr in das von WHATWG definierte Sanitization-Modell.

---

## 22. DOM Interfaces

| Element | DOM Interface |
|---|---|
| `picture` | `HTMLPictureElement` |
| `source` | `HTMLSourceElement` |
| `img` | `HTMLImageElement` |
| `iframe` | `HTMLIFrameElement` |
| `embed` | `HTMLEmbedElement` |
| `object` | `HTMLObjectElement` |
| `video` | `HTMLVideoElement` |
| `audio` | `HTMLAudioElement` |
| `track` | `HTMLTrackElement` |
| `map` | `HTMLMapElement` |
| `area` | `HTMLAreaElement` |

Zusätzliche zentrale APIs/Konzepte dieses Bereichs sind:

- `HTMLMediaElement`
- `AudioTrackList`
- `VideoTrackList`
- Text Track API
- `TrackEvent`
- `TimeRanges`
- `MediaError`

Diese Interfaces und Objekte sind **keine zusätzlichen HTML-Elemente**.

---

## 23. Normative Sonderregeln

### 23.1 `picture` benötigt `img`

Das `picture`-Content-Model verlangt ein `img`-Element nach den vorgesehenen `source`-Elementen.

### 23.2 `source` ist kontextabhängig

`source` hat abhängig vom Parent zwei unterschiedliche normative Funktionsmodelle:

- `picture`
- `audio` / `video`

Diese Kontexte dürfen nicht vermischt werden.

### 23.3 `source[src]` ist in `picture` bedeutungslos

Innerhalb von `picture` ist `src` nicht die relevante Bildquellenbeschreibung.

Dafür wird `srcset` verwendet.

### 23.4 `img` benötigt `src` oder `srcset`

Mindestens eines von:

- `src`
- `srcset`

muss vorhanden sein.

### 23.5 `alt` ist kontextabhängig

Die Konformität und der konkrete Inhalt von `alt` müssen anhand des tatsächlichen Bildzwecks beurteilt werden.

### 23.6 `ismap`

`ismap` darf nicht frei auf jedem `img` verwendet werden.

Die Spezifikation bindet das Attribut an einen `a`-Ancestor mit `href`.

### 23.7 `controls` auf `img`

`controls` darf nicht mit einem fehlenden oder leeren `alt` kombiniert werden.

### 23.8 `iframe` ist kein Fallback-Container

`iframe` erzeugt einen Content Navigable und fällt nicht wie `object` auf seine Kinder zurück.

### 23.9 `object` besitzt Fallback Content

`object` kann bei nicht verwendbarer Ressource seine Kinder als Fallback Content repräsentieren.

### 23.10 `embed` kann abhängig vom Zustand nichts repräsentieren

Ein `embed` kann unter bestimmten Bedingungen:

- nichts repräsentieren
- keinen Plugin-Inhalt bereitstellen

### 23.11 Media Content Models

Bei `audio` und `video` hängt die zulässige Struktur unter anderem davon ab, ob `src` direkt am Media Element vorhanden ist.

### 23.12 Keine verschachtelten Media Elements

Das transparente Content Model von `audio` und `video` ist ausdrücklich mit der Einschränkung versehen, dass keine Media-Element-Nachfahren enthalten sein dürfen.

### 23.13 `track`

`track` ist selbst nicht darstellender Inhalt.

Es stellt Daten für das Media-Text-Track-System bereit.

### 23.14 Image Maps

`area` ist ohne `map`-Ancestor nicht konform.

### 23.15 `area[href]`

Wenn `href` vorhanden ist:

- `area` repräsentiert einen Hyperlink.
- `alt` ist erforderlich.

### 23.16 `area` ohne `href`

Ohne `href`:

- keine auswählbare Fläche
- `alt` muss fehlen.

### 23.17 Fremdsprachen

MathML und SVG sind Integrationskonzepte und keine HTML-Elemente.

---

## 24. Querverweise

| Thema | Relevanz |
|---|---|
| Content Categories | §3.2.5 und Definitionen der Embedded-Content-Elemente |
| Global Attributes | §3.2.6 |
| Embedded Content | §3.2.5.2.6 |
| Interactive Content | §3.2.5.2.7 |
| Links | §4.6 |
| Media Elements | §4.8.11 |
| Image Maps | §4.8.14 |
| MathML | §4.8.15 |
| SVG | §4.8.16 |
| Dimension Attributes | §4.8.17 |
| Fetch | Fetch Standard und HTML-Fetch-Integration |
| CORS | Fetch-/CORS-Infrastruktur |
| Referrer Policy | Referrer Policy |
| Permissions Policy | Permissions Policy |
| WebVTT | WebVTT |
| DOM | DOM Standard |
| URL | URL Standard |
| MIME Types | MIME Sniffing / MIME-Type-Infrastruktur |
| ARIA | ARIA in HTML |
| Accessibility API Mappings | HTML Accessibility API Mappings |
| CSS Media Queries | CSS-/Media-Query-Infrastruktur |
| Canvas | Canvas und `img`-Ressourcen |
| Forms | Form-associated Eigenschaften von `img` und `object` |

---

## 25. Feature-Ebenen

### 25.1 Elementebene

Als HTML-Elemente werden ausschließlich geführt:

- `picture`
- `source`
- `img`
- `iframe`
- `embed`
- `object`
- `video`
- `audio`
- `track`
- `map`
- `area`

### 25.2 Konzept-/Verarbeitungsebene

Nicht als Elemente geführt werden:

- Source Sets
- Image Candidates
- Image Selection
- Image Decoding
- Lazy Loading
- Media Resource Selection
- Media Tracks
- Text Tracks
- Image Maps
- Dimension Attributes
- MathML Integration
- SVG Integration

### 25.3 API-Ebene

Nicht als HTML-Elemente geführt werden:

- `HTMLMediaElement`
- `MediaError`
- `AudioTrackList`
- `VideoTrackList`
- `TimeRanges`
- `TrackEvent`
- Text Track APIs

### 25.4 Fremdsprachenelemente

MathML- und SVG-Elemente werden nicht in das HTML-Elementinventar aufgenommen.

---

## 26. Status / V1

### 26.1 WHATWG-Definition

Alle elf benannten HTML-Elemente dieses Bereichs sind in der aktuellen WHATWG HTML Living Standard definiert:

- `picture`
- `source`
- `img`
- `iframe`
- `embed`
- `object`
- `video`
- `audio`
- `track`
- `map`
- `area`

### 26.2 V1-Aufnahme

Für die V1-HTML-Referenz von ZE-WebLab werden alle elf Elemente aufgenommen.

**V1-Status:** aktuell definiert.

### 26.3 Konformität

„Aktuell definiert“ bedeutet nicht:

- dass jede beliebige Verwendung konform ist,
- dass jedes Attribut immer zulässig ist,
- dass jedes Content Model automatisch erfüllt ist,
- dass Sanitization unkritisch ist,
- dass Accessibility-Anforderungen erfüllt sind.

Konformität ist abhängig von:

- Kontext
- Content Model
- Content Categories
- Attributzuständen
- kontextabhängigen Attributregeln
- normativen Sonderregeln
- weiteren Querverweisen.

### 26.4 Browser-Support

Browser-Kompatibilität ist nicht Bestandteil des WHATWG-Status.

Die in der WHATWG-Seite eingeblendeten MDN-Kompatibilitätsinformationen werden deshalb nicht in den V1-Status übernommen.

Eine Browser-Support-Matrix wird separat recherchiert.

---

## 27. Offene bzw. separat zu bearbeitende Punkte

Die Detailprüfung von §4.8 ist abgeschlossen.

Folgende Themen bleiben bewusst eigene Referenzbereiche:

1. vollständiges globales Attributinventar,
2. vollständige elementbezogene Attributmatrix,
3. vollständige Fetch-/CORS-Referenz,
4. vollständige Permissions-Policy-Referenz,
5. vollständige Media-API-Referenz,
6. vollständige Text-Track-/WebVTT-Referenz,
7. vollständige Accessibility-Mappings,
8. vollständige ARIA-in-HTML-Referenz,
9. vollständige Bild-`alt`-Praxis als eigenständige Accessibility-Wissensbasis,
10. vollständige MathML-Referenz,
11. vollständige SVG-Referenz,
12. vollständige Image-Selection-/`srcset`-/`sizes`-Parsing-Referenz,
13. vollständige Lazy-Loading-Referenz,
14. vollständige Browser-Kompatibilitätsrecherche,
15. Rendering-Details außerhalb der HTML-spezifischen normativen Ebene.

Diese Punkte sind keine Lücken innerhalb der Elementinventarisierung von §4.8.

---

## 28. Recherchefazit

§4.8 „Embedded content“ ist deutlich mehr als eine Liste von Multimedia-Tags.

Der Bereich besteht aus mehreren miteinander verbundenen Ebenen:

### Bildfamilie

- `picture`
- `source`
- `img`

mit:

- Source Sets
- Responsive Images
- `srcset`
- `sizes`
- Image Selection
- Alternative Text
- Lazy Loading
- Decoding

### Externe Ressourcen und Dokumente

- `iframe`
- `embed`
- `object`

mit unterschiedlichen Modellen für:

- Content Navigables
- externe Ressourcen
- Fallback Content
- Sanitization
- Permissions Policy
- SVG-Integration

### Media

- `video`
- `audio`
- `track`

mit einer umfangreichen gemeinsamen Media-Infrastruktur:

- Resource Loading
- Playback
- Seeking
- Ready States
- Errors
- Tracks
- Text Tracks
- Events
- Time Ranges
- User Interface
- Security/Privacy

### Image Maps

- `map`
- `area`

mit:

- geometrischen Shapes
- Hyperlinks
- alternativen Texten
- Koordinatensystem
- Layering
- Processing Model

### Fremdsprachenintegration

- MathML
- SVG

Diese sind nicht Teil des HTML-Elementinventars, sondern eigene Integrationsfamilien.

### Gemeinsame Infrastruktur

- Dimension Attributes
- Fetch
- CORS
- Referrer Policy
- Permissions Policy
- DOM APIs
- Accessibility APIs
- WebVTT

Für ZE-WebLab ist deshalb insbesondere die Trennung zwischen **HTML-Element**, **Attribut**, **Content Category**, **Processing Model**, **API** und **Fremdsprachenintegration** wesentlich.

---

## 29. Quellen / Referenzen

### Primärquelle

WHATWG HTML Living Standard, §4.8 „Embedded content“, aktueller Stand 11. August 2026.

Relevante Primärbereiche:

- §4.8.1 `picture`
- §4.8.2 `source`
- §4.8.3 `img`
- §4.8.4 Images
- §4.8.5 `iframe`
- §4.8.6 `embed`
- §4.8.7 `object`
- §4.8.8 `video`
- §4.8.9 `audio`
- §4.8.10 `track`
- §4.8.11 Media elements
- §4.8.12 `map`
- §4.8.13 `area`
- §4.8.14 Image maps
- §4.8.15 MathML
- §4.8.16 SVG
- §4.8.17 Dimension attributes

### Ergänzende WHATWG-Infrastruktur

Für die fachliche Interpretation wurden außerdem die von §4.8 referenzierten WHATWG-Konzepte berücksichtigt, insbesondere:

- Content Categories
- Content Models
- Global Attributes
- URLs
- Fetch
- CORS Settings Attributes
- Referrer Policy
- Permissions Policy
- DOM Interfaces
- Media APIs

### Externe Quellen

Die WHATWG-Elementdefinitionen verweisen für Accessibility auf die einschlägigen W3C-/ARIA-Spezifikationen.

Diese externen Accessibility-Spezifikationen werden in dieser Datei nicht als Ersatz für die WHATWG-Primärquelle verwendet.

Browser-Kompatibilitätsinformationen wurden nicht als WHATWG-Status übernommen.

---

**Prüfstatus:** abgeschlossen für WHATWG §4.8 „Embedded content“ auf Ebene der HTML-Elemente, der zugehörigen Elementdefinitionen, relevanten Attribute, Content Categories, Contexts, Content Models, Tag-Omission-Regeln, Sanitization, DOM Interfaces, Accessibility-Verweise sowie der normativen Bild-, Media-, Image-Map-, MathML-, SVG- und Dimension-Attribute-Konzepte.

**V1-Elementinventar:** 11 HTML-Elemente.

**HTML-Elemente:** `picture`, `source`, `img`, `iframe`, `embed`, `object`, `video`, `audio`, `track`, `map`, `area`.

**Nicht als HTML-Elemente gezählt:** Images Processing Model, Media Elements Infrastructure, Image Maps, MathML Integration, SVG Integration, Dimension Attributes und die zugehörigen APIs.