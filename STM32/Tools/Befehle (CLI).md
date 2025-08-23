| `reset halt` | Ziel stoppen |
| ------------ | ------------ |

| `flash banks` | Flash-Konfiguration anzeigen |
| ------------- | ---------------------------- |

| `stm32f1x unlock 0` | Flash-Schutz aufheben |
| ------------------- | --------------------- |

| `stm32f1x mass_erase 0` | gesamten Flash löschen |
| ----------------------- | ---------------------- |

| `flash write_image ...` | Firmware schreiben und verifizieren |
| ----------------------- | ----------------------------------- |

| `reset run` | Programm starten |
| ----------- | ---------------- |
**Alle Register, Peripherie, Speicher etc. werden in den Anfangszustand versetzt**
- Der **Program Counter (PC)** springt auf die Startadresse (z. B. `0x08000000` für STM32)

| `exit` | Telnet-Verbindung schließen |
| ------ | --------------------------- |

openocd -f openocd.cfg


ELF → BIN konvertieren
arm-none-eabi-objcopy -O binary build/SPI_Loopback.elf build/SPI_Loopback_Debug.bin
