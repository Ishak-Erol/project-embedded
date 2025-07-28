
---
![[Pasted image 20250719150941.png]]
STM32_CubeMX/BlinkingLights/Core/Src/main.c

---
![[Pasted image 20250719151105.png]]
STM32_CubeMX/BlinkingLights/Drivers/STM32F1xx_HAL_Driver/Src/stm32f1xx_hal_gpio.c
Parameter 1: Pointer auf ein GPIO_TypeDef, d.h. *GPIOx speichert die Adresse eines GPIO_TypeDef Wertes
Paramter 2: Speicheradresse des richtigen Pins im Register

---
![[Pasted image 20250719151321.png]]
STM32_CubeMX/BlinkingLights/Drivers/CMSIS/Device/ST/STM32F1xx/Include/stm32f100xb.h
GPIO_TypeDef wird hier deklariert. Enthhält Register für GPIO

---
![[Pasted image 20250719151509.png]]
STM32_CubeMX/BlinkingLights/Drivers/STM32F1xx_HAL_Driver/Inc/stm32f1xx_hal_gpio.h
GPIO pins werden definiert

---
![[Pasted image 20250719151653.png]]
STM32_CubeMX/BlinkingLights/Drivers/CMSIS/Device/ST/STM32F1xx/Include/stm32f100xb.h

---
![[Pasted image 20250719152939.png]]
STM32_CubeMX/BlinkingLights/Drivers/CMSIS/Device/ST/STM32F1xx/Include/stm32f100xb.h
GPIO_BASE als Konstante definiert. wird ersetzt durch exakte speicheradresse

---

GPIO ports werden definiert. GPIOA_BASE wird in Pointer umgewandelt (type casting). D.h., dass die Adresse durch die GPIOA_BASE ersetzt wurde nun ein Ppointer ist, der auf ein GPIO_TypeDef referenziert. Die GPIO Register (z.B. CRL, CRH, IDR) haben einen festen Bereich im Register relativ zum GPIO-Port![[Pasted image 20250719164339.png]]
siehe Seite 37 im [RM0041](file:///home/ishak/Downloads/rm0041-stm32f100xx-advanced-armbased-32bit-mcus-stmicroelectronics-1.pdf)