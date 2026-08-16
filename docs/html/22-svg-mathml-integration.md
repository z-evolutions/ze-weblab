# ZE-WebLab – HTML-Referenz: SVG-/MathML-Integration

## Arbeitsstand / Quellenstand

Rechercheebene: 2 – übergreifende HTML-Konzepte und Feature-Familien

Feature-Typ:

- Integration Feature
- Parsing Concept
- Normative Concept
- Namespace-/DOM-Konzept

Zielpfad:

`docs/html/22-svg-mathml-integration.md`

Normative Primärquelle:

WHATWG HTML Living Standard

Geprüfter WHATWG-Stand:

Living Standard, zuletzt aktualisiert am 11. August 2026.

Projekt-/Bestandsquelle:

ZE-WebLab GitHub-Repository, Branch `main`.

Repository-Abgrenzung:

- `01-document-element.md` bis `12-scripting.md` bilden die erste Rechercheebene.
- `13-global-attributes.md` behandelt Global Attributes.
- `14-content-categories.md` behandelt Content Categories.
- `15-content-models.md` behandelt Content Models.
- `16-link-types.md` behandelt Link Types.
- `17-custom-elements.md` und `20-custom-elements.md` behandeln Custom-Elements-Themen im bestehenden Projektbestand.
- `18-contexts.md` behandelt Contexts.
- `19-dom-interfaces-and-apis.md` behandelt DOM Interfaces und APIs.
- `21-parsing.md` behandelt HTML Parsing als eigenständiges Processing Model.

Diese Datei behandelt deshalb die HTML/SVG/MathML-Integration als eigene übergreifende Feature-Familie.

Wichtig:

SVG- und MathML-Elemente werden in dieser Datei nicht als native HTML-Elemente gezählt.

Die Datei dokumentiert die Regeln, durch die Inhalte aus anderen XML-Vokabularen innerhalb von HTML-Dokumenten verarbeitet, in Namespaces eingeordnet und mit HTML-Inhalten verbunden werden.

## Einordnung

HTML-Dokumente können neben Elementen im HTML-Namespace auch Elemente aus anderen Namespaces enthalten.

Für die HTML/SVG/MathML-Integration sind insbesondere relevant:

- HTML Namespace
- SVG Namespace
- MathML Namespace
- Foreign Content
- HTML Integration Points
- MathML Text Integration Points
- Namespace-bezogene Elementerzeugung
- Namespace-bezogene Attributverarbeitung
- SVG-Attributanpassung
- MathML-Attributanpassung
- Foreign-Attribute-Anpassung
- Übergänge zwischen HTML- und Foreign-Content-Verarbeitung
- Parsing von `svg`
- Parsing von `math`
- Einbettung von HTML-Inhalten innerhalb bestimmter SVG-/MathML-Kontexte
- DOM-Verhalten der erzeugten Nodes
- Fragment Parsing
- Serialisierung

Diese Konzepte sind keine zusätzlichen nativen HTML-Elemente.

Insbesondere gilt:

- `svg` ist ein HTML-Parsing-Einstiegspunkt für den SVG-Namespace.
- `math` ist ein HTML-Parsing-Einstiegspunkt für den MathML-Namespace.
- SVG-Elemente innerhalb dieses Namespace sind SVG-Elemente.
- MathML-Elemente innerhalb dieses Namespace sind MathML-Elemente.
- Ein Elementname allein bestimmt nicht immer den Namespace.
- Für Parsing und DOM ist die Kombination aus Namespace und Local Name entscheidend.

## WHATWG-Struktur

Die Integrationsregeln sind nicht in einem einzigen ausschließlich dafür vorgesehenen Kapitel konzentriert.

Die wesentlichen normativen Regeln verteilen sich insbesondere auf:

- §3.2.5 Content models
- §4 The elements of HTML
- §8 Web application APIs, soweit DOM-/Verarbeitungsbeziehungen betroffen sind
- §13 The HTML syntax
- §13.2 Parsing HTML documents
- §13.2.6 Tree construction
- §13.2.6.5 The rules for parsing tokens in foreign content
- Regeln zur Erzeugung von Elementen und Attributen
- Regeln zur HTML-Fragmentverarbeitung
- Regeln zur HTML-Serialisierung

Für die eigentliche Integration sind insbesondere die Parsing-Regeln zu folgenden Konzepten relevant:

- MathML text integration point
- HTML integration point
- foreign element
- adjusted current node
- adjusted insertion location
- MathML namespace
- SVG namespace
- HTML namespace
- adjustment of SVG attributes
- adjustment of MathML attributes
- adjustment of foreign attributes

## Begriffsdefinitionen

### HTML Namespace

Der HTML-Namespace ist der Namespace, in dem native HTML-Elemente liegen.

Die WHATWG-Spezifikation verwendet für HTML-Elemente grundsätzlich den HTML-Namespace, sofern kein anderer Namespace ausdrücklich angegeben wird.

Ein Element mit einem bekannten HTML-Local-Name ist deshalb nicht allein aufgrund seines Local Names als HTML-Element zu klassifizieren.

Der Namespace ist Bestandteil der DOM-Identität des Elements.

### SVG Namespace

Der SVG-Namespace ist der Namespace für SVG-Elemente.

Innerhalb eines HTML-Dokuments können SVG-Inhalte über die HTML-Parsing-Regeln erzeugt werden.

Das HTML-Parsing-Modell verwendet hierfür den SVG-Namespace.

### MathML Namespace

Der MathML-Namespace ist der Namespace für MathML-Elemente.

Innerhalb eines HTML-Dokuments können MathML-Inhalte über die HTML-Parsing-Regeln erzeugt werden.

Das HTML-Parsing-Modell verwendet hierfür den MathML-Namespace.

### Foreign Content

