|        |                                                                      |
| ------ | -------------------------------------------------------------------- |
| Linux  | Kernel (verwaltet Hardware, Speicher, ...)                           |
| Ubuntu | Betriebssystem (GNU + Linux)                                         |
| GNU    | Projekt, dass Tools bereitstellt                                     |
| Unix   | erstes Betriebssystem mit bestimmten Eigenschaften-> Basis von MacOS |
- STM32 standard periperal library: https://www.st.com/en/embedded-software/stsw-stm32054.html#get-software (/home/ishak/projekte)
- **STM32VL Template** https://github.com/geoffreymbrown/STM32-Template#
 - GNU Tools -> Debugger (GDB), Compiler (GCC), Assembler (GAS),  Dateikonverter (objcopy), Disassembler (objdump)
	- sudo apt install gcc-arm-none-eabi (Ubunut repo), da **Sourcery CodeBench Lite Edition** das Projekt eingestellt hat 
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

# BlinkingLights

`ishak@ishak-ThinkPad-T14-Gen-2a:~$ st-util`
==st-util 1.8.0-117-gdb953ea==
==2025-05-31T07:56:21 INFO common_legacy.c: NRST is not connected --> using software reset via AIRCR==
==2025-05-31T07:56:21 INFO common_legacy.c: STM32F1xx_VL_MD_LD: 8 KiB SRAM, 128 KiB flash in at least 1 KiB pages.==
==2025-05-31T07:56:21 INFO gdb-server.c: Listening at *:4242...==
`ishak@ishak-ThinkPad-T14-Gen-2a:~/projekte/MindLab$ find . -name "*.elf"`
==`./STM32/STM32-Template/BlinkingLight.elf`==
`ishak@ishak-ThinkPad-T14-Gen-2a:~/projekte/MindLab$ gdb-multiarch ./STM32/STM32-Template/BlinkingLight.elf`
==`GNU gdb (Ubuntu 15.0.50.20240403-0ubuntu1) 15.0.50.20240403-git`==
==`Copyright (C) 2024 Free Software Foundation, Inc.`==
==`License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>`==
==`This is free software: you are free to change and redistribute it.`==
==`There is NO WARRANTY, to the extent permitted by law.`==
==`Type "show copying" and "show warranty" for details.`==
==`This GDB was configured as "x86_64-linux-gnu".`==
==`Type "show configuration" for configuration details.`==
==`For bug reporting instructions, please see:`==
==`<https://www.gnu.org/software/gdb/bugs/>.`==
==`Find the GDB manual and other documentation resources online at:`==
    ==`<http://www.gnu.org/software/gdb/documentation/>.`==

==`For help, type "help".`==
==`Type "apropos word" to search for commands related to "word"...`==
==`Reading symbols from ./STM32/STM32-Template/BlinkingLight.elf...`==
`(gdb) target extended-remote :4242`
==`Remote debugging using :4242`==
==`0x080001a4 in g_pfnVectors ()`==
`(gdb) load`
==`Loading section .text, size 0x17b8 lma 0x8000000`==
==`Loading section .init, size 0xc lma 0x80017b8`==
==`Loading section .fini, size 0xc lma 0x80017c4`==
==`Loading section .data, size 0x2c lma 0x80017d0`==
==`Loading section .init_array, size 0x4 lma 0x80017fc`==
==`Loading section .fini_array, size 0x4 lma 0x8001800`==
==`Loading section .jcr, size 0x4 lma 0x8001804`==
==`Start address 0x08000208, load size 6152`==
==`Transfer rate: 6 KB/sec, 878 bytes/write.`==
`(gdb) continue` 
==`Continuing.`==
==`^C`==
==`Program received signal SIGTRAP, Trace/breakpoint trap.`==
==`0x080003d8 in Delay (nTime=250) at main.c:60`==
==`Warnung: 60	main.c: Datei oder Verzeichnis nicht gefunden`==
`(gdb) quit`
==`A debugging session is active.`==
	==`Inferior 1 [Remote target] will be killed.`==

`Trotzdem beenden? (y or n) y`

