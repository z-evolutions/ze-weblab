# ZE-WebLab – HTML-Dokumentation: Links

## Arbeits- und Recherchestand

**WHATWG-Bereich:** §4.6 „Links“  
**Primärquelle:** WHATWG HTML Living Standard  
**Recherche-/Quellenstand:** 11. August 2026  
**Status:** fachliche Detailprüfung für §4.6 abgeschlossen.

Diese Datei dokumentiert die HTML-Elementbeziehungen und die fachlich relevanten Unterkonzepte aus WHATWG §4.6. Sie ist keine Kopie der Spezifikation. Normative Anforderungen werden zusammengefasst; Beispiele und Hinweise dienen der Lern- und Referenzfunktion von ZE-WebLab.

> **Abgrenzung:** §4.6 enthält nicht nur HTML-Elementdefinitionen. Der Abschnitt definiert zusätzlich APIs, Navigations- und Download-Verarbeitung, Hyperlink-Auditing sowie Link Types. Diese Konzepte werden hier als eigene Feature-Ebenen behandelt und nicht als zusätzliche HTML-Elemente gezählt.

> **Browser-Kompatibilität:** Die WHATWG-Seite kann ergänzend MDN-Kompatibilitätsinformationen anzeigen. Diese Informationen gehören nicht zum WHATWG-Status und werden in ZE-WebLab nicht als Konformitätsstatus verwendet.

---

## 1. Vollständigkeitskontrolle

### 1.1 Struktur von WHATWG §4.6

Der aktuelle Abschnitt §4.6 besitzt folgende Struktur:

| WHATWG | Inhalt |
|---|---|
| 4.6.1 | Introduction |
| 4.6.2 | Links created by `a` and `area` elements |
| 4.6.3 | API for hyperlink elements |
| 4.6.4 | API for `a` and `area` elements |
| 4.6.5 | Following hyperlinks |
| 4.6.6 | Downloading resources |
| 4.6.7 | Hyperlink auditing |
| 4.6.7.1 | The `Ping-From` and `Ping-To` headers |
| 4.6.8 | Link types |
| 4.6.8.1 | Link type `alternate` |
| 4.6.8.2 | Link type `author` |
| 4.6.8.3 | Link type `bookmark` |
| 4.6.8.4 | Link type `canonical` |
| 4.6.8.5 | Link type `dns-prefetch` |
| 4.6.8.6 | Link type `expect` |
| 4.6.8.7 | Link type `external` |
| 4.6.8.8 | Link type `help` |
| 4.6.8.9 | Link type `icon` |
| 4.6.8.10 | Link type `license` |
| 4.6.8.11 | Link type `manifest` |
| 4.6.8.12 | Link type `modulepreload` |
| 4.6.8.13 | Link type `nofollow` |
| 4.6.8.14 | Link type `noopener` |
| 4.6.8.15 | Link type `noreferrer` |
| 4.6.8.16 | Link type `opener` |
| 4.6.8.17 | Link type `pingback` |
| 4.6.8.18 | Link type `preconnect` |
| 4.6.8.19 | Link type `prefetch` |
| 4.6.8.20 | Link type `preload` |
| 4.6.8.21 | Link type `privacy-policy` |
| 4.6.8.22 | Link type `search` |
| 4.6.8.23 | Link type `stylesheet` |
| 4.6.8.24 | Link type `tag` |
| 4.6.8.25 | Link type `terms-of-service` |
| 4.6.8.26 | Sequential link types |
| 4.6.8.26.1 | Link type `next` |
| 4.6.8.26.2 | Link type `prev` |
| 4.6.8.27 | Other link types |

Die Struktur ist ausdrücklich mehr als eine Elementliste. §4.6 definiert `a`, `area`, `form` und `link` als Elemente, die Links erzeugen können, behandelt aber gleichzeitig mehrere nicht-elementare Konzepte. :contentReference[oaicite:1]{index=1}

---

## 2. Was in §4.6 als Link gilt

Links sind in WHATWG ein **konzeptionelles Konstrukt**.

Sie werden durch folgende Elemente erzeugt:

- `a`
- `area`
- `form`
- `link`

Ein Link stellt eine Verbindung zwischen zwei Ressourcen dar, von denen eine das aktuelle `Document` ist.

WHATWG unterscheidet drei grundlegende Linkarten:

1. Links zu externen Ressourcen
2. Hyperlinks
3. interne Resource Links

Diese Kategorien sind keine zusätzlichen HTML-Elemente.

### 2.1 Links zu externen Ressourcen

External Resource Links verweisen auf Ressourcen, die das aktuelle Dokument ergänzen.

Der User Agent verarbeitet solche Ressourcen typischerweise automatisch.

Für External Resource Links existiert ein Fetch-and-Process-Modell, das beschreibt, wann und wie die Ressource abgerufen und verarbeitet wird.

Beispiele sind unter anderem:

- `stylesheet`
- `icon`
- `manifest`
- `preload`
- `modulepreload`
- `preconnect`
- `prefetch`
- `dns-prefetch`

### 2.2 Hyperlinks

Hyperlinks verweisen auf andere Ressourcen und werden typischerweise dem Benutzer zugänglich gemacht, damit dieser eine Navigation oder einen Download auslösen kann.

Typische Hyperlinks entstehen beispielsweise durch:

```html
<a href="/docs/">Dokumentation</a>
```

Ein Hyperlink kann zusätzlich durch Link-Type-Anmerkungen in seinem Verarbeitungsverhalten beeinflusst werden.

### 2.3 Interne Resource Links

Internal Resource Links verweisen auf Ressourcen innerhalb des aktuellen Dokuments und geben diesen Ressourcen eine besondere Bedeutung oder ein besonderes Verhalten.

Der aktuelle Standard verwendet dafür insbesondere den Link Type `expect`.

### 2.4 Link-Erzeugung durch `link`

Bei einem `link`-Element mit `href` und `rel` werden Links für die in `rel` angegebenen und vom Standard definierten Link-Type-Keywords erzeugt.

`link` ist damit nicht einfach nur ein alternatives `a`-Element.

Seine Linktypen können insbesondere External Resource Links oder in bestimmten Fällen Hyperlinks bzw. Internal Resource Links erzeugen.

### 2.5 Link-Erzeugung durch `a` und `area`

Bei `a` und `area` mit `href` und `rel` werden Links entsprechend den Link-Type-Keywords erzeugt.

Zusätzlich gilt eine wichtige Besonderheit:

Ein `a`- oder `area`-Element mit `href` erzeugt auch dann einen Hyperlink, wenn:

- kein `rel` vorhanden ist oder
- `rel` keine Keywords enthält, die einen Hyperlink erzeugen.

Dieser implizite Hyperlink besitzt keine besondere Link-Type-Semantik.

### 2.6 Link-Erzeugung durch `form`

Auch `form` kann über `rel` Link Types erzeugen.

Ein `form` ohne `rel` oder ohne entsprechende Hyperlink-Linktypen erzeugt ebenfalls einen Hyperlink.

Die Linkfunktion von `form` gehört damit fachlich zum Link-Modell, obwohl `form` primär ein Formular-Element ist.

Quelle: WHATWG §4.6.1. :contentReference[oaicite:2]{index=2}

---

# 3. Elementinventar

## 3.1 Elemente, die in §4.6 am Link-Modell beteiligt sind

| Element | Rolle in §4.6 | Eigenständige Elementdefinition in diesem Block |
|---|---|---|
| `a` | Hyperlink-Erzeugung | nein, Definition liegt in §4.5.1 |
| `area` | Hyperlink-Erzeugung | nein, Definition liegt in §4.8 |
| `form` | Hyperlink-Erzeugung und Navigation | nein, Definition liegt in §4.10 |
| `link` | externe Ressourcen, Hyperlinks und interne Ressourcen | nein, Definition liegt in §4.2.4 |

Damit enthält §4.6 **keine neuen eigenständigen HTML-Elementdefinitionen**.

Die vier Elemente werden hier wegen ihrer Linkfunktion untersucht.

---

## 3.2 Inventar der Link-Features

| Feature | WHATWG-Abschnitt | Feature-Typ | Status |
|---|---|---|---|
| Links allgemein | 4.6.1 | Konzept | definiert |
| `a`/`area` Linkerzeugung | 4.6.2 | Element-/Link-Modell | definiert |
| `HyperlinkElementUtils` | 4.6.3 | API | definiert |
| `HTMLHyperlinkElementUtils` | 4.6.4 | API | definiert |
| Hyperlink-Navigation | 4.6.5 | Processing Model | definiert |
| Download | 4.6.6 | Processing Model | definiert |
| Hyperlink Auditing | 4.6.7 | Processing Model | definiert |
| `Ping-From` / `Ping-To` | 4.6.7.1 | HTTP-/Processing-Konzept | definiert |
| Link Types | 4.6.8 | Feature-Familie | definiert |
| `alternate` | 4.6.8.1 | Link Type | definiert |
| `author` | 4.6.8.2 | Link Type | definiert |
| `bookmark` | 4.6.8.3 | Link Type | definiert |
| `canonical` | 4.6.8.4 | Link Type | definiert |
| `dns-prefetch` | 4.6.8.5 | Link Type | definiert |
| `expect` | 4.6.8.6 | Link Type | definiert |
| `external` | 4.6.8.7 | Link Type | definiert |
| `help` | 4.6.8.8 | Link Type | definiert |
| `icon` | 4.6.8.9 | Link Type | definiert |
| `license` | 4.6.8.10 | Link Type | definiert |
| `manifest` | 4.6.8.11 | Link Type | definiert |
| `modulepreload` | 4.6.8.12 | Link Type | definiert |
| `nofollow` | 4.6.8.13 | Link Type | definiert |
| `noopener` | 4.6.8.14 | Link Type | definiert |
| `noreferrer` | 4.6.8.15 | Link Type | definiert |
| `opener` | 4.6.8.16 | Link Type | definiert |
| `pingback` | 4.6.8.17 | Link Type | definiert |
| `preconnect` | 4.6.8.18 | Link Type | definiert |
| `prefetch` | 4.6.8.19 | Link Type | definiert |
| `preload` | 4.6.8.20 | Link Type | definiert |
| `privacy-policy` | 4.6.8.21 | Link Type | definiert |
| `search` | 4.6.8.22 | Link Type | definiert |
| `stylesheet` | 4.6.8.23 | Link Type | definiert |
| `tag` | 4.6.8.24 | Link Type | definiert |
| `terms-of-service` | 4.6.8.25 | Link Type | definiert |
| `next` | 4.6.8.26.1 | Link Type | definiert |
| `prev` | 4.6.8.26.2 | Link Type | definiert |
| Erweiterte Link Types | 4.6.8.27 | Extension Model | definiert |

