Grundbegriffe: [[AuthentifkationAuthentisierungAutorisierung.jpg]]

Beim Passwort-Verfahren handelt es sich um das einfachste und am weitesten verbreitete Verfahren zur **Authentifizierung** (auch: **Authentifikation**) eines Nutzers.    
Man spricht hierbei von einem **Authentifizierungsfaktor der Kategorie „Wissen“**, da sich der Nutzer über sein Wissen ausweißt.

Daneben gibt es noch weitere Kategorien von Authentifizierungsfaktoren:

- **Besitz** – etwas, das man **hat** (z. B. ein Smartphone oder ein Token),
- **Biometrie** – etwas, das man **ist** (z. B. ein Fingerabdruck oder Gesichtserkennung),
- sowie Kombinationen daraus, wie bei der **Multi-Faktor-Authentifizierung** (z. B. Passwort + Fingerabdruck).
    
Im Folgenden betrachten wir drei **Angriffsvektoren**([[#Erraten]], [[#Abfangen]], [[#Entwenden]]), über die das Passwort-Verfahren verwundbar ist.
[[PWverfahrenAngriffsvektoren.jpg]]
### Erraten [[]]
Durch schlecht gewählte Passwörter wird es Angreifern erleichtert, das richtige Passwort systematisch zu **erraten**.  
Der direkteste Ansatz ist der sogenannte **Brute-Force-Angriff**: Dabei werden alle möglichen Passwortkombinationen systematisch ausprobiert.

Eine weitere Methode sind **Wörterbuchangriffe**. Hierbei verwendet der Angreifer Passwortlisten mit häufig verwendeten oder bereits geleakten Passwörtern, um gezielt schwache Passwörter zu finden.

Um sich vor solchen Angriffen zu schützen, sollte man:
- Ein möglichst **langes Passwort** wählen.
- Eine Kombination aus **Groß- und Kleinbuchstaben, Zahlen und Sonderzeichen** verwenden.  
  (Je mehr Zeichenarten und je länger das Passwort, desto mehr mögliche Kombinationen: $Anzahl Der Zeichen^{LaengeDesPWs}$) [[KombinationsMöglichkeiten.jpg]]
- **Passwörter nicht mehrfach verwenden**. 

Der Entwickler hingegen sollte:
- **Login-Versuche begrenzen**
- **Verwendung unsicherer Passwörter verbieten**, z. B. durch Abgleich mit bekannten Leak-Listen.

### Abfangen [[]]
Bei diesem Angriffsvektor agiert der Angreifer als **Man-in-the-Middle** und fängt das gesendete Passwort ab.  
Voraussetzung für den Erfolg ist, dass die Passwörter **unverschlüsselt übertragen** werden.

### Entwenden [[]]
Bei diesem Angriffsvektor versucht der Angreifer, an die in der Datenbank gespeicherten Passwörter zu gelangen.  
**Passwörter, die im Klartext gespeichert sind, sind hier ein leichtes Ziel für Angreifer.**
###### Idee 1: Symmetrische Verschlüsselung der Passwörter
- Beispiel: AES im ECB-Modus

- **Nachteil:**  
    Wenn der symmetrische Schlüssel kompromittiert wird, kann der Angreifer **alle Passwörter entschlüsseln**.  
    Außerdem gilt: Gleiche Passwörter führen zu gleichem Chiffretext, was Angriffe erleichtert.

##### Idee 2: Hashen der Passwörter
- Passwörter werden gehasht und die Hashwerte in der Datenbank gespeichert.
    
- **Nachteil:**  
    Gleiche Passwörter erzeugen denselben Hashwert.  
    Durch den Einsatz von **Rainbow Tables** kann ein Angreifer häufig verwendete Passwörter schnell zurückgewinnen („Compute now, use later“).

###### Idee 3: Hashen mit Salt
- Jedem Passwort wird ein eigener, zufälliger **Salt** hinzugefügt, der im Klartext in der Datenbank gespeichert wird.
- So haben gleiche Passwörter unterschiedliche Hashwerte

- **Nachteil:**  
    Brute-Force-Angriffe sind weiterhin möglich, wenn der Salt bekannt ist.

##### Idee 4: Hash-Stretching mit Argon2
- Verwendet ressourcenintensive Algorithmen wie **Argon2**, um das Berechnen der Hashwerte zeit- und rechenintensiver zu machen.
- Dadurch werden Brute-Force-Angriffe deutlich erschwert.

##### Idee 4+ : Verwendung von Pepper zusätzlich zum Salt
- Neben dem Salt wird ein geheimer **Pepper** verwendet, der für alle Passwörter gleich ist.
- Der Pepper wird **nicht in der Datenbank gespeichert**, sondern in der **Anwendungslogik** geheim gehalten.
- Dies erhöht die Sicherheit, da ein Angreifer, der nur die Datenbank erbeutet, den Pepper nicht kennt.