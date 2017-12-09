---
title: "Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f542e0ba3bf35319c270fe9f93d3f355cc45ac95
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>Nástroj pro hledání soukromého klíče (FindPrivateKey.exe)
Tento nástroj příkazového řádku lze získat privátní klíč z úložiště certifikátů. FindPrivateKey.exe můžete například použít k vyhledání umístění a název souboru privátního klíče přidruženého k určité X.509 certifikátu v úložišti certifikátů.  
  
> [!IMPORTANT]
>  Nástroj FindPrivateKey je dodávána jako Ukázka WCF. Další informace o tom, kde najít ukázky a jak vytvořit, najdete v části  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a>Poznámky  
 Následující tabulky popisují argumenty a možnosti, které je možné pomocí nástroje Najít privátního klíče (FindPrivateKey.exe).  
  
|Argument|Popis|  
|--------------|-----------------|  
|`storeName`|Název úložiště certifikátů.|  
|`storeLocation`|Umístění úložiště certifikátů.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/n <`*subjectName*`>`|Určuje název předmětu certifikátu.|  
|`/t <`*kryptografický otisk*`>`|Určuje kryptografický otisk certifikátu. Pomocí Certmgr.exe získat kryptografický otisk certifikátu.|  
|`/f`|Výstupy pouze název souboru.|  
|`/d`|Výstupy pouze adresáři.|  
|`/a`|Výstupy název souboru na absolutní.|  
  
## <a name="examples"></a>Příklady  
 Tento příkaz načte privátní klíč pro John Doe.  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 Tento příkaz načte privátní klíč pro místní počítač.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```