Foreign Content bezeichnet im Parsing-Kontext Inhalte, die nicht im HTML-Namespace liegen und daher nach den Foreign-Content-Regeln behandelt werden können.

Für ZE-WebLab sind insbesondere SVG und MathML relevant.

Foreign Content ist kein Content Model und keine Content Category.

Es ist ein Parsing-/Namespace-Konzept.

### HTML Integration Point

Ein HTML Integration Point ist ein definierter Knoten innerhalb von Foreign Content, an dem HTML-Inhalt wieder nach den HTML-Regeln verarbeitet werden kann.

Nach den aktuellen WHATWG-Regeln gehören insbesondere dazu:

- SVG `foreignObject`
- SVG `desc`
- SVG `title`
- bestimmte MathML-`annotation-xml`-Elemente mit passenden `encoding`-Attributwerten

Für MathML `annotation-xml` sind insbesondere die Werte:

- `text/html`
- `application/xhtml+xml`

relevant, wenn sie ASCII-case-insensitiv entsprechend den WHATWG-Regeln vorliegen.

### MathML Text Integration Point

Ein MathML Text Integration Point ist ein definierter MathML-Knoten, an dem bestimmte HTML-Parsing-Regeln für nachfolgenden Inhalt relevant werden.

Die aktuelle WHATWG-Definition umfasst insbesondere:

- MathML `mi`
- MathML `mo`
- MathML `mn`
- MathML `ms`
- MathML `mtext`

Der MathML Text Integration Point ist nicht mit einem HTML Integration Point gleichzusetzen.

## Normative Regeln

### Namespace ist Bestandteil der Elementidentität

Für DOM und Parsing ist die Kombination aus Namespace und Local Name relevant.

Beispielsweise sind:

- HTML-`title`
- SVG-`title`

unterschiedliche Elemente, obwohl beide denselben Local Name `title` besitzen.

Entsprechendes gilt für andere Namen, die in mehreren Vokabularen vorkommen können.

Daher darf ZE-WebLab Foreign Elements nicht allein anhand ihres Tag-Namens klassifizieren.

### `svg` als SVG-Einstiegspunkt

Wenn der HTML-Parser im HTML-Inhalt ein Start-Tag mit dem Namen `svg` verarbeitet, wird nach den Foreign-Content-Regeln ein Element im SVG-Namespace erzeugt.

Vor der Erzeugung werden die für SVG relevanten Attributanpassungen durchgeführt.

Zusätzlich werden Foreign Attributes angepasst.

Die resultierende DOM-Struktur enthält daher ein SVG-Element und kein HTML-Element mit dem Local Name `svg`.

### `math` als MathML-Einstiegspunkt

Wenn der HTML-Parser im HTML-Inhalt ein Start-Tag mit dem Namen `math` verarbeitet, wird ein Element im MathML-Namespace erzeugt.

Vor der Erzeugung werden die MathML-Attributanpassungen durchgeführt.

Zusätzlich werden Foreign Attributes angepasst.

Die resultierende DOM-Struktur enthält daher ein MathML-Element und kein HTML-Element mit dem Local Name `math`.

### Foreign-Content-Dispatcher

Bei der Tree Construction entscheidet der Parser anhand des aktuellen Parsing-Kontexts, ob ein Token nach HTML-Regeln oder nach Foreign-Content-Regeln verarbeitet wird.

Dabei spielen insbesondere folgende Bedingungen eine Rolle:

- Namespace des adjusted current node
- MathML Text Integration Point
- HTML Integration Point
- Tokenart
- Tokenname
- aktueller Insertion Mode

Damit ist die Frage

> „Ist dieses Token HTML oder Foreign Content?“

nicht ausschließlich vom Token selbst abhängig.

### Wechsel zurück zu HTML-Parsing

Innerhalb von Foreign Content können bestimmte Token dazu führen, dass der Parser Foreign Content verlässt beziehungsweise die Verarbeitung nach HTML-Regeln wiederaufnimmt.

Die WHATWG-Spezifikation definiert dafür insbesondere:

- bestimmte HTML-Elementnamen
- HTML Integration Points
- MathML Text Integration Points
- besondere MathML-/SVG-Situationen

Dieser Übergang ist Bestandteil des normativen Tree-Construction-Modells.

## Foreign Elements

### Allgemeines

Foreign Elements werden mit einem expliziten Namespace erzeugt.

Der Parser verwendet für SVG und MathML jeweils den entsprechenden Namespace.

Das erzeugte DOM-Element besitzt damit:

- Namespace
- Local Name
- Attribute
- Children
- gegebenenfalls weitere DOM-Eigenschaften

### Namespace-Zuordnung

Für ZE-WebLab gilt als fachliche Dokumentationsregel:

| Vokabular | Namespace | HTML-natives Element? |
|---|---|---|
| HTML | HTML Namespace | Ja |
| SVG | SVG Namespace | Nein |
| MathML | MathML Namespace | Nein |

Die Tabelle beschreibt die Informationsklassifikation und stellt keine zusätzliche WHATWG-Elementliste dar.

## SVG-Integration

### SVG als eingebettetes Vokabular

SVG kann innerhalb von HTML-Dokumenten als Foreign Content vorkommen.

Der HTML-Parser besitzt dafür spezielle Regeln.

Der Einstieg erfolgt insbesondere über:

`<svg>`

Das erzeugte Element befindet sich im SVG-Namespace.

### SVG-Namespace-Vererbung

Nach dem Eintritt in SVG-Content werden nachfolgende Elemente grundsätzlich im SVG-Namespace erzeugt, sofern die Foreign-Content-Regeln keinen Übergang in einen anderen Namespace beziehungsweise HTML-Parsing-Kontext bestimmen.

