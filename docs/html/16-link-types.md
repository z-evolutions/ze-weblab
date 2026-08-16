# ZE-WebLab – HTML-Referenz: Link Types

## Arbeitsstand / Quellenstand

**Rechercheebene:** 2 – übergreifende HTML-Konzepte und Feature-Familien

**Feature-Typ:** Link Type

**Zielpfad:** `docs/html/16-link-types.md`

**Normative Primärquelle:** WHATWG HTML Living Standard, §4.6.8 „Link types“ einschließlich der zugehörigen Unterabschnitte.

**Aktueller geprüfter WHATWG-Stand:** 17. Juli 2026, gemäß der aktuell veröffentlichten Living-Standard-Fassung.

**Projektquelle:** ZE-WebLab, insbesondere `docs/html/06-links.md` sowie die übrigen Elementreferenzen der ersten Rechercheebene.

### Abgrenzung

Link Types sind **keine HTML-Elemente**.

Ein Link Type ist ein normativ definiertes Keyword, das über das `rel`-Attribut eine Beziehung zwischen Ressourcen beschreibt oder ein bestimmtes Link-Verarbeitungsmodell aktiviert.

Link Types können je nach Definition:

- einen Hyperlink erzeugen,
- einen External Resource Link erzeugen,
- einen Internal Resource Link erzeugen,
- einen vorhandenen Hyperlink annotieren,
- oder mehrere dieser Funktionen in Kombination erfüllen.

Die HTML-Elemente `a`, `area`, `form` und `link` bleiben Bestandteil der Elementreferenz.

Diese Datei dokumentiert dagegen die übergreifende Link-Type-Systematik.

---

## Einordnung

WHATWG behandelt Links als konzeptionelles Konstrukt.

§4.6 „Links“ unterscheidet drei grundlegende Arten:

1. Links zu externen Ressourcen
2. Hyperlinks
3. interne Resource Links

Welche Art eines Links durch ein Element erzeugt wird, hängt unter anderem von den in `rel` angegebenen Link-Type-Keywords ab.

Die Link-Type-Definitionen befinden sich in §4.6.8.

Die aktuelle WHATWG-Struktur umfasst:

- `alternate`
- `author`
- `bookmark`
- `canonical`
- `dns-prefetch`
- `expect`
- `external`
- `help`
- `icon`
- `license`
- `manifest`
- `modulepreload`
- `nofollow`
- `noopener`
- `noreferrer`
- `opener`
- `pingback`
- `preconnect`
- `prefetch`
- `preload`
- `privacy-policy`
- `search`
- `stylesheet`
- `tag`
- `terms-of-service`
- `next`
- `prev`

Zusätzlich definiert WHATWG ein Modell für weitere bzw. registrierte Link Types.

Die Tabelle in §4.6.8 ist eine nicht-normative Übersicht; die normative Bedeutung ergibt sich aus den jeweiligen nachfolgenden Link-Type-Definitionen.

---

## WHATWG-Struktur

### §4.6 Links

Der übergeordnete Abschnitt behandelt:

- allgemeine Link-Konzepte,
- Link-Erzeugung,
- Hyperlink-APIs,
- Navigation,
- Downloads,
- Hyperlink Auditing,
- Link Types.

### §4.6.8 Link types

Die aktuelle Unterstruktur lautet:

| WHATWG | Link Type |
|---|---|
| 4.6.8.1 | `alternate` |
| 4.6.8.2 | `author` |
| 4.6.8.3 | `bookmark` |
| 4.6.8.4 | `canonical` |
| 4.6.8.5 | `dns-prefetch` |
| 4.6.8.6 | `expect` |
| 4.6.8.7 | `external` |
| 4.6.8.8 | `help` |
| 4.6.8.9 | `icon` |
| 4.6.8.10 | `license` |
| 4.6.8.11 | `manifest` |
| 4.6.8.12 | `modulepreload` |
| 4.6.8.13 | `nofollow` |
| 4.6.8.14 | `noopener` |
| 4.6.8.15 | `noreferrer` |
| 4.6.8.16 | `opener` |
| 4.6.8.17 | `pingback` |
| 4.6.8.18 | `preconnect` |
| 4.6.8.19 | `prefetch` |
| 4.6.8.20 | `preload` |
| 4.6.8.21 | `privacy-policy` |
| 4.6.8.22 | `search` |
| 4.6.8.23 | `stylesheet` |
| 4.6.8.24 | `tag` |
| 4.6.8.25 | `terms-of-service` |
| 4.6.8.26.1 | `next` |
| 4.6.8.26.2 | `prev` |
| 4.6.8.27 | Other link types |

Die Reihenfolge ist die aktuelle WHATWG-Struktur und nicht automatisch die Reihenfolge der ZE-WebLab-Dateien.

---

## Inventar

