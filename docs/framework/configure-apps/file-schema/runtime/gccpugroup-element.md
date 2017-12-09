---
title: "&lt;Gccpugroup –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abcb6d1b5f9dbb7a866b55628aabfe996a0a747c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltgccpugroupgt-element"></a>&lt;Gccpugroup –&gt; – Element
Určuje, jestli uvolňování paměti podporuje více skupin procesoru.  
  
 \<Konfigurace >  
\<modul runtime >  
\<Gccpugroup – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<GCCpuGroup    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`enabled`|Požadovaný atribut.<br /><br /> Určuje, jestli uvolňování paměti podporuje více skupin procesoru.|  
  
## <a name="enabled-attribute"></a>Atribut enabled  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|`false`|Uvolňování paměti nepodporuje více skupin procesoru. Toto nastavení je výchozí.|  
|`true`|Uvolňování paměti podporuje více skupin procesoru, pokud je povolená kolekce paměti na serveru.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
|`runtime`|Obsahuje informace o vazbách sestavení a uvolnění paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud počítač obsahuje více skupin procesoru, kolekce paměti na serveru je povoleno (najdete v článku [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti ve všech skupinách procesoru a trvá všechny jader do účet při vytváření a vyrovnávání haldách.  
  
> [!NOTE]
>  Tento prvek se vztahuje pouze na kolekce vláken uvolňování paměti. Pokud chcete povolit distribuci vlákna uživatelského ve všech skupinách procesoru modulu runtime, musíte zároveň povolit [< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesoru.  
  
```xml  
<configuration>  
   <runtime>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Postupy: zakázat souběžná kolekce paměti](http://msdn.microsoft.com/en-us/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [Uvolňování paměti serveru a pracovní stanice](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)