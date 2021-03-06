---
title: 'Omezení rizik: Ověřování schématu XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e757962f02cce104d8c5ab805d0481861cab426e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389210"
---
# <a name="mitigation-xml-schema-validation"></a>Omezení rizik: Ověřování schématu XML
V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], ověření schématu XSD zjistí porušení jedinečné omezení, pokud je použit složený klíč a jeden klíč je prázdný.  
  
## <a name="impact"></a>Dopad  
 Dopad tato změna by měl být minimální: na základě schématu specifikace, chybu ověření schématu se očekává, pokud `xsd:unique` porušení pomocí složeného klíče s prázdným klíčem.  
  
## <a name="mitigation"></a>Zmírnění  
 Jestli se zjistí chybu ověření schématu, pokud má složený klíč jeden prázdný klíč je konfigurovat funkce:  
  
-   Od verze aplikace cílených [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], ve výchozím nastavení je povoleno vyhledávání chybu ověření schématu; ale je možné, pro vyjádření výslovného nesouhlasu, takže nebudou zjištěna chyba ověření schématu.  
  
-   V aplikacích, které běží pod [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] cíle, ale [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a starší verze, ve výchozím nastavení není zjištěna chyba ověření schématu; ale je možné, který se přidá do, tak, že bude zjištěna chyba ověření schématu.  
  
 Toto chování se dá nakonfigurovat pomocí <xref:System.AppContext> třídy definují hodnotu `System.Xml.IgnoreEmptyKeySequences` přepínače. Protože přepínač na výchozí hodnota je `false` (prázdný posloupnosti kláves nejsou ignorovat), aplikace, které cílí [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] můžete vyjádření výslovného nesouhlasu chování pomocí následující kód k nastavení hodnoty na přepínač na `true`:  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 Pro aplikace, které cílí [!INCLUDE[net_v452](../../../includes/net-v452-md.md)] a starší verze, protože na přepínač Výchozí hodnota je `true` (prázdný posloupnosti kláves ignorují), je možné zajistit, že složené klíče s prázdným klíčem generovat chybu ověření schématu pomocí Následující kód k nastavení hodnoty na přepínač na `false`.  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
