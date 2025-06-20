Das hypertrext transfer Protocol (HTTP) ist das am häufigste genutzte Prokoll im Internet, voallem für die Kommunikatio zwischen Webbrosern und Webservern.

Das **HTTP-Protokoll** basiert auf **textuellen Daten** und ist **zustandslos**. Das bedeutet, dass der Server **keine Informationen über frühere Anfragen eines Clients speichert**. Ohne zusätzlichen Mechanismus wäre es z. B. **nicht möglich**, einen Artikel in einen Warenkorb zu legen und diesen später auf der Webseite noch zu sehen – denn HTTP „vergisst“ vorherige Interaktionen. Um Sitzungsinformationen über mehrere HTTP-Anfragen hinweg zu speichern, werden sogenannte **Session Cookies** eingesetzt. Diese speichert der Browser und sendet sie bei jeder neuen Anfrage mit.
![[HTTP.jpg]]
Aufbau eines HTTP-Request:
`<request methode> <Request-URI> <HTTP-Version>\r\n`
`<Header-Name>: <Header-Wert>\r\n`
`Cookie: session=1234-abcd          ← optional, wenn Session-Cookie vorhanden`
`...`
`\r\n`
`<Request-Body>                     ← optional, z. B. bei POST`


Aufbau eines HTTP-Response
`<HTTP-Version> <Status-Code>\r\n`
`<Header-Name>: <Header-Wert>\r\n`
`Set-Cookie: session=1234-abcd      ← optional, bei erstmaliger Session-Erstellung`
`...`
`\r\n`
`<Response-Body>                    ← optional`


![[URL.jpg]]

### Statuscode
| Kategorie | Bedeutung    | Beispiele                      |
| --------- | ------------ | ------------------------------ |
| **1xx**   | information  | 100 Continue                   |
| **2xx**   | succcesful   | 200 OK, 201 Created            |
| **3xx**   | redirection  | 301 Moved Permanently          |
| **4xx**   | client-error | 400 Bad Request, 404 Not Found |
| **5xx**   | server-error | 500 Internal Server Error      |
