# Programmierübung: Zustände und Signale mit `ENUM` und `STRUCT` modellieren

In dieser Übung soll ein kleines TwinCAT-Programm in drei Schritten verbessert werden.  
Ziel ist es, die bisher verwendeten **einfachen Datentypen** durch **ENUM** und **STRUCT** zu ersetzen und dadurch den Code lesbarer und strukturierter zu machen.

---

## Ausgangssituation

Ein Tank wird über wenige Signale überwacht:

- `rLevel` beschreibt den aktuellen Füllstand
- `rLimit` ist ein Grenzwert
- `bValveOpen` gibt an, ob ein Ventil geöffnet ist
- `bAlarm` signalisiert einen Alarmzustand

Der aktuelle Zustand des Tanks wird im gegebenen Programm noch über eine `INT`-Variable beschrieben:

- `0` = OK
- `1` = WARNUNG
- `2` = ALARM

Diese Darstellung soll in den folgenden Teilaufgaben verbessert werden.

---

## Vorgegebener Code

Die Ausgangsbasis für diese Aufgabe ist in der Datei **`Ueb_03_050_ENUM_STRUCT.tpzip`** enthalten.

Das Projekt besteht aus:

- **`MAIN`**  
  Enthält das Hauptprogramm mit der bisherigen Tanküberwachung

- **`GVL`**  
  Kann für globale Konstanten oder Hilfsvariablen genutzt werden

Deine Aufgabe ist es, das bestehende Programm in den folgenden drei Schritten anzupassen.

---

## Teilaufgabe 1: Zustand mit `ENUM` statt `INT`

Ersetze die bisherige Zustandsvariable vom Typ `INT` durch einen passenden **ENUM-Datentyp**.

### Anforderungen

- Lege einen neuen ENUM-Datentyp **`E_TankState`** an.
- Der ENUM soll die drei Zustände enthalten:
  - `OK`
  - `WARNING`
  - `ALARM`
- Verwende den ENUM-Datentyp im Programm anstelle der Zahlenwerte `0`, `1` und `2`.
- Passe die Zuweisungen im `IF`-Block und die Auswertung im `CASE`-Statement entsprechend an.

---

## Teilaufgabe 2: Signale mit `STRUCT` bündeln

Fasse logisch zusammengehörige Signale in Strukturen zusammen.

### Anforderungen

Lege zwei Strukturdatentypen an:

#### `ST_TankIn`
Diese Struktur soll die Eingangsdaten des Tanks enthalten:

- `rLevel : REAL`
- `rLimit : REAL`

#### `ST_TankOut`
Diese Struktur soll die Ausgangs- bzw. Meldesignale enthalten:

- `bValveOpen : BOOL`
- `bAlarm : BOOL`
- `sText : STRING`

### Anpassung im Programm

- Ersetze die bisherigen Einzelvariablen durch:
  - `stIn : ST_TankIn`
  - `stOut : ST_TankOut`
- Passe alle Zugriffe im Programm auf die neue Strukturierung an.

---

## Teilaufgabe 3: `ENUM` und `STRUCT` kombinieren

Erweitere die Ausgabestruktur um die Zustandsinformation.

### Anforderungen

- Ergänze die Struktur **`ST_TankOut`** um eine weitere Membervariable:
  - `eState : E_TankState`
- Speichere den aktuellen Zustand des Tanks in `stOut.eState`.
- Nutze `stOut.eState` im `CASE`-Statement zur Zustandsauswertung.

---

## Ziel der Übung

Nach der Bearbeitung der Aufgabe solltest du:

- einen **ENUM-Datentyp** selbst anlegen und verwenden können,
- **STRUCTs** zur Bündelung zusammengehöriger Variablen einsetzen können,
- ENUM und STRUCT **kombiniert** in einem ST-Programm verwenden können,
- erkennen, wie sich durch benutzerdefinierte Datentypen die **Lesbarkeit und Struktur** eines Programms verbessern lässt.

---

## Hinweis

Bearbeite die Teilaufgaben **nacheinander**.  
Teste nach jeder Änderung, ob das Programm weiterhin fehlerfrei übersetzt werden kann.

---

## Optional

Wenn du schneller fertig bist, kannst du das Programm zusätzlich erweitern:

- Ergänze in `ST_TankOut` eine weitere BOOL-Variable `bWarningLamp`
- Diese soll **nur im Zustand `WARNING`** auf `TRUE` gesetzt werden.