| ID | Feature | Feature-Typ | WHATWG | Linkwirkung |
|---|---|---|---|---|
| LT-001 | `alternate` | Link Type | §4.6.8.1 | Hyperlink bzw. Modifikation von `stylesheet` |
| LT-002 | `author` | Link Type | §4.6.8.2 | Hyperlink |
| LT-003 | `bookmark` | Link Type | §4.6.8.3 | Hyperlink |
| LT-004 | `canonical` | Link Type | §4.6.8.4 | Hyperlink |
| LT-005 | `dns-prefetch` | Link Type | §4.6.8.5 | External Resource Link |
| LT-006 | `expect` | Link Type | §4.6.8.6 | Internal Resource Link |
| LT-007 | `external` | Link Type | §4.6.8.7 | Hyperlink-Annotation |
| LT-008 | `help` | Link Type | §4.6.8.8 | Hyperlink |
| LT-009 | `icon` | Link Type | §4.6.8.9 | External Resource Link |
| LT-010 | `license` | Link Type | §4.6.8.10 | Hyperlink |
| LT-011 | `manifest` | Link Type | §4.6.8.11 | External Resource Link |
| LT-012 | `modulepreload` | Link Type | §4.6.8.12 | External Resource Link |
| LT-013 | `nofollow` | Link Type | §4.6.8.13 | Hyperlink-Annotation |
| LT-014 | `noopener` | Link Type | §4.6.8.14 | Hyperlink-Processing |
| LT-015 | `noreferrer` | Link Type | §4.6.8.15 | Hyperlink-Processing |
| LT-016 | `opener` | Link Type | §4.6.8.16 | Hyperlink-Processing |
| LT-017 | `pingback` | Link Type | §4.6.8.17 | External Resource Link |
| LT-018 | `preconnect` | Link Type | §4.6.8.18 | External Resource Link |
| LT-019 | `prefetch` | Link Type | §4.6.8.19 | External Resource Link |
| LT-020 | `preload` | Link Type | §4.6.8.20 | External Resource Link |
| LT-021 | `privacy-policy` | Link Type | §4.6.8.21 | Hyperlink |
| LT-022 | `search` | Link Type | §4.6.8.22 | Hyperlink |
| LT-023 | `stylesheet` | Link Type | §4.6.8.23 | External Resource Link |
| LT-024 | `tag` | Link Type | §4.6.8.24 | Hyperlink |
| LT-025 | `terms-of-service` | Link Type | §4.6.8.25 | Hyperlink |
| LT-026 | `next` | Link Type | §4.6.8.26.1 | Hyperlink |
| LT-027 | `prev` | Link Type | §4.6.8.26.2 | Hyperlink |
| LT-028 | Additional Link Types | Extension Model | §4.6.8.27 | abhängig von Registrierung |

---

## Begriffsdefinitionen

### Link Type

Ein Link Type ist ein Keyword, das über `rel` eine definierte Beziehung oder Verarbeitung eines Links angibt.

Die Keywords werden als ASCII-case-insensitive behandelt.

Damit sind beispielsweise:

```html
rel="next"
```

und:

```html
rel="NEXT"
```

dieselbe Link-Type-Angabe.

---

### `rel`

Das `rel`-Attribut enthält eine durch ASCII-Whitespace getrennte Menge von Tokens.

Die Tokens repräsentieren Link Types.

Außer wenn ausdrücklich anders spezifiziert, darf ein Keyword nicht mehrfach innerhalb desselben `rel`-Attributs angegeben werden.

Beispiel:

```html
<a href="/next" rel="next">Weiter</a>
```

---

### Link Type und Element

Ein Link Type ist nicht an ein einziges HTML-Element gebunden.

Die jeweilige Definition legt fest, auf welchen Elementen das Keyword verwendet werden darf.

Je nach Link Type kommen insbesondere folgende Elemente infrage:

- `link`
- `a`
- `area`
- `form`

Nicht jedes Keyword ist für jedes dieser Elemente zulässig.

---

### Hyperlink

Ein Hyperlink ist ein Link, der typischerweise zur Navigation zu einer anderen Ressource verwendet wird.

Viele Link Types erzeugen einen Hyperlink.

Andere Link Types erzeugen keinen eigenen Hyperlink, sondern annotieren einen bereits vorhandenen Hyperlink.

---

### External Resource Link

Ein External Resource Link verbindet das Dokument mit einer Ressource, die vom User Agent verarbeitet werden kann.

Typische Beispiele:

- `stylesheet`
- `icon`
- `manifest`
- `preload`
- `modulepreload`
- `preconnect`
- `prefetch`
- `dns-prefetch`

Für External Resource Links existieren Fetch-and-Process-Verarbeitungsmodelle.

---

### Internal Resource Link

Ein Internal Resource Link verweist auf eine Ressource innerhalb des aktuellen Dokuments und verleiht dieser Ressource eine besondere Bedeutung oder ein bestimmtes Verhalten.

Der aktuelle WHATWG-Link-Type hierfür ist insbesondere:

```text
expect
```

---

### Hyperlink Annotation

Ein Link Type kann einen bereits vorhandenen Hyperlink annotieren, ohne selbst einen eigenständigen Hyperlink zu erzeugen.

Beispiele sind:

- `external`
- `nofollow`
- bestimmte Processing-Keywords wie `noopener`, `noreferrer` und `opener`

Die genaue Wirkung ist jeweils der Link-Type-Definition zu entnehmen.

---

## Normative Regeln

### Regel LT-R001 – Keywords sind ASCII-case-insensitive

Link-Type-Keywords werden ohne Unterscheidung zwischen Groß- und Kleinschreibung verglichen.

---

### Regel LT-R002 – `rel` ist eine Token-Menge

Das `rel`-Attribut wird als Menge von durch ASCII-Whitespace getrennten Keywords verarbeitet.

---

### Regel LT-R003 – Doppelte Keywords

Außer bei ausdrücklich anders definierten Regeln darf ein Link-Type-Keyword nicht mehrfach im selben `rel`-Attribut erscheinen.

---

### Regel LT-R004 – Link Types bestimmen Linkwirkung

Die jeweilige Link-Type-Definition bestimmt, ob das Keyword:

- einen Hyperlink,
- einen External Resource Link,
- einen Internal Resource Link,
- eine Hyperlink Annotation

oder eine entsprechende Kombination erzeugt.

---

### Regel LT-R005 – Ein Element kann mehrere Links erzeugen

