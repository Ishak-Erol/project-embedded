**USB ist ein Kommunikationsprotokoll, das die USB-Schnittstelle des Rechners nutzt, um über ein Bündel von Leitungen Daten zu senden.**

**UART ist ein Kommunikationsprotokoll, das die UART-Schnittstelle nutzt, um über eine Leitung Daten zu senden und über eine andere zu empfangen.**

---
https://support.saleae.com/logic-software/sw-installation#ubuntu-instructions
chmod +x Logic-2.4.29-linux-x64.AppImage 
Downloads/Logic-2.4.29-linux-x64.AppImage --no-sandbox
![[Pasted image 20250725171456.png]]
- capture rate to 100 Khz
- the number of samples to 1 M
- trigger condition on Serial Out to the falling arrow
---

Ab Seite 75

## 🧠 Merksatz:

> **Jeder Pin ist von Haus aus GPIO-fähig.**  
> Für alles andere (USART, I2C, SPI, etc.) muss er **umgeschaltet werden** → "Alternative Function".
---
Sowohl die CPU als auch alle Peripehrien haben eigene Register. Die Register sind beim STM32F1 32 bit breit, sodass mit einem einzigen Befehl die CPU (32 bit arm cortex kern) das ganze Register verabreiten kann. 
Register sind **Steuerbefehle für die Hardware**
## 🧠 Besser gesagt:

> **Register sind spezielle Speicherstellen, mit denen man Hardware direkt kontrolliert – durch gezieltes Setzen oder Auslesen einzelner Bits.**

---

## 📦 Vergleich: Schaltkasten

Stell dir vor:

- Jedes Register ist wie ein kleiner **Schaltkasten** in einem Haus.
    
- Die einzelnen **Bits** sind Schalter.
    
- Wenn du einen Schalter **umlegst** (Bit setzt), reagiert ein Gerät: z. B. eine Lampe geht an (LED an Pin leuchtet), ein Motor startet, usw.
st-flash --reset write build/BlinkingLights.bin 0x08000000
make

---

[[USART_register_map.pdf]]


ls /dev/ttyUSB*

sudo usermod -aG dialout $USER
sudo screen /dev/ttyUSB0 9600
