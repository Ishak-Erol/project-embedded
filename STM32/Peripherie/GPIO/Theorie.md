- GPIO für Pegelsteuerung
- standard (primitve) Funktion für die meisten pins
- jeder GPIO-port (GPIOA, GPIOB, ...) besitzt 7 Register (CRL, CRH, IDR, ODR, BSRR, BRR, LCKR)


**Jeder Pin ist von Haus aus GPIO-fähig.**  
> Für alles andere (USART, I2C, SPI, etc.) muss er **umgeschaltet werden** → "Alternative Function".

Die GPIO Register (z.B. CRL, CRH, IDR) haben einen festen Bereich im Register relativ zum GPIO-Port![[Pasted image 20250719164339.png]]
siehe Seite 37 im [RM0041](file:///home/ishak/Downloads/rm0041-stm32f100xx-advanced-armbased-32bit-mcus-stmicroelectronics-1.pdf)