Ein einzelnes `link`-Element kann aufgrund mehrerer `rel`-Keywords mehrere Links erzeugen.

Beispiel:

```html
<link rel="next stylesheet" href="/resource">
```

kann entsprechend der einzelnen Link-Type-Semantik sowohl einen Hyperlink als auch einen External Resource Link erzeugen.

Die Verarbeitung erfolgt pro erzeugtem Link und nicht lediglich einmal pro Element.

---

### Regel LT-R006 – `a` und `area` besitzen einen impliziten Hyperlink

Ein `a`- oder `area`-Element mit `href` erzeugt einen Hyperlink auch dann, wenn kein `rel` vorhanden ist oder die vorhandenen `rel`-Keywords keinen Hyperlink erzeugen.

Dieser implizite Hyperlink besitzt keine besondere Link-Type-Semantik.

---

### Regel LT-R007 – Zulässige Elemente sind Link-Type-spezifisch

Es darf nicht angenommen werden, dass ein Link Type auf allen Link-erzeugenden Elementen zulässig ist.

Die jeweilige Definition legt die erlaubten Elemente fest.

---

### Regel LT-R008 – Body-OK-Link-Types

Bestimmte Link Types erlauben, dass ein `link`-Element im `body` verwendet wird.

Die aktuelle WHATWG-Liste der entsprechenden body-ok Keywords umfasst:

- `dns-prefetch`
- `modulepreload`
- `pingback`
- `preconnect`
- `prefetch`
- `preload`
- `stylesheet`

Diese Eigenschaft ist eine normative Einordnung für `link` und darf nicht auf beliebige `rel`-Keywords übertragen werden.

---

### Regel LT-R009 – Synonyme

WHATWG definiert bei bestimmten Link Types historische Synonyme.

Solche Synonyme können von User Agents unterstützt werden, sollen aber nicht von Autoren verwendet werden, sofern die Definition dies entsprechend festlegt.

Beispiel:

```text
previous
```

ist ein historisches Synonym für:

```text
prev
```

---

### Regel LT-R010 – Erweiterte Link Types

Link Types außerhalb des vordefinierten HTML-Inventars können nach dem von WHATWG beschriebenen Extension-Modell registriert werden.

Sie werden dadurch nicht automatisch zu nativen HTML-Elementen.

---

# Detailprüfung

## LT-001 – `alternate`

**WHATWG:** §4.6.8.1

`alternate` bezeichnet eine alternative Darstellung des aktuellen Dokuments.

Das Keyword kann auf:

- `link`
- `a`
- `area`

verwendet werden.

Bei `link` besitzt `alternate` eine besondere Interaktion mit `stylesheet`.

Wenn `alternate` gemeinsam mit `stylesheet` verwendet wird, modifiziert es die Bedeutung von `stylesheet` und erzeugt nicht zusätzlich eine eigenständige alternative Hyperlink-Beziehung.

In anderen Fällen bezeichnet `alternate` eine alternative Repräsentation des aktuellen Dokuments.

`hreflang` kann dabei eine sprachliche Alternative anzeigen.

`type` kann den Medientyp bzw. das Format der alternativen Ressource angeben.

---

## LT-002 – `author`

**WHATWG:** §4.6.8.2

`author` bezeichnet eine Ressource mit weiteren Informationen über den Autor.

Bei `a` und `area` bezieht sich die Beziehung auf den Autor des nächstgelegenen `article`-Elements, sofern ein solches vorhanden ist; andernfalls auf den Autor der Seite als Ganzes.

Bei `link` bezieht sie sich auf den Autor der Seite als Ganzes.

`author` erzeugt einen Hyperlink.

Ein historisches `rev="made"` wird von User Agents entsprechend der WHATWG-Regel als `author` behandelt.

---

## LT-003 – `bookmark`

**WHATWG:** §4.6.8.3

`bookmark` bezeichnet einen Permalink für den relevanten Abschnitt des Dokuments.

Das Keyword kann auf:

- `a`
- `area`

verwendet werden.

Die Zuordnung erfolgt anhand des relevanten umgebenden Abschnitts bzw. `article`-Kontexts.

---

## LT-004 – `canonical`

**WHATWG:** §4.6.8.4

`canonical` bezeichnet die bevorzugte URL für das aktuelle Dokument.

Das Keyword darf auf `link` verwendet werden.

Die normative Definition verweist für die genauere Semantik auf die Canonical-Link-Relation.

`canonical` ist damit nicht mit einer generischen Hyperlink-Navigation gleichzusetzen.

---

## LT-005 – `dns-prefetch`

**WHATWG:** §4.6.8.5

`dns-prefetch` weist den User Agent an, DNS-Auflösung für die Origin der Zielressource vorzeitig durchzuführen.

Das Keyword erzeugt einen External Resource Link.

Es ist body-ok.

---

## LT-006 – `expect`

**WHATWG:** §4.6.8.6

`expect` bezeichnet einen internen Link zu einem Element, dessen Ziel-ID angegeben ist.

Das Keyword erzeugt einen Internal Resource Link.

Damit unterscheidet es sich von normalen Hyperlinks, die typischerweise zu einer Navigation zu einer Ressource führen.

Die interne Zielressource wird über die entsprechende Ziel-ID bestimmt.

---

## LT-007 – `external`

**WHATWG:** §4.6.8.7

`external` kennzeichnet, dass der referenzierte Inhalt nicht Teil derselben Site wie das aktuelle Dokument ist.

Das Keyword kann auf:

- `a`
- `area`
- `form`

verwendet werden.

`external` erzeugt keinen eigenständigen Hyperlink.

Es annotiert andere durch das Element erzeugte Hyperlinks.

---

## LT-008 – `help`

