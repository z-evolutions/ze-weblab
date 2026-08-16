# ZE-WebLab – HTML-Referenz: Safe Passing of Structured Data

## Arbeitsstand / Quellenstand

- **Projekt:** ZE-WebLab
- **Datei:** `docs/html/29-safe-passing-of-structured-data.md`
- **Rechercheebene:** Zweite Rechercheebene – übergreifende HTML-Konzepte und Feature-Familien
- **Feature-Familie:** Safe Passing of Structured Data
- **Feature-Typ:** Processing Model / Serialization Model / Transfer Model / API
- **Normative Primärquelle:** WHATWG HTML Living Standard
- **WHATWG-Hauptbereich:** §2.7 „Safe passing of structured data“
- **Geprüfter WHATWG-Stand:** 11. August 2026
- **Prüfstatus:** vollständig recherchiert für §2.7 und §2.7.1–§2.7.10
- **Browser-Kompatibilität:** nicht Bestandteil dieser Datei
- **V1-Status:** projektspezifisch und nicht mit dem WHATWG-Status gleichzusetzen

### Quellenabgrenzung

Das ZE-WebLab-Repository beantwortet die Frage:

> Welche Informationen wurden im Projekt bereits dokumentiert?

Der WHATWG HTML Living Standard beantwortet die Frage:

> Welche Regeln definiert HTML für das sichere Serialisieren, Deserialisieren, Kopieren und Übertragen strukturierter JavaScript-Werte?

Diese Datei dokumentiert die gemeinsame HTML-Infrastruktur für Structured Cloning.

Sie ist:

- keine Elementreferenz,
- keine vollständige JavaScript-Referenz,
- keine vollständige Web-IDL-Referenz,
- keine vollständige Dokumentation des DOM Standards,
- keine vollständige Dokumentation des Worker- oder Messaging-Modells.

Die konkrete Verwendung der Structured-Clone-Infrastruktur durch andere HTML- oder Web-APIs wird dort zusätzlich dokumentiert, wo diese APIs definiert sind.

---

## Einordnung

### Safe Passing of Structured Data

HTML definiert eine gemeinsame Infrastruktur, mit der JavaScript-Werte:

- serialisiert,
- deserialisiert,
- zwischen Realms übertragen,
- zwischen Agents beziehungsweise Agent Clusters verwendet,
- als strukturierte Kopien erzeugt,
- oder bei bestimmten Objekten durch Transfer statt durch Kopieren weitergegeben

werden können.

Die Spezifikation bezeichnet diesen Gesamtmechanismus als:

**structured cloning**

Die Infrastruktur ist insbesondere für APIs relevant, die JavaScript-Werte zwischen unterschiedlichen Ausführungskontexten oder Zuständen übertragen müssen.

### Structured Cloning ist kein HTML-Element

Structured Cloning ist:

- kein HTML-Element,
- keine Content Category,
- kein Content Model,
- kein Link Type,
- kein Global Attribute,
- kein Custom Element.

Es handelt sich um ein normatives Serialisierungs- und Verarbeitungsmodell.

### Structured Cloning ist nicht dasselbe wie JSON

Structured Cloning darf nicht mit JSON-Serialisierung gleichgesetzt werden.

Insbesondere unterstützt das WHATWG-Modell Werte und Objektstrukturen, die mit einer einfachen JSON-Konvertierung nicht gleichwertig behandelt werden können.

Dazu gehören unter anderem:

- `Map`
- `Set`
- `Date`
- `RegExp`
- `ArrayBuffer`
- bestimmte ArrayBuffer Views
- `SharedArrayBuffer` unter den definierten Voraussetzungen
- bestimmte serialisierbare Plattformobjekte
- zirkuläre Objektstrukturen

### Structured Cloning ist nicht dasselbe wie eine flache Kopie

Der Mechanismus arbeitet rekursiv.

Verschachtelte Werte werden entsprechend den definierten Serialisierungsregeln verarbeitet.

Beispiel:

```js
const source = {
  name: "example",
  nested: {
    value: 42
  }
};

const copy = structuredClone(source);
```

`copy` ist dabei nicht lediglich eine neue Referenz auf `source`.

---

# WHATWG-Struktur

Der aktuelle WHATWG HTML Living Standard führt unter §2.7 folgende Unterabschnitte:

1. §2.7.1 Serializable objects
2. §2.7.2 Transferable objects
3. §2.7.3 StructuredSerializeInternal
4. §2.7.4 StructuredSerialize
5. §2.7.5 StructuredSerializeForStorage
6. §2.7.6 StructuredDeserialize
7. §2.7.7 StructuredSerializeWithTransfer
8. §2.7.8 StructuredDeserializeWithTransfer
9. §2.7.9 Performing serialization and transferring from other specifications
10. §2.7.10 Structured cloning API

Damit umfasst §2.7 sowohl:

- Objektklassifikation,
- Serialisierung,
- Deserialisierung,
- Transfer,
- Speicher-/Zustandsbehandlung,
- API-Integration

als auch die globale `structuredClone()`-API.

---

# Inventar

| ID | Feature | Feature-Typ | WHATWG-Abschnitt | Erste-Ebene-Abdeckung | Abdeckungsstatus | Zweite-Ebene-Relevanz |
|---|---|---|---|---|---|---|
| SCD-001 | Safe passing of structured data | Processing Model | §2.7 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-002 | Serializable objects | Serialization Model | §2.7.1 | API-/Scripting-Bezug vorhanden | teilweise | eigenständig |
| SCD-003 | `[Serializable]` | Web IDL Integration | §2.7.1 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-004 | Serialization steps | Processing Model | §2.7.1 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-005 | Deserialization steps | Processing Model | §2.7.1 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-006 | Transferable objects | Transfer Model | §2.7.2 | API-bezogen | teilweise | eigenständig |
| SCD-007 | `[Transferable]` | Web IDL Integration | §2.7.2 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-008 | Transfer steps | Processing Model | §2.7.2 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-009 | Transfer-receiving steps | Processing Model | §2.7.2 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-010 | `[[Detached]]` | Internal State | §2.7.2 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-011 | `StructuredSerializeInternal` | Serialization Algorithm | §2.7.3 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-012 | Serialization memory map | Processing Model | §2.7.3 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-013 | Structured cyclic graph serialization | Processing Model | §2.7.3 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-014 | `StructuredSerialize` | Serialization API Primitive | §2.7.4 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-015 | `StructuredSerializeForStorage` | Storage Serialization | §2.7.5 | teilweise über History APIs | teilweise | eigenständig |
| SCD-016 | `StructuredDeserialize` | Deserialization Algorithm | §2.7.6 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-017 | Target Realm | Processing Model | §2.7.6 | API-bezogen | teilweise | eigenständig |
| SCD-018 | `StructuredSerializeWithTransfer` | Transfer Serialization | §2.7.7 | API-bezogen | teilweise | eigenständig |
| SCD-019 | Transfer List | Transfer Model | §2.7.7 | API-bezogen | teilweise | eigenständig |
| SCD-020 | `StructuredDeserializeWithTransfer` | Transfer Deserialization | §2.7.8 | API-bezogen | teilweise | eigenständig |
| SCD-021 | Transferred Values | Transfer Model | §2.7.8 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-022 | Cross-specification serialization | Integration Feature | §2.7.9 | teilweise | teilweise | eigenständig |
| SCD-023 | Structured Cloning API | API | §2.7.10 | API-/Scripting-Bezug | teilweise | eigenständig |
| SCD-024 | `structuredClone()` | API | §2.7.10 | nicht zentral dokumentiert | neu | eigenständig |
| SCD-025 | `DataCloneError` | Error / API Processing | §2.7.1–§2.7.10 | API-bezogen | teilweise | eigenständig |

