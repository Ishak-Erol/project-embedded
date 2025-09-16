- 128x160 resolution
- 12-bit/pixel: RGB=(444) 
- 16-bit/pixel: RGB=(565) --> geringere datenmenge und ausreichend auf kleinem display
- 18-bit/pixel: RGB=(666)
![[Pasted image 20250903184101.png]]
- uses spi serial bus

controler, lcd panel, display ram

1. initilize controller
2. set ddrawing rectangle
3. write color to rectagnel

![[Pasted image 20250903202317.png]]

![[Pasted image 20250903202813.png]]

![[Pasted image 20250903203725.png]]





# ST7735S – Verhalten bei Breaks

## 1. RESX (Reset, aktiv LOW)
- Globaler Reset des Controllers
- Unterbricht Übertragung vollständig
- Alle vorherigen Befehle/Parameter **werden verworfen**
- Chip kehrt in Power-On-Reset-Zustand zurück
- **Init-Sequenz muss komplett neu gesendet werden**

**Beispiel:**
- Befehl `0x2A` (Column Address Set, 4 Parameter)
- Nach 2 Parametern → RESX-Puls
- Ergebnis: Alle Parameter verworfen, Init neu nötig
![[Pasted image 20250904084237.png]]

---

## 2. CSX (Chip Select, aktiv LOW)
- Steuert nur SPI-Interface, kein Reset
- Wenn HIGH vor Ende eines Bytes → **nur dieses Byte verworfen**
- Bereits übertragene Bytes/Parameter bleiben gültig
- Danach kann Byte erneut gesendet oder mit nächstem fortgefahren werden
![[Pasted image 20250904084253.png]]

**Beispiel:**
- Befehl `0x2A` (Column Address Set, 4 Parameter)
- Param1 (0x00) OK
- Param2 (0x10) OK
- Param3 Übertragung abgebrochen → verworfen
- Ergebnis: Param1+2 gespeichert, Param3 nochmal senden

---

## 3. Break bei Multi-Parameter-Befehlen
- Wenn Befehl mehrere Parameter erwartet und Abbruch **nicht beim letzten** Parameter passiert:
  - Bereits gesendete Parameter bleiben gültig
  - Abgebrochener Parameter wird verworfen
  - Interface ist bereit, den nächsten Befehl zu empfangen

**Beispiel:**
- Befehl `0x2A` (4 Parameter)
- Param1 (0x00) OK  
- Param2 (0x10) OK  
- Abbruch bei Param3 → verworfen  
- Neuer Befehl `0x2B` wird gesendet  
- Ergebnis: Param1+2 gespeichert, Param3+4 bleiben alte Werte

---

## 4. Neuer Befehl mitten in Parametern
- Wenn während eines Befehls (mit mehreren Parametern) ein **anderer Befehl** gesendet wird:
  - Bereits gesendete Parameter bleiben gespeichert
  - Fehlende Parameter behalten ihren alten Wert

**Beispiel:**
- `0x2A` (Column Address Set, 4 Parameter)
- Param1 (0x00) OK  
- Param2 (0x10) OK  
- Statt Param3 → neuer Befehl `0x29` (Display ON)  
- Ergebnis: Param1+2 gespeichert, Param3+4 bleiben alte Werte


# ST7735S – Data Transfer: Pause vs. Break

## Pause
- **CSX HIGH nach komplettem Byte**
- Übertragung kann später fortgesetzt werden
- 4 Fälle möglich:
  1. Command → Pause → Command
  2. Command → Pause → Parameter
  3. Parameter → Pause → Command
  4. Parameter → Pause → Parameter
![[Pasted image 20250904084654.png]]

## Break
- **CSX HIGH mitten im Byte**
- Aktuelles Byte wird verworfen
- Interface wartet auf neuen Befehl/Parameter


# ST7735S – Pixel zeichnen Ablauf

## 1️⃣ Initialize Controller
- Sende Initialisierungs-Befehle (nur einmal)
- Beispiel SLEEP_OUT, MADCTL, CASET/RASET, RAMWR

## 2️⃣ Set Drawing Rectangle (Fenster)
- Legt Spalten/Zeilen fest, in die Pixel geschrieben werden


## 3️⃣ Write Color to Rectangle
- Memory Write → danach nur noch Pixel-Daten

![[Pasted image 20250904111133.png]]

![[Pasted image 20250904111230.png]]
![[Pasted image 20250904111332.png]]
![[Pasted image 20250904112135.png]]
