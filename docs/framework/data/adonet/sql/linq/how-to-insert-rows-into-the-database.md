---
title: "Postupy: vložení řádků do databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a96a0ab800076db16022f5b02c84d7a53ca99147
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-insert-rows-into-the-database"></a>Postupy: vložení řádků do databáze
Vložení řádků do databáze přidáním objektů do přidruženého [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> kolekce a potom odeslání změn do databáze. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přeloží změny do příslušné SQL `INSERT` příkazy.  
  
> [!NOTE]
>  Můžete přepsat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] výchozí metody pro `Insert`, `Update`, a `Delete` databáze operace. Další informace najdete v tématu [přizpůsobení vložit, aktualizovat a odstranit operace](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Vývojáře, kteří používají [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] můžete použít [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] vyvíjet uložené procedury k tomuto účelu.  
  
 Následující postup předpokládá, že platný <xref:System.Data.Linq.DataContext> naváže připojení k databázi Northwind. Další informace najdete v tématu [postupy: připojení k databázi](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### <a name="to-insert-a-row-into-the-database"></a>O vložení řádku do databáze  
  
1.  Vytvořte nový objekt, který obsahuje data ve sloupci na odeslání.  
  
2.  Přidat nový objekt, který má [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] `Table` kolekci spojenou s cílovou tabulkou v databázi.  
  
3.  Odeslání změn do databáze.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu vytvoří nový objekt typu `Order` a naplní s příslušnými hodnotami. Potom přidá nový objekt, který má `Order` kolekce. Nakonec dojde k odeslání změn do databáze jako nový řádek `Orders` tabulky.  
  
 [!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Správa je v konfliktu změn](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Metody DataContext (Návrhář relací objektů)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Postupy: přiřazení uložené procedury k provedení aktualizací, vložení a odstranění (Návrhář relací objektů)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
 [Vytvoření a odeslání změn dat](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)