Damit können verschachtelte SVG-Elemente verarbeitet werden, ohne dass jedes Element im HTML-Quelltext einen expliziten Namespace deklarieren muss.

### SVG Local Names

Das Parsing-Modell enthält für bestimmte SVG-Elementnamen eine Anpassung der Schreibweise.

Dies betrifft insbesondere Namen, deren SVG-Schreibweise Großbuchstaben enthält, während HTML-Tokenisierung die Namen zunächst in einer Form liefert, die angepasst werden muss.

Die aktuelle WHATWG-Tabelle enthält unter anderem:

- `altglyph` → `altGlyph`
- `altglyphdef` → `altGlyphDef`
- `altglyphitem` → `altGlyphItem`
- `animatecolor` → `animateColor`
- `animatemotion` → `animateMotion`
- `animatetransform` → `animateTransform`
- `clippath` → `clipPath`
- `feblend` → `feBlend`
- `fecolormatrix` → `feColorMatrix`
- `fecomponenttransfer` → `feComponentTransfer`
- `fecomposite` → `feComposite`
- `feconvolvematrix` → `feConvolveMatrix`
- `fediffuselighting` → `feDiffuseLighting`
- `fedisplacementmap` → `feDisplacementMap`
- `fedistantlight` → `feDistantLight`
- `fedropshadow` → `feDropShadow`
- `feflood` → `feFlood`
- `fefunca` → `feFuncA`
- `fefuncb` → `feFuncB`
- `fefuncg` → `feFuncG`
- `fefuncr` → `feFuncR`
- `fegaussianblur` → `feGaussianBlur`
- `feimage` → `feImage`
- `femerge` → `feMerge`
- `femergenode` → `feMergeNode`
- `femorphology` → `feMorphology`
- `feoffset` → `feOffset`
- `fepointlight` → `fePointLight`
- `fespecularlighting` → `feSpecularLighting`
- `fespotlight` → `feSpotLight`
- `fetile` → `feTile`
- `feturbulence` → `feTurbulence`
- `foreignobject` → `foreignObject`
- `glyphref` → `glyphRef`
- `lineargradient` → `linearGradient`
- `radialgradient` → `radialGradient`
- `textpath` → `textPath`

Diese Anpassung ist Teil des HTML-Parsing-Modells.

### SVG-Attribute

SVG besitzt Attribute, deren normative Schreibweise nicht vollständig mit der HTML-Tokenisierung übereinstimmt.

Der HTML-Parser besitzt deshalb einen Algorithmus zur Anpassung von SVG-Attributnamen.

Zu den normativ relevanten Beispielen gehören unter anderem:

- `attributename` → `attributeName`
- `attributetype` → `attributeType`
- `basefrequency` → `baseFrequency`
- `baseprofile` → `baseProfile`
- `calcmode` → `calcMode`
- `clippathunits` → `clipPathUnits`
- `diffuseconstant` → `diffuseConstant`
- `edgemode` → `edgeMode`
- `filterunits` → `filterUnits`
- `glyphname` → `glyphName`
- `gradienttransform` → `gradientTransform`
- `gradientunits` → `gradientUnits`
- `kernelmatrix` → `kernelMatrix`
- `kernelunitlength` → `kernelUnitLength`
- `keypoints` → `keyPoints`
- `keysplines` → `keySplines`
- `keytimes` → `keyTimes`
- `lengthadjust` → `lengthAdjust`
- `limitingconeangle` → `limitingConeAngle`
- `markerheight` → `markerHeight`
- `markerunits` → `markerUnits`
- `markerwidth` → `markerWidth`
- `maskcontentunits` → `maskContentUnits`
- `maskunits` → `maskUnits`
- `numoctaves` → `numOctaves`
- `pathlength` → `pathLength`
- `patterncontentunits` → `patternContentUnits`
- `patterntransform` → `patternTransform`
- `patternunits` → `patternUnits`
- `pointsatx` → `pointsAtX`
- `pointsaty` → `pointsAtY`
- `pointsatz` → `pointsAtZ`
- `preservealpha` → `preserveAlpha`
- `preserveaspectratio` → `preserveAspectRatio`
- `primitiveunits` → `primitiveUnits`
- `refx` → `refX`
- `refy` → `refY`
- `repeatcount` → `repeatCount`
- `repeatdur` → `repeatDur`
- `requiredextensions` → `requiredExtensions`
- `requiredfeatures` → `requiredFeatures`
- `specularconstant` → `specularConstant`
- `specularexponent` → `specularExponent`
- `spreadmethod` → `spreadMethod`
- `startoffset` → `startOffset`
- `stddeviation` → `stdDeviation`
- `stitchtiles` → `stitchTiles`
- `surfacescale` → `surfaceScale`
- `systemlanguage` → `systemLanguage`
- `tablevalues` → `tableValues`
- `targetx` → `targetX`
- `targety` → `targetY`
- `textlength` → `textLength`
- `viewbox` → `viewBox`
- `viewtarget` → `viewTarget`
- `zoomandpan` → `zoomAndPan`

Die genaue aktuelle Tabelle der WHATWG-Spezifikation ist für die normative Referenz maßgeblich.

Diese Datei übernimmt nicht die Rolle einer vollständigen SVG-Spezifikation.

### Foreign Attributes in SVG

Bei SVG-Inhalten können Attribute aus anderen Namespaces vorkommen.

Der HTML-Parser besitzt dafür einen eigenen Algorithmus zur Anpassung von Foreign Attributes.

Dazu gehören insbesondere:

- XLink
- XML
- XMLNS

Beispiele:

- `xlink:actuate`
- `xlink:arcrole`
- `xlink:href`
- `xlink:role`
- `xlink:show`
- `xlink:title`
- `xlink:type`
- `xml:lang`
- `xml:space`
- `xmlns`
- `xmlns:xlink`

