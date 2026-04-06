# Vergleich der Implementierung in ST, FUP, LD und CFC

## Kurzvorstellung des Beispiels

In diesem Verzeichnis wird eine kleine Förderbandsteuerung in verschiedenen Programmiersprachen umgesetzt. Das Beispiel ist so gewählt, dass es überschaubar bleibt und sich dennoch gut eignet, um typische Eigenschaften textueller und grafischer SPS-Sprachen zu vergleichen.

Die Steuerung arbeitet mit den Signalen `bStart`, `bStop` und `bFault`. Nach einem Startbefehl soll das Förderband laufen, solange kein Fehler anliegt. Wird gestoppt, soll der Motor nicht sofort abschalten, sondern noch für **3 Sekunden nachlaufen**. Tritt dagegen ein Fehler auf, muss der Motor **unverzüglich** abgeschaltet werden.

Zur Realisierung werden ein **SR-Speicher** für den Fahrbefehl und ein **TOF-Baustein** für die Ausschaltverzögerung verwendet. Damit enthält das Beispiel sowohl logische Verknüpfungen als auch den Aufruf von Standardfunktionsbausteinen.

## Inhalt dieses Verzeichnisses

Die Implementierung der Steuerung ist jeweils in einem eigenen Funktionsbaustein enthalten:

- `FB_ConveyorCtrl_ST` – Umsetzung in **Structured Text (ST)**
- `FB_ConveyorCtrl_FBD` – Umsetzung in **Funktionsplan (FUP)** mit mehreren Netzwerken
- `FB_ConveyorCtrl_FBD2` – Umsetzung in **Funktionsplan (FUP)** in nur einem Netzwerk
- `FB_ConveyorCtrl_LD` – Umsetzung in **Kontaktplan / Ladder Diagram (LD)**
- `FB_ConveyorCtrl_CFC` – Umsetzung in **Continuous Function Chart (CFC)**

Zusätzlich enthält das Verzeichnis eine **`.tnzip`-Datei** mit dem zugehörigen TwinCAT-SPS-Projekt.

## Ziel des Vergleichs

An dem Beispiel lässt sich gut erkennen,

- wie dieselbe Steuerungsaufgabe in unterschiedlichen Sprachen dargestellt wird,
- welche Sprache besonders kompakt oder besonders anschaulich ist,
- und wie sich grafische und textuelle Darstellungen hinsichtlich Lesbarkeit und Nachvollziehbarkeit unterscheiden.

## Funktion der Steuerung

Die Steuerung lässt sich vereinfacht wie folgt beschreiben:

1. Mit `bStart` wird ein Fahrbefehl gesetzt, sofern kein Fehler anliegt.
2. Mit `bStop` oder `bFault` wird der gespeicherte Fahrbefehl zurückgesetzt.
3. Beim Stoppen bleibt der Motor über eine Ausschaltverzögerung noch **3 Sekunden** aktiv.
4. Bei `bFault` wird der Motor unabhängig vom Nachlauf sofort abgeschaltet.

## Test der Funktionsbausteine

Zum Testen der unterschiedlichen Implementierungen ist im Projekt ein gemeinsames `MAIN`-Programm enthalten. Darin wird jeweils genau ein der Funktionsbausteine instanziiert. Über den Typ der Variable `fbCtrl` kann ausgewählt werden, welche Variante getestet werden soll, z. B. `FB_ConveyorCtrl_ST`, `FB_ConveyorCtrl_FUP`, `FB_ConveyorCtrl_LD` oder `FB_ConveyorCtrl_CFC`.

Die Signale `bStart`, `bStop` und `bFault` können anschließend im Online-Modus manuell gesetzt werden, um das Verhalten der Steuerung zu simulieren. Das Ausgangssignal `bMotor` zeigt dabei, ob der Motor eingeschaltet ist. Auf diese Weise lässt sich prüfen, ob alle Implementierungen funktional gleich arbeiten und insbesondere das Starten, Stoppen, die Ausschaltverzögerung sowie das Verhalten im Fehlerfall korrekt umgesetzt sind.

## Hinweis

Die verschiedenen Implementierungen verfolgen dieselbe Funktion, können sich aber in ihrer Darstellung und internen Struktur unterscheiden. Genau diese Unterschiede sollen mit dem Beispiel sichtbar gemacht werden.