---

# Begriffsdefinitionen

## Structured Clone

Ein Structured Clone ist eine nach den HTML-Regeln erzeugte strukturierte Kopie eines JavaScript-Wertes.

Dabei werden nicht einfach Objektidentitäten übernommen.

Stattdessen wird ein serialisierter, Realm-unabhängiger Zustand erzeugt und anschließend in einem Zielkontext wiederhergestellt.

---

## Serializable Object

Ein serializable object ist ein Objekt, das nach den Regeln von §2.7 serialisiert und anschließend deserialisiert werden kann.

Für Plattformobjekte kann die Serialisierbarkeit über die Web-IDL Extended Attribute:

```webidl
[Serializable]
```

ausgedrückt werden.

Eine solche Schnittstelle muss die zugehörigen:

- serialization steps
- deserialization steps

definieren.

---

## Transferable Object

Ein transferable object ist ein Objekt, dessen zugrunde liegende Ressource beziehungsweise Daten nicht lediglich kopiert, sondern an den Zielkontext übertragen werden können.

Der ursprüngliche Wert wird dabei in einen Zustand versetzt, in dem er nicht mehr normal verwendet werden kann.

Transfer ist deshalb grundsätzlich von Cloning zu unterscheiden.

---

## Serialization

Serialization wandelt einen JavaScript-Wert in eine Realm-unabhängige interne Repräsentation um.

Diese Repräsentation kann später deserialisiert werden.

---

## Deserialization

Deserialization erzeugt aus einer zuvor erzeugten serialisierten Repräsentation einen neuen JavaScript-Wert in einem angegebenen Ziel-`Realm`.

---

## Transfer

Transfer verschiebt bestimmte zugrunde liegende Ressourcen beziehungsweise Zustände an den Zielkontext.

Dabei wird der ursprüngliche Wert entsprechend den definierten Regeln unbrauchbar beziehungsweise detached.

Transfer ist:

- irreversibel,
- nicht idempotent,
- nicht mit normalem Kopieren gleichzusetzen.

---

## Realm

Ein Realm ist ein JavaScript-Ausführungskontext im Sinne der JavaScript-Spezifikation.

Structured Cloning ist ausdrücklich so modelliert, dass Daten zwischen unterschiedlichen Realms übertragen beziehungsweise rekonstruiert werden können.

---

## Target Realm

Der target realm ist der Realm, in dem ein deserialisiertes Objekt erzeugt wird.

Die Deserialisierung muss deshalb nicht lediglich Daten rekonstruieren, sondern auch die korrekten Ziel-Realm-Objekte erzeugen.

---

## Transfer List

Eine Transfer List enthält Objekte, die bei einer Structured-Clone-Operation nicht kopiert, sondern übertragen werden sollen.

Sie wird insbesondere von:

```js
structuredClone(value, {
  transfer: [...]
});
```

verwendet.

---

## DataCloneError

`DataCloneError` ist eine `DOMException`, die unter anderem dann verwendet wird, wenn ein Wert nicht nach den jeweiligen Structured-Clone-Regeln verarbeitet werden kann.

Typische Ursachen sind:

- nicht serialisierbare Objekte,
- nicht zulässige Transferobjekte,
- bereits detached Objekte,
- unzulässige Transferlisten,
- Ziel- oder Agent-Cluster-Konflikte bei bestimmten Objekttypen.

---

# Serializable Objects

## §2.7.1

Serializable objects können:

1. serialisiert,
2. gespeichert oder übertragen,
3. später deserialisiert

werden.

Dabei muss die serialisierte Repräsentation unabhängig von einem konkreten JavaScript-`Realm` sein.

---

## `[Serializable]`

Für Plattformobjekte kann eine Schnittstelle mit:

```webidl
[Serializable]
```

gekennzeichnet werden.

Die Extended Attribute:

- nimmt keine Argumente,
- darf nur auf Interfaces verwendet werden,
- darf pro Interface nicht mehrfach angegeben werden.

Die betreffende Interface-Definition muss die erforderlichen Algorithmen bereitstellen.

---

## Serialization Steps

Serialization Steps erhalten konzeptionell:

- das zu serialisierende Plattformobjekt,
- die serialisierte Repräsentation,
- den `forStorage`-Zustand.

Die Schritte bestimmen, welche internen Daten des Objekts serialisiert werden.

Die konkrete Datenstruktur ist nicht pauschal für alle Plattformobjekte identisch.

---

## Deserialization Steps

Deserialization Steps erhalten konzeptionell:

- die serialisierte Repräsentation,
- ein neu erzeugtes Zielobjekt,
- den Ziel-`Realm`.

Die Schritte stellen die internen Daten des neuen Objekts wieder her.

Das Zielobjekt wird nicht einfach als Referenz des ursprünglichen Objekts übernommen.

---

## Primary Interface

Für ein serialisierbares Plattformobjekt ist die primäre Interface-Definition maßgeblich.

Bei einer Interface-Vererbung muss jede entsprechend markierte Interface-Definition ihre eigenen erforderlichen Serialisierungs- und Deserialisierungsschritte bereitstellen.

Dabei müssen relevante geerbte Daten berücksichtigt werden.

---

## Sub-Serialization

Serialisierungsschritte können verschachtelte Werte über Sub-Serialization verarbeiten.

Konzeptionell wird hierfür erneut:

```text
StructuredSerializeInternal(subValue, forStorage, memory)
```

verwendet.

Die Verwendung des gemeinsamen `memory`-Kontexts ist wichtig, damit zyklische beziehungsweise gemeinsam referenzierte Strukturen korrekt verarbeitet werden.

---

# Transferable Objects

## §2.7.2

Transferable objects können zwischen Agents beziehungsweise Ausführungskontexten übertragen werden.

Beim Transfer wird nicht einfach eine unabhängige Kopie erstellt.

Stattdessen wird die zugrunde liegende Ressource entsprechend den normativen Regeln übertragen.

Der ursprüngliche Wert wird anschließend detached.

---

## `[Transferable]`

Eine Plattformobjekt-Schnittstelle kann über:

```webidl
[Transferable]
```

als transferable definiert werden.

Die Extended Attribute:

- nimmt keine Argumente,
- darf nur auf Interfaces verwendet werden,
- darf pro Interface nicht mehrfach angegeben werden.

Die Interface-Definition muss die zugehörigen Transferalgorithmen bereitstellen.

---

## Transfer Steps

Transfer Steps übernehmen den Zustand eines transferierbaren Objekts in einen internen `dataHolder`.

