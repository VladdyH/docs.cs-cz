---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 68de80e4a01de27c16c0ed85c4177c562d5e328b
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204713"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>, včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.GridItemPattern> – Vzor ovládacích prvků slouží k podpoře jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider>. Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, mějte na paměti následující pokyny a konvence:  
  
-   Souřadnice mřížky jsou počítány od nuly s levá horní buňka s souřadnice (0, 0).  
  
-   Sloučené buňky budou hlásit jejich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> a <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastnosti na základě jejich základní ukotvení buňky definované ve zprostředkovateli automatizace uživatelského rozhraní. Obvykle bude nejvyšší a levém řádku nebo sloupce.  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> neposkytuje aktivní manipulaci s například slučování nebo rozdělení buňky v mřížce.  
  
-   Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IGridItemProvider> lze obvykle Procházet (automatizace uživatelského rozhraní klienta můžete přesunout na sousední ovládací prvky) pomocí klávesnice.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Požadované členy pro IGridItemProvider  
 Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Vlastnost|Žádné|  
  
 Tento model ovládací prvek nemá žádné přidružené metody a události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Tento model ovládací prvek nemá žádné související výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
