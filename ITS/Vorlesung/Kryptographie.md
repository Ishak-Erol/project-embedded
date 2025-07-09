## Lerntagebuch
- Datum: 2025.05.15
- Vorlesung: [Grundlagen  der Kryptographie](https://moodle.w-hs.de/pluginfile.php/697757/mod_resource/content/2/03_Kryptographie_Einfuehrung.pdf)

Heute habe ich in der dritten Vorlesung die Grundlagen der Kryptographie kennengelernt, um damit das zentrale Schutzziel der Informationssicherheit, nämlich die **Vertraulichkeit (Confidentiality)**, zu gewährleisten.  
Kryptographie bedeutet, **verständliche Informationen in unverständliche (also verschlüsselte) Informationen zu transformieren**. Dieses Verfahren nennt man **Verschlüsselung**.

Ein häufig genutztes Verfahren basiert auf der **XOR-Verschlüsselung**, die aufgrund ihrer **mathematischen Eigenschaften** sehr effizient und einfach ist.  
Bei der XOR-Verschlüsselung arbeitet man auf **Bit-Ebene**. Neben der zu verschlüsselnden Nachricht (**Plaintext**) benötigt man einen **Schlüsseltext** (**Key**).  
Die Verschlüsselung erfolgt, indem man die **Bit-Darstellung** der Zeichen des Klartexts mit der Bit-Darstellung des Schlüssels **XOR-verknüpft**.  
Die Bit-Darstellung eines Zeichens ergibt sich aus seiner **Byte-Darstellung**, die man wiederum mithilfe der **ASCII-Tabelle** bestimmen kann.

Neben der Bit-Ebene kann man auch auf der **Textebene** verschlüsseln. Dabei werden die einzelnen Buchstaben des Klartexts durch andere ersetzt, was man als **Substitution** bezeichnet.  
Es gibt drei grundlegende Methoden der Substitution:

1. **Monoalphabetische Substitution**:  
    Hier wird **jedem Zeichen** des Klartexts **ein festes anderes Zeichen** zugeordnet – nach einer bestimmten Regel.  
    Der Nachteil dieser Methode besteht darin, dass sie durch **Häufigkeitsanalyse** leicht zu knacken ist.  
    Wenn z. B. in einer Sprache ein bestimmter Buchstabe eine Häufigkeit von 50 % hat, wird auch im Ciphertext ein Zeichen mit ähnlicher Häufigkeit erscheinen – das verrät Rückschlüsse auf den ursprünglichen Text.
    
2. **Polyalphabetische Substitution**:  ![[Polyalphabetische Substitution.jpg]]
    Diese Methode erweitert die monoalphabetische Substitution, indem **mehrere Alphabete** verwendet werden (wie der Name „poly“ = „mehrfach“ schon andeutet).  
    Das bedeutet: **Ein Buchstabe im Klartext kann je nach Position unterschiedlich verschlüsselt werden.**  
    Ein bekanntes Beispiel ist die [vigenere-Verschlüssleung](https://inf-schule.de/imperative-programmierung/python/projekte/modularisierung/verschluesselung/vigenereverfahren) .
    Hier wird ein Schlüsselwort wiederholt über den Klartext gelegt, und die Buchstaben werden nach der Position im Alphabet verschoben.
    
3. **Homophone Substitution**:  
    Diese Methode versucht die Schwäche der monoalphabetischen Substitution zu umgehen, indem **mehreren Klartextzeichen mehrere mögliche Ciphertext-Zeichen** zugeordnet werden.  
    So bekommt z. B. der häufige Buchstabe **„E“** mehrere Zahlen zugewiesen, z. B. **10, 5, 7, 11, 32**, während ein seltener Buchstabe wie **„K“** nur eine zugewiesen bekommt.  
    Dadurch werden **Häufigkeitsmuster verschleiert**, was die Häufigkeitsanalyse erschwert.
    

Ein grundlegendes Prinzip, an dem sich alle modernen Verschlüsselungsverfahren orientieren, ist das sogenannte  [Kerckhoff-Prinzip](https://rock-the-prototype.com/kryptografie/kerckhoff-prinzip/).  
Es besagt:

> _„Ein kryptographisches System sollte selbst dann sicher sein, wenn alles außer dem Schlüssel öffentlich bekannt ist.“_

Oder in anderen Worten:

> _„Ein Verschlüsselungsverfahren muss auch dann noch sicher sein, wenn der Angreifer den Algorithmus zur Ver- und Entschlüsselung kennt.“_


Gut zu Wissen: Man unterscheidet zwischen zwei Sicherheitskategorien:
					1. Perfekte Sicherheit (One-Time Pad als Beispiel)
					2. praktische Sicherheit (theoretisch möglich, praktisch aufgrund von ressourcen grenzen nicht möglich )
					
[[2)Kryptographie.jpg]]