Quelle: WHATWG §4.6 Inhaltsübersicht und aktuelle Link-Type-Definitionen. :contentReference[oaicite:3]{index=3}

---

# 4. `a` und `area`: Linkerzeugung

## 4.1 `href`

Das `href`-Attribut von `a` und `area` muss einen gültigen URL-Wert enthalten, der gegebenenfalls von Leerzeichen umgeben sein darf.

Das Attribut ist jedoch nicht zwingend erforderlich.

Fehlt `href`, erzeugt das Element keinen Hyperlink.

Damit besitzt `a` zwei unterschiedliche fachliche Zustände:

- `a` ohne `href`: kein Hyperlink
- `a` mit `href`: Hyperlink

Für `area` gilt hinsichtlich der Linkerzeugung ebenfalls die Abhängigkeit von `href`.

Quelle: WHATWG §4.6.2. :contentReference[oaicite:4]{index=4}

---

## 4.2 `target`

Das `target`-Attribut gibt das Ziel-Navigable an.

Der Wert muss ein gültiger Navigable Target Name oder ein gültiges Target Keyword sein.

Das Target wird bei der späteren Navigation berücksichtigt.

Typische Keywords sind beispielsweise:

- `_self`
- `_blank`
- `_parent`
- `_top`

Die vollständige Navigation ist jedoch Bestandteil des in §4.6.5 beschriebenen Processing Models.

---

## 4.3 `download`

Das `download`-Attribut signalisiert die Absicht des Autors, dass der Hyperlink zum Download einer Ressource verwendet werden soll.

Das Attribut kann ohne Wert verwendet werden.

Es kann auch einen Wert enthalten.

Der Wert dient als vom Autor empfohlener Dateiname für die Speicherung der Ressource.

WHATWG schreibt für die erlaubten Werte keine spezielle Dateinamenssyntax vor. User Agents können den vorgeschlagenen Dateinamen an die Einschränkungen des jeweiligen Dateisystems anpassen.

Die eigentliche Download-Verarbeitung wird in §4.6.6 definiert.

Quelle: WHATWG §4.6.2 und §4.6.6. :contentReference[oaicite:5]{index=5}

---

## 4.4 `ping`

Das `ping`-Attribut gibt URLs von Ressourcen an, die über das Folgen eines Hyperlinks informiert werden sollen.

Der Wert muss aus durch ASCII-Whitespace getrennten Tokens bestehen.

Jedes Token muss eine gültige, nichtleere URL sein.

Die URLs müssen HTTP(S)-Schemas verwenden.

Die Verarbeitung gehört zum Hyperlink-Auditing-Modell.

Wichtig:

`ping` ist kein allgemeiner Navigationsmechanismus.

Es beschreibt zusätzliche Benachrichtigungsanfragen im Zusammenhang mit dem Folgen eines Hyperlinks.

Quelle: WHATWG §4.6.2 und §4.6.7. :contentReference[oaicite:6]{index=6}

---

## 4.5 `rel`

Bei `a` und `area` steuert `rel`, welche Arten von Links das Element erzeugt bzw. welche Link-Anmerkungen auf den Hyperlink angewendet werden.

Der Wert muss eine ungeordnete Menge eindeutiger, durch Leerzeichen getrennter Tokens sein.

Die Bedeutungen der Tokens werden in §4.6.8 definiert.

WHATWG unterscheidet zwischen:

- Link Types, die tatsächlich Links erzeugen,
- Link Types, die bestehende Hyperlinks annotieren,
- Link Types, die externe Ressourcen definieren.

Für `a` und `area` nennt die aktuelle API-Definition als unterstützte Processing-Model-Tokens:

- `noreferrer`
- `noopener`
- `opener`

Diese unterstützten Tokens sind eine API-/Implementierungsinformation und nicht identisch mit der vollständigen Liste aller Link Types.

Quelle: WHATWG §4.6.2 und §4.6.3/§4.6.8. :contentReference[oaicite:7]{index=7}

---

## 4.6 `referrerpolicy`

`referrerpolicy` bestimmt die Referrer Policy, die beim Folgen eines Hyperlinks verwendet wird.

Die konkrete Policy stammt aus dem Referrer-Policy-Modell.

`noreferrer` besitzt zusätzlich eine besondere Wechselwirkung mit der Hyperlink Referrer Policy:

Wenn `noreferrer` als Link Type vorhanden ist, wird die Hyperlink Referrer Policy auf `no-referrer` gesetzt.

Quelle: WHATWG §4.6.2 und §4.6.5. :contentReference[oaicite:8]{index=8}

---

## 4.7 Aktivierungsverhalten

Bei der Aktivierung eines `a`- oder `area`-Elements wird zunächst geprüft, ob `href` vorhanden ist.

Ohne `href` endet das Aktivierungsverhalten.

Anschließend wird abhängig von Benutzerbeteiligung und Attributen entschieden, ob:

- der Hyperlink heruntergeladen oder
- der Hyperlink verfolgt

wird.

Standardmäßig gilt:

- ohne `download`: Navigation
- mit `download`: Download

Der User Agent kann dabei eine explizite Benutzerpräferenz berücksichtigen.

Quelle: WHATWG §4.6.2. :contentReference[oaicite:9]{index=9}

---

# 5. API für Hyperlink-Elemente

## 5.1 `HyperlinkElementUtils`

WHATWG definiert ein Interface-Mixin:

```webidl
interface mixin HyperlinkElementUtils {
  readonly attribute USVString origin;
  [CEReactions] attribute USVString protocol;
  [CEReactions] attribute USVString username;
  [CEReactions] attribute USVString password;
  [CEReactions] attribute USVString host;
  [CEReactions] attribute USVString hostname;
  [CEReactions] attribute USVString port;
  [CEReactions] attribute USVString pathname;
  [CEReactions] attribute USVString search;
  [CEReactions] attribute USVString hash;

  [CEReactions, Reflect] attribute DOMString hreflang;
  [CEReactions, Reflect] attribute DOMString type;
};
```

Das Mixin stellt URL-bezogene Eigenschaften für Hyperlink-Elemente bereit.

Es handelt sich um eine **API-Ebene**, nicht um ein HTML-Element.

Quelle: WHATWG §4.6.3. :contentReference[oaicite:10]{index=10}

---

## 5.2 `origin`

`origin` liefert den Origin der URL des Hyperlinks.

Ist keine URL vorhanden, greifen die im API-Modell definierten Null-/Leerwertregeln.

---

## 5.3 `protocol`

`protocol` repräsentiert das Schema der Hyperlink-URL.

Der Wert kann gesetzt werden.

Durch das Setzen wird die URL entsprechend dem WHATWG-URL-Modell verändert.

---

## 5.4 `username`

`username` repräsentiert den Username-Anteil der URL.

Der Wert kann gesetzt werden.

Ist die URL nicht vorhanden oder unterstützt die URL keine Userinfo, greifen die im Standard definierten Rückgaberegeln.

---

## 5.5 `password`

`password` repräsentiert den Passwort-Anteil der URL.

Der Wert kann gesetzt werden.

Auch hier gelten die Einschränkungen des WHATWG-URL-Modells für URLs, die Userinfo unterstützen.

---

## 5.6 `host`

`host` liefert Host und gegebenenfalls Port.

Wenn ein nicht-default Port vorhanden ist, wird dieser berücksichtigt.

Der Setter kann Host und Port der URL verändern.

---

## 5.7 `hostname`

`hostname` repräsentiert ausschließlich den Hostnamen.

Der Port ist nicht Bestandteil des zurückgegebenen Hostname-Werts.

---

## 5.8 `port`

`port` repräsentiert den Port der Hyperlink-URL.

Der Wert kann gesetzt werden.

---

## 5.9 `pathname`

`pathname` repräsentiert den Pfad der URL.

Der Setter kann den Pfad verändern.

---

## 5.10 `search`

`search` repräsentiert die Query-Komponente der URL.

Die serialisierte Form umfasst den führenden `?`, wenn eine Query vorhanden ist.

---

## 5.11 `hash`

`hash` repräsentiert das Fragment der URL.

Bei einem nichtleeren Fragment enthält die serialisierte Form das führende `#`.

Beim Setzen wird ein führendes `#` entsprechend den URL-Regeln verarbeitet.

---

## 5.12 `hreflang`

`hreflang` ist als reflektierendes DOM-Attribut Bestandteil des Hyperlink-API-Modells.

Es beschreibt die erwartete Sprache bzw. Sprachvariante der referenzierten Ressource.

Die konkrete Bedeutung für die Navigation wird nicht mit einer eigenständigen Navigationslogik gleichgesetzt.

---

## 5.13 `type`

`type` ist ebenfalls Bestandteil des Hyperlink-API-Modells.

Es wird als DOMString reflektiert und kann zur Beschreibung des erwarteten Medientyps der referenzierten Ressource dienen.

Die Verarbeitung hängt vom jeweiligen Link-Kontext ab.

Quelle: WHATWG §4.6.3. :contentReference[oaicite:11]{index=11}

---

# 6. API für `a` und `area`

## 6.1 `HTMLHyperlinkElementUtils`

WHATWG definiert für `a` und `area` ein weiteres Interface-Mixin:

```webidl
interface mixin HTMLHyperlinkElementUtils {
  [CEReactions, ReflectSetter] stringifier attribute USVString href;
  [CEReactions, Reflect] attribute DOMString target;
};
```

Dieses API-Modell ist ebenfalls keine neue Elementdefinition.

Quelle: WHATWG §4.6.4. :contentReference[oaicite:12]{index=12}