**WHATWG:** §4.6.8.8

`help` bezeichnet eine Ressource mit kontextbezogenen Hilfeinformationen.

Das Keyword kann auf:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Bei `a`, `area` und `form` bezieht sich die Hilfe auf das Element und seine Kinder.

Bei `link` bezieht sie sich auf die Seite als Ganzes.

`help` erzeugt einen Hyperlink.

---

## LT-009 – `icon`

**WHATWG:** §4.6.8.9

`icon` bezeichnet eine externe Ressource, die als Symbol bzw. Icon für das aktuelle Dokument verwendet werden kann.

Das Keyword ist für `link` definiert.

Es erzeugt einen External Resource Link.

---

## LT-010 – `license`

**WHATWG:** §4.6.8.10

`license` bezeichnet eine Ressource, die die Lizenzbedingungen des Hauptinhalts des aktuellen Dokuments beschreibt.

Das Keyword kann auf:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Es erzeugt einen Hyperlink.

Die Spezifikation überlässt die konkrete Abgrenzung des Hauptinhalts der Dokumentstruktur bzw. dem jeweiligen Kontext.

---

## LT-011 – `manifest`

**WHATWG:** §4.6.8.11

`manifest` bezeichnet eine Web-App-Manifest-Ressource für das aktuelle Dokument.

Das Keyword kann auf `link` verwendet werden.

Es erzeugt einen External Resource Link.

Die Verarbeitung umfasst ein eigenes Fetch-and-Process-Modell.

---

## LT-012 – `modulepreload`

**WHATWG:** §4.6.8.12

`modulepreload` bezeichnet eine Ressource, die als JavaScript-Modul für eine spätere bzw. aktuelle Modulverarbeitung vorab geladen werden soll.

Das Keyword kann auf `link` verwendet werden.

Es erzeugt einen External Resource Link.

Es ist body-ok.

Das Verarbeitungsmodell steht in Beziehung zum JavaScript-Modul- und Fetch-Modell.

---

## LT-013 – `nofollow`

**WHATWG:** §4.6.8.13

`nofollow` annotiert einen Hyperlink und gibt an, dass der Link nicht als vom Autor bestätigte bzw. unterstützte Beziehung interpretiert werden soll.

Das Keyword ist für Hyperlink-Elemente definiert.

Es erzeugt keinen separaten External Resource Link.

Die genaue Bedeutung für externe Systeme, insbesondere Suchmaschinen, darf nicht über die WHATWG-Definition hinaus verallgemeinert werden.

---

## LT-014 – `noopener`

**WHATWG:** §4.6.8.14

`noopener` aktiviert das `noopener`-Verhalten bei Hyperlink-Navigation.

Das Keyword verhindert insbesondere die entsprechende `opener`-Beziehung des neu geöffneten Browsing Contexts.

Es ist Teil des Navigations-Processing-Models.

Die tatsächliche Navigation und die Bestimmung des Ziel-Navigable werden durch das Hyperlink-Processing-Modell geregelt.

---

## LT-015 – `noreferrer`

**WHATWG:** §4.6.8.15

`noreferrer` beeinflusst die Navigation eines Hyperlinks.

Es bewirkt insbesondere eine Referrer Policy von `no-referrer`.

Darüber hinaus führt `noreferrer` entsprechend dem WHATWG-Navigationsmodell zu `noopener`-Verhalten.

Damit besitzt `noreferrer` sowohl:

- Referrer-bezogene
- als auch Browsing-Context-bezogene

Auswirkungen.

---

## LT-016 – `opener`

**WHATWG:** §4.6.8.16

`opener` beeinflusst das Verhalten eines Links hinsichtlich der Erhaltung einer `opener`-Beziehung.

Es steht insbesondere in Beziehung zu:

- `target`
- `_blank`
- `noopener`
- `noreferrer`

Die genaue Wirkung ergibt sich aus dem Hyperlink-Navigationsmodell.

---

## LT-017 – `pingback`

**WHATWG:** §4.6.8.17

`pingback` bezeichnet eine Pingback-Ressource.

Das Keyword ist für `link` definiert und ist body-ok.

Es erzeugt einen External Resource Link.

Die konkrete Pingback-Funktionalität ist von der entsprechenden Pingback-Spezifikation abhängig.

---

## LT-018 – `preconnect`

**WHATWG:** §4.6.8.18

`preconnect` weist den User Agent an, möglichst früh eine Verbindung zur Origin der Zielressource vorzubereiten.

Das Keyword erzeugt einen External Resource Link.

Es ist body-ok.

Die konkrete Verbindungsoptimierung bleibt Bestandteil des User-Agent-Processing-Models.

---

## LT-019 – `prefetch`

**WHATWG:** §4.6.8.19

`prefetch` signalisiert, dass eine Ressource für eine zukünftige Verwendung vorab abgerufen werden kann.

Das Keyword erzeugt einen External Resource Link.

Es ist body-ok.

Die Spezifikation definiert entsprechende Fetch-and-Process-Regeln.

---

## LT-020 – `preload`

**WHATWG:** §4.6.8.20

`preload` signalisiert, dass eine Ressource frühzeitig für die aktuelle Navigation bzw. das aktuelle Dokument geladen werden soll.

Das Keyword erzeugt einen External Resource Link.

Es ist body-ok.

Die Verarbeitung hängt unter anderem von Attributen wie:

- `as`
- `crossorigin`
- `media`
- `type`

ab.

Die konkrete Ressourcennutzung ist Teil des Preload-Processing-Modells.

---

## LT-021 – `privacy-policy`

**WHATWG:** §4.6.8.21

