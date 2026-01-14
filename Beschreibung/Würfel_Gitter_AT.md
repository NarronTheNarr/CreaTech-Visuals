# Würfel_Gitter_AT

## Idee

Erstellung eines audio-reaktiven Visuellen Effekts basierend auf einem Gitter-Würfel. Das Projekt nutzt custom TouchDesigner Komponenten, um Audiovisuals mit reaktiven Parametern zu erstellen.

## Tutorial

**Audio Reactive Visuals in TouchDesigner - von Acrylicode**

**Links & Downloads:**
- **YouTube Video:** Grid Lines Texture | TouchDesigner Tutorial
- **Absolute Beginner Video:** https://www.youtube.com/watch?v=qbupH...

**Grundkonzept:**
- Verwendung von drei custom TouchDesigner Komponenten für audio-reaktive Effekte
- Setup Audio Reactive Song - automatisiert die Timeline-Anpassung an die Audiolänge
- Audio Reactive Rotation - kontinuierlich wachsende Werte (geeignet für Rotations- und Translations-Parameter)
- Audio Reactive Value - Werte mit definierten Grenzen (geeignet für Parameter mit bestimmtem Wertebereich)

## Umsetzung

### Audio Setup
1. Audio-Track in TouchDesigner importieren (z.B. von Epidemic Sound)
2. Audio Device Out anschließen für Ausgabe
3. Custom Component "Setup Audio Reactive Song" verwenden:
   - Audio CHOP in die Song-Parameter einfügen
   - Setup-Button drücken
   - Timeline wird automatisch auf die Audiolänge angepasst
   - Play Mode wird automatisch auf "Set to Timeline" gestellt

### Audio Reactive Rotation Komponente
- Gibt konstant wachsende Werte aus
- Ideal für Parameter, die kontinuierlich wachsen können (Rotation, Translation)
- **Nicht geeignet** für Skalierung (würde zu schnell aus dem Bild laufen)
- Multiplizieren mit Faktoren (z.B. 0.01, 0.03) zur Geschwindigkeitsanpassung
- Kann auf jeden Parameter angewendet werden, der normalerweise mit `abs(time.seconds)` animiert wird

### Audio Reactive Value Komponente
- Hat zwei Ausgaben:
  - **Oben:** Clamped Values (begrenzte Werte)
  - **Unten:** Raw Data (Rohdaten vom Track)
- Parameter:
  - **Gain:** Multiplikator für Ausgabewerte
  - **To Range:** Definiert obere und untere Grenze für die Ausgabewerte
- Beispiel: Noise TOP Period von 0.5 bis 1.8 animieren
- **Wichtig:** Immer die obere Null (clamped values) verwenden

## Abänderungen

- Würfel statt Sphere im Sinne unseres Projekts
- Anpassung der Verstärkung (Gain) für optimale Audio-Reaktivität
- Definition der Wertebereich (To Range) für spezifische Parameter
- Mehrfache Parameter können mit unterschiedlichen Multiplikatoren gesteuert werden

## Erfolge

- Einfache Umwandlung von statischen Visuals zu audio-reaktiven Effekten
- Automatisiertes Audio-Setup reduziert manuelle Konfiguration
- Flexible Komponenten erlauben kreative Anwendung auf verschiedenste Parameter
- Custom Komponenten reduzieren Komplexität und Wiederholungsarbeit
