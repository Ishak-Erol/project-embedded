![[Stm32f1.jpg]]
[Zum Bild in groß](Stm32f1.jpg)


> Sowohl die CPU als auch alle Peripehrien haben eigene Register. Die Register sind beim STM32F1 **32** bit breit, sodass mit einem einzigen Befehl die CPU (32 bit arm cortex kern) das ganze Register verabreiten kann. 

> #Register **sind spezielle Speicherstellen, mit denen man Hardware direkt kontrolliert – durch gezieltes Setzen oder Auslesen einzelner Bits.**

**Analogie:**
- Jedes Register ist wie ein kleiner **Schaltkasten** in einem Haus.
- Die einzelnen **Bits** sind Schalter.
- Wenn du einen Schalter **umlegst** (Bit setzt), reagiert ein Gerät: z. B. eine Lampe geht an (LED an Pin leuchtet), ein Motor startet, usw.

Register **setzen nur Steuerbits**, die wiederum **Transistoren im Chip** schalten, die den Pin elektrisch treiben.  
Alles Physische passiert **in Hardware**, der Code ändert nur die Zustände in diesen kleinen Schaltwerken.