`privacy-policy` bezeichnet eine Ressource mit Informationen über Datenerhebung und Datennutzung, die für das aktuelle Dokument gelten.

Das Keyword kann auf:

- `link`
- `a`
- `area`

verwendet werden.

Es erzeugt einen Hyperlink.

Die Definition verweist ergänzend auf die entsprechende zusätzliche Link-Relation.

---

## LT-022 – `search`

**WHATWG:** §4.6.8.22

`search` bezeichnet eine Ressource bzw. Schnittstelle, die der Suche über das Dokument und zugehörige Ressourcen dient.

Das Keyword kann auf:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Es erzeugt einen Hyperlink.

Bei `link` kann die Beziehung unter anderem für die automatische Erkennung von Suchschnittstellen verwendet werden.

---

## LT-023 – `stylesheet`

**WHATWG:** §4.6.8.23

`stylesheet` bezeichnet ein CSS-Stylesheet, das zur Darstellung des Dokuments beiträgt.

Das Keyword kann auf `link` verwendet werden.

Es erzeugt einen External Resource Link.

Es ist body-ok.

Das Standard-MIME-Type-Modell für `stylesheet` ist `text/css`.

Ein `link`-Element mit `stylesheet` kann insbesondere:

- render-blockierend wirken,
- durch `media` bedingt verarbeitet werden,
- durch `disabled` deaktiviert werden,
- durch `crossorigin` beeinflusst werden,
- durch `type` hinsichtlich der Ressourcenverarbeitung eingeschränkt werden.

Wird `alternate` zusätzlich angegeben, entsteht ein alternatives Stylesheet und `title` erhält eine besondere Bedeutung.

---

## LT-024 – `tag`

**WHATWG:** §4.6.8.24

`tag` bezeichnet eine Ressource, die ein Tag repräsentiert, das auf das aktuelle Dokument angewendet wird.

Das Keyword kann auf:

- `a`
- `area`

verwendet werden.

Es erzeugt einen Hyperlink.

Die Beziehung bezeichnet den Tag als für das aktuelle Dokument relevant.

---

## LT-025 – `terms-of-service`

**WHATWG:** §4.6.8.25

`terms-of-service` bezeichnet eine Ressource mit Informationen über die Vereinbarungen zwischen dem Anbieter des aktuellen Dokuments und Benutzern, die das Dokument nutzen möchten.

Das Keyword kann auf:

- `link`
- `a`
- `area`

verwendet werden.

Es erzeugt einen Hyperlink.

Die Definition verweist ergänzend auf die entsprechende zusätzliche Link-Relation.

---

# Sequenzielle Link Types

## LT-026 – `next`

**WHATWG:** §4.6.8.26.1

`next` bezeichnet das nächste logische Dokument einer Dokumentsequenz.

Das Keyword kann auf:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Es erzeugt einen Hyperlink.

Bei `link` kann der User Agent das Ziel entsprechend den von WHATWG beschriebenen Vorab-Lade- bzw. Verbindungsmechanismen behandeln.

---

## LT-027 – `prev`

**WHATWG:** §4.6.8.26.2

`prev` bezeichnet das vorherige logische Dokument einer Dokumentsequenz.

Das Keyword kann auf:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Es erzeugt einen Hyperlink.

Das historische Keyword:

```text
previous
```

ist als Synonym für `prev` definiert.

Autoren sollen das Synonym nicht anstelle von `prev` verwenden.

---

## Other Link Types

### LT-028 – Erweiterte Link Types

**WHATWG:** §4.6.8.27

WHATWG erlaubt zusätzliche Link Types außerhalb der unmittelbar in HTML definierten Liste.

Ein solcher Link Type muss entsprechend dem beschriebenen Extension-Modell registriert bzw. spezifiziert werden.

Für einen Extension Link Type werden unter anderem Informationen benötigt über:

- Keyword
- Wirkung auf `link`
- Wirkung auf `a` und `area`
- Wirkung auf `form`
- kurze Beschreibung
- Spezifikation
- Synonyme

### Keyword

Ein Extension Keyword darf nicht verwirrend ähnlich zu einem bereits definierten Keyword sein.

Enthält es einen Doppelpunkt (`:`), muss es eine absolute URL sein.

### Wirkung auf `link`

Für `link` kann ein Extension Link Type insbesondere als:

- nicht erlaubt,
- Hyperlink,
- External Resource Link

definiert werden.

### Wirkung auf `a` und `area`

Für `a` und `area` sind insbesondere möglich:

- nicht erlaubt,
- Hyperlink,
- External Resource Link,
- Hyperlink Annotation.

### Wirkung auf `form`

Für `form` sind ebenfalls möglich:

- nicht erlaubt,
- Hyperlink,
- External Resource Link,
- Hyperlink Annotation.

### Status

Ein Extension Link Type wird dadurch nicht zu einem nativen HTML-Element.

Er bleibt ein Link-Type-Konzept.

---

## Attribute

### `rel`

`rel` ist das zentrale Attribut für Link Types.

Es enthält die Link-Type-Keywords als ASCII-Whitespace-getrennte Tokens.

Die konkrete zulässige Tokenmenge hängt vom verwendeten Element und dem jeweiligen Link Type ab.

---

### `href`

`href` identifiziert bei den entsprechenden Link-erzeugenden Elementen die Zielressource.

Ein `rel`-Keyword allein erzeugt nicht automatisch einen Link, wenn die betreffende Elementdefinition die dafür erforderlichen Voraussetzungen nicht erfüllt.

---

### `type`

`type` kann insbesondere bei `alternate`, `stylesheet`, `preload` und anderen ressourcenbezogenen Beziehungen relevant sein.

