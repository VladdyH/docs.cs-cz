---
title: "Zobrazení dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 839a4fd8052578e32e4d46d10e07aa52a1f23d90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a>Zobrazení dat v ovládacím prvku Windows Forms DataGridView
`DataGridView` Řízení se používá k zobrazení dat z různých zdrojů externí data. Alternativně můžete přidávání řádků a sloupců do ovládacího prvku a ručně přidejte do ní data.  
  
 Při vytvoření vazby ovládacího prvku ke zdroji dat, můžete vygenerovat automaticky na základě schématu zdroje dat sloupců. Pokud tyto sloupce nezobrazí stejně, jako je chcete, můžete skrýt, odebrat nebo změna uspořádání je. Můžete také přidat nevázaných sloupců zobrazíte dodatečná data, která nepochází z datového zdroje.  
  
 Kromě toho můžete zobrazit svá data pomocí standardní formáty (například formátu měny), nebo můžete přizpůsobit zobrazení formátování k prezentaci dat, ale budete muset (jako je například změna barvy pozadí pro záporná čísla nebo výměna řetězcové hodnoty pomocí odpovídající bitových kopií).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 Popisuje možnosti pro sestavování ovládacího prvku s daty.  
  
 [Formátování dat v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 Popisuje možnosti formátování hodnot v buňkách zobrazení.  
  
 [Návod: Vytvoření ovládacího prvku nevázaný Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 Popisuje, jak ručně naplnit ovládací prvek s daty.  
  
 [Postupy: vytvoření vazby dat do ovládacího prvku Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 Popisuje, jak k naplnění ovládacího prvku s daty pomocí vytvoření vazby, aby `BindingSource` obsahující informací načtených z databáze.  
  
 [Postupy: automatické generování sloupců v vázané na Data Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 Popisuje, jak lze automaticky generovat sloupce podle vázaný datový zdroj.  
  
 [Postupy: odebrání automaticky vygenerovaných sloupců z Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 Popisuje, jak můžete skrýt nebo odstranit sloupce, které automaticky generují z vázaný datový zdroj.  
  
 [Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak ke změně uspořádání sloupců generovaných automaticky z vázaný datový zdroj.  
  
 [Postupy: Přidání nepřipojeného sloupce do vázané na Data Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/unbound-column-to-a-data-bound-datagridview.md)  
 Popisuje postup doplňují data z vázaný datový zdroj zobrazením Další, nevázaných sloupců.  
  
 [Postupy: připojení objektů k ovládacích prvků Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 Popisuje, jak vytvořit vazbu ovládacího prvku do skupiny libovolný objekty tak, aby každý objekt je zobrazen na samostatném řádku.  
  
 [Postupy: přístup k objektům připojeným do Windows Forms DataGridView řádků](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 Popisuje, jak načíst objekt vázaný na konkrétní řádek ovládacího prvku.  
  
 [Návod: Vytvoření hlavního a podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 Popisuje, jak zobrazit data ze dvou tabulek souvisejících databáze tak, aby hodnoty zobrazené v jednom `DataGridView` řízení závisí na aktuálně vybraný řádek v jiném ovládacím prvku.  
  
 [Postupy: přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 Popisuje způsob zpracování <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> událostí Změna vzhledu buněk v závislosti na jejich hodnot.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> součásti.  
  
## <a name="related-sections"></a>Související oddíly  
 [Vkládání dat v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak změnit způsob uživatele, přidání a změna dat v ovládacím prvku.  
  
## <a name="see-also"></a>Viz také  
 [DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)