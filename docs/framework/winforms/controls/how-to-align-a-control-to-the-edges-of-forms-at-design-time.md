---
title: "Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 86134902a6645d2c9bf7bcef2cf93bf543d8c9bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a>Postupy: Zarovnání ovládacího prvku k okrajům formuláře během návrhu
Můžete provést kontrolu nad zarovnání na hranu svých formulářů podle nastavení <xref:System.Windows.Forms.Control.Dock%2A>. Tato vlastnost určuje, kde vlastní ovládací prvek nachází ve formuláři. <xref:System.Windows.Forms.Control.Dock%2A> Vlastnost lze nastavit následující hodnoty:  
  
|Nastavení|Vliv na vlastní ovládací prvek|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|Překladišť k dolní části formuláře.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Doplní veškerý zbývající prostor ve tvaru.|  
|<xref:System.Windows.Forms.DockStyle.Left>|Přepraviště na levé straně formuláře.|  
|<xref:System.Windows.Forms.DockStyle.None>|Nepodporuje není ukotvení odkudkoli a zobrazí se v umístění určeném pomocí jeho <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle.Right>|Přepraviště na pravé straně formuláře.|  
|<xref:System.Windows.Forms.DockStyle.Top>|Překladišť k horní části formuláře.|  
  
 Tyto hodnoty lze nastavit i v kódu. Další informace najdete v tématu [postupy: zarovnání ovládacího prvku k okrajům formuláře](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a>Nastavit vlastnost ukotvení pro ovládací prvek v době návrhu  
  
1.  V Návrháři formulářů Windows vyberte vlastní ovládací prvek.  
  
2.  V **vlastnosti** klikněte na rozevírací seznam pole vedle <xref:System.Windows.Forms.Control.Dock%2A> vlastnost.  
  
     Grafické rozhraní představující šesti možné <xref:System.Windows.Forms.Control.Dock%2A> nastavení se zobrazí.  
  
3.  Vyberte příslušné nastavení.  
  
4.  Vlastní ovládací prvek bude nyní ukotvení způsobem zadané nastavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [Postupy: zarovnání ovládacího prvku k okrajům formulářů](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [Návod: Uspořádání ovládacích prvků ve Windows Forms pomocí zarovnávacích čar](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Postupy: Ukotvování ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Postupy: ukotvení a dokování podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: ukotvení a dokování podřízených ovládacích prvků v ovládacím prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Vývoj Windows Forms – ovládací prvky v době návrhu](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)