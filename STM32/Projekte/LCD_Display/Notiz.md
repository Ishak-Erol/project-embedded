Pins verbunden und initialisiert (CS, DC/A0, RST, SCK, MOSI)
  - SPI konfiguriert über CubeMX
  - Init-Sequenz manuell versucht (SLEEP_OUT, MADCTL, CASET/RASET, RAMWR)
  - Pixel über drawPixel() oder eigene Funktionen gesendet
- Problem: Display bleibt weiß
- Fazit: Verstanden, aber funktioniert mit eigener Umsetzung nicht. Projekt nicht weiter verfolgt.


MOSI -SCL - CS - (MISO)

schwarz - clock ersatz ->  CLK => ? SCL ?
weiß - SDA => D0 (aka MOSI)
grün - RS => D/CX (interner pin)
gelb - RST => RESX (intenrer pin) 
orange - CS => CSX(interner pin)

| Display-Pin | Steckbrett-Verbindung | STM32-Pin |
|------------|---------------------|-----------|
| CS         | J1 → H1 → B1 → A1  | PA4       |
| RST        | J2 → H2 → B2 → A2  | PA3       |
| RS / DC    | J3 → H3 → B3 → A3  | PA1       |
| SDA / MOSI | J4 → H4 → B4 → A4  | PA6       |
| CLK / SCK  | J5 → H5 → B5 → A5  | PA5       |
| NC         | leer                | –         |
| NC         | leer                | –         |
| NC         | leer                | –         |
| GND        | J9 → H9             | GND       |
| GND        | J10 → G10           | GND       |
| VCC        | J11 → H11           | 3.3 V     |
| –          | –                   | GND       |
| +          | –                   | 3.3 V     |
IM2 = 0, 4WSPI =1  --> 4-line serial interface  -- SPI4W default auf 1, da RS Pin herausgeführt ist