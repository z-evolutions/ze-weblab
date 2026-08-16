# ZE-WebLab – HTML-Vollständigkeits-Matrix

## Arbeitsstand

WHATWG-basierte Inventar- und Detailprüfungsstufe: HTML-Elemente, aktuell bis einschließlich §4.4 „Grouping content“.

**Primärquelle:** WHATWG HTML Living Standard / Edition for Web Developers.

**Rechercheabschluss dieses Arbeitsstands:** 16. August 2026.  
**Für die hier ausgewertete WHATWG-Edition ausgewiesener Stand:** 11. August 2026.

Diese Datei ist ein fachliches Arbeits- und Qualitätssicherungsartefakt. Sie ist keine Kopie der WHATWG-Spezifikation.

## Methodik

- Zuerst wird das Inventar der in WHATWG §4 definierten HTML-Elemente erfasst.
- Ein Element erhält genau eine Primär-ID. Wenn es im Standard an mehreren Stellen thematisch vorkommt, wird dies über Querverweise dokumentiert.
- Die Einordnung als konform/obsolete/non-conforming wird nicht allein aus dem Auftreten in §4 abgeleitet. Die individuelle Statusprüfung erfolgt als eigener Prüfschritt.
- V1-Zugehörigkeit folgt dem zuvor beschlossenen Referenzumfang und wird in dieser Inventarstufe vorläufig aufgenommen geführt.
- Fremdsprachige Elemente aus SVG/MathML werden nicht als HTML-Elemente inventarisiert; ihre HTML-Integrationsregeln werden separat geprüft.
- Custom Elements sind keine endliche Liste benannter HTML-Elemente und werden separat als Feature-Familie erfasst.
- Browser-Kompatibilitätsdaten werden nicht als WHATWG-Primärstatus übernommen.

## Matrix – eindeutiges HTML-Elementinventar

Die ursprünglich doppelt erfassten Elemente `a` und `area` werden hier nur einmal geführt. Ihre zusätzlichen Vorkommen im Standard werden als Querverweis dokumentiert.

