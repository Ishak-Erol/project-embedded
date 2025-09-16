### Überblick
- **SPI = Kommunikationsprotokoll** → definiert Regeln, wie Geräte Daten austauschen.  
- Kann in **Hardware** oder per **Software (Bit-Banging)** umgesetzt werden.  
- Typisch für **Master-Slave Kommunikation** (ein Master, mehrere Slaves).  

### Hardware-Implementierung
- **Fest verdrahtete Schaltkreise** im Mikrocontroller (Logikgatter).  
- MCU mit **SPI-Modul** = spezieller Hardware-Block, der nach SPI-Regeln arbeitet.  
- Vergleich: Ein **OR-Gatter** besteht intern auch aus mehreren Gattern → SPI-Modul ist ebenfalls eine Zusammenschaltung, die SPI automatisch handhabt.  
- Vorteil: **schnell, effizient, zuverlässig**.  

### Software-Implementierung
- Umsetzung in **Software** durch manuelles Steuern der GPIO-Pins.  
- CPU „taktet“ und setzt Signale **per Software (Bit-Banging)**. 


### Blockdiagramm
![[Pasted image 20250821115417.png| SPI Protocol Block Diagram]][[Pasted image 20250821115417.png| SPI Protocol Block Diagram]]

### Funktionsweise
- **Master** kontrolliert Kommunikation 
- Jeder Slave hat eine eigene **SS-Leitung (Slave Select)**.  
- Master zieht SS auf **Low**, um den gewünschten Slave zu aktivieren.  
- Datenleitungen:  
  - **MOSI** → Master sendet an Slave  
  - **MISO** → Slave sendet an Master  
  - **SCK** → Clock-Signal vom Master (synchronisiert Übertragung)  
- Eigenschaften:  
  - **seriell** (Bit für Bit)  
  - **voll-duplex** (gleichzeitiges Senden/Empfangen)  
  - **synchron** (gemeinsamer Takt vom Master)  
  - **1 Taktimpuls = 1 Bit**  
- Einsatz: Datentransfer zwischen „smarten“ Controllern und „einfacheren“ Geräten (Sensoren, Displays, Speicherchips).  
Wichtig: - **Dummy-Bytes (z. B. 0xFF, sihe datenblatt)** nötig, wenn Master nur lesen möchte, da voll duplex! 

### SPI Clock Modes
- CPOL (Clock polarity)=0  ==> idle(Ruhezustand) low(0) - active low
- CPOL (Clock polarity)=1 ==> idle(Ruhezustand) high(1) - active high
- CPHA (Clock phase)=0 ==> Daten werden an  **erster Flanke** (direkt nach Idle-Zustand) gelesen
- CPHA (Clock phase)=1==> Daten werden an der **zweiten Flanke** gelesen

| CPOL | CPHA | Beschreibung                           |
| ---- | ---- | -------------------------------------- |
| 0    | 0    | Idle Low, Daten bei steigender Flanke  |
| 0    | 1    | Idle Low, Daten bei fallender Flanke   |
| 1    | 0    | Idle High, Daten bei fallender Flanke  |
| 1    | 1    | Idle High, Daten bei steigender Flanke |
Wichtig: **Master und Slave müssen denselben Modus verwenden!**
### Multi slave Konfigurationen
![[Pasted image 20250821162453.png]]




![[Pasted image 20250905172317.png]]
Datasheet seite 25


![[Pasted image 20250905173254.png]]
Datasheet seite 26