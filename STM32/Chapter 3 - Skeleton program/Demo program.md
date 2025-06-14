`int i;
`int off = 5; `

`void inc(void){ `
	`i += off;` 
`}`

i`nt main(void){ 
	`while (1) { `
		`inc(); `
	`}`
`}`

Makefile.common
`TOOLROOT=/usr/bin`
	->  verzeichnis meines toolchains (arm-none-eabi-gcc)
	
`LIBROOT=/home/ishak/projekte/en.stsw-stm32054_v3-6-0/STM32F10x_StdPeriph_Lib_V3`
	-> pfad zu STM32 standard peripheral library
	
`LDFLAGS+= -T$(LDSCRIPT) -mthumb -mcpu=cortex-m3 -nostdlib`
	-> `-nostdlib` ergänzt


`dpkg -L gcc-arm-none-eabi | grep '/usr/bin/' `
	-> gibt eine Liste der Pfade der im Paket enthaltenen Dateien aus (Listfiles), die mit /usr/bin/ beginnen

`ls /usr/bin/arm-none-eabi-*'
	-> listet alle arm tools in /usr/bin/ auf

`dpkg -S $(which gdb-multiarch)`
	-> gibt an in welchen Paketen sich Dateien befinden (which multiarch gibt pfad von multiarch)

---
## Header Dateien
Header-Dateien (mit der Endung `.h`) sind reine Textdateien, die Deklarationen enthalten. Sie enthalten keinen ausführbaren Code, sondern dienen dazu, dem Compiler Informationen über Funktionen und Datenstrukturen bereitzustellen, die an anderer Stelle (meist in einer `.c`-Datei) definiert sind. Durch das Einbinden einer Header-Datei mit `#include` kann eine Quellcodedatei diese Deklarationen verwenden.
## ⚙️ Rolle des Compilers:

`#include "gpio.h"`
`int main(void) {`
    `init_gpio();         // Funktion aus einer anderen Datei`
    `return 0;`
`}`

- **Er ersetzt `#include "gpio.h"`** durch den Inhalt der Datei `gpio.h`.
- Er **überprüft, ob `init_gpio()` gültig deklariert** ist.
- Er kompiliert `main.c` zu `main.o`, ohne zu wissen, **wo `init_gpio()` definiert ist** – das macht später der **Linker**.
---

`ishak@ishak-ThinkPad-T14-Gen-2a:~$ gdb-multiarch ./projekte/MindLab/STM32/STM32-Template/Demo/Demo.elf` 
==GNU gdb (Ubuntu 15.0.50.20240403-0ubuntu1) 15.0.50.20240403-git==
==Copyright (C) 2024 Free Software Foundation, Inc.==
==License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>==
==This is free software: you are free to change and redistribute it.==
==There is NO WARRANTY, to the extent permitted by law.==
==Type "show copying" and "show warranty" for details.==
==This GDB was configured as "x86_64-linux-gnu".==
==Type "show configuration" for configuration details.==
==For bug reporting instructions, please see:==
==<https://www.gnu.org/software/gdb/bugs/>.==
==Find the GDB manual and other documentation resources online at:==
    ==<http://www.gnu.org/software/gdb/documentation/>.==

==For help, type "help".==
==Type "apropos word" to search for commands related to "word"...==
==Reading symbols from ./projekte/MindLab/STM32/STM32-Template/Demo/Demo.elf...==
`(gdb) target extended-remote :4242`
==Remote debugging using :4242==
==0x0800038c in inc () at main.c:5==
==5	  i += off;==
`(gdb) load`
==Loading section .text, size 0x3b8 lma 0x8000000==
==Loading section .data, size 0x8 lma 0x80003b8==
==Start address 0x080001d4, load size 960==
==Transfer rate: 3 KB/sec, 480 bytes/write.==
`(gdb) print /x $sp`
==$1 = 0x20001ff0==
`(gdb) print /x $sp`
==$2 = 0x20001ff0==
`(gdb) print /x $pc`
==$3 = 0x80001d4==
`(gdb) print /x $lr`
==$5 = 0x80003a7==
`(gdb) print /x $0`  
==$7 = 0x80003a7==
`(gdb) print /x $2`
==$9 = 0x20001ff0==
`(gdb) break main.c:11`
==Haltepunkt 1 at 0x80003a2: file main.c, line 11.==
==Anmerkung: Hardware-Haltepunkte für Nur-Lesen-Adressen werden automatisch benutzt.==
`(gdb) continue`
==Continuing.==

==Breakpoint 1, main () at main.c:11==
==11	    inc();==
`(gdb) continue`
==Continuing.==

==Breakpoint 1, main () at main.c:11==
==11	    inc();==
`(gdb) delete`
==Delete all breakpoints, watchpoints, tracepoints, and catchpoints? (y or n) y==

`(gdb) break main.c:11` 
==Haltepunkt 2 at 0x80003a2: file main.c, line 11.==
`(gdb) commands`
==Type commands for breakpoint(s) 2, one per line.==
==End with a line saying just "end".==
 print i 
 continue 
 end
`(gdb) continue` 
==Continuing.==

==Breakpoint 2, main () at main.c:11==
==11	    inc();==
==$10 = 30611150==

==Breakpoint 2, main () at main.c:11==
==11	    inc();==
==$11 = 30611155==
