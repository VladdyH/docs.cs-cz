---
title: 'Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: b732aa510be22f3cbdc5197574f1e2a825c35df4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536482"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Postupy: Nastavení ikon pro ovládací prvek Windows Forms TreeView
Windows Forms <xref:System.Windows.Forms.TreeView> ovládací prvek může zobrazit ikonami vedle každého uzlu. Ikony jsou umístěné okamžitou vlevo od textu uzlu. Pokud chcete zobrazit tyto ikony, je nutné přidružit zobrazení stromu s <xref:System.Windows.Forms.ImageList> ovládacího prvku. Další informace o seznamech obrázků najdete v tématu [ImageList – komponenta](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) a [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Chyby v Microsoft .NET Framework verze 1.1 bránil bitové kopie v <xref:System.Windows.Forms.TreeView> uzly, kdy aplikace volá <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Chcete-li vyřešit tuto chybu, volejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> ve vaší `Main` metoda ihned po volání <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Tato chyba je opravena v [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
### <a name="to-display-images-in-a-tree-view"></a>Pro zobrazení obrázků v zobrazení stromu  
  
1.  Nastavte <xref:System.Windows.Forms.TreeView> ovládacího prvku <xref:System.Windows.Forms.TreeView.ImageList%2A> vlastnost, která má existující <xref:System.Windows.Forms.ImageList> řízení, které chcete použít.  
  
     Tyto vlastnosti můžete nastavit v návrháři se okno Vlastnosti, nebo v kódu.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  Nastavte uzel <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> vlastnosti. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Vlastnost určuje obrázku zobrazovaného uzlu běžné a rozšířené stavů a <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> vlastnost určuje obrázku zobrazovaného pro uzlu vybraném stavu.  
  
     Tyto vlastnosti můžete nastavit v kódu nebo editoru TreeNode. Chcete-li otevřít TreeNode Editor, klikněte na tlačítko se třemi tečkami ( ![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) vedle položky <xref:System.Windows.Forms.TreeView.Nodes%2A> vlastnost v okně Vlastnosti.  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [Postupy: Přidání a odebrání uzlů s ovládacím prvkem Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Postupy: Iterace všemi uzly ovládacího prvku Windows Forms TreeView](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [Postupy: Určení uzlu TreeView označeného kliknutím](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [Postupy: Přidání vlastních informací do ovládacího prvku TreeView nebo ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
