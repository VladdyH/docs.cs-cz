### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>Vazby WCF s režim zabezpečení TransportWithMessageCredential

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.6.1, vazby WCF, který používá režim zabezpečení TransportWithMessageCredential lze nastavit pro příjem zpráv s bez znaménka &quot;k&quot; záhlaví zabezpečení asymetrického klíče. Ve výchozím nastavení, bez znaménka &quot;k&quot; hlavičky budou odmítnuty v rozhraní .NET Framework 4.6.1. Jsou pouze přijme-li do tohoto nového režimu operace pomocí konfigurační přepínač Switch.System.ServiceModel.AllowUnsignedToHeader požádá o aplikaci.|
|Doporučení|Protože jde o funkci vyjádření souhlasu se službou, by neměla ovlivňují chování stávající aplikace.<br/>Pokud chcete řídit, jestli se používá nové chování, nebo Ne, použijte následující nastavení konfigurace:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Rozsah|Transparentní|
|Version|4.6.1|
|Typ|Změna cílení|
|Ovlivněná rozhraní API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

