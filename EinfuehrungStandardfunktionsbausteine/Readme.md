## Aufgabe: Einführung Standardfunktionsbausteine

### Worum es geht

Ein Kollege bittet dich um Hilfe, da in seinem Programm für das Demo-Rack unerwartete Probleme auftreten. 
Die Aufgabe soll dir typische Anwendungen und den Nutzen der Standardfunktionsbausteine verdeutlichen. 
Du implementierst daher die gewünschten Anforderungen mit Timern, Zählern und Triggern und kannst deine Lösung direkt in der Simulation testen.

### Programmanforderung

Ein Zähler soll zählen, wie häufig Taster gedrückt werden. 
Dabei soll der Zähler von 0-10 beschränkt sein.
Das Drücken von Taster S10 soll den Zähler um eins erhöhen, während das Loslassen von Taster S11 den Zähler um eins verringern soll. 
Beides soll über die jeweiligen Flanken der Tastersignale erkannt werden.
Der aktuelle Wert der Zählers ist auf dem Display P10 zu sehen.

Zusätzlich sollen alle LEDs in der oberen Reihe nacheinander an gehen, wenn der Schalter S10 eingeschaltet bleibt. 
Die erste LED10 soll sofort eingeschaltet werden, LED11 1s, LED12 2s und LED13 3s nach der ersten.

### Projektstand

Dein Kollege hat dir sein Programm als xml-Datei zukommen lassen. 
In diesem hat er bereits alle nötigen Variablen deklariert.
Er hat bereits die Funktionsweise der Taster implementiert, jedoch funktioniert es so nicht richtig. 
Die LEDs hat er zwar auch bereits angesteuert, jedoch entspricht seine Implementierung nicht der Anforderung.

> [!NOTE]
> Dein Kollege hat die LIMIT-Operation verwendet. Eine Erklärung findest du [hier](https://infosys.beckhoff.com/index.php?content=../content/1031/tc3_plc_intro/2528972171.html&id=). Du kannst diese Operation weiter verwenden oder dich für einen anderen Weg entscheiden.

### Arbeitsauftrag

Um folgendes hat dich dein Kollege gebeten:
1. Lade dir aus dem ILIAS die Simulation des Demo-Racks herunter, entpacke und öffne das Projekt.
2. Lösche das aktuelle MAIN-Programm im Ordner POUs der PLC_Rack und importiere dort die xml-Datei deines Kollegen.
3. Erstelle das Projekt und verknüpfe die Ein- und Ausgänge. Beachte hierbei, dass dein Kollege ggf. für einzelne Variablen einen falschen Datentyp gewählt haben könnte, um die Verknüpfung zu den Hardwaresignalen herstellen zu können. In diesem Fall musst du den Datentyp der Deklaration entsprechend korrigieren.
4. Starte das Projekt im Run-Modus, logge dich in beide SPS ein und starte sie.
5. Finde und erkläre kurz das auftretende Problem beim Zähler.
6. Verwende die bereits deklarierten Trigger und den Zähler, um das Programm nach den Anforderungen umzuschreiben. Vermeide dabei die Verwendung von bedingten Anweisungen (z.B. IF-Anweisungen).
7. Teste dein Programm.
8. Verwende anschließend die Timer, um die Anforderungen bezüglich der LEDs umzusetzen.
9. Teste dein Programm erneut.

> [!IMPORTANT]
> Dein Kollege erinnert dich daran, dass du vor dem Start des Run-Modus unter System->Echtzeit die Kerne deines Laptops einlesen und einen der isolierten Kerne auswählen solltest, damit du das Projekt ohne Probleme starten kannst.
