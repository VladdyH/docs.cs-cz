---
title: 'Postupy: vrácení sady řádků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 725718f5-da29-4841-9f53-aafef64ba977
ms.openlocfilehash: a2666b752d936e10d377113d5bf18111393df3ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-return-rowsets"></a>Postupy: vrácení sady řádků
Tento příklad vrací sadu řádků z databáze a zahrnuje vstupní parametr filtrovat výsledek.  
  
 Při spuštění uložené procedury, jež vrací sadu řádků, je použít *výsledek* třídu, která ukládá vrátí z uložené procedury. Další informace najdete v tématu [analýza technologie LINQ to SQL zdrojový kód](../../../../../../docs/framework/data/adonet/sql/linq/analyzing-linq-to-sql-source-code.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu představuje uložené procedury, jež vrací řádky zákazníků a používá vstupní parametr vrátit pouze řádky tohoto seznamu "Praha" jako město zákazníka. Příklad předpokládá Výčtový `CustomersByCityResult` třídy.  
  
```  
CREATE PROCEDURE [dbo].[Customers By City]  
    (@param1 NVARCHAR(20))  
AS  
BEGIN  
    -- SET NOCOUNT ON added to prevent extra result sets from  
    -- interfering with SELECT statements.  
    SET NOCOUNT ON;  
    SELECT CustomerID, ContactName, CompanyName, City from Customers  
        as c where c.City=@param1  
END  
```  
  
 [!code-csharp[DLinqSprox#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#1)]
 [!code-vb[DLinqSprox#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Uložené procedury](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 [Stažení ukázkových databází](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
