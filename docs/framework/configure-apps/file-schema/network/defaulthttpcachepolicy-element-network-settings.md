---
title: "&lt;defaulthttpcachepolicy –&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy
helpviewer_keywords:
- defaultHttpCachePolicy element
- <defaultHttpCachePolicy> element
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: "19"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f2db2fd10ca20209c21c8add71d8ee4f26951ca6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltdefaulthttpcachepolicygt-element-network-settings"></a>&lt;defaulthttpcachepolicy –&gt; – Element (nastavení sítě)
Popisuje, jestli ukládání do mezipaměti HTTP je aktivní a popisuje výchozí zásady ukládání do mezipaměti.  
  
 \<Konfigurace >  
\<System.NET >  
\<requestCaching – >  
\<defaulthttpcachepolicy – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss|minValue|maxValue"  
  maximumAge="d.hh:mm:ss|minValue|maxValue"  
  maximumStale="d.hh:mm:ss|minValue|maxValue"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`maximumAge`|Určuje maximální časový interval před objektu v mezipaměti je označena jako neplatná.|  
|`maximumStale`|Určuje maximální dobu, po čase počítaný aktuálnosti před objektu v mezipaměti je označena jako neplatná.|  
|`minimumFresh`|Určuje minimální dobu do považovat za nový objekt v mezipaměti.|  
|`policyLevel`|Určuje, zda je automatické zásady ukládání do mezipaměti, nebo jestli přeskočí mezipaměti. Výchozí hodnota je `BypassCache`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[requestCaching –](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|Ovládací prvky ukládání do mezipaměti mechanismus pro síťové požadavky.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `policyLevel` atribut je buď `BypassCache` nebo `Default`.  
  
 Hodnoty `maximumAge`, `maximumStale`, a `minimumFresh` prvky jsou buď explicitní časový interval, ve formátu *d*. *hh*:*mm*:*ss* (dny, hodiny, minuty a sekundy), nebo konstanty `minValue` nebo `maxValue`podle potřeby.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak chcete zadat minimální čerstvé čas šest hodin, maximální stáří čas dva dny a maximální zastaralé doba čtyři hodiny.  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy  
        minimumFresh="0.06:00:00"  
        maximumAge="2.00:00:00"  
        maximumStale="0.04:00:00"
      />  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)