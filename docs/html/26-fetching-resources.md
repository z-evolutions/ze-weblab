# ZE-WebLab – HTML-Referenz: Fetching Resources

## Arbeitsstand / Quellenstand

**Projekt:** ZE-WebLab

**Datei:** `docs/html/26-fetching-resources.md`

**Rechercheebene:** Zweite Rechercheebene – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Processing Model / Resource Fetching / Attribute Family / Integration Feature

**WHATWG-Bereich:** §2.5 „Fetching resources“

**Geprüfter WHATWG-Stand:** HTML Living Standard, 11. August 2026

**Prüfstatus:** vollständig recherchiert für §2.5 „Fetching resources“ und die darin enthaltenen Unterabschnitte 2.5.1–2.5.9.

Diese Datei dokumentiert die übergreifende Fetching-Systematik des HTML
Living Standard.

Sie behandelt insbesondere:

- Fetch-bezogene HTML-Infrastruktur
- CORS-bezogene Fetch-Verarbeitung
- Ermittlung des Ressourcentyps
- MIME-Type-Bestimmung
- Ermittlung von Character Encodings aus `meta`
- CORS Settings Attributes
- Referrer Policy Attributes
- Nonce Attributes
- Lazy Loading Attributes
- Blocking Attributes
- Fetch Priority Attributes
- Beziehungen zwischen HTML und Fetch
- Beziehungen zwischen HTML und MIME Sniffing
- Beziehungen zwischen HTML und Encoding
- Beziehungen zwischen HTML und Content Security Policy
- Beziehungen zwischen HTML und Referrer Policy
- Beziehungen zwischen HTML und Intersection Observer
- DOM-/IDL-Beziehungen der Fetch-bezogenen Attribute
- normative Processing Models

Die Datei behandelt **nicht** den vollständigen WHATWG Fetch Standard.

Die eigentliche allgemeine Fetch-Infrastruktur, Request- und Response-Datenmodelle,
Fetch-Schemata, Netzwerkverarbeitung, CORS-Protokoll und sonstige allgemeine
Fetch-Algorithmen werden im WHATWG Fetch Standard definiert und von HTML
verwendet.

---

## Quellenabgrenzung

### WHATWG HTML

Die HTML-Spezifikation beantwortet für diesen Themenbereich insbesondere:

> Welche HTML-spezifischen Regeln gelten für das Laden und Verarbeiten von
> Ressourcen und welche Attribute beeinflussen dieses Verhalten?

Der zentrale HTML-Bereich ist:

- §2.5 Fetching resources
  - §2.5.1 Terminology
  - §2.5.2 Determining the type of a resource
  - §2.5.3 Extracting character encodings from `meta` elements
  - §2.5.4 CORS settings attributes
  - §2.5.5 Referrer policy attributes
  - §2.5.6 Nonce attributes
  - §2.5.7 Lazy loading attributes
  - §2.5.8 Blocking attributes
  - §2.5.9 Fetch priority attributes

### ZE-WebLab

Das Repository beantwortet:

> Welche der übergreifenden Fetching-Konzepte wurden bereits in den
> Elementdateien bzw. anderen Feature-Familien elementbezogen dokumentiert?

Die vorhandene Elementreferenz behandelt beispielsweise:

- URL-Attribute
- `crossorigin`
- `referrerpolicy`
- `nonce`
- `loading`
- `fetchpriority`
- ressourcenbezogene Elementverarbeitung

Diese elementbezogenen Informationen werden hier nicht erneut als
Elementdefinitionen geführt, sondern auf die gemeinsame Infrastruktur
bezogen.

---

## Abgrenzung zu anderen ZE-WebLab-Dateien

### `25-urls.md`

`25-urls.md` behandelt:

- URL-Terminologie
- URL-Parsing
- Document Base URL
- Fallback Base URL
- Frozen Base URL
- URL-Auflösung

`26-fetching-resources.md` behandelt dagegen:

- was mit einer aufgelösten URL im Rahmen eines Fetches geschieht,
- welche Fetch-Eigenschaften HTML beeinflusst,
- CORS,
- Referrer Policy,
- Nonces,
- Lazy Loading,
- Blocking,
- Fetch Priority,
- Ressourcentypbestimmung.

Damit gilt:

**URL-Auflösung ≠ Ressourcen-Fetching**

---

### `19-dom-interfaces-and-apis.md`

`19-dom-interfaces-and-apis.md` behandelt die allgemeinen DOM Interfaces
und APIs.

Diese Datei dokumentiert dagegen nur die DOM-/IDL-Beziehungen, die
unmittelbar aus §2.5 entstehen.

Beispiele:

- `nonce`
- `crossOrigin`
- `referrerPolicy`
- `loading`
- `fetchPriority`

Die vollständigen Interface-Definitionen bleiben Bestandteil der
DOM-/API-Dokumentation.

---

### `20-sanitization.md`

Sanitization ist eine eigenständige Informationsebene.

Ein Fetch ist nicht automatisch ein Sanitization-Konzept.

Fetch-bezogene Attribute können jedoch mit Sicherheitsmechanismen
zusammenwirken, insbesondere:

- `nonce`
- CORS
- Referrer Policy

Die Sicherheitsbedeutung eines Features darf dabei nicht mit einer
Sanitization-Klassifikation gleichgesetzt werden.

---

### `21-parsing.md`

Parsing und Fetching stehen in Beziehung, sind aber unterschiedliche
Verarbeitungsebenen.

Beispielsweise können Parser und Elementerzeugung Attribute erzeugen,
die später Fetch-Verarbeitung auslösen.

Der Fetch selbst gehört jedoch in diese Datei.

---

## Einordnung

## Fetching als übergreifendes HTML-Konzept

HTML enthält zahlreiche Elemente, die externe Ressourcen laden oder deren
Verarbeitung beeinflussen.

Beispiele:

- `img`
- `script`
- `link`
- `iframe`
- `audio`
- `video`
- `source`
- `track`
- `object`
- `embed`

Der konkrete Fetch eines Elements wird jeweils in dessen
Elementdefinition bzw. dem zugehörigen Infrastrukturabschnitt beschrieben.

§2.5 definiert darüber hinaus gemeinsame Konzepte, die über einzelne
Elemente hinausgehen.

---

## Fetching ist kein HTML-Element

Fetching ist:

- kein HTML-Element,
- keine Content Category,
- kein Content Model,
- kein Link Type,
- kein Custom Element,
- kein DOM Interface.

Fetching ist ein **Processing Model bzw. eine Infrastruktur-Familie**.

---

# WHATWG-Struktur

## §2.5 Fetching resources

Der aktuelle HTML Living Standard führt unter §2.5 neun Unterabschnitte:

1. §2.5.1 Terminology
2. §2.5.2 Determining the type of a resource
3. §2.5.3 Extracting character encodings from `meta` elements
4. §2.5.4 CORS settings attributes
5. §2.5.5 Referrer policy attributes
6. §2.5.6 Nonce attributes
7. §2.5.7 Lazy loading attributes
8. §2.5.8 Blocking attributes
9. §2.5.9 Fetch priority attributes

