---
version: alpha
name: Contour Drawing
description: >
  Corporate Identity der Contour-Drawing-App. Format nach
  github.com/google-labs-code/design.md, übernommen vom Bitcoin-Wiki
  Visualizer und auf diese App angepasst. Tokens haben Vorrang vor
  eigenen Annahmen.
omitted:
  - Elevation & Depth
colors:
  primary: "{colors.ink}"
  paper: "#ece2cd"                      # Seitenhintergrund, Bildfläche, Panel
  paper-bright: "#f2ead6"               # Text auf dunklen Flächen, Marker-Rand
  ink: "#5c4a34"                        # Überschriften, aktive Elemente, Buttons, Slider
  ink-soft: "#6b5a42"                   # Regler-Beschriftung
  ink-faint: "#8a7a5e"                  # Grundtext, Hinweise, Status
  line: "rgba(74,58,40,0.68)"           # Konturlinien im generierten SVG
  border: "rgba(110,92,64,0.25)"        # Trennlinien Panel/Titelleiste, Bildrahmen
  border-strong: "rgba(110,92,64,0.4)"  # Button-Rahmen
  accent: "rgba(150,90,50,0.95)"        # Quellpunkt-Marker
typography:
  title:                                # h1 Titelleiste
    fontFamily: "ui-sans-serif, system-ui, sans-serif"
    fontSize: 15px
    fontWeight: 600
  base:                                 # Grundschrift
    fontFamily: "ui-sans-serif, system-ui, sans-serif"
    fontSize: 13px
    fontWeight: 400
    lineHeight: 1.4
  ui:                                   # Regler, Buttons, Hinweise, Status
    fontFamily: "ui-sans-serif, system-ui, sans-serif"
    fontSize: 12px
    fontWeight: 400
rounded:
  button: 4px
spacing:
  page: 16px                            # Aussenabstand Titelleiste und Bildfläche
  panel: 12px                           # Innenabstand Panel, Abstand zwischen Panel-Blöcken
  control: 8px                          # Abstand benachbarter Buttons in einer Reihe
components:
  button:
    backgroundColor: transparent
    textColor: "{colors.ink}"
    typography: "{typography.ui}"
    rounded: "{rounded.button}"
    border: "1px solid {colors.border-strong}"
  marker:
    backgroundColor: "{colors.accent}"
    border: "1px solid {colors.paper-bright}"
    size: 12px
---

## Overview

Die App sieht aus wie eine alte topografische Vermessungskarte: Sepia-Papier,
dünne braune Höhenlinien, zurückhaltende Beschriftung. Eine einzige
Farbfamilie (warme Braun- und Beigetöne), kein reines Schwarz, kein reines
Weiss, keine zweite Akzentfarbe ausser dem wärmeren Rotbraun für die
Quellpunkt-Marker. Das generierte SVG selbst ist Teil des Designs: Konturen
in `line`-Braun auf `paper`. Interface-Elemente benutzen dieselbe Palette,
damit sie wie Kartenrand und Legende wirken.

## Colors

Alle Farben stammen aus einer Familie. `paper` ist die einzige Flächenfarbe;
Panel, Titelleiste und Bildfläche unterscheiden sich nur durch Trennlinien
(`border`). Text staffelt sich über drei Braunstufen von `ink` (wichtig) bis
`ink-faint` (beiläufig). Aktive Buttons invertieren: Grund `ink`, Text
`paper-bright`. Das Rotbraun (`accent`) markiert ausschliesslich die
Quellpunkte, sonst nichts. Linien und Rahmen sind nie voll deckend, nur
Flächen sind es. Keine neuen Alpha-Stufen.

## Typography

Systemschrift ohne Ausnahme, keine Webfonts. Drei Grössen genügen; nichts
unter 12px, nichts über 15px. Fett (600) nur für den Titel. Hinweise in
Kleinschreibung («click sets a point»).

## Layout

Feste Masse ausserhalb des Token-Schemas:

- Titelleiste: 61px hoch
- Panel: 276px breit, rechts
- Marker: 12px Durchmesser

## Components

- **Buttons**: 1px-Rahmen `border-strong`, Text `ink`, transparenter Grund.
  Aktiver Zustand invertiert: Grund `ink`, Text `paper-bright`. Kein
  Hover-Effekt.
- **Regler**: native range-Inputs mit `accent-color: ink`, Beschriftung
  links in `ink-soft`, aktueller Wert rechts in `ink`.
- **Marker**: rotbrauner Punkt (`accent`) mit hellem 1px-Rand, ziehbar.
- **Masken-Formen**: Umriss und Griffe in `accent`, Füllung fast
  transparent (rgba(150,90,50,0.08)); sichtbar nur bei offenem
  Masken-Panel.

## Do's and Don'ts

- Keine Animationen und keine Übergänge. Zustandswechsel springen.
  Einzige Ausnahme (wie im Bitcoinkb-Visualizer): das Panel gleitet beim
  Ein-/Ausklappen mit 0.2s heraus, die Lasche wandert mit.
- Keine Schatten, keine Verläufe.
- Interface-Sprache: Englisch, knapp, Kleinschreibung in Hinweisen.
- Keine Emojis, keine Icons.
