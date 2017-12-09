---
title: "Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView"
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
helpviewer_keywords:
- DataGridView control [Windows Forms], removing columns
- columns [Windows Forms], removing
ms.assetid: 92e28d98-95a3-446c-9150-41b7c7e5be15
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 04375c89e80acb079f4862c159583adb4b0e4ca1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-autogenerated-columns-from-a-windows-forms-datagridview-control"></a>Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView
Pokud vaše <xref:System.Windows.Forms.DataGridView> řízení nastavena na Generovat její sloupce na základě dat ze svého zdroj dat, je možné selektivně vynechat některé sloupce. To provedete pomocí volání <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> metodu <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce. Alternativně můžete skrýt sloupce v zobrazení nastavením <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> vlastnost `false`. Tento postup je užitečné, když chcete zobrazit skrytých sloupců v určité podmínky, nebo když potřebujete přístup k datům ve sloupcích bez zobrazení ho.  
  
### <a name="to-remove-autogenerated-columns"></a>K odebrání automaticky vygenerovaných sloupců  
  
-   Volání <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A> metodu <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#111)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#111)]  
  
### <a name="to-hide-autogenerated-columns"></a>Chcete-li skrýt automaticky vygenerovaných sloupců  
  
-   Nastavit sloupce <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> vlastnost `false`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#112)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#112](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#112)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#110)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#110)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` vázána na tabulku, která obsahuje `Fax` a `CustomerID` sloupců, jako `Customers` tabulky v ukázkové databázi Northwind.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumnCollection.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)