---
title: Anonymní funkce (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 90a5a71f83a7117a7468bab0d9fe9d013685ebbe
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515236"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonymní funkce (Průvodce programováním v C#)
Anonymní funkce je "vloženě" příkaz nebo výraz, který se dá použít, kdykoli se očekává typ delegáta. Slouží k inicializaci pojmenovaný delegát nebo předat místo pojmenovaný delegát typu jako parametr metody.  
  
 Existují dva druhy anonymní funkce, které jsou jednotlivě podrobněji popsána v následujících tématech:  
  
-   [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [Anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Výrazy lambda mohou být vázány na stromy výrazů a také na delegáty.  
  
## <a name="the-evolution-of-delegates-in-c"></a>Vývoj v jazyce C# delegátů  
 V jazyce C# 1.0 vytvořeného instanci delegáta explicitně inicializuje s metodu, která byla definována kdekoli v kódu. 2.0 C# představila koncept anonymní metody jako způsob, jak zapsat vložený nepojmenovaný výkazu bloků, které mohou být provedeny v vyvolání delegáta. C# 3.0 představila výrazy lambda, které jsou v principu podobná anonymní metody, ale výrazová a stručné. Tyto dvě funkce se souhrnně nazývají *anonymní funkce*. Obecně platí, aplikace, jejichž cílem verze 3.5 a novější [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] by měl použití výrazů lambda.  
  
 Následující příklad ukazuje vývoj vytvoření delegáta z 1.0 C# do jazyka C# 3.0:  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Příkazy, výrazy a operátory](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Stromy výrazů (C#)](../concepts/expression-trees/index.md)  
