---
title: ICorDebugVariableHome rozhraní
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae11cdbbdb0fa63d1b903d18aff133344fd17f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422530"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome rozhraní
Představuje místní proměnné nebo argument funkce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetArgumentIndex – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|Získá index argument funkce.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|Získá instanci "ICorDebugCode", která obsahuje toto `ICorDebugVariableHome` objektu.|  
|[GetLiveRange – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|Získá nativní rozsahu, za které je tato proměnná za provozu.|  
|[GetLocationType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|Získá typ proměnné nativní umístění.|  
|[GetOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|Získá posun od základní registrace proměnné.|  
|[GetRegister – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|Získá registrace, který obsahuje proměnnou s typem umístění `VLT_REGISTER`a základní registrace pro proměnné s typem umístění `VLT_REGISTER_RELATIVE`.|  
|[GetSlotIndex – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|Získá spravovaného indexu slotu místní proměnné.|  
  
## <a name="example"></a>Příklad  
 Používá následující fragment kódu [ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md) objekt s názvem `pCode4`.  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugVariableHomeEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
