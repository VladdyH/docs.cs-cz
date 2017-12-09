---
title: "SqlTypes a datové sady"
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
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 86132e266b4421cce048ea38fc91967267a6ae6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sqltypes-and-the-dataset"></a>SqlTypes a datové sady
ADO.NET 2.0 zavedená rozšířenou podporu typ `DataSet` prostřednictvím <xref:System.Data.SqlTypes> oboru názvů. Typy v <xref:System.Data.SqlTypes> poskytují datové typy jako typy dat v databázi systému SQL Server se stejnou sémantiku a přesnosti. Každý typ dat v <xref:System.Data.SqlTypes> ekvivalentní datový typ je v systému SQL Server se stejnou základní reprezentaci data.  
  
 Pomocí <xref:System.Data.SqlTypes> přímo v <xref:System.Data.DataSet> poskytuje několik výhod při práci s datovými typy systému SQL Server. <xref:System.Data.SqlTypes>podporuje stejnou sémantiku jako nativní datové typy systému SQL Server. Zadáním jednoho z <xref:System.Data.SqlTypes> v definici <xref:System.Data.DataColumn> eliminuje ztrátu přesnosti, který může nastat při převodu desítkový nebo číselný datový typy na jednu z běžné typy dat language runtime (CLR).  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Data.DataTable> objekt, explicitně definování <xref:System.Data.DataColumn> datové typy pomocí <xref:System.Data.SqlTypes> místo typy CLR. Vyplní celé kód <xref:System.Data.DataTable> s daty z Sales.SalesOrderDetail tabulky v databázi AdventureWorks v systému SQL Server. V okně konzoly zobrazí výstup ukazuje datový typ jednotlivých sloupců a hodnoty načíst ze serveru SQL Server.  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Mapování datového typu SQL Server](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Konfigurace parametrů a datové typy parametrů](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)