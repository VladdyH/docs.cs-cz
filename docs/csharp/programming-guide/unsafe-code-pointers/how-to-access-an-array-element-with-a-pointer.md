---
title: Jak přistupovat k elementu pole pomocí ukazatele (C# Programming Guide)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 0e76ebddd8b703e8d0de4aa6825cbd6d0221079b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861647"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>Jak přistupovat k elementu pole pomocí ukazatele (C# Programming Guide)

V nezabezpečeném kontextu můžete přístup k prvku v paměti pomocí přístup k prvkům ukazatele, jak je znázorněno v následujícím příkladu:

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

Výraz v hranatých závorkách musí být implicitně převeditelný na `int`, `uint`, `long`, nebo `ulong`. Operace p [e] odpovídá \*(p + e). Podobně jako C a C++, přístup k prvkům ukazatel nekontroluje celočíselných chyby.

## <a name="example"></a>Příklad

V tomto příkladu jsou 123 umístění v paměti přidělené na pole znaků `charPointer`. Pole se používá k zobrazení písmena malá a velká písmena ve dvou [pro](../../../csharp/language-reference/keywords/for.md) smyčky.

Všimněte si, že výraz `charPointer[i]` je ekvivalentní výraz `*(charPointer + i)`, a získáte stejný výsledek jedním ze dvou výrazů.

[!code-csharp[csProgGuidePointers#11](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_1.cs)]

[!code-csharp[csProgGuidePointers#12](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-an-array-element-with-a-pointer_2.cs)]

**Velká písmena:**
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**
**malá písmena:**
**abcdefghijklmnopqrstuvwxyz**

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Výrazy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [Typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed – příkaz](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