Der WHATWG-Bereich endet anschließend mit §2.6 Common DOM interfaces.

---

# Inventar

| ID | Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Abdeckungsstatus | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|---|
| FETCH-001 | Fetch terminology | Normative Concept / Processing Concept | §2.5.1 | teilweise elementbezogen | teilweise | eigenständig |
| FETCH-002 | Potential-CORS request | Processing Model | §2.5.1 | teilweise über `crossorigin` | teilweise | eigenständig |
| FETCH-003 | Resource type determination | Processing Concept | §2.5.2 | elementbezogen | teilweise | eigenständig |
| FETCH-004 | MIME type determination | Integration Feature | §2.5.2 | elementbezogen | teilweise | eigenständig |
| FETCH-005 | Character encoding extraction from `meta` | Processing Model | §2.5.3 | `meta` elementbezogen | teilweise | eigenständig |
| FETCH-006 | CORS settings attributes | Attribute Family | §2.5.4 | elementbezogen | teilweise | eigenständig |
| FETCH-007 | Referrer policy attributes | Attribute Family | §2.5.5 | elementbezogen | teilweise | eigenständig |
| FETCH-008 | Cryptographic nonce | Attribute / Security Concept | §2.5.6 | `script`/globale Ebene elementbezogen | teilweise | eigenständig |
| FETCH-009 | Lazy loading attributes | Attribute Family / Processing Model | §2.5.7 | insbesondere `img`/`iframe` elementbezogen | teilweise | eigenständig |
| FETCH-010 | Blocking attributes | Attribute Family / Processing Model | §2.5.8 | elementbezogen | teilweise | eigenständig |
| FETCH-011 | Fetch priority attributes | Attribute Family | §2.5.9 | `img`, `link`, `script` elementbezogen | teilweise | eigenständig |

---

# Begriffsdefinitionen

## Resource Fetching

Fetching bezeichnet in diesem Dokument die Verarbeitung, durch die ein
User Agent eine Ressource anhand der HTML-spezifischen Vorgaben und der
allgemeinen Fetch-Infrastruktur anfordert bzw. deren Abruf vorbereitet.

HTML definiert nicht den vollständigen Netzwerkstack neu.

HTML verwendet dafür insbesondere den WHATWG Fetch Standard.

---

## Request

Ein Request ist ein Konzept des Fetch Standards.

HTML kann jedoch Eigenschaften eines Requests bestimmen oder beeinflussen.

Beispiele:

- URL
- Destination
- Mode
- Credentials Mode
- Referrer
- Referrer Policy
- Integrity-bezogene Informationen
- CORS-Einstellungen
- Priorität

---

## Response

Eine Response ist ebenfalls primär ein Fetch-Konzept.

HTML unterscheidet im Rahmen seiner CORS-Verarbeitung insbesondere:

- CORS-same-origin Responses
- CORS-cross-origin Responses

Eine Response mit Typ:

- `basic`
- `cors`
- `default`

ist CORS-same-origin.

Eine Response mit Typ:

- `opaque`
- `opaqueredirect`

ist CORS-cross-origin.

Diese Begriffe werden aus dem Fetch-Modell übernommen.

---

## Destination

Die Fetch Destination beschreibt den vorgesehenen Verwendungszweck
eines Requests bzw. einer Ressource.

HTML-Elemente können unterschiedliche Ressourcenarten und damit
unterschiedliche Fetch Destinations erzeugen.

Die konkrete Destination ist Teil des Fetch-Modells.

---

## CORS

CORS steht für Cross-Origin Resource Sharing.

HTML definiert für bestimmte Elemente ein gemeinsames CORS-Settings-
Attribute-Modell.

Die eigentliche CORS-Protokoll- und Fetch-Infrastruktur wird jedoch
durch den Fetch Standard definiert.

---

## Referrer

Ein Referrer beschreibt Informationen über die Quelle eines Requests,
soweit diese im Rahmen der geltenden Referrer-Regeln übermittelt werden.

HTML kann die für einen Fetch verwendete Referrer Policy beeinflussen.

---

## Cryptographic Nonce

Ein Nonce ist ein kryptographischer Wert, der insbesondere mit Content
Security Policy zusammenwirkt.

HTML stellt dafür das `nonce`-Content-Attribut und die zugehörige
IDL-Verarbeitung bereit.

---

## Lazy Loading

Lazy Loading bezeichnet eine Verarbeitung, bei der das Laden einer
Ressource unter definierten Bedingungen verzögert werden kann.

HTML definiert dafür das gemeinsame Konzept des Lazy Loading Attributes.

---

## Blocking

Ein Blocking Attribute gibt an, dass bestimmte Operationen im Rahmen
des Ladens einer externen Ressource blockiert werden sollen.

Der aktuelle Standard definiert als möglichen Blocking Token:

`render`

Damit kann ein Element als potentiell render-blockierend bestimmt werden.

---

## Fetch Priority

Fetch Priority beschreibt einen Hinweis auf die relative Priorität eines
Fetches gegenüber anderen Fetches mit derselben Destination.

Die definierten Zustände sind:

- High
- Low
- Auto

---

# Normative Regeln

## §2.5.1 Terminology

### CORS-same-origin

Eine Response mit einem der folgenden Response-Typen ist
CORS-same-origin:

- `basic`
- `cors`
- `default`

---

### CORS-cross-origin

Eine Response mit einem der folgenden Response-Typen ist
CORS-cross-origin:

- `opaque`
- `opaqueredirect`

---

### Unsafe Response

Die unsafe response einer Response ist:

1. ihre interne Response, wenn eine solche vorhanden ist;
2. andernfalls die Response selbst.

Dieses Konzept stammt aus der Fetch-Infrastruktur und wird von HTML
für weitere Verarbeitung verwendet.

---

# Potential-CORS Request

## Zweck

HTML definiert einen gemeinsamen Algorithmus zum Erzeugen eines
Potential-CORS Requests.

Der Algorithmus erhält insbesondere:

- URL
- Destination
- CORS Attribute State
- optional einen Same-Origin-Fallback

---

## Mode

Bei der Erzeugung wird zunächst zwischen folgenden Zuständen unterschieden:

### No CORS

Der Request erhält grundsätzlich den Mode:

`no-cors`

### CORS

Der Request erhält den Mode:

`cors`

### Same-Origin Fallback

Wenn der Same-Origin-Fallback aktiviert ist und zunächst `no-cors`
bestimmt wurde, wird der Mode auf:

`same-origin`

gesetzt.

---

## Credentials Mode

Der Default-Wert des erzeugten Potential-CORS Requests ist:

`include`

Für den Anonymous State wird der Credentials Mode auf:

`same-origin`

gesetzt.

---

## Request-Zusammensetzung

Der erzeugte Request enthält insbesondere:

- URL
- Destination
- Mode
- Credentials Mode
- Use-URL-Credentials Flag

Damit bildet der Algorithmus eine Verbindung zwischen HTML-
Attributzuständen und dem allgemeinen Fetch Request Modell.

---

