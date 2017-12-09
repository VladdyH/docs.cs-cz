---
title: "Dotazování datové sady (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4f1b1a70025dc81bdf99c636b65c23d373e73a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="querying-datasets-linq-to-dataset"></a>Dotazování datové sady (LINQ na DataSet)
Po <xref:System.Data.DataSet> objekt naplněné s daty, můžete začít dotazování ho. Formulování dotazy s [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] je podobný používání [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] proti dalších [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]-povolené datové zdroje. Nezapomeňte, ale, že při použití [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazuje přes <xref:System.Data.DataSet> objekt dotazujete výčet <xref:System.Data.DataRow> objekty, místo výčet vlastního typu. To znamená, že můžete použít některý z členů <xref:System.Data.DataRow> tříd ve vaší [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazy. Umožňuje vytvořit bohatě a složité dotazy.  
  
 Stejně jako u jiných implementace [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], můžete vytvořit [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazů ve dvou různých formách: výraz syntaxe využívající dotazy a syntaxe dotazu na základě metod. Další informace o těchto dvou formách najdete v tématu [Začínáme s dotazy LINQ](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9). Můžete použít syntaxe výrazu dotazu nebo syntaxe dotazu na základě metod provádět dotazy proti jedné tabulky v <xref:System.Data.DataSet>, před několika tabulkám ve <xref:System.Data.DataSet>, nebo podle tabulky v zadaný <xref:System.Data.DataSet>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Dotazy na jedné tabulky](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy jedné tabulky.  
  
 [Dotazy křížové tabulky](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 Popisuje, jak provádět dotazy křížové tabulky.  
  
 [Dotazování typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 Popisuje, jak dotazovat zadali <xref:System.Data.DataSet> objekty.  
  
## <a name="see-also"></a>Viz také  
 [LINQ na DataSet příklady](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)  
 [Načítání dat do datové sady](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)