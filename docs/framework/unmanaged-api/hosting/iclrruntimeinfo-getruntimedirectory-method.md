---
title: "ICLRRuntimeInfo::GetRuntimeDirectory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetRuntimeDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddaca8232f0b262377c7915852da89cecec09993
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a>ICLRRuntimeInfo::GetRuntimeDirectory – metoda
Získá instalační adresář common language runtime (CLR) spojené s tímto rozhraním.  
  
 Tato metoda nahrazuje [getcorsystemdirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) funkce, které jsou k dispozici v rozhraní .NET Framework verze 2.0, 3.0 a 3.5.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzBuffer`  
 [out] Vrátí instalační adresář modulu CLR. Cesta instalace je plně kvalifikovaný; například "c:\windows\microsoft.net\framework\v1.0.3705\\".  
  
 `pchBuffer`  
 [ve out] Určuje velikost `pwzBuffer` předejdete přetečení vyrovnávací paměti. Pokud `pwzBuffer` má hodnotu null, `pchBuffer` vrátí požadovaná velikost `pwzBuffer`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzBuffer`nebo `pchBuffer` má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrruntimeinfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)