Der Parser kann diese Attribute als tatsächlich namespace-qualified DOM-Attribute erzeugen.

## MathML-Integration

### MathML als eingebettetes Vokabular

MathML kann innerhalb eines HTML-Dokuments als Foreign Content auftreten.

Der Einstieg erfolgt insbesondere über:

`<math>`

Das erzeugte Element befindet sich im MathML-Namespace.

### MathML-Attribute

Der HTML-Parser besitzt einen eigenen Anpassungsalgorithmus für bestimmte MathML-Attribute.

Ein aktuelles Beispiel ist:

`definitionurl` → `definitionURL`

Die Anpassung ist erforderlich, weil HTML-Tokenisierung und die Schreibweise bestimmter MathML-Attribute unterschiedliche Anforderungen haben.

### MathML Text Integration Points

MathML Text Integration Points sind:

- `mi`
- `mo`
- `mn`
- `ms`
- `mtext`

Sie haben eine besondere Bedeutung für die Tree Construction.

Wenn ein Token an einem solchen Punkt verarbeitet wird, können die HTML-Regeln zur Anwendung kommen, obwohl der umgebende Inhalt im MathML-Namespace liegt.

### MathML `annotation-xml`

`annotation-xml` besitzt besondere Integrationsregeln.

Ein `annotation-xml`-Element kann unter bestimmten Voraussetzungen als HTML Integration Point fungieren.

Relevant sind insbesondere `encoding`-Attributwerte, die ASCII-case-insensitiv mit folgenden Werten übereinstimmen:

- `text/html`
- `application/xhtml+xml`

Damit kann HTML-Inhalt in einen MathML-Kontext eingebettet werden.

### MathML und `svg`

Die WHATWG-Parsingregeln enthalten außerdem eine besondere Regel für ein `svg`-Start-Tag innerhalb eines MathML-`annotation-xml`-Kontexts.

Damit kann der Parser von MathML in SVG wechseln.

Dies ist ein normatives Parsing-/Integration-Verhalten und keine Aussage über eine HTML-Elementhierarchie.

## HTML Integration Points

### SVG Integration Points

Folgende SVG-Elemente sind als HTML Integration Points relevant:

- `foreignObject`
- `desc`
- `title`

Innerhalb dieser Elemente kann HTML-Inhalt entsprechend den WHATWG-Regeln verarbeitet werden.

Beispiel:

    <svg>
      <foreignObject>
        <div>HTML content</div>
      </foreignObject>
    </svg>

Das `foreignObject`-Element selbst befindet sich im SVG-Namespace.

Das darin erzeugte `div`-Element kann dagegen im HTML-Namespace liegen.

### MathML Integration Points

Für MathML ist insbesondere `annotation-xml` relevant.

Ob ein `annotation-xml`-Element als HTML Integration Point fungiert, hängt von seinem `encoding`-Attribut ab.

Die beiden normativ relevanten Werte sind:

- `text/html`
- `application/xhtml+xml`

Die Prüfung erfolgt ASCII-case-insensitiv.

## HTML ↔ SVG ↔ MathML Übergänge

Die HTML/SVG/MathML-Integration kann als Übergangssystem betrachtet werden:

    HTML
      |
      +--> SVG
      |     |
      |     +--> HTML Integration Point
      |
      +--> MathML
            |
            +--> MathML Text Integration Point
            |
            +--> annotation-xml
                  |
                  +--> HTML Integration Point
                  |
                  +--> SVG-Einstiegspunkt

Diese Darstellung ist eine fachliche Modellierung der normativen Parsing-Regeln und kein eigenständiges WHATWG-Diagramm.

## Context

Die Integrationsregeln sind stark kontextabhängig.

Relevant sind insbesondere:

- aktueller Namespace
- adjusted current node
- Stack of Open Elements
- aktueller Insertion Mode
- MathML Text Integration Point
- HTML Integration Point
- Tokenart
- Tokenname
- Attribute des Tokens
- Fragment-Parsing-Kontext

Deshalb kann derselbe Tokenname abhängig vom Parsing-Kontext unterschiedliche DOM-Ergebnisse erzeugen.

Beispiel:

`title`

kann abhängig vom Namespace beziehungsweise Parsing-Kontext unter anderem bedeuten:

- HTML-`title`
- SVG-`title`

Der Local Name allein ist daher kein ausreichendes Klassifikationsmerkmal.

## Content Categories

Die HTML/SVG/MathML-Integration ist von den HTML Content Categories zu unterscheiden.

### Embedded Content

Die WHATWG-Definition von Embedded Content umfasst unter anderem Inhalte aus anderen Vokabularen.

Insbesondere SVG und MathML können in HTML als eingebetteter Inhalt auftreten.

Dabei ist zu unterscheiden zwischen:

- der Content Category eines Elements,
- dem Namespace des Elements,
- dem Parsing-Verhalten,
- dem DOM Interface,
- dem konkreten Vokabular.

### Keine neue Content Category

`SVG Namespace` ist keine Content Category.

`MathML Namespace` ist keine Content Category.

`Foreign Content` ist keine Content Category.

`HTML Integration Point` ist keine Content Category.

Diese Konzepte gehören zur Parsing-/Integrationsdimension.

## Content Model

SVG- und MathML-Inhalte können innerhalb der von HTML definierten Content Models vorkommen, soweit die jeweils geltenden Regeln dies vorsehen.

Die HTML Content Models werden durch die Integration nicht in SVG- oder MathML-Elementlisten umgewandelt.

Wichtig ist insbesondere die Trennung zwischen:

- HTML Content Model
- Foreign Content
- Namespace
- Parsing-Kontext

Ein Element aus einem anderen Namespace darf deshalb nicht allein aufgrund seiner Einbettung als HTML-Element klassifiziert werden.

