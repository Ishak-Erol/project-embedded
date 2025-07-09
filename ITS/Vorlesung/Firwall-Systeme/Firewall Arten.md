 ![[IsoOsiTcpIp.jpg]]
Eine Firewall besteht unter anderem aus einem **Analysemodul**, das Datenpakete untersucht und an das Entscheidungsmodul weiterleitet. Je nach Art der Firewall ist dieses Analysemodul unterschiedlich aufgebaut. Folgende drei Firewalls, die ein solches Analysemodul beinhalten, wurden in der Vorlesung thematisiert:
1. [[#Paket Filter]]
2. [[#Application Gateway]]
3. [[#Next Generation Firewall]]

### Paket Filter
Ein **Paketfilter** analysiert Datenpakete auf Netzwerk- und Transportschicht (OSI-Schicht 3 & 4).  
Er trifft Entscheidungen auf Basis von **IP-Adressen, Ports und Protokollen**, **ohne** die Inhalte der Pakete zu untersuchen.

Beispiel: Nur TCP-Verbindungen auf Port 80 von einer bestimmten IP-Adresse werden erlaubt.

### Application Gateway 
Ein **Application Gateway** ist eine spezielle Art von Firewall, die Verbindungen auf **Anwendungsebene** (OSI-Schicht 7) kontrolliert. Dabei werden ausschließlich Datenpakete für bestimmte **Dienste** zugelassen. So kann beispielsweise konfiguriert werden, dass nur **HTTP-Verkehr** erlaubt ist, selbst wenn dieser über einen **ungewöhnlichen Port** wie 456 abgewickelt wird oder dass nur Webseite "xyz.com" blockiert werden soll auch wenn es das selbe Protokoll wie zugelassene Webseiten benutzt (z.B. HTTPS).
UNTERSCHIED: Paket Filter würde in dem Beispiel entweder alle webseiten blockieren oder keins.

Zur Umsetzung wird häufig eine **Software** eingesetzt, auch bezeichnet als **Proxy** (Kurzform für „Stellvertreter“). Der Proxy übernimmt dabei eine zentrale Rolle bei der **Trennung** des **unsicheren Netzwerks** (z. B. dem Internet) vom **internen, geschützten Netzwerk**. Aus Sicht des Nutzers scheint es, als würde er direkt mit dem Zielsystem kommunizieren. Tatsächlich jedoch sendet der Client seine Anfragen an den Proxy, der diese analysiert im eigenen Namen an das Zielsystem weiterleitet.
![[ApplicationGateway.jpg]]

### Next generation Firewall
Eine Next Generation Firewall (NGFW) ist eine erweiterte Form der Firewall, die neben den klassischen Funktionen wie Paketfilterung auch die Analyse des Datenverkehrs auf Anwendungsebene ermöglicht. Dadurch kann sie Anwendungen unabhängig vom verwendeten Port erkennen und gezielt kontrollieren (vgl. Application Gateway). NGFWs verfügen zusätzlich über die Fähigkeit, Datenströme einzelnen Nutzern anhand der IP-Adressen zuzuordnen. Diese nutzerbezogene Steuerung erlaubt es, Zugriffsrechte differenziert zu vergeben und bestimmte Dienste nur für ausgewählte Nutzer freizugeben oder zu blockieren.



### Wichtig
- Firewalls bieten keine Schutz für interen Angriffe
- Backdoors machen ganze Firewall-Systeme wirkungslos.
- je eingeschänkter die Verbindung umso geringer die Möglcihkeit mit externen Diensten zu kommunizieren (China)