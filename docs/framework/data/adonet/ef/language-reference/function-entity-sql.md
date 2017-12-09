---
title: FUNKCE (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bb88992-37ed-4991-ace5-55be612a2c4d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 40c8f218238492bbbc4af543aa6f9a635454b359
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="function-entity-sql"></a>FUNKCE (entita SQL)
Definuje funkci v oboru příkaz dotazu Entity SQL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
FUNCTION function-name  
( [ { parameter_name <type_definition>   
        [ ,...n ]  
  ]  
) AS ( function_expression )   
  
<type_definition>::=  
    { data_type | COLLECTION ( <type_definition> )   
                | REF ( data_type )   
                | ROW ( row_expression )   
        }   
```  
  
## <a name="arguments"></a>Arguments  
 `function-name`  
 Název funkce.  
  
 `parameter-name`  
 Název parametru ve funkci.  
  
 `function_expression`  
 Platný výraz Entity SQL, který je funkce. Příkaz ve funkci může fungovat na `parameter_name` funkci byl předán parametry.  
  
 `data_type`  
 Název podporovaného typu.  
  
 KOLEKCE (< type_definition`>` )  
 Výraz, který vrátí kolekce podporované typy, řádky nebo odkazy.  
  
 REF **(**`data_type`**)**  
 Výraz, který vrátí odkaz na typ entity.  
  
 ŘÁDEK **(**`row_expression`**)**  
 Výraz, který vrátí anonymní, strukturálně zadali záznamů z jednoho nebo více hodnot. Další informace najdete v tématu [řádek](../../../../../../docs/framework/data/adonet/ef/language-reference/row-entity-sql.md).  
  
## <a name="remarks"></a>Poznámky  
 Víc funkcí se stejným názvem lze deklarovat vložením, tak dlouho, dokud se liší funkce podpisů. Další informace najdete v tématu [rozlišení přetížení funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
 Vložená funkce jde volat v Entity SQL příkazu až poté, co byla definována v tomto příkazu. Vložená funkce lze však volat uvnitř jiné vložená funkce před i po definování volaná funkce. V následujícím příkladu funkce A volání funkce B předtím, než je definována funkce B:  
  
 `Function A() as ('A calls B. ' + B())`  
  
 `Function B() as ('B was called.')`  
  
 `A()`  
  
 Další informace najdete v tématu [postupy: volání funkce definované uživatelem](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02).  
  
 Funkce lze deklarovat také v přímo pro model. Funkce, které jsou deklarované v modelu se stejným způsobem provést, protože funkce deklarované vložené v příkazu. Další informace najdete v tématu [funkce definované uživatelem](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md).  
  
## <a name="example"></a>Příklad  
 Následující příkaz Entity SQL definuje funkci `Products` celočíselnou hodnotu pro filtrování vrácených produktů, která má.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function1)]  
  
## <a name="example"></a>Příklad  
 Následující příkaz Entity SQL definuje funkci `StringReturnsCollection` , která má kolekci řetězců pro filtrování vrácených kontaktů.  
  
 [!code-csharp[DP EntityServices Concepts 2#FUNCTION2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#function2)]  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Jazyk SQL entity](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)