## Attribute

### HTML-Attribute

HTML-Attribute werden grundsätzlich nach den HTML-Regeln verarbeitet.

### SVG-Attribute

Für SVG existiert eine spezielle Attributanpassung.

### MathML-Attribute

Für MathML existiert eine spezielle Attributanpassung.

### Foreign Attributes

Für bestimmte XML-/XLink-/XMLNS-Attribute existiert eine eigene Namespace-Anpassung.

Damit gibt es drei unterschiedliche relevante Verarbeitungsschritte:

1. HTML-Attributverarbeitung
2. SVG-/MathML-spezifische Namensanpassung
3. Foreign-Attribute-Namespace-Anpassung

Diese Schritte dürfen nicht zu einer einzigen allgemeinen „SVG-Attributregel“ zusammengefasst werden.

## DOM Interfaces / APIs

### Namespace-aware DOM

Die erzeugten Nodes sind normale DOM-Nodes mit Namespace-Information.

Für Elemente sind insbesondere relevant:

- `namespaceURI`
- `localName`
- `prefix`
- `nodeName`

Die tatsächliche DOM-API stammt aus den DOM-Spezifikationen beziehungsweise aus den jeweiligen HTML-/SVG-/MathML-Spezifikationen.

### HTML Interfaces

Native HTML-Elemente können HTML-spezifische Interfaces besitzen.

### SVG Interfaces

SVG-Elemente können SVG-spezifische DOM Interfaces besitzen.

### MathML Interfaces

MathML-Elemente können MathML-spezifische DOM Interfaces besitzen, soweit die einschlägigen Spezifikationen diese definieren.

Diese Datei zählt solche Interfaces nicht als HTML-Elemente.

### Namespace-aware Elementerzeugung

Für DOM-APIs ist zwischen beispielsweise folgenden Operationen zu unterscheiden:

- `createElement()`
- `createElementNS()`

Die Namespace-aware Erzeugung ist für die korrekte Repräsentation von SVG und MathML im DOM relevant.

Die vollständige API-Dokumentation gehört in `19-dom-interfaces-and-apis.md`.

## Processing Models

### Parser Dispatcher

Die Tree Construction bestimmt, ob Tokens nach HTML- oder Foreign-Content-Regeln verarbeitet werden.

Das ist ein normatives Processing Model.

### Foreign-Content Processing

Im Foreign Content gelten eigene Regeln für:

- Character Tokens
- Comments
- DOCTYPE
- Start Tags
- End Tags
- Namespace-Anpassungen
- Self-closing Flags
- Übergang zurück in HTML-Content

### Namespace-Erzeugung

Das Erzeugen eines Foreign Elements enthält insbesondere die Auswahl des Namespace.

Damit ist Namespace-Erzeugung ein Teil des Processing Models.

### Attributanpassung

Die Anpassungsalgorithmen für:

- MathML Attributes
- SVG Attributes
- Foreign Attributes

sind normative Verarbeitungsschritte.

## Parsing

Die umfassende Parsing-Dokumentation befindet sich in:

`docs/html/21-parsing.md`

Diese Datei behandelt daraus nur die Integrationsregeln.

### Relevanter WHATWG-Unterabschnitt

Besonders relevant ist:

§13.2.6.5 – The rules for parsing tokens in foreign content

Zusätzlich relevant sind die Tree-Construction-Regeln in:

§13.2.6 – Tree construction

### Foreign-Content-Regeln

Im Foreign Content unterscheidet die WHATWG-Spezifikation insbesondere:

- Character Tokens
- Comment Tokens
- Processing Instruction Tokens
- DOCTYPE Tokens
- bestimmte HTML-Start-Tags
- sonstige Start-Tags
- End-Tags

Die konkreten Regeln bestimmen, wann:

- ein Token ignoriert wird,
- ein Parse Error entsteht,
- ein Element aus dem Stack entfernt wird,
- HTML-Parsing erneut angewendet wird,
- ein Foreign Element erzeugt wird.

### Self-closing Flag

Bei Foreign Elements besitzt das Self-closing Flag eine besondere Parsing-Bedeutung.

Nach der Erzeugung eines Foreign Elements kann der Parser das aktuelle Element wieder vom Stack of Open Elements entfernen und das Self-closing Flag bestätigen.

Dies unterscheidet sich vom allgemeinen HTML-Verständnis der Solidus-Syntax.

Die genaue Verarbeitung wird durch die Foreign-Content-Regeln bestimmt.

### SVG `script`

Für ein SVG-`script`-Element existieren besondere Parsing-Regeln.

Diese Regeln sind nicht mit dem HTML-`script`-Element gleichzusetzen.

Für die tatsächliche Ausführung und SVG-seitige Verarbeitung verweist die WHATWG-Spezifikation auf die einschlägige SVG-Spezifikation.

## Fragment Parsing

SVG und MathML können auch im Rahmen des HTML Fragment Parsing relevant sein.

Dabei ist der Parsing-Kontext entscheidend.

Der Parser kann für ein Fragment einen Kontextknoten verwenden.

Dieser Kontext beeinflusst unter anderem:

- Namespace
- adjusted current node
- Tree Construction
- Foreign-Content-Verarbeitung
- Integration Points

Deshalb kann derselbe Fragment-Quelltext abhängig vom Kontextknoten unterschiedliche DOM-Strukturen erzeugen.

## HTML-Serialisierung

Bei der HTML-Serialisierung müssen Namespace-Informationen berücksichtigt werden.

Für Elemente aus:

- HTML Namespace
- MathML Namespace
- SVG Namespace

wird der jeweilige Local Name für die Serialisierung verwendet.

Attribute können abhängig von ihrem Namespace unterschiedlich serialisiert werden.

Relevant sind insbesondere:

- kein Namespace
- XML Namespace
- XMLNS Namespace
- XLink Namespace
- sonstige Namespaces

Die Serialisierung darf deshalb nicht als einfache Ausgabe von `tagName` und `attribute.name` verstanden werden.

## XML Namespace

Der XML Namespace ist bei Foreign Attributes relevant.

Beispielsweise kann:

`xml:lang`

als Attribut mit XML-Namespace und Local Name `lang` im DOM repräsentiert werden.

Dies unterscheidet sich von einem gewöhnlichen unqualified HTML-Attribut mit einem Doppelpunkt im Namen.

## XMLNS Namespace

Für Namespace-Deklarationen können insbesondere folgende Namen relevant sein:

- `xmlns`
- `xmlns:xlink`

Die HTML-Parserregeln können diese in den XMLNS Namespace einordnen.

Diese Regeln sind insbesondere für die korrekte DOM-Repräsentation und spätere XML-kompatible Verarbeitung relevant.

## XLink

XLink-Attribute können innerhalb von SVG/MathML-Kontexten namespace-aware verarbeitet werden.

Zu den relevanten Namen gehören:

- `xlink:actuate`
- `xlink:arcrole`
- `xlink:href`
- `xlink:role`
- `xlink:show`
- `xlink:title`
- `xlink:type`

Der HTML-Parser besitzt hierfür den Algorithmus zur Anpassung von Foreign Attributes.

Die Existenz dieser Parsing-Regel bedeutet nicht, dass ZE-WebLab XLink als eigenständige HTML-Feature-Familie behandelt.

## Accessibility

WHATWG definiert für HTML/SVG/MathML-Integration nicht automatisch eine vollständige Accessibility-Spezifikation für jedes SVG- oder MathML-Element.

Für diese Datei gilt daher:

- Namespace- und Parsing-Regeln werden aus WHATWG dokumentiert.
- Accessibility-Aussagen werden nicht aus der Namespace-Zugehörigkeit abgeleitet.
- Aussagen über zugängliche Namen, Rollen oder unterstützende Technologien müssen gegebenenfalls aus den einschlägigen Accessibility-Spezifikationen ergänzt werden.
- Eine solche externe Quelle ist ausdrücklich als externe normative Quelle zu kennzeichnen.

Insbesondere darf nicht behauptet werden:

„SVG ist barrierefrei“

oder:

„MathML ist automatisch barrierefrei“

nur weil der Inhalt normativ in HTML eingebettet werden kann.

## Sanitization

Sanitization ist von Parsing und Namespace-Integration zu trennen.

Die HTML/SVG/MathML-Integration bestimmt insbesondere:

- Namespace
- Elementerzeugung
- Attributanpassung
- Foreign-Content-Verarbeitung
- Integration Points

Daraus folgt nicht automatisch eine Aussage darüber, ob ein bestimmtes SVG- oder MathML-Element durch eine Sanitization-Regel entfernt oder verändert wird.

Für Sanitization-relevante Aussagen sind die jeweils aktuellen WHATWG-Sanitization-Regeln beziehungsweise einschlägige Sanitizer-API-Regeln separat zu prüfen.

Es wird aus der Namespace-Zugehörigkeit keine eigene Sanitization-Regel abgeleitet.

## Konformitätsregeln

### Namespace und Authoring

Autoren schreiben HTML normalerweise ohne explizite XML-Namespace-Deklarationen für gewöhnliche SVG-/MathML-Einbettungen.

Das HTML-Parsing-Modell bestimmt die Namespace-Zuordnung.

### Konformität und Parsing

Konformität und Parsing sind getrennte Dimensionen.

Ein Dokument kann nicht konform sein und trotzdem nach den normativen HTML-Parsing-Regeln zu einer definierten DOM-Struktur verarbeitet werden.

Dies gilt insbesondere für:

- falsche Verschachtelungen
- ungültige Attribute
- unerwartete Foreign-Content-Strukturen
- Parse Errors

### Parse Error

Ein Parse Error bedeutet nicht automatisch, dass das Parsing abgebrochen wird.

Die WHATWG-Spezifikation definiert für die jeweiligen Parserzustände, wie nach einem Parse Error weiterverfahren wird.

## Tag Omission

Tag-Omission-Regeln sind primär elementbezogene HTML-Syntaxregeln.

Für Foreign Elements darf aus den HTML-Regeln für optionale HTML-Tags nicht pauschal eine allgemeine SVG-/MathML-Regel abgeleitet werden.

Foreign-Content-Syntax und Foreign-Content-Parsing sind getrennt von den HTML-Tag-Omission-Regeln zu betrachten.

## DOM-Verhalten

### Namespace URI

Ein korrekt durch HTML-Parsing erzeugtes SVG-Element besitzt den SVG-Namespace.

Ein korrekt durch HTML-Parsing erzeugtes MathML-Element besitzt den MathML-Namespace.

Ein korrekt erzeugtes HTML-Element besitzt den HTML-Namespace.

### Local Name

Der Local Name ist vom Namespace unabhängig.

Daher können beispielsweise zwei Elemente denselben Local Name besitzen, aber verschiedenen Namespaces angehören.

### Namespace-sensitive Vergleiche

DOM-Anwendungen dürfen Foreign Elements deshalb nicht ausschließlich über:

`tagName`

klassifizieren.

Namespace-aware Prüfungen sind für eine robuste Unterscheidung relevant.

## Querverweise

### Element ↔ Namespace

Jedes relevante Foreign Element besitzt einen Namespace-Bezug.

### Namespace ↔ Parsing

Der Namespace beeinflusst die Tree Construction.

### Parsing ↔ Integration Point

Integration Points bestimmen, wann HTML-Verarbeitung innerhalb von Foreign Content wieder relevant wird.

