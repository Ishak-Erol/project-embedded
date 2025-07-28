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



