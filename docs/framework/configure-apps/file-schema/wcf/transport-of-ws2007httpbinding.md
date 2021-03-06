---
title: '&lt;transport&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 692befa3-8b0b-4ec5-b601-755874e98eb0
ms.openlocfilehash: 5c7e96beee2fc1e4780729e56f10a52b63dde4e8
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841414"
---
# <a name="lttransportgt-of-ltws2007httpbindinggt"></a>&lt;transport&gt; – &lt;ws2007HttpBinding&gt;
Definuje nastavení ověřování pro přenos pomocí protokolu HTTP.  
  
 \<system.serviceModel>  
\<vazby >  
\<ws2007HttpBinding>  
\<Vytvoření vazby >  
\<zabezpečení >  
\<přenos >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
transport clientCredentialType =   
       "Basic/Certificate/Digest/None/Ntlm/Windows"  
       proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
       realm="string"   
```  
  
## <a name="type"></a>Typ  
 <xref:System.ServiceModel.HttpTransportSecurity>  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`clientCredentialType`|Určuje přihlašovací údaje pro ověření klienta ke službě. Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.|  
|`proxyCredentialType`|Určuje přihlašovací údaje pro ověření klienta pro proxy server domény. Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|`realm`|Sféra ověřování hodnotou hash nebo základní ověřování. Výchozí hodnota je prázdný řetězec.<br /><br /> Sféra ověření určuje nejméně název hostitele, který provádí ověřování. Můžete také určit kolekci uživatelů, kteří mají přístup. Sféra ověření k určení, která z nich několik možných uživatelská jména a hesla je možné dotazovat uživatele.|  
  
## <a name="clientcredentialtype-attribute"></a>Typ clientCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázaná.|  
|Základní|Používá základní ověřování.|  
|ověřování algoritmem Digest|Použití ověřování algoritmem digest.|  
|NTLM|Ověřování protokolem NTLM se používá jako nouzové řešení pomocí domény Windows.|  
|Windows|Používá integrované ověřování Windows.|  
|Certifikát|Certifikáty X.509 používá k ověření klienta.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázaná.|  
|Základní|Používá základní ověřování.|  
|ověřování algoritmem Digest|Použití ověřování algoritmem digest.|  
|NTLM|Používá NTLM jako nouzové řešení pomocí domény Windows.|  
|Windows|Používá integrované ověřování Windows.|  
|Certifikát|Certifikáty X.509 používá k ověření klienta.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-ws2007httpbinding.md)|Představuje možnosti zabezpečení [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.WSHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpTransportSecurityElement>  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