### SVG ↔ HTML

SVG `foreignObject`, `desc` und `title` sind zentrale Übergangspunkte für HTML-Inhalte.

### MathML ↔ HTML

MathML Text Integration Points und bestimmte `annotation-xml`-Elemente stellen Übergangsmechanismen zwischen MathML und HTML dar.

### MathML ↔ SVG

Ein `svg`-Start-Tag innerhalb des einschlägigen MathML-`annotation-xml`-Kontexts besitzt eine besondere Tree-Construction-Regel.

### Parsing ↔ DOM

Das Parsing erzeugt DOM-Nodes mit Namespace- und Attributinformationen.

### DOM ↔ Serialization

Die Namespace-Informationen des DOM beeinflussen die HTML-Serialisierung.

### Parsing ↔ Custom Elements

Die Elementerzeugung innerhalb des Parsing-Modells kann mit der Custom-Element-Registry interagieren.

Die ausführliche Custom-Elements-Dokumentation bleibt in den entsprechenden Custom-Elements-Dateien.

## Status / V1

### WHATWG-Status

HTML/SVG/MathML-Integration ist im WHATWG HTML Living Standard definiert.

Die hier dokumentierten Konzepte sind insbesondere:

- normative Parsing-Regeln
- normative Namespace-Regeln
- normative Attributanpassung
- normative Integration-Point-Regeln
- normative DOM-/Parsing-Beziehungen

### V1-Einstufung

ZE-WebLab V1:

**Rechercheebene 2 – Integration Feature**

Begründung:

Die HTML/SVG/MathML-Integration ist keine Elementgruppe der ersten Ebene.

Sie beschreibt ein übergreifendes Zusammenspiel von:

- HTML
- SVG
- MathML
- Namespaces
- Parsing
- DOM
- Attributverarbeitung

### Browser-Kompatibilität

Browser-Kompatibilität ist nicht Bestandteil dieser Statusbewertung.

Aus der WHATWG-Definition wird kein Browser-Support-Status abgeleitet.

## Abgrenzung zu `21-parsing.md`

`21-parsing.md` dokumentiert das allgemeine HTML-Parsing-Processing-Model.

Dazu gehören insbesondere:

- Tokenization
- Tokenizer States
- Tree Construction
- Insertion Modes
- Stack of Open Elements
- Active Formatting Elements
- Parsing Errors
- Fragment Parsing
- Serialisierung
- Parser-/Script-Interaktionen

Diese Datei konzentriert sich dagegen auf:

- Namespace-Grenzen
- Foreign Content
- SVG-Integration
- MathML-Integration
- HTML Integration Points
- MathML Text Integration Points
- SVG-Attributanpassung
- MathML-Attributanpassung
- Foreign-Attribute-Anpassung
- HTML/SVG/MathML-Übergänge

Damit besteht eine bewusste Überschneidung auf normativer Parsing-Ebene, aber keine inhaltliche Duplizierung des gesamten Parsing-Modells.

## Abgrenzung zu `19-dom-interfaces-and-apis.md`

`19-dom-interfaces-and-apis.md` behandelt DOM Interfaces und APIs als eigene Feature-Ebene.

Diese Datei verwendet DOM-Konzepte nur dort, wo sie für die Namespace-/Integrationsregeln erforderlich sind.

Insbesondere werden:

- `namespaceURI`
- `localName`
- namespace-aware Elementerzeugung
- Serialisierung

als Integrationsbeziehungen dokumentiert.

Sie bilden keine neue DOM-API-Inventarliste.

## Abgrenzung zu Custom Elements

Custom Elements und Foreign Content sind unterschiedliche Feature-Familien.

Ein Custom Element ist nicht automatisch ein SVG- oder MathML-Element.

Umgekehrt ist ein SVG-/MathML-Element nicht allein wegen seiner Namespace-Zugehörigkeit ein Custom Element.

Die Interaktion zwischen Custom-Element-Erzeugung und Parser wird in den Custom-Elements- und Parsing-Dokumentationen behandelt.

## Abgrenzung zu Content Categories

Content Categories beschreiben Eigenschaften von HTML-Elementen innerhalb des HTML-Modells.

Namespaces und Integration Points sind dagegen Parsing-/DOM-Konzepte.

Deshalb sind:

- SVG Namespace
- MathML Namespace
- Foreign Content
- HTML Integration Point
- MathML Text Integration Point

keine neuen Content Categories.

## Abgrenzung zu Content Models

Ein Content Model beschreibt, welche Inhalte in einem bestimmten Kontext zulässig sind.

Die Namespace-Integration beschreibt dagegen, wie Foreign Content im DOM und beim Parsing repräsentiert und verarbeitet wird.

Diese beiden Dimensionen dürfen nicht miteinander vermischt werden.

## Abgrenzung zu nativen HTML-Elementen

Die folgenden Namen werden in dieser Datei als Integrations-/Foreign-Content-Konzepte behandelt:

- `svg`
- `math`
- SVG `foreignObject`
- SVG `desc`
- SVG `title`
- MathML `annotation-xml`
- MathML `mi`
- MathML `mo`
- MathML `mn`
- MathML `ms`
- MathML `mtext`

Die Auflistung stellt keine Erweiterung der nativen HTML-Elementinventarliste dar.

Insbesondere sind SVG- und MathML-Elemente keine HTML-Elemente.

## Normative Sonderregeln

### ASCII-case-insensitive `encoding`-Prüfung

Bei den relevanten MathML-`annotation-xml`-Regeln wird der Wert des `encoding`-Attributs ASCII-case-insensitiv mit den normativ genannten Werten verglichen.

### SVG Local-Name-Anpassung

Bestimmte SVG-Elementnamen werden beim Parsing von ihrer tokenisierten Schreibweise auf die SVG-definierte Schreibweise angepasst.

