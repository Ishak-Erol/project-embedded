# 🧠 **STM32 HAL Code & Projektstruktur – Kompaktübersicht für Wiederholung**

---

## ✅ **1. Was macht der STM32 HAL-Code in `main.c`?**

### Beispielcode (vereinfacht):
`int main(void)`
`{`
    `HAL_Init();`
    `SystemClock_Config();`
    `MX_GPIO_Init();`
    `while (1) { }`
`}`

💡 Zweck:

| Funktion               | Bedeutung                                                |
| ---------------------- | -------------------------------------------------------- |
| `HAL_Init()`           | Initialisiert HAL-Bibliothek: Flash, SysTick, Interrupts |
| `SystemClock_Config()` | Taktquelle (HSI/PLL) einstellen                          |
| `MX_GPIO_Init()`       | GPIOs konfigurieren (z. B. PC9 als Output)               |
| `while(1)`             | Haupt-Loop (Endlosschleife)                              |

🔧 **2. Clock-Konfiguration (`SystemClock_Config`)**
Beispiel: `HSI (8 MHz) → PLL (x6) → SYSCLK = 48 MHz`

Einstellungen:
![[Pasted image 20250718193509.png]]

🔌 **3. GPIO-Konfiguration (`MX_GPIO_Init`)**
Beispielkonfiguration:
GPIOC, Pin 9, Output Push-Pull, keine Pulls, mittlere Geschwindigkeit
### Ablauf:

1. Takt für Port C & A aktivieren (`__HAL_RCC_GPIOx_CLK_ENABLE()`)
    
2. Pin 9 konfigurieren:
    
    - Output
        
    - Kein Pullup/down
        
    - Mittlere Frequenz
        
3. Pin 9 auf LOW setzen (`HAL_GPIO_WritePin(..., RESET)`)


🔁 **4. Pin toggeln mit HAL**
Funktion:
`HAL_GPIO_TogglePin(GPIOC, GPIO_PIN_9);`
- `GPIOC`: Port (Typ: `GPIO_TypeDef *`)
    
- `GPIO_PIN_9`: Pin-Maske (Typ: `uint16_t`, z. B. `0x0200`)
    

Wechselt den Zustand (HIGH ↔ LOW).

🔗 **5. Woher kommt `HAL_GPIO_TogglePin`? – Include-Kette**
Standardmäßig nur:
`\#include "main.h"`

Die Kette:
main.c
└── main.h
    └── stm32f1xx_hal.h
        └── stm32f1xx_hal_gpio.h
            └── stm32f1xx_hal_def.h
                └── stm32f1xx.h

- `main.h`: Projekt-Datei, enthält `stm32f1xx_hal.h`
    
- `stm32f1xx_hal.h`: Zentrale HAL-Datei mit allen HAL-Komponenten
    
- `stm32f1xx_hal_gpio.h`: GPIO-Funktionen wie `HAL_GPIO_TogglePin`
    
- `stm32f1xx.h`: CMSIS-Kern mit Registerdefinitionen (z. B. `GPIO_TypeDef`)

📄 **Wichtige Header erklärt**

| Datei                  | Inhalt                                                             |
| ---------------------- | ------------------------------------------------------------------ |
| `main.h`               | Projekt-spezifische Deklarationen + HAL include                    |
| `stm32f1xx_hal.h`      | Zentrale Datei, die alle HAL-Komponenten einbindet                 |
| `stm32f1xx_hal_gpio.h` | GPIO-Funktionen, `GPIO_PIN_X`, `HAL_GPIO_TogglePin()`              |
| `stm32f1xx_hal_def.h`  | HAL-Basistypen, wie `GPIO_TypeDef`, `HAL_StatusTypeDef`            |
| `stm32f1xx.h`          | Registerdefinitionen für STM32F1-Peripherie (CMSIS, ST-spezifisch) |

## ✅ Zusammenfassung: So arbeitet der STM32 HAL-Code

- **HAL ist modular aufgebaut**, durch gestaffelte Includes
    
- Du musst meist **nur `main.h` inkludieren**
    
- Die eigentlichen Hardware-Details stecken **tief in `stm32f1xx.h`**
    
- HAL-Funktionen kapseln **direkte Registerzugriffe**
    
- Du kannst jederzeit HAL verlassen und **mit Direktzugriffen arbeiten** (wenn du willst)