---

## 6.2 `href` als IDL-Attribut

Das `href`-IDL-Attribut wird als `USVString` behandelt und ist ein Stringifier.

Damit kann beispielsweise die String-Repräsentation eines Hyperlink-Objekts über die URL-bezogene API bestimmt werden.

---

## 6.3 `target` als IDL-Attribut

`target` wird als reflektierendes `DOMString`-Attribut bereitgestellt.

Es repräsentiert das Target-Attribut des Hyperlinks.

---

## 6.4 DOM-Interfaces

Die konkreten Elementinterfaces sind:

- `a` → `HTMLAnchorElement`
- `area` → `HTMLAreaElement`

Das Link-API-Modell ergänzt diese Interfaces um die Hyperlink-spezifischen Eigenschaften.

Quelle: WHATWG §4.6.3 und §4.6.4. :contentReference[oaicite:13]{index=13}

---

# 7. Hyperlink-Processing und Navigation

## 7.1 Navigierbarkeit

Ein Element kann nicht navigieren, wenn unter anderem:

- sein Node Document nicht vollständig aktiv ist oder
- es kein `a`-Element ist und nicht verbunden ist.

Die besondere Behandlung von `a` ist eine Kompatibilitätsregel des Standards.

Das Modell wird außerdem bei der Formularübermittlung verwendet.

Quelle: WHATWG §4.6.5. :contentReference[oaicite:14]{index=14}

---

## 7.2 `noopener`

WHATWG definiert ein eigenes Verfahren, um zu bestimmen, ob ein Element `noopener`-Verhalten besitzt.

`noopener` ist aktiv, wenn:

1. die Link Types `noopener` oder `noreferrer` enthalten oder
2. `opener` nicht vorhanden ist und das Target `_blank` ist.

Zusätzliche Regeln betreffen unter anderem Blob-URLs und deren Origin-Beziehungen.

Damit ist `noopener` nicht nur eine semantische Beschreibung, sondern Teil des Navigations-Processing-Models.

Quelle: WHATWG §4.6.5. :contentReference[oaicite:15]{index=15}

---

## 7.3 Folgen eines Hyperlinks

Das Verfahren „follow the hyperlink“ erhält unter anderem:

- das Element,
- einen optionalen Hyperlink-Suffix,
- die User Involvement Information.

Zunächst wird geprüft, ob das Element navigieren kann.

Für `a` und `area` wird das Target ermittelt.

Anschließend wird der `href`-Wert relativ zum Node Document als URL verarbeitet.

Die Navigation wird anschließend unter Berücksichtigung des Targets, der Referrer Policy und der User Involvement ausgeführt.

Quelle: WHATWG §4.6.5. :contentReference[oaicite:16]{index=16}

---

## 7.4 Hyperlink Referrer Policy

Die Hyperlink Referrer Policy wird folgendermaßen bestimmt:

1. Enthält der Link Type `noreferrer`, wird `no-referrer` verwendet.
2. Andernfalls wird die aktuelle `referrerpolicy`-Eigenschaft des Elements verwendet.

Damit besitzt `noreferrer` eine unmittelbare Verbindung zur Navigation.

Quelle: WHATWG §4.6.5. :contentReference[oaicite:17]{index=17}

---

## 7.5 Navigation und History

Das Folgen eines Hyperlinks führt grundsätzlich zu einer Navigation des ermittelten Navigable.

WHATWG weist darauf hin, dass Hyperlink-Navigation nicht dieselbe besondere Replace-Behandlung besitzt, die für bestimmte andere Navigationssituationen bei noch nicht vollständig geladenen Dokumenten verwendet wird.

Auch scriptbasierte Aktivierung, etwa über `click()`, fällt in dieses Verarbeitungsmodell.

Quelle: WHATWG §4.6.5. :contentReference[oaicite:18]{index=18}

---

# 8. Downloading resources

## 8.1 Zweck von `download`

Das `download`-Attribut wird verwendet, wenn eine Ressource zur späteren Verwendung gespeichert werden soll, anstatt sie unmittelbar zu betrachten.

Es kann auf `a` und `area` verwendet werden.

---

## 8.2 Vorgeschlagener Dateiname

Enthält `download` einen Wert, kann dieser als vorgeschlagener Dateiname verwendet werden.

Der Wert ist jedoch nicht zwingend der letztendlich verwendete Dateiname.

Insbesondere kann der `Content-Disposition`-HTTP-Header mit seinem `filename`-Parameter den vorgeschlagenen Namen beeinflussen bzw. überschreiben.

---

## 8.3 Cross-Origin-Downloads

Für Cross-Origin-Situationen definiert WHATWG eine zusätzliche Schutzanforderung.

Das `download`-Attribut muss dort mit einem `Content-Disposition`-Header kombiniert werden, dessen Disposition `attachment` ist, um entsprechende Warnungen bzw. Schutzmechanismen zu vermeiden.

Der Grund liegt im Schutz vor dem unerwarteten Herunterladen sensibler oder vertraulicher Informationen.

---

## 8.4 Download-Processing-Model

Beim Download eines Hyperlinks werden unter anderem geprüft:

1. ob das Element navigieren kann,
2. ob ein Sandbox-Flag Downloads verhindert,
3. ob die URL erfolgreich geparst und serialisiert werden kann,
4. ob ein optionaler Hyperlink-Suffix vorhanden ist,
5. ob die User Involvement Information berücksichtigt werden muss.

Wenn ein Download nicht zulässig ist, wird die Verarbeitung beendet.

Quelle: WHATWG §4.6.6. :contentReference[oaicite:19]{index=19}

---

# 9. Hyperlink Auditing

## 9.1 Zweck

Das Hyperlink-Auditing-Modell beschreibt zusätzliche HTTP(S)-Anfragen, die ausgelöst werden können, wenn ein Benutzer einem Hyperlink folgt.

Das Modell wird durch das `ping`-Attribut von `a` und `area` aktiviert.

---

## 9.2 Verarbeitung des `ping`-Werts

Wenn:

- ein Hyperlink von `a` oder `area` existiert,
- das Element ein `ping`-Attribut besitzt,
- der Benutzer dem Hyperlink folgt und
- `href` erfolgreich relativ zum Node Document geparst werden kann,

wird der `ping`-Wert in ASCII-Whitespace-getrennte Tokens aufgeteilt.

Jedes Token wird relativ zum Node Document als URL verarbeitet.

Fehlerhafte URLs werden ignoriert.

---

## 9.3 HTTP(S)-Beschränkung

Wenn die URL eines Ping-Eintrags kein HTTP(S)-Schema besitzt, wird die Verarbeitung dieses Ping-Eintrags beendet.

Damit ist Hyperlink Auditing nicht als beliebiger URL-Aufrufmechanismus definiert.

---

## 9.4 Optionale Unterdrückung

WHATWG erlaubt dem User Agent, Hyperlink-Auditing-Anfragen optional zu unterdrücken.

Als Beispiel nennt die Spezifikation Benutzerpräferenzen.

Daraus folgt:

Das Vorhandensein eines `ping`-Attributs bedeutet nicht zwingend, dass unter allen Umständen tatsächlich eine Netzwerk-Anfrage gesendet wird.

Quelle: WHATWG §4.6.7. :contentReference[oaicite:20]{index=20}

---

# 10. `Ping-From` und `Ping-To`

## 10.1 `Ping-From`

`Ping-From` ist ein HTTP-Request-Header, der bei Hyperlink-Auditing-Anfragen verwendet wird.

Sein Wert ist eine serialisierte URL.

---

## 10.2 `Ping-To`

`Ping-To` ist ebenfalls ein HTTP-Request-Header für Hyperlink-Auditing.

Sein Wert ist ebenfalls eine serialisierte URL.

Die Header gehören zum Auditing-Processing-Model und sind keine HTML-Attribute.

Quelle: WHATWG §4.6.7.1. :contentReference[oaicite:21]{index=21}

---

# 11. Link Types

## 11.1 Grundmodell

Link Types werden über das `rel`-Attribut angegeben.

Für `link`, `a`, `area` und `form` wird der `rel`-Wert in ASCII-Whitespace-getrennte Tokens aufgeteilt.

Diese Tokens bestimmen die Link Types des Elements.

Keywords sind ASCII-case-insensitive.

Damit gelten beispielsweise:

```html
rel="next"
```

und

```html
rel="NEXT"
```

als dasselbe Keyword.

---

## 11.2 Doppelte Keywords

Ein Keyword darf grundsätzlich nicht mehr als einmal im `rel`-Attribut angegeben werden, sofern keine spezielle Regel etwas anderes vorsieht.

---

## 11.3 Link-Type-Synonyme

Einige historische Synonyme existieren weiterhin für User Agents.

Solche Synonyme dürfen jedoch nicht als normative Dokumentautoren-Syntax verwendet werden, wenn der Standard dies ausdrücklich untersagt.

Beispiel:

`previous` wird als historisches Synonym für `prev` behandelt.

---

## 11.4 `body-ok`

WHATWG klassifiziert bestimmte Link Types als `body-ok`.

Die aktuellen `body-ok`-Keywords sind:

- `dns-prefetch`
- `modulepreload`
- `pingback`
- `preconnect`
- `prefetch`
- `preload`
- `stylesheet`

Diese Eigenschaft ist insbesondere für die Zulässigkeit von `link`-Elementen im `body` relevant.

Sie ist nicht identisch mit der Frage, ob ein Link Type ein Hyperlink oder ein External Resource Link ist.

Quelle: WHATWG §4.6.8. :contentReference[oaicite:22]{index=22}

---

# 12. Link-Type-Inventar

