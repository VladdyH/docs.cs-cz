---
title: "Postupy: Vrstvení objektů ve formulářích Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bda4cb3641ff890646614af35d38ff13621cc16b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Postupy: Vrstvení objektů ve formulářích Windows
Při vytváření složitých uživatelského rozhraní nebo pracovat s více formuláře rozhraní (MDI) dokumentu, často můžete vrstvy ovládacích prvků a podřízených formulářů, chcete-li vytvořit složitější uživatelská rozhraní (UI). Přesunutí a uchovávání informací o ovládací prvky a systému windows v rámci skupiny, můžete upravit pořadí vykreslování. *Pořadí Z-order* je vizuální rozvržení ovládací prvky ve formuláři podél osy z formuláře (hloubku). V horní části pořadí z-order okno překrývá všechny ostatní systémy windows. Všechny ostatní systémy windows překrývat okna v dolní části pořadí.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-layer-controls-at-design-time"></a>K ovládacím prvkům vrstvy v době návrhu  
  
1.  Vyberte ovládací prvek, který chcete vrstvy.  
  
2.  Na **formátu** nabídky, přejděte na příkaz **pořadí**a potom klikněte na **přenést dopředu** nebo **odeslat zpět**.  
  
### <a name="to-layer-controls-programmatically"></a>Chcete-li vrstvy ovládacích prvků prostřednictvím kódu programu  
  
-   Použití <xref:System.Windows.Forms.Control.BringToFront%2A> a <xref:System.Windows.Forms.Control.SendToBack%2A> metody pro manipulaci s pořadí vykreslování ovládacích prvků.  
  
     Například pokud <xref:System.Windows.Forms.TextBox> řízení, `txtFirstName`, je pod jinou řízení a chcete mít v horní části, použijte následující kód:  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows Forms podporuje *kontejnerů ovládacích prvků*. Uzavření ovládacího prvku zahrnuje umístění řadu ovládacích prvků v rámci nadřazeného ovládacího prvku, například počtu <xref:System.Windows.Forms.RadioButton> ovládací prvky v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku. Potom můžete vrstvy ovládací prvky v rámci nadřazeného ovládacího prvku. Ovládací prvky taky přesunutím skupinový rámeček přesunete, protože se nacházejí v jeho.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Uspořádání ovládacích prvků ve formulářích Windows](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Popisování jednotlivých Windows Forms – ovládací prvky a zajišťování zástupců pro tyto](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Ovládací prvky používané ve formulářích Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Windows Forms – ovládací prvky podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)