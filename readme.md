# CreaTech-Visuals – Audiovisuelle Livevisuals mit TouchDesigner

**Projektgruppe:** macherinne  
**Teilnehmende:** Aaron Täschler, Jan Schmidt  
**Semester:** HS 2025  
**Auftritt:** 16. Januar 2026 (Salzhaus, Winterthur)

---

## 📋 Projektabsicht

Wir haben audiovisuelle Livevisuals mittels **TouchDesigner** kreiert. Dabei haben wir verschiedene Tutorials analysiert, nachgebaut und mit eigenen Modifikationen erweitert. Das Projekt umfasst insgesamt **8 verschiedene TouchDesigner-Files**, wovon die **4 besten** für die finale Abgabe und den Auftritt ausgewählt wurden.

### Finale Visuals

1. **[6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT](./Beschreibung/6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.md)** – Projection Mapping mit Audio-Reaktivität
2. **[Würfel_Gitter_AT](./Beschreibung/Würfel_Gitter_AT.md)** – Audio-reaktive Gitter-Würfel Effekte
3. **[Prism_Instances_JS](Beschreibung/Prism_Instances_JS.md)** – Prismatische Würfel-Instancing mit Audio-Reaktivität
4. **[Blocks_JS](Beschreibung/Blocks_JS.md)** – Cubes auf einer Ebene verteilt und Manipulation durch Audio

---

## 🛠️ Technologie & Setup

### System Architecture

```
┌──────────────────────────────────────────────────────────────────────────┐
│                        LIVE SETUP WORKFLOW                                │
└──────────────────────────────────────────────────────────────────────────┘

AUDIO EINGABE                          VERARBEITUNG              AUSGABE
   
┌──────────┐      ┌───────────┐    ┌──────────────┐    ┌──────────────┐
│  CDJ     │──────│  Mixer    │────│ Mischpult    │────│   Zoom       │
│          │ DMX  │  & Audio  │ HF │ (AUX Input)  │    │  Aufnahmegerät
└──────────┘      └───────────┘    └──────────────┘    │   (USB Out)  │
                                      ▲                 └──────────────┘
                                      │                        │
                                  Chinch-Kabel              USB-Audio
                                   (RCA)                       │
                                                              ▼
                                                    ┌──────────────────┐
                                                    │  Laptop          │
                                                    │ TouchDesigner    │
                                                    │  2023            │
                                                    │                  │
                                                    │ • Audio Analysis │
                                                    │ • Real-time      │
                                                    │   Rendering      │
                                                    └──────────────────┘
                                                            │
                                                          HDMI
                                                            │
                                                            ▼
                                                    ┌──────────────────┐
                                                    │  HDMI Splitter   │
                                                    └──────────────────┘
                                                      │              │
                                                    HDMI          HDMI
                                                      │              │
                                    ┌─────────────────┘              │
                                    ▼                                ▼
                          ┌──────────────────┐            ┌──────────────────┐
                          │    Beamer 1      │            │    Beamer 2      │
                          │  (Projektion)    │            │  (Projektion)    │
                          └──────────────────┘            └──────────────────┘
```

**Grafische Veranschaulichung der Systemarchitektur:**
![System Architecture Diagram](/creaTech_system_architecture.jpg)

**Komponenten-Details:**

| Komponente | Funktion | Verbindung |
|---|---|---|
| **CDJ** | Audio-Quelle | DMX → Mixer |
| **Mixer** | Audio-Signalverarbeitung | Analoges Audio → Mischpult |
| **Mischpult (AUX)** | Audio-Pegelregelung | Chinch/RCA → Zoom |
| **Zoom Aufnahmegerät** | Audio-Digitalisierung | USB → Laptop |
| **Laptop** | Visuals Processing & Rendering | HDMI → Splitter |
| **HDMI Splitter** | Video-Distribution | HDMI → 2× Beamer |
| **Beamer 1 & 2** | Projektion auf Flächen | Video-Input (HDMI) |


---

- **Software:** TouchDesigner 2023 (Non-Commercial)
- **Betriebssystem:** Windows
- **Audio-Input:** CDJ → Mixer → Mischpult (AUX) → Zoom Aufnahmegerät (USB)
- **Zusätzliche Komponenten:** Custom AudioAnalysis Components für Frequenzband-Separation



