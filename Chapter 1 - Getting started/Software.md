**STM32VL Template** https://github.com/geoffreymbrown/STM32-Template#
- GNU Tools -> Debugger (GDB), Compiler (GCC), Assembler (GAS),  Dateikonverter (objcopy), Disassembler (objdump)
	- GDB Server (Vermittler zwischen Debugger und MCU)
		- Software die es ermöglicht mit dem GNU Debugger auf stm32 board zuzugriefen 
	- sudo apt install gcc-arm-none-eabi (Ubunut repo), da **Sourcery CodeBench Lite Edition** das Projekt eingestellt hat

- ST-Link
	- zum herunterladen und debuggen von code auf den STM32VL Discovery board über USB debugger Schnittstelle (stlink)
	- interface durch reverese engineering auch für linux und macos nutzbar gemacht https://github.com/stlink-org/stlink
	- selbst kompilieren <=> sudo apt install stlink-tools
		 1. cd stlink          *# in den Quellcode-Ordner*
		 2. mkdir -p build/Release  *# Build-Ordner anlegen*
		 3. cd build/Release    *# in den Build-Ordner wechseln*
		 4. cmake -DCMAKE_BUILD_TYPE=Release ../..  *# Build-Dateien generieren*
		 5. make               * # kompilieren*
		 6. sudo make install   *# Systemweite installation (/usr/local/bin)*
		 7. sudo ldconfig       *# Bibliothekscache aktualisieren (optional)*

| ST-link tool | Zweck                                   |
| ------------ | --------------------------------------- |
| st-util      | GDB- Server für Debugging über ST-Link  |
| st-info      | Abfragen on ST-Link Geräteinfos         |
| st-trace     | Trace Daten auslesen und protokollieren |
| st-flash     | Programmieren des STM32 Chips           |
