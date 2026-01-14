# Reflection Report: Making Process

**Projektgruppe:** macherinne  
**Teilnehmende:** Aaron Täschler, Jan Schmidt

---

## A: Planungs- und Entwicklungsprozess

Nach dem wir uns entschieden haben, dass wir audiovisuelle Visuals machen möchten, haben wir uns aufgeteilt und unabhängig von einander je vier Tutorials nach unseren persönlichen Ansprüchen heraus gesucht. 

Wichtig war uns dabei, dass wir uns nicht übernehmen und zuerst die Tutorials bis zum Schluss schauen.
Desöfteren begegnete man nämlich Erklärungsvideos die entweder unsere Fähigkeiten masslos übersteigten oder gewisse components hinter Paywalls integrierten.

Wir arbeiteten individuell an unseren TD-Projekten und besprachen sie in den gemeinsamen Sessions in der Schule oder wo wir uns halt trafen.
---

## B: Herausforderungen, Lösungsansätze & Re-Planning

*Welche Probleme sind aufgetreten? Welche Lösungen haben wir verworfen? Wie haben wir uns angepasst?*

Aaron fiel das Verständnis von komplexeren TouchDesigner-Konzepten schwerer, deshalb hat er sich auf einfachere Tutorials konzentriert. Dieser pragmatische Ansatz war sinnvoll und ermöglichte es ihm, funktionierende Visuals zu erstellen.

Ein zentrales Problem trat beim Zusammenführen unserer beiden Projekte auf: Die unterschiedlichen Framerate-Einstellungen führten zu Synchronisationsproblemen zwischen den Elementen.

Zudem stellten wir fest, dass beim Streaming ein Lag von ca. 1 Sekunde auftritt, was bei Live Visuals besonders frustrierend ist und die Reaktivität auf die Musik beeinträchtigt.

---

## C: Aufgabenverteilung

Beide haben je vier verschiedene audiovisuelle Visuals erarbeitet. Die besten zwei Visuals von jedem wurden ausgewählt und schlussendlich in das finale Projekt übernommen.

Die weiteren Aufgaben wurden wie folgt verteilt:
- **Jan:** Zusammenführung der ausgewählten Visuals in einem finalen TouchDesigner-Projekt
- **Aaron:** Dokumentation des gesamten Projekts und des Entwicklungsprozesses

**Termine:**
- **Testing in Winterthur:** 12. Januar (beide)
- **Auftritt im Salzhaus:** 16. Januar (beide)

## D: Lerneffekte

*Was haben wir gelernt? Welche neuen Fähigkeiten haben wir erworben?*

**Aaron:**
Ein grundsätzliches Verständnis für die Möglichkeiten von TouchDesigner konnte ich mir erarbeiten – welche Optionen die Software bietet und wo ich zeitliche Investitionen tätigen müsste, falls ich damit arbeiten möchte. Ich habe gelernt, wie audio-reaktive Visuals funktionieren und wie man Signale effektiv nutzt, um visuelle Effekte zu steuern. Zudem wurde mir bewusst, dass eine sorgfältige Auswahl an Anfängertutorials wichtig ist, um nicht in unnötig komplexe Konzepte zu geraten.

**Jan:**

---

## E: Tools (insbesondere AI-Tools)

*Welche Tools haben wir verwendet? Wie haben uns AI-Tools unterstützt?*

**Hauptwerkzeug:** YouTube-Tutorials waren das zentrale Lernmedium unseres Projekts. Wir haben sie extensiv genutzt, wobei die Qualität sehr unterschiedlich ausfiel. Eine sorgfältige Auswahl der richtigen Tutorials erwies sich als entscheidend für unseren Erfolg.

**AI-Tools:** Abgesehen von der Dokumentation haben wir keine AI-Tools im Entwicklungsprozess eingesetzt. Bei der Dokumentation unterstützten uns AI-Tools bei der Ausformulierung von Gedanken und zur Rechtschreibeprüfung, um die Reflection aussagekräftig und professionell zu gestalten.

---

## F: Bekannte Bugs & Limitationen

*Gibt es bekannte Fehler oder Limitationen in unseren Implementierungen?*

### Framerate-Problem beim Zusammenführen

Das Framerate-Problem trat auf, weil unterschiedliche Framerate-Einstellungen zwischen den beiden Projekten nicht synchronized waren.

**Was beeinflusst die Framerate in TouchDesigner:**

**CPU vs. GPU Bottleneck:**
- **CPU-Bottleneck:** Tritt auf, wenn die CPU nicht schnell genug Operationen verarbeitet. Lösungen: Unnötige Cooking-Vorgänge reduzieren, Python-Scripts optimieren, Geometrie-Transformationen auf Object-Level machen statt in SOPs.
- **GPU-Bottleneck:** Hauptursachen sind Auflösung (Resolution) und Komplexität der Pixel-Shader. Lösungen: Render-Auflösung reduzieren, Overdraw minimieren, Shader-Features optimieren.

**Spezifische Faktoren:**
- **Auflösung/Resolution:** Je höher die Auflösung, desto mehr Pixels müssen berechnet werden. Reduzierung der Auflösung um die Hälfte in X/Y reduziert die Pixel-Menge auf ein Viertel.
- **Anzahl der Vertices/Geometrie:** Zu viele Vertices oder komplexe Geometrie belasten den Vertex Shader.
- **Shader-Komplexität:** Rim Lighting und andere MAT-Features erhöhen die Pixel-Shader-Kosten.
- **Lighting:** Unterschiedliche Light-Typen (Cone Light vs. Point Light) haben unterschiedliche Performance-Kosten.
- **Unnecessary Cooking:** Nodes sollten nur kochen, wenn ihre Eingaben sich ändern.

### Streaming-Lag

Beim Streaming entsteht ein Lag von ca. 1 Sekunde, was die Live-Reaktivität auf die Musik beeinträchtigt. Dies ist eine bekannte Limitation bei der Übertragung über Netzwerk und kann nur durch optimierte Streaming-Settings oder Hardware-Upgrades minimiert werden.

---
