### Asymmetrisches Challenge-Response-Verfahren
[[AssymmetrischesCR_Verfahren.jpg]]
Der Client überprüft die Identität des Servers, indem er ihm eine zufällige **Challenge** (Herausforderung) schickt, die der Server mit seinem privaten Schlüssel signiert[[Digitale Signatur]]. Der Client kann die Signatur mit dem öffentlichen Schlüssel überprüfen, der durch ein Zertifikat bestätigt wird.

1. **Der Server (Challengee)** besitzt ein **asymmetrisches Schlüsselpaar** (privater und öffentlicher Schlüssel) sowie ein **Zertifikat**, das seinen öffentlichen Schlüssel enthält.
2. **Der Client fordert das Zertifikat** des Servers an, um dessen öffentlichen Schlüssel zu erhalten.
3. **Der Server sendet sein Zertifikat** an den Client.
4. **Der Client validiert das Zertifikat**, indem er z. B. prüft:
    - ob es von einer **vertrauenswürdigen Zertifizierungsstelle (CA)** ausgestellt wurde,
5. Der **Client generiert eine Challenge** – eine zufällige Zeichenfolge (Nonce).
6. Die **Challenge wird an den Server gesendet**.
7. Der **Server signiert die Challenge** mit seinem **privaten Schlüssel** und sendet die **digitale Signatur** zurück an den Client.
8. Der **Client prüft die Signatur** mit dem **öffentlichen Schlüssel aus dem Server-Zertifikat** und vergleicht die entschlüsselte Challenge mit der ursprünglich gesendeten.
9. Wenn die Signatur gültig ist und die Challenge übereinstimmt, ist sich der Client sicher:  



### Symmetrisches Challenge-Response-Verfahren
[[SymmetrischesCR_Verfahren.jpg]]
Der **Client überprüft die Identität des Servers**, indem er ihm eine zufällige **Challenge** (Herausforderung) schickt.  
Der **Server berechnet daraus eine Response (Antwort)** mithilfe eines **symmetrischen Geheimschlüssels**, den beide zuvor sicher ausgetauscht haben.  
Der **Client berechnet parallel selbst die erwartete Antwort** mit demselben Schlüssel – stimmt sie mit der Server-Response überein, ist der Server authentisch.

1. Server (Challengee) und Client(Challenger) besitzen symmetrischen Schlüssel
2. Der Client generiert eine Challenge (Zufallszahl)
3. Der **Server empfängt die Challenge** und berechnet eine **Response**, indem er die Zufallszahl mit dem symmetrischen Schlüssel hasht
4. Der **Client berechnet dieselbe Response**
5. Der **Client vergleicht die empfangene Response mit seiner berechneten Response**