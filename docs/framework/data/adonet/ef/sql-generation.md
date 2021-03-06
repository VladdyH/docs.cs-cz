---
title: Generování SQL
ms.date: 03/30/2017
ms.assetid: 0e16aa02-d458-4418-a765-58b42aad9315
ms.openlocfilehash: e130fed22b9ea450c848d45195346dc717e63515
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764525"
---
# <a name="sql-generation"></a>Generování SQL
Při psaní poskytovatele pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], musí překládat [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] příkaz stromy do SQL, který můžete porozumět konkrétní databázi, například Transact-SQL pro SQL Server nebo PL/SQL pro databázi Oracle. V této části se dozvíte, jak vyvíjet součást generování SQL (pro vyberte dotazy) pro [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele. Informace o vložení, aktualizace a odstranit dotazy najdete [generování SQL úpravy](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md).  
  
 Zjistit, v této části, měli byste se seznámit s [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] a Model poskytovatele ADO.NET. Také byste měli porozumět stromy příkazů a <xref:System.Data.Common.CommandTrees.DbExpression>.  
  
## <a name="the-role-of-the-sql-generation-module"></a>Role modulu generování jazyka SQL  
 Modul generování SQL [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zprostředkovatele překládá stromu příkazů daný dotaz do jednoho příkazu SQL SELECT, který se zaměřuje SQL:1999 – databáze kompatibilní. Vygenerovaný SQL by měl mít jako několika vnořené dotazy míře. Modul generování SQL by neměl zjednodušit strom příkazů výstup dotazu. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Se to udělat, například odstraňuje spojení a sbalení uzly po sobě jdoucích filtrů.  
  
 <xref:System.Data.Common.DbProviderServices> Třída je výchozím bodem pro přístup k vrstvě generování SQL pro převod stromy příkazů do <xref:System.Data.Common.DbCommand>.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Tvar stromu příkazů](../../../../../docs/framework/data/adonet/ef/the-shape-of-the-command-trees.md)  
  
 [Generování SQL ze stromů příkazů – osvědčené postupy](../../../../../docs/framework/data/adonet/ef/generating-sql-from-command-trees-best-practices.md)  
  
 [Generování SQL ve zprostředkovateli ukázek](../../../../../docs/framework/data/adonet/ef/sql-generation-in-the-sample-provider.md)  
  
## <a name="see-also"></a>Viz také  
 [Zápis zprostředkovatele dat Entity Framework](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