| ID | Kategorie | Feature-Typ | Feature | WHATWG-Bereich | Statussystem | Status | V1-Referenz | ZE-WebLab-Kategorie | Prüfstatus | Querverweise / Hinweise | Offene Fragen |
|---|---|---|---|---|---|---|---|---|---|---|---|
| HTML-ELEM-001 | HTML | Element | `html` | 4.1 Document element | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-002 | HTML | Element | `head` | 4.2 Document metadata | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-003 | HTML | Element | `title` | 4.2 Document metadata | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-004 | HTML | Element | `base` | 4.2 Document metadata | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-005 | HTML | Element | `link` | 4.2 Document metadata | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-006 | HTML | Element | `meta` | 4.2 Document metadata | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-007 | HTML | Element | `style` | 4.2 Document metadata | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-008 | HTML | Element | `body` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-009 | HTML | Element | `article` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-010 | HTML | Element | `section` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-011 | HTML | Element | `nav` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-012 | HTML | Element | `aside` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-013 | HTML | Element | `h1` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Bestandteil der gemeinsamen `h1`–`h6`-Definition | |
| HTML-ELEM-014 | HTML | Element | `h2` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Bestandteil der gemeinsamen `h1`–`h6`-Definition | |
| HTML-ELEM-015 | HTML | Element | `h3` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Bestandteil der gemeinsamen `h1`–`h6`-Definition | |
| HTML-ELEM-016 | HTML | Element | `h4` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Bestandteil der gemeinsamen `h1`–`h6`-Definition | |
| HTML-ELEM-017 | HTML | Element | `h5` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Bestandteil der gemeinsamen `h1`–`h6`-Definition | |
| HTML-ELEM-018 | HTML | Element | `h6` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Bestandteil der gemeinsamen `h1`–`h6`-Definition | |
| HTML-ELEM-019 | HTML | Element | `hgroup` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-020 | HTML | Element | `header` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-021 | HTML | Element | `footer` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-022 | HTML | Element | `address` | 4.3 Sections | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-023 | HTML | Element | `p` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-024 | HTML | Element | `hr` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-025 | HTML | Element | `pre` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-026 | HTML | Element | `blockquote` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-027 | HTML | Element | `ol` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-028 | HTML | Element | `ul` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-029 | HTML | Element | `menu` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-030 | HTML | Element | `li` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-031 | HTML | Element | `dl` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-032 | HTML | Element | `dt` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-033 | HTML | Element | `dd` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-034 | HTML | Element | `figure` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-035 | HTML | Element | `figcaption` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-036 | HTML | Element | `main` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Hierarchische Zulässigkeit gesondert beachten | |
| HTML-ELEM-037 | HTML | Element | `search` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen |  | |
| HTML-ELEM-038 | HTML | Element | `div` | 4.4 Grouping content | WHATWG | aktuell definiert | Ja | Elemente | Detailprüfung abgeschlossen | Auch als Container für Name-Value-Gruppen in `dl` | |
| HTML-ELEM-039 | HTML | Element | `a` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar bereinigt; Detailprüfung später | Auch §4.6 Links | |
| HTML-ELEM-040 | HTML | Element | `em` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-041 | HTML | Element | `strong` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-042 | HTML | Element | `small` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-043 | HTML | Element | `s` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-044 | HTML | Element | `cite` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-045 | HTML | Element | `q` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-046 | HTML | Element | `dfn` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-047 | HTML | Element | `abbr` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-048 | HTML | Element | `ruby` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-049 | HTML | Element | `rt` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-050 | HTML | Element | `rp` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-051 | HTML | Element | `data` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-052 | HTML | Element | `time` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-053 | HTML | Element | `code` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-054 | HTML | Element | `var` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-055 | HTML | Element | `samp` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-056 | HTML | Element | `kbd` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-057 | HTML | Element | `sub` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-058 | HTML | Element | `sup` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-059 | HTML | Element | `i` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-060 | HTML | Element | `b` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-061 | HTML | Element | `u` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-062 | HTML | Element | `mark` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-063 | HTML | Element | `bdi` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-064 | HTML | Element | `bdo` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-065 | HTML | Element | `span` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-066 | HTML | Element | `br` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-067 | HTML | Element | `wbr` | 4.5 Text-level semantics | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-068 | HTML | Element | `area` | 4.6 Links | WHATWG | aktuell definiert | Ja | Elemente | Inventar bereinigt; Detailprüfung später | Auch §4.8 Embedded content | |
| HTML-ELEM-069 | HTML | Element | `ins` | 4.7 Edits | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-070 | HTML | Element | `del` | 4.7 Edits | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-071 | HTML | Element | `picture` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-072 | HTML | Element | `source` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-073 | HTML | Element | `img` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-074 | HTML | Element | `iframe` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-075 | HTML | Element | `embed` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-076 | HTML | Element | `object` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-077 | HTML | Element | `video` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-078 | HTML | Element | `audio` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-079 | HTML | Element | `track` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-080 | HTML | Element | `map` | 4.8 Embedded content | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend | `area` wird nur einmal im Inventar geführt | |
| HTML-ELEM-081 | HTML | Element | `table` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-082 | HTML | Element | `caption` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-083 | HTML | Element | `colgroup` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-084 | HTML | Element | `col` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-085 | HTML | Element | `tbody` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-086 | HTML | Element | `thead` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-087 | HTML | Element | `tfoot` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-088 | HTML | Element | `tr` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-089 | HTML | Element | `td` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-090 | HTML | Element | `th` | 4.9 Tabular data | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-091 | HTML | Element | `form` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-092 | HTML | Element | `label` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-093 | HTML | Element | `input` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-094 | HTML | Element | `button` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-095 | HTML | Element | `select` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-096 | HTML | Element | `datalist` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-097 | HTML | Element | `optgroup` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-098 | HTML | Element | `option` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-099 | HTML | Element | `textarea` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-100 | HTML | Element | `output` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-101 | HTML | Element | `progress` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-102 | HTML | Element | `meter` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-103 | HTML | Element | `fieldset` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-104 | HTML | Element | `legend` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-105 | HTML | Element | `selectedcontent` | 4.10 Forms | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-106 | HTML | Element | `details` | 4.11 Interactive elements | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-107 | HTML | Element | `summary` | 4.11 Interactive elements | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-108 | HTML | Element | `dialog` | 4.11 Interactive elements | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-109 | HTML | Element | `script` | 4.12 Scripting | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-110 | HTML | Element | `noscript` | 4.12 Scripting | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-111 | HTML | Element | `template` | 4.12 Scripting | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-112 | HTML | Element | `slot` | 4.12 Scripting | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |
| HTML-ELEM-113 | HTML | Element | `canvas` | 4.12 Scripting | WHATWG | aktuell definiert | Ja | Elemente | Inventar erfasst; Detailprüfung ausstehend |  | |

## Separate Feature-Familien innerhalb/um §4