Der erzeugte Datenhalter muss unabhängig von einem bestimmten Realm sein.

---

## Transfer-Receiving Steps

Transfer-Receiving Steps übernehmen einen zuvor erzeugten `dataHolder` und richten damit ein neues Objekt im Zielkontext ein.

Das Zielobjekt wird neu erzeugt.

Die zugrunde liegenden Daten werden jedoch nach den Transferregeln übernommen.

---

## `[[Detached]]`

Transferable Plattformobjekte können einen internen Zustand:

```text
[[Detached]]
```

besitzen.

Ist dieser Zustand gesetzt, kann das Objekt nicht erneut auf dieselbe Weise transferiert werden.

Damit wird die Einmaligkeit des Transfers normativ abgesichert.

---

# StructuredSerializeInternal

## §2.7.3

`StructuredSerializeInternal` ist der zentrale Serialisierungsalgorithmus.

Er erhält:

```text
value
forStorage
memory
```

und erzeugt eine Realm-unabhängige serialisierte Repräsentation.

---

## Memory Map

Der `memory`-Parameter ist ein zentrales Element des Algorithmus.

Er verhindert:

- doppelte Serialisierung desselben Objekts,
- Verlust von Objektidentität innerhalb des Graphen,
- Probleme bei zyklischen Referenzen.

Beispiel:

```js
const object = {};
object.self = object;
```

Die Struktur enthält eine zyklische Referenz.

Der Serialisierungsalgorithmus kann diese Struktur durch die `memory`-Map repräsentieren, ohne unendlich rekursiv zu werden.

---

## Primitive Werte

Folgende primitive JavaScript-Werte können unmittelbar als primitive serialisierte Werte behandelt werden:

- `undefined`
- `null`
- Boolean-Werte
- Number-Werte
- BigInt-Werte
- String-Werte

---

## Symbol

Ein `Symbol` kann nicht über die normale Structured-Clone-Serialisierung verarbeitet werden.

Für einen entsprechenden Wert wird:

```text
DataCloneError
```

ausgelöst.

---

## Boolean Objects

Boolean Wrapper Objects können anhand ihres internen Boolean-Zustands serialisiert werden.

---

## Number Objects

Number Wrapper Objects werden anhand ihres internen Number-Zustands serialisiert.

---

## BigInt Objects

BigInt Wrapper Objects werden anhand ihres internen BigInt-Zustands serialisiert.

---

## String Objects

String Wrapper Objects werden anhand ihres internen String-Zustands serialisiert.

---

## Date

`Date`-Objekte werden anhand ihres internen Datumswerts serialisiert.

---

## RegExp

`RegExp`-Objekte werden unter anderem anhand ihrer:

- Matcher-Repräsentation,
- ursprünglichen Source,
- ursprünglichen Flags

serialisiert.

---

## ArrayBuffer

`ArrayBuffer` kann serialisiert werden, sofern die jeweils definierten Voraussetzungen erfüllt sind.

Die Serialisierung umfasst die zugrunde liegenden Daten.

Ein bereits detached Buffer kann nicht regulär serialisiert werden.

---

## ResizableArrayBuffer

Für Resizable ArrayBuffers berücksichtigt die Structured-Clone-Infrastruktur zusätzlich die maximale Byte-Länge.

---

## SharedArrayBuffer

`SharedArrayBuffer` besitzt besondere Sicherheits- und Agent-Cluster-Regeln.

Insbesondere ist die Verarbeitung an die cross-origin-isolated capability gebunden.

Ein SharedArrayBuffer kann nicht beliebig über beliebige Agent-Cluster-Grenzen hinweg serialisiert werden.

Für Storage-Serialisierung ist `SharedArrayBuffer` nicht zulässig.

---

## ArrayBuffer Views

Zu den ArrayBuffer Views gehören insbesondere:

- `DataView`
- Typed Arrays

Die Serialisierung berücksichtigt:

- zugrunde liegenden Buffer,
- Byte Length,
- Byte Offset,
- gegebenenfalls Array Length,
- Typed-Array-Typ.

---

## Map

`Map` wird als strukturierte Liste von Schlüssel-/Wert-Paaren verarbeitet.

Sowohl:

- Schlüssel
- Werte

werden rekursiv serialisiert.

---

## Set

`Set` wird als strukturierte Liste von Einträgen verarbeitet.

Jeder Eintrag wird rekursiv serialisiert.

---

## Error Objects

Error Objects werden nach den definierten Structured-Clone-Regeln verarbeitet.

Dabei können insbesondere berücksichtigt werden:

- Error-Typ,
- `message`,
- `stack`,
- zusätzliche interessante Daten.

Die konkrete Behandlung des `stack`-Wertes besitzt einen implementation-defined Anteil.

---

## Arrays

Arrays werden mit:

- Länge,
- Eigenschaften,
- rekursiv serialisierten Werten

repräsentiert.

Die Struktur wird als tiefe Struktur behandelt.

---

## Ordinary Objects

Normale Objekte werden als Objekt mit einer Liste eigener Eigenschaften serialisiert.

Für die Eigenschaften werden die relevanten Enumerable Own Properties verarbeitet.

Die jeweiligen Property-Werte werden rekursiv serialisiert.

---

## Funktionen

Callable Objects können nicht regulär strukturiert serialisiert werden.

Ein entsprechender Versuch führt zu:

```text
DataCloneError
```

---

## Promise und andere nicht serialisierbare interne Zustände

Objekte mit nicht zulässigen internen Zuständen können nicht über Structured Cloning verarbeitet werden.

Dazu gehören insbesondere Objekte, deren interne Slots nicht vom Structured-Clone-Modell unterstützt werden.

---

## Exotische Objekte

Bestimmte exotische Objekte können nicht strukturiert serialisiert werden.

Eine Ausnahme bildet insbesondere das dafür definierte Standardmodell für normale Objekte.

---

## Nicht serialisierbare Plattformobjekte

Ein Plattformobjekt, das nicht als serializable object definiert ist, kann nicht regulär serialisiert werden.

Der Algorithmus löst in diesem Fall:

```text
DataCloneError
```

aus.

---

# StructuredSerialize

## §2.7.4

`StructuredSerialize` ist die allgemeine Serialisierungsoperation ohne Storage-Modus.

Konzeptionell:

```text
StructuredSerialize(value)
        ↓
StructuredSerializeInternal(value, false)
```

Damit ist:

```text
forStorage = false
```

gesetzt.

---

# StructuredSerializeForStorage

## §2.7.5

`StructuredSerializeForStorage` verwendet dieselbe zentrale Serialisierungsinfrastruktur, setzt aber:

```text
forStorage = true
```

Konzeptionell:

```text
StructuredSerializeForStorage(value)
        ↓
StructuredSerializeInternal(value, true)
```

Der Storage-Modus kann dadurch zu anderen Zulässigkeitsregeln führen.

---

## Unterschied zwischen normaler Serialisierung und Storage-Serialisierung

Die beiden Operationen dürfen nicht als vollständig identisch betrachtet werden.

Insbesondere können Plattformobjekte unterschiedliche Regeln anwenden, wenn:

```text
forStorage = true
```

gesetzt ist.

Ein wichtiges Beispiel ist:

```text
SharedArrayBuffer
```

Dieser ist für Storage-Serialisierung nicht zulässig.

---

# StructuredDeserialize

## §2.7.6

`StructuredDeserialize` nimmt eine zuvor erzeugte serialisierte Repräsentation und erstellt daraus einen neuen JavaScript-Wert im angegebenen:

```text
targetRealm
```

---

## Memory Map

Wie bei der Serialisierung kann ein `memory`-Parameter verwendet werden.

Dieser verhindert:

- doppelte Deserialisierung,
- Verlust gemeinsamer Objektidentität,
- Probleme mit zyklischen Strukturen.

---

## Primitive Werte

Primitive serialisierte Werte werden wieder als entsprechende JavaScript-Werte hergestellt.

---

## Wrapper Objects

Die entsprechenden Wrapper Objects werden im Ziel-`Realm` neu erzeugt.

Dies gilt unter anderem für:

- Boolean Objects,
- Number Objects,
- BigInt Objects,
- String Objects.

---

## Date

Ein serialisierter `Date`-Wert wird als neues `Date`-Objekt im Ziel-`Realm` hergestellt.

---

## RegExp

Ein serialisierter RegExp-Zustand wird in ein neues `RegExp`-Objekt des Ziel-`Realms` überführt.

---

## SharedArrayBuffer

Bei der Deserialisierung eines `SharedArrayBuffer` muss das Ziel-`Realm` zum erforderlichen Agent Cluster gehören.

Andernfalls wird:

```text
DataCloneError
```

ausgelöst.

---

## ArrayBuffer

Ein `ArrayBuffer` wird im Ziel-`Realm` mit der serialisierten Datenrepräsentation hergestellt.

Fehler bei der erforderlichen Speicherallokation werden gemäß den definierten Fehlerregeln als `DataCloneError` behandelt.

---

## ArrayBuffer Views

ArrayBuffer Views werden unter Verwendung des deserialisierten zugrunde liegenden Buffers rekonstruiert.

Dabei werden insbesondere berücksichtigt:

- View-Typ,
- Byte Length,
- Byte Offset,
- Array Length.

---

## Map

Eine neue `Map` wird im Ziel-`Realm` erzeugt.

Anschließend werden Schlüssel und Werte rekursiv deserialisiert.

---

## Set

Eine neue `Set` wird erzeugt.

Die Einträge werden rekursiv deserialisiert.

---

## Arrays

Arrays werden mit ihrer serialisierten Länge und den serialisierten Eigenschaften im Ziel-`Realm` neu erzeugt.

---

## Objects

Normale Objekte werden als neue Objekte im Ziel-`Realm` erzeugt.

Ihre serialisierten Eigenschaften werden anschließend rekursiv wiederhergestellt.

---

## Error Objects

Error Objects werden anhand des serialisierten Namens und der zugehörigen Daten rekonstruiert.

Unterstützte Fehlernamen umfassen insbesondere:

- `Error`
- `EvalError`
- `RangeError`
- `ReferenceError`
- `SyntaxError`
- `TypeError`
- `URIError`

---

## Serializable Platform Objects

Für serialisierbare Plattformobjekte wird der serialisierte Interface-Name verwendet.

Wenn die entsprechende Interface im Ziel-`Realm` nicht exponiert ist, wird:

```text
DataCloneError
```

ausgelöst.

Andernfalls wird ein neues Objekt der entsprechenden Interface erzeugt und anschließend dessen Deserialisierungsalgorithmus ausgeführt.

---

# StructuredSerializeWithTransfer

## §2.7.7

`StructuredSerializeWithTransfer` kombiniert:

- Structured Serialization
- Transfer

Die Operation erhält:

```text
value
transferList
```

---

## Transfer Memory

Der Algorithmus verwendet eine `memory`-Map, um die Elemente der Transferliste während der normalen Serialisierung gezielt auszuschließen und separat zu behandeln.

---

## Validierung der Transferliste

Für jedes Element der Transferliste muss geprüft werden, ob es transferierbar ist.

Nicht zulässige Objekte führen zu:

```text
DataCloneError
```

---

## SharedArrayBuffer in der Transferliste

Ein `SharedArrayBuffer` darf nicht über die Transferliste übertragen werden.

Ein entsprechender Versuch führt zu:

```text
DataCloneError
```

---

## Doppelte Transferobjekte

Ein Transferobjekt darf nicht mehrfach in derselben Transferliste verarbeitet werden.

Wird dasselbe Objekt mehrfach angegeben, führt dies zu:

```text
DataCloneError
```

---

## Fehler vor Seiteneffekten

Ein wichtiger Bestandteil des Modells ist, dass zunächst die erforderliche Serialisierung erfolgreich durchgeführt werden muss.

Das eigentliche Übertragen erfolgt erst anschließend.

Dadurch wird verhindert, dass ein Transferobjekt bereits detached wird, obwohl die Gesamtoperation später wegen eines anderen Serialisierungsfehlers scheitert.

---

## ArrayBuffer Transfer

Für `ArrayBuffer` wird die zugrunde liegende Datenrepräsentation in einen Transfer-Datenhalter übernommen.

Anschließend wird der ursprüngliche Buffer detached.

Bei Resizable ArrayBuffers wird zusätzlich die maximale Byte-Länge berücksichtigt.

---

## Plattformobjekt Transfer

Für ein transferierbares Plattformobjekt werden die definierten:

- transfer steps

aufgerufen.

Danach wird der ursprüngliche Zustand als detached markiert.

---

## Ergebnis

`StructuredSerializeWithTransfer` liefert konzeptionell ein Ergebnis mit:

```text
[[Serialized]]
[[TransferDataHolders]]
```

---

# StructuredDeserializeWithTransfer

## §2.7.8

`StructuredDeserializeWithTransfer` stellt die Gegenoperation zu `StructuredSerializeWithTransfer` dar.

Sie erhält:

```text
serializeWithTransferResult
targetRealm
```

---

## Transferred Values

Zunächst werden die übertragenen Datenhalter verarbeitet.

Für jeden Datenhalter wird ein entsprechender Wert im Ziel-`Realm` erzeugt.

---

## ArrayBuffer Transfer

Bei einem übertragenen `ArrayBuffer` kann die vorhandene Datenrepräsentation im Zielkontext als neuer `ArrayBuffer` verwendet werden.

Dabei ist nicht zwingend eine erneute vollständige Speicherkopie erforderlich.

---

## ResizableArrayBuffer Transfer

Bei einem Resizable ArrayBuffer werden zusätzlich:

- aktuelle Byte-Länge,
- maximale Byte-Länge

berücksichtigt.

---

## Transferable Platform Objects

Bei einem transferierten Plattformobjekt wird:

1. der Interface-Name bestimmt,
2. geprüft, ob die Interface im Ziel-`Realm` exponiert ist,
3. eine neue Instanz erzeugt,
4. der Transfer-Receiving-Algorithmus ausgeführt.

---

## Ergebnis

Die Operation liefert konzeptionell:

```text
[[Deserialized]]
[[TransferredValues]]
```

Damit können sowohl:

- der deserialisierte Hauptwert,
- als auch die übertragenen Werte

zur weiteren Verarbeitung verfügbar gemacht werden.

---

# Performing Serialization and Transferring from Other Specifications

## §2.7.9

Andere Web-Spezifikationen dürfen die in §2.7 definierten Structured-Clone-Algorithmen verwenden.

Die HTML-Spezifikation definiert hierfür keine neue Serialisierungsvariante für jede einzelne API.

Stattdessen stellt sie eine gemeinsame Infrastruktur bereit.

---

## Verwendung von `StructuredSerializeWithTransfer`

Diese Operation ist insbesondere geeignet, wenn:

- ein Wert an einen anderen Realm übertragen wird,
- eine Transferliste verwendet wird,
- der Ziel-`Realm` erst später bekannt wird.

Ein wichtiges Beispiel ist:

```js
messagePort.postMessage(value, transferList);
```

wobei die Zielumgebung zum Zeitpunkt der Serialisierung nicht zwingend bereits vollständig bestimmt sein muss.

---

## Verwendung von `StructuredSerialize`

`StructuredSerialize` eignet sich für die Erzeugung einer Realm-unabhängigen strukturierten Repräsentation ohne Transfer.

---

## Verwendung von `StructuredSerializeForStorage`

`StructuredSerializeForStorage` ist für Situationen vorgesehen, in denen eine strukturierte Repräsentation gespeichert und später wiederhergestellt werden soll.

Ein wichtiges HTML-Beispiel ist die History-Infrastruktur.

`history.pushState()` und `history.replaceState()` verwenden die Storage-Variante für den vom Autor gelieferten State.

---

## Verwendung von `StructuredDeserialize`

`StructuredDeserialize` kann anschließend verwendet werden, um aus einem gespeicherten serialisierten Zustand wieder einen neuen JavaScript-Wert zu erzeugen.

---

## Broadcast Channel

Die Broadcast-Channel-Infrastruktur verwendet Structured Serialization und Deserialization.

Da ein Wert an mehrere Empfänger verteilt werden kann, ist ein einmaliger Transfer nicht das passende Modell.

Stattdessen erhalten die Empfänger strukturierte Kopien.

---

## `postMessage()`

`window.postMessage()` verwendet Structured Serialization mit Transfermöglichkeiten.

Die Serialisierung erfolgt im synchronen Teil des API-Aufrufs.

Dadurch gelten die für die Vorbereitung der Script-Ausführung relevanten Regeln entsprechend.

---

# Structured Cloning API

## §2.7.10

HTML stellt die globale API:

```js
structuredClone(value)
```

bereit.

Zusätzlich kann eine Transferliste übergeben werden:

```js
structuredClone(value, {
  transfer: [...]
});
```

---

## Grundfunktion

`structuredClone()` nimmt einen Wert entgegen und gibt eine strukturierte tiefe Kopie zurück.

Konzeptionell:

```text
value
  ↓
StructuredSerializeWithTransfer
  ↓
StructuredDeserializeWithTransfer
  ↓
new value
```

---

## Transfer über `structuredClone()`

Transferable Objects können über die Option:

```js
{
  transfer: [...]
}
```

übertragen werden.

Beispiel:

```js
const buffer = new ArrayBuffer(1024);

const clone = structuredClone(buffer, {
  transfer: [buffer]
});
```

Nach dem Transfer ist der ursprüngliche Buffer detached und kann nicht mehr wie zuvor verwendet werden.

---

## Fehlerverhalten

Wenn ein Teil des Eingabewertes nicht serialisierbar ist oder die Transferliste einen unzulässigen Zustand enthält, wird:

```text
DataCloneError
```

ausgelöst.

---

## Keine Referenzkopie

Bei:

```js
const copy = structuredClone(source);
```

wird nicht einfach:

```js
const copy = source;
```

ausgeführt.

Die API erzeugt eine strukturelle Kopie nach dem normativen Structured-Clone-Modell.

---

# Detailprüfung: Unterstützte Wertklassen

| Wert / Objekt | Structured Clone | Besonderheit |
|---|---|---|
| `undefined` | ja | primitiver Wert |
| `null` | ja | primitiver Wert |
| Boolean | ja | primitiver Wert |
| Number | ja | primitiver Wert |
| BigInt | ja | primitiver Wert |
| String | ja | primitiver Wert |
| Symbol | nein | `DataCloneError` |
| Boolean Object | ja | interner Zustand |
| Number Object | ja | interner Zustand |
| BigInt Object | ja | interner Zustand |
| String Object | ja | interner Zustand |
| `Date` | ja | `[[DateValue]]` |
| `RegExp` | ja | Matcher / Source / Flags |
| `ArrayBuffer` | ja | Datenblock |
| Resizable ArrayBuffer | ja | inklusive Maximalgröße |
| `SharedArrayBuffer` | eingeschränkt | Agent-Cluster-/Isolation-Regeln |
| Typed Array | ja | Buffer + View-Daten |
| `DataView` | ja | Buffer + View-Daten |
| `Map` | ja | rekursive Schlüssel/Werte |
| `Set` | ja | rekursive Einträge |
| Array | ja | rekursive Eigenschaften |
| gewöhnliches Object | ja | rekursive Own Properties |
| Error | ja | definierte Error-Daten |
| serialisierbares Plattformobjekt | ja | `[Serializable]` |
| nicht serialisierbares Plattformobjekt | nein | `DataCloneError` |
| Callable Object | nein | `DataCloneError` |
| bestimmte exotische Objekte | nein | `DataCloneError` |

Die konkrete Zulässigkeit richtet sich immer nach den aktuellen normativen Algorithmen.

---

# Detailprüfung: Transfer

| Objekt / Zustand | Transferierbar | Ergebnis |
|---|---|---|
| `ArrayBuffer` | ja | Daten werden übertragen, Quelle detached |
| Resizable `ArrayBuffer` | ja | Daten + Größeninformationen werden übertragen |
| `SharedArrayBuffer` | nein | darf nicht transferiert werden |
| bereits detached `ArrayBuffer` | nein | `DataCloneError` |
| bereits detached transferable object | nein | `DataCloneError` |
| `[Transferable]` Plattformobjekt | ja | Transfer Steps |
| nicht transferierbares Objekt | nein | `DataCloneError` |

---

# Attribute

§2.7 definiert keine eigene Gruppe von HTML-Content-Attributes.

Die Feature-Familie ist primär API- und Processing-orientiert.

Es existieren jedoch API-Parameter und Web-IDL-Erweiterungen, die fachlich als Attribute beziehungsweise Optionen auftreten.

## `[Serializable]`

Web-IDL Extended Attribute für serialisierbare Plattformobjekte.

---

## `[Transferable]`

Web-IDL Extended Attribute für transferierbare Plattformobjekte.

---

## `transfer`

Die `structuredClone()`-API besitzt eine Option:

```js
{
  transfer: [...]
}
```

Diese Option definiert die Transferliste für den API-Aufruf.

---

# Content Categories

Content Categories sind für §2.7 nicht das zentrale Informationsmodell.

