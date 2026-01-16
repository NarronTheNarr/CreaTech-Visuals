# Prism_Instances_JS

## Idee

Erstellung eines prismatischen, audio-reaktiven Visuellen Effekts durch **Instancing** von Würfeln. Das Projekt kombiniert Farb-Trails, Noise-Texturen und prismatische Überlagerungen, um einen dynamischen, multi-perspektivischen 3D-Effekt zu erzeugen.

## Tutorial

**[Audio Reactive Prismatic Visuals - TouchDesigner Tutorial](https://www.youtube.com/watch?v=tZt1SQUZl6U)**

**Links & Downloads:**
- **von:** nsohfi (Noah Shipman)
- **Zeigt:** Instancing, Audio-Analysis, Feedback-Loops, Prismatic Compositing
- **Zielgruppe:** Fortgeschrittene TouchDesigner-Nutzer (Grundlagen erforderlich)

**Grundkonzept:**
- Detaillierter Prozess hinter audio-reaktiven Prismen-Visuals
- Verwendung von **Instancing** für Performance-Optimierung statt Node-Duplikation
- Audio-Analysis zur Frequenzband-Separation (Low, Mid, High)
- Feedback-Loops und Color Trails für kontinuierliche visuelle Rückkopplung
- Prismatische Compositing-Effekte durch mehrfache Überlagerungen

## Umsetzung

### Audio Setup
1. Audio-Datei in Projekt importieren (Drag & Drop)
2. **Audio Device Out CHOP** für Audioausgabe
3. **Math CHOP** mit "Combine Channels" → "Average" für Mono-Konvertierung
4. **Audio Analysis** mit Mid & High Kanälen aktiviert
   - Threshold, Gain und Smoothing zur Musik anpassen für glatte, aber dynamische Bewegung
5. **Select CHOP** mit Kanälen: `low`, `mid`, `high`
6. **CHOP to TOP** (Format: RGB, Image Layout: Row per Channel)
   - Resultat: Ein Pixel mit R, G, B = Low, Mid, High

### Farb-Trail-Netzwerk (Color Trail)
1. **Fit TOP** – Einzelnes Pixel hochskalieren
2. **Transform TOP** – Translate Y: `0.9`
3. **Feedback TOP** mit integriertem Loop:
   - **Transform TOP** – Translate Y: `0.09`
   - **Composite TOP** (Mode: Over) – Feedback als Target, erste Transform als Input
4. **Null** – Name: "color trail" (Basis für Instancing)

### Noise-Geometrie
1. **Tube SOP** mit Twist-Effekten:
   - Rows/Columns: 100, Orientation: Z-axis, Height: 10
   - Twist 1: Strength 500
   - Twist 2: Axis Z, Strength 22
2. **SOP to CHOP** → **SOP to TOP** (RGB, Fit to Square)
3. **Noise TOP** mit finalen Parametern:
   - Period: 0.12, Harmonics: 0.46, Amplitude: 0.19, Offset: 0.057
   - Transform Tab – Translate C: `abs(ime.docs)`

### Composite-Netzwerk
1. Zwei **Composite TOPs** (Overlay & Glow):
   - Color Trail (Input 1) + Noise (Input 2)
2. **Cross TOP** – Wert: ~0.4
3. **Null** – Name: "for instancing"

### Instancing & 3D-Setup
1. **Box SOP** – Size: 0.7, Scale: 0.001
2. **Geometry COMP** – Instancing aktivieren
3. **Default OP Parameter** → "for instancing" NULL
4. **Translate XYZ** → R, G, B (Farben steuern Positionen)
5. **Constant Material** – Opacity: ~0.1, Blending & Transparency aktivieren
6. **Render TOP** + **Camera**
7. **RGB Key** vor Output

### Resolution Management
- **Constant CHOP** "global res" mit W (1080) und H (1080)
- Drag & Drop auf Render-Resolution als CHOP Reference
- Render Pixel Format: 16-bit Float RGBA

### Multi-Kamera-Blending
1. Zwei **Cameras**:
   - Cam 1: Orthografisch, direkte Ansicht
   - Cam 2: Isometrisch, angewinkelt
2. **Cam Blend Component**:
   - **LFO**: Frequenz 0.025, Offset 0.5, Amplitude 0.5
   - Weight 1: LFO-Channel 1
   - Weight 2: `1 - [Weight 1]`

### Geometrie-Rotation
- **LFO**: Frequenz 0.11, Offset 69.8, Amplitude 20, Type Gaussian, Bias 0.5

### Prismatisches Compositing
1. **Level TOP** – Opacity: ~0.13
2. Mehrfache **Over + Transform** Paare mit unterschiedlichen Transformationen:
   - Beispiel: Translate X: 0.5, Y: 0.2, Scale: -1, -1
   - Erzeugt Würfel-Duplikate an verschiedenen Positionen

### Feedback & Blur-Effekte
1. **Feedback TOP** + **Level TOP** (0.75) + **Composite TOP** (Add-Mode)
2. **Luma Blur** mit **Ramp** (Circular, Filter Size: 60)
3. **Bloom TOP**

### Light Leaks (Optional)
1. Stock-Video importieren
2. **Fit TOP** mit Global-Resolution-Referenzen
3. **Composite TOP** (Add-Mode)
4. **Multiply Composite** mit **Ramp** zur Center-Maskierung (Center: Schwarz, Enden: Weiß)
5. **Level TOP** – Opacity gesteuert durch Audio-High:
   - Select (High) → Filter → Math (×1.1) → Null "light leak control"
   - Als CHOP Reference auf Level Opacity

### Dynamische Audio-Steuerung
Für Parameter-Switches basierend auf Audio (z.B. Transform Y zwischen -0.1 und 0.9):
1. **Select CHOP** (Low/Mid/High-Channel)
2. **Math CHOP** (×10)
3. **Trigger** (Threshold: ~1.4, Attack/Sustain: 0)
4. **Logic CHOP** (Channel Preop: Toggle)
5. **Switch CHOP** mit zwei Constant-Werten
6. Switch ← Logic Null (als CHOP Reference)
7. **Wiederholen** für Mid und High auf anderen Parametern

### Finale Optimierungen
1. **Noise Level Top** vor "for instancing" reduzieren (konzentriert Würfel-Darstellung)
2. **Lookup TOP** nach RGB Key mit **Ramp** für Farbanpassung
3. **RGB Delay TOP** optional

## Abänderungen

- Unterschiedliche Blend-Modes für Overlay/Glow Composites testen
- Cross-Wert variieren für stärkere/schwächere Noise-Integration
- Prismatische Transformationen randomisieren
- Post-Processing in After Effects: Color/Contrast-Editing, erweiterte Blur, Grain gegen Banding

## Erfolge

- Visuell spektakulär mit prismatischen Effekten und Audio-Reaktivität
- **Instancing** ermöglicht hohe Performance statt Node-Duplikation
- Flexible Parameter erlauben einfache Anpassung an verschiedene Audio-Quellen
- Vollständig echtzeitfähig für Live-Performances
- Großer Experimentierraum für kreative Variationen und Anpassungen