| Feature-Familie | WHATWG-Bereich | Behandlung in ZE-WebLab |
|---|---|---|
| Custom Elements | §4.13 | Separater Referenzbereich; keine endliche Elementliste |
| Content Categories / Content Models | §3.2.5 und elementbezogene Definitionen | Als Eigenschaften/Querverweise der Elemente erfassen |
| Globale Attribute | §3.2.6 | Eigene Attribut-Inventarliste; nicht als Elementbestandteil duplizieren |
| Elementbezogene Attribute | elementbezogene Definitionen in §4 | Eigene Attribut-Inventarliste mit Elementbeziehungen |
| HTML/MathML/SVG-Integration | §4.8.15–4.8.16 | HTML-Integrationsregeln erfassen; vollständige MathML/SVG-Referenz nicht Teil der HTML-Elementliste |
| APIs und Verarbeitungsmodelle | verschiedene Unterabschnitte in §4 | Separat als API-/Konzept-Features prüfen |
| Heading / Outline | §4.3.11 | Eigenständige Konzept-/Verarbeitungsfamilie |
| Link Types | §4.6.8 | Eigenständige Feature-Familie |
| Meta-Namen und Pragma-Direktiven | §4.2.5.1–4.2.5.3 | Unterbestand des `meta`-Features mit eigenständiger Statusprüfung |

## Gemeinsames Detailmodell

Für jede Elementdefinition werden mindestens folgende Felder geführt:

- ID
- Bereich
- Feature-Typ
- Feature
- WHATWG-Abschnitt
- Statussystem
- Status
- V1-Referenz
- ZE-WebLab-Kategorie
- Content Categories
- Contexts
- Content Model
- Tag Omission
- Content Attributes
- Accessibility
- Sanitization
- DOM Interface
- normative Sonderregeln / Beschreibung
- Querverweise
- Quellen
- Prüfstatus
- offene Fragen

`Contexts`, `Content Model`, `Tag Omission`, `Content Attributes`, `Accessibility`, `Sanitization` und `DOM Interface` werden bewusst getrennt geführt. WHATWG beschreibt diese Angaben als unterschiedliche Bestandteile einer Elementdefinition; insbesondere sind Content Model und Tag Omission nicht dasselbe. Accessibility verweist für Autoren auf ARIA in HTML und für Implementierer auf HTML-AAM. Sanitization beschreibt die Sanitization-Kategorie eines Elements und ggf. URL-Attribute. Der DOM Interface-Eintrag ist normativ. 

---

# Detailprüfung – Block 4.1–4.2

## Verifizierte WHATWG-Struktur

§4.1 enthält das `html`-Element. §4.2 enthält `head`, `title`, `base`, `link`, `meta` und `style`. Die zusätzlichen Unterabschnitte zu `link` und `meta` werden als Verarbeitungs-/Feature-Untermodelle und nicht als zusätzliche Elemente erfasst.

## Ergebnis

| Feature | Content Categories | Verwendungskontext | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Statusprüfung |
|---|---|---|---|---|---|---|---|---|
| `html` | None | Dokumentelement | `head` gefolgt von `body` | Start- und Endtag unter definierten Bedingungen optional | Global | Default | `HTMLHtmlElement` | abgeschlossen |
| `head` | None | Erstes Element in `html` | Metadata content | Start- und Endtag unter definierten Bedingungen optional | Global | Default | `HTMLHeadElement` | abgeschlossen |
| `title` | Metadata | `head`, sofern kein anderes `title` vorhanden ist | Text ohne Inter-Element-Whitespace | Keine Auslassung | Global | Default | `HTMLTitleElement` | abgeschlossen |
| `base` | Metadata | `head` | Nothing | Kein Endtag | Global + `href`, `target` | Unsafe | `HTMLBaseElement` | abgeschlossen |
| `link` | Metadata; kontextabhängig auch Flow/Phrasing | Metadata-Kontext und bestimmte zusätzliche Kontexte | Nothing | Kein Endtag | Global + elementbezogene Link-Attribute | Uncategorized | `HTMLLinkElement` | abgeschlossen |
| `meta` | Metadata; mit `itemprop` zusätzlich Flow/Phrasing | Kontext abhängig von `charset`, `http-equiv`, `name`, `itemprop` | Nothing | Kein Endtag | Global + `name`, `http-equiv`, `content`, `charset`, `media` | Uncategorized | `HTMLMetaElement` | abgeschlossen |
| `style` | Metadata | Metadata-Kontext; definierte `noscript`-Sonderfälle | Stylesheet-Text | Keine Auslassung | Global + `media`, `blocking` | Uncategorized | `HTMLStyleElement` | abgeschlossen |

## Fachliche Feststellungen

