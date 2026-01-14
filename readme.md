# CreaTech-Visuals – Audiovisuelle Livevisuals mit TouchDesigner

**Projektgruppe:** macherinne  
**Teilnehmende:** Aaron Täschler, Jan Schmidt  
**Semester:** HS 2025  
**Auftritt:** 16. Januar 2026 (Salzhaus, Winterthur)

---

## 📋 Projektabsicht

- [6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT](Beschreibung/6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.md)
- [Würfel_Gitter_AT](Beschreibung/Würfel_Gitter_AT.md)
- [Prism_Insctances_JS](TouchDesigner/visuals/Prism_Instances_JS.toe)
- [Platzhalter File 4]

### Finale Visuals

1. **[6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT](./Beschreibung/6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.md)** – Projection Mapping mit Audio-Reaktivität
2. **[Würfel_Gitter_AT](./Beschreibung/Würfel_Gitter_AT.md)** – Audio-reaktive Gitter-Würfel Effekte

---

## 🛠️ Technologie & Setup

- **Software:** TouchDesigner 2025 (Non-Commercial)
- **Betriebssystem:** Windows
- **Audio-Input:** Unterstützung für externe Audio-Quellen
- **Zusätzliche Komponenten:** Custom AudioAnalysis Components für Frequenzband-Separation

### Systemanforderungen

- **GPU:** Dedizierte Grafikkarte erforderlich (für optimale Performance)
- **CPU:** Multi-Core Prozessor empfohlen
- **RAM:** Mindestens 8GB
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

**Konzept:** Audio-reaktive Grid-Effekte auf Würfel-Struktur

**Umsetzung:**
- **Audio Setup:** Standard Audio-Import mit automatischer Timeline-Anpassung
- **Komponenten:**
  - Setup Audio Reactive Song (automatisiert Timeline-Anpassung)
  - Audio Reactive Rotation (kontinuierlich wachsende Werte für Rotationen)
  - Audio Reactive Value (Werte mit definierten Grenzen)
- **Effekte:** Gitter-basierte Visualisierung mit Noise-Funktionen

**Basis-Tutorial:** Audio Reactive Visuals in TouchDesigner von Acrylicode

**Spezifische Konfiguration:**
- Audio CHOP in Song-Parameter integriert
- Automation der Timeline auf Audiolänge
- Audio Reactive Value mit Gain und Range-Parametern konfiguriert

---

## 🔧 Aufgabenverteilung

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

[Wird ergänzt]

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

- **TouchDesigner 2025** – Hauptentwicklungssoftware
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
│   └── Würfel_Gitter_AT.md
└── TouchDesigner/
    ├── attachements/
    └── visuals/
        ├── 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT.toe
        ├── Würfel_Gitter_AT.toe
        └── Backup/ & ungenutzt/
```

---

## 📞 Kontakt & Lizenz

**Projekt:** FH Graubünden CreaTech  
**Lizenz:** [Zu definieren]  
**Kontakt:** aaron.taeschler@fh-graubuenden.ch, jan.schmidt@fh-graubuenden.ch

---

*Letzte Aktualisierung: Januar 2026*