### SVG Attribute Adjustment

Bestimmte SVG-Attributnamen werden auf ihre definierte Schreibweise angepasst.

### MathML Attribute Adjustment

Bestimmte MathML-Attributnamen werden angepasst.

### Foreign Attribute Adjustment

Bestimmte Attribute werden in XML-, XMLNS- oder XLink-Namespaces überführt.

### Integration Points

Integration Points können dazu führen, dass HTML-Content-Regeln innerhalb eines Foreign-Content-Kontexts angewendet werden.

### Self-closing Foreign Elements

Foreign Elements unterliegen eigenen Regeln für das Self-closing Flag.

## Prüfstatus

### WHATWG-Struktur

**Geprüft**

### HTML Namespace

**Geprüft**

### SVG Namespace

**Geprüft**

### MathML Namespace

**Geprüft**

### Foreign Content

**Geprüft**

### HTML Integration Points

**Geprüft**

### MathML Text Integration Points

**Geprüft**

### SVG Attribute Adjustment

**Geprüft**

### MathML Attribute Adjustment

**Geprüft**

### Foreign Attribute Adjustment

**Geprüft**

### SVG-/MathML-Parsing

**Geprüft**

### Fragment Parsing

**Geprüft**

### DOM-/Namespace-Bezug

**Geprüft**

### HTML-Serialisierung

**Geprüft**

### Accessibility

**Teilweise geprüft**

Begründung:

WHATWG-Integrationsregeln wurden geprüft. Eine vollständige Accessibility-Abdeckung der SVG-/MathML-Vokabulare würde zusätzliche normative Accessibility-Spezifikationen erfordern.

### Sanitization

**Teilweise geprüft**

Begründung:

Die Namespace-/Parsing-Regeln wurden geprüft. Eine vollständige Feature-Matrix der Sanitization-Regeln ist eine davon getrennte Recherche.

## Offene Punkte

1. Eine vollständige Accessibility-Referenz für sämtliche SVG-/MathML-Elemente gehört nicht in diese Datei und erfordert die einschlägigen externen Accessibility-Spezifikationen.

2. Eine vollständige Beschreibung der SVG-2-Spezifikation gehört nicht in diese Datei. Diese Datei dokumentiert ausschließlich die HTML-seitige Integration.

3. Eine vollständige Beschreibung der MathML-Spezifikation gehört nicht in diese Datei. Diese Datei dokumentiert ausschließlich die HTML-seitige Integration.

4. Eine vollständige Browser-Kompatibilitätsmatrix ist nicht Bestandteil der WHATWG-Statusbewertung.

5. Die vollständigen Tabellen für SVG-Attributanpassung und Foreign Attributes müssen bei zukünftigen Aktualisierungen gegen die jeweils aktuelle WHATWG-Fassung erneut geprüft werden.

6. Änderungen der SVG- oder MathML-Spezifikationen können Auswirkungen auf die HTML-Integrationsregeln haben. Bei einer zukünftigen Living-Standard-Prüfung müssen deshalb die extern referenzierten Spezifikationen erneut abgeglichen werden.

7. Die genaue Zuordnung einzelner SVG-/MathML-DOM-Interfaces bleibt den jeweiligen DOM-/SVG-/MathML-Spezifikationen vorbehalten.

## Quellen / Referenzen

### Primärquelle

WHATWG HTML Living Standard

Relevante Bereiche:

- §3.2.5 Content models
- §4 The elements of HTML
- §13 The HTML syntax
- §13.2 Parsing HTML documents
- §13.2.6 Tree construction
- §13.2.6.5 The rules for parsing tokens in foreign content
- HTML Fragment Parsing
- HTML Serialisation

### Externe normative Quellen

Für die vollständige Semantik von SVG und MathML sind die jeweiligen Spezifikationen maßgeblich.

Diese externen Spezifikationen werden in dieser Datei nicht als Ersatz für die WHATWG-HTML-Spezifikation verwendet.

### Projektquelle

ZE-WebLab:

`docs/html/01-document-element.md`

`docs/html/02-document-metadata.md`

`docs/html/03-sections.md`

`docs/html/04-grouping-content.md`

`docs/html/05-text-level-semantics.md`

`docs/html/06-links.md`

`docs/html/07-edits.md`

`docs/html/08-embedded-content.md`

`docs/html/09-tabular-data.md`

`docs/html/10-forms.md`

`docs/html/11-interactive-elements.md`

`docs/html/12-scripting.md`

`docs/html/13-global-attributes.md`

`docs/html/14-content-categories.md`

`docs/html/15-content-models.md`

`docs/html/16-link-types.md`

`docs/html/17-custom-elements.md`

`docs/html/18-contexts.md`

`docs/html/19-dom-interfaces-and-apis.md`

`docs/html/20-custom-elements.md`

`docs/html/21-parsing.md`

## Kurzfazit

Die HTML/SVG/MathML-Integration ist eine eigenständige Rechercheebene-2-Feature-Familie.

Sie beschreibt nicht zusätzliche HTML-Elemente, sondern das normative Zusammenspiel zwischen:

- HTML Namespace
- SVG Namespace
- MathML Namespace
- Foreign Content
- Tree Construction
- Integration Points
- Attributanpassung
- DOM-Namespace-Modell
- Fragment Parsing
- Serialisierung

Die zentrale normative Grenze lautet:

**HTML-Elementinventar, Content Categories, Content Models, DOM Interfaces, Parsing und Foreign-Content-Integration sind getrennte Informationsdimensionen.**

SVG- und MathML-Elemente werden daher nicht in die native HTML-Elementliste aufgenommen.

Der Schwerpunkt dieser Datei liegt auf den Regeln, durch die HTML den Übergang zwischen diesen Vokabularen definiert.