1. `Sanitization` bleibt eine eigene Matrixspalte.
2. `Global Attributes` und elementbezogene Attribute werden getrennt.
3. `Contexts` bleibt erhalten, obwohl die Darstellung als Elementdefinition nicht dieselbe normative Rolle wie das Content Model besitzt.
4. `Content Model` ist eine normative Beschreibung des erwarteten Inhalts.
5. `Tag Omission` ist eine nicht-normative Kurzbeschreibung; die normativen Regeln befinden sich in den Syntaxregeln.
6. `DOM Interface` gehört zum Referenzmodell.
7. Accessibility wird später anhand der maßgeblichen Accessibility-Spezifikationen vertieft.
8. Status muss auf Feature-Ebene und ggf. auf Attribut-/State-Ebene unterscheidbar bleiben.
9. Kontextabhängige Content Categories werden ausdrücklich unterstützt.
10. Elementdefinition und Untermodelle werden getrennt erfasst.

## Offene Punkte

- Vollständiges globales Attributinventar.
- Vollständiges elementbezogenes Attributinventar.
- `link`-Typen.
- `meta`-Namen.
- `meta`-`http-equiv`.
- Accessibility-Vertiefung.
- Browser-Kompatibilität als getrennte Informationsschicht.

---

# Detailprüfung – §4.3 Sections

## Inventar

| Feature | Content Categories | Kontext | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface |
|---|---|---|---|---|---|---|---|
| `body` | None | Zweites Element in `html` | Flow content | Start- und Endtag unter Bedingungen optional | Global + Window-reflecting event-handler content attributes | Default | `HTMLBodyElement` |
| `article` | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | Keine Auslassung | Global | Default | `HTMLElement` |
| `section` | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | Keine Auslassung | Global | Default | `HTMLElement` |
| `nav` | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | Keine Auslassung | Global | Default | `HTMLElement` |
| `aside` | Flow, Sectioning, Palpable | Wo Sectioning Content erwartet wird | Flow content | Keine Auslassung | Global | Default | `HTMLElement` |
| `h1`–`h6` | Flow, Heading, Palpable | `legend`, `summary`, Flow | Phrasing content | Keine Auslassung | Global | Default | `HTMLHeadingElement` |
| `hgroup` | Flow, Palpable | `legend`, `summary`, Flow | strukturierte Folge aus `h1`–`h6`, `p` und script-supporting elements | Keine Auslassung | Global | Default | `HTMLElement` |
| `header` | Flow, Palpable | Flow | Flow ohne `header`-/`footer`-Nachfahren | Keine Auslassung | Global | Default | `HTMLElement` |
| `footer` | Flow, Palpable | Flow | Flow ohne `header`-/`footer`-Nachfahren | Keine Auslassung | Global | Default | `HTMLElement` |
| `address` | Flow, Palpable | Flow | Flow ohne Heading-, Sectioning-, `header`-, `footer`- oder `address`-Nachfahren | Keine Auslassung | Global | Default | `HTMLElement` |

## Fachliche Feststellungen

- `body` ist kein Sectioning Content und besitzt Window-reflecting Event-Handler-Content-Attributes.
- `article` ist Flow + Sectioning + Palpable und steht für eine eigenständige/reusable Komposition.
- `section` ist thematische Gruppierung und nicht lediglich ein generischer Styling-Container.
- `nav` ist für wichtige Navigationsblöcke vorgesehen; nicht jede Linkgruppe muss ein `nav` sein.
- `aside` bezeichnet tangential verbundenen, vom Hauptinhalt abgrenzbaren Inhalt.
- `h1`–`h6` werden als gemeinsame Elementdefinition behandelt; die Heading-Level sind ein separates Konzept.
- `hgroup` besitzt ein strukturiertes Content Model und ist deshalb nicht mit allgemeinem Flow Content gleichzusetzen.
- `header` und `footer` sind keine Sectioning-Elemente und erzeugen keine eigene Section.
- `address` bezeichnet Kontaktinformationen zum nächsten `article`- bzw. `body`-Vorfahren und ist nicht das allgemeine Element für beliebige Postadressen.

## Konzeptfamilie §4.3.11 / §4.3.12

Folgende Inhalte sind keine zusätzlichen Tags:

- Heading levels & offsets
- Sample outlines
- Exposing outlines to users
- Article or section?

Sie werden als eigene Konzept-/Verarbeitungsfeatures erfasst.

---

# Detailprüfung – §4.4 Grouping content

**WHATWG-Struktur:** §4.4 enthält genau 16 Elementdefinitionen: `p`, `hr`, `pre`, `blockquote`, `ol`, `ul`, `menu`, `li`, `dl`, `dt`, `dd`, `figure`, `figcaption`, `main`, `search` und `div`.

## Ergebnis der Detailprüfung

