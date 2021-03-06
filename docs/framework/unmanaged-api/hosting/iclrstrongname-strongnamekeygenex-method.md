---
title: ICLRStrongName::StrongNameKeyGenEx – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93377f82992b8d7d55b21b53abfd7d7c2e9e620b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003656"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a>ICLRStrongName::StrongNameKeyGenEx – metoda
Generuje nový pár veřejného a privátního klíče se zadanou velikost klíče pro použití silným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [in] Název požadovaný kontejner klíče. `wszKeyContainer` musí být neprázdný řetězec nebo hodnota null pro generování dočasný název.  
  
 `dwFlags`  
 [in] Hodnota, která určuje, zda má zůstat zkratku zaregistrovanou. Podporovány jsou následující hodnoty:  
  
-   0x00000000 - nepoužívá, pokud `wszKeyContainer` má hodnotu null. k vygenerování názvu dočasného kontejneru klíčů.  
  
-   0x00000001 (`SN_LEAVE_KEY`)-určuje, že klíč by měl být vlevo zaregistrován.  
  
 `dwKeySize`  
 [in] Požadovaná velikost klíče v bitech.  
  
 `ppbKeyBlob`  
 [out] Vrácený pár veřejného a privátního klíče.  
  
 `pcbKeyBlob`  
 [out] Velikost v bajtech, z `ppbKeyBlob`.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).  
  
## <a name="remarks"></a>Poznámky  
 Vyžadují rozhraní .NET Framework verze 1.0 a 1.1 `dwKeySize` z 1 024 bity k podepisování sestavení silným názvem; přidá verze 2.0 podporuje pro klíče 2048 bitů.  
  
 Po načtení klíče, měli byste zavolat [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metodu pro uvolnění přidělené paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameKeyGen – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
