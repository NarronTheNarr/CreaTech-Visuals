# 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT

## Idee

Erstellung von audiovisuellen Effekten durch Projection Mapping auf mehrere Würfel. Edge-Detection, Feedback-Loops und pixelierte Effekte werden auf die Würfelflächen projiziert und durch Audio-Reaktivität von der Musik beeinflusst.

## Tutorial

**[Realtime White Visuals - TouchDesigner Tutorial (Beginner Friendly!)](https://www.youtube.com/watch?v=8ABSC0gkJrU)**

**Links & Downloads:**
- **von:** Daniel Steenhoff
- **Zeigt:** Edge TOP, Feedback-Loop und Limit TOP für pixelierte Effekte
- **Grundkonzept:** Audio-reaktive Visuals mit Noise-Funktionen

## Umsetzung

### Audio Setup
- Custom **AudioAnalysis Component** für Frequenzband-Separation
- Audio-Input wird in separate Signale aufgeteilt: Low, Mid, High, Snare, Kick, etc.
- Separate Kanäle ermöglichen präzise Parameter-Steuerung nach Frequenzbereichen
- Jedes Signal wird als Parameter an die Feedback-Loops weitergeleitet

### Effekt-Netzwerk
- Edge TOP für Kantenerkennung
- Feedback-Loop für kontinuierliche visuelle Rückkopplung
- Audio-Signale steuern Feedback-Parameter (z.B. Decay, Opacity basierend auf Frequency-Bands)
- Limit TOP für pixelierte Effekte
- Noise-Funktionen für zusätzliche Parameter-Animation

### Projektion auf Würfel
- Projection Mapping auf **6 verschiedene Würfel** mit unterschiedlichen Größen
- Separate Texture-Transformationen für jede Würfelfläche
- Audioreaktivität wird durch die aufgesplitteten Frequency-Bänder erzeugt

## Abänderungen

- Adaption des Tutorials von ebener Fläche auf Würfel-Geometrie
- Integration von audio-reaktiven Parametern für dynamische Effekte
- Optimierung der Verstärkungsfaktoren für visuelle Ausgabe

## Erfolge

- Visuell ansprechend mit organischen Mustern und Audio-Reaktivität
- Erfolgreiche Projektion auf mehrere 3D-Geometrien
- Für zukünftige Iterationen: **Instancing** statt Node-Duplikation für bessere Performance