### Systemanforderungen

- **GPU:** Dedizierte Grafikkarte erforderlich (für optimale Performance)
- **CPU:** Multi-Core Prozessor empfohlen
- **RAM:** Mindestens 8GB (empfohlen mindesten 16GB)
- **Monitor:** Full HD oder höher für Live-Performance

---

## 🎬 Projektdetails

### Visual 1: 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT

**Konzept:** Projection Mapping auf mehrere Würfel mit Edge-Detection und Audio-Reaktivität

**Umsetzung:**
- **Audio Setup:** Custom AudioAnalysis Component separiert Audio-Input in Frequency-Bänder (Low, Mid, High, Snare, Kick)
- **Effekte:** 
  - Edge TOP für Kantenerkennung
  - Feedback-Loops für kontinuierliche visuelle Rückkopplung
  - Limit TOP für pixelierte Effekte
  - Noise-Funktionen für Parameter-Animation
- **Geometrie:** 6 verschiedene Würfel mit unterschiedlichen Größen
- **Audio-Steuerung:** Frequency-Bänder steuern Feedback-Parameter (Decay, Opacity)

**Basis-Tutorial:** [Realtime White Visuals - TouchDesigner Tutorial](https://www.youtube.com/watch?v=8ABSC0gkJrU) von Daniel Steenhoff

**Modifikationen:**
- Adaption von ebener Fläche zu Würfel-Geometrie
- Integration von AudioAnalysis Components für erweiterte Audio-Reaktivität
- Optimierte Verstärkungsfaktoren für visuellen Output

### Visual 2: Würfel_Gitter_AT

**Konzept:** Audio-reaktive Grid-Effekte auf Würfel-Struktur durch parametrische Gitter und automatisierte Audio-Reaktiv-Komponenten

**⚠️ Voraussetzung:** Custom Audio-Reactive Komponenten müssen vom [Acrylicode Patreon](https://www.patreon.com/acrylicode) heruntergeladen werden:
- Setup Audio Reactive Song Component
- Audio Reactive Rotation Component

**Tutorial-Reihe:**

1. **Basis:** [Grid Lines Texture | TouchDesigner Tutorial](https://www.youtube.com/watch?v=U1HsqYYmn78)
   - Parametrische Gitter-Strukturen durch SOP/CHOP/TOP Konvertierung
   - Liniendicken-Kontrolle via Noise & Ramp Texturen
   
2. **Haupttutorial:** [Create audio reactive visuals on TouchDesigner](https://www.youtube.com/watch?v=dPXkWLHYCQk)
   - Custom Audio-Reactive Komponenten Integration
   - Timeline-Automatisierung und Parametersteuerung

**Umsetzung:**
- **Gitter-Struktur:** Grid SOP mit SOP→CHOP→TOP→CHOP→SOP Konvertierungspipeline
- **Liniendicke-Kontrolle:** Line Material mit Alpha-Channel (Noise/Ramp basiert)
- **Audio Setup:** Audio-Track mit automatischer Timeline-Anpassung via Setup Audio Reactive Song Component
- **Custom Komponenten:**
  - Setup Audio Reactive Song (automatisiert Timeline-Länge und Play Mode)
  - Audio Reactive Rotation (kontinuierlich wachsende Werte für Rotations- und Translations-Parameter)
- **Effekte:** Parametrische Würfel-Visualisierung mit Noise- und Ramp-kontrollierten Liniendicken
- **Parameter-Animation:** Multiplizierte LFO-Werte für kontinuierliche Bewegung (z.B. ×0.01, ×0.03)

**Modifikationen:**
- **Grid SOP statt Sphere** als primäre Geometrie-Basis
- Nur Audio Reactive Rotation implementiert (bis Minute 5:30)
- Liniendicken-Kontrolle durch Noise- und Ramp-Texturen
- Resolutions-Synchronisierung zwischen Chops und Tops
- Fokus auf kontinuierliche, zeitbasierte Animationen durch Audio

### Visual 3: Prism_Instances_JS

**Konzept:** Prismatische Würfel-Instancing mit Audio-Reaktivität und dynamischen 3D-Überlagerungen

**Voraussetzung:** Custom Instancing Components sind im Projekt enthalten oder können via nsohfi Patreon erweitert werden.

**Umsetzung:**
- **Audio Setup:** Audio-Datei importieren, Audio Device Out und Mono-Konvertierung via Math CHOP
- **Audio Analysis:** Frequency-Separation in Low, Mid, High Kanäle mit Threshold/Gain/Smoothing
- **Farb-Trail-Netzwerk:** Color Trail mit Feedback-Loops und kontinuierlicher visueller Rückkopplung
- **Noise-Geometrie:** Tube SOP mit Twist-Effekten, konvertiert zu Noise TOP für organische Formen
- **Instancing:** Box SOP mit Geometry Component und Custom Default OP Parameter (Translate XYZ = R, G, B)
- **Effekte:**
  - Multi-Kamera-Blending (Orthographisch + Isometrisch mit LFO-Steuerung)
  - Prismatisches Compositing (mehrfache Over/Transform Paare mit verschiedenen Transformationen)
  - Light Leaks mit Audio-Steuerung (High-Frequenzen steuern Opacity)
  - Dynamische Parameter-Switches (Low/Mid/High triggern unterschiedliche Transformationen)
- **Post-Processing:** Bloom, Luma Blur, RGB Lookup, optionales RGB Delay

**Basis-Tutorial:** [Audio Reactive Prismatic Visuals - TouchDesigner Tutorial](https://www.youtube.com/watch?v=tZt1SQUZl6U) von nsohfi (Noah Shipman)

**Modifikationen:**
- Instancing statt Node-Duplikation für optimale Performance
- Erweiterte Audio-Analyse mit Frequenzband-Separation
- Prismatische Effekte durch mehrfache zufällige Überlagerungen
- Dual-Kamera-Blending für dynamische Perspektivwechsel
- Audio-reaktive Light Leaks für erhöhte Dynamik

### Visual 4: Blocks_JS

**Konzept:** Audio-reaktive Würfel-Visualisierung durch hochperformantes Instancing mit verschiedenen geometrischen Anordnungen (Grid, Circular, Random)

**Umsetzung:**
- **Audio Setup:** Custom AudioAnalysis Component mit Frequenzband-Separation (Low, Mid, High, Kick, Snare, High-Hat)
- **Block-Geometrie:** 
  - Box SOP als Basis-Würfelgeometrie
  - Multiple Copy SOPs für verschiedene Anordnungen (Grid-Rows/Columns, Circular mit Transform SOP, Random via Scatter SOP)
  - Merge SOP zur Kombination verschiedener Geometrie-Sets
- **Instancing & Material:** Geometry COMP mit aktiviertem Instancing und Constant Material (Audio-gesteuerte Ambient/Specular-Parameter)
- **Rotation & Transformation:** LFO CHOPs kombiniert mit Math CHOPs für audio-gesteuerte Rotation (LFO × Audio-Kick × 360°)
- **Effekte:**
  - Feedback TOP mit Transform (Scale 1.01 für Zoom-Out-Effekt)
  - Composite TOP (Add-Mode), Blur & Bloom für visuelle Persistenz
  - Color Grading via Lookup TOP, Level TOP, HSV Adjust (Hue Shift durch Audio-Low × 360°)
- **3D-Setup:** Camera COMP mit dynamischen Light COMPs und Render TOP

**Basis-Tutorial:** [How I Create Audio-Reactive Art | Touch Designer Crash Course](https://www.youtube.com/watch?v=12J2XH2UxDc&t) von pwnisher

**Modifikationen:**
- **MIDI zu Audio:** Alle MIDI-gesteuerten Parameter auf Audio-Reaktivität umgestellt
- Hochperformantes Instancing statt Node-Duplikation
- Flexible Audio-Analyse-Pipeline für verschiedene Musik-Genres
- Modularer Aufbau für einfaches Austauschen von Komponenten

---

## � Installation & Setup

### Dateien öffnen

1. **TouchDesigner installieren:**
   - [TouchDesigner Non-Commercial Download](https://derivative.ca/download) (kostenlos)
   - Version 2023 oder höher empfohlen

2. **.toe Dateien öffnen:**
   ```
   TouchDesigner/visuals/*.toe
   ```
   - Einfach mit TouchDesigner öffnen oder Drag & Drop

### Custom Components installieren

Für **Visual 2 (Würfel_Gitter_AT)** sind Custom Audio-Reactive Komponenten erforderlich:

- **Acrylicode Patreon:** https://www.patreon.com/acrylicode
  - Setup Audio Reactive Song Component
  - Audio Reactive Rotation Component
  
Nach dem Download in das Projekt-Verzeichnis kopieren oder im Netzwerk-Dialog laden.

### Audio-Setup vor Live-Performance

1. Zoom H5/H6 Aufnahmegerät mit USB verbinden
2. In Windows Sound Settings als Default Input setzen
3. In TouchDesigner Audio-Input konfigurieren (Audio Device CHOP)
4. **Test:** Musik abspielen und Visuals sollten reagieren

---

## 📹 Video-Ressourcen

### Demo Videos
Schaue dir die erstellten Visuals in Aktion an:
→ **[Demo Videos Playlist](https://youtube.com/playlist?list=PL1AuDKbdA11S-ClVK1wWQfbwvTORzaZr3&si=Oept_Ms1Qnhzgilk)**

### Erklär Videos
Detaillierte Erklärungen zur Technik und Umsetzung:
→ **[Erklär Videos Playlist](https://www.youtube.com/playlist?list=PL1AuDKbdA11TB7vLqEOIXLVz_h47NN9El)**

---

## 📝 Entwicklungsprozess & Reflexion

### Planungs- und Entwicklung

Das Projekt startete mit einer individuellen Recherche-Phase: Jedes Projektmitglied suchte unabhängig vier Tutorials nach persönlichen Ansprüchen aus. **Entscheidend war die pragmatische Tutorial-Auswahl** – es wurde bewusst auf Anfänger-freundliche Tutorials geachtet, um nicht in unnötig komplexe Konzepte zu geraten und Paywalls zu vermeiden.

Danach erfolgte die **individuelle Umsetzung** der Tutorials in eigene TouchDesigner-Projekte mit Modifikationen. Die Arbeiten wurden in regelmäßigen Sessions besprochen und koordiniert.

### Zentrale Herausforderungen & Lösungen

**Framerate-Synchronisation:**
- **Problem:** Beim Zusammenführen der Projekte entstanden Synchronisationsprobleme durch unterschiedliche Framerate-Einstellungen
- **Ursache:** CPU vs. GPU Bottlenecks, unterschiedliche Resolutionen, Shader-Komplexität
- **Lösung:** Resolution-Management, Cooking-Optimierung, Shader-Features minimieren

**Streaming-Lag:**
- **Problem:** Ca. 1 Sekunde Lag beim Streaming beeinträchtigt Live-Reaktivität
- **Impact:** Kritisch für Audio-Reaktivität auf der Bühne
- **Mitigation:** Optimierte Streaming-Settings und Hardware-Planung

### Verwendete Tools & Ressourcen

- **YouTube Tutorials** – Zentrale Lernressource (Qualität sehr unterschiedlich)
- **TouchDesigner 2023** – Hauptentwicklungssoftware
- **AI-Tools** – Unterstützung bei Dokumentation und Rechtschreibeprüfung


---

**→ [Ausführlicher Reflection Report mit allen Details](./REFLECTION.md)**

---
## �🔧 Aufgabenverteilung

| Aufgabe | Verantwortlich |
|---------|---|
| Individuelle Visual-Entwicklung (je 4 Visuals) | Aaron & Jan |
| Finale Projektintegration | Jan |
| Dokumentation & Reflection | Aaron |
| Live-Performance | Aaron & Jan |

### Wichtige Meilensteine

- **12. Januar:** Testing in Winterthur
- **16. Januar:** Live-Auftritt im Salzhaus

---

## 📚 Lerneffekte

### Aaron Täschler

- Grundsätzliches Verständnis für TouchDesigner's Möglichkeiten und Kapazitäten
- Wie audio-reaktive Visuals funktionieren und Audiosignale visuelle Effekte steuern
- Wichtigkeit einer sorgfältigen Tutorial-Auswahl um überkomplexe Konzepte zu vermeiden
- Praktisches Wissen über Frequency-Band-Separation und Parameter-Steuerung

### Jan Schmidt

- Erste Berühungspunkte mit TouchDesigner und dessen Audioverarbeitung
- Was cooking in diesem Kontext ist und wie zwischen verschiedenen Effekten hin und her geschalten werden kann
- Wie Pixelclouds funktionieren und wie GPU-hungrig diese sind

---

## 🐛 Bekannte Bugs & Limitationen

### 1. Framerate-Synchronisation

**Problem:** Beim Zusammenführen der Projekte entstanden Synchronisationsprobleme durch unterschiedliche Framerate-Einstellungen.

**Ursachen:**
- CPU vs. GPU Bottlenecks beeinflussen Performance unterschiedlich
- Resolution und Shader-Komplexität wirken sich stark auf Framerate aus
- Unnecessary Cooking von Nodes reduziert Performance

**Factoren die Framerate beeinflussen:**
- **Auflösung:** Höhere Auflösung = mehr Pixels = höhere GPU-Last
- **Shader-Komplexität:** Features wie Rim Lighting erhöhen Pixel-Shader-Kosten
- **Geometrie-Komplexität:** Zu viele Vertices belasten Vertex Shader
- **Lighting-Setup:** Unterschiedliche Light-Typen haben verschiedene Performance-Kosten
- **CPU-Operationen:** Python-Scripts und Cooking-Vorgänge beeinflussen CPU-Load

**Lösungsansätze:**
- Resolution reduzieren
- Shader-Features minimieren
- Cooking-Operationen optimieren
- Geometrie-Transformationen auf Object-Level durchführen

### 2. Streaming-Lag

**Problem:** Beim Streaming entsteht ein Lag von ca. 1 Sekunde.

**Impact:** Beeinträchtigt die Live-Reaktivität auf die Musik – ein kritischer Faktor für Livevisuals.

**Mitigation:** Optimierte Streaming-Settings oder Hardware-Upgrades nötig.

---

## 🎯 Tools & Ressourcen

### Verwendete Tools

- **TouchDesigner 2023** – Hauptentwicklungssoftware
- **YouTube Tutorials** – Primäre Lernressource
- **AI-Tools** – Unterstützung bei Dokumentation und Rechtschreibeprüfung
- **Custom Components** – AudioAnalysis für Frequenzband-Separation

### Tutorial-Qualität

Qualität der Tutorials war sehr unterschiedlich. Eine sorgfältige Auswahl war entscheidend, um:
- Nicht in unnötig komplexe Konzepte zu geraten
- Paywalls und proprietäre Components zu vermeiden
- Realistische Anforderungen zu berücksichtigen

---

## 📖 Weitere Informationen

Detaillierte Informationen zum Entwicklungsprozess, Herausforderungen, und Lerneffekten:

→ **[Vollständiger Reflection Report](./REFLECTION.md)**

### Projektstruktur

```
CreaTech-Visuals/
├── readme.md                           (diese Datei)
├── REFLECTION.md                       (Reflection Report)
├── Beschreibung/
│   ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.md
│   ├── Blocks_JS.md
│   ├── Prism_Instances_JS.md
│   └── Würfel_Gitter_AT.md
└── TouchDesigner/
    └── visuals/
        ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.toe
        ├── Blocks_JS.toe
        ├── Blocks_JS.2.toe
        ├── Prism_Instances_JS.toe
        ├── Würfel_Gitter_AT.toe
        ├── Würfel_Gitter_AT.1.toe
        ├── Backup/
        │   ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.1.toe
        │   ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.2.toe
        │   ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.4.toe
        │   ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.4.1.toe
        │   ├── Prism_Instances_JS.toe
        │   ├── Prism_Instances_JS.1.toe
        │   ├── Prism_Instances_JS.2.toe
        │   └── Prism_Instances_JS.3.toe
        ├── Combined/
        │   └── cookingnightmare.toe
        └── ungenutzt/
            ├── Soundwaves_AT.toe
            └── Würfel_mit_spikes_AT.toe
```

---
