---
title: S výjimkou (entita SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: fb7f8040e9e310798b003ad02614cd464e996389
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760203"
---
# <a name="except-entity-sql"></a>S výjimkou (entita SQL)
Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operand EXCEPT nejsou také vrácená z dotazu výrazu napravo od EXCEPT operand. Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a>Arguments  
 `expression`  
 Libovolný platný dotaz výraz, který vrátí kolekce k porovnání s kolekcí vrácená z jiného výrazu dotazu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.  
  
## <a name="remarks"></a>Poznámky  
 S výjimkou je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory. Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava. V následující tabulce jsou uvedeny prioritu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.  
  
|Priorita|Operátory|  
|----------------|---------------|  
|Nejvyšší|INTERSECT|  
||UNION<br /><br /> UNION ALL|  
||S VÝJIMKOU|  
|Nejnižší|EXISTUJE<br /><br /> PŘEKRYTÍ.<br /><br /> VYROVNÁNÍ<br /><br /> NASTAVENÍ|  
  
## <a name="example"></a>Příklad  
 Následující dotaz Entity SQL pomocí operátoru EXCEPT vracet kolekci všech jedinečných hodnot ze dvou výrazů dotazu. Dotaz je založen na modelu prodej AdventureWorks. Pro zkompilování a spuštění tohoto dotazu, postupujte takto:  
  
1.  Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
