---
title: 'Postupy: pomocí uložených procedur mapovaný pro více výsledků obrazců'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 03a003bd5b09ae19b01dcc9880137661ba6fccae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356787"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a>Postupy: pomocí uložených procedur mapovaný pro více výsledků obrazců
Pokud uložená procedura může vrátit více obrazců výsledek, nemohou být návratový typ typu důrazně do obrazců jeden projekce. I když [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] může generovat všechny možné projekce typy, ho nemůže vědět pořadí, ve kterém bude vrácen.  
  
 Protějšek tento scénář s uloženými procedurami, které vytváří více obrazců výsledek postupně. Další informace najdete v tématu [postupy: použití uložené procedury mapovaný pro sekvenční tvarů výsledek](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).  
  
 <xref:System.Data.Linq.Mapping.ResultTypeAttribute> Atribut se používá k uloženým procedurám, které vracejí víc typů výsledek určit sadu typů procedura může vrátit.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu SQL tvar výsledku závisí na vstupu (`shape =1` nebo `shape = 2`). Nevíte, které projekce bude vrácen první.  
  
```  
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a>Příklad  
 Podobný následujícímu kódu byste použili k spouštět tuto uloženou proceduru.  
  
> [!NOTE]
>  Je nutné použít <xref:System.Data.Linq.IMultipleResults.GetResult%2A> vzor získat enumerátor správného typu, podle vašeho vědomí uložené procedury.  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
