---
title: Výpočetní součet hodnot v číselného pořadí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: d1c49d45eaf82101e57e0886af52a134d24b1651
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361426"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Výpočetní součet hodnot v číselného pořadí
Použití <xref:System.Linq.Enumerable.Sum%2A> operátor vypočítat součet číselných hodnot v pořadí.  
  
 Všimněte si těchto vlastností `Sum` operátor v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]:  
  
-   Agregační operátor standardní – operátor dotazu `Sum` vyhodnotí na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null. V [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sémantika SQL jsou ponechána beze změny. Z tohoto důvodu `Sum` vyhodnocen jako null místo na nulu pro prázdnou sekvencí nebo sekvenci, která obsahuje jenom hodnoty Null.  
  
-   Platí omezení SQL na mezilehlých výsledků agregace v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Součet počty 32bitové celé číslo není počítaný pomocí 64-bit výsledky a pro může dojít k přetečení [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překlad `Sum`. Tato možnost existuje i v případě implementace standardní – operátor dotazu nezpůsobí přetečení pro odpovídající sekvence v paměti.  
  
## <a name="example"></a>Příklad  
 Vyhledá celkový nákladní všech objednávek v následujícím příkladu `Order` tabulky.  
  
 Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Příklad  
 Následující příklad vyhledá celkový počet jednotek v pořadí pro všechny produkty.  
  
 Pokud spustíte tento dotaz proti ukázková databáze Northwind, je výstup: `780`.  
  
 Všimněte si, že musíte vysílat `short` typy (například `UnitsOnOrder`) protože `Sum` nemá žádné přetížení pro krátké typy.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Viz také  
 [Agregační dotazy](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
