# SineScore

Mathematische Rhythmus- und Notenquantisierung via Sinuswellen-Ableitungen

## 1. Einleitung und Motivation
Traditionelle Notationssysteme und digitale Audio-Workstations (DAWs) trennen mathematische Signalverarbeitung (wie Oszillatoren und Wellenformen) oft strikt von der symbolischen Notenkomposition. Dieses Idea Paper beschreibt einen hybriden Ansatz: Die Phasenlage und die lokale Steigung (Ableitung) einer Sinuskurve werden direkt zur Bestimmung von Notenlängen und -geschwindigkeiten genutzt, um organische, mathematisch fundierte Rhythmen zu erzeugen.

## 2. Kernkonzept: Steigungsbasierte Notenquantisierung
Das System koppelt die Rhythmik an die mathematischen Eigenschaften einer Sinuskurve f(t) = \sin(t):
 * **Extrema (Höhe- und Tiefpunkte):** An diesen Punkten ist die Ableitung (Steigung) gleich null (\cos(t) = 0). Diese stabilen Zonen werden genutzt, um **lange Noten** (z. B. Halbe Noten) zu triggern.
 * **Flanken (Nulldurchgänge):** Hier ist die Steigung maximal. Diese Bereiche erzeugen **schnelle, kurze Noten** (z. B. Achtelnoten).
 * **Grid-Synchronisation:** Um ein Verrutschen des Takts zu verhindern, rasten alle Noten-Events auf einem festen, quantisierten Takt-Raster ein. Die Sinuskurve selbst passt sich dynamisch an, wenn sich das Tempo ändert.
## 3. System-Architektur & Modi
Die Implementierung erfolgt über eine modulare Software-Struktur mit zwei zentralen Betriebsmodi:

### Modus 1: Programmatische Partiturerstellung (music21)
 * Berechnet die Notenwerte basierend auf den Amplituden- und Steigungswerten.
 * Exportiert die Daten direkt in eine strukturierte Partitur oder MIDI-Datei über die Python-Bibliothek music21.

### Modus 2: Dynamische BPM-Anpassung & Audio-Analyse
 * **Automatischer Modus:** Analysiert hochgeladene Audiodateien (MP3, WAV) mittels librosa auf deren Transienten und das Tempo, um die BPM-Zahl zu ermitteln.
 * **Manueller Override:** Erlaubt dem Nutzer die direkte Eingabe einer festen BPM-Zahl, welche die Audio-Analyse überschreibt und die Frequenz der Sinuskurve sofort skaliert.

## 4. Visualisierung der Architektur
Im Folgenden ist der visuelle Entwurf des Noten-Grids im Zusammenspiel mit der Sinuskurve eingebunden:
```text
[ Platzhalter für das generierte Bild / Data-URI ]
data:image/jpeg;base64,/9j/4AAQSkZJRgABAQEASABIAAD/4QBaRXhpZgAATU0AKgAAAAgABAEaAAUAAAABAAAAPgEbAAUAAAABAAAARgEoAAMAAAABAAIAAAExAAIAAAARAAAATgAAAAAyMDE5OjEwOjAyIDEyOjM0OjU2AAAAAABgAAAAAQAAAGAAAAAB... [gekürzt für das Paper]

```
## 5. Fazit und Ausblick
Durch die direkte mathematische Kopplung von Signalverarbeitung und Notensatz entsteht ein intuitives Werkzeug für experimentelle Kompositionen und generative Musik. Zukünftige Erweiterungen könnten die Einbindung von MIDI-Live-Eingaben sowie die direkte Synthese der Noten als Sound-Waves umfassen.
