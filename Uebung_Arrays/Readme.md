# Programmieraufgabe: Array mit variabler Länge an einen FB übergeben

## Kurzbeschreibung
In dieser Aufgabe soll ein vorgegebener Funktionsbaustein so angepasst werden, dass er **Arrays mit variabler Länge** verarbeiten kann. Dazu soll der Eingabeparameter als **offenes Array** deklariert und die gültigen Grenzen mit `LOWER_BOUND` und `UPPER_BOUND` ermittelt werden.

---

## Aufgabenstellung
Ein vorhandener Funktionsbaustein `FB_ArraySum` berechnet aktuell die Summe eines eindimensionalen Integer-Arrays mit **fest vorgegebener Länge**.

Ändere den Code des Funktionsbausteins so, dass:

1. der Eingabeparameter `arrValues` **ein Array mit variabler Länge** ist,
2. die Schleife **nicht mehr mit fest codierten Grenzen** arbeitet,
3. stattdessen die Funktionen `LOWER_BOUND` und `UPPER_BOUND` verwendet werden,
4. der Baustein dadurch mit unterschiedlich langen Arrays aufgerufen werden kann.

Ändere **nur den Funktionsbaustein**. Das `MAIN`-Programm dient zum Testen und soll **nicht** verändert werden.

---

## Vorgegebener Code

### Funktionsbaustein `FB_ArraySum`
```iecst
FUNCTION_BLOCK FB_ArraySum
VAR_INPUT
    arrValues : ARRAY[1..5] OF INT;
END_VAR
VAR_OUTPUT
    nSum : INT;
END_VAR
VAR
    i : INT;
END_VAR

nSum := 0;
FOR i := 1 TO 5 DO
    nSum := nSum + arrValues[i];
END_FOR
```

### Programm `MAIN`
```iecst
PROGRAM MAIN
VAR
    fbSumA : FB_ArraySum;
    fbSumB : FB_ArraySum;

    arrA : ARRAY[1..5] OF INT := [1, 2, 3, 4, 5];
    arrB : ARRAY[-2..2] OF INT := [10, 20, 30, 40, 50];

    nResultA : INT;
    nResultB : INT;
END_VAR

fbSumA(arrValues := arrA);
fbSumB(arrValues := arrB);

nResultA := fbSumA.nSum;
nResultB := fbSumB.nSum;
```

---

## Erwartetes Verhalten
Nach der Anpassung des Funktionsbausteins soll gelten:

- `nResultA = 15`
- `nResultB = 150`

---

## Hinweise

- Verwende für `arrValues` ein **offenes Array**.
- Ermittle die gültigen Indexgrenzen mit:
  - `LOWER_BOUND(arrValues, 1)`
  - `UPPER_BOUND(arrValues, 1)`
- Es handelt sich um ein **eindimensionales Array**, daher ist die Dimensionsnummer immer `1`.

---

## Mögliche Testfragen zur Selbstkontrolle

- Warum funktioniert der ursprüngliche FB nicht mit `arrB`?
- Welchen Wert liefert `LOWER_BOUND(arrB, 1)`?
- Welchen Wert liefert `UPPER_BOUND(arrB, 1)`?
- Warum ist die Lösung mit `LOWER_BOUND` und `UPPER_BOUND` flexibler als eine fest codierte Schleifengrenze?
