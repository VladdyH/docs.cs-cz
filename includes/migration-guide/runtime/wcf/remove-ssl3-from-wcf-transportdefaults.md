### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a>Odebrání Ssl3 WCF TransportDefaults

|   |   |
|---|---|
|Podrobnosti|Při použití NetTcp se zabezpečením přenosu a přihlašovacích údajů typu certifikátu, protokol SSL 3 je již výchozí protokol použitý pro vyjednávání zabezpečeného připojení. Ve většině případů by měl existovat žádný vliv na stávající aplikace jako TLS 1.0 vždy byla zahrnuta do seznamu protokolů pro NetTcp. Všichni existující klienti měli být schopni vyjednat připojení pomocí na nejnižší protokol TLS 1.0.|
|Doporučení|Ssl3 je potřeba, použijte jednu z následujících mechanismů konfigurace Ssl3 přidat do seznamu vyjednávaný protokolů.<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li>[&lt;sslStreamSecurity&gt; část &lt;customBinding&gt;] ~ / docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</li></ul>|
|Rozsah|Edge|
|Version|4.6.2|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|