Bei Hyperlinks ist der Wert grundsätzlich eine MIME-Type-Angabe mit lediglich beratender Wirkung.

Der User Agent darf die tatsächliche Ressourcentypisierung nicht ausschließlich aufgrund des `type`-Attributs bestimmen.

---

### `hreflang`

`hreflang` beschreibt die erwartete Sprache der referenzierten Ressource.

Es besitzt insbesondere für `alternate` eine relevante semantische Funktion.

---

### `media`

`media` kann bei ressourcenbezogenen Link Types die Umgebungsbedingungen für die Ressourcenverarbeitung einschränken.

Es ist insbesondere für `stylesheet`, `preload` und `alternate` relevant.

---

### `as`

`as` ist insbesondere für `preload` relevant.

Es beschreibt die vorgesehene Destination bzw. den Typ der vorab geladenen Ressource.

Die konkrete Verarbeitung erfolgt gemäß dem Preload-Modell.

---

### `crossorigin`

`crossorigin` kann die Fetch-Verarbeitung von External Resource Links beeinflussen.

Es ist insbesondere für ressourcenbezogene Link Types wie `stylesheet`, `preload` und `modulepreload` relevant.

---

### `title`

`title` kann insbesondere bei alternativen Stylesheets eine besondere Funktion besitzen.

Bei `rel="alternate stylesheet"` ist ein nichtleerer `title` für die entsprechende Stylesheet-Behandlung erforderlich.

---

### `disabled`

`disabled` beeinflusst insbesondere die Aktivierung bzw. Verarbeitung eines Stylesheets.

Die entsprechende Verarbeitung gehört zum `stylesheet`-Processing-Model.

---

## Content Categories

Link Types selbst besitzen keine Content Categories.

Die beteiligten Elemente besitzen diese weiterhin entsprechend ihrer eigenen Elementdefinition.

Beispiel:

```text
rel="stylesheet"
```

ist kein Content Category Feature.

Das `link`-Element bleibt ein HTML-Element mit seinem eigenen Context und Content Model.

---

## Context

Link Types besitzen keinen eigenen allgemeinen HTML-Context.

Der zulässige Verwendungskontext wird durch die Kombination aus:

- Elementdefinition,
- verwendeten Attributen,
- Link-Type-Definition,
- gegebenenfalls weiteren Content-Model-Regeln

bestimmt.

Beispiel:

`stylesheet` ist für `link` definiert.

Daraus folgt nicht, dass `stylesheet` selbst einen HTML-Context besitzt.

---

## Content Model

Link Types besitzen kein eigenes Content Model.

Das Content Model gehört zum jeweiligen HTML-Element.

Damit gilt:

```text
Link Type ≠ Content Model
```

und:

```text
rel="preload"
```

ist kein Inhaltsmodell.

---

## Processing Models

Link Types können unmittelbar mit Processing Models verbunden sein.

Besonders relevant sind:

- `stylesheet`
- `preload`
- `modulepreload`
- `prefetch`
- `preconnect`
- `dns-prefetch`
- `manifest`
- `icon`
- `noopener`
- `noreferrer`
- `opener`
- `expect`

### Link-Erzeugung

Die `rel`-Tokens werden verarbeitet und erzeugen je nach Link Type unterschiedliche Link-Objekte bzw. Linkbeziehungen.

### External Resource Processing

External Resource Links besitzen ein Fetch-and-Process-Modell.

Dabei können unter anderem folgende Bedingungen relevant sein:

- URL
- `type`
- `media`
- `crossorigin`
- `as`
- Dokumentstatus
- Browsing-Context-Verbindung.

### Hyperlink Navigation

Hyperlink-Link Types stehen in Beziehung zum Navigationsmodell.

Insbesondere:

- `noopener`
- `noreferrer`
- `opener`

verändern die Verarbeitung beim Folgen eines Hyperlinks.

---

## DOM Interfaces / APIs

Link Types sind keine DOM Interfaces.

Das `rel`-Attribut wird jedoch über die DOM-APIs der jeweiligen Elemente repräsentiert.

Beispiele:

- `HTMLAnchorElement`
- `HTMLAreaElement`
- `HTMLLinkElement`
- `HTMLFormElement`

Die DOM-Interfaces stellen die Attribute und Elementfunktionalität bereit.

Die Semantik eines `rel`-Tokens stammt dagegen aus dem Link-Type-Modell.

---

## Accessibility

Link Types besitzen keine pauschale Accessibility-Bedeutung.

Die Auswirkungen auf die Zugänglichkeit hängen unter anderem vom verwendeten Element und dem resultierenden Linkverhalten ab.

Beispielsweise kann `help` eine semantische Beziehung zu Hilfeinformationen ausdrücken.

Aus einem Link Type darf jedoch nicht automatisch eine vollständige Accessibility-Anforderung abgeleitet werden.

Accessibility-Aussagen sind daher anhand der jeweils einschlägigen WHATWG-Regeln und gegebenenfalls externer Accessibility-Spezifikationen zu prüfen.

---

## Sanitization

Link Types sind nicht mit Sanitization-Regeln gleichzusetzen.

Die bloße Existenz eines `rel`-Keywords bestimmt nicht automatisch, ob ein Element bei Sanitization entfernt, behalten oder verändert wird.

Für Sanitization ist die dafür zuständige WHATWG-Systematik separat zu prüfen.

---

## Konformitätsregeln

### Zulässiges Element

Jeder Link Type darf nur auf den in seiner Definition erlaubten Elementen verwendet werden.

Beispielsweise ist:

```html
<link rel="stylesheet" href="/style.css">
```

normativ anders zu behandeln als eine beliebige Verwendung:

```html
<a rel="stylesheet" href="/style.css">
```

Das zweite Beispiel darf nicht aus der bloßen Existenz des Keywords als konform angenommen werden.

---

### Einmalige Keywords

Link-Type-Keywords dürfen grundsätzlich nicht mehrfach im selben `rel`-Attribut angegeben werden.

Beispiel:

```html
<a href="/next" rel="next next">Weiter</a>
```

ist nicht die konforme Schreibweise für ein einzelnes `next`-Keyword.

---

### Groß-/Kleinschreibung

Die Keyword-Erkennung ist ASCII-case-insensitive.

```html
<a href="/next" rel="NEXT">Weiter</a>
```

wird hinsichtlich des Keywords wie `next` behandelt.

---

### Unbekannte Keywords

Ein unbekanntes `rel`-Keyword darf nicht automatisch wie ein bekanntes WHATWG-Link-Type-Keyword behandelt werden.

Insbesondere darf aus einem beliebigen Token nicht geschlossen werden, dass ein bestimmtes Processing Model ausgeführt wird.

---

### Mehrere Link Types

Mehrere Link Types können in einem `rel`-Attribut kombiniert werden.

Beispiel:

```html
<link rel="alternate stylesheet" href="/print.css" title="Print">
```

Die einzelnen Keywords können gemeinsam eine kombinierte Bedeutung erzeugen.

Bei bestimmten Kombinationen modifiziert ein Keyword die Wirkung eines anderen, anstatt einen vollständig unabhängigen Link zu erzeugen.

---

## Querverweise

### Link Type ↔ `rel`

`rel` ist die zentrale Markup-Schnittstelle zur Angabe von Link Types.

---

### Link Type ↔ `link`

`link` verwendet Link Types insbesondere für:

- externe Ressourcen,
- Preloading,
- Stylesheets,
- Icons,
- Manifeste,
- alternative Darstellungen,
- sequenzielle Dokumentbeziehungen.

---

### Link Type ↔ `a`

`a` verwendet Link Types insbesondere für semantische Hyperlink-Beziehungen und Navigationsverhalten.

---

### Link Type ↔ `area`

`area` verwendet Link Types analog zu Hyperlinks in Image Maps, soweit die jeweilige Link-Type-Definition dies erlaubt.

---

### Link Type ↔ `form`

`form` kann Link Types für die Formularnavigation und entsprechende Hyperlink-Beziehungen verwenden.

Nicht jeder Link Type ist für `form` zulässig.

---

### Link Type ↔ Navigation

Die Link Types:

- `noopener`
- `noreferrer`
- `opener`
- `next`
- `prev`

stehen in direkter Beziehung zum Hyperlink-Navigationsmodell.

---

### Link Type ↔ Fetch

Die External Resource Link Types stehen in Beziehung zum Fetch- und Ressourcenverarbeitungsmodell.

Besonders relevant:

- `stylesheet`
- `preload`
- `modulepreload`
- `prefetch`
- `preconnect`
- `dns-prefetch`
- `manifest`
- `icon`

---

### Link Type ↔ Referrer Policy

`noreferrer` besitzt eine unmittelbare Beziehung zur Referrer Policy.

Bei diesem Link Type wird die Hyperlink Referrer Policy entsprechend dem WHATWG-Navigationsmodell auf `no-referrer` gesetzt.

---

### Link Type ↔ Content Categories

Keine direkte Kategoriebeziehung.

Die beteiligten Elemente besitzen ihre eigenen Content Categories.

---

### Link Type ↔ Content Models

Keine direkte eigene Content-Model-Dimension.

Die Content Models gehören zu den Elementen.

---

## Status / V1

### WHATWG-Status

Die oben aufgeführten Link Types sind in der aktuellen WHATWG HTML Living Standard definiert.

**Status:** definiert.

**Normative Definition:** ja.

**Normative Konformitätsregeln:** ja.

**Processing Model:** abhängig vom Link Type.

**Browser-Kompatibilität:** nicht Bestandteil dieser Statusbewertung.

---

### ZE-WebLab-V1

**V1-Einstufung:** übergreifende Feature-Familie.

**Begründung:**

Die erste Ebene behandelt Links primär im Zusammenhang mit den Elementen `a`, `area`, `link` und `form`.

Die vollständige Link-Type-Systematik ist jedoch kein Elementinventar und bildet daher eine eigenständige zweite-Ebenen-Feature-Familie.

---

## Erste-Ebene-Abdeckung

Die vorhandene Datei:

```text
docs/html/06-links.md
```

behandelt bereits den WHATWG-Bereich §4.6 ausführlich.

Die Bestandsprüfung zeigt insbesondere:

- Link-Konzept
- `a`/`area`-Linkerzeugung
- `form`-Linkfunktion
- `HyperlinkElementUtils`
- `HTMLHyperlinkElementUtils`
- Navigation
- Downloads
- Hyperlink Auditing
- `Ping-From` / `Ping-To`
- vollständige aktuelle Link-Type-Unterstruktur

sind dort bereits berücksichtigt.

### Warum trotzdem eine zweite Datei?

`06-links.md` ist eine übergreifende Links-Datei der ersten Rechercheebene und behandelt §4.6 als Gesamtthema.

Die Link Types bilden darin einen eigenen normativen Unterbereich.

Die zweite Ebene abstrahiert diesen Unterbereich zu einer eigenständigen Feature-Familie:

```text
06-links.md
    ↓
Link-System insgesamt

16-link-types.md
    ↓
Link-Type-System als eigenständige Feature-Familie
```

Es handelt sich damit nicht um eine Behauptung, dass Link Types in ZE-WebLab zuvor fehlten.