| Link Type | Typische Elemente | Linkwirkung |
|---|---|---|
| `alternate` | `link`, `a`, `area` | abhängig vom Kontext |
| `author` | `link`, `a`, `area` | Hyperlink |
| `bookmark` | `a`, `area` | Hyperlink |
| `canonical` | `link` | Hyperlink |
| `dns-prefetch` | `link` | External Resource |
| `expect` | `link` | Internal Resource |
| `external` | `a`, `area`, `form` | Annotation |
| `help` | `link`, `a`, `area`, `form` | Hyperlink |
| `icon` | `link` | External Resource |
| `license` | `link`, `a`, `area`, `form` | Hyperlink |
| `manifest` | `link` | External Resource |
| `modulepreload` | `link` | External Resource |
| `nofollow` | `a`, `area`, `form` | Annotation |
| `noopener` | `a`, `area`, `form` | Annotation |
| `noreferrer` | `a`, `area`, `form` | Annotation |
| `opener` | `a`, `area`, `form` | Annotation |
| `pingback` | `link` | External Resource |
| `preconnect` | `link` | External Resource |
| `prefetch` | `link` | External Resource |
| `preload` | `link` | External Resource |
| `privacy-policy` | `link`, `a`, `area` | Hyperlink |
| `search` | `link`, `a`, `area`, `form` | Hyperlink |
| `stylesheet` | `link` | External Resource |
| `tag` | `a`, `area` | Hyperlink |
| `terms-of-service` | `link`, `a`, `area` | Hyperlink |
| `next` | `link`, `a`, `area`, `form` | Hyperlink |
| `prev` | `link`, `a`, `area`, `form` | Hyperlink |

Quelle: WHATWG §4.6.8. :contentReference[oaicite:23]{index=23}

---

# 13. Link Type `alternate`

`alternate` kann mit `link`, `a` und `area` verwendet werden.

Die konkrete Bedeutung hängt von den übrigen Attributen ab.

Insbesondere bei `link` in Kombination mit `stylesheet` verändert `alternate` die Bedeutung des Stylesheet-Linktypes und erzeugt nicht selbst einen eigenständigen Link.

Das ist ein wichtiges Beispiel dafür, dass Link Types kombinierbar sind und ihre Bedeutung kontextabhängig sein kann.

Quelle: WHATWG §4.6.8.1. :contentReference[oaicite:24]{index=24}

---

# 14. Link Type `author`

`author` kann mit:

- `link`
- `a`
- `area`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Bei `a` und `area` verweist der Link auf weitere Informationen über den Autor:

- des nächsten `article`-Ancestors, sofern vorhanden,
- andernfalls der Seite insgesamt.

Bei `link` bezieht sich die Autoreninformation auf die Seite als Ganzes.

Die referenzierte Ressource kann beispielsweise eine `mailto:`-URL sein.

Historisch muss ein `rev="made"` entsprechend behandelt werden, darf aber nicht als moderne Dokumentautoren-Syntax für diese Beziehung verwendet werden.

Quelle: WHATWG §4.6.8.2. :contentReference[oaicite:25]{index=25}

---

# 15. Link Type `bookmark`

`bookmark` kann mit `a` und `area` verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet einen Permalink für den relevanten Abschnitt bzw. das relevante `article`.

Wenn ein `article`-Ancestor existiert, bezieht sich der Bookmark auf den nächstgelegenen relevanten `article`-Bereich.

Andernfalls bezieht er sich auf den Abschnitt, dem das Linking Element am engsten zugeordnet ist.

Quelle: WHATWG §4.6.8.3. :contentReference[oaicite:26]{index=26}

---

# 16. Link Type `canonical`

`canonical` darf mit `link` verwendet werden.

Er erzeugt einen Hyperlink.

Die durch `href` angegebene URL wird als bevorzugte URL für das aktuelle Dokument bezeichnet.

Der Link Type ist damit ein semantischer Link Relationship Type und keine allgemeine Browser-Navigationsanweisung.

WHATWG verweist für die nähere Bedeutung auf die Canonical-Link-Relation.

Quelle: WHATWG §4.6.8.4. :contentReference[oaicite:27]{index=27}

---

# 17. Link Type `dns-prefetch`

`dns-prefetch` darf mit `link` verwendet werden.

Der Link Type erzeugt einen External Resource Link.

Er signalisiert, dass der User Agent die DNS-Auflösung für die Origin der Zielressource vorzeitig durchführen sollte.

`dns-prefetch` gehört zu den `body-ok`-Linktypen.

Quelle: WHATWG §4.6.8.5. :contentReference[oaicite:28]{index=28}

---

# 18. Link Type `expect`

`expect` darf mit `link` verwendet werden.

Er erzeugt einen Internal Resource Link.

Der Link verweist auf ein Element innerhalb des aktuellen Dokuments.

Der Link Type kann verwendet werden, um Rendering zu blockieren, bis das durch die URL bestimmte Element verbunden und vollständig geparst ist.

---

## 18.1 `expect` und Fragment

Das `href`-Ziel muss auf das aktuelle Dokument zeigen.

Die URL wird ohne Fragmentvergleich gegen die URL des aktuellen Dokuments geprüft.

Anschließend wird der angegebene Teil des Dokuments ermittelt.

---

## 18.2 Render-Blocking

Wenn die entsprechenden Bedingungen erfüllt sind, kann ein `expect`-Link das Rendering blockieren.

Zu den relevanten Bedingungen gehören unter anderem:

- Dokument befindet sich noch im Zustand `loading`,
- `link` erzeugt den entsprechenden Internal Resource Link,
- Element ist browsing-context-connected,
- `rel` enthält `expect`,
- Element ist potentiell render-blocking,
- `media` passt zur Umgebung,
- das angegebene Ziel ist noch nicht entsprechend geparst bzw. verbunden.

Die Verarbeitung reagiert auch auf dynamische Änderungen.

Quelle: WHATWG §4.6.8.6. :contentReference[oaicite:29]{index=29}

---

# 19. Link Type `external`

`external` kann mit:

- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt keinen eigenen Hyperlink.

Stattdessen annotiert er andere durch das Element erzeugte Hyperlinks.

Er kennzeichnet eine Navigation zu einem Dokument, das nicht Teil derselben Site wie das aktuelle Dokument ist.

Quelle: WHATWG §4.6.8.7. :contentReference[oaicite:30]{index=30}

---

# 20. Link Type `help`

`help` kann mit:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Bei `a`, `area` und `form` verweist er auf kontextbezogene Hilfe für das übergeordnete Element und dessen Kinder.

Bei `link` bezieht sich die Hilfe auf die Seite insgesamt.

Quelle: WHATWG §4.6.8.8. :contentReference[oaicite:31]{index=31}

---

# 21. Link Type `icon`

`icon` darf mit `link` verwendet werden.

Er erzeugt einen External Resource Link.

Er importiert ein Icon, das das aktuelle Dokument bzw. die Anwendung repräsentiert.

Die Verarbeitung des Icons ist Teil des `link`-External-Resource-Modells.

Quelle: WHATWG §4.6.8.9. :contentReference[oaicite:32]{index=32}

---

# 22. Link Type `license`

`license` kann mit:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet eine Ressource, die die Lizenzbedingungen des Hauptinhalts des aktuellen Dokuments beschreibt.

WHATWG weist darauf hin, dass die Spezifikation nicht selbst definiert, wie Hauptinhalt und Nicht-Hauptinhalt eines Dokuments zu unterscheiden sind.

Quelle: WHATWG §4.6.8.10. :contentReference[oaicite:33]{index=33}

---

# 23. Link Type `manifest`

`manifest` darf mit `link` verwendet werden.

Er erzeugt einen External Resource Link.

Er verweist auf ein Manifest mit Metadaten für das aktuelle Dokument bzw. die Webanwendung.

Es gibt für `manifest` keinen von diesem Link Type definierten Default Resource Type.

Die geeignete Zeit zum Abruf und zur Verarbeitung kann insbesondere davon abhängen, ob eine Webanwendung installiert werden soll oder bereits installiert ist.

Quelle: WHATWG §4.6.8.11. :contentReference[oaicite:34]{index=34}

---

# 24. Link Type `modulepreload`

`modulepreload` darf mit `link` verwendet werden.

Der Link Type erzeugt einen External Resource Link.

Er ist `body-ok`.

`modulepreload` ist auf das Vorladen von Module Scripts spezialisiert.

Im Unterschied zu `preload` wird das Ergebnis entsprechend dem Module-Script-Fetching verarbeitet und in die passende Module Map eingebracht.

Damit ist `modulepreload` nicht bloß ein Alias für `preload`.

Quelle: WHATWG §4.6.8.12. :contentReference[oaicite:35]{index=35}

---

# 25. Link Type `nofollow`

`nofollow` kann mit:

- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt keinen eigenen Hyperlink.

Er annotiert einen anderen durch das Element erzeugten Hyperlink.

Die Annotation signalisiert, dass der Link vom ursprünglichen Autor oder Publisher nicht endorsed wird oder insbesondere aufgrund einer kommerziellen Beziehung aufgenommen wurde.

Quelle: WHATWG §4.6.8.13. :contentReference[oaicite:36]{index=36}

---

# 26. Link Type `noopener`

`noopener` kann mit:

- `a`
- `area`
- `form`

verwendet werden.

Der Link Type annotiert einen Hyperlink und erzeugt keinen eigenen Hyperlink.

Er beeinflusst das Navigationsverhalten dahingehend, dass ein neu erzeugtes Top-Level-Navigable keinen entsprechenden Opener-Kontext erhält.

Besonders relevant ist die Verbindung zu `target="_blank"`.

WHATWG definiert außerdem Regeln, nach denen `_blank` ohne `opener` implizit `noopener`-Verhalten auslösen kann.

Quelle: WHATWG §4.6.5 und §4.6.8.14. :contentReference[oaicite:37]{index=37}

---

# 27. Link Type `noreferrer`

`noreferrer` kann mit:

- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt keinen eigenen Hyperlink.

Er annotiert vorhandene Hyperlinks.

Er bewirkt:

1. dass keine Referrer-Information beim Folgen des Links weitergegeben wird,
2. dass unter den entsprechenden Bedingungen auch `noopener`-Verhalten entsteht.

Beispiel:

```html
<a href="..." rel="noreferrer" target="_blank">Ziel</a>
```

entspricht hinsichtlich des beschriebenen Verhaltens:

```html
<a href="..." rel="noreferrer noopener" target="_blank">Ziel</a>
```

Quelle: WHATWG §4.6.8.15. :contentReference[oaicite:38]{index=38}

---

# 28. Link Type `opener`

`opener` kann mit:

- `a`
- `area`
- `form`