# §2.5.2 Determining the type of a resource

## Grundprinzip

HTML verlangt, dass der Content-Type einer Ressource entsprechend den
Regeln des WHATWG MIME Sniffing Standards ermittelt und interpretiert
wird.

Das betrifft insbesondere:

- Content-Type Metadata
- Computed MIME Type
- Bild-Sniffing
- Text-vs-Binary-Ermittlung
- Audio-Sniffing
- Video-Sniffing

---

## MIME Type

HTML definiert für diesen Bereich keine konkurrierende eigene
MIME-Type-Sniffing-Engine.

Die normative Ressourcentypbestimmung wird an den MIME Sniffing Standard
delegiert.

---

## Sicherheitsrelevanz

Die Spezifikation verlangt, dass die MIME-Sniffing-Regeln exakt befolgt
werden.

Abweichende Heuristiken können zu Sicherheitsproblemen führen, wenn
Server und User Agent unterschiedliche Vorstellungen über den
Ressourcentyp besitzen.

---

## Abgrenzung

Diese Datei dokumentiert die HTML-Integration des MIME Sniffing.

Sie dokumentiert nicht den vollständigen MIME Sniffing Standard.

---

# §2.5.3 Extracting character encodings from `meta` elements

## Zweck

HTML definiert einen Algorithmus, mit dem aus einem `meta`-Element bzw.
einer entsprechenden Zeichenfolge eine Character Encoding extrahiert
werden kann.

Das Ergebnis ist:

- eine Character Encoding
- oder kein Ergebnis.

---

## Algorithmische Grundstruktur

Der Algorithmus:

1. beginnt am Anfang der Eingabe,
2. sucht nach einem ASCII-case-insensitiven Auftreten von `charset`,
3. berücksichtigt ASCII-Whitespace nach `charset`,
4. verlangt ein `=`,
5. berücksichtigt erneut ASCII-Whitespace,
6. verarbeitet anschließend den Encoding-Wert.

---

## Anführungszeichen

Der Wert kann unter anderem durch:

- doppelte Anführungszeichen,
- einfache Anführungszeichen

begrenzt werden.

Bei einem passenden Abschlusszeichen wird der dazwischenliegende
Text als Encoding-Bezeichnung verarbeitet.

---

## Unvollständige Werte

Bei einem nicht abgeschlossenen Quoting oder fehlendem Wert kann der
Algorithmus ohne Ergebnis enden.

---

## Encoding Lookup

Die eigentliche Ermittlung eines Character-Encodings erfolgt über die
entsprechende Encoding-Infrastruktur.

HTML definiert somit die HTML-spezifische Extraktion, nicht eine
zweite vollständige Character-Encoding-Spezifikation.

---

## Beziehung zu `meta`

Das `meta`-Element ist in:

`02-document-metadata.md`

als Element dokumentiert.

Diese Datei dokumentiert dagegen den gemeinsamen
ressourcen-/Dokumentverarbeitungsbezogenen Algorithmus.

---

# §2.5.4 CORS Settings Attributes

## Definition

Ein CORS Settings Attribute ist ein enumeriertes Attribut mit den
Zuständen:

- No CORS
- Anonymous
- Use Credentials

---

## Keywords

| Keyword | Zustand | Request-Verhalten |
|---|---|---|
| `anonymous` | Anonymous | `cors` + `same-origin` Credentials |
| `use-credentials` | Use Credentials | `cors` + `include` Credentials |
| leerer Wert | Anonymous | entspricht Anonymous |
| nicht vorhanden | No CORS | kein CORS-Mode aufgrund dieses Attributes |

---

## Missing Value Default

Der Missing Value Default ist:

**No CORS**

---

## Empty Value Default

Der Empty Value Default ist:

**Anonymous**

---

## Invalid Value Default

Der Invalid Value Default ist:

**Anonymous**

---

## CORS Settings Attribute Credentials Mode

Für moderne Features, bei denen der Request Mode bereits `cors` ist,
kann der CORS Settings State insbesondere für die Bestimmung des
Credentials Mode verwendet werden.

Zuordnung:

| Zustand | Credentials Mode |
|---|---|
| No CORS | `same-origin` |
| Anonymous | `same-origin` |
| Use Credentials | `include` |

Die konkrete Verwendung hängt vom jeweiligen Fetch-Feature ab.

---

## Elementbezogene Verwendung

Das gemeinsame CORS Settings Attribute wird unter anderem von
ressourcenladenden Elementen verwendet.

Im aktuellen ZE-WebLab-Bestand ist es bereits elementbezogen dokumentiert,
insbesondere bei:

- `img`
- `audio`
- `video`
- `link`
- `script`

Die gemeinsame Attributsystematik wird hier zentral dokumentiert.

---

# §2.5.5 Referrer Policy Attributes

## Definition

Ein Referrer Policy Attribute ist ein enumeriertes Attribut.

Die Zustände entsprechen den definierten Referrer Policies einschließlich
des leeren Strings.

---

## Missing Value Default

Der Missing Value Default ist:

**leerer String**

---

## Invalid Value Default

Der Invalid Value Default ist ebenfalls:

**leerer String**

---

## Bedeutung

Das Attribut beeinflusst die Referrer-Verarbeitung von Fetches, die durch
das jeweilige Element ausgelöst werden.

Es bestimmt jedoch nicht allein die gesamte Referrer-Verarbeitung.

---

## Reihenfolge der Signale

HTML beschreibt mehrere mögliche Quellen für die Bestimmung einer
Referrer Policy.

Die Reihenfolge ist:

1. `noreferrer` Link Type
2. Wert des Referrer Policy Attributes
3. `meta` mit `name="referrer"`
4. `Referrer-Policy` HTTP-Header

Damit ist das Attribut nur ein Bestandteil des gesamten
Referrer-Policy-Verarbeitungsmodells.

---

## Elementbezogene Verwendung

Das Attribut kann insbesondere bei folgenden HTML-Features auftreten:

- Hyperlinks
- `img`
- `iframe`
- `script`
- `link`

Die konkrete Zulässigkeit und Bedeutung ergibt sich jeweils aus der
Elementdefinition.

---

# §2.5.6 Nonce Attributes

## `nonce`

Das `nonce`-Attribut repräsentiert einen kryptographischen Nonce-Wert.

Der Wert wird im Zusammenhang mit Content Security Policy verwendet,
um bestimmte Fetches bzw. die Ausführung von Ressourcen zu autorisieren.

---

## Nicht gewöhnliche Attribut-Reflection

Der Nonce-Wert wird nicht wie ein gewöhnlicher frei lesbarer
Content-Attributwert behandelt.

HTML führt dafür einen internen Slot:

`[[CryptographicNonce]]`

---

## Verarbeitung

Für Elemente mit `nonce` wird der Wert aus dem Content Attribute in
den internen kryptographischen Nonce-Slot übernommen.

Anschließend kann das Content Attribute aus Sicherheitsgründen auf den
leeren String gesetzt werden, während der interne Wert erhalten bleibt.

---

## DOM-Zugriff

Das IDL-Attribut:

