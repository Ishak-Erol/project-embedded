
Modulation ist der Prozess, bei dem man das Basisbandsignal in ein Trägersignal überführt wird – man spricht auch vom Hochmischen. Dies wird unter anderem durchgeführt, um niederfrequente Signale in den Hochfrequenzbereich (HF-Bereich) zu übertragen und so von dessen Vorteilen zu profitieren.

Es gibt drei grundlegende Arten der Modulation:

- Amplitudenmodulation (AM)  
- Frequenzmodulation (FM)  
- Phasenmodulation (PM)  

Uns muss zu Beginn klar sein, dass reale modulierte Signale (auf eine Trägerfrequenz aufgesetzte Basisbandsignal) **nicht nur aus einer einzelnen Frequenz bestehen**, sondern ein ganzes **Frequenzgemisch** darstellen – das sogenannte **Basisbandspektrum**. [Abbildung 1](MCC/MCC_images/BasisbandspektrumRealesSignal.png) zeigt ein  beispielhaftes Spektrum einer [UMTS](https://de.wikipedia.org/wiki/Universal_Mobile_Telecommunications_System) [Basisstation](https://de.wikipedia.org/wiki/Basisstation) .

Diese Erkenntnis erhält man durch die **Fourier-Transformation** des Basisbandsignals. Sie erlaubt es, ein komplexes Signal in seine einzelnen Frequenzanteile zu zerlegen. 

Mithilfe der **Fourier-Reihe** können wir außerdem bestimmte periodische Basisbandsignale – beispielsweise ein Rechtecksignal – in harmonische Sinusschwingungen zerlegen. Je mehr Sinusfunktionen wir berücksichtigen, desto genauer wird die Annäherung an die Rechteckfunktion.

In [Abbildung 3](/MCC/MCC_images/Basisbandspektrum.png) wird das Amplitudenspektrum eines Signal dargestellt, das bei $0 Hz$ beginnt und bis zu einer Frequenz $fmax$​ ansteigt. Danach gibt es keine weiteren Frequenzanteile mehr. Das heißt, dass unser Basisbandsignal, also das Signal, dass die Information enthält, vor der Modulation seine Frequenzanteile im Bereich von 0 bis $f_\text{max}$ hat. Mit zunehmender Frequenz nimmt die Amplitude der Frequenzanteile **ab**. Die Form des Spektrums ergibt sich durch die **Fourier-Analyse**, konkret durch die **Fourier-Reihe**, wenn es sich um ein **periodisches Signal** handelt. Diese zerlegt das Signal in eine Summe aus **harmonischen Sinus- und Kosinusfunktionen**, die zusammen das ursprüngliche Signal exakt beschreiben. Die Dreieckform sagt aus, dass höhere Frequenzen etwas stärker vertreten sind als beispielsweise die $0 Hz$.

[Abbildung 4](/MCC/MCC_images/HF-Spektrum.png) hingegen zeigt das Spektrum nach einer Amplitudenmodulation (Hochmischung). In der Mitte befindet sich die Trägerfrequenz $f_\text{c}$  . Durch die **Multiplikation** des niederfrequenten Nutzsignals (Basisbandsignal) mit einer hochfrequenten Trägerfrequenz entsteht im Frequenzbereich eine **Addition und Subtraktion der Frequenzanteile**.  
Dadurch bilden sich im Spektrum **zwei Seitenbänder**:  
- ein **oberes Seitenband** bei $f_\text{Träger} + f_\text{Nutz}$
- und ein **unteres Seitenband** bei $f_\text{Träger} - f_\text{Nutz}$
![[reddit_sideband.png]]
 *Quelle:* *https://www.reddit.com/r/amateurradio/comments/15ra9tj/where_do_the_am_sidebands_actually_come_from/*

![[Systemdarstellung.png]]

	Beachte, dass die Abbildung 4 gespiegelt ist (Original:[[Amplitudenspektrum.png]]). Das bedeutet, dass die Frequenzen umso schwächer werden, je weiter sie sich vom Trägersignal entfernen (in der Abbildung ist es andersherum dargestellt). Zudem wurde hier das Trägersignal ausgefiltert, da es keine Information enthält (Energieeffizienz). 

Theoretisch kann man auch eines der Seitenbänder filtern, da diese den gleichen Informationsgehalt haben.
