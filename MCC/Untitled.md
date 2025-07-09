Symbol (https://www.youtube.com/watch?v=RJMqMa4E1u0) + logarithmus dualis
IQ Diagramm https://www.youtube.com/watch?v=h_7d-m1ehoY&t=513s
BER - bit error rate
Übung 4
Lorawan

Eine **elektromagnetische Welle** entsteht, weil eine **beschleunigte elektrische Ladung** ein sich periodisch änderndes elektrisches und magnetisches Feld erzeugt. Sie breitet sich durch den Raum aus und schwingt bei einer bestimmten **Frequenz** (z. B. 100 Hz bedeutet 100 Schwingungen pro Sekunde).

Um Daten zu übertragen, verwendet man eine **Trägerfrequenz** (z. B. bei Wi‑Fi 5 GHz, also 5·10^9 Schwingungen pro Sekunde), die durch einen Oszillator gezielt erzeugt wird. Sie dient als „Transportmittel“ für das eigentliche Nutzsignal.

Die Information selbst wird durch **Modulation** (z. B. Amplituden-, Frequenz- oder Phasenmodulation) in den Träger „eingeprägt“. Das Modulieren verändert Eigenschaften des Trägers (Amplitude, Frequenz, Phase), wodurch das Signal nicht mehr nur eine einzelne Frequenz ist, sondern einen ganzen Frequenzbereich einnimmt – die sogenannte **Bandbreite**. Sie hängt davon ab, wie schnell und wie viele Daten übertragen werden: Je höher die Datenrate, desto breiter die Bandbreite.

Der gesamte Bereich, der durch das modulierte Trägersignal und mögliche Umgebungs- bzw. Schutzabstände belegt ist, bildet den **Funkkanal**. Das heißt:

- Der **Funkkanal** beschreibt den reservierten Frequenzbereich (inklusive Bandbreite und Abständen zum Nachbarkanal).
    
- Das **Trägersignal** ist eine einzelne Frequenz in der Mitte des Kanals, um die herum durch Modulation die eigentliche Information verteilt ist.
    
- Die **Bandbreite** ist der Frequenzbereich, den das modulierte Signal einnimmt.
    

**Beispiel (Wi‑Fi 6 bei 5 GHz):**  
Dein Router generiert eine Trägerwelle bei ungefähr 5 GHz. Durch die Modulation werden Daten (Informationen) übertragen, und das Signal breitet sich um diese Trägerfrequenz herum aus, z. B. in einem Kanal von 20 MHz Breite. Das modulierte Signal „schwingt“ also nicht nur bei genau 5 GHz, sondern im Frequenzbereich von etwa 5 GHz ± 10 MHz. So können die Daten in dieser Bandbreite transportiert werden.