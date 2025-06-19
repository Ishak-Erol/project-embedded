![[Firewall_aufbau.jpg]]
Protokollelement - Datenpakete, die durch das Firewall-System überprüft werden

Einbindungsmodul - Bindet die Firewall in das Kommunikationssystem ein und setzt Sicherheitsregeln technisch um, z. B. durch das Zulassen oder Blockieren von Datenpaketen

Analysemodul - Analysiert eingehende Pakete und leitet die Analyseergebnisse an das Entscheidungsmodul weiter

Authentifikationsmodul - Authentifiziert Nutzer und Prozesse anhand des Regelwerks und übermittelt diese Informationen ebenfalls an das Analysemodul zur weiteren Bewertung

Entscheidungsmodul - Vergleicht die Analyseergebnisse mit dem Regelwerk. Wird das Protokollelement zugelassen, aktiviert es das Einbindungsmodul zur Weiterleitung. Wird es **nicht zugelassen**, übergibt es die Informationen an das **Verarbeitungsmodul für sicherheitsrelevante Ereignisse**

Verarbeitungsmodul für sicherheitsrelevante Ereignisse - Reagiert auf erkannte Sicherheitsverstöße und leitet sicherheitsrelevante Informationen an das Logbuch weiter

Logbuch - Protokolliert sicherheitsrelevante Ereignisse, die vom Verarbeitungsmodul erkannt wurden

Regelwerk - Vom Security Manager definiert, enthält es die technischen Umsetzungen der Sicherheitsrichtlinien. Es wird vom Authentifikationsmodul, Entscheidungsmodul und Verarbeitungsmodul verwendet

Firewallschutzmodule - schützt Firewall vor Angriffen 

Sicherheitsmanagement - Erstellt und pflegt Sicherheitsregeln, analysiert Logbucheinträge und leitet daraus Maßnahmen zur Weiterentwicklung der Sicherheitsstrategie ab.