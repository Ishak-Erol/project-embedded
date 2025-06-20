### [[Cross-Site Scripting|Cross-Site Scripting (XSS)]]
Cross-Site Scripting ist ein Injection Angriff bei dem malicious Code in guartige Webseiten eingefügt werden.
![[XSS.jpg]]
Wir unterscheiden zwischen 
- DOM basiertem XSS (Typ 0)
- Refelected XSS (Type 1)
- Stored XSS (Typ 2)

### Code Injection
Coed Injection ist ein Injection Angriff bei dem malicious Input von dem Nutzer (Angreifer) als Befehl interpretiert wird

`public int ping(String ipAddress) throws IOException, InterruptedException {`
    `Process process = Runtime.getRuntime().exec("cmd.exe /c ping " + ipAddress);`
    `int statusCode = process.waitFor();`
    `return statusCode;`
`}`

Input: 
	`ping("8.8.8.8 & echo test");`
	
Ausgeführt wird: 
	`cmd.exe /c ping 8.8.8.8 & echo test`

Wie können wir uns schützen? 
- Nach Möglichkeit keine Betriebssystembefehl direkt ausführen (kann oft über die Programmiersprache erfolgen) 
- Begrenzung und Bereinigung („sanitize“) von erlaubten Sonderzeichen (escape characters) 
- Betriebssystembefehle mit einem Nutzeraccount ausführen, der sehr limitierte Rechte hat („priviledge Seperation“)
### SQL Injection

**Stacked SQL injection**
	`SELECT * FROM users WHERE id = 'id'; SELECT * FROM kunden --'`

**tautology based SQL injection**
	`SELECT * FROM users WHERE id = '' OR 1=1 --'`

**Union operator based SQL injection**
	`SELECT username, age FROM users WHERE id = '1'`
	`UNION`
	`SELECT password, salt FROM passwords --'`

Wie können wir uns schützen? 
- Anstatt „hardcoding“ der SQL-Statements vorzunehmen, Objekte der Klasse PreparedStatement nutzen 
`String name = "tobias";`
`PreparedStatement myStmt = myCon.prepareStatement("SELECT * FROM users WHERE name = ?");`
`myStmt.setString(1, name);`
`ResultSet rs = myStmt.executeQuery();`
