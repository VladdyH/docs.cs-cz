---
title: Vrátí nebo přeskočit elementy v pořadí
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 228de9f3b92d45866c98976be08b84988a2db8d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359875"
---
# <a name="return-or-skip-elements-in-a-sequence"></a>Vrátí nebo přeskočit elementy v pořadí
Použití <xref:System.Linq.Queryable.Take%2A> operátor a vrátí zadaný počet elementů v pořadí a pak přeskočit zbytek.  
  
 Použití <xref:System.Linq.Queryable.Skip%2A> operátor přeskočit zadaný počet elementů v pořadí a pak se vraťte zbytek.  
  
> [!NOTE]
>  <xref:System.Linq.Enumerable.Take%2A> a <xref:System.Linq.Enumerable.Skip%2A> mají určitá omezení, když jsou použity v dotazy pro SQL Server 2000. Další informace najdete v tématu "Přeskočit a trvat výjimky v systému SQL Server 2000" položky v [Poradce při potížích s](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přeloží <xref:System.Linq.Queryable.Skip%2A> pomocí poddotazu SQL `NOT EXISTS` klauzule. Tento překlad má následující omezení:  
  
-   Argument musí být sada. Multisets nejsou podporovány, i v případě, že řazení.  
  
-   Vygenerovaný dotazu může být mnohem složitější než dotazu generované pro základní dotaz, na kterém <xref:System.Linq.Queryable.Skip%2A> platí. Tato složitost může způsobit snížení výkonu nebo i vypršení časového limitu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Take` vybrat prvních pět `Employees` pronajaty formou. Všimněte si, že kolekce je nejdřív seřazené podle `HireDate`.  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Linq.Queryable.Skip%2A> vyberte všechny kromě nejnákladnější 10 `Products`.  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kombinuje <xref:System.Linq.Queryable.Skip%2A> a <xref:System.Linq.Queryable.Take%2A> metody pro přeskočte prvních 50 záznamy a pak se vraťte další 10.  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> operace jsou dobře definované pouze proti seřazené sady. Pro multisets nebo Neseřazený sady sémantiky není definován.  
  
 Z důvodu omezení na pořadí v SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pokusí přesunout řazení argument <xref:System.Linq.Queryable.Take%2A> nebo <xref:System.Linq.Queryable.Skip%2A> operátor výsledek operátor.  
  
> [!NOTE]
>  Překlad se liší pro [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] a [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)]. Pokud budete chtít použít <xref:System.Linq.Queryable.Skip%2A> s dotazem jakékoli složitosti, použijte [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].  
  
 Vezměte v úvahu následující [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazu [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Přesune řazení na konec v kódu SQL následujícím způsobem:  
  
```  
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 Když <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou zřetězen dohromady, všechny zadané pořadí musí být konzistentní. Jinak výsledky nejsou definovány.  
  
 Pro nezáporné, konstantní argumenty pro integrální podle specifikace SQL obě <xref:System.Linq.Queryable.Take%2A> a <xref:System.Linq.Queryable.Skip%2A> jsou dobře definovaný.  
  
## <a name="see-also"></a>Viz také  
 [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Převod standardních operátorů dotazů](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
