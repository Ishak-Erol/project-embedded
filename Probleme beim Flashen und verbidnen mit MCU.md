
1. **Problem beim Flashen und Verbinden:**
    
    - Ich hatte Probleme, meinen STM32F100RBT6B über ST-Link mit `st-flash` oder `st-util` zu verbinden.
        
    - Fehlermeldungen wie `LIBUSB_ERROR_PIPE`, `Failed to enter SWD mode` und `Can not connect to target` kamen immer wieder.
        
    - Manchmal half es, den Reset-Button gedrückt zu halten, aber das funktionierte nicht immer zuverlässig.
        
    - Das Flashen schlug oft mit Fehlern beim Flash-Loader fehl.
        
2. **Firmware flashen:**
    
    - Ich versuchte erst eine `.elf` Datei zu flashen, was aber nicht ging, da `st-flash` nur `.bin` oder `.hex` Dateien direkt flashen kann.
        
    - Danach wechselte ich zu einer `.bin` Datei, was besser klappte, aber ich bekam weiterhin Fehler beim Flash-Loader.
        
    - Der Versuch mit `--connect-under-reset` brachte keine Verbesserung.
        
3. **Tools und Verbindungen:**
    
    - Ich testete `openocd`, wollte den Chip entsperren, aber das schlug fehl.
        
    - Es gab Probleme mit der USB-Verbindung, vermutlich, weil mehrere Programme gleichzeitig versuchten, auf den ST-Link zuzugreifen.
        
    - Ich lernte, dass die SWD Pins (SWDIO und SWCLK) kritisch sind für Debugging und Flashen und nicht falsch belegt oder blockiert werden dürfen.
        

### Update: Wie ich das Problem gelöst habe

Ich habe das Problem letztlich gelöst, indem ich das Programm **st-utility** installiert und von dort aus den Speicher gelöscht habe. Wichtig war, dass ich dabei **den Reset-Knopf am STM32 gedrückt gehalten** habe, während ich den Speicher gelöscht habe.

So konnte ich den Chip aus einem möglichen "Blockierzustand" holen, der das Flashen vorher verhindert hat.

Ich habe das Vorgehen in einem hilfreichen YouTube-Video gefunden, das genau diesen Trick zeigt.
https://www.youtube.com/watch?v=jEz0C2bT2M0

Alternativ auch über terminal mögich:
`st-flash read testErase.bin 0x08000000 0x4000` –› liest **16 KiB** (0x4000 Bytes) ab der Speicheradresse **0x08000000** (==Startadresse des Flash-Speichers, siehe [RM0041](file:///home/ishak/Downloads/rm0041-stm32f100xx-advanced-armbased-32bit-mcus-stmicroelectronics-1.pdf), Seite 42==) aus dem Flash des STM32 und speichert die Daten in der Datei **testErase.bin**.

`hexdump -C dump.bin | less` -› Zeigt den Inhalt der Datei **dump.bin** hexadezimal und ASCII-kodiert an, dabei wird die Ausgabe per `less` durchblätterbar gemacht.

![[Pasted image 20250719122907.png]]
Wichtig: Offset Angabe springt um 0x10 Bytes -›  binär 0001 0000 -› dezimal 2 hoch 4 = 16
		--› also springt offset um 16bytes




![[Pasted image 20250718120533.png]]


![[Pasted image 20250718120733.png]]

-----------

### 🧩 **1. BOOT0 und BOOT1 – Boot-Modus bestimmen**

Beim **Reset oder Power-On** schaut der STM32 auf die Pegel von **BOOT0** und ggf. **BOOT1**, um zu entscheiden:

| BOOT1 | BOOT0 | Boot-Modus    | Startadresse (Aliasing)                             |
| ----- | ----- | ------------- | --------------------------------------------------- |
| x     | 0     | Main Flash    | Dein Programm startet                               |
| 0     | 1     | System Memory | Interner ST-Bootloader (USB, UART, etc.) wird aktiv |
| 1     | 1     | Embedded SRAM | Start aus RAM – für Debug oder Spezialfälle         |
🗝️ Das nennt man **Aliasing**: Die Adresse **0x0000_0000** zeigt temporär auf Flash, ROM oder RAM – je nach Boot-Modus.

### 🔄 **2. RESET – Neustart auslösen**

- Wenn du **RESET drückst**, hältst du die MCU im Stillstand.
    
- Beim **Loslassen** schaut die MCU auf **BOOT0/BOOT1** und wählt den Boot-Modus.
    
- Deshalb ist die **Kombination von RESET + BOOT0/BOOT1 kritisch** fürs Flashen oder Retten.


### 🔌 **3. SWD (SWDIO + SWCLK) – Für Flashen & Debuggen**

- **SWD** ist die serielle Debug-Schnittstelle (weniger Pins als JTAG).
    
- Wird z. B. vom **ST-Link** verwendet, um:
    
    - Firmware zu flashen
        
    - Variablen zu beobachten
        
    - Register live zu lesen/schreiben
        

> ⚠️ SWD funktioniert **nur**, wenn:
> 
> - Die MCU **nicht im Reset** ist
>     
> - BOOT-Modus **nicht den ST-Bootloader aktiviert**
>     
> - Dein Programm **die SWD-Pins nicht blockiert**


### ⚠️ **4. Wann funktioniert SWD nicht?**

| Zustand                           | SWD verfügbar? | Warum?                                 |
| --------------------------------- | -------------- | -------------------------------------- |
| BOOT0 = 0, normaler Start         | ✅ Ja           | Main Flash → SWD aktiv                 |
| BOOT0 = 1, BOOT1 = 0 (Bootloader) | ❌ Meist nicht  | ST-Bootloader deaktiviert oft SWD      |
| RESET wird gehalten               | ❌ Nein         | MCU ist gestoppt                       |
| Fehlerhafte Firmware              | ❌ Teilweise    | Möglicherweise SWD-Pins umkonfiguriert |
### 🛠️ **5. Praktischer Ablauf beim Flashen mit ST-Link (SWD):**

1. **BOOT0 = 0**
    
2. **RESET gedrückt → loslassen**
    
3. MCU startet aus **Main Flash**
    
4. SWD funktioniert → Flashen & Debuggen mit ST-Link
    

---

### 🛟 **6. Wenn SWD blockiert ist → Bootloader-Modus nutzen:**

1. **BOOT0 = 1, BOOT1 = 0**
    
2. RESET kurz drücken
    
3. MCU startet in den **System-Bootloader**
    
4. Du kannst über **USB oder UART** flashen (z. B. mit STM32CubeProgrammer)
    
5. Danach: BOOT0 wieder auf 0 → normaler Betrieb