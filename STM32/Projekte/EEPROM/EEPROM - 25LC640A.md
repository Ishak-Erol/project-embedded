Electrically Erasable Programmable Read Only Memory (EEPROM)  
**Speichergröße:** 64 Kbit → 8 KB  
**Package:** PDIP  

Datasheet: https://ww1.microchip.com/downloads/aemDocuments/documents/MPD/ProductDocuments/DataSheets/25AA640A-25LC640A-64K-SPI-Bus-Serial-EEPROM-20001830G.pdf
#### Speicherorganisation
- **Organisation:** 8192 × 8 Bit  
  - 8192 Speicheradressen, jede 8 Bit groß  
  - Zum Adressieren werden **13 Bit** benötigt (2¹³)  
  - EEPROM arbeitet mit **16 Bit Adressen**  
    - Die oberen 3 Bits sind „**Don't care**“ Bits  
#### Datenübertragung
- Alle **Instruktionen, Adressen und Daten** werden **MSB (Most Significant Byte) zuerst**, LSB (Least Significant Byte) zuletzt übertragen  
- Beispiel: 16-Bit Adresse 0x0123  
  - MSB = 0x01 → zuerst übertragen  
  - LSB = 0x23 → danach übertragen

![[Pasted image 20250824210427.png]]
![[Pasted image 20250824152424.png]]

#### Pins (PDIP)
- **CS** → Chip Select (Slave Select) 
- **SCK** → SPI Clock  
- **SI (MOSI)** → Master Out, Slave In  
- **SO (MISO)** → Master In, Slave Out  
- **VCC** → Versorgungsspannung  
- **GND** → Masse  
![[Pasted image 20250824210727.png]]

