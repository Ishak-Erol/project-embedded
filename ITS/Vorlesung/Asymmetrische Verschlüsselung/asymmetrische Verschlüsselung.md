- [x] Was ist asymmetrische Verschlüsselung? + Beispiel verlinken
- [x] diffie-hellman-schlüsselaustausch

[[asymmetrische_Verschlüssung.png]]

In der vorherigen [[Symmetrische Verschlüsselung|Vorlesung]] zur symmetrischen Verschlüsselung habe ich gelernt, wie dieses Verfahren funktioniert. Dabei bin ich auf das grundlegende Problem der **sicheren Schlüsselverteilung** gestoßen:
>Beide Kommunikationspartner benötigen denselben geheimen Schlüssel, doch dieser muss zunächst vertraulich übermittelt werden.

Um dieses Problem zu lösen, wurde die **asymmetrische Verschlüsselung** entwickelt. Hierbei gibt es ein **Schlüsselpaar** aus einem **öffentlichen Schlüssel** (Public Key) und einem **privaten Schlüssel** (Private Key). Der Sender verwendet einen öffentlichen Schlüssel , der von einer **vertrauenswürdigen Instanz** innerhalb der **Public-Key-Infrastruktur (PKI)** bereitgestellt worden ist, um seine Nachricht zu verschlüsseln. Nur der Empfänger besitzt den passenden privaten Schlüssel, mit dem sich die Nachricht wieder entschlüsseln lässt. Das [[RSA|RSA-Kryptosystem]] ist das asymmetrischen Verfahren anhadnd dessen wir uns die asymmetrische Verschlüsselung angeschaut haben.

Die Sicherheit dieses Verfahrens beruht auf sogenannten **Einwegfunktionen** (One-Way Functions). Das sind mathematische Vorschriften, die sich leicht in eine Richtung berechnen lassen, deren **Umkehrung (inverse Transformation)** jedoch **praktisch nicht durchführbar** ist.

#asymmetrischeVerschlüsselung

---

## Diffie-Hellman-Schlüsselaustausch

Der **Diffie-Hellman-Schlüsseltausch** war das erste Verfahren, das entwickelt wurde, um das Problem der **sicheren Schlüsselverteilung** zu lösen. [[Diffie-Hellman-Schlüsselaustausch.jpg|Diffie-Hellman-Schlüsselaustausch Ablauf]]

Bei diesem Verfahren einigen sich beide Kommunikationspartner zunächst auf eine **große Primzahl n**, die **öffentlich bekannt** ist. Zusätzlich wird eine Zahl g gewählt, die **teilerfremd zu n** ist (auch g ist öffentlich bekannt).  Im nächsten Schritt wählt jeder Partner eine **private, geheime Zufallszahl**:

- Der Sender (z. B. Alice) wählt eine geheime Zahl a
    
- Der Empfänger (z. B. Bob) wählt eine geheime Zahl b

Nun berechnen beide jeweils einen öffentlichen Teil:
- Alice berechnet:  
    $A = g^a \mod n$ 
    und sendet A an Bob
    
- Bob berechnet:  
    $B = g^b \mod n$
    und sendet B an Alice

Damit sind im öffentlichen Raum nun folgende Werte bekannt:
- Die Primzahl n
- Die Zahl g
- Die berechneten Werte A und B
    
Im letzten Schritt berechnen **beide Parteien jeweils lokal denselben geheimen Schlüssel S**:
- Alice berechnet:  
    $S = B^a \mod n = (g^b)^a \mod n = g^{ab} \mod n$

- Bob berechnet:  
    $S = A^b \mod n = (g^a)^b \mod n = g^{ab} \mod n$

Die **Sicherheit** des Verfahrens beruht darauf, dass es **extrem schwer ist**, aus den bekannten Werten g, n und A bzw. B auf die geheimen Exponenten a oder b zu schließen. Denn bei Nutzung des Logarithmus handelt es sich um eine sogenannte **Einwegfunktion** (one-way-funktion), d. h. sie ist leicht in eine Richtung zu berechnen, aber praktisch **nicht umkehrbar**.
[[Diffie-Hellman_Beispiel.jpg|Beispiel]]

#Diffie-Hellman