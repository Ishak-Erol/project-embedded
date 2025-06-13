**Einmal-Passwort-Verfahren (OTP)** bezeichnet ein Authentifikationsverfahren, bei dem das einzugebende Passwort nur einmalig gültig ist. Für jede Sitzung wird ein neues Passwort generiert, wodurch abgefangene Passwörter nicht wiederverwendet werden können.

Die geheimen Schlüssel zur Erzeugung dieser Einmal-Passwörter werden in der Regel in einem Sicherheitsmodul (z. B. SM-C) gespeichert. Dieses Modul kommuniziert über eine Schnittstelle mit den eingehenden Passwörtern, sodass der Server selbst keinen direkten Zugriff auf die Schlüssel erhält.
### Funktionsweise
1. Server generiert einen geheimen Schlüssel (symmetrischer Schlüssel) ()
2. Schlüssel wird mit Client geteilt (QR-Code)
3. Schlüssel wird im Sicherheitsmodul gespeichert (serverseitig)
4. Nutzer speichert den aus dem gescannten QR-Code gewonnenen Schlüssel in der Authenticator-App
5. Beim Login wird im Sicherheitsmodul OTP generiert und mit der Eingabe des Nutzers verglichen -- Nutzer findet sein OTP in der Authenticator APp

### Verfahren
1. zeitgesteuerte Generierung (Im Skript behandelt) 
		- Passwörter sind nur für einen bestimmten Zeitraum gültig
		- Passwörter werden nach gleichem Algo generiert
2. Ereignisgesteuerte Generierung
3. Generierung durch Anforderung des Servers