| Feature | WHATWG-Abschnitt | Content Categories | Kontext | Content Model | Tag Omission | Content Attributes | Sanitization | DOM Interface | Statusprüfung |
|---|---|---|---|---|---|---|---|---|---|
| `p` | 4.4.1 | Flow, Palpable | Flow | Phrasing content | Starttag unter definierten Bedingungen optional; Endtag optional, wenn unmittelbar ein Element folgt, das einen neuen Absatz impliziert, oder der Elternelement-Kontext endet | Global | Default | `HTMLParagraphElement` | abgeschlossen |
| `hr` | 4.4.2 | Flow | Flow; auch `select` | Nothing | Kein Endtag | Global | Default | `HTMLHRElement` | abgeschlossen |
| `pre` | 4.4.3 | Flow, Palpable | Flow | Phrasing content | Keine Auslassung | Global | Default | `HTMLPreElement` | abgeschlossen |
| `blockquote` | 4.4.4 | Flow, Palpable | Flow | Flow content | Keine Auslassung | Global + `cite` | Default | `HTMLQuoteElement` | abgeschlossen |
| `ol` | 4.4.5 | Flow, Palpable* | Flow | `li`-Elemente und script-supporting elements | Keine Auslassung | Global + `reversed`, `start`, `type` | Default | `HTMLOListElement` | abgeschlossen |
| `ul` | 4.4.6 | Flow, Palpable* | Flow | `li`-Elemente und script-supporting elements | Keine Auslassung | Global | Default | `HTMLUListElement` | abgeschlossen |
| `menu` | 4.4.7 | Flow, Palpable* | Flow | `li`-Elemente und script-supporting elements | Keine Auslassung | Global | Default | `HTMLMenuElement` | abgeschlossen |
| `li` | 4.4.8 | None | `ol`, `ul`, `menu` | Flow content | Endtag unter definierten Bedingungen optional | Global + `value` in den dafür vorgesehenen Listen-Kontexten | Default | `HTMLLIElement` | abgeschlossen |
| `dl` | 4.4.9 | Flow, Palpable* | Flow | Name-Value-Gruppen aus `dt`/`dd`, alternativ gruppiert über `div`, plus script-supporting elements | Keine Auslassung | Global | Default | `HTMLDListElement` | abgeschlossen |
| `dt` | 4.4.10 | None | `dl` bzw. definierte `div`-Gruppen innerhalb von `dl` | Flow content | Endtag unter definierten Bedingungen optional | Global | Default | `HTMLElement` | abgeschlossen |
| `dd` | 4.4.11 | None | `dl` bzw. definierte `div`-Gruppen innerhalb von `dl` | Flow content | Endtag unter definierten Bedingungen optional | Global | Default | `HTMLElement` | abgeschlossen |
| `figure` | 4.4.12 | Flow, Palpable | Flow | `figcaption` optional plus Flow content | Keine Auslassung | Global | Default | `HTMLElement` | abgeschlossen |
| `figcaption` | 4.4.13 | None | Als Kind von `figure` | Flow content | Keine Auslassung | Global | Default | `HTMLElement` | abgeschlossen |
| `main` | 4.4.14 | Flow, Palpable | Flow, hierarchisch korrekt | Flow content | Keine Auslassung | Global | Default | `HTMLElement` | abgeschlossen |
| `search` | 4.4.15 | Flow, Palpable | Flow | Flow content | Keine Auslassung | Global | Default | `HTMLElement` | abgeschlossen |
| `div` | 4.4.16 | Flow, Palpable | Flow; außerdem definierte `dl`-/Form-Control-Kontexte | Flow content | Keine Auslassung | Global | Default | `HTMLDivElement` | abgeschlossen |

`*` Die Palpable-Zuordnung von `ol`, `ul` und `menu` ist bedingt: WHATWG berücksichtigt hierfür insbesondere das Vorhandensein mindestens eines `li`-Elements.

## Fachliche Detailfeststellungen

### `p`

`p` repräsentiert einen Absatz. Sein Content Model ist Phrasing Content. Der Parser behandelt `p` besonders: Bestimmte neu beginnende Flow-Elemente führen in der HTML-Syntax zum impliziten Schließen eines offenen `p`. Das ist sowohl für die Tag-Omission-Dokumentation als auch für die Parsing-Referenz relevant.

Wichtig für ZE-WebLab:

- `p` ist nicht als beliebiger Block-Container zu erklären.
- Das Content Model ist Phrasing Content.
- Die Parser-/Optional-Tag-Regeln werden als eigene Querverbindung zur HTML-Syntax dokumentiert.
- Paragraphengrenzen können auch implizit durch andere Konstrukte entstehen; `p` ist die explizite Elementform.

### `hr`

`hr` repräsentiert einen thematischen Umbruch bzw. thematischen Wechsel. Es hat ein leeres Content Model und daher keinen Endtag.

