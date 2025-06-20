### Typ 0
DOM-basiertes XSS  ist eine clientseitige Schwachstelle. Angreifende nutzen diese aus, indem unter Einsatz eines vorhandenen vertrauenswürdigen Skripts Schadcode in das DOM (Document Object Model) eingefügt wird.

- Server kann Angriffsvektor nicht erkennen

### Typ 1
Reflektiertes XSS ist ein Angriffsvektor indem der Server (bösartige) Eingaben ohne weitere Prüfung in die HTTP-Antwort einfügt

- Der Server hat die Möglichkeit den Angriffsvektor zu erkennen und zu verhindern

### Typ 2
Bei Stored XSS Angriffsvektoren speichert die Web-Anwendung Schadcode persistent ab. Der Code wird später vom Server in Antworten mit ausgeliefert

- Bei reflektierten XSS wird der Schadcode nur in die unmittelbare Antwort eingefügt. Bei Type II Angriffen in jede Antwort

### Cross-Site Request Forgery (CSRF)
- Der Nutzer ist bei `bank.com` angemeldet → sein Browser hat ein gültiges **Session-Cookie**.
- Der Nutzer besucht eine **bösartige Seite** (`evil.com`).
- Diese Seite enthält einen versteckten **Request an `bank.com`**     
- **Der Browser sendet automatisch die Session-Cookies mit**, weil er `bank.com` vertraut.
- `bank.com` denkt: „Ah, das ist ein legitimer eingeloggter Nutzer“, und führt den Request aus – obwohl **der Nutzer das nie wollte**.

--> CSRF nutzt aus, dass der Browser Cookies automatisch an vertraute Seiten mitsendet (Coookieverwaltung)

![[CSRF.jpg]]

###### Schützen durch CSRF-Token:
- Der Server generiert einen Token und bettet ihn in das HTML der Webseite ein.
- Der Client schickt diesen Token bei jedem relevanten Request mit.
- Ein Angreifer kann den Token nicht einfach aus dem HTML auslesen, da die Same-Origin Policy (SOP) ihn daran hindert, Code in einem anderen Origin auszuführen.
###### Schützen durch SameSite Cookies:
- Das SameSite-Flag wird bei Cookies gesetzt.
- Dieses Flag verhindert, dass Cookies bei Cross-Origin-Requests (also Requests, die von Webseiten mit anderen Origins stammen) mitgesendet werden.