`element.nonce`

liefert den Wert des internen kryptographischen Nonce-Slots.

Beim Setzen des IDL-Attributes wird der interne Slot aktualisiert.

Der Setter muss dabei nicht das Content Attribute aktualisieren.

---

## Sicherheitsgrund

Diese Trennung reduziert das Risiko, dass der Nonce-Wert über Mechanismen
ausgelesen wird, die Content Attributes lesen können.

Dazu gehören beispielsweise Selektoren bzw. andere Mechanismen, die
Attributwerte sichtbar machen könnten.

---

## Browsing-Context Connection

Wenn ein entsprechendes Element browsing-context-connected wird,
definiert HTML zusätzliche Verarbeitungsschritte im Zusammenhang mit
der CSP des zuständigen Policy Containers.

---

## Cloning

Für entsprechende Elemente sind Cloning Steps definiert.

Der interne kryptographische Nonce-Wert wird beim Klonen entsprechend
den HTML-Regeln übernommen.

---

## Elementbezug

Nonce-Verarbeitung ist insbesondere mit script- und stylebezogenen
Ressourcen sowie CSP verbunden.

Die konkrete Zulässigkeit des Attributes richtet sich nach den jeweiligen
Elementdefinitionen.

---

# §2.5.7 Lazy Loading Attributes

## Definition

Ein Lazy Loading Attribute ist ein enumeriertes Attribut.

Es besitzt die Zustände:

- Lazy
- Eager

---

## Keywords

| Keyword | Zustand | Bedeutung |
|---|---|---|
| `lazy` | Lazy | Ressourcenabruf kann unter definierten Bedingungen verzögert werden |
| `eager` | Eager | Ressource soll unmittelbar geladen werden |

---

## Defaults

Der Missing Value Default ist:

**Eager**

Der Invalid Value Default ist:

**Eager**

---

## `will lazy load`

HTML definiert ein gemeinsames Verarbeitungskonzept:

**will lazy load element**

Der Algorithmus prüft insbesondere:

1. ob Scripting für das Element deaktiviert ist;
2. ob sich das Lazy Loading Attribute im Lazy State befindet.

---

## Scripting als Voraussetzung

Ist Scripting deaktiviert, liefert der Algorithmus:

**false**

Diese Regel ist ausdrücklich als Anti-Tracking-Maßnahme begründet.

Ohne diese Einschränkung könnte Lazy Loading unter Umständen zur
Ermittlung ungefährer Scrollpositionen verwendet werden.

---

## Lazy State

Befindet sich das Attribut im Lazy State, liefert der Algorithmus:

**true**

---

## Eager State

Im Eager State wird kein Lazy Loading durch dieses gemeinsame
Attributkonzept aktiviert.

---

## Betroffene Elemente

Die gemeinsame Lazy-Loading-Infrastruktur wird unter anderem für:

- `img`
- `audio`
- `video`
- `iframe`

verwendet.

Die konkrete Ressourcenauswahl und weitere Verarbeitung bleibt
elementabhängig.

---

## Lazy Load Resumption Steps

Bestimmte Elemente besitzen zugehörige:

**lazy load resumption steps**

Diese sind zunächst `null`.

Wenn die Bedingungen zum Fortsetzen des Ladens erfüllt sind, werden
diese Schritte ausgeführt.

---

## Intersection Observer

HTML verwendet für die Lazy-Loading-Verarbeitung einen
Lazy-Load-Intersection-Observer.

Dieser kann als `IntersectionObserver`-Instanz implementiert bzw. über
dessen definierte Schnittstelle angebunden werden.

---

## Intersection

Wird ein beobachtetes Lazy-Loading-Element relevant sichtbar bzw.
intersecting, kann der User Agent:

1. das Element aus der Beobachtung entfernen,
2. die gespeicherten Resumption Steps ausführen,
3. den Fetch bzw. die weitere Ressourcenverarbeitung fortsetzen.

---

## Poster bei `video`

Für `video` existieren zusätzlich eigene:

**poster lazy load resumption steps**

Diese werden zusammen mit den allgemeinen Lazy-Loading-Schritten
berücksichtigt.

---

## Lazy Load Scroll Margin

HTML definiert eine:

**lazy load scroll margin**

Diese ist implementation-defined.

Die Spezifikation gibt jedoch Hinweise für die Bestimmung, insbesondere
unter Berücksichtigung von:

- typischer Scrollgeschwindigkeit,
- aktueller Scrollgeschwindigkeit,
- Netzwerkqualität,
- Nutzerpräferenzen.

---

## Datenschutz

Die Lazy-Load-Scroll-Margin darf nicht dazu verwendet werden,
zusätzliche Informationen über das Nutzerverhalten bzw. das Gerät in
einer Weise zu leaken, die neue Fingerprinting-Vektoren erzeugt.

---

# §2.5.8 Blocking Attributes

## Definition

Ein Blocking Attribute zeigt an, dass bestimmte Operationen beim Laden
einer externen Ressource blockiert werden sollen.

---

## Possible Blocking Tokens

Der aktuelle Standard definiert als möglichen Token:

`render`

Bedeutung:

> Das Element ist potentiell render-blockierend.

Die Spezifikation lässt ausdrücklich die Möglichkeit weiterer
Blocking Tokens in zukünftigen Entwicklungen offen.

---

## Wertemodell

Das Blocking Attribute enthält:

- ein ungeordnetes Set,
- eindeutiger,
- durch ASCII-Whitespace getrennter Tokens.

---

## Unterstützte Tokens

Die unterstützten Tokens eines Blocking Attributes sind die aktuell
definierten Possible Blocking Tokens.

Der aktuelle normative Token ist:

`render`

---

## Anzahl

Ein Element darf höchstens ein Blocking Attribute besitzen.

---

## Blocking Tokens Set

Das Blocking Tokens Set eines Elements wird aus dem Attributwert
bestimmt.

Verarbeitung:

1. Attributwert lesen;
2. falls nicht vorhanden, leeren String verwenden;
3. Wert in ASCII-Kleinbuchstaben konvertieren;
4. an ASCII-Whitespace aufteilen;
5. nur bekannte Possible Blocking Tokens übernehmen.

---

## Potentially Render-blocking

Ein Element ist potentiell render-blockierend, wenn sein Blocking
Tokens Set den Token:

`render`

enthält.

Darüber hinaus können einzelne Elementdefinitionen ein Element
implizit als potentiell render-blockierend bestimmen.

Standardmäßig ist ein Element nicht implizit
potentiell render-blockierend.

---

## Blocking ist kein Fetch-Modus

Das Blocking Attribute:

- definiert keinen neuen Fetch Mode,
- definiert keinen CORS Mode,
- verändert nicht automatisch die URL,
- ist kein Link Type.

Es ist ein Steuerungskonzept für die Verarbeitung rund um externe
Ressourcen und Rendering.

---

# §2.5.9 Fetch Priority Attributes

## Definition

Ein Fetch Priority Attribute ist ein enumeriertes Attribut.

Es besitzt drei Zustände:

- High
- Low
- Auto

---

