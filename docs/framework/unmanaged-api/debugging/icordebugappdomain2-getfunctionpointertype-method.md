---
title: "ICorDebugAppDomain2::GetFunctionPointerType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetFunctionPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85c07ec6177621b571a376ad58a386e8ed31ea63
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a>ICorDebugAppDomain2::GetFunctionPointerType – metoda
Získá ukazatel na funkci, která má daný podpis.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nTypeArgs`  
 [v] Počet argumentů pro funkci.  
  
 `ppTypeArgs`  
 [v] Pole ukazatele, každý z nich odkazuje na objekt ICorDebugType, který představuje argument typu funkce. První prvek je návratový typ; Každá z dalších prvků je typ parametru.  
  
 `ppType`  
 [out] Ukazatel na adresu `ICorDebugType` objekt, který reprezentuje ukazatele na funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]