# 6_Würfel_mit_projizierten_Visuals_auf_Seiten_AT

## Idee

Erstellung von audiovisuellen Effekten durch Edge-Detection, Feedback-Loops und pixelierte Effekte, die auf mehrere Würfel projiziert werden und durch Parameter der Noise-Funktionen von der Musik beeinflusst werden.

## Tutorial

**[Realtime White Visuals - TouchDesigner Tutorial (Beginner Friendly!)](https://www.youtube.com/watch?v=8ABSC0gkJrU)**
- von Daniel Steenhoff  
- Zeigt: Edge TOP, Feedback-Loop und Limit TOP für pixelierte Effekte
- [TouchDesigner Download](https://derivative.ca/download)

## Umsetzung

Im Tutorial werden einfache Netzwerke mit Edge TOP, Feedback-Loops und dem Limit TOP verwendet, um pixelierte Effekte zu erzeugen. Eine Fläche wird mit mehreren Quadraten gefüllt, deren Parameter durch Noise-Funktionen beeinflusst werden. Dies erzeugt ein musikabhängiges, sich veränderndes Muster.

## Abänderungen

- Anpassung gewisser Parameter zur Optimierung des visuellen Outputs
- Projektion der Fläche auf **6 verschiedene, unterschiedlich große Würfel** statt auf einer ebenen Fläche

## Erfolge

Das Ergebnis sieht visuell sehr ansprechend aus. Für zukünftige Iterationen sollte **Instancing** verwendet werden statt die Nodes zu kopieren, um die Performance zu verbessern und die Wartbarkeit zu erhöhen.
