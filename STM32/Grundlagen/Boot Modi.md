![[Pasted image 20250718120733.png]]

-----------

### **1. BOOT0 und BOOT1 – Boot-Modus bestimmen**

Beim **Reset oder Power-On** schaut der STM32 auf die Pegel von **BOOT0** und ggf. **BOOT1**, um zu entscheiden:


### **2. RESET – Neustart auslösen**

- Wenn du **RESET drückst**, hältst du die MCU im Stillstand.
- Beim **Loslassen** schaut die MCU auf **BOOT0/BOOT1** und wählt den Boot-Modus


### **3. SWD (SWDIO + SWCLK) – Für Flashen & Debuggen**

- **SWD** ist die serielle Debug-Schnittstelle (weniger Pins als JTAG)- siehe [[Flash Programming]]

> ⚠️ SWD funktioniert **nur**, wenn:
> 
> - Die MCU **nicht im Reset** ist
> - BOOT-Modus **nicht den ST-Bootloader aktiviert**
> - Dein Programm **die SWD-Pins nicht blockiert!!!!!!!**


### **4. Wann funktioniert SWD nicht?**

| Zustand                           | SWD verfügbar? | Warum?                                 |
| --------------------------------- | -------------- | -------------------------------------- |
| BOOT0 = 0, normaler Start         | ✅ Ja           | Main Flash → SWD aktiv                 |
| BOOT0 = 1, BOOT1 = 0 (Bootloader) | ❌ Meist nicht  | ST-Bootloader deaktiviert oft SWD      |
| RESET wird gehalten               | ❌ Nein         | MCU ist gestoppt                       |
| Fehlerhafte Firmware              | ❌ Teilweise    | Möglicherweise SWD-Pins umkonfiguriert |
### **5. Praktischer Ablauf beim Flashen mit ST-Link (SWD):**

1. **BOOT0 = 0**
2. **RESET gedrückt → loslassen**
3. MCU startet aus **Main Flash**
4. SWD funktioniert → Flashen & Debuggen mit ST-Link
    

---

### **6. Wenn SWD blockiert ist → Bootloader-Modus nutzen:**

1. **BOOT0 = 1, BOOT1 = 0**
2. RESET kurz drücken
3. MCU startet in den **System-Bootloader**
4. Du kannst über **USB oder UART** flashen (z. B. mit STM32CubeProgrammer)
5. Danach: BOOT0 wieder auf 0 → normaler Betrieb