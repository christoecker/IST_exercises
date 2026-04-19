# Programmierübung: Ablaufsteuerung „Sackabfüllung“

## Systembeschreibung

In einer Abfüllanlage werden Säcke automatisch mit einem Schüttgut befüllt.  
Die Steuerung soll sicherstellen, dass:

- ein vorhandener Sack erkannt wird
- die Befüllung zunächst mit hoher Geschwindigkeit erfolgt
- kurz vor Erreichen des Zielgewichts die Füllgeschwindigkeit reduziert wird
- der Sack nach Erreichen des Zielgewichts nicht weiter befüllt wird

Das Abfüllventil kann dabei stufenlos angesteuert werden:
- `1.0` → vollständig geöffnet (schnelle Befüllung)
- `0.2` → teilweise geöffnet (reduzierter Volumenstrom für präzise Befüllung)
- `0.0` → geschlossen

---

## Gegebene Implementierung

Eine erste Implementierung ist bereits vorgegeben. Diese findest du auch in dem Projekt-Archiv `Ueb04_020_SchrittketteAbfuellung.tpzip.

### Programm `MAIN`
```iecst
PROGRAM MAIN
VAR
    // Eingänge
    bBagPresent      : BOOL;   // Sack vorhanden
    rWeight          : REAL;   // aktuelles Gewicht

    // Parameter
    rPreWeight       : REAL := 8.0;   // Umschaltpunkt auf langsam
    rTargetWeight    : REAL := 10.0;  // Zielgewicht

    // Ausgänge
    rValveCmd        : REAL;   // 0.0 ... 1.0 (Ventilöffnung)
END_VAR
---------------------
// Ablaufsteuerung unter Verwendung von IF ... THEN ... ELSE
IF NOT bBagPresent THEN
    // IDLE
    rValveCmd := 0.0;

ELSIF rWeight < rPreWeight THEN
    // FILL_FAST
    rValveCmd := 1.0;

ELSIF rWeight < rTargetWeight THEN
    // FILL_SLOW
    rValveCmd := 0.2;

ELSE
    // Sack voll -> zurück in IDLE
    rValveCmd := 0.0;

END_IF;
```

Diese Steuerung arbeitet **ohne Zustandsvariable** und nutzt ausschließlich eine `IF-THEN-ELSE`-Struktur zur Ableitung des Systemverhaltens aus dem aktuellen Gewicht.

---

## Aufgabenstellung

### **1. Analyse der gegebenen Implementierung**

Erläutere, warum die vorliegende Implementierung mit `IF-THEN-ELSE` für die Abbildung einer Ablaufsteuerung (Schrittkette) **ungeeignet** ist. Gehe dabei insbesondere auf folgende Aspekte ein:
- fehlende explizite Zustände
- mangelnde Erweiterbarkeit
- fehlende klare Trennung von Ablauf und Bedingungen

---

### **2. Umsetzung mit Zustandsvariable (CASE-OF)**

Überführe die gegebene Implementierung in eine **zustandsbasierte Ablaufsteuerung**:

- Erstelle einen **ENUM-Datentyp** für die Zustände (z. B. `IDLE`, `FILL_FAST`, `FILL_SLOW`)
- Implementiere die Steuerung mithilfe einer **CASE-OF-Struktur**
- Verwende eine Zustandsvariable zur Steuerung des Ablaufs
- Bilde die Zustandsübergänge explizit im Code ab

---

### **3. Erweiterung der Ablaufsteuerung**

#### **3a. Erweiterung um zusätzliche Zustände**

Erweitere die Steuerung um die Zustände `SETTLING` und `RELEASE` und definiere die Zustandsübergänge wie folgt:

- **Übergang von `FILL_SLOW` nach `SETTLING`**  erfolgt, wenn das Zielgewicht erreicht oder überschritten wird (`rWeight >= rTargetWeight`).

- **Verhalten in `SETTLING`:**  Das Ventil ist geschlossen (`rValveCmd := 0.0`). Zusätzlich wird ein Timer gestartet, der eine kurze Beruhigungszeit (z. B. 2 Sekunden) abbildet.

- **Übergang von `SETTLING` nach `RELEASE`** erfolgt, wenn die Beruhigungszeit abgelaufen ist (Timer abgelaufen).

- **Verhalten in `RELEASE`:** Der Sack wird freigegeben bzw. abtransportiert (z. B. durch ein Förderband). In dem Zustand wartet die Steuereung nur darauf, dass kein Sack mehr in der Abfüllstation vorhanden ist.

- **Übergang von `RELEASE` nach `IDLE`** erfolgt, wenn kein Sack mehr erkannt wird (`NOT bBagPresent`).

Passe die Ablaufsteuerung entsprechend an und erweitere deine Implementierung.

---

#### **3b. Erweiterung um einen zusätzlichen Zustandsübergang**

Ergänze im Zustand `SETTLING` einen weiteren möglichen Zustandsübergang:

- Wechsel in den Zustand `RELEASE`, wenn das Gewicht im zulässigen Bereich liegt  
- Wechsel zurück in den Zustand `FILL_SLOW`, wenn das Gewicht noch unterhalb des Zielgewichts liegt  

Damit besitzt der Zustand `SETTLING` zwei mögliche Folgezustände. Passe die Implementierung entsprechend an.

---

## Lernziel

Du lernst:
- den Unterschied zwischen zustandsloser und zustandsbasierter Implementierung
- den Einsatz von `ENUM` und `CASE-OF` zur Modellierung von Ablaufsteuerungen
- die strukturierte Erweiterung einer bestehenden Steuerungslogik