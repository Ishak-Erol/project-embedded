Stell dir vor, **Alice** möchte dem **Bob** eine vertrauliche und gleichzeitig überprüfbare Nachricht schicken. Damit das funktioniert, macht Alice Folgendes:

Zuerst erstellt sie einen **zufälligen symmetrischen Schlüssel**, den sie nur für diese Kommunikation mit Bob verwenden möchte. Dieser Schlüssel ist später dafür da, die eigentliche Nachricht schnell und effizient zu verschlüsseln – denn symmetrische Verschlüsselung (wie AES) ist viel schneller als asymmetrische.

Jetzt hat Alice aber ein Problem: Wie kann sie diesen geheimen Schlüssel sicher an Bob übertragen? Dafür benutzt sie die **asymmetrische Verschlüsselung**. Bob besitzt nämlich ein Schlüsselpaar: einen öffentlichen und einen privaten Schlüssel. Dieses Schlüsselpaar wurde Bob zuvor erzeugt, entweder durch ihn selbst oder durch eine vertrauenswürdige Zertifizierungsstelle (z. B. eine offizielle Behörde oder ein Dienstanbieter), die Bob’s öffentlichen Schlüssel bestätigt und verbreitet. Bob hält seinen privaten Schlüssel geheim und gibt nur den öffentlichen Schlüssel weiter.

Alice verschlüsselt den geheimen Schlüssel mit Bobs **öffentlichem Schlüssel** – und nur Bob kann ihn später mit seinem **privaten Schlüssel** wieder entschlüsseln. So wird der geheime Schlüssel sicher über das unsichere Internet übertragen.

Nachdem das erledigt ist, verschlüsselt Alice die Nachricht mit dem gerade erzeugten symmetrischen Schlüssel. Zusätzlich berechnet sie noch eine Art "digitalen Fingerabdruck" der Nachricht (ein sogenannter MAC), der sicherstellt, dass die Nachricht auf dem Weg nicht verändert wurde.

Anschließend sendet Alice drei Dinge an Bob:

1. Den verschlüsselten geheimen Schlüssel,
    
2. die verschlüsselte Nachricht und
    
3. den MAC.
    

Wenn Bob das empfängt, kann er zuerst mit seinem privaten Schlüssel den geheimen Schlüssel entschlüsseln. Dann entschlüsselt er die eigentliche Nachricht und prüft mit dem MAC, ob sie unterwegs verändert wurde.

Das Besondere daran:

- Der **asymmetrische Teil** sorgt dafür, dass der Schlüssel sicher bei Bob ankommt.
    
- Der **symmetrische Teil** sorgt für eine schnelle, sichere Nachrichtenverschlüsselung.
    
- Der **MAC** stellt sicher, dass niemand heimlich etwas verändert hat.