verwendet werden.

Der Link Type annotiert einen Hyperlink.

Er signalisiert, dass ein neu erzeugtes Top-Level Traversable einen Auxiliary Browsing Context enthalten soll.

`opener` ist damit die ausdrückliche Gegenposition zum `noopener`-Verhalten.

Quelle: WHATWG §4.6.8.16. :contentReference[oaicite:39]{index=39}

---

# 29. Link Type `pingback`

`pingback` darf mit `link` verwendet werden.

Er erzeugt einen External Resource Link.

Der Link Type ist `body-ok`.

Die konkrete Bedeutung wird durch die Pingback-Spezifikation definiert, auf die WHATWG verweist.

Quelle: WHATWG §4.6.8.17. :contentReference[oaicite:40]{index=40}

---

# 30. Link Type `preconnect`

`preconnect` darf mit `link` verwendet werden.

Er erzeugt einen External Resource Link.

Der Link Type ist `body-ok`.

Er signalisiert, dass der User Agent möglichst früh eine Verbindung zur Origin der angegebenen Ressource aufbauen sollte, weil die Ressource mit hoher Wahrscheinlichkeit benötigt wird.

Das Ziel ist die Vorwegnahme der Verbindungslatenz.

Quelle: WHATWG §4.6.8.18. :contentReference[oaicite:41]{index=41}

---

# 31. Link Type `prefetch`

`prefetch` darf mit `link` verwendet werden.

Er erzeugt einen External Resource Link.

Der Link Type ist `body-ok`.

Er signalisiert, dass das vorzeitige Abrufen und Cachen einer Ressource oder eines same-site Dokuments wahrscheinlich sinnvoll ist, weil eine spätere Navigation dorthin wahrscheinlich ist.

Es gibt keinen Default Resource Type für `prefetch`.

Quelle: WHATWG §4.6.8.19. :contentReference[oaicite:42]{index=42}

---

# 32. Link Type `preload`

`preload` ist ein External Resource Link Type für das frühzeitige Abrufen einer Ressource, die das Dokument voraussichtlich benötigt.

Der Link Type ist `body-ok`.

Die genaue Verarbeitung wird durch die für Preload definierten Attribute und das External-Resource-Link-Modell bestimmt.

Insbesondere spielen `as`, `type`, `crossorigin`, `media` und `fetchpriority` je nach Kontext eine Rolle.

`preload` ist von `modulepreload` zu unterscheiden.

Quelle: WHATWG §4.6.8.20 und das zugehörige External-Resource-Processing. :contentReference[oaicite:43]{index=43}

---

# 33. Link Type `privacy-policy`

`privacy-policy` kann mit:

- `link`
- `a`
- `area`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er verweist auf Informationen darüber, wie Daten im Zusammenhang mit dem aktuellen Dokument gesammelt und verwendet werden.

Die referenzierte Ressource kann eine eigenständige Datenschutzerklärung oder ein entsprechender Abschnitt eines umfassenderen Dokuments sein.

Quelle: WHATWG §4.6.8.21. :contentReference[oaicite:44]{index=44}

---

# 34. Link Type `search`

`search` kann mit:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet eine Ressource, die eine Suchschnittstelle für das aktuelle Dokument und dessen verbundene Ressourcen bereitstellt.

WHATWG nennt außerdem OpenSearch Description Documents als mögliches Anwendungsbeispiel für `link`.

Quelle: WHATWG §4.6.8.22. :contentReference[oaicite:45]{index=45}

---

# 35. Link Type `stylesheet`

`stylesheet` ist ein External Resource Link Type.

Er darf mit `link` verwendet werden.

Der Link Type ist `body-ok`.

Der Default Resource Type ist `text/css`.

Wenn `alternate` gleichzeitig angegeben wird, entsteht ein alternatives Stylesheet.

In diesem Fall muss `title` auf dem `link`-Element mit einem nichtleeren Wert vorhanden sein.

Ein durch Parser erzeugtes Stylesheet-`link` kann implizit potentiell render-blocking sein.

Quelle: WHATWG §4.6.8.23. :contentReference[oaicite:46]{index=46}

---

## 35.1 Stylesheet-Verarbeitung

Das Stylesheet kann unter anderem neu geladen bzw. verarbeitet werden, wenn:

- das External Resource Link erzeugt wird,
- das Element browsing-context-connected wird,
- `href` geändert wird,
- `disabled` geändert wird,
- `crossorigin` geändert wird,
- `type` geändert wird,
- der Alternative-Stylesheet-Status geändert wird.

Die vollständige Verarbeitung umfasst zusätzlich Fetch- und CSS-Processing-Regeln.

Quelle: WHATWG §4.6.8.23. :contentReference[oaicite:47]{index=47}

---

# 36. Link Type `tag`

`tag` darf mit:

- `a`
- `area`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet ein Tag, das auf das aktuelle Dokument angewendet wird.

Die Spezifikation weist ausdrücklich darauf hin, dass dies nicht mit einem allgemeinen Tag-Cloud-Link verwechselt werden sollte.

Quelle: WHATWG §4.6.8.24. :contentReference[oaicite:48]{index=48}

---

# 37. Link Type `terms-of-service`

`terms-of-service` kann mit:

- `link`
- `a`
- `area`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet eine Ressource, die Informationen über Vereinbarungen zwischen dem Anbieter des aktuellen Dokuments und seinen Benutzern enthält.

Quelle: WHATWG §4.6.8.25. :contentReference[oaicite:49]{index=49}

---

# 38. Sequenzielle Link Types

WHATWG definiert eine besondere Familie von Link Types für Dokumentsequenzen.

Eine Dokumentsequenz besteht aus Dokumenten, die jeweils einen vorherigen und/oder nächsten logischen Nachbarn besitzen können.

Ein Dokument kann Bestandteil mehrerer Sequenzen sein.

Die Familie besteht aus:

- `next`
- `prev`

---

# 39. Link Type `next`

`next` kann mit:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet das nächste logische Dokument einer Dokumentsequenz.

Bei Verwendung mit `link` soll der User Agent den Link für Vorabverarbeitung behandeln können, etwa entsprechend:

- `dns-prefetch`
- `preconnect`
- `prefetch`

Welche konkrete Strategie verwendet wird, bleibt dem User Agent überlassen.

Quelle: WHATWG §4.6.8.26.1. :contentReference[oaicite:50]{index=50}

---

# 40. Link Type `prev`

`prev` kann mit:

- `link`
- `a`
- `area`
- `form`

verwendet werden.

Der Link Type erzeugt einen Hyperlink.

Er kennzeichnet das vorherige logische Dokument einer Dokumentsequenz.

Das historische Keyword `previous` wird von User Agents als Synonym für `prev` behandelt.

`previous` soll jedoch nicht als moderne Dokumentautoren-Syntax verwendet werden.

Quelle: WHATWG §4.6.8.26.2. :contentReference[oaicite:51]{index=51}

---

# 41. Andere Link Types / Erweiterungen

WHATWG definiert neben den standardisierten Link Types ein Erweiterungsmodell.

Neue Link Types, die von Webbrowsern implementiert werden sollen, müssen in den HTML Standard aufgenommen werden.

Andere Link Types können als Erweiterungen registriert werden.

Damit existiert keine endliche, für alle Zeiten abgeschlossene Menge von `rel`-Tokens außerhalb des standardisierten Link-Type-Systems.

Für Erweiterungen werden unter anderem Angaben zu folgenden Punkten verlangt:

- Keyword
- Bedeutung
- erlaubte Elemente
- Verhalten
- weitere notwendige Metadaten

Wichtig für ZE-WebLab:

Ein beliebiger `rel`-String darf daher nicht automatisch als WHATWG-standardisierter Link Type klassifiziert werden.

Quelle: WHATWG §4.6.8.27. :contentReference[oaicite:52]{index=52}

---

# 42. Link-Type-Klassifikation

Für ZE-WebLab ist die folgende Trennung besonders wichtig:

## 42.1 Hyperlink erzeugende Link Types

Dazu gehören beispielsweise:

- `author`
- `bookmark`
- `canonical`
- `help`
- `license`
- `privacy-policy`
- `search`
- `tag`
- `terms-of-service`
- `next`
- `prev`

---

## 42.2 External Resource Links

Dazu gehören beispielsweise:

- `dns-prefetch`
- `icon`
- `manifest`
- `modulepreload`
- `pingback`
- `preconnect`
- `prefetch`
- `preload`
- `stylesheet`

---

## 42.3 Internal Resource Links

Aktuell besonders relevant:

- `expect`

---

## 42.4 Hyperlink Annotations

Dazu gehören beispielsweise:

- `external`
- `nofollow`
- `noopener`
- `noreferrer`
- `opener`

Diese erzeugen nicht zwingend einen eigenen Link, sondern beeinflussen einen bereits erzeugten Hyperlink.

---

## 42.5 Kontextabhängige Link Types

`alternate` ist ein wichtiges Beispiel.

Die Bedeutung hängt davon ab, welche weiteren Attribute bzw. Link Types angegeben werden.

Damit darf die Link-Type-Matrix nicht ausschließlich nach dem Keywordwert betrachtet werden.

---

# 43. Content Categories und Links

§4.6 ist kein klassischer Elementdefinitionsblock wie §4.5.

Daher besitzt die Link-Familie keine eigene gemeinsame Content-Category-Tabelle.

Die Content Categories der beteiligten Elemente müssen weiterhin aus deren jeweiligen Elementdefinitionen entnommen werden:

- `a` → §4.5.1
- `area` → §4.8
- `form` → §4.10
- `link` → §4.2.4

Für die Link-Dokumentation ist daher zwischen:

1. Elementstruktur,
2. Linkerzeugung,
3. Link Type,
4. Navigation und
5. External-Resource-Processing

zu unterscheiden.

Quelle: WHATWG §4.6 und die jeweiligen Elementdefinitionen. :contentReference[oaicite:53]{index=53}

---

# 44. Context und Content Model

Auch Context und Content Model gehören primär zu den jeweiligen Elementdefinitionen.

§4.6 beschreibt dagegen, **unter welchen Bedingungen diese Elemente Links erzeugen**.

