# Würfel_Gitter_AT

## Idee

Erstellung eines audio-reaktiven Visuellen Effekts basierend auf einem Gitter-Würfel. Das Projekt nutzt custom TouchDesigner Komponenten, um Audiovisuals mit reaktiven Parametern zu erstellen.

## Tutorial

**[Create audio reactive visuals on TouchDesigner](https://www.youtube.com/watch?v=dPXkWLHYCQk)**

**Links & Downloads:**
- **von:** Acrylicode
- **Zeigt:** Custom Audio-Reactive Komponenten, Setup-Automatisierung, Timeline-Anpassung, Parameterkontrolle nach Audio-Frequenzbändern
- **Grundkonzept:** Audio-reaktive Visuals mit custom TouchDesigner Komponenten für präzise und flexible Parametersteuerung

## Umsetzung

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

## Abänderungen

- **Sphere durch Würfel ersetzt** als Geometrie-Element
- **Nur Audio Reactive Rotation implementiert** (bis Minute 5:30 des Tutorials)
- Würfel-Parameter statt Sphere-Parameter für Translate Z und andere Transformationen
- Fokus auf kontinuierliche, zeitbasierte Animationen durch Audio

## Erfolge

- Audio-reaktive Geometrie mit automatisiertem Timeline-Setup
- Einfache Geschwindigkeit und Bewegung durch Audio-Pegel steuerbar
- Custom Komponenten reduzieren Konfigurationsaufwand
- Flexible Multiplikatoren ermöglichen schnelle Anpassung an verschiedene Audiotracks
