---
title: 'Postupy: Vytvoření jednoduchého nebo složitého zobrazení TreeViews'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], creating
- Control class [WPF], TreeView [WPF], creating
ms.assetid: 1defbb78-b8e7-4c0e-b650-576453ac828d
ms.openlocfilehash: 54e9218ea1460a0c29d8b9d7b9c740c18ac7ab24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552995"
---
# <a name="how-to-create-simple-or-complex-treeviews"></a>Postupy: Vytvoření jednoduchého nebo složitého zobrazení TreeViews
Tento příklad ukazuje, jak vytvořit jednoduché nebo komplexní <xref:System.Windows.Controls.TreeView> ovládací prvky.  
  
 A <xref:System.Windows.Controls.TreeView> se skládá z hierarchie <xref:System.Windows.Controls.TreeViewItem> ovládací prvky, které může obsahovat jednoduché textové řetězce a také složitější obsah, jako například <xref:System.Windows.Controls.Button> ovládací prvky nebo <xref:System.Windows.Controls.StackPanel> s vložený obsah. Můžete definovat explicitně <xref:System.Windows.Controls.TreeView> obsah nebo zdroj dat může poskytovat obsah. Toto téma obsahuje příklady tyto koncepty.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> Vlastnost <xref:System.Windows.Controls.TreeViewItem> obsahuje obsah, <xref:System.Windows.Controls.TreeView> zobrazí pro danou položku. A <xref:System.Windows.Controls.TreeViewItem> může mít <xref:System.Windows.Controls.TreeViewItem> ovládací prvky jako jeho podřízených elementů a vy můžete definovat tyto podřízené elementy pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastnost.  
  
 Následující příklad ukazuje, jak definovat explicitně <xref:System.Windows.Controls.TreeViewItem> obsahu nastavením <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> vlastnost textového řetězce.  
  
 [!code-xaml[TreeViewSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#1)]  
  
 Následující příklad ukazuje, jak definovat podřízených elementů <xref:System.Windows.Controls.TreeViewItem> definováním <xref:System.Windows.Controls.ItemsControl.Items%2A> , které jsou <xref:System.Windows.Controls.Button> ovládací prvky.  
  
 [!code-xaml[TreeViewSimple#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#3)]  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> kde <xref:System.Windows.Data.XmlDataProvider> poskytuje <xref:System.Windows.Controls.TreeViewItem> obsah a <xref:System.Windows.HierarchicalDataTemplate> definuje vzhled obsahu.  
  
 [!code-xaml[TreeViewSimple#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#6)]  
  
 [!code-xaml[TreeViewSimple#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#7)]  
  
 [!code-xaml[TreeViewSimple#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#5)]  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.TreeView> kde <xref:System.Windows.Controls.TreeViewItem> obsahuje obsah <xref:System.Windows.Controls.DockPanel> ovládacích prvků, které mají vložený obsah.  
  
 [!code-xaml[TreeViewSimple#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#9)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [TreeView – přehled](../../../../docs/framework/wpf/controls/treeview-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)
