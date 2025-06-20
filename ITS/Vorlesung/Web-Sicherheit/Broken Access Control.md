Tritt auf, wenn Nutzer auf Ressourcen oder Funktionen zugreifen können, für die sie keine Berechtigung haben (gebrochene Zugriffkontrolle)
- vertikal - Zugriff auf Daten/Funktionen anderer Nutzergruppen
- horizontal - Zugriff auf Daten/Funktionen anderer Nutzer
- kontextabhängig - Zugriff auf auf Daten/Funktion basierend auf dem Zustand der Anwendung

### Insecure Direct Object Referencing (IDOR)
IDOR ist eine spezielle Form von Broken Access Control, bei der interne Objektreferenzen (z. B. Dateinamen, Datenbank-IDs) direkt in URLs oder API-Anfragen verwendet werden. Angreifer können die Referenz manipulieren (z. B. eine ID ändern) und so auf Daten oder Funktionen zugreifen, die ihnen eigentlich nicht gehören.
###### Gegenmaßnahmen:
- Immer prüfen, ob der Nutzer berechtigt ist, auf das angeforderte Objekt zuzugreifen
- Referenzen nicht direkt verwenden, sondern z. B. indirekt referenzieren und an Session binden