Beispiel:

`a` mit `href` erzeugt einen Hyperlink.

Das bedeutet nicht, dass §4.6 dadurch ein neues Content Model für `a` definiert.

Für die fachliche Matrix von ZE-WebLab müssen deshalb folgende Ebenen getrennt bleiben:

| Ebene | Quelle |
|---|---|
| Elementdefinition | jeweiliger Elementabschnitt |
| Content Categories | Elementdefinition |
| Context | Elementdefinition |
| Content Model | Elementdefinition |
| Linkerzeugung | §4.6 |
| Link Types | §4.6.8 |
| Navigation | §4.6.5 |
| Download | §4.6.6 |
| Auditing | §4.6.7 |
| DOM API | §4.6.3 / §4.6.4 |

---

# 45. Attribute im Link-Modell

## 45.1 `href`

Primär relevant für:

- `a`
- `area`
- `link`

Je nach Element besitzt `href` unterschiedliche fachliche Bedeutung.

---

## 45.2 `target`

Primär relevant für:

- `a`
- `area`
- `form`

Es bestimmt das Navigationsziel bzw. Navigable Target.

---

## 45.3 `download`

Relevant für:

- `a`
- `area`

Es beeinflusst die Wahl zwischen Navigation und Download.

---

## 45.4 `ping`

Relevant für:

- `a`
- `area`

Es aktiviert Hyperlink Auditing.

---

## 45.5 `rel`

Relevant für:

- `a`
- `area`
- `form`
- `link`

Es ist die zentrale Schnittstelle zum Link-Type-System.

---

## 45.6 `referrerpolicy`

Relevant für das Hyperlink-Verhalten.

Es bestimmt die Referrer Policy beim Folgen eines Hyperlinks.

---

## 45.7 `hreflang`

Wird im Hyperlink-API-Modell reflektiert.

Es ist insbesondere für die Beschreibung der erwarteten Sprache des Zielinhalts relevant.

---

## 45.8 `type`

Wird ebenfalls im Hyperlink-API-Modell reflektiert.

Seine konkrete Verarbeitung hängt vom Link-Kontext ab.

---

# 46. DOM Interfaces

## 46.1 Elementinterfaces

Die an §4.6 beteiligten Elementinterfaces sind:

| Element | DOM Interface |
|---|---|
| `a` | `HTMLAnchorElement` |
| `area` | `HTMLAreaElement` |
| `form` | `HTMLFormElement` |
| `link` | `HTMLLinkElement` |

Diese Interfaces stammen aus den jeweiligen Elementdefinitionen bzw. DOM-Bereichen und werden durch das Link-Modell verwendet.

---

## 46.2 Hyperlink API

Das Link-API-Modell ergänzt insbesondere `a` und `area` um URL-bezogene Eigenschaften.

Dazu gehören:

- `origin`
- `protocol`
- `username`
- `password`
- `host`
- `hostname`
- `port`
- `pathname`
- `search`
- `hash`
- `hreflang`
- `type`
- `href`
- `target`

Quelle: WHATWG §4.6.3 und §4.6.4. :contentReference[oaicite:54]{index=54}

---

# 47. Sanitization

## 47.1 Abgrenzung

Sanitization ist nicht dasselbe wie Konformität.

Ein Attribut kann sanitization-relevant sein, ohne dass damit automatisch die vollständige Konformität einer Verwendung beschrieben wird.

Ebenso ist die Sanitization-Ebene nicht mit Browser-Support gleichzusetzen.

---

## 47.2 Link-spezifische Sanitization

Die Link-Familie besitzt mehrere URL- und Navigationsattribute.

Besonders relevant sind:

- `href`
- `target`
- `download`
- `ping`
- `rel`
- `referrerpolicy`

Für `a`, `area` und `link` muss die jeweilige Elementdefinition bzw. die übergreifende Sanitization-Spezifikation berücksichtigt werden.

§4.6 selbst ist primär ein Link-Processing-Abschnitt und stellt nicht für jedes Attribut eine vollständige eigenständige Sanitization-Matrix bereit.

Daher wird hier keine zusätzliche Sanitization-Regel erfunden.

---

# 48. Accessibility

## 48.1 Hyperlinks

Ein `a`-Element mit `href` ist ein Hyperlink.

Die Accessibility-Bedeutung hängt damit wesentlich davon ab, ob das Element tatsächlich einen Hyperlink erzeugt.

Ein `a` ohne `href` ist nicht einfach nur ein technisch gleichwertiger Hyperlink.

---

## 48.2 Verständliche Linkbeschriftung

§4.6 konzentriert sich auf das Link- und Navigationsmodell.

Eine vollständige Accessibility-Bewertung der Linkbeschriftung, Rollen, Namensberechnung und assistiven Technologien ist nicht allein aus §4.6 ableitbar.

Für ZE-WebLab wird deshalb zwischen:

- WHATWG-Linksemantik,
- Accessibility API Mapping,
- ARIA,
- Autorensicht und
- tatsächlicher Benutzerinteraktion

getrennt.

---

## 48.3 `noopener`, `noreferrer`, `opener`

Diese Link Types besitzen sicherheits- und navigationsrelevante Auswirkungen.

Sie sollten deshalb in der späteren Accessibility-/Security-Dokumentation nicht mit rein visuellen Linkeigenschaften vermischt werden.

---

## 48.4 Accessibility-Status

Die WHATWG-Definition allein stellt keine vollständige Accessibility-Referenz dar.

Eine vertiefte Accessibility-Ebene sollte später insbesondere folgende Quellenfamilien berücksichtigen:

- ARIA in HTML
- HTML Accessibility API Mappings
- WAI-ARIA
- Accessibility API Mapping der jeweiligen Plattformen

Für diese Datei wird daher nur die aus §4.6 unmittelbar belegbare Linksemantik dokumentiert.

---

# 49. Normative Sonderregeln

## 49.1 `href` entscheidet über Hyperlink-Erzeugung

Bei `a` und `area` erzeugt das Fehlen von `href` keinen Hyperlink.

---

## 49.2 Impliziter Hyperlink

`a` und `area` mit `href` erzeugen auch ohne passende `rel`-Hyperlink-Keywords einen impliziten Hyperlink.

Dieser besitzt keine besondere Link-Type-Semantik.

---

## 49.3 `rel` ist Token-basiert

`rel` wird als Menge von ASCII-Whitespace-getrennten Tokens verarbeitet.

Die Reihenfolge ist für die grundsätzliche Link-Type-Erkennung nicht als semantische Reihenfolge definiert.

---

## 49.4 Keywords sind ASCII-case-insensitive

Link-Type-Keywords werden ohne Unterscheidung von Groß-/Kleinschreibung verglichen.

---

## 49.5 Link Types können kombiniert werden

Beispielsweise kann `alternate` die Bedeutung von `stylesheet` verändern.

Andere Kombinationen können ebenfalls mehrere Annotationen oder Processing-Regeln gleichzeitig aktivieren.

---

## 49.6 `noreferrer` impliziert `noopener`

Das WHATWG-Navigationsmodell berücksichtigt `noreferrer` bei der Ermittlung des `noopener`-Verhaltens.

---

## 49.7 `_blank` und `noopener`

Wenn kein `opener`-Link Type angegeben ist und das Target `_blank` verwendet wird, kann das Navigationsmodell `noopener`-Verhalten ergeben.

---

## 49.8 `download` ist keine Garantie

Das Vorhandensein von `download` bedeutet nicht, dass jede Ressource zwingend heruntergeladen wird.

Das Download-Processing unterliegt weiteren Bedingungen, unter anderem:

- Navigierbarkeit,
- Sandbox-Regeln,
- URL-Verarbeitung,
- User Involvement,
- HTTP-Headern,
- Cross-Origin-Bedingungen.

---

## 49.9 Hyperlink Auditing ist optional unterdrückbar

Ein User Agent darf Ping-Anfragen unter bestimmten Umständen unterdrücken, etwa aufgrund von Benutzerpräferenzen.

---

## 49.10 `expect` kann Rendering blockieren

`expect` ist kein gewöhnlicher Hyperlink.

Er gehört zum Internal-Resource-Link-Modell und kann unter den im Standard definierten Bedingungen Rendering blockieren.

---

# 50. Link Types und `body`

Die `body-ok`-Eigenschaft ist eine wichtige normative Information für `link`.

Aktuell sind folgende Link Types als `body-ok` gekennzeichnet:

- `dns-prefetch`
- `modulepreload`
- `pingback`
- `preconnect`
- `prefetch`
- `preload`
- `stylesheet`

Daraus folgt insbesondere:

Nicht jeder `link`-Link Type darf beliebig im `body` verwendet werden.

Die `body-ok`-Information muss deshalb in einer vollständigen Link-Type-Matrix separat geführt werden.

Quelle: WHATWG §4.6.8. :contentReference[oaicite:55]{index=55}

---

# 51. Link Types und `Link`-Header

Das Link-Type-System steht außerdem mit HTTP `Link`-Headern in Beziehung.

Insbesondere bei External Resource Links existieren Verarbeitungsmodelle, die nicht ausschließlich aus HTML-Markup entstehen.

Für ZE-WebLab muss daher zwischen:

- HTML-`link`-Element,
- `rel`-Attribut,
- HTTP `Link`-Header,
- Link Type,
- External Resource Processing

unterschieden werden.

Das bedeutet:

Ein Link Type ist kein Synonym für das HTML-Element `link`.

---

# 52. Link Types und APIs

Die DOM-API und das Link-Type-System sind ebenfalls getrennte Ebenen.

Beispiel:

```html
<a href="/docs/" rel="noopener">Dokumentation</a>
```

enthält:

1. ein HTML-Element `a`,
2. ein `href`-Attribut,
3. einen Hyperlink,
4. den Link Type `noopener`,
5. Navigationsverarbeitung,
6. ein `HTMLAnchorElement`,
7. Hyperlink-API-Eigenschaften.

Für ZE-WebLab dürfen diese Informationen nicht auf einen einzigen „Link-Status“ reduziert werden.

---

# 53. Link Types und Konformität

„Link Type ist im WHATWG Standard definiert“ bedeutet nicht automatisch:

> Jede Kombination dieses Keywords mit jedem Element ist konform.

Die zulässigen Elemente sind für jeden Link Type separat definiert.

Beispiele:

- `canonical` → `link`
- `bookmark` → `a`, `area`
- `stylesheet` → `link`
- `external` → `a`, `area`, `form`
- `search` → `link`, `a`, `area`, `form`

Die Elementzulässigkeit ist deshalb ein eigener Teil der Matrix.

---

# 54. V1-Referenzmodell für ZE-WebLab

## 54.1 Elementebene

Die folgenden Elemente werden als bereits in anderen WHATWG-Bereichen definierte Elemente verknüpft:

- `a`
- `area`
- `form`
- `link`

§4.6 wird dabei als Link-Feature-Familie referenziert.

---

## 54.2 Feature-Ebene

Folgende Feature-Familien werden in V1 aufgenommen:

1. Link-Konzept
2. External Resource Links
3. Hyperlinks
4. Internal Resource Links
5. Hyperlink API
6. `a`/`area` Hyperlink API
7. Hyperlink Navigation
8. Download Processing
9. Hyperlink Auditing
10. Ping Headers
11. Link Types
12. Link-Type-Erweiterungen

---

## 54.3 Link-Type-Ebene

Alle im aktuellen WHATWG §4.6.8 definierten Link Types werden in V1 als eigene Feature Records geführt.

Dazu gehören:

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

---

# 55. WHATWG-Status und Browser-Support

Für diese Datei gilt ausdrücklich:

**WHATWG-Status ≠ Browser-Kompatibilität**

Ein Feature kann im WHATWG Standard definiert sein, auch wenn einzelne Browser es nicht oder unterschiedlich implementieren.

Die in der WHATWG-Seite eingeblendeten MDN-Kompatibilitätsinformationen werden daher nicht in den V1-Status übernommen.

Der V1-Status bedeutet hier:

> Das Feature ist Bestandteil der aktuell recherchierten WHATWG-Spezifikation.

Er bedeutet nicht:

> Das Feature funktioniert in jedem Browser.

---

# 56. Querverweise zu anderen WHATWG-Bereichen

| Thema | Relevanz |
|---|---|
| §3.2.5 Content Categories | Eigenschaften der beteiligten Elemente |
| §3.2.6 Global attributes | globale Attribute |
| §3.2.9 Accessibility | Accessibility-Modell |
| §4.2 Document metadata | `link`-Element |
| §4.5 Text-level semantics | `a`-Element |
| §4.8 Embedded content | `area`-Element |
| §4.10 Forms | `form`-Element |
| Navigation | Verarbeitung von Hyperlinks |
| URL Standard | URL-Parsing und Serialisierung |
| Fetch Standard | Ressourcenabruf |
| Referrer Policy | Referrer-Verarbeitung |
| DOM Standard | DOM Interfaces und Elementverhalten |
| CSS | Stylesheet-Verarbeitung |
| HTTP | `Link`, `Content-Disposition`, Ping-Header |
| Web Manifest | `manifest` |
| Module | `modulepreload` |
| Pingback | `pingback` |
| RFC 6596 | `canonical` |
| RFC 6903 | `privacy-policy`, `terms-of-service` |

---

# 57. Fachliche Abgrenzung: `a` versus Link Type

Ein häufiger Modellierungsfehler wäre:

> `a` = Link

Das ist zu kurz.

Korrekt ist:

`a` ist ein HTML-Element, das unter bestimmten Bedingungen einen Hyperlink erzeugt.

Dieser Hyperlink kann:

- keine spezielle `rel`-Semantik besitzen,
- durch `rel` annotiert werden,
- mehrere Link Types besitzen,
- navigieren,
- einen Download auslösen,
- Hyperlink Auditing auslösen,
- ein bestimmtes Target verwenden,
- eine bestimmte Referrer Policy besitzen.

Damit ist der Hyperlink ein **Konzept**, während `a` ein **Element** ist.

---

# 58. Fachliche Abgrenzung: `link` versus Link Type

Ebenso darf nicht modelliert werden:

> `link` = Stylesheet

`link` ist ein Element.

Je nach `rel` kann es unter anderem:

- Stylesheets laden,
- Icons laden,
- Manifeste laden,
- Ressourcen vorladen,
- Verbindungen vorab aufbauen,
- Ressourcen prefetchen,
- interne Ressourcen referenzieren,
- Hyperlinks repräsentieren.

`stylesheet` ist nur einer der Link Types.

---

# 59. Fachliche Abgrenzung: `rel` versus Link Type

`rel` ist das Attribut.

Ein Link Type ist die semantische Bedeutung eines einzelnen `rel`-Tokens.

Beispiel:

```html
<a
  href="/docs/"
  rel="noopener noreferrer"
>
  Dokumentation
</a>
```

Hier ist:

- `rel` das Attribut,
- `noopener` ein Link Type,
- `noreferrer` ein weiterer Link Type.

Die beiden dürfen deshalb nicht als identisches Datenmodell behandelt werden.

---

# 60. Fachliche Abgrenzung: Hyperlink versus Navigation

Ein Hyperlink ist die semantische Verbindung.

Navigation ist die Verarbeitung, die beim Folgen des Hyperlinks ausgeführt werden kann.

Ein Hyperlink kann beispielsweise durch:

- Benutzeraktivierung,
- Scriptaktivierung,
- `download`,
- Target-Regeln

unterschiedlich verarbeitet werden.

Daher sind „Hyperlink vorhanden“ und „Navigation ausgeführt“ zwei unterschiedliche Zustände.

---

# 61. Fachliche Abgrenzung: Hyperlink versus Download

`download` verändert das Aktivierungs-/Processing-Verhalten.

Der Hyperlink bleibt ein Hyperlink.

Die Aktivierung kann jedoch in das Download-Processing statt in das normale Follow-Hyperlink-Processing führen.

Damit darf `download` nicht als eigener Link Type modelliert werden.

Es ist ein Attribut mit Processing-Model-Auswirkung.

---

# 62. Fachliche Abgrenzung: `ping` versus `rel`

`ping` und `rel` erfüllen unterschiedliche Funktionen.

`rel` beschreibt Link Types.

`ping` beschreibt zusätzliche URLs für Hyperlink Auditing.

Beide sind Bestandteil des Link-Modells, gehören aber zu unterschiedlichen Feature-Ebenen.

---

# 63. Fachliche Abgrenzung: `noopener` versus `noreferrer`

`noopener` beeinflusst den Opener-/Browsing-Context-Zusammenhang.

`noreferrer` beeinflusst die Referrer-Übermittlung und bewirkt zusätzlich entsprechendes `noopener`-Verhalten.

Sie sind daher nicht semantisch identisch.

---

# 64. Fachliche Abgrenzung: `next` versus Navigation

`next` beschreibt die logische Position des referenzierten Dokuments innerhalb einer Sequenz.

Es ist nicht einfach eine alternative Schreibweise für „Navigation nach vorne“.

Die Navigation selbst bleibt Teil des Hyperlink-Processing-Modells.

---

# 65. Fachliche Abgrenzung: `prev` versus Browser-History

`prev` beschreibt das vorherige logische Dokument einer Dokumentsequenz.

Es ist nicht automatisch gleichbedeutend mit dem Zurückgehen in der Browser-History.

Diese Unterscheidung muss in ZE-WebLab ausdrücklich erhalten bleiben.

---

# 66. Fachliche Abgrenzung: `canonical` versus Redirect

`canonical` beschreibt eine bevorzugte URL für das aktuelle Dokument.

Es ist kein HTTP-Redirect.

Es ersetzt insbesondere nicht:

- `301`
- `302`
- andere HTTP-Redirect-Mechanismen.

Die HTTP-/SEO-Verarbeitung ist eine separate Ebene.

---

# 67. Fachliche Abgrenzung: `preload` versus `prefetch`

`preload` und `prefetch` sind nicht dasselbe.

`preload` beschreibt eine Ressource, die das aktuelle Dokument voraussichtlich benötigt.

`prefetch` beschreibt eine Ressource oder ein Dokument, dessen zukünftige Nutzung wahrscheinlich ist.

Die Priorität und konkrete Fetch-Verarbeitung unterscheiden sich.

---

# 68. Fachliche Abgrenzung: `preload` versus `modulepreload`

`modulepreload` ist speziell auf Module Scripts ausgerichtet.

Es verwendet das für Module Scripts vorgesehene Fetch-Verhalten und beeinflusst die Module Map.

`preload` verwendet dagegen das allgemeine Preload-Modell.

Daher ist `modulepreload` als eigener Link Type zu führen.

Quelle: WHATWG §4.6.8.12 und §4.6.8.20. :contentReference[oaicite:56]{index=56}

---

# 69. Fachliche Abgrenzung: `stylesheet` versus CSS

`stylesheet` ist ein HTML-Link Type.

Die eigentliche Stylesheet-Semantik und CSS-Verarbeitung liegt nicht vollständig in §4.6.

Für ZE-WebLab muss daher zwischen:

- HTML-Linkerzeugung,
- Fetch,
- CSS Resource,
- CSS Style Sheet Object,
- Rendering

unterschieden werden.

---

# 70. Fachliche Abgrenzung: `icon` versus Favicon

`icon` ist der standardisierte Link Type.

Die konkrete Verwendung als sogenanntes Favicon ist ein Anwendungsfall dieses Link Types.

Das Datenmodell sollte daher nicht den informellen Begriff „Favicon“ als WHATWG-Link-Type verwenden.

---

# 71. Fachliche Abgrenzung: Standard-Link Types versus Extensions

Nicht jeder in der Praxis verwendete `rel`-Wert ist automatisch ein WHATWG-standardisierter Link Type.

ZE-WebLab sollte deshalb mindestens drei Zustände unterscheiden:

1. WHATWG-definierter Link Type
2. registrierter/standardisierter externer Link Relation Type
3. unbekanntes bzw. nicht standardisiertes Token

Damit wird vermieden, externe Konventionen fälschlich als WHATWG-Feature zu kennzeichnen.

---

# 72. Inventar für die spätere Vollständigkeitsmatrix