Structured Cloning besitzt keine eigene Content Category.

Die folgenden Begriffe sind deshalb nicht als Content Categories zu behandeln:

- Serializable Object
- Transferable Object
- Structured Clone
- Serialized Record
- Transfer Data Holder

Sie sind Verarbeitungs- beziehungsweise Datenmodellbegriffe.

---

# Context

§2.7 besitzt keinen HTML-Element-Context im Sinne der Elementdefinitionen.

Die relevanten Kontexte sind vielmehr:

- JavaScript Realm,
- target Realm,
- Agent,
- Agent Cluster,
- global object,
- Storage-Kontext,
- API-Aufrufkontext.

Diese Begriffe dürfen nicht mit den HTML-Element-Contexts aus `18-contexts.md` verwechselt werden.

---

# Content Model

Structured Cloning besitzt kein HTML Content Model.

Insbesondere:

```text
Structured Clone
≠
HTML Content Model
```

Das Content Model eines Elements bleibt Bestandteil seiner jeweiligen HTML-Elementdefinition.

Structured Cloning beschreibt dagegen die Verarbeitung von JavaScript-Werten.

---

# Processing Models

## Gesamtmodell

Das Gesamtmodell kann vereinfacht dargestellt werden als:

```text
JavaScript Value
      │
      ▼
Classification
      │
      ├── primitive
      ├── built-in object
      ├── serializable platform object
      └── unsupported object
      │
      ▼
StructuredSerialize
      │
      ▼
Realm-independent Serialized Record
      │
      ├── normal clone
      │
      └── transfer data
      │
      ▼
StructuredDeserialize
      │
      ▼
Value in Target Realm
```

---

## Deep Serialization

Bei verschachtelten Objekten werden die relevanten Unterwerte rekursiv verarbeitet.

Dadurch entsteht ein Objektgraph statt lediglich einer flachen Property-Kopie.

---

## Zyklische Strukturen

Die `memory`-Map verhindert unendliche Rekursion.

Sie erhält außerdem die notwendige Graphstruktur.

Beispiel:

```js
const value = {};
value.self = value;
```

Eine korrekte Structured-Clone-Verarbeitung muss diese zyklische Beziehung berücksichtigen.

---

## Gemeinsame Referenzen

Wenn mehrere Eigenschaften auf dasselbe Objekt zeigen, muss der Clone-Graph diese Identitätsbeziehung innerhalb des Clones entsprechend erhalten.

Beispiel:

```js
const shared = {};
const value = {
  first: shared,
  second: shared
};
```

Die beiden Referenzen sollen innerhalb des erzeugten Clones weiterhin auf dasselbe entsprechende Clone-Objekt verweisen.

---

## Transfer Processing

Transfer Processing unterscheidet sich von normalem Cloning:

```text
Clone:
source object
    ↓
new object
```

gegen:

```text
Transfer:
source resource
    ↓
target resource
source becomes detached
```

---

## Fehler vor Transfer

Die Spezifikation stellt sicher, dass notwendige Fehlerprüfungen vor dem endgültigen Transfer mit Seiteneffekten durchgeführt werden.

Dadurch wird verhindert, dass eine teilweise ausgeführte Transferoperation bei einem späteren Fehler einen inkonsistenten Zustand hinterlässt.

---

# DOM Interfaces / APIs

## `structuredClone()`

Die zentrale API ist:

```js
structuredClone(value, options)
```

Sie liefert eine strukturierte Kopie des Eingabewertes.

---

## `DataCloneError`

Fehlerhafte Structured-Clone-Operationen verwenden die `DOMException`-Fehlersemantik mit:

```text
DataCloneError
```

---

## Beziehungen zu anderen APIs

Die Structured-Clone-Infrastruktur wird von mehreren Web-APIs verwendet.

Beispiele:

- `window.postMessage()`
- `MessagePort.postMessage()`
- Broadcast Channel
- History State
- `structuredClone()`

Die jeweiligen APIs besitzen darüber hinaus eigene Regeln.

---

## `history.pushState()`

History State verwendet:

```text
StructuredSerializeForStorage
```

für den vom Autor bereitgestellten State.

Der gespeicherte Zustand wird später über Structured Deserialization wieder in einen JavaScript-Wert überführt.

---

## `history.replaceState()`

Für `history.replaceState()` gelten entsprechende Structured-Serialization-Regeln für den State.

---

## `MessagePort.postMessage()`

`MessagePort.postMessage()` kann Structured Serialization mit Transfer verwenden.

Dies ermöglicht unter anderem das Übertragen von transferierbaren Ressourcen.

---

## Broadcast Channel

Broadcast Channel verwendet Structured Serialization für Werte, die an mehrere Empfänger verteilt werden.

Transfer ist bei einer Multi-Destination-Verteilung nicht das entsprechende allgemeine Modell.

---

# Accessibility

§2.7 definiert keine eigenständige Accessibility-Semantik.

Structured Cloning:

- definiert keine ARIA-Rolle,
- definiert keinen Accessibility State,
- definiert keine Accessibility Property,
- definiert keine semantische HTML-Darstellung.

Accessibility-relevante Auswirkungen entstehen ausschließlich mittelbar über die APIs und Objekte, die Structured Cloning verwenden.

Daher darf aus der Existenz von Structured Cloning keine eigene Accessibility-Anforderung abgeleitet werden.

---

# Sanitization

Structured Cloning ist kein Sanitization-Mechanismus.

Insbesondere bedeutet:

```text
structuredClone(value)
```

nicht automatisch:

```text
sanitized(value)
```

Structured Cloning bestimmt, welche Werte und Objektzustände kopiert oder übertragen werden können.

Sanitization bestimmt dagegen, ob Inhalte beziehungsweise Strukturen sicher bereinigt oder zugelassen werden.

Diese Ebenen sind getrennt.

---

# Konformitätsregeln

## `[Serializable]`

Eine Interface darf nur entsprechend den Web-IDL- und HTML-Regeln als serialisierbar gekennzeichnet werden.

Die zugehörigen Serialization Steps und Deserialization Steps müssen die normativen Anforderungen erfüllen.

---

## `[Transferable]`

Eine Interface darf nur entsprechend der dafür definierten Regeln als transferable gekennzeichnet werden.

Die erforderlichen Transferalgorithmen müssen definiert werden.

---

## Transferlisten

Autoren dürfen nur tatsächlich transferierbare Werte in einer Transferliste verwenden.

Ein nicht transferierbarer Wert führt zu einem Fehler.

---

## Duplicate Transfer Entries

Dasselbe Transferobjekt darf nicht mehrfach in derselben Transferliste verarbeitet werden.

---

## Detached Values

Bereits detached Werte können nicht beliebig erneut transferiert werden.

---

## Storage Serialization

Storage Serialization muss mit:

```text
forStorage = true
```

behandelt werden.

Die besonderen Storage-Regeln dürfen nicht durch die normale Structured-Clone-Semantik ersetzt werden.

---

## Ziel-`Realm`

Bei der Deserialisierung muss das Zielobjekt im korrekten Ziel-`Realm` erzeugt werden.

