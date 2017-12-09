---
title: "IMetaDataDispenserEx::SetOption – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.SetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::SetOption
helpviewer_keywords:
- IMetaDataDispenserEx::SetOption method [.NET Framework metadata]
- SetOption method [.NET Framework metadata]
ms.assetid: 9f1c7ccd-7fb2-41d8-aa00-24b823376527
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a58ac4379522c13125f98df058cd67bceb7cdbd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexsetoption-method"></a>IMetaDataDispenserEx::SetOption – metoda
Nastaví Zadaná možnost zadanou hodnotu pro aktuální obor metadat. Možnost určuje způsob zpracování volání do aktuálního oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetOption (  
    [in] REFGUID optionId,   
    [in] const VARIANT *pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `optionId`  
 [v] Ukazatel na identifikátor GUID, který určuje možnost nastavení.  
  
 `pValue`  
 [v] Hodnota, která chcete použít k nastavení možnosti. Typ této hodnoty musí být typu variant Zadaná možnost typu.  
  
## <a name="remarks"></a>Poznámky  
 V následující tabulce jsou uvedeny dostupné identifikátory GUID, `optionId` parametru může ukazovat na a odpovídající platné hodnoty pro `pValue` parametr.  
  
|GUID|Popis|`pValue`Parametr|  
|----------|-----------------|------------------------|  
|MetaDataCheckDuplicatesFor|Ovládací prvky položek, které se kontroluje duplicity. Pokaždé, když zavoláte [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) metoda, která vytvoří novou položku, můžete požádat metodu zkontrolujte, zda položka již existuje v aktuálním oboru. Například můžete zkontrolovat existenci `mdMethodDef` položky; v takovém případě při volání [imetadataemit::definemethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md), zkontroluje, že metoda již neexistuje v aktuálním oboru. Tato kontrola používá klíč, který jedinečně identifikuje dané metody: nadřazený typ, název a podpis.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [CorCheckDuplicatesFor](../../../../docs/framework/unmanaged-api/metadata/corcheckduplicatesfor-enumeration.md) výčtu.|  
|MetaDataRefToDefCheck|Ovládací prvky, které odkazuje položky se převedou na definice. Ve výchozím nastavení bude modul metadata optimalizovat kód převádění odkazovaná položka k jeho definici, pokud odkazovaná položka je ve skutečnosti definovaná v aktuálním oboru.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [CorRefToDefCheck](../../../../docs/framework/unmanaged-api/metadata/correftodefcheck-enumeration.md) výčtu.|  
|MetaDataNotificationForTokenMovement|Ovládací prvky, které token znovu mapuje, ke kterým došlo během metadat sloučení generovat zpětných volání. Použití [imetadataemit::sethandler –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) metodu pro vytvoření vaší [imaptoken –](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) rozhraní.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [CorNotificationForTokenMovement](../../../../docs/framework/unmanaged-api/metadata/cornotificationfortokenmovement-enumeration.md) výčtu.|  
|MetaDataSetENC|Řídí chování upravit a pokračovat (ŠIF). Současně lze nastavit pouze jeden režim chování.|Musí mít hodnotu typu variant typu UI4 a musí obsahovat hodnotu [CorSetENC](../../../../docs/framework/unmanaged-api/metadata/corsetenc-enumeration.md) výčtu. Hodnota není bitová maska.|  
|MetaDataErrorIfEmitOutOfOrder|Ovládací prvky, které chyby vygenerované out pořadí generovat zpětných volání. Generování metadat mimo pořadí není závažná; Pokud jste emitování metadata v pořadí, které se podporuje modul metadata, metadata jsou však kompaktnější a proto lze efektivněji vyhledat. Použití `IMetaDataEmit::SetHandler` metodu pro vytvoření vaší [imetadataerror –](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md) rozhraní.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [CorErrorIfEmitOutOfOrder](../../../../docs/framework/unmanaged-api/metadata/corerrorifemitoutoforder-enumeration.md) výčtu.|  
|MetaDataImportOption|Určuje, jaké druhy položky, které byly odstraněny během ŠIF jsou načítána enumerátor.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [CorImportOptions – výčet](../../../../docs/framework/unmanaged-api/metadata/corimportoptions-enumeration.md) výčtu.|  
|MetaDataThreadSafetyOptions|Určuje, zda modul metadata získává čtečky nebo zapisovač zámků, tím se zajišťuje zabezpečení vlákna. Ve výchozím nastavení modul předpokládá, že přístup se jednovláknové volající, proto jsou získány žádné zámky. Klienti jsou odpovědné za údržbu synchronizace správné vláken při použití metadat rozhraní API.|Musí mít hodnotu typu variant typu UI4 a musí obsahovat hodnotu [CorThreadSafetyOptions](../../../../docs/framework/unmanaged-api/metadata/corthreadsafetyoptions-enumeration.md) výčtu. Hodnota není bitová maska.|  
|MetaDataGenerateTCEAdapters|Určuje, zda knihovna typů – Importér by měl generovat adaptéry úzce párované událostí (TCE) pro kontejnerů COM připojovací bod.|Musí být typu variant typu BOOL. Pokud `pValue` je nastaven na `true`, knihovna typů – Importér generuje TCE adaptéry.|  
|MetaDataTypeLibImportNamespace|Určuje jiné než výchozí obor názvů pro knihovny typů, která se importují.|Musí být buď hodnotu null, nebo hodnotu typu variant typu BSTR. Pokud `pValue` je hodnota null, nastaví aktuální obor názvů na řetězec, který se nachází v typu variant na BSTR, aktuální obor názvů je nastaven na hodnotu null; jinak hodnota.|  
|MetaDataLinkerOptions|Určuje, zda by měl linkeru generovat sestavení nebo soubor modulu rozhraní .NET Framework.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot [CorLinkerOptions](../../../../docs/framework/unmanaged-api/metadata/corlinkeroptions-enumeration.md) výčtu.|  
|MetaDataRuntimeVersion|Určuje verzi modulu CLR, proti kterému bylo vytvořeno tuto bitovou kopii. Verze je uložený jako řetězec, jako je například "v1.0.3705".|Musí být hodnota null, VT_EMPTY hodnotu nebo hodnotu typu variant typu BSTR. Pokud `pValue` je null, verze modulu runtime je nastavená na hodnotu null. Pokud `pValue` je VT_EMPTY, verze je nastaveno na výchozí hodnotu, která pochází z verzi Mscorwks.dll, ve kterém je spuštěn kód metadat. Verze runtime, jinak hodnota nastavena na řetězec, který se nachází v typ BSTR variant.|  
|MetaDataMergerOptions|Určuje možnosti pro slučování metadat.|Musí být typu variant typu UI4 a musí obsahovat kombinaci hodnot `MergeFlags` výčtu, který je popsaný v souboru CorHdr.h.|  
|MetaDataPreserveLocalRefs|Zakáže optimalizace místní odkazy do definice.|Musí obsahovat kombinaci hodnot [CorLocalRefPreservation](../../../../docs/framework/unmanaged-api/metadata/corlocalrefpreservation-enumeration.md) výčtu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadatadispenserex – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [Imetadatadispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)