## Keywords

| Keyword | Zustand | Bedeutung |
|---|---|---|
| `high` | High | höhere Priorität relativ zu Fetches mit derselben Destination |
| `low` | Low | niedrigere Priorität relativ zu Fetches mit derselben Destination |
| `auto` | Auto | automatische Prioritätsbestimmung |

---

## Defaults

Der Missing Value Default ist:

**Auto**

Der Invalid Value Default ist:

**Auto**

---

## Relative Bedeutung

`fetchpriority` definiert keine globale absolute Priorität aller
Netzwerkoperationen.

Die normative Beschreibung bezieht die Priorisierung ausdrücklich auf
Fetches mit derselben Destination.

---

## Keine harte Netzwerkgarantie

Das Attribut beschreibt einen Fetch-Priority-Hinweis bzw. Zustand.

Es definiert nicht:

- eine konkrete TCP-Priorität,
- eine konkrete HTTP/2-Priorität,
- eine konkrete HTTP/3-Priorität,
- eine bestimmte Reihenfolge aller Netzwerkrequests.

Die konkrete interne Umsetzung der Priorität gehört nicht zu einer
HTML-Konformitätsgarantie für einen bestimmten Netzwerk-Scheduler.

---

## Elementbezogene Verwendung

Das gemeinsame Konzept wird insbesondere durch folgende
ressourcenbezogene Elemente verwendet:

- `img`
- `script`
- `link`

Die konkrete Auswirkung ergibt sich aus dem jeweiligen Fetch, der
durch das Element ausgelöst wird.

---

# Attribute

## Zentrale Fetch-bezogene Attribute

| Attribut | Feature-Familie | Zustände / Werte | Hauptfunktion |
|---|---|---|---|
| `crossorigin` | CORS Settings | No CORS / Anonymous / Use Credentials | CORS-/Credentials-Verarbeitung |
| `referrerpolicy` | Referrer Policy | Referrer-Policy-Zustände | Referrer-Verarbeitung |
| `nonce` | Cryptographic Nonce | Stringwert | CSP-bezogene Autorisierung |
| `loading` | Lazy Loading | `lazy` / `eager` | verzögertes Laden |
| `blocking` | Blocking | Token Set, aktuell `render` | Blockierung bestimmter Operationen |
| `fetchpriority` | Fetch Priority | `high` / `low` / `auto` | relative Fetch-Priorität |

---

## Attributzustand ≠ Fetch-Ergebnis

Der Wert eines Attributes ist nicht automatisch identisch mit dem
resultierenden Request- oder Response-Zustand.

Beispiel:

`crossorigin="anonymous"`

ist ein HTML-Attributzustand.

Daraus entstehen im Rahmen des jeweiligen Fetch-Modells unter anderem:

- Mode `cors`
- Credentials Mode `same-origin`

Der konkrete Request kann jedoch durch weitere Fetch-Regeln beeinflusst
werden.

---

# Content Categories

## Fetching selbst

Fetching besitzt keine Content Category.

Es ist ein Processing-/Infrastrukturkonzept.

---

## Ressource ladende Elemente

Die Content Category eines Elements wird durch dessen Elementdefinition
bestimmt.

Beispiele:

- `img` → Embedded Content
- `iframe` → Embedded Content
- `script` → Script-supporting bzw. abhängig von seinem konkreten Kontext
- `link` → Metadata Content
- `audio` / `video` → Embedded Content

Fetching verändert diese Klassifikation nicht.

---

# Context

Fetching besitzt keinen eigenen HTML-Element-Context.

Der Context wird durch das Element bestimmt, das den Fetch auslöst.

Beispielsweise unterscheiden sich die Anforderungen für:

- `img[src]`
- `script[src]`
- `link[href]`
- `iframe[src]`
- `video[src]`

obwohl sie alle Fetches auslösen können.

---

# Content Model

Fetching besitzt kein Content Model.

Ein Fetch ist kein Element und besitzt daher keine Kindinhalte.

Die Content Models der auslösenden Elemente bleiben Bestandteil der
Elementdefinitionen.

---

# Processing Models

## Allgemeines Modell

Die Fetch-bezogene Verarbeitung lässt sich konzeptionell als
Zusammenspiel mehrerer Ebenen verstehen:

```text
HTML Element
    ↓
Content Attribute / DOM State
    ↓
HTML-spezifische Verarbeitung
    ↓
Fetch Request
    ↓
Fetch Standard
    ↓
Response
    ↓
MIME / CORS / weitere Verarbeitung
    ↓
Element-spezifische Ressourcenverarbeitung
```

Diese Darstellung ist eine fachliche Ableitung aus den normativen
Beziehungen zwischen HTML, Fetch, MIME Sniffing und den jeweiligen
Elementdefinitionen.

---

## HTML bestimmt nicht den vollständigen Fetch

HTML liefert insbesondere:

- HTML-spezifische Request-Eigenschaften,
- CORS Attribute States,
- Referrer Policy Inputs,
- Nonce-Verarbeitung,
- Lazy Loading,
- Blocking,
- Fetch Priority.

Die allgemeine Fetch-Verarbeitung erfolgt über den WHATWG Fetch Standard.

---

# DOM Interfaces / APIs

## Allgemeines

Die Fetching-Infrastruktur definiert selbst kein einzelnes
„Fetching-DOM-Interface“.

Stattdessen spiegeln konkrete HTML-Interfaces bestimmte Attribute.

---

## `crossOrigin`

Je nach Element kann ein IDL-Attribut wie:

`crossOrigin`

den `crossorigin`-Content-Attributzustand widerspiegeln.

Die konkrete IDL-Definition gehört zum jeweiligen Elementinterface.

---

## `referrerPolicy`

Je nach Element kann:

`referrerPolicy`

das `referrerpolicy`-Content-Attribut widerspiegeln.

---

## `nonce`

Das:

`nonce`

IDL-Attribut greift auf den internen:

`[[CryptographicNonce]]`

Slot zu.

Der Setter aktualisiert den internen Nonce-Wert.

---

## `loading`

Ressourcenbezogene Interfaces können den `loading`-Zustand über
entsprechende IDL-Attribute zugänglich machen.

---

## `fetchPriority`

Ressourcenbezogene Interfaces können den Fetch-Priority-Zustand über:

`fetchPriority`

zugänglich machen.

---

## Vollständige Interface-Dokumentation

Die vollständigen DOM Interfaces werden in:

`docs/html/19-dom-interfaces-and-apis.md`

behandelt.

Diese Datei dokumentiert nur den Fetching-spezifischen Zusammenhang.

---

# Accessibility

## Fetching selbst

Fetching besitzt keine eigenständige Accessibility-Semantik.

---

## Indirekte Auswirkungen

Ein Fetch kann jedoch Ressourcen laden, die für Accessibility relevant
sind.

Beispiele:

- Bilder
- Texttracks
- Medien
- Stylesheets
- Scripts

Die Accessibility-Anforderungen an das jeweilige Element bzw. den
Inhalt werden nicht durch §2.5 ersetzt.

---

## Abgrenzung

