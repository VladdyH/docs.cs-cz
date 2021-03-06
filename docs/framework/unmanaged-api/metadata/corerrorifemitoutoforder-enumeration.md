---
title: CorErrorIfEmitOutOfOrder – výčet
ms.date: 03/30/2017
api_name:
- CorErrorIfEmitOutOfOrder
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorErrorIfEmitOutOfOrder
helpviewer_keywords:
- CorErrorIfEmitOutOfOrder enumeration [.NET Framework metadata]
ms.assetid: 6d758aad-29a7-44fe-9481-bbff5b799a32
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4e9d03dcf4603f9470f8f2509050eb6f875746a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442637"
---
# <a name="corerrorifemitoutoforder-enumeration"></a>CorErrorIfEmitOutOfOrder – výčet
Obsahuje příznak hodnoty, které označují podmínky, za kterých by měl být vygenerován chybovou zprávu, když metadata jsou vydávány mimo pořadí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorErrorIfEmitOutOfOrder {  
  
    MDErrorOutOfOrderDefault    = 0x00000000,  
    MDErrorOutOfOrderNone       = 0x00000000,  
    MDErrorOutOfOrderAll        = 0xffffffff,  
    MDMethodOutOfOrder          = 0x00000001,  
    MDFieldOutOfOrder           = 0x00000002,  
    MDParamOutOfOrder           = 0x00000004,  
    MDPropertyOutOfOrder        = 0x00000008,  
    MDEventOutOfOrder           = 0x00000010  
  
} CorErrorIfEmitOutOfOrder;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDErrorOutOfOrderDefault`|Určuje výchozí chování, který negeneruje chybové zprávy.|  
|`MDErrorOutOfOrderNone`|Označuje, že kompilátor by neměla generovat chybové zprávy.|  
|`MDErrorOutOfOrderAll`|Označuje, že kompilátor by měl generovat chybovou zprávu, pokud pole, vlastnost, události, metoda nebo parametr je vygenerované mimo pořadí.|  
|`MDMethodOutOfOrder`|Označuje, že kompilátor by měl generovat chybovou zprávu, když metoda je vygenerované mimo pořadí.|  
|`MDFieldOutOfOrder`|Označuje, že kompilátor by měl generovat chybovou zprávu, pokud je pole vygenerované mimo pořadí.|  
|`MDParamOutOfOrder`|Označuje, že kompilátor by měl generovat chybovou zprávu, pokud je parametr vygenerované mimo pořadí.|  
|`MDPropertyOutOfOrder`|Označuje, že kompilátor by měl generovat chybovou zprávu, pokud je vlastnost vygenerované mimo pořadí.|  
|`MDEventOutOfOrder`|Označuje, že kompilátor by měl generovat chybovou zprávu, když je vygenerované událost mimo pořadí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