Besonderheit des aktuellen Standards: Das Element ist nicht ausschließlich im gewöhnlichen Flow-Kontext dokumentiert; die Elementübersicht weist auch `select` als möglichen Elternkontext aus. Diese Sonderregel muss in der Detailreferenz erhalten bleiben.

`hr` ist semantisch kein bloßes „Linien“-Element. Die visuelle Darstellung gehört zur CSS-/Rendering-Ebene.

### `pre`

`pre` repräsentiert vorformatierten Text. Sein Content Model ist Phrasing Content.

Für die Referenz sind insbesondere relevant:

- Whitespace-/Newline-Verhalten,
- die besondere Behandlung des ersten Newline-Zeichens im HTML-Syntaxmodell,
- die Verbindung zur CSS-Eigenschaft `white-space`,
- die Verwendung für Text, dessen Formatierung durch Whitespace semantisch bzw. inhaltlich relevant ist.

Die Darstellung als Monospace-Block ist keine ausreichende semantische Definition des Elements.

### `blockquote`

`blockquote` repräsentiert einen Abschnitt, der aus einer anderen Quelle zitiert wurde. Das Content Model ist Flow Content.

Das `cite`-Attribut ist ein elementbezogenes Content Attribute und enthält eine URL zur Quelle bzw. zu weiterführenden Informationen über die Quelle. Die URL-Beziehung ist getrennt vom sichtbaren Zitattext zu dokumentieren.

Für Accessibility und Semantik ist wichtig, dass ein Zitat nicht nur durch visuelle Einrückung simuliert wird.

### `ol`

`ol` repräsentiert eine geordnete Liste. Das Content Model besteht aus `li`-Elementen und script-supporting elements.

Elementbezogene Attribute:

- `reversed` – Boolean; nummeriert die Liste rückwärts.
- `start` – legt den Startwert fest.
- `type` – legt den Typ der Listenmarkierung fest (`1`, `a`, `A`, `i`, `I`).

`ol` ist damit ein Beispiel dafür, dass die Semantik der Liste und ihre konkrete Nummerierungsdarstellung über getrennte Attribute gesteuert werden.

Die Palpable-Eigenschaft ist bedingt und wird bei der Auswertung der Content Categories berücksichtigt.

### `ul`

`ul` repräsentiert eine ungeordnete Liste. Das Content Model besteht aus `li`-Elementen und script-supporting elements.

Es besitzt außer globalen Attributen keine elementbezogenen Content Attributes.

Wichtig: Die Beschränkung auf `li`-Kinder ist ein echtes Content-Model-Erfordernis und nicht lediglich eine Konvention.

### `menu`

`menu` repräsentiert ein Menü von Befehlen. Im aktuellen Standard ist es eng an das Listenmodell gekoppelt: Das Content Model besteht aus `li`-Elementen und script-supporting elements.

Für ZE-WebLab wird `menu` deshalb nicht als bloße historische Alternative zu `ul` behandelt. Seine aktuelle Semantik und seine Rolle als Befehls-/Menücontainer werden separat dokumentiert.

### `li`

`li` repräsentiert ein Listenelement. Es darf nur in den vorgesehenen Listeneltern (`ol`, `ul`, `menu`) verwendet werden.

Das Content Model ist Flow Content.

Das `value`-Attribut ist für die entsprechenden geordneten Listenfälle relevant und definiert den ordinalen Wert des Listenelements. Es gehört deshalb in das elementbezogene Attributinventar und darf nicht mit CSS-Listenmarkern verwechselt werden.

Der Endtag kann unter den normativ definierten Bedingungen weggelassen werden, insbesondere wenn unmittelbar ein weiteres `li` folgt oder der Elternelement-Kontext endet.

### `dl`

`dl` repräsentiert eine Association List aus Name-Value-Gruppen.

Das aktuelle Content Model erlaubt:

- `dt`- und `dd`-Elemente als Name-/Value-Komponenten,
- definierte `div`-Gruppierungen von Name-Value-Gruppen,
- script-supporting elements.

Damit ist `dl` nicht auf klassische Glossare beschränkt. Für die Referenz sollte der Begriff „Name-Value-Gruppe“ verwendet werden.

Die Palpable-Eigenschaft ist bedingt: Sie hängt davon ab, ob mindestens eine Name-Value-Gruppe vorhanden ist.

### `dt`

`dt` repräsentiert die Bezeichnung bzw. den Namen einer zugehörigen `dd`-Gruppe.

Es besitzt keine eigene Content Category und wird innerhalb der vorgesehenen `dl`-Strukturen verwendet.