Für `img` ist beispielsweise der alternative Text ein Accessibility-
relevantes Thema.

Dieses Thema gehört primär zur `img`-Definition und zur dortigen
Accessibility-Dokumentation, nicht zum allgemeinen Fetching-Modell.

---

# Sanitization

## Fetching selbst

§2.5 definiert kein allgemeines Sanitization-Modell für alle Fetches.

---

## Sicherheitsbezogene Konzepte

Fetching steht jedoch in Beziehung zu Sicherheitsmechanismen wie:

- CORS
- Content Security Policy
- Referrer Policy
- MIME Sniffing

Diese Mechanismen dürfen nicht pauschal als Sanitization bezeichnet
werden.

---

## `nonce`

Der Nonce ist ein Sicherheitsmechanismus und steht in direkter Beziehung
zu Content Security Policy.

Er ist deshalb sicherheitsrelevant, aber nicht mit dem allgemeinen
Sanitization-Modell gleichzusetzen.

---

# Konformitätsregeln

## CORS Settings Attributes

Wenn ein Element ein CORS Settings Attribute verwendet, gelten die
für diesen Attributtyp definierten Zustände und Defaults.

Nicht erlaubte Werte können je nach enumeriertem Attributzustand über
den Invalid Value Default verarbeitet werden.

---

## Referrer Policy Attributes

Ein Referrer Policy Attribute muss entsprechend den für enumerierte
Attribute geltenden Regeln verarbeitet werden.

Der konkrete Referrer wird zusätzlich durch andere Signale beeinflusst.

---

## Nonce

Die Nonce-Verarbeitung unterliegt den normativen Regeln des
`[[CryptographicNonce]]`-Modells.

Der sichtbare Content-Attributwert und der interne Nonce-Wert dürfen
nicht ohne Weiteres als identisch betrachtet werden.

---

## Lazy Loading

Der User Agent muss die normativen Bedingungen des Lazy-Loading-Modells
berücksichtigen.

Insbesondere ist die Scripting-Bedingung Bestandteil des Algorithmus.

---

## Blocking

Das Blocking Attribute verwendet nur die aktuell definierten
Possible Blocking Tokens.

Nicht bekannte Tokens werden nicht Bestandteil des normativen
Blocking Tokens Sets.

---

## Fetch Priority

`fetchpriority` besitzt die Zustände:

- High
- Low
- Auto

Missing Value Default und Invalid Value Default sind Auto.

---

# Beziehungen zu externen Standards

## WHATWG Fetch Standard

HTML delegiert wesentliche Fetch-Infrastruktur an den Fetch Standard.

Dazu gehören insbesondere:

- Requests
- Responses
- Fetch Modes
- Credentials Modes
- Destinations
- Response Types
- allgemeine Fetch-Verarbeitung

---

## WHATWG MIME Sniffing Standard

Die Ermittlung des Ressourcentyps erfolgt nach den Anforderungen des
MIME Sniffing Standards.

HTML schreibt ausdrücklich die Verwendung dieser Regeln vor.

---

## WHATWG Encoding Standard

Die Character-Encoding-Verarbeitung nutzt die Encoding-Infrastruktur.

Insbesondere wird bei der Extraktion eines Encodings aus `meta`
die definierte Encoding-Ermittlung verwendet.

---

## Content Security Policy

`nonce` ist unmittelbar mit Content Security Policy verbunden.

Die CSP-Regeln selbst sind nicht Teil des HTML-Standards.

---

## Referrer Policy

Die allgemeine Definition von Referrer Policies und die entsprechenden
Policy-Werte sind Bestandteil der Referrer Policy-Spezifikation.

HTML definiert die HTML-seitige Integration des entsprechenden
Attributs und der zugehörigen Signale.

---

## Intersection Observer

Das Lazy-Loading-Modell verwendet die Intersection-Observer-Infrastruktur
für die Ermittlung relevanter Intersections.

Die allgemeine Intersection Observer API ist nicht Teil dieser Datei.

---

# Querverweise

## HTML-Element ↔ Fetch

| Element | Typischer Fetch-Bezug |
|---|---|
| `img` | Bildressource |
| `iframe` | eingebettetes Dokument |
| `script` | Script-Ressource |
| `link` | verknüpfte externe Ressource |
| `audio` | Media Resource |
| `video` | Media Resource |
| `source` | alternative Ressource |
| `track` | Texttrack-Ressource |
| `object` | externe Ressource |
| `embed` | eingebettete Ressource |

---

## Attribute ↔ Fetch

| Attribut | Beziehung |
|---|---|
| `crossorigin` | CORS Settings / Credentials |
| `referrerpolicy` | Referrer Policy |
| `nonce` | CSP / kryptographische Autorisierung |
| `loading` | Lazy Loading |
| `blocking` | Blocking / Rendering |
| `fetchpriority` | relative Fetch-Priorität |

---

## URL ↔ Fetch

`25-urls.md` bestimmt insbesondere:

- URL-Terminologie,
- URL-Parsing,
- Base URL,
- Document Base URL.

`26-fetching-resources.md` setzt diese URL-Infrastruktur für
Ressourcen-Fetches voraus.

Damit gilt:

```text
URL
 ↓
URL Resolution
 ↓
absolute URL / URL Record
 ↓
HTML Fetch Processing
 ↓
Fetch Request
```

---

## Element ↔ Attribute ↔ Fetch

Die vollständige fachliche Beziehung lautet beispielsweise:

```text
<img
    src="..."
    crossorigin="anonymous"
    referrerpolicy="no-referrer"
    loading="lazy"
    fetchpriority="high"
>
```

Dabei sind:

- `src` → URL-Systematik
- `crossorigin` → CORS Settings
- `referrerpolicy` → Referrer Policy
- `loading` → Lazy Loading
- `fetchpriority` → Fetch Priority

Die konkrete Bildverarbeitung bleibt Bestandteil der
`img`-Definition.

---

# Erste-Ebene-Abdeckung

## `08-embedded-content.md`

Bereits elementbezogen dokumentiert sind insbesondere:

- `img[src]`
- `img[crossorigin]`
- `img[referrerpolicy]`
- `img[loading]`
- `img[fetchpriority]`
- Media-bezogene `crossorigin`-Verarbeitung
- weitere Ressourcenverarbeitung

Damit besteht eine **teilweise** Abdeckung.

Die übergreifende Attributsystematik und ihre Beziehungen zu Fetch
waren jedoch nicht automatisch dadurch vollständig dokumentiert.

---

## `12-scripting.md`

Die Script-Dokumentation behandelt Script-bezogene Fetch- und
Sicherheitsaspekte.

Dazu gehören insbesondere:

- externe Script-Ressourcen,
- `src`,
- `crossorigin`,
- `referrerpolicy`,
- `nonce`,
- Fetch-bezogene Verarbeitung.

Die gemeinsame §2.5-Systematik wird hier zentralisiert.

---

## `06-links.md`

Die Link-Dokumentation behandelt:

- `link[href]`
- externe Ressourcen
- Link Types
- `crossorigin`
- `referrerpolicy`
- ressourcenbezogene Link-Verarbeitung

