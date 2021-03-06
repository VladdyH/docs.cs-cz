---
title: IHostControl::GetHostManager – metoda
ms.date: 03/30/2017
api_name:
- IHostControl.GetHostManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::GetHostManager
helpviewer_keywords:
- GetHostManager method [.NET Framework hosting]
- IHostControl::GetHostManager method [.NET Framework hosting]
ms.assetid: 0fa34bca-ed18-4626-9e78-d33684d18edb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 355d2e259adb13da44b09e19872337c17ac20ade
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439319"
---
# <a name="ihostcontrolgethostmanager-method"></a>IHostControl::GetHostManager – metoda
Získá ukazatele rozhraní hostitele implementaci rozhraní se zadaným `IID`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHostManager (  
    [in] REFIID riid,  
    [out, iid_is(riid)] void** ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [v] `IID` Rozhraní, které je dotazování common language runtime (CLR).  
  
 `ppObject`  
 [out] Ukazatel rozhraní implementované hostitele nebo hodnota null, pokud hostitel nepodporuje toto rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetHostManager` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|Požadovanou `IID` není platný.|  
|E_NOINTERFACE|Nepodporuje požadované rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR dotazuje na hostiteli a zjistit, jestli podporuje jeden nebo více z následujících rozhraní:  
  
-   [Ihostmemorymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
  
-   [Ihosttaskmanager –](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
  
-   [Ihostthreadpoolmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
  
-   [Ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
  
-   [Ihostsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
  
-   [Ihostassemblymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
  
-   [Ihostgcmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
  
-   [Ihostpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
  
-   [Ihostsecuritymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
  
 Pokud hostitel podporuje rozhraní zadané, nastaví `ppObject` její implementace tohoto rozhraní. Jinak, nastaví `ppObject` na hodnotu null.  
  
 Modul CLR nevyvolá `Release` hostitele manažerů, i když ho vypnout.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
