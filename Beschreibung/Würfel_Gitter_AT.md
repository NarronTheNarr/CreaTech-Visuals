# Würfel_Gitter_AT

## Idee

Erstellung eines audio-reaktiven Visuellen Effekts basierend auf einem Gitter-Würfel. Das Projekt nutzt custom TouchDesigner Komponenten und parametrische Gitter-Strukturen, um Audiovisuals mit reaktiven Parametern zu erstellen.

## Tutorial-Reihe

### Basis-Tutorial: Grid Lines Texture

**[Grid Lines Texture | TouchDesigner Tutorial](https://www.youtube.com/watch?v=U1HsqYYmn78)**

**Grundkonzept:** Parametrische Gitter-Strukturen durch Konvertierung zwischen Subs, Tops und Chops. Basis für dynamische Liniendicken-Kontrolle.

### Haupttutorial: Audio Reactive Visuals

**[Create audio reactive visuals on TouchDesigner](https://www.youtube.com/watch?v=dPXkWLHYCQk)**

**Links & Downloads:**
- **von:** Acrylicode
- **Zeigt:** Custom Audio-Reactive Komponenten, Setup-Automatisierung, Timeline-Anpassung, Parameterkontrolle nach Audio-Frequenzbändern
- **Grundkonzept:** Audio-reaktive Visuals mit custom TouchDesigner Komponenten für präzise und flexible Parametersteuerung

## Umsetzung

### Gitter-Struktur-Basis (Grid Lines Texture)

**Daten-Konvertierungspipeline:**
1. **Green TOP** → **SOP to CHOP** → **CHOP to TOP** (für Datenmanipulation)
2. **TOP to CHOP** → **CHOP to SOP** (zurück zu Geometrie-Daten)

**Grid-Parameter:**
- Primitive Type: Polygon
- Connectivity: Columns
- Channel Scope: R, G, B (vollständig, nicht nur R)
- **CHOP to TOP** Image Layout: **Fit to Square**
- **TOP to CHOP** Setting: **Output as Single Channel** aktiviert

**Liniendicke-Kontrolle:**
- **Line Material** auf Geometry anwenden
- **CHOP to SOP** Parameter:
  - Channel Scope: R, G, B, **A** (Alpha)
  - Attribute Scope: P0, P1, P2, **Width**
  - Format: **32-bit Float RGBA**
- **Reorder TOP:** Input 1 (Grid) + Input 2 (Noise/Ramp) → Alpha-Kanal
- **Noise TOP:** Für organische Variation (Parameter: Period, Harmonic Gain, Exponent)
- **Ramp TOP:** Für systematische Gradation (Extend Left: Mirror)

### Audio Setup
1. Audio-Track in TouchDesigner importieren (z.B. von Epidemic Sound)
2. **Audio Device Out CHOP** anschließen für Audioausgabe
3. **Null CHOP** nach dem Audio anschließen (optional, für einfacheren Track-Wechsel später)

### Setup Audio Reactive Song Komponente
- Custom Component "Setup Audio Reactive Song" automatisiert die Timeline-Anpassung
- Prozess:
  - Audio CHOP in die **Song-Parameter** einfügen
  - **Setup-Button** drücken
  - Timeline-Länge wird automatisch auf Audiolänge angepasst
  - Play Mode wird automatisch auf "Set to Timeline" gestellt

### Audio Reactive Rotation Komponente
- Gibt konstant wachsende Werte aus (ideal für kontinuierliche Animationen)
- **Geeignet für:** Rotations-, Translations- und Positions-Parameter
- **Nicht geeignet für:** Skalierung (würde zu schnell aus dem Bild laufen)
- **Anwendung:**
  - Null CHOP nach der Komponente anschließen
  - Auf Parameter wie Translate Z ziehen
  - Mit Multiplikatoren anpassen (z.B. ×0.01, ×0.03) zur Geschwindigkeitsregelung
- **Verwendbar** auf jedem Parameter, der normalerweise mit `abs(time.seconds)` animiert wird
- In diesem Projekt: Würfel-Parameter mit Audio-Reaktivität verbunden

### Rendering & Visualisierung
1. **Geometry Component** mit Line Material
2. **Render TOP** + **Camera**
3. **RGB Key** für schwarzen Hintergrund
4. **Level TOP** optional (für Opacity-Anpassung)

### Animation
- **Noise Translation:** `abs(time.seconds)` auf Translate Z (kontinuierliche Bewegung)
- **Grid Rotation:** Optional auf Rotate Y für sphärische Variationen

## Abänderungen

- **Grid SOP statt Sphere** als primäre Geometrie-Basis
- **Nur Audio Reactive Rotation implementiert** (bis Minute 5:30 des Audio Reactive Visuals Tutorials)
- Liniendicken-Kontrolle durch Noise- und Ramp-Texturen
- Würfel-Parameter statt Sphere-Parameter für Translate Z
- Fokus auf kontinuierliche, zeitbasierte Animationen durch Audio
- Resolutions-Synchronisierung zwischen Chops und Tops

## Erfolge

- Effektive Daten-Konvertierung zwischen SOP/TOP/CHOP-Formaten
- Parametrische Kontrolle über Liniendicke und Linien-Muster
- Audio-reaktive Geometrie mit automatisiertem Timeline-Setup
- Flexible Multiplikatoren ermöglichen schnelle Anpassung an verschiedene Audiotracks
- Basis-Framework für komplexere Grid-Animationen
- Custom Komponenten reduzieren Konfigurationsaufwand
