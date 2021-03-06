---
title: Vyrovnávání zatížení
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: c9d554dfd8d21b6e0e5f4aef0f4402e16485c2e8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807522"
---
# <a name="load-balancing"></a>Vyrovnávání zatížení
Jedním ze způsobů navýšení kapacity aplikace Windows Communication Foundation (WCF) je škálování je jejich nasazením do Vyrovnávání zatížení sítě serverové farmy. Aplikace WCF může být Vyrovnávané pomocí vyrovnávání techniky, včetně služby Vyrovnávání zatížení softwaru jako je například Vyrovnávání zatížení sítě Windows standardní zatížení, jakož i hardwarové zařízení pro vyrovnávání zatížení.  
  
 Následující části popisují důležité informace týkající se aplikace WCF vytvořené pomocí různých vazby poskytované systémem Vyrovnávání zatížení.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Vyrovnávání zatížení s vazby základní HTTP  
 Z perspektivy aplikací služby WCF, které komunikují pomocí vyrovnávání zatížení <xref:System.ServiceModel.BasicHttpBinding> nejsou jiné než jiné běžné typy HTTP síťový provoz (statický obsah HTML, stránek ASP.NET nebo webovými službami ASMX). Kanály WCF, které tuto vazbu používají jsou ze své podstaty bezstavové a ukončit jejich připojení Zavře kanál. Jako takový <xref:System.ServiceModel.BasicHttpBinding> pracuje s existující HTTP rozložení zátěže techniky.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> pošle hlavičku připojení protokolu HTTP v zprávy s `Keep-Alive` hodnotu, která umožňuje klientům vytvořit trvalé připojení ke službám, které je podporují. Tato konfigurace nabízí lepší propustnost, protože dříve vytvořeno, že připojení lze opětovně použít k odeslání dalších zpráv na stejném serveru. Opakované použití připojení však může způsobit klientů se důrazně přidružené k určitému serveru ve farmě Vyrovnávání zatížení sítě, což snižuje efektivitu Vyrovnávání zatížení pomocí kruhového dotazování. Pokud je toto chování žádoucí, HTTP `Keep-Alive` lze vypnout na serveru pomocí <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost s <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definovaných <xref:System.ServiceModel.Channels.Binding>. Následující příklad ukazuje, jak to provést pomocí konfigurace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 Pomocí zjednodušená konfigurace byla zavedená v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], stejné chování lze provést pomocí následujících zjednodušená konfigurace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Vyrovnávání zatížení s WSHttp vazby a WSDualHttp vazby  
 Jak <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> může být s vyrovnáváním zatížení pomocí techniky Vyrovnávání zatížení HTTP zadaný několik úprav výchozí vazby konfigurace.  
  
-   Vypnout navázání kontextu zabezpečení: To lze provést nastavení <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost <xref:System.ServiceModel.WSHttpBinding> k `false`. Případně, pokud zabezpečení relací, je možné použít stavová zabezpečení relace, jak je popsáno v [zabezpečené relace](../../../docs/framework/wcf/feature-details/secure-sessions.md) tématu. Stavová zabezpečení relací povolit službu zůstat bezstavové jako všechny stavu pro relaci zabezpečení se přenášejí při každém požadavku jako součást ochrany token zabezpečení. Všimněte si, že pokud chcete povolit relaci stavová zabezpečení, je potřeba použít <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definovaných <xref:System.ServiceModel.Channels.Binding> jako nezbytné konfigurace nastavení se nezobrazí na <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> jsou k dispozici v systému.  
  
-   Nepoužívejte spolehlivé relace. Tato funkce je ve výchozím nastavení vypnutý.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Vazba Net.TCP Vyrovnávání zatížení  
 <xref:System.ServiceModel.NetTcpBinding> Může být s vyrovnáváním zatížení pomocí techniky pro vyrovnávání zatížení vrstvy IP. Ale <xref:System.ServiceModel.NetTcpBinding> fondy připojení TCP ve výchozím nastavení ke snížení latence připojení. Toto je optimalizace, která brání systému základní mechanismus Vyrovnávání zatížení. Hodnota primární konfigurace pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, která je součástí fondu nastavení připojení. Sdružování připojení způsobí, že připojení klientů k přidružené ke konkrétním serverům v rámci farmy. Stejně jako životnost tato připojení zvýšit (faktor, který řídí nastavení časový limit zapůjčení), je distribuce zatížení mezi různými servery ve farmě se stane nevyváženou. V důsledku volání průměr prodlužuje čas. Ano, při použití <xref:System.ServiceModel.NetTcpBinding> ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozí časový limit zapůjčení používané vazby. Vypršení časového limitu 30 sekund zapůjčení je přiměřené výchozím bodem pro scénáře s vyrovnáváním zatížení, i když optimální hodnota je aplikace závislá. Další informace o časový limit zapůjčení kanálu a ostatní přenosové kvóty najdete v tématu [přenosové kvóty](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Chcete-li dosáhnout optimálního výkonu ve scénářích s vyrovnáváním zatížení, zvažte použití <xref:System.ServiceModel.NetTcpSecurity> (buď <xref:System.ServiceModel.SecurityMode.Transport> nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy hostování Internetové informační služby](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