Das Content Model ist Flow Content. Die zulässige Struktur und die mögliche Tag-Omission sind zusammen mit `dl` und `dd` zu dokumentieren, weil isolierte Einzelregeln sonst leicht missverstanden werden.

### `dd`

`dd` repräsentiert den Inhalt zur zugehörigen `dt`-Bezeichnung bzw. den Value-Teil einer Name-Value-Gruppe.

Es besitzt keine eigene Content Category und hat Flow Content als Content Model.

Wie bei `dt` ist die Tag-Omission kontextabhängig. Die Regeln werden zusammen mit dem `dl`-Modell und der HTML-Parserlogik dokumentiert.

### `figure`

`figure` repräsentiert eine eigenständige Komposition bzw. einen Inhalt, der als Einheit referenziert werden kann. Es kann optional eine `figcaption` enthalten.

Das Content Model ist Flow Content mit der Bedingung, dass eine `figcaption` höchstens einmal und in der vorgesehenen Position vorkommt.

Typische Beispiele sind:

- Abbildungen,
- Diagramme,
- Codebeispiele,
- Tabellen,
- andere eigenständige Inhalte mit optionaler Beschriftung.

Die Semantik hängt nicht von der visuellen Darstellung als „Bildrahmen“ ab.

### `figcaption`

`figcaption` ist die Beschriftung einer `figure`.

Es darf ausschließlich im dafür vorgesehenen `figure`-Kontext verwendet werden.

Das Content Model ist Flow Content. Es besitzt keine eigene Content Category.

Für ZE-WebLab ist die Beziehung `figure` ↔ `figcaption` als strukturelle Beziehung zu modellieren, nicht lediglich als Styling- oder Textbeziehung.

### `main`

`main` repräsentiert den dominanten Inhalt eines Dokuments.

Es gehört zu Flow Content und Palpable Content. Sein Content Model ist Flow Content.

Wesentlich ist die hierarchische Zulässigkeit: WHATWG definiert Bedingungen dafür, wann ein `main`-Element als hierarchisch korrekt gilt. Deshalb darf die Referenz nicht nur „Hauptinhalt der Seite“ schreiben, sondern muss die hierarchische/semantische Einschränkung als normative Sonderregel dokumentieren.

`main` ist außerdem ein Beispiel für eine kontextabhängige Content Category: Es wird als Flow Content geführt, wenn es sich um ein hierarchisch korrektes `main` handelt.

### `search`

`search` repräsentiert einen Container für Suchsteuerelemente.

Es gehört zu Flow Content und Palpable Content und besitzt Flow Content als Content Model. Es hat keine eigenen elementbezogenen Attribute über die globalen Attribute hinaus.

Wichtig für die Referenz:

- `search` ist ein semantischer Container.
- Es ist nicht auf eine bestimmte visuelle Suchfeld-Darstellung beschränkt.
- Die konkreten Form Controls innerhalb des Containers werden über die Forms-Spezifikation erfasst.

### `div`

`div` ist der generische Flow-Container.

Es gehört zu Flow Content und Palpable Content und hat Flow Content als Content Model.

Der aktuelle Standard weist `div` außerdem als zulässigen strukturellen Bestandteil bestimmter `dl`-Name-Value-Gruppen sowie bestimmter Form-Control-Kontexte aus.

Für die redaktionelle Referenz ist besonders wichtig:

- `div` hat keine eigene fachliche Semantik über seine generische Containerfunktion hinaus.
- Es soll nicht anstelle eines semantisch passenden Elements verwendet werden, wenn ein solches vorhanden ist.
- Styling- oder Scripting-Gründe allein erzeugen keine neue Semantik.
- `div` darf nicht mit `span` verwechselt werden: Beide sind generische Container, unterscheiden sich aber in ihren Content-/Kontextregeln und im Renderingmodell.

---

## Querschnittserkenntnisse aus §4.4

### 1. Listen bilden ein zusammenhängendes Modell

Die Elemente `ol`, `ul`, `menu` und `li` müssen als zusammengehörige Feature-Familie modelliert werden.

Insbesondere:

- `ol` → geordnete Liste
- `ul` → ungeordnete Liste
- `menu` → Menü von Befehlen
- `li` → Listenelement

Die Einschränkung, dass Listen im Content Model nur die vorgesehenen `li`-Kinder sowie script-supporting elements enthalten, ist normativ und muss in der Referenz sichtbar sein.

### 2. `dl`, `dt`, `dd` bilden ebenfalls eine geschlossene Struktur

Die drei Elemente dürfen nicht als drei unabhängige Tags erklärt werden.

Das Datenmodell ist:

`dl` → Name-Value-Gruppen  
`dt` → Name/Bezeichnung  
`dd` → Value/Inhalt

