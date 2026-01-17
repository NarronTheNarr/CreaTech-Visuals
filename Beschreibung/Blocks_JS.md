# Prism_Instances_JS

## Idee

Erstellung eines audio-reaktiven Visuellen Effekts durch **Instancing** von Würfeln. Das Projekt kombiniert verschiedene Würfelarten und die Manipulation von ihnen im 3D-Raum.

## Tutorial

**[How I Create Audio-Reactive Art | Touch Designer Crash Course](https://www.youtube.com/watch?v=12J2XH2UxDc&t)**

**Links & Downloads:**
- **von:** pwnisher
- **Zeigt:** Kreation der Würfel und Midi-Kontrolle dieser Attribute
- **Zielgruppe:** Fortgeschrittene TouchDesigner-Nutzer (Grundlagen erforderlich)

**Grundkonzept:**
- Verwendung von **Instancing** für Performance-Optimierung statt Node-Duplikation
- Manipulation von Visuals auf Knopfdruck

## Umsetzung

### Audio Setup
1. Audio-Datei in Projekt importieren (Drag & Drop)
2. **Audio Device Out CHOP** für Audioausgabe
3. Custom **AudioAnalysis Component** erstellen:
   - **Audio File In CHOP** als Quelle
   - **Math CHOP** mit "Combine Channels" → "Average" für Mono-Konvertierung
   - **Audio Analysis CHOP** mit allen Kanälen aktiviert (Low, Mid, High)
   - Zusätzliche **Band EQ Filter CHOPs** für spezifische Frequenzbereiche:
     - Kick: Low-Pass Filter (~60-120 Hz)
     - Snare: Band-Pass Filter (~150-250 Hz)
     - High-Hat: High-Pass Filter (~8-12 kHz)
4. **Select CHOPs** für jeden benötigten Kanal
5. **Null CHOPs** als Output-Referenzen benennen
   - "audio_kick", "audio_snare", "audio_low", "audio_mid", "audio_high"

### Block-Geometrie Setup
1. **Box SOP** – Basis-Würfelgeometrie
2. Mehrere **Copy SOPs** für verschiedene Würfel-Anordnungen:
   - Grid-Anordnung: Rows/Columns mit Spacing
   - Circular-Anordnung: Mit Transform SOP rotieren
   - Random-Anordnung: Scatter SOP verwenden
3. **Merge SOP** um verschiedene Geometrie-Sets zu kombinieren

### Instancing & Material Setup
1. **Geometry COMP** – Instancing aktivieren
2. **Constant Material MAT**:
   - Color Map: Texture-Referenz (siehe nächster Schritt)
   - Ambient Color: Audio-gesteuert (Mid-Channel)
   - Specular: Audio-gesteuert (High-Channel)

### Rotation & Transformation
1. **LFO CHOPs** für kontinuierliche Bewegung
2. **Math CHOPs** um Audio-Signale zu multiplizieren:
   - LFO × Audio-Kick für impulsive Rotation
   - Amplitude-Scaling: ×360 für volle Drehungen

### 3D-Kamera & Rendering
1. **Camera COMP** Setup
2. **Light COMPs** für dynamische Beleuchtung
3. **Render TOP**

### MIDI-Integration (Optional)
1. **MIDI In CHOP** für Controller-Input
2. **MIDI In Map CHOP** zum Mapping von CC-Werten
3. **Select CHOPs** für spezifische MIDI-Kanäle
4. **Parameter-Switches** mit MIDI-Triggern:
   - Button 1: Geometrie-Type wechseln
   - Button 2: Material-Mode umschalten
   - Button 3: Rotation-Speed ändern
   - Fader 1-4: Opacity, Scale, Color, Brightness
5. **Logic CHOP** für Toggle-Funktionen

### Feedback & Post-Processing
1. **Feedback TOP** für visuelle Persistenz
   - **Transform TOP** intern: Scale 1.01 (Zoom-Out-Effekt)
2. **Composite TOP** (Add-Mode):
   - Current Frame + Feedback
3. **Blur TOP**
4. **Bloom TOP**

### Color Grading
1. **Lookup TOP** mit **Ramp**
2. **Level TOP**
3. **HSV Adjust TOP**:
   - Hue Shift: Audio-Low × 360 (kontinuierliche Farbrotation)

### Performance-Optimierung
1. **Resolution CHOPs** als globale Variablen
2. **Instancing** statt Duplikation verwenden
3. **Null OPs** für häufig referenzierte Nodes
4. Cook-Type auf "Auto" nur bei finalen Output-Nodes

## Abänderungen

- Im Tutorial alles mit MIDI gesteuert, diese habe ich zu Audioreaktiv geändert

## Erfolge

- Hochperformantes Instancing ermöglicht große Mengen an Würfeln in Echtzeit
- MIDI-Integration erlaubt intuitive Live-Kontrolle während Performances
- Flexible Audio-Analyse-Pipeline für verschiedene Musik-Genres
- Modularer Aufbau ermöglicht einfaches Austauschen von Komponenten
- Vollständig echtzeitfähig für Live-VJ-Sets und Performances

