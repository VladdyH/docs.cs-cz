---
title: 'Přetažení funkce ve Windows Forms '
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
ms.openlocfilehash: b1189da9fa0b76ede3261cf6da5305a09147bba5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865082"
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a>Přetažení funkce ve Windows Forms 
Windows Forms obsahuje sadu metod, událostí a třídy, které implementují chování a přetažení. Toto téma poskytuje přehled podpory a přetažení ve Windows Forms.  Viz také [operace a přetažení a podpora schránky](https://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\)).  
  
## <a name="performing-drag-and-drop-operations"></a>Provádění operací přetažení myší  
 Chcete-li provést operaci přetažení myší, použijte <xref:System.Windows.Forms.Control.DoDragDrop%2A> metodu <xref:System.Windows.Forms.Control> třídy. Další informace o tom, jak se provádí operace přetažení myší, naleznete v tématu <xref:System.Windows.Forms.Control.DoDragDrop%2A>. Chcete-li získat obdélník, který musí být přetaženy ukazatel myši nad před zahájení operace přetažení myší, použijte <xref:System.Windows.Forms.SystemInformation.DragSize%2A> vlastnost <xref:System.Windows.Forms.SystemInformation> třídy.  
  
## <a name="events-related-to-drag-and-drop-operations"></a>Události týkající se operací přetažení myší  
 Existují dvě kategorie událostí v operaci přetažení: události, ke kterým dochází na aktuální cíl operace přetažení myší a události, ke kterým dochází na zdrojovém operaci přetažení.  
  
### <a name="events-on-the-current-target"></a>Události na aktuálním cíli  
 Následující tabulka uvádí události, ke kterým dochází na aktuální cíl operace přetažení myší.  
  
|Události myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|Tato událost se vyvolá při přetažení objektu do hranic ovládacího prvku. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragOver>|Při přetažení objektu v rámci hranice ovládacího prvku při umístění ukazatele myši, dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragDrop>|Po dokončení operace přetažení myší, dojde k této události. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.DragEventArgs>.|  
|<xref:System.Windows.Forms.Control.DragLeave>|Tato událost nastane, pokud objekt ocitne mimo hranice ovládacího prvku. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.EventArgs>.|  
  
 <xref:System.Windows.Forms.DragEventArgs> Třída poskytuje umístění ukazatele myši, aktuální stav tlačítka myši a klávesnice, data jsou kvůli usnadnění použití vypsány, modifikační klávesy a <xref:System.Windows.Forms.DragDropEffects> hodnoty, které určují operace, povolený zdroj události přetažení a cíl přetažení účinek pro operaci.  
  
### <a name="events-on-the-source"></a>Události ve zdroji  
 Následující tabulka uvádí události, ke kterým dochází na zdrojovém operace přetažení myší.  
  
|Události myši|Popis|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|Tato událost se vyvolá během operace přetažení. Poskytuje možnost poskytují vizuální upozornění pro uživatele, který vyskytující se operace přetažení myší, jako je například změna umístění ukazatele myši. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.GiveFeedbackEventArgs>.|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|Tato událost se vyvolá během operace přetažení myší a umožňuje zdroji přetažení určit, zda by měla být operace přetažení myší zrušena. Obslužné rutiny pro tuto událost přijme argument typu <xref:System.Windows.Forms.QueryContinueDragEventArgs>.|  
  
 <xref:System.Windows.Forms.QueryContinueDragEventArgs> Třída poskytuje aktuální stav myši tlačítka a modifikační klávesy na klávesnici, hodnotu určující, zda byla stisknuta klávesa ESC a <xref:System.Windows.Forms.DragAction> hodnotu, která lze použít k určení, zda by měla pokračovat v operaci přetažení myší.  
  
## <a name="see-also"></a>Viz také  
 [Vstup z myši v aplikaci Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
