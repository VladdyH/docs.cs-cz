---
title: '&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: f2bac6a4320980d80a9b6c2597dcf8dc6f08ac70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865020"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)
Operátor přiřazení posunutí doprava.  
  
## <a name="remarks"></a>Poznámky  
 Výraz ve tvaru  
  
```csharp  
x >>= y  
```  
  
 je vyhodnocen jako  
  
```csharp  
x = x >> y  
```  
  
 s tím rozdílem, že `x` se jenom vyhodnotí jednou. [>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` přímo podle zadaného množství určené `y`.  
  
 >> = Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Operátory jazyka C#](../../../csharp/language-reference/operators/index.md)
