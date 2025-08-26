### Problem
Mechanische Taster prellen beim Drücken oder Loslassen:
- Signal oszilliert kurz zwischen HIGH und LOW
- Mikrocontroller kann mehrere „falsche“ Tastendrücke registrieren

### Ursache
- Geschwindigkeit der Code-Ausführung > Dauer des Prellens
- MCU liest den Pin schneller als der Taster stabil ist
- 
### Lösungen
1. **Delay einfügen**  
   Kurzes Warten nach Tastendruck, z. B. `HAL_Delay(50)`