Für die zentrale Matrix sollte §4.6 mindestens folgende Feature Records erhalten:

| ID-Familie | Feature |
|---|---|
| LINK-CONCEPT | Links |
| LINK-EXTERNAL | External Resource Link |
| LINK-HYPERLINK | Hyperlink |
| LINK-INTERNAL | Internal Resource Link |
| LINK-A-HREF | `a`/`area` `href` |
| LINK-TARGET | `target` |
| LINK-DOWNLOAD | `download` |
| LINK-PING | `ping` |
| LINK-REL | `rel` |
| LINK-REFERRERPOLICY | `referrerpolicy` |
| LINK-API | `HyperlinkElementUtils` |
| LINK-API-AAREA | `HTMLHyperlinkElementUtils` |
| LINK-NAVIGATION | Follow Hyperlink |
| LINK-DOWNLOAD-MODEL | Download Processing |
| LINK-AUDIT | Hyperlink Auditing |
| LINK-PING-FROM | `Ping-From` |
| LINK-PING-TO | `Ping-To` |
| REL-ALTERNATE | `alternate` |
| REL-AUTHOR | `author` |
| REL-BOOKMARK | `bookmark` |
| REL-CANONICAL | `canonical` |
| REL-DNS-PREFETCH | `dns-prefetch` |
| REL-EXPECT | `expect` |
| REL-EXTERNAL | `external` |
| REL-HELP | `help` |
| REL-ICON | `icon` |
| REL-LICENSE | `license` |
| REL-MANIFEST | `manifest` |
| REL-MODULEPRELOAD | `modulepreload` |
| REL-NOFOLLOW | `nofollow` |
| REL-NOOPENER | `noopener` |
| REL-NOREFERRER | `noreferrer` |
| REL-OPENER | `opener` |
| REL-PINGBACK | `pingback` |
| REL-PRECONNECT | `preconnect` |
| REL-PREFETCH | `prefetch` |
| REL-PRELOAD | `preload` |
| REL-PRIVACY-POLICY | `privacy-policy` |
| REL-SEARCH | `search` |
| REL-STYLESHEET | `stylesheet` |
| REL-TAG | `tag` |
| REL-TERMS-OF-SERVICE | `terms-of-service` |
| REL-NEXT | `next` |
| REL-PREV | `prev` |
| REL-EXTENSIONS | Other link types |

---

# 73. Prüfmatrix für die Link-Type-Familie

| Link Type | `link` | `a` | `area` | `form` | Hyperlink | External Resource | Internal Resource | Annotation | body-ok |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| `alternate` | ja | ja | ja | nein | kontextabhängig | kontextabhängig | nein | nein | nein |
| `author` | ja | ja | ja | nein | ja | nein | nein | nein | nein |
| `bookmark` | nein | ja | ja | nein | ja | nein | nein | nein | nein |
| `canonical` | ja | nein | nein | nein | ja | nein | nein | nein | nein |
| `dns-prefetch` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `expect` | ja | nein | nein | nein | nein | nein | ja | nein | nein |
| `external` | nein | ja | ja | ja | nein | nein | nein | ja | — |
| `help` | ja | ja | ja | ja | ja | nein | nein | nein | kontextabhängig |
| `icon` | ja | nein | nein | nein | nein | ja | nein | nein | nein |
| `license` | ja | ja | ja | ja | ja | nein | nein | nein | nein |
| `manifest` | ja | nein | nein | nein | nein | ja | nein | nein | nein |
| `modulepreload` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `nofollow` | nein | ja | ja | ja | nein | nein | nein | ja | — |
| `noopener` | nein | ja | ja | ja | nein | nein | nein | ja | — |
| `noreferrer` | nein | ja | ja | ja | nein | nein | nein | ja | — |
| `opener` | nein | ja | ja | ja | nein | nein | nein | ja | — |
| `pingback` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `preconnect` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `prefetch` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `preload` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `privacy-policy` | ja | ja | ja | nein | ja | nein | nein | nein | nein |
| `search` | ja | ja | ja | ja | ja | nein | nein | nein | nein |
| `stylesheet` | ja | nein | nein | nein | nein | ja | nein | nein | ja |
| `tag` | nein | ja | ja | nein | ja | nein | nein | nein | nein |
| `terms-of-service` | ja | ja | ja | nein | ja | nein | nein | nein | nein |
| `next` | ja | ja | ja | ja | ja | kontextabhängig | nein | nein | nein |
| `prev` | ja | ja | ja | ja | ja | kontextabhängig | nein | nein | nein |

> Die Tabelle ist eine normalisierte ZE-WebLab-Darstellung. Die normative Quelle bleibt die jeweilige Link-Type-Definition in WHATWG §4.6.8. Bei kontextabhängigen Link Types darf die Tabelle nicht als Ersatz für die vollständige normative Definition interpretiert werden.

Quelle: WHATWG §4.6.8. :contentReference[oaicite:57]{index=57}

---

# 74. Status / V1

## 74.1 WHATWG-Status

Die in dieser Datei dokumentierten §4.6-Features sind in der aktuell recherchierten WHATWG HTML Living Standard definiert.

**Status:** aktuell definiert.

---

## 74.2 Konformität

Die Aussage „definiert“ bedeutet nicht:

> Jede Verwendung ist konform.

Die Konformität hängt unter anderem ab von:

- dem verwendeten Element,
- vorhandenen Attributen,
- dem konkreten Link Type,
- dem zulässigen Elementkontext,
- weiteren Attributkombinationen,
- dem jeweiligen Processing Model.

---

## 74.3 Browser-Support

Browser-Support ist bewusst nicht Bestandteil des WHATWG-Status.

Er wird später separat recherchiert.

---

# 75. Offene bzw. separat zu bearbeitende Punkte

Die Detailprüfung von §4.6 ist abgeschlossen.

Folgende Themen bleiben bewusst eigene Referenzbereiche:

1. vollständiges globales Attributinventar,
2. vollständige elementbezogene Attributmatrix,
3. vollständige `a`-Elementdefinition aus §4.5.1,
4. vollständige `area`-Elementdefinition aus §4.8,
5. vollständige `form`-Elementdefinition aus §4.10,
6. vollständige `link`-Elementdefinition aus §4.2.4,
7. vollständige Content-Category-Matrix,
8. vollständige Accessibility-Zuordnungen,
9. vollständiges Sanitization-Modell,
10. URL-Standard als eigenständige Referenz,
11. Fetch- und HTTP-Verarbeitungsmodelle,
12. Referrer Policy als eigenständige Spezifikation,
13. CSS Stylesheet Processing,
14. Web Manifest,
15. Module Scripts,
16. Pingback,
17. externe Link-Relation-Registrierungen,
18. Browser-Kompatibilität.

Diese Punkte sind keine Lücken in der §4.6-Recherche, sondern bewusst getrennte Referenzebenen.

---

# 76. Recherchefazit

§4.6 ist nicht lediglich eine Beschreibung des `a`-Elements.

Der Abschnitt definiert ein umfangreiches Link-Modell mit mehreren Ebenen:

- Link als konzeptionelle Beziehung,
- External Resource Links,
- Hyperlinks,
- Internal Resource Links,
- `a`-/`area`-Linkerzeugung,
- Hyperlink APIs,
- Navigation,
- Download,
- Hyperlink Auditing,
- Ping-Header,
- Link Types,
- Link-Type-Erweiterungen.

Besonders wichtig für ZE-WebLab ist die Trennung zwischen:

**Element**

und

**Link**

und

**Link Type**

und

**Processing Model**

und

**DOM API**.

Eine einfache Liste wie:

```text
<a>
<area>
<link>
```

würde den fachlichen Umfang von §4.6 daher nicht angemessen abbilden.

---

# 77. Quellen / Referenzen

## Primärquelle

- WHATWG HTML Living Standard, §4.6 „Links“, aktuelle Fassung, Stand 11. August 2026. :contentReference[oaicite:58]{index=58}
- WHATWG HTML Living Standard, §4.6.1–§4.6.8, vollständige Link-Struktur. :contentReference[oaicite:59]{index=59}
- WHATWG HTML Living Standard, API für Hyperlink-Elemente. :contentReference[oaicite:60]{index=60}
- WHATWG HTML Living Standard, Navigation und Download Processing. :contentReference[oaicite:61]{index=61}
- WHATWG HTML Living Standard, `expect` Internal Resource Link. :contentReference[oaicite:62]{index=62}
- WHATWG HTML Living Standard, `noopener`, `noreferrer` und `opener`. :contentReference[oaicite:63]{index=63}
- WHATWG HTML Living Standard, `stylesheet`-Processing. :contentReference[oaicite:64]{index=64}

## Verwandte WHATWG-Bereiche

- WHATWG HTML Living Standard, §4.5 „Text-level semantics“ – insbesondere `a`. :contentReference[oaicite:65]{index=65}
- WHATWG HTML Living Standard, §4.2 „Document metadata“ – insbesondere `link`. :contentReference[oaicite:66]{index=66}
- WHATWG HTML Living Standard, §4.8 „Embedded content“ – insbesondere `area`. :contentReference[oaicite:67]{index=67}
- WHATWG HTML Living Standard, §4.10 „Forms“ – insbesondere `form`. :contentReference[oaicite:68]{index=68}

---

## Prüfstatus

**§4.6 „Links“ vollständig recherchiert und für ZE-WebLab dokumentiert.**

Die Datei behandelt:

- Link-Konzept
- `a`-/`area`-Linkerzeugung
- `href`
- `target`
- `download`
- `ping`
- `rel`
- `referrerpolicy`
- Hyperlink APIs
- Navigation
- Download Processing
- Hyperlink Auditing
- `Ping-From`
- `Ping-To`
- sämtliche aktuellen WHATWG-Link Types aus §4.6.8
- sequenzielle Link Types
- Link-Type-Erweiterungen
- DOM-Interfaces
- Accessibility-Abgrenzung
- Sanitization-Abgrenzung
- normative Sonderregeln
- Querverweise
- V1-Status
- offene, bewusst separat zu bearbeitende Themen

**Browser-Kompatibilität wurde nicht als WHATWG-Status übernommen.**