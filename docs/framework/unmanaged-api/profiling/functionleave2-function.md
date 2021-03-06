---
title: FunctionLeave2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d6486a90d952208af89428423867a3daa4e8618
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453356"
---
# <a name="functionleave2-function"></a>FunctionLeave2 – funkce
Profileru upozorní, že funkce je vrátit volajícímu a poskytuje informace o zásobník rámec a funkce návratovou hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [v] Identifikátor funkce, která vrací.  
  
 `clientData`  
 [v] Identifikátor změnu mapování funkce, které profileru dříve zadán prostřednictvím [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce.  
  
 `func`  
 [v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.  
  
 To profileru by měly zpracovávat jako neprůhledného popisovače, který může být předán zpět do modulu provádění v [ICorProfilerInfo2::getfunctioninfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metoda.  
  
 `retvalRange`  
 [v] Ukazatel [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktura, která určuje umístění paměti funkce návratovou hodnotu.  
  
 Chcete-li získat přístup k informacím návratovou hodnotu `COR_PRF_ENABLE_FUNCTION_RETVAL` musí být nastaven příznak. Můžete použít profileru [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metodu a nastavit příznaky událostí.  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty `func` a `retvalRange` parametry nejsou platné po `FunctionLeave2` funkce vrátí hodnotu, protože hodnoty může změnit nebo zničena.  
  
 `FunctionLeave2` Je funkce zpětného volání, je nutné implementovat. Musíte použít implementaci `__declspec`(`naked`) atribut třídy úložiště.  
  
 Spouštěcí modul neukládá žádné registry před voláním této funkce.  
  
-   Na záznam je nutné uložit všechny registrů, které používáte, včetně těch, které v jednotce s plovoucí desetinnou čárkou (FPU).  
  
-   Při ukončení je nutné obnovit zásobníku tím, že odebere vypnout všechny parametry, které byly nabídnutých jeho volající.  
  
 Implementace `FunctionLeave2` by neměly blokovat, protože zpozdí uvolňování paměti. Implementace neměli uvolnění paměti, protože zásobník nemusí být ve stavu paměti procházející kolekci. Pokud dojde k pokusu o uvolnění paměti, až bude blokovat modulu runtime `FunctionLeave2` vrátí.  
  
 Navíc `FunctionLeave2` funkce nesmějí provádět volání do spravovaného kódu nebo v jakékoli příčina způsob přidělení spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [FunctionEnter2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionTailcall2 – funkce](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
