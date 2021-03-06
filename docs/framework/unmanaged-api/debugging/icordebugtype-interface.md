---
title: ICorDebugType Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de2871b406bb9da84d20d7c526ad4a703baae409
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422854"
---
# <a name="icordebugtype-interface1"></a>ICorDebugType Interface1
Představuje typ, základní nebo komplexní (která je, uživatelem definované). Pokud je typ Obecné, `ICorDebugType` představuje instanci obecného typu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateTypeParameters – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|Získá ukazatele rozhraní k ICorDebugTypeEnum, který odkazuje na Obecné <xref:System.Type> parametry třídy odkazuje toto `ICorDebugType`.|  
|[GetBase – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|Získá ukazatele rozhraní k `ICorDebugType` který odkazuje na základní třídy třídy odkazuje toto `ICorDebugType`, pokud existuje.|  
|[GetClass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|Získá ukazatele rozhraní k ICorDebugClass odkazující typové konstruktoru tohoto `ICorDebugType`.|  
|[GetFirstTypeParameter – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|Získá ukazatele rozhraní k `ICorDebugType` který odkazuje na první obecná <xref:System.Type> parametr pro konstruktor třídy odkazuje toto `ICorDebugType`.|  
|[GetRank – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|Získá počet dimenzí v typu pole.|  
|[GetStaticFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|Získá ukazatele rozhraní k ICorDebugValue, který obsahuje hodnotu statického pole odkazovaná v zadaném poli token v rámci zadaného zásobníku.|  
|[GetType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|Získá hodnotu CorElementType, která popisuje typ nativní modul common language runtime <xref:System.Type> odkazuje toto `ICorDebugType`.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je typ Obecné, `ICorDebugClass` představuje typ bez instancí. `ICorDebugType` Rozhraní představuje instanci obecného typu. Například zatřiďovací tabulky\<tisíc, V > by být reprezentovaná `ICorDebugClass`, zatímco zatřiďovací tabulky\<Int32, řetězec > by být reprezentovaná `ICorDebugType`.  
  
 Jak jsou reprezentována non obecné typy `ICorDebugClass` a `ICorDebugType`. Rozhraní pozdější byla zavedena v rozhraní .NET Framework verze 2.0, jak nakládat s vytvoření instance typu.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
