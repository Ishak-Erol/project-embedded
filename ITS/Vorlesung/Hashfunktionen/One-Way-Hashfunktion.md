-------Abbildung Link
Unter einer **One-Way-Hashfunktion** versteht man eine #Einwegfunktion ( $H$ ), die eine beliebig lange Nachricht ( $M$ ) als Eingabe nimmt und einen Hashwert ( $h$ ) mit einer festen Ausgabelänge berechnet (mindestens 256 Bit, um Kollisionen zu vermeiden). Dieser Hashwert ist der digitale Fingerabdruck der Nachricht.

Wichtige Eigenschaften einer solchen Funktion sind vor allem:

- Die Inversion ist praktisch unmöglich, das heißt, es ist extrem schwierig, aus \( $h$ \) die ursprüngliche Nachricht ( $M$ ) zu berechnen (also ( $M = H^{-1}(h$) ) praktisch nicht möglich).
- Sie ist kollisionsresistent, das heißt, es ist praktisch unmöglich, zwei verschiedene Nachrichten \( $M \neq M'$ \) mit demselben Hashwert \( $h$ \) zu finden.
- Die Funktion erfüllt das **Kerckhoffs-Prinzip**, das heißt, die Hashfunktion selbst ist öffentlich bekannt

Das BSI empfiehlt die Verwendung der #Hashfunktionen aus den **SHA-2**- und **SHA-3**-Familien.  
Die Hashfunktion wird unter anderem beim **Message Authentication Code (MAC)** genutzt und ist eine **Möglichkeit** zur Sicherstellung von Authentizität und Integrität, die sich von der digitalen Signatur unterscheidet.

Um eine Hashfunktion in einen MAC umzuwandeln, wird der Hashwert mit einem **geheimen symmetrischen Schlüssel** kombiniert (nicht verschlüsselt im klassischen Sinn). Ist der Schlüssel öffentlich, handelt es sich wieder um eine reine #Einweg-Hashfunktion.

### Anwendungszweck
Der MAC ist eine **symmetrische Methode zur Sicherstellung der Datenintegrität und Authentizität**, die gegenüber der digitalen Signatur effizienter arbeitet, jedoch Einschränkungen bei der Nachweisbarkeit des Absenders hat. Während bei der **digitalen Signatur** der Empfänger mithilfe des öffentlichen Schlüssels verifizieren kann, ob die Nachricht tatsächlich vom erwarteten Absender stammt (da nur dieser den passenden privaten Schlüssel zum Signieren besitzt), beruht die Datenauthentizität beim **Message Authentication Code (MAC)** auf einem symmetrischen Schlüssel. Das bedeutet, dass beide Kommunikationspartner denselben Schlüssel besitzen und es im Nachhinein nicht eindeutig festgestellt werden kann, wer von beiden die Nachricht tatsächlich erzeugt hat. Bei der digitalen Signatur hingegen kann nur derjenige die Nachricht signiert haben, der den geheimen privaten Schlüssel besitzt. -------Abbildung-Link

In der Vorlesung wurden zwei MAC-Methoden vorgestellt: der **CBC-MAC** und **HMAC (Keyed-Hashing for Message Authentication)**.  
Beim **CBC-MAC** wird der MAC mit dem Verschlüsselungsalgorithmus AES verknüpft. Der letzte Verschlüsselungsblock dient dann als MAC, welcher beim Empfänger geprüft wird. Ein Nachteil dieser Variante ist, dass sie bei Nachrichten mit variabler Länge unsicher ist. ---------Abbildung Link

Der **HMAC** arbeitet zwar langsamer als der #CBC-MAC, ist dafür aber auch bei Nachrichten mit variabler Länge sicher. Die Generierung des #HMAC erfolgt wie folgt:
1. Das **ipad** (innerer Padding-Block) wird bitweise mit dem symmetrischen Schlüssel XOR-verknüpft.
    
2. Das Ergebnis wird zusammen mit der Nachricht als Eingabe in die Hashfunktion gegeben (innere Hashing) - konkatenieren
    
3. Die zweite Hashfunktion bekommt den Hashwert der ersten Hashfunktion sowie die XOR-Verknüpfung des **opad** (äußerer Padding-Block) und des Schlüssels als Eingabe (äußere Hashing) - konkatenieren
    
4. Der Hashwert der zweiten Hashfunktion ist der finale **HMAC**
----------- Abbildung-Link