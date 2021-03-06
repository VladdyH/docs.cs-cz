---
title: '&lt;Diagnostika&gt;'
ms.date: 03/30/2017
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
ms.openlocfilehash: 0854ce6525fd7c96cf7c19d2c86dadef1b9a53bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747304"
---
# <a name="ltdiagnosticsgt"></a>&lt;Diagnostika&gt;
`diagnostics` Element definuje nastavení, které lze použít správce pro spuštění kontroly a řízení.  
  
 \<system.ServiceModel>  
\<Diagnostika >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.serviceModel>  
  <diagnostics 
      etwProviderId="String"       
      performanceCounters="Off/ServiceOnly/All/Default"              
      wmiProviderEnabled="Boolean" >       
    <endToEndTracing 
        activityTracing="Boolean"  
        messageFlowTracing="Boolean"  
        propagateActivity="Boolean" />  
    <messageLogging 
        logEntireMessage="Boolean"  
        logMalformedMessages="Boolean"  
        logMessagesAtServiceLevel="Boolean"  
        logMessagesAtTransportLevel="Boolean"  
        maxMessagesToLog="Integer"  
        maxSizeOfMessageToLog="Integer" >  
      <filters>  
        <clear />  
      </filters>  
    </messageLogging>  
  </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|etwProviderId|Řetězec, který určuje identifikátor pro zprostředkovatele trasování událostí, která zapisuje události relací trasování událostí pro Windows.|  
|čítače výkonu|Určuje, zda jsou povoleny čítače výkonu pro sestavení. Platné hodnoty jsou<br /><br /> -Vypnutí: Čítače výkonu jsou zakázány.<br />-ServiceOnly: Je povoleno pouze čítače výkonu relevantní pro tuto službu.<br />-Všechny: Výkonu čítače lze zobrazit v době běhu.<br />-Výchozí: Je vytvořen _WCF_Admin instance čítače výkonu jeden. Tato instance slouží k povolení shromažďování těchto dat SQM pro používá infrastrukturu. Žádná z hodnoty čítače pro tuto instanci jsou aktualizovány a proto zůstanou na nule. Toto je výchozí hodnota, pokud není k dispozici pro WCF žádná konfigurace.|  
|wmiProviderEnabled|Logická hodnota, která určuje, zda je povoleno zprostředkovatele rozhraní WMI pro sestavení. Zprostředkovatel rozhraní WMI pro uživatele je potřeba k získání přístupu spuštění kontroly a řízení funkcí služby Windows Communication Foundation (WCF). Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<endToEndTracing >](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|Konfigurace element, který umožňuje povolit nebo zakázat různé aspekty začátku do konce trasování během spuštění aplikace služby.|  
|[\<messageLogging >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|Popisuje nastavení pro protokolování zpráv WCF.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|ServiceModel|Kořenový element všechny konfigurační prvky WCF.|  
  
## <a name="remarks"></a>Poznámky  
 `diagnostics` Oddíl definuje nastavení diagnostiky pro všechny služby, které jsou umístěné v sestavení. Není možné definovat nastavení samostatné diagnostiky na úrovni služby, pokud existuje jenom jedna služba v sestavení. Atributy se nastavují v souladu s požadavky oddílu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<diagnostics
    wmiProviderEnabled="false"  
    performanceCounters="all">  
  <messageLogging 
      logEntireMessage="true"  
      logMalformedMessages="true"  
      logMessagesAtServiceLevel="true"  
      logMessagesAtTransportLevel="true"  
      maxMessagesToLog="42"  
      maxSizeOfMessageToLog="42">  
    <filters>  
      <clear />  
    </filters>  
  </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>
