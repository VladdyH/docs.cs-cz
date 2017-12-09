---
title: "ICorRuntimeHost – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost
helpviewer_keywords: ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 844648cd2cfafc561e27bea870703ee3a55fb404
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost – rozhraní
Poskytuje metody, které umožní hostitele spuštění a zastavení common language runtime (CLR) explicitně, vytvořte a nakonfigurujte aplikační domény, pro přístup k výchozí doméně a chcete získat výčet všech domén, které jsou spuštěné v procesu.  
  
 V rozhraní .NET Framework verze 2.0, toto rozhraní oprávněni [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Closeenum – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Obnoví enumerátor domény zpět na začátek seznamu domény.|  
|[CreateDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Vytvoří doménu aplikace. Volající obdrží ukazatele rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[Createdomainex – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Vytvoří doménu aplikace. Tato metoda umožňuje volajícímu předat instanci iappdomainsetup – Chcete-li konfigurovat další funkce vrácený <xref:System._AppDomain> instance.|  
|[Createdomainsetup – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Získá ukazatele rozhraní typu `IAppDomainSetup` k <xref:System.AppDomainSetup> instance. `IAppDomainSetup`poskytuje metody pro konfiguraci aspektů domény aplikace předtím, než se vytvoří.|  
|[Createevidence – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Získá ukazatele rozhraní typu <xref:System.Security.Principal.IIdentity>, což umožňuje na hostiteli a poté vytvořit důkaz zabezpečení mají být předány [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) nebo [createdomainex –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[Createlogicalthreadstate – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Nepoužívejte.|  
|[CurrentDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Získá ukazatele rozhraní typu <xref:System._AppDomain> představující domény načtené na aktuální vlákno.|  
|[Deletelogicalthreadstate – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Nepoužívejte.|  
|[Enumdomains – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Získá enumerátor pro domény v aktuálním procesu.|  
|[Getconfiguration – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Získá objekt, který umožňuje na hostiteli a poté zadejte konfiguraci zpětného volání modulu CLR.|  
|[Getdefaultdomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Získá ukazatele rozhraní typu <xref:System._AppDomain> představující výchozí doménu pro aktuální proces.|  
|[Locksheldbylogicalthread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Nepoužívejte.|  
|[MapFile – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mapuje zadaný soubor do paměti. Tato metoda je zastaralá.|  
|[Nextdomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Získá ukazatele rozhraní do další domény ve výčtu.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Spuštění modulu CLR.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Zastaví spuštění kódu v modulu runtime pro aktuální proces.|  
|[Switchinlogicalthreadstate – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Nepoužívejte.|  
|[Switchoutlogicalthreadstate – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Nepoužívejte.|  
|[Unloaddomain – metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Uvolní doménu zadané aplikace z aktuální proces.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Viz také  
 <xref:System.AppDomain>  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [Iclrruntimehost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [Modulu runtime](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Corruntimehost – třída typu Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)