Die allgemeine Fetch-Infrastruktur bleibt davon getrennt.

---

## `02-document-metadata.md`

Die `meta`-Definition behandelt das `meta`-Element.

Für diese Datei relevant ist insbesondere:

- Character Encoding
- `charset`
- `name="referrer"`

Die übergreifende Encoding-Extraktion aus §2.5.3 wird hier
als gemeinsames Processing Model dokumentiert.

---

# Feature-Abgrenzung

## Kein Link Type

`crossorigin`, `loading`, `blocking` und `fetchpriority` sind keine
Link Types.

---

## Kein Content Category

Fetching ist keine Content Category.

---

## Kein Content Model

Fetching besitzt kein Content Model.

---

## Kein DOM Interface

„Fetching“ als Ganzes ist kein DOM Interface.

Einzelne Attribute können jedoch über DOM-/IDL-Mitglieder zugänglich
sein.

---

## Kein Custom Element Feature

Fetching ist keine Custom-Elements-Funktion.

Custom Elements können allerdings selbst Ressourcenverarbeitung
auslösen und dadurch indirekt mit Fetching interagieren.

---

# Status / V1

## WHATWG-Status

Die hier dokumentierten Konzepte sind im aktuellen WHATWG HTML Living
Standard definiert.

Die Unterkonzepte von §2.5 sind normative Bestandteile der aktuellen
HTML-Spezifikation, soweit die jeweiligen Anforderungen als normative
Regeln formuliert sind.

---

## Normative Definition

Insbesondere sind folgende Konzepte normativ definiert:

- Potential-CORS Request
- CORS Settings Attributes
- Referrer Policy Attributes
- Nonce Verarbeitung
- Lazy Loading Attributes
- Blocking Attributes
- Fetch Priority Attributes
- Ressourcentypbestimmung
- Character-Encoding-Extraktion

---

## Externe Spezifikationen

Einige normative Details werden ausdrücklich an andere Standards
delegiert.

Das betrifft insbesondere:

- Fetch
- MIME Sniffing
- Encoding
- Content Security Policy
- Referrer Policy
- Intersection Observer

Die Existenz einer externen Abhängigkeit ändert nicht den normativen
Status der HTML-Integrationsregeln.

---

## ZE-WebLab-V1

**V1-Einstufung:**

Übergreifende HTML-Infrastruktur / Fetching Feature Family.

**Begründung:**

Der Bereich ist kein Elementinventar, sondern ein gemeinsames
Verarbeitungsmodell, das von zahlreichen HTML-Elementen und Attributen
verwendet wird.

---

## Browser-Kompatibilität

Browser-Kompatibilität wird hier **nicht** als WHATWG-Status verwendet.

Diese Datei enthält keine Browser-Support-Matrix.

---

# Detailprüfung

## §2.5.1 Terminology

Geprüft:

- CORS-same-origin
- CORS-cross-origin
- unsafe response
- Potential-CORS Request
- Request Mode
- Credentials Mode
- Destination
- Use-URL-Credentials

**Status:** geprüft.

---

## §2.5.2 Determining the type of a resource

Geprüft:

- Content-Type Metadata
- computed MIME type
- MIME Sniffing
- Image Sniffing
- Text/Binary-Erkennung
- Audio/Video Sniffing
- Sicherheitsanforderung an exakte Sniffing-Regeln

**Status:** geprüft.

---

## §2.5.3 Extracting character encodings from `meta`

Geprüft:

- Suche nach `charset`
- ASCII-case-insensitive Matching
- Whitespace
- `=`
- Quoting
- Encoding Lookup
- Fehler-/No-result-Fälle
- Abgrenzung zum HTTP-Verfahren

**Status:** geprüft.

---

## §2.5.4 CORS settings attributes

Geprüft:

- No CORS
- Anonymous
- Use Credentials
- `anonymous`
- `use-credentials`
- Empty String
- Missing Value Default
- Invalid Value Default
- Credentials Mode
- Potential-CORS Request
- moderne CORS-Features

**Status:** geprüft.

---

## §2.5.5 Referrer policy attributes

Geprüft:

- enumeriertes Attribut
- Referrer-Policy-Zustände
- leerer String
- Missing Value Default
- Invalid Value Default
- Signalreihenfolge
- `noreferrer`
- `meta[name="referrer"]`
- HTTP Header
- Fetch-Verarbeitung

**Status:** geprüft.

---

## §2.5.6 Nonce attributes

Geprüft:

- `nonce`
- `[[CryptographicNonce]]`
- IDL-Zugriff
- Setter
- Attribute Change Steps
- Browsing-context Connection
- CSP
- Cloning Steps
- Schutz vor Attribut-basierter Exfiltration

**Status:** geprüft.

---

## §2.5.7 Lazy loading attributes

Geprüft:

- `lazy`
- `eager`
- Missing Value Default
- Invalid Value Default
- `will lazy load`
- Scripting-Prüfung
- Lazy Load Resumption Steps
- Poster Lazy Load Resumption Steps
- Intersection Observer
- Intersection-Verarbeitung
- Lazy Load Scroll Margin
- Datenschutzanforderungen

**Status:** geprüft.

---

## §2.5.8 Blocking attributes

Geprüft:

- Blocking Attribute
- Possible Blocking Tokens
- `render`
- Token-Set
- ASCII-Lowercasing
- ASCII-Whitespace
- Blocking Tokens Set
- potentially render-blocking
- implicit potentially render-blocking
- maximale Anzahl von Blocking Attributes

**Status:** geprüft.

---

## §2.5.9 Fetch priority attributes

Geprüft:

- `high`
- `low`
- `auto`
- High State
- Low State
- Auto State
- Missing Value Default
- Invalid Value Default
- relative Priorisierung nach Destination

**Status:** geprüft.

---

# Normative Sonderregeln

## CORS

Ein CORS Settings Attribute beeinflusst die Request-Erzeugung, ersetzt
aber nicht das vollständige Fetch-CORS-Modell.

---

## Referrer Policy

Eine elementbezogene Referrer Policy steht nicht isoliert.

Andere Signale können die resultierende Policy beeinflussen.

---

## Nonce

Der kryptographische Nonce darf nicht wie ein gewöhnlicher frei
zugänglicher Content-Attributwert behandelt werden.

Das interne Slot-Modell ist Teil der normativen Sicherheitsverarbeitung.

---

## Lazy Loading

Lazy Loading ist nicht bloß eine Performance-Empfehlung.

Die HTML-Spezifikation definiert konkrete normative Verarbeitung für
den Lazy State.

---

## Blocking

`blocking="render"` ist ein normatives Konzept zur Bestimmung von
potentiell render-blockierenden Elementen.

---

## Fetch Priority

`fetchpriority` ist relativ zu Fetches mit derselben Destination.

Es definiert keine globale absolute Prioritätsordnung.

---

# Sicherheits- und Datenschutzbeziehungen

## CORS

CORS begrenzt bzw. steuert den Zugriff auf cross-origin Ressourcen
entsprechend dem Fetch-Modell.

