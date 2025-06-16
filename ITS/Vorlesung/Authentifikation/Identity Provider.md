Ein **Identity Provider** wie Facebook oder Google stellt Dienstanbietern einen Service für Identifikation und Authentifikation bereit. Dadurch muss sich der Nutzer nur noch die Zugangsdaten zu einem einzigen Identity Provider merken, anstatt für jeden Dienst eigene Zugangsdaten zu verwalten.

### Vorteile
- Vereinfachte Anmeldung bei verschiedenen Diensten
- Weniger Passwörter zu merken

### Nachteile
- Es besteht die Gefahr eines **Single Point of Failure**, da der Ausfall beim Identity Provider viele Dienste gleichzeitig beeinträchtigen kann.

Um dieses Verfahren zu nutzen, muss der Nutzer zunächst eine Single Sign-On-Identität erstellen. Das standardisierte Protokoll hierfür ist OpenID
	1. OpenID Provider auswählen
	2. Identifikator auswählen (URL, die deine Identität darstellt - Email Adresse)
	3. Eingabe persönlicher Informationen
	4. Zugangsdaten festlegen