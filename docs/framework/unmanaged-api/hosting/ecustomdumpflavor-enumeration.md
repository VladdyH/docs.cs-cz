---
title: ECustomDumpFlavor – výčet
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6d0ba3f722f63650a3db6a8f633189993db0716
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431405"
---
# <a name="ecustomdumpflavor-enumeration"></a>ECustomDumpFlavor – výčet
Obsahuje hodnoty, které označují, které položky, které chcete zahrnout do podmnožinu haldy vlastní dump při zasílání zpráv o chybách.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|Určuje, že by měl vlastní haldy výpisu spusťte jako minimální výpis a zahrnují doplňující data zadané žádné [customdumpitem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instance předána metodě stejné.|  
|`DUMP_FLAVOR_NonHeapCLRState`|Určuje, že vlastní haldy výpisu byste měli získat všechna data stavu runtime, která nebyla přidělena dynamicky.|  
  
## <a name="remarks"></a>Poznámky  
 Parametr typu `ECustomDumpFlavor` je předán [iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ECustomDumpItemKind – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
