- Datum: 2025.05.30
- Vorlesung: [Symmetrische Verschlüsselung](https://moodle.w-hs.de/pluginfile.php/699130/mod_resource/content/1/04_Symetrische_Verschluesselung.pdf)

In dem vierten Kapitel "symmetrische Verschküsselungen" habe ich die symmetrische Verschlüssselung kennen gelernt und mir als Beipsiels die Produktverschlüselung des AES Algorithmus angeschuat.

**Bevor wir uns aber den Algorithmus anschauen, erkläre ich zunächst einige Grundbegriffe.**  
Unter einer _symmetrischen Verschlüsselung_ versteht man im Grunde eine Verschlüsselungsmethode, bei der beide Gesprächspartner denselben Schlüssel verwenden, der sowohl zum Ver- als auch zum Entschlüsseln genutzt wird ([[symmetrische_Verschlüsselung.png]]).
#symmetrischeVerschlüsselung

Eine Verschlüsselung wird _Produktverschlüsselung_ genannt, sobald sie eine Kombination aus mehreren Elementarverschlüsselungen (XOR, Substitution, Permutation, ...) nutzt und dadurch kryptographische Eigenschaften einer sicheren Verschlüsselung wie _Konfusion_ und _Diffusion_ sichergestellt werden. #Elementarverschlüsselungen #Produktverschlüsselung

**Konfusion** beschreibt die Verschleierung der Struktur des Klartexts, was durch Substitution erreicht werden kann. Ziel ist es, es einem Angreifer möglichst schwer zu machen, den Inhalt des Gesprächs zu verstehen.
#Konfusion

**Diffusion** hingegen versucht, Musteranalysen/Häufigkeitsanalysen durch den Angreifer nutzlos zu machen, indem bereits kleine Veränderungen im Klartext große Änderungen im Chiffretext verursachen.
Erreicht wird dies durch Strukturänderungen auf Block bzw. bitebene. Man verteilt die Information eines einzelnen Klartextzeichens über den Chiffretext. Nehmen wir als Beispiel den Klartext „HELLO“, den wir in Zahlen umwandeln (H=8, E=5, L=12, O=15). Nach einer einfachen Permutation, bei der das letzte Zeichen an den Anfang verschoben wird, erhalten wir die Folge 15, 8, 5, 12, 12. Ändern wir jetzt nur das letzte Zeichen von „O“ zu „P“ (P=16), so wird daraus 16, 8, 5, 12, 12.
Um die Diffusion zu verstärken, multiplizieren wir jeweils zwei benachbarte Zahlen modulo 26. Für „HELLO“ ergibt das 16, 14, 8, 14, während es für „HELLP“ 24, 14, 8, 14 wird. Obwohl sich im Klartext nur ein Buchstabe geändert hat, unterscheidet sich der Chiffretext an mehreren Stellen deutlich.
#Diffusion

Symmetrische Verschlüsselungen lassen sich sowohl mit **Blockchiffren** als auch mit **Stromchiffren** realisieren ([[strom-blockchiffre.jpg]]), wobei es bisher keine allgemein als sicher anerkannten Algorithmen für Stromchiffren gibt.  
Bei einer Stromchiffre werden mehrere Schlüssel aus einem Hauptschlüssel abgeleitet, die dann nacheinander mit den einzelnen Zeichen des Klartexts per XOR verknüpft werden.  
Dagegen verschlüsselt eine Blockchiffre den Klartext blockweise, typischerweise in Blöcken von 128, 192 oder 256 Bit, mit einem einzigen Schlüssel.
#Blockchiffre #Stromchiffre

### AES [[AES_Ablauf.jpg]]
Der AES-Algorithmus ist eine bewährte Blockchiffre, die mit Schlüssellängen von 128, 192 oder 256 Bit arbeitet und auf 128-Bit-(16-Byte-)Blockgrößen operiert. Die Verschlüsselung besteht aus mehreren Runden, die jeweils aus vier Schritten bestehen.  
Der erste Schritt jeder Runde ist die sogenannte **Byte-Substitution**. Dabei wird der Klartextblock noch vor dem ersten Schritt in ein zweidimensionales Array, den sogenannten **State** (eine 4x4-Byte-Matrix), umgewandelt. Anschließend wird jeder Eintrag der Matrix durch eine Substitution mittels einer **öffentlichen S-Box** ersetzt.

Im nächsten Schirtt, der sogenannten SHiftRow-Transformation (permutation), werden die einezelnen Reihen der Matrix verschoben 

- 1. Reihe: bleibt unverändert  
- 2. Reihe: 1 Byte nach links verschoben
- 3. Reihe: 2 Bytes nach links verschoben
- 4. Reihe: 3 Bytes nach links verschoben

Im dritten Schritt, **MixColumns**, wird jede Spalte der 4x4-Byte-Matrix des Klartextblocks mit einer festen, öffentlichen Matrix multipliziert.

Im letzten Schritt, **AddRoundKey**, wird jeder Block einzeln mit dem jeweiligen Rundenschlüssel per XOR verknüpft. Der Rundenschlüssel ist der einzige geheime Parameter in diesem Vorgang. 

Dieser Schritt steht in engem Zusammenhang mit dem **Kerckhoffschen Prinzip**, das besagt, dass ein Kryptosystem auch dann sicher sein muss, wenn der Angreifer den Algorithmus kennt. Nur der Schlüssel darf geheim bleiben. Durch die AddRoundKey-Operation wird genau dieser geheime Schlüssel eingebunden, sodass ohne ihn keine Entschlüsselung möglich ist.
#AES-Algorithmus #KerckhoffschePrinzip



------

n Partner benötigen $\frac{n \cdot (n - 1)}{2}$ Schlüssel

