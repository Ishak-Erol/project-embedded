
Modulation ist der Prozess, bei dem man das Basisbandsignal bzw. Nutzsignal in ein Trägersignal überführt – man spricht auch vom Hochmischen. Dies wird unter anderem durchgeführt, um niederfrequente Signale in den Hochfrequenzbereich (HF-Bereich) zu übertragen und so von dessen Vorteilen zu profitieren.

Es gibt drei grundlegende Arten der Modulation:

- Amplitudenmodulation (AM)  
- Frequenzmodulation (FM)  
- Phasenmodulation (PM)  

Uns muss zu Beginn klar sein, dass reale modulierte Signale (auf eine Trägerfrequenz aufgesetzte Basisbandsignal) **nicht nur aus einer einzelnen Frequenz bestehen**, sondern ein ganzes **Frequenzgemisch** darstellen – das sogenannte **Basisbandspektrum**. [Abbildung 1](MCC/MCC_images/BasisbandspektrumRealesSignal.png) und [Abbildung 2](/MCC/MCC_images/BasisbandspektrumReineSinusschwingung.png) zeigen beispielhafte Spektren solcher Signale.

Diese Erkenntnis erhält man durch die **Fourier-Transformation** des Basisbandsignals. Sie erlaubt es, ein komplexes Signal in seine einzelnen Frequenzanteile zu zerlegen. 

Mithilfe der **Fourier-Reihe** können wir außerdem bestimmte periodische Basisbandsignale – beispielsweise ein Rechtecksignal – in harmonische Sinusschwingungen zerlegen. Je mehr Sinusfunktionen wir berücksichtigen, desto genauer wird die Annäherung an die Rechteckfunktion.

In [Abbildung 3](/MCC/MCC_images/Basisbandspektrum.png) wird ein Signal dargestellt, das bei $0 Hz$ beginnt und bis zu einer Frequenz $fmax$​ ansteigt. Danach gibt es keine weiteren Frequenzanteile mehr. Das heißt, dass unser Basisbandsignal – also das Signal, das die Information enthält – vor der Modulation nur diese niedrigen Frequenzen umfasst. Die Dreieckform sagt aus, dass höhere Frequenzen etwas stärker vertreten sind als beispielsweise die $0 Hz$.

[Abbildung 4](/MCC/MCC_images/HF-Spektrum.png) hingegen zeigt das Spektrum nach einer Amplitudenmodulation (Hochmischung). In der Mitte befindet sich die Trägerfrequenz $fc$. Durch Addition bzw. Subtraktion der niederfrequenten Frequenzen (Nutzsignal/Basisbandsignal) mit der hochfrequenten Frequenz des Trägersignals entstehen zwei Seitenbänder.

Beachte, dass diese Abbildung gespiegelt ist. Das bedeutet, dass die Frequenzen umso schwächer werden, je weiter sie sich vom Trägersignal entfernen (in der Abbildung ist es andersherum dargestellt). Zudem wurde hier das Trägersignal ausgefiltert, da es keine Information enthält (Energieeffizienz). 

Theoretisch kann man auch eines der Seitenbänder filtern, da diese den gleichen Informationsgehalt haben.
