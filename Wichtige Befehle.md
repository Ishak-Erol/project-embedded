`st-flash --connect-under-reset`

`st-flash read testErase.bin 0x08000000 0x4000` –› liest **16 KiB** (0x4000 Bytes) ab der Speicheradresse **0x08000000** (==Startadresse des Flash-Speichers, siehe [RM0041](file:///home/ishak/Downloads/rm0041-stm32f100xx-advanced-armbased-32bit-mcus-stmicroelectronics-1.pdf), Seite 42==) aus dem Flash des STM32 und speichert die Daten in der Datei **testErase.bin**.


`hexdump -C dump.bin | less` -› Zeigt den Inhalt der Datei **dump.bin** hexadezimal und ASCII-kodiert an, dabei wird die Ausgabe per `less` durchblätterbar gemacht.

make

find . -name "*.elf"`
st-util`
gdb-multiarch ./STM32/STM32-Template/BlinkingLight.elf`
`dpkg -L gcc-arm-none-eabi | grep '/usr/bin/' `
	-> gibt eine Liste der Pfade der im Paket enthaltenen Dateien aus (Listfiles), die mit /usr/bin/ beginnen

`ls /usr/bin/arm-none-eabi-*'
	-> listet alle arm tools in /usr/bin/ auf

`dpkg -S $(which gdb-multiarch)`
	-> gibt an in welchen Paketen sich Dateien befinden (which multiarch gibt pfad von multiarch)

Dateien
.ioc
.elf
.bin
.c
.h








telnet localhost 4444
exit
openocd -f openocd.cfg
halt
flash erase_address 0x08000000 0x20000

flash write_image /home/ishak/projekte/MindLab/STM32/STM32_CubeMX/BlinkingLightsButton/build/BlinkingLightsButton.bin 0x08000000
	reset halt



[Datasheet](file:///home/ishak/Downloads/stm32f100rb.pdf) -› Überblick über das physische Bauteil. Enthält mechanische und elektrische Informationen, Pinbelegung, Gehäusevarianten und grundlegende Eigenschaften des Mikrochips.
[Reference manual](file:///home/ishak/Downloads/rm0041-stm32f100xx-advanced-armbased-32bit-mcus-stmicroelectronics-1.pdf) -› Detaillierter als das Datasheet. Enthält die vollständige Beschreibung der Peripherie und der Register. Wichtig für das Programmieren auf Registerebene.



openocd -f interface/stlink.cfg -f target/stm32f1x.cfg
telnet localhost 4444
init
reset halt
flash banks
stm32f1x unlock 0
reset halt
flash banks
stm32f1x mass_erase 0
flash write_image erase verify build/firmware.bin 0x08000000
reset run
exit

|              |                                         |
| ------------ | --------------------------------------- |
| `init`       | Verbindung und Ziel initialisieren      |
| ST-link tool | Zweck                                   |
| st-util      | GDB- Server für Debugging über ST-Link  |
| st-info      | Abfragen on ST-Link Geräteinfos         |
| st-trace     | Trace Daten auslesen und protokollieren |
| st-flash     | Programmieren des STM32 Chips           |

|              |              |
| ------------ | ------------ |
| `reset halt` | Ziel stoppen |

|               |                              |
| ------------- | ---------------------------- |
| `flash banks` | Flash-Konfiguration anzeigen |

|                     |                       |
| ------------------- | --------------------- |
| `stm32f1x unlock 0` | Flash-Schutz aufheben |
|                     |                       |

|                         |                        |
| ----------------------- | ---------------------- |
| `stm32f1x mass_erase 0` | gesamten Flash löschen |

|                         |                                     |
| ----------------------- | ----------------------------------- |
| `flash write_image ...` | Firmware schreiben und verifizieren |

|             |                  |
| ----------- | ---------------- |
| `reset run` | Programm starten |
- **Alle Register, Peripherie, Speicher etc. werden in den Anfangszustand versetzt**
- Der **Program Counter (PC)** springt auf die Startadresse (z. B. `0x08000000` für STM32)

|        |                             |
| ------ | --------------------------- |
| `exit` | Telnet-Verbindung schließen |

---

|             |                                                            |                        |
| ----------- | ---------------------------------------------------------- | ---------------------- |
| **OpenOCD** | Verbindet PC mit dem Mikrocontroller über ST-Link/JTAG/SWD | zentraler Debug-Server |

|            |                                               |                         |
| ---------- | --------------------------------------------- | ----------------------- |
| **telnet** | Terminal-Zugang zu OpenOCDs Kommandointerface | steuert OpenOCD manuell |

|                   |                                                       |                                          |
| ----------------- | ----------------------------------------------------- | ---------------------------------------- |
| **gdb-multiarch** | Debugger für viele Architekturen (z. B. ARM Cortex-M) | verbindet sich mit OpenOCD für Debugging |

|            |                           |                                                                 |
| ---------- | ------------------------- | --------------------------------------------------------------- |
| **screen** | Serielles Terminal (UART) | verbindet sich mit dem UART des STM32 über z. B. `/dev/ttyUSB0` |
📊 Beispiel-Workflow in einem Satz:
Du **flashst mit OpenOCD**, **kontrollierst per telnet**, **debuggst mit gdb**, und **sprichst mit deinem Code per UART über screen**.

---
