---
title: "IMetaDataAssemblyImport::GetExportedTypeProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetExportedTypeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e142d0c77493ac1e9ab2bf485d8e111af4fb3ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a>IMetaDataAssemblyImport::GetExportedTypeProps – metoda
Získá sadu vlastností typu exportovaný podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,   
    [out] LPWSTR            szName,   
    [in]  ULONG             cchName,   
    [out] ULONG             *pchName,   
    [out] mdToken           *ptkImplementation,   
    [out] mdTypeDef         *ptkTypeDef,   
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdct`  
 [v] `mdExportedType` Metadata token, který představuje typ exportovaný.  
  
 `szName`  
 [out] Název typu exportovaný.  
  
 `cchName`  
 [v] Velikost v široké znaky z `szName`.  
  
 `pchName`  
 [out] Počet aktuálně vrácenou široké znaky`szName`  
  
 `ptkImplementation`  
 [out] `mdFile`, `mdAssemblyRef`, Nebo `mdExportedType` metadata token, který obsahuje nebo povoluje přístup k vlastnosti exportovaný typu.  
  
 `ptkTypeDef`  
 [out] Ukazatel na `mdTypeDef` token, který představuje typ v souboru.  
  
 `pdwExportedTypeFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použít u exportovaných typu. Příznaky hodnota může být jeden nebo více [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Imetadataassemblyimport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)