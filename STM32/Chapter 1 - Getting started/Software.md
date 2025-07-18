|        |                                                                      |
| ------ | -------------------------------------------------------------------- |
| Linux  | Kernel (verwaltet Hardware, Speicher, ...)                           |
| Ubuntu | Betriebssystem (GNU + Linux)                                         |
| GNU    | Projekt, dass Tools bereitstellt                                     |
| Unix   | erstes Betriebssystem mit bestimmten Eigenschaften-> Basis von MacOS |
- ~~STM32 standard periperal library: https://www.st.com/en/embedded-software/stsw-stm32054.html#get-software (/home/ishak/projekte/en.stsw-stm32054_v3-6-0)~~
- **STM32VL Template** https://github.com/geoffreymbrown/STM32-Template#
 - Toolchain GNU Tools -> Debugger (GDB), Compiler (GCC), Assembler (GAS),  Dateikonverter (objcopy), Disassembler (objdump)
	- sudo apt install gcc-arm-none-eabi (Ubunut repo), da **Sourcery CodeBench Lite Edition** das Projekt eingestellt hat (toolchain von ARM Ltd.)
		- "Hinweis: »**gdb-multiarch**« wird an Stelle von »**gdb-arm-none-eabi**« gewählt"
	- GDB Server (Vermittler zwischen Debugger auf dem Host Computer und MCU)
		- Software die es ermöglicht mit dem GNU Debugger auf stm32 board zuzugreifen 
-> Systemwelt installiert

- ST-Link
	- zum herunterladen und debuggen von code auf den STM32VL Discovery board über USB debugger Schnittstelle (stlink) (Hardware)
	- interface durch reverese engineering auch für linux und macos nutzbar gemacht (software) https://github.com/stlink-org/stlink
	- selbst kompilieren <=> sudo apt install stlink-tools 
		 1. cd stlink          *# in den Quellcode-Ordner*
		 2. mkdir -p build/Release  *# Build-Ordner anlegen*
		 3. cd build/Release    *# in den Build-Ordner wechseln*
		 4. cmake -DCMAKE_BUILD_TYPE=Release ../..  *# Build-Dateien generieren*
		 5. make               * # kompilieren*
		 6. sudo make install   *# Systemweite installation (/usr/local/bin)*
		 7. sudo ldconfig       *# Bibliothekscache aktualisieren (optional)*
-> System weit installiert

| ST-link tool | Zweck                                   |
| ------------ | --------------------------------------- |
| st-util      | GDB- Server für Debugging über ST-Link  |
| st-info      | Abfragen on ST-Link Geräteinfos         |
| st-trace     | Trace Daten auslesen und protokollieren |
| st-flash     | Programmieren des STM32 Chips           |=====
![[St-LinkUndWeiteres.jpg]]
[Zur Skizze in groß](St-LinkUndWeiteres.jpg)

---

### Umstieg von SPL zu HAL + STM32CubeMX
STM32CubeMX: https://www.st.com/en/microcontrollers-microprocessors/stm32f100rb.html
Ab dem 14.06.2025 bin ich von der Standard Peripheral Library (SPL) auf die Hardware Abstraction Layer (HAL) in Kombination mit STM32CubeMX umgestiegen.

- HAL - Eine **C-Bibliothek von ST**, die eine höhere Abstraktion über die Hardware bietet.
- STM32CubeMX - Ein **grafisches Konfigurationstool**, das dir automatisch Startcode auf Basis von HAL (oder auch LL = Low Layer) generiert. */home/ishak/STM32CubeMX*
- SPL - durch HAL ersetzt


Der wichtigste Grund für den Umstieg ist, dass ich **möglichst schnell mit der praktischen Entwicklung beginnen** möchte – ohne mich anfangs zu sehr mit Low-Level-Registerdetails zu beschäftigen.  
Mit HAL und CubeMX kann ich mich auf die Logik und Funktionalität konzentrieren, statt Zeit mit manueller Initialisierung und Hardware-Konfiguration zu verlieren.

Parallel dazu arbeite ich mich **gezielt und bewusst in Bare-Metal-Programmierung ein**, z. B. anhand der Literatur von **Geoffrey Brown (Introduction to Embedded Systems with ARM Cortex-M Microcontrollers)**.