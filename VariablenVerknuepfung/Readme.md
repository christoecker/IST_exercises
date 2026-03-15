## Aufgabe: Testen der Funktionen der Simulation

### Worum es geht
Die Simulation des Racks soll getestet werden. Es wurden Änderungen an den LEDs (1), dem Motor (2) und der Waage (3) vorgenommen und nun ist es deine Aufgabe zu testen, ob alles noch einwandfrei funktioniert. 
Die Aufgabe soll dir den Nutzen von globalen Variablenlisten zeigen. 
Zudem lernst du das Verknüpfen von Variablen und wiederholst bereits Gelerntes aus der Lehrveranstaltung.

### Projektanforderungen
Die Testung der Funktionen soll übersichtlich gestaltet werden. Aus diesem Grund wurde entschieden, dass das Testprojekt drei Programme beinhalten soll. Folgendes soll implementiert werden:

- Programm `BLINK`: Wenn Schalter S10 gedrückt wird, sollen die LEDs anfangen in unterschiedlichen Rythmen zu blinken.
- Programm `MOTOR`: Wenn Schalter S11 gedrückt wird, soll der Motor mit einer Geschwindigkeit von 1000 eingeschaltet werden.
- Programm `WAAGE`: Das gemessene Gewicht soll auf dem Display P10 ausgegeben werden. Wenn der Schalter S12 gedrückt wird, soll die Tara-Funktion ausgeführt werden.

Die Schalter und die LEDs sollen durch zwei Arrays wie folgt deklariert werden:
```
bSchalter 	AT%I* 	: ARRAY [1..7] OF BOOL;
bLEDs 	    AT%Q* 	: ARRAY [1..7] OF BOOL;
```
Dir ist frei überlassen, wie du die restlichen Variablen deklarierst und, ob du eine globale Variablenliste anlegst. Allerdings sollen wenn dann so wenig Variablen wie möglich in dieser Liste stehen.

### Vorgehen
1. Lade dir aus dem ILIAS die Rack-Simulation herunter und öffne sie.
2. Lösche die MAIN in der PLC_Rack.
3. Erstelle die drei Programme mit nötigen Ein- und Ausgängen und Hilfsvariablen.
4. Implementiere die angeforderten Funktionsweisen der Programme.

> [!IMPORTANT]
> Damit die neuen Programme auch ausgeführt werden, müssen sie einer Taskreferenz zugeordnet werden. Das kannst du machen, indem du ein Programm im Projektmappen-Explorer per Drag & Drop in die bereits vorhandene Taskrefrenz ziehst.

4. Erstelle dein Projekt.
5. Verknüpfe die Ein- und Ausgänge.
6. Aktiviere die Konfiguration und starte den Run-Modus.
7. Logge dich in beide SPS ein und starte sie.
8. Teste, ob dein Projekt richtig funktioniert.

> [!TIP]
> Im Dokument `Arbeiten mit dem Demo-Rack` im ILIAS findest du in Kapitel 8.2 eine Übersicht zu den Variablen in der Simulation.
> Ebenfalls findest du dort in Kapitel 6.1 ein Beispiel für ein Blinklicht, das du leicht adaptiert übernehmen könntest.
> Auch der Motor und die Waage werden in den folgenden Beispielen des Dokuments erklärt.

### Teste deine Lösung
Deine Lösung ist dann richtig, wenn:

- alle LEDs anfangen zu blinken, wenn du den Schalter S10 einschaltest. Scheinbar ist die LED S17 falsch programmiert.
- der Motor sich anfängt zu drehen, wenn du den Schalter S11 einschaltest.
- der Wert 21 auf dem Display P10 steht, wenn du das rote Gewicht drauf stellst.
- der Wert 26 auf dem Display P10 steht, wenn du das schwarze Gewicht drauf stellst.
- das setzen der Tara-Funktion durch den Schalter S12 keine Auswirkung auf das Gewicht hat. Scheinbar ist das falsch programmiert worden. Prüfe trotzdem, ob das Schalten des Schalters den Ausgang Tara auf TRUE setzt.