Die aktuelle WHATWG-Fassung erlaubt zusätzlich definierte `div`-Gruppierungen innerhalb von `dl`.

### 3. `p` benötigt eine eigene Parsing-Querverbindung

`p` besitzt besondere implizite Schließungsregeln. Deshalb muss die Referenz:

- Elementdefinition,
- Tag Omission,
- HTML-Syntax,
- Parsing-Verarbeitung

miteinander verknüpfen.

### 4. Content Categories sind teilweise bedingt

`ol`, `ul`, `menu` und `dl` zeigen, dass Palpable Content nicht immer als unbedingte Eigenschaft eines Elementtyps behandelt werden kann.

Ebenso ist `main` als Flow Content an seine hierarchische Korrektheit gekoppelt.

Damit bestätigt §4.4 die bereits in §4.2 und §4.3 gewonnene Erkenntnis:

> Eine einzelne statische Kategorie-Spalte reicht fachlich nicht aus; Bedingungen und Ausnahmen müssen modellierbar sein.

### 5. Semantik und Rendering bleiben getrennt

`hr`, `pre`, `blockquote`, `figure`, `div` und `menu` zeigen besonders deutlich, dass die visuelle Standarddarstellung nicht die Semantik des Elements definiert.

Die Rendering-Regeln werden daher als separate Ebene behandelt.

### 6. `figure` und `figcaption` sind strukturell gekoppelt

Die Beziehung zwischen Abbildung/Komposition und Beschriftung wird als eigene strukturelle Beziehung erfasst.

### 7. `main` und `search` gehören in die semantische Referenz

Beide Elemente sind keine bloßen Styling-Container. Ihre Bedeutung liegt in der semantischen Beschreibung der Dokumentstruktur bzw. des Suchbereichs.

---

## Statusentscheidung für §4.4

Alle 16 Elementdefinitionen des Abschnitts §4.4 sind in der ausgewerteten aktuellen WHATWG-Fassung definiert und werden für die V1-Referenz aufgenommen.

Die Browser-Support-Informationen, die in der WHATWG-Webdarstellung teilweise aus MDN eingeblendet werden, werden nicht als WHATWG-Status übernommen.

## Offene Punkte nach §4.4

- Vollständige Attributdefinitionen und Zustände von `ol`, `li` und `blockquote` im separaten Attributinventar.
- Vollständige Parsing-/Optional-Tag-Matrix für `p`, `li`, `dt`, `dd` und die weiteren Elemente mit Tag-Omission-Regeln.
- Accessibility-Vertiefung anhand ARIA in HTML und HTML-AAM.
- Sanitization-Detailprüfung auf Attributebene.
- Rendering-Regeln bleiben eine separate Informationsebene.
- `dl`-Struktur und `div`-Gruppierung als eigene Lern-/Validierungsregeln modellieren.
- `main`-Hierarchieregeln als eigene Prüfregel erfassen.
- `menu`-Semantik und Beziehung zu Befehlen/Interaktion separat vertiefen.

---

# Kontrollstand

## Inventar

Der bisherige Arbeitsstand enthält die eindeutige HTML-Elementliste ohne doppelte IDs für Elemente, die in mehreren WHATWG-Bereichen vorkommen.

**Korrektur gegenüber dem vorherigen Stand:**

- `a` wird nicht mehr doppelt inventarisiert.
- `area` wird nicht mehr doppelt inventarisiert.
- Mehrfachvorkommen im Standard werden als Querverweis dokumentiert.

## Detailprüfungen abgeschlossen

- §4.1 The document element
- §4.2 Document metadata
- §4.3 Sections
- §4.4 Grouping content

## Noch nicht detailgeprüft

- §4.5 Text-level semantics
- §4.6 Links
- §4.7 Edits
- §4.8 Embedded content
- §4.9 Tabular data
- §4.10 Forms
- §4.11 Interactive elements
- §4.12 Scripting
- §4.13 Custom elements
- weitere Konzepte und Unterabschnitte von §4

## Quellen

Primärquelle:

- WHATWG HTML Living Standard: https://html.spec.whatwg.org/
- WHATWG Edition for Web Developers / Index: https://html.spec.whatwg.org/dev/indices.html
- WHATWG HTML Standard – Abschnitt §4: https://html.spec.whatwg.org/multipage/index.html
- WHATWG HTML Syntax / Optional Tags: https://html.spec.whatwg.org/multipage/syntax.html

Für die aktuelle Prüfung wurden ausschließlich WHATWG-Quellen als Primärquellen verwendet. MDN-/Browser-Support-Informationen wurden nicht als normativer Status in die Matrix übernommen.
