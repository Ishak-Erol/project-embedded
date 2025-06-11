Für Blockchiffren haben sich darüber hinaus vier bewährte kryptographische Betriebsmodi entwickelt, die unterschiedliche Sicherheitsanforderungen erfüllen (Skizze). Diese sind:

- **Electronic Code Book Mode** #ECB  
- **Cipher Block Chaining Mode** #CBC
- **Counter Mode**  #CTR 
- und **Galois/Counter Mode** #GCM 

Jeder Modus hat spezielle Eigenschaften und Einsatzbereiche, die sich auf Sicherheit und Performance auswirken.
[[Mode_of-Operations.jpg|Mode of Operations]]

## ==Electronic Code Book Mode==
Beim **ECB-Modus** arbeitet der Algorithmus mit 256-Bit-Blöcken. Dabei wird der Klartext in Blöcke aufgeteilt und jeder Block einzeln mit demselben AES-Schlüssel (Masterkey, aus dem die Rundenschlüssel abgeleitet werden) verschlüsselt. Der Empfänger entschlüsselt die Blöcke mit demselben Schlüssel .

Der Nachteil dieses Modus ist, dass bei gleichem Klartextblock und gleichem Schlüssel immer derselbe Chiffretextblock entsteht. Dadurch können Muster im Chiffretext sichtbar bleiben, was die Analyse durch einen Angreifer erleichtert ([[ECB_Beispielbild.png]]).

## ==Cipher Block Chaining Mode==
Der **CBC-Modus** (Cipher Block Chaining) versucht, die Problematik des ECB-Modus zu umgehen, indem zu Beginn der Verschlüsselung ein zufällig generierter **Initialisierungsvektor (IV)** mit dem ersten Klartextblock per XOR verknüpft wird. Dadurch unterscheiden sich die Chiffretexte auch bei gleichen Klartextblöcken im ersten Block.

Innerhalb eines Blocks können sich somit die Chiffretexte nicht wiederholen. Allerdings können sich bei gleichem IV und Schlüssel die Chiffretexte in unterschiedlichen Nachrichten trotzdem gleichen.

Ein weiteres Problem des CBC-Modus ist die **Fehlerfortpflanzung**: Wenn ein Fehler im Chiffretext eines Blocks auftritt, beeinflusst das nicht nur die Entschlüsselung dieses Blocks, sondern auch des darauffolgenden Blocks, da jeder Klartextblock mit dem Chiffretext des vorherigen Blocks XOR-verknüpft wird.

## ==Galois/Counter Mode==
Beim GCM-Modus wird auf 128 bit Blöcken mit einem Initialisierungsvektor gearbeitet. Neben der Verschlüsselung ermöglicht GCM auch die Authentifizierung. Der AES-Algorithmus erhält als Eingabe einen Zählerwert (GCM-Zähler), der bei jedem Block erhöht wird, sowie den geheimen Schlüssel. Die AES-Ausgabe dient als Schlüsselstrom (Verschlüssleungsmaske aus gehiemern Schlüssel und IV/Zähler) und wird mit dem jeweiligen Klartextblock per XOR verknüpft, wodurch der Chiffretext entsteht.

Zur Authentifizierung werden die sogenannten authentifizierten Daten blockweise verarbeitet. Jeder dieser Blöcke wird mit einem geheimen Hash-Schlüssel H multipliziert. Dieses Zwischenergebnis , häufig als „MULT“ bezeichnet,  bildet die Grundlage für die Authentifizierungsprüfung und wird über alle Blöcke hinweg fortgeführt.

Am Ende der Berechnung wird zusätzlich ein Block eingebracht, der sich aus der Bitlänge der authentifizierten Daten und der Bitlänge des Chiffretexts zusammensetzt. Dieses finale Zwischenergebnis wird dann mit der AES-Ausgabe des initialen Zählerwerts XOR-verknüpft. Das Resultat ist der sogenannte Tag – ein Authentifizierungscode, der sicherstellt, dass weder die verschlüsselten noch die authentifizierten Daten manipuliert wurden.