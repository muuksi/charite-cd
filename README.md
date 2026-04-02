# charite-cd — Claude AI Skill

> **Automatisch CD-konforme Dokumente, Präsentationen und Abbildungen mit Claude erstellen**

Ein [Claude AI Skill](https://www.anthropic.com/claude) für das offizielle Corporate Design der **Charité – Universitätsmedizin Berlin**. Nach der Installation erstellt Claude automatisch Ausgaben im korrekten Charité-Stil – ohne manuelle Eingabe von Farben, Schriften oder Layoutvorgaben.

---

## Was macht dieser Skill?

Der `charite-cd` Skill gibt Claude vollständige Kenntnisse des Charité Corporate Designs:

- **Alle Charité-Farben** (Primär-, Sekundär- und Tertiärpalette) mit exakten HEX/RGB/CMYK-Werten
- **Typografie-Regeln** (Charité-Hausschrift, Fallback Calibri)
- **Logo-Verwendungsregeln**
- **Format-spezifische Anleitungen** für jeden Ausgabetyp

## Unterstützte Ausgabeformate

| Format | Details |
|--------|---------|
| 📊 **ggplot2 / R** | `theme_charite()`, Farbpaletten, `nice_save()` via [{charite}](https://github.com/johannesjuliusm/charite) |
| 📄 **Quarto (.qmd)** | HTML-Reports, PDF, Reveal.js mit CD-CSS-Templates |
| 📝 **Word (.docx)** | Briefe & Berichte auf offiziellen Charité-Vorlagen |
| 📽️ **PowerPoint (.pptx)** | Präsentationen auf offiziellen .potx-Vorlagen |
| 🌐 **HTML** | Standalone-Seiten, Dashboards, Shiny-Apps |
| 📋 **Excel / CSV** | Tabellen mit Charité-Formatierung (openxlsx, openpyxl) |

---

## Installation

### 1. Skill herunterladen

Lade die Datei [`charite-cd.skill`](https://github.com/maximilian-hinse/charite-cd/releases/latest/download/charite-cd.skill) herunter.

### 2. In Claude installieren

1. [claude.ai](https://claude.ai) aufrufen und einloggen
2. **Einstellungen** → **Profil** → **Skills**
3. **„+ Skill hinzufügen"** klicken
4. Die heruntergeladene `.skill`-Datei auswählen
5. Skill aktivieren ✓

### 3. Verwenden

Claude aktiviert den Skill automatisch bei Phrasen wie:

```
"Erstelle einen Charité-Bericht über..."
"Ich brauche eine Charité-Präsentation für..."
"Mach das CD-konform"
"Charité Corporate Design"
"ggplot2 im Charité-Stil"
```

Oder direkt: `/charite-cd`

---

## Trigger-Phrasen (automatische Aktivierung)

Der Skill wird automatisch aktiviert wenn Claude folgendes erkennt:

- `Charité Stil` / `Charité style`
- `Corporate Design` / `CD-konform`
- `Charité Vorlage` / `Charité template`
- `Charité Bericht` / `Charité Präsentation`
- `Charité Farben` / `Charité CD`
- `institutionelle Vorlage`
- `ggplot2 Charité` / `theme_charite`

---

## Voraussetzungen

### Für R-Ausgaben (empfohlen)

Das R-Paket `{charite}` von Johannes Julius Mohn installieren:

```r
# install.packages("devtools")
devtools::install_github("johannesjuliusm/charite")
```

→ Stellt `theme_charite()`, `charite_colors`, `charite_palettes`, `nice_save()` u.v.m. bereit.

### Charité-Hausschrift (optional)

Für optimale Typografie: **Charité Text Office** aus dem Charité-Intranet herunterladen und installieren. Ohne Installation wird automatisch **Calibri** als Fallback verwendet.

---

## Skill-Struktur

```
charite-cd/
├── SKILL.md                          # Haupt-Skill-Datei (Farben, Typografie, Übersicht)
├── references/
│   ├── colors.md                     # Alle 24 Charité-Farben (HEX/RGB/CMYK/PMS)
│   ├── r-quarto.md                   # R, ggplot2, Quarto HTML/PDF/Reveal.js
│   ├── word.md                       # Word (.docx) mit python-docx / Vorlagen
│   ├── pptx.md                       # PowerPoint mit pptxgenjs / Vorlagen
│   ├── html.md                       # HTML-Templates, Reveal.js, Shiny
│   └── excel.md                      # Excel mit openxlsx / openpyxl
└── assets/templates/
    ├── Charite-Praesentation_Vorlage_DE.potx
    ├── Charite-Praesentation_Vorlage_EN.potx
    ├── Charite_Bericht_Vorlage.dotx
    ├── Charite_Geschaeftsbrief_Vorlage_CCM_DE.dotx
    └── Charite_Geschaeftsbrief_Vorlage_CCM_EN.dotx
```

---

## Farb-Schnellreferenz

| Farbe | HEX | Verwendung |
|-------|-----|-----------|
| Charité-Blau | `#004D9B` | Primärfarbe, Überschriften, Akzente |
| Charité-Hellblau | `#007BC3` | Sekundär, Illustrationen |
| Charité-Dunkelblau | `#002552` | Dunkle Hintergründe |
| Charité-Hellgrau | `#CBCFD2` | Hintergründe, Tabellenzeilen |
| Charité-Korall | `#EA5451` | Akzent (sparsam!) |
| Textgrau | `#5E676C` | Fließtext |

→ Alle 24 Charité-Farben: siehe [`references/colors.md`](charite-cd/references/colors.md)

---

## Hinweise

- Die offiziellen Charité-Vorlagendateien (.potx, .dotx) sind Teil des Skills und dürfen nur für interne Charité-Zwecke verwendet werden.
- Das `{charite}` R-Paket wird separat von [Johannes Julius Mohn](https://github.com/johannesjuliusm/charite) gepflegt – bitte bei Nutzung korrekt acknowledgen.
- Dieser Skill ist kein offizielles Produkt der Charité – Universitätsmedizin Berlin.

---

## Autor

**Dr. Maximilian Hinse**  
Postdoctoral Researcher · Institut für Epidemiologie und Evidenzbasierte Medizin  
Charité – Universitätsmedizin Berlin

---

## Lizenz

MIT License – siehe [LICENSE](LICENSE)

Die eingebetteten Charité-Vorlagendateien unterliegen den Nutzungsbedingungen der Charité – Universitätsmedizin Berlin.
