UART Kommunikation handlet es sich um eine asynchrone USART Kommunikation, d.h. eine serielle asynchorne kommunikation. Host und Target einigen sich auf eine gemeinsame Symoblrate (+/- 2%), nhemen wir mal 9600 Baud. Das heißt, dass auf beiden Seiten 9600 symbole/sekunde gesenedt werden. Symbole sind physikalische repräsentaito eines signals. Hier entspeerchen es einem bit. Somit lässt sich auch sagen, dass 9600 bits/sekunde versendet werden. Durch den Kherwert erfahren wir, dass ein bit 104mikrosekunde unterwegs ist. Um den Startbit korrekt zu erfassen wird die interne taktrate des empängers auf ein vielfaches der symbolrate eingestellt (hier: 16x). Das heißt, dass der Quarzoszillator, die elektrischen signale entsprechedn hoch frequentiert. Statt nun alle 104 mikrosekudne abzutasten, wird jede 6,5 mikrosekunden abgetatstet und gemessen ob eine fallende flanke vorliegt. Das nennt man oversampling. Nachdem das Startbit erkannt wurde wird nun die ersten 1.5 bit das tasten eingestellt. nach 1.5 bitdauer, das heißt 24 takten, wird inmitten des ersten bits der nutzdaten das signal gemessen(wieso?). Die restlcihen bits werden anschließend alle 104 mikrosekundne also nach 16 takten abgetastet.

![[UART.jpg]]

1. **Host und Target einigen sich auf eine Symbolrate (Baudrate), z.B. 9600 Baud**  
    → Das heißt: 9600 Symbole pro Sekunde werden gesendet.  
    → Bei UART entspricht 1 Symbol meist 1 Bit, also 9600 Bits pro Sekunde.
    
2. **Daraus folgt: 1 Bit dauert ca. 1/9600 s ≈ 104 Mikrosekunden**
    
3. **Um das Signal zuverlässig zu erkennen, arbeitet der Empfänger mit einer internen Taktfrequenz, die ein Vielfaches der Baudrate ist (z.B. 16×)**  
    → Das heißt, er taktet mit etwa 16 × 9600 = 153600 Takte pro Sekunde.
    
4. **So wird das Signal nicht nur einmal pro Bit abgetastet, sondern alle ca. 6,5 Mikrosekunden (104 µs / 16)**  
    → Das nennt man Oversampling.
    
5. **Der Empfänger wartet, bis er eine fallende Flanke erkennt (Idle ist HIGH, Startbit LOW)**  
    → Das ist das Startbit – der Beginn eines neuen Datenrahmens.
    
6. **Nach Erkennen der Fallkante wartet der Empfänger 1,5 Bitzeiten (also 24 interne Takte)**  
    → Warum? Um **genau in der Mitte** des ersten Nutzdatenbits zu messen.  
    → Die Mitte ist am stabilsten, hier ist die Wahrscheinlichkeit für eine Fehlmessung am geringsten.
    
7. **Dann wird alle 1 Bitzeit (16 interne Takte) der Pegel gemessen, um die einzelnen Datenbits zu lesen**
    

---

### Warum  1,5 Bitzeit Wartezeit:

- Direkt nach der Fallkante bist du **am Übergang Startbit → erstes Datenbit**.
- Die Fallkante könnte etwas „unscharf“ sein, das Signal braucht vielleicht etwas Zeit, um stabil zu werden.
- Wenn du **1,5 Bitzeiten wartest**, bist du **in der Mitte des ersten Datenbits** – das ist ein stabiler Zeitpunkt für eine saubere Messung.

- Das #Oversampling sorgt für **höhere Genauigkeit** und **Robustheit** gegen Störungen und Taktabweichungen.
    
- Das 1,5-Bit-Warten ist ein Trick, um die Abtastung auf den stabilsten Moment zu legen.