Ein serialisiertes Objekt wird nicht als Objekt des ursprünglichen `Realm` wiederverwendet.

---

# Normative Sonderregeln

## Structured Clone ist Realm-unabhängig

Die serialisierte Repräsentation muss so modelliert sein, dass sie unabhängig von einem konkreten JavaScript-`Realm` verarbeitet werden kann.

---

## Transfer ist nicht Copy

Transfer und Copy sind zwei unterschiedliche Verarbeitungspfade.

Ein Transfer kann die Nutzung des Quellobjekts verhindern.

---

## Transfer ist irreversibel

Nach einem erfolgreichen Transfer kann das ursprüngliche transferable object nicht einfach wieder in den vorherigen Zustand zurückversetzt werden.

---

## Transfer ist nicht idempotent

Ein erfolgreicher Transfer kann nicht beliebig erneut mit demselben ursprünglichen Objekt ausgeführt werden.

---

## SharedArrayBuffer besitzt Sonderregeln

`SharedArrayBuffer` besitzt besondere Regeln bezüglich:

- Cross-Origin Isolation,
- Agent Clusters,
- Storage,
- Transfer.

Diese Regeln dürfen nicht mit den Regeln gewöhnlicher `ArrayBuffer`-Objekte gleichgesetzt werden.

---

## Serialization kann User Code auslösen

Bei der abschließenden Verarbeitung gewöhnlicher Objekte können autorendefinierte Getter beziehungsweise Accessors ausgeführt werden.

Daher können Serialisierungsoperationen nicht pauschal als vollständig nebenwirkungsfrei betrachtet werden.

Spezifikationen, die solche Operationen außerhalb eines unmittelbaren synchronen Author-Code-Aufrufs verwenden, müssen die Anforderungen zur Vorbereitung der Script-Ausführung berücksichtigen.

---

## `structuredClone()` ist kein JSON-Parser

Die API:

```js
structuredClone()
```

verwendet nicht:

```js
JSON.stringify()
JSON.parse()
```

und besitzt daher ein anderes Datenmodell.

---

# Querverweise

## Structured Cloning ↔ DOM Interfaces / APIs

Die Structured-Clone-Infrastruktur wird von zahlreichen APIs verwendet.

Sie ist deshalb mit:

`docs/html/19-dom-interfaces-and-apis.md`

verbunden.

Die vollständige Definition des jeweiligen API-Mitglieds bleibt jedoch in der zuständigen Featurefamilie.

---

## Structured Cloning ↔ Scripting

`docs/html/12-scripting.md` behandelt die HTML-Scripting-Familie.

Structured Cloning ist davon zu unterscheiden.

Scripting beschreibt unter anderem:

- Script Processing,
- Script Execution,
- Module,
- Template-/Slot-/Canvas-bezogene APIs.

Structured Cloning beschreibt dagegen die Übertragung und Serialisierung von JavaScript-Werten.

---

## Structured Cloning ↔ Common DOM Interfaces

`docs/html/28-common-dom-interfaces.md` behandelt:

- Reflection,
- IDL,
- Collections,
- HTML-spezifische DOM-Infrastruktur.

Structured Cloning verwendet ebenfalls Web-IDL- und DOM-nahe Konzepte, ist aber ein eigenständiges Serialisierungsmodell.

---

## Structured Cloning ↔ Fetching Resources

Structured Cloning ist nicht Bestandteil des Fetch-Modells.

Ein Fetch kann API-Daten erzeugen oder übertragen, aber:

```text
Fetching
≠
Structured Cloning
```

---

## Structured Cloning ↔ Custom Elements

Custom Elements können DOM-/Plattformobjekte bereitstellen.

Eine Custom-Element-Interface ist jedoch nicht automatisch serialisierbar.

Serialisierbarkeit muss nach den dafür definierten Regeln gegeben sein.

---

## Structured Cloning ↔ Web Workers

Worker-Kommunikation verwendet Structured-Clone-Infrastruktur für die Übertragung von Nachrichtenwerten.

Worker selbst sind jedoch nicht Teil der §2.7-Definition.

---

## Structured Cloning ↔ History

History State verwendet die Storage-Variante:

```text
StructuredSerializeForStorage
```

und entsprechende Deserialisierung.

---

## Structured Cloning ↔ Broadcast Channel

Broadcast Channel verwendet Structured Serialization und Deserialization für die Verteilung von Werten an mehrere Empfänger.

---

## Structured Cloning ↔ Web IDL

Web IDL definiert unter anderem:

```text
[Serializable]
[Transferable]
```

als Extended Attributes.

HTML definiert deren konkrete Verwendung innerhalb der Structured-Clone-Infrastruktur.

---

## Structured Cloning ↔ ECMAScript

Das Structured-Clone-Modell arbeitet mit JavaScript-Sprachkonzepten wie:

- Realm,
- internal slots,
- Array,
- Map,
- Set,
- Date,
- RegExp,
- Object,
- callable objects.

Die vollständige Definition dieser JavaScript-Sprachobjekte stammt jedoch aus ECMAScript und nicht aus HTML.

---

# Status / V1

## WHATWG-Status

| Feature | WHATWG-Status |
|---|---|
| Safe passing of structured data | im HTML Living Standard definiert |
| Serializable objects | normative HTML-Infrastruktur |
| `[Serializable]` | normative Web-IDL-/HTML-Integration |
| Serialization Steps | normative Processing Rules |
| Deserialization Steps | normative Processing Rules |
| Transferable objects | normative HTML-Infrastruktur |
| `[Transferable]` | normative Web-IDL-/HTML-Integration |
| Transfer Steps | normative Processing Rules |
| Transfer-Receiving Steps | normative Processing Rules |
| `StructuredSerializeInternal` | normative abstract operation |
| `StructuredSerialize` | normative abstract operation |
| `StructuredSerializeForStorage` | normative abstract operation |
| `StructuredDeserialize` | normative abstract operation |
| `StructuredSerializeWithTransfer` | normative abstract operation |
| `StructuredDeserializeWithTransfer` | normative abstract operation |
| Structured Cloning API | normative API |
| `structuredClone()` | normative API |
| `DataCloneError` | normative Error-Verarbeitung |

---

## Obsolete / Deprecated

§2.7 ist im geprüften WHATWG-Stand nicht als obsolete Feature-Familie definiert.

Einzelne von Structured Cloning verwendete JavaScript- oder Web-API-Konzepte können unabhängig davon historische oder spezielle Regeln besitzen.

Dies darf nicht auf §2.7 als Ganzes übertragen werden.

---

## Browser-Kompatibilität

Browser-Kompatibilität ist kein WHATWG-Status.

Daher wird sie in dieser Datei nicht als Statussystem verwendet.

---

## V1

Die V1-Einstufung ist eine ZE-WebLab-Projektentscheidung.

Sie darf nicht mit:

- WHATWG-Status,
- Browser-Support,
- API-Verfügbarkeit

gleichgesetzt werden.

Für die zweite Rechercheebene wird §2.7 als eigenständige normative Feature-Familie geführt.

---

# Offene Punkte