---

## MIME Sniffing

Eine falsche Ressourcentypbestimmung kann Sicherheitsprobleme erzeugen.

Daher verlangt HTML die konsistente Anwendung der MIME-Sniffing-Regeln.

---

## Nonce

Nonces dienen der CSP-basierten Autorisierung und müssen vor
unbeabsichtigter Exposition geschützt werden.

---

## Lazy Loading

Lazy Loading enthält ausdrücklich eine Anti-Tracking-Regel für den Fall
deaktivierten Scriptings.

---

## Lazy Load Scroll Margin

Die Scroll Margin soll keine zusätzlichen Informationen über
Nutzerverhalten oder Geräteeigenschaften als Fingerprinting-Vektor
offenlegen.

---

# Querverweis auf die Informationsdimensionen

| Informationsdimension | Fetching-Relevanz |
|---|---|
| ID | FETCH-001 bis FETCH-011 |
| Bereich | Fetching Resources |
| Feature-Typ | Processing Concept / Attribute Family / Integration |
| Feature | siehe Inventar |
| WHATWG-Abschnitt | §2.5.1–§2.5.9 |
| Statussystem | WHATWG / ZE-WebLab V1 getrennt |
| Status | aktuell definiert |
| V1-Referenz | zweite Rechercheebene |
| ZE-WebLab-Kategorie | Fetching / Resource Processing |
| Content Categories | nicht auf Fetch selbst anwendbar |
| Context | elementabhängig |
| Content Model | nicht auf Fetch selbst anwendbar |
| Content Attributes | `crossorigin`, `referrerpolicy`, `nonce`, `loading`, `blocking`, `fetchpriority` |
| Accessibility | keine eigenständige Fetch-Semantik |
| Sanitization | nicht identisch mit Fetch |
| DOM Interface | elementabhängig |
| API | Fetch / Intersection Observer / CSP / Referrer Policy als externe bzw. integrierte APIs |
| Processing Model | zentral |
| normative Sonderregeln | umfangreich |
| Querverweise | URL, DOM, Elements, Fetch, MIME, Encoding, CSP |
| Quellen | WHATWG HTML + abhängige normative Standards |
| Prüfstatus | abgeschlossen |
| offene Fragen | siehe unten |

---

# Offene Punkte

## Allgemeiner Fetch Standard

Die vollständige Fetch-Spezifikation ist nicht Bestandteil dieser Datei.

Für Details zu:

- Request
- Response
- Fetch
- CORS Protocol
- Credentials
- Modes
- Destinations

ist der WHATWG Fetch Standard die maßgebliche normative Quelle.

---

## MIME Sniffing

Die vollständigen Sniffing-Algorithmen sind nicht Bestandteil dieser
Datei.

Dafür ist der WHATWG MIME Sniffing Standard maßgeblich.

---

## Character Encoding

Die vollständige Character-Encoding-Infrastruktur ist nicht Bestandteil
dieser Datei.

HTML definiert für §2.5.3 die HTML-spezifische Extraktion.

---

## Content Security Policy

Die vollständige CSP-Spezifikation ist nicht Bestandteil dieser Datei.

Dokumentiert wird ausschließlich die HTML-Integration des Nonce-Konzepts.

---

## Referrer Policy

Die vollständigen Referrer-Policy-Definitionen sind nicht Bestandteil
dieser Datei.

Dokumentiert wird die HTML-seitige Attribut- und Signalverarbeitung.

---

## Intersection Observer

Die vollständige Intersection Observer API ist nicht Bestandteil
dieser Datei.

Dokumentiert wird ausschließlich ihre Verwendung innerhalb des
HTML-Lazy-Loading-Modells.

---

## Keine künstlichen offenen Punkte

Für die geprüften §2.5-Unterabschnitte wurde keine ungeklärte normative
Lücke innerhalb des abgegrenzten HTML-Bereichs festgestellt.

Die oben genannten Abgrenzungen zu externen Standards sind keine
inhaltlichen offenen Punkte, sondern bewusst definierte
Quellengrenzen.

---

# Quellen / Referenzen

## Primärquelle

**WHATWG HTML Living Standard**

Relevanter Bereich:

- §2.5 Fetching resources
- §2.5.1 Terminology
- §2.5.2 Determining the type of a resource
- §2.5.3 Extracting character encodings from `meta` elements
- §2.5.4 CORS settings attributes
- §2.5.5 Referrer policy attributes
- §2.5.6 Nonce attributes
- §2.5.7 Lazy loading attributes
- §2.5.8 Blocking attributes
- §2.5.9 Fetch priority attributes

Geprüfter Stand:

**11. August 2026**

---

## Weitere normative Quellen

### WHATWG Fetch Standard

Verwendet für die Definition und Verarbeitung von:

- Request
- Response
- CORS
- Mode
- Credentials Mode
- Destination
- Fetch

---

### WHATWG MIME Sniffing Standard

Verwendet für:

- Content-Type-Verarbeitung
- Computed MIME Type
- Resource Type Determination
- Image/Text/Audio/Video Sniffing

---

### WHATWG Encoding Standard

Verwendet für:

- Character Encoding
- Encoding Lookup
- Character-Encoding-Ermittlung

---

### Content Security Policy

Verwendet für:

- Cryptographic Nonce
- CSP-basierte Autorisierung von Ressourcen

---

### Referrer Policy

Verwendet für:

- Referrer Policy States
- Referrer-Verarbeitung

---

### Intersection Observer

Verwendet für:

- Lazy Loading Intersection Observer
- Intersection-basierte Fortsetzung des Ressourcenladens

---

## ZE-WebLab-Projektquellen

Geprüfte bzw. abgegrenzte bestehende Dokumente:

- `docs/html/02-document-metadata.md`
- `docs/html/06-links.md`
- `docs/html/08-embedded-content.md`
- `docs/html/12-scripting.md`
- `docs/html/19-dom-interfaces-and-apis.md`
- `docs/html/20-sanitization.md`
- `docs/html/21-parsing.md`
- `docs/html/25-urls.md`

Besonders relevant:

`docs/html/25-urls.md`

definiert die Abgrenzung zwischen URL-Systematik und Fetching.

---

# Abschlussstatus

**Feature-Familie:** Fetching Resources

**Zielpfad:** `docs/html/26-fetching-resources.md`

**WHATWG-Abdeckung:** §2.5.1–§2.5.9 geprüft

**Elementinventar erweitert:** Nein

**Feature-Familie dokumentiert:** Ja

**Erste-Ebene-Überschneidungen geprüft:** Ja

**URL-Abgrenzung geprüft:** Ja

**DOM/API-Abgrenzung geprüft:** Ja

**Sanitization-Abgrenzung geprüft:** Ja

**Parsing-Abgrenzung geprüft:** Ja

**Externe normative Abhängigkeiten gekennzeichnet:** Ja

**Browser-Support als WHATWG-Status verwendet:** Nein

**Offene normative Lücke innerhalb §2.5:** Keine festgestellt

**Recherchebereich abgeschlossen:** Ja