---
title: Funkce QualifierSet_EndEnumeration (referenční dokumentace nespravovaného rozhraní API)
description: Funkce QualifierSet_EndEnumeration skončí výčet.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbf47dbfddac7d48b78c9d52969de1ef03385c15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524311"
---
# <a name="qualifiersetendenumeration-function"></a>QualifierSet_EndEnumeration – funkce
Ukončí výčet začal s voláním [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) funkce.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Tento parametr se nepoužívá.

`ptr`   
[in] Ukazatel [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.

## <a name="return-value"></a>Návratová hodnota

Následující hodnota vrácená touto funkcí je definována v *WbemCli.h* hlavičkový soubor, nebo můžete definovat ji jako konstantu. ve vašem kódu:

|Konstanta  |Hodnota  |Popis  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | Volání funkce byla úspěšná.  |
  
## <a name="remarks"></a>Poznámky

Tato funkce zalamuje volání na [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) metody.

Toto volání je doporučené, ale nevyžaduje. Okamžitě uvolní prostředky přidružené k výčtu.

## <a name="requirements"></a>Požadavky  

**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
**Záhlaví:** WMINet_Utils.idl  
  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:  
[WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
