- [x] Was ist eine digitale Signatur?
- [x] Wofür?
- [x] Zusammenhang zur asymmetrischen Verschlüsselung
- [x] Wie?

Eine **digitale Signatur** ist eine Anwendung der **asymmetrischen Kryptographie**, bei der eine Nachricht mit dem **privaten Schlüssel** der sendenden Person „unterschrieben“ wird.  
Mit dem **zugehörigen öffentlichen Schlüssel** kann anschließend jeder prüfen, ob die Nachricht wirklich vom angegebenen Absender stammt und **nicht verändert wurde**.
[[]]
### Signaturerstellung 
$s = S(m, \text{GS}_A)$

### Signaturverifikation
$V(m, s, \text{ÖS}_A) {=} \text{ true}$

HINWEIS: In der Praxis werden nicht die gesamten Nachsrichten signiert, da dies seeeehr rechenintesiv wäre. Stattdessen signiert man sogenannte "Hash" 

### Anwendungsbeispiel 
Bei der Erstellung digitaler Zertifikate wird mit dem **privaten Schlüssel der Zertifizierungsstelle** und dem **Hashwert des Zertifikats** eine **digitale Signatur** erzeugt.  
Dadurch kann die **Authentizität des Zertifikats** überprüft und sichergestellt werden.

#digitaleSignatur #digitaleZertifikate
