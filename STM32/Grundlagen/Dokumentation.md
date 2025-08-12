[Datasheet](file:///home/ishak/Downloads/stm32f100rb.pdf) -› Überblick über das physische Bauteil. Enthält mechanische und elektrische Informationen, Pinbelegung, Gehäusevarianten und grundlegende Eigenschaften des Mikrochips.
[Reference manual](file:///home/ishak/Downloads/rm0041-stm32f100xx-advanced-armbased-32bit-mcus-stmicroelectronics-1.pdf) -› Detaillierter als das Datasheet. Enthält die vollständige Beschreibung der Peripherie und der Register. Wichtig für das Programmieren auf Registerebene.

[HAL-Dokumentation](file:///home/ishak/Downloads/um1850-description-of-stm32f1-hal-and-lowlayer-drivers-stmicroelectronics.pdf)

###### Wichitge Header :

| Datei                  | Inhalt                                                             |
| ---------------------- | ------------------------------------------------------------------ |
| `main.h`               | Projekt-spezifische Deklarationen + HAL include                    |
| `stm32f1xx_hal.h`      | Zentrale Datei, die alle HAL-Komponenten einbindet                 |
| `stm32f1xx_hal_gpio.h` | GPIO-Funktionen, `GPIO_PIN_X`, `HAL_GPIO_TogglePin()`              |
| `stm32f1xx_hal_def.h`  | HAL-Basistypen, wie `GPIO_TypeDef`, `HAL_StatusTypeDef`            |
| `stm32f1xx.h`          | Registerdefinitionen für STM32F1-Peripherie (CMSIS, ST-spezifisch) |