Für den abgegrenzten §2.7-Bereich bestehen nach der Prüfung des aktuellen WHATWG-Standes keine offenen Punkte hinsichtlich der Identifikation der relevanten Unterabschnitte.

Bewusst außerhalb dieser Datei bleiben:

1. Die vollständige ECMAScript-Spezifikation.
2. Die vollständige Web-IDL-Spezifikation.
3. Die vollständige DOM-Spezifikation.
4. Die vollständige Worker-Spezifikation.
5. Die vollständige Message-Port-/Messaging-Spezifikation.
6. Die vollständige Storage-Spezifikation.
7. Die vollständige History-Spezifikation außerhalb ihrer Structured-Clone-Beziehung.
8. Browser-spezifische Implementierungsdetails.
9. Browser-Kompatibilitätsdaten.

Diese Punkte stellen keine Lücken in der Recherche von WHATWG §2.7 dar.

Sie sind fachlich eigenständige Spezifikationsbereiche.

---

# Prüfstatus

| Prüfbereich | Status |
|---|---|
| §2.7 Safe passing of structured data | geprüft |
| §2.7.1 Serializable objects | geprüft |
| `[Serializable]` | geprüft |
| Serialization Steps | geprüft |
| Deserialization Steps | geprüft |
| §2.7.2 Transferable objects | geprüft |
| `[Transferable]` | geprüft |
| Transfer Steps | geprüft |
| Transfer-Receiving Steps | geprüft |
| `[[Detached]]` | geprüft |
| §2.7.3 StructuredSerializeInternal | geprüft |
| Memory Map | geprüft |
| Primitive Values | geprüft |
| Symbol Handling | geprüft |
| Date | geprüft |
| RegExp | geprüft |
| ArrayBuffer | geprüft |
| SharedArrayBuffer | geprüft |
| Resizable ArrayBuffer | geprüft |
| ArrayBuffer Views | geprüft |
| Map | geprüft |
| Set | geprüft |
| Error Objects | geprüft |
| Arrays | geprüft |
| Ordinary Objects | geprüft |
| Serializable Platform Objects | geprüft |
| Non-serializable Objects | geprüft |
| §2.7.4 StructuredSerialize | geprüft |
| §2.7.5 StructuredSerializeForStorage | geprüft |
| §2.7.6 StructuredDeserialize | geprüft |
| Target Realm | geprüft |
| Deserialization Memory | geprüft |
| §2.7.7 StructuredSerializeWithTransfer | geprüft |
| Transfer List | geprüft |
| Transfer Validation | geprüft |
| ArrayBuffer Transfer | geprüft |
| Platform Object Transfer | geprüft |
| §2.7.8 StructuredDeserializeWithTransfer | geprüft |
| Transferred Values | geprüft |
| Transfer Receiving | geprüft |
| §2.7.9 Cross-specification usage | geprüft |
| History State | geprüft |
| MessagePort | geprüft |
| Broadcast Channel | geprüft |
| Script Preparation Relationship | geprüft |
| §2.7.10 Structured cloning API | geprüft |
| `structuredClone()` | geprüft |
| `transfer` option | geprüft |
| `DataCloneError` | geprüft |
| Attribute-Ebene | geprüft |
| Content Categories | geprüft / nicht relevant |
| Context | geprüft / abgegrenzt |
| Content Model | geprüft / nicht relevant |
| Processing Models | geprüft |
| DOM/API-Beziehungen | geprüft |
| Accessibility | geprüft / keine eigenständige Semantik |
| Sanitization | geprüft / kein Sanitization-Modell |
| Konformitätsregeln | geprüft |
| Querverweise | geprüft |
| WHATWG-Status | geprüft |
| Browser-Support-Trennung | geprüft |
| Offene Punkte | geprüft |

---

# Quellen / Referenzen

## Normative Primärquelle

WHATWG, **HTML Living Standard**, §2.7:

- §2.7 Safe passing of structured data
- §2.7.1 Serializable objects
- §2.7.2 Transferable objects
- §2.7.3 StructuredSerializeInternal
- §2.7.4 StructuredSerialize
- §2.7.5 StructuredSerializeForStorage
- §2.7.6 StructuredDeserialize
- §2.7.7 StructuredSerializeWithTransfer
- §2.7.8 StructuredDeserializeWithTransfer
- §2.7.9 Performing serialization and transferring from other specifications
- §2.7.10 Structured cloning API

## Weitere normative Spezifikationsbeziehungen

- ECMAScript
- WHATWG Web IDL
- WHATWG DOM
- WHATWG Infra
- WHATWG Storage
- WHATWG URL
- WHATWG Fetch
- WHATWG HTML Scripting
- WHATWG Web Workers
- HTML History APIs
- Messaging APIs

Diese Spezifikationen werden nur insoweit berücksichtigt, wie sie für die normative Einordnung der HTML-§2.7-Infrastruktur erforderlich sind.

---

## ZE-WebLab-Projektquellen

Zur Abgrenzung und Bestandsprüfung wurden insbesondere berücksichtigt:

- `docs/html/12-scripting.md`
- `docs/html/19-dom-interfaces-and-apis.md`
- `docs/html/27-common-microsyntaxes.md`
- `docs/html/28-common-dom-interfaces.md`

Diese Dateien sind Projekt-/Bestandsquellen und ersetzen nicht die normative WHATWG-Quelle.

---

## Quellenabgrenzung

Die normative Definition der Structured-Clone-Infrastruktur stammt aus dem WHATWG HTML Living Standard.

Die vorhandenen ZE-WebLab-Dateien dienen ausschließlich dazu festzustellen:

- welche verwandten Konzepte bereits dokumentiert sind,
- welche Informationen lediglich element- oder API-bezogen vorhanden sind,
- welche Abgrenzung für die zweite Rechercheebene erforderlich ist.

Browser-Support wird nicht zur Bestimmung des WHATWG-Status verwendet.

---

# Fachliche Zusammenfassung

§2.7 „Safe passing of structured data“ bildet eine eigenständige Infrastruktur-Familie des HTML Living Standard.

Der Bereich definiert nicht lediglich die API `structuredClone()`, sondern ein vollständiges normatives Modell für:

```text
Serializable Objects
        │
        ▼
Structured Serialization
        │
        ├── normal serialization
        │
        └── storage serialization
        │
        ▼
Serialized Representation
        │
        ├── normal deserialization
        │
        └── transfer-aware deserialization
        │
        ▼
Target Realm
```

Für Transferfälle erweitert HTML dieses Modell um:

```text
Transferable Objects
        │
        ▼
Transfer Steps
        │
        ▼
Transfer Data Holder
        │
        ▼
Transfer-Receiving Steps
        │
        ▼
Transferred Value
```

Damit ist §2.7 fachlich eindeutig von:

- HTML-Elementen,
- Content Categories,
- Content Models,
- Global Attributes,
- Link Types,
- Parsing,
- Fetching,
- Reflection

zu unterscheiden.

Die Feature-Familie gehört in die zweite Rechercheebene, weil ihre Regeln zahlreiche HTML- und Web-APIs übergreifend unterstützen und nicht auf ein einzelnes HTML-Element beschränkt sind.