Vielmehr wird die bereits vorhandene element-/bereichsbezogene Dokumentation auf Feature-Ebene weitergeführt.

---

## Abdeckungsstatus

### Bereits in Ebene 1 vorhanden

- `rel` im Kontext von Links
- grundlegende Linkerzeugung
- Link-Type-Unterabschnitte
- Link-Type-Keywords
- Beziehungen zu `link`, `a`, `area` und `form`
- Processing Model einzelner Link Types

### Ebene 2 – eigenständig erforderlich

- Link Type als eigener Feature-Typ
- vollständiges Link-Type-Inventar
- normative Klassifizierung nach Linkwirkung
- Elementzulässigkeit pro Link Type
- body-ok-Eigenschaft
- Synonymmodell
- Extension-Modell
- Beziehungen zwischen Link Types
- Abgrenzung zu Elementen
- Abgrenzung zu Content Categories
- Abgrenzung zu Content Models
- Abgrenzung zu APIs
- Feature-Level-Status

### Nicht Bestandteil dieser Datei

- vollständige Navigation
- vollständiges Download-Processing
- vollständiges Hyperlink-Auditing
- vollständige URL-Spezifikation
- vollständige Referrer-Policy-Spezifikation
- vollständige Fetch-Spezifikation
- vollständige Web-App-Manifest-Spezifikation
- vollständige CSS-Spezifikation

Diese Bereiche werden über Querverweise referenziert und sind eigenständige normative Themen.

---

## Offene Punkte

### LT-O001 – Erweiterte Link Types

WHATWG beschreibt ein Extension-/Registrierungsmodell für weitere Link Types.

Die Existenz eines registrierten externen Link Types bedeutet nicht automatisch, dass dieser Bestandteil des nativen HTML-Link-Type-Inventars ist.

**Status:** geklärt; externe Erweiterungen sind vom nativen Inventar zu unterscheiden.

---

### LT-O002 – Externe Spezifikationen

Einige Link-Type-Definitionen verweisen für die vollständige Semantik auf externe Spezifikationen.

Beispiele sind:

- Canonical Link Relation
- Web App Manifest
- Pingback
- zusätzliche Link Relations

**Status:** für die HTML-Referenz als externe normative Querverweise zu behandeln.

---

### LT-O003 – Browser-Support

Browser-Kompatibilität ist ausdrücklich nicht Bestandteil der WHATWG-Statusbewertung.

**Status:** separate Rechercheebene.

---

## Quellen / Referenzen

### Primärquelle

**WHATWG HTML Living Standard – §4.6 Links**

Relevante Unterabschnitte:

- §4.6.1 Introduction
- §4.6.2 Links created by `a` and `area` elements
- §4.6.3 API for hyperlink elements
- §4.6.4 API for `a` and `area` elements
- §4.6.5 Following hyperlinks
- §4.6.6 Downloading resources
- §4.6.7 Hyperlink auditing
- §4.6.7.1 The `Ping-From` and `Ping-To` headers
- §4.6.8 Link types
- §4.6.8.1 `alternate`
- §4.6.8.2 `author`
- §4.6.8.3 `bookmark`
- §4.6.8.4 `canonical`
- §4.6.8.5 `dns-prefetch`
- §4.6.8.6 `expect`
- §4.6.8.7 `external`
- §4.6.8.8 `help`
- §4.6.8.9 `icon`
- §4.6.8.10 `license`
- §4.6.8.11 `manifest`
- §4.6.8.12 `modulepreload`
- §4.6.8.13 `nofollow`
- §4.6.8.14 `noopener`
- §4.6.8.15 `noreferrer`
- §4.6.8.16 `opener`
- §4.6.8.17 `pingback`
- §4.6.8.18 `preconnect`
- §4.6.8.19 `prefetch`
- §4.6.8.20 `preload`
- §4.6.8.21 `privacy-policy`
- §4.6.8.22 `search`
- §4.6.8.23 `stylesheet`
- §4.6.8.24 `tag`
- §4.6.8.25 `terms-of-service`
- §4.6.8.26.1 `next`
- §4.6.8.26.2 `prev`
- §4.6.8.27 Other link types

### Projektquelle

**ZE-WebLab**

Relevante Bestandsdatei:

```text
docs/html/06-links.md
```

Diese Datei behandelt bereits den vollständigen Links-Bereich §4.6 einschließlich der Link-Type-Struktur.

Die vorliegende Datei stellt daher keine Behauptung einer fehlenden Erste-Ebenen-Dokumentation auf, sondern führt die Link Types als eigenständige Feature-Familie der Rechercheebene 2.

---

## Prüfstatus

**Feature-Familie:** Link Types

**Rechercheebene:** 2

**WHATWG §4.6.8 geprüft:** Ja

**Alle aktuell definierten HTML-Link-Types geprüft:** Ja

**Sequential Link Types geprüft:** Ja

**Extension-Modell geprüft:** Ja

**`rel`-Tokenmodell geprüft:** Ja

**Elementzulässigkeit berücksichtigt:** Ja

**body-ok berücksichtigt:** Ja

**Synonyme berücksichtigt:** Ja

**Hyperlink / External Resource / Internal Resource unterschieden:** Ja

**Processing Models berücksichtigt:** Ja

**DOM/API-Abgrenzung berücksichtigt:** Ja

**Content Categories abgegrenzt:** Ja

**Content Models abgegrenzt:** Ja

**Browser-Support nicht als WHATWG-Status verwendet:** Ja

**Erste-Ebene-Bestand `06-links.md` berücksichtigt:** Ja

**Abschlussstatus:** Recherche der Feature-Familie `Link Types` abgeschlossen.