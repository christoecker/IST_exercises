# Programmieraufgabe: Array mit variabler Länge an einen FB übergeben

## Kurzbeschreibung
In dieser Aufgabe soll ein vorgegebener Funktionsbaustein so angepasst werden, dass er **Arrays mit variabler Länge** verarbeiten kann. Dazu soll der Eingabeparameter als **offenes Array** deklariert und die gültigen Grenzen mit `LOWER_BOUND` und `UPPER_BOUND` ermittelt werden.

---

## Aufgabenstellung
Ein vorhandener Funktionsbaustein `FB_ArraySum` berechnet aktuell die Summe eines eindimensionalen Integer-Arrays mit **fest vorgegebener Länge**.

Ändere den Code des Funktionsbausteins so, dass:

1. der Eingabeparameter `aList` **ein Array mit variabler Länge** ist,
2. die Schleife **nicht mehr mit fest codierten Grenzen** arbeitet,
3. stattdessen die Funktionen `LOWER_BOUND` und `UPPER_BOUND` verwendet werden,
4. der Baustein dadurch mit unterschiedlich langen Arrays aufgerufen werden kann.

Ändere **nur den Funktionsbaustein**. Das `MAIN`-Programm dient zum Testen und soll **nicht** verändert werden.

---

## Vorgegebener Code

Die Ausgangsbasis für diese Aufgabe ist in der Datei `Ueb_03_060_Arrays.tpzip` enthalten.
Das Projekt besteht aus:

* `MAIN`: Testprogramm zur Instanziierung und Ausführung des Funktionsbausteins

* `FB_ArraySum`: Funktionsbaustein zur Berechnung der Summe aller Elemente eines `REAL`-Arrays

* `GVL`: Globale Variablenliste mit der Konstante `nLen`, über die aktuell die feste Länge des Arrays vorgegeben ist

Deine Aufgabe besteht darin, den Baustein `FB_ArraySum` so anzupassen, dass er auch Arrays variabler Länge verarbeiten kann.

### Programm `MAIN`
```iecst
PROGRAM MAIN
VAR
	// Arrays zum Testen des FBs (ggf. Länge anpassen)
	aArray1 : ARRAY[1..GVL.nLen] OF REAL := [1.1, 2.2, 3.3, 4.4, 5.5, 6.6, 7.7, 8.8, 9.9];
	aArray2 : ARRAY[0..5] OF REAL := [6.0, 5.0, 4.0, 3.0, 2.0, 1.0];
	
	// Speicher die Summe aller Elemente des Arrays
	fRes : REAL;
	// Start der Berechnung
	bRun : BOOL;
	
	// FB zum Berechnen der Summe der Arrayelemente
	fbArrSum : FB_ArraySum;
END_VAR
---------------------
fbArrSum(aList:= aArray1, bCalc:= bRun, fSum=> fRes);
```

---

## Erwartetes Verhalten
Nach der Anpassung des Funktionsbausteins sollen sowohl `aArray1` als auch `aArray2` an den Funkltionsbaustein übergeben werden können, ohne dass dafür der Wert der globalen Variablen 'GVL.nLen` geändert werden muss.

