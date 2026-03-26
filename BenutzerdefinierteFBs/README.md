## Aufgabe: Programmierung benutzerdefinierter Funktionsbausteine

### Worum es geht

In dieser Aufgabenstellung soll ein Teil einer Anlagensteuerung programmiert werden. 
Für die zwei benötigten Motoren gibt es noch keine Implementierung, daher sind benutzerdefinierte Funktionsbausteine zu programmieren. 
Hierbei soll der Nutzen von solchen Bausteinen verdeutlicht werden.

### Anforderungen

Du sollst einen Funktionsbaustein programmieren, welcher einen der Motoren steuern kann.
Eine bedienende Person kann über ein Benutzerinterface Variablen aus dem Main-Programm lesen und schreiben und so Eingänge des FBs schreiben und Ausgänge lesen.
Zur Ansteuerung muss der Motor zunächst von einer bedienenden Person freigegeben werden. Dies soll über eine Eingangsvariable des Typs Bool passieren.
Über eine manuelle Eingabe der bedienenden Person soll auch die Soll-Geschwindigkeit des Motors übergeben werden können.
Dabei ist in der Implementierung des FBs darauf zu achten, dass der Motor nur Geschwindigkeiten in den Grenzen von 0 bis 100 annehmen kann, anderenfalls würde er Schaden nehmen.
Die Ist-Geschwindigkeit soll dann als Ausgang des FBs übergeben werden.
Der Motor darf zudem nur 10 Sekunden am Stück laufen und muss dann eine Pause von mindestens 5 Sekunden machen, damit er nicht überhitzt. Nutze dazu Timer als interne Variablen des FBs.

### Aufgabenstellung

1. Implementiere den FB für den Motor mit den genannten Anforderungen.
2. Instanziere den ersten Motor über den implementierden FB in dem Main-Programm. Dekraliere Hilfsvariablen, um den Motor zu testen und prüfe, ob die Anforderungen erfüllt werden.
3. Instanziiere den zweiten Motor ebenfalls mit diesem FB im Main-Programm und teste, ob die Motoren unabhängig voneinander funktionieren.
4. Der zweite Motor soll nun doch andere Spezifikationen haben und kann zusätzlich auch Rückwärts drehen. Kopiere den bestehenden Motor-FB und ergänze eine Variable im Ein- und Ausgang, welche die Drehrichtung angibt.
5. Teste die Funktionsweise und prüfe, ob die Anforderungen erfüllt werden.
