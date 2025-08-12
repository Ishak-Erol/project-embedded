|        |                                                                      |
| ------ | -------------------------------------------------------------------- |
| Linux  | Kernel (verwaltet Hardware, Speicher, ...)                           |
| Ubuntu | Betriebssystem (GNU + Linux)                                         |
| GNU    | Projekt, dass Tools bereitstellt                                     |
| Unix   | erstes Betriebssystem mit bestimmten Eigenschaften-> Basis von MacOS |

---

![[St-LinkUndWeiteres.jpg]]
[Zur Skizze in groß](St-LinkUndWeiteres.jpg)

---
**STM32 standard periperal library:** https://www.st.com/en/embedded-software/stsw-stm32054.html#get-software  ACHTUNG:([[Abweichungen#Umstieg von SPL zu HAL + STM32CubeMX| Ersetzt]])

**Toolchain (GNU Tools)**
	- Debugger (GDB)
	- Compiler (GCC)
	- Assembler (GAS),
	- Dateikonverter (objcopy)
	- Disassembler (objdump)
**Installation**:
	 `sudo apt install gcc-arm-none-eabi (Ubunut repo)` 
	 
**gdb-multiarch**« wird an Stelle von »**gdb-arm-none-eabi**« gewählt"

| **gdb-multiarch** | Debugger für viele Architekturen (z. B. ARM Cortex-M) | verbindet sich mit OpenOCD für Debugging |
| ----------------- | ----------------------------------------------------- | ---------------------------------------- |

**ST-Link GDB server** ([[Abweichungen#Ersatz von ST-Link GDB Server durch OpenOCD| Änderungen]])
- Wird genutzt zum **Herunterladen** (Flashen) und **Debuggen** von Code auf STM32-Boards
- Kommuniziert über die **USB-Debug-Schnittstelle** des **ST-LINK-Hardwareadapters** (z. B. auf dem STM32VL Discovery Board integriert)
- Ursprünglich nur für Windows verfügbar, durch **Reverse Engineering** und Community-Tools (z. B. `stlink`-Projekt) auch unter **Linux** und **macOS** nutzbar
    	
- **GDB Server** (Vermittler zwischen Debugger auf dem Host Computer und MCU)
		->Software die es ermöglicht mit dem GNU Debugger auf stm32 board zuzugreifen (auch nötig zum flashen)

