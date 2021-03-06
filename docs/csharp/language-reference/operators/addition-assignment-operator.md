---
title: += – operátor (Referenční dokumentace jazyka C#)
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ac9330e283cb58ae4e0ee7b644aa2c22bdf64c46
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192028"
---
# <a name="-operator-c-reference"></a>+= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení sčítání.

Pomocí výrazu `+=` operátorů, například

```csharp
x += y
```

je ekvivalentem

```csharp
x = x + y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.
  
Pro číselné typy [operátor sčítání](addition-operator.md) `+` kód vypočítá součet operandů. Pokud je jeden nebo oba operandy typu [řetězec](../keywords/string.md), zřetězí řetězcové reprezentace jeho operandy. Pro typy delegátů `+` operátor vrátí novou instanci delegáta, který je kombinací operandů.

Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md). Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

Následující příklad ukazuje použití `+=` operátor:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor sčítání](addition-operator.md) `+`, operátor přiřazení sčítání `+=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení sčítání.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) a [události přiřazení](~/_csharplang/spec/expressions.md#event-assignment) oddíly [ C# specifikace jazyka](../language-specification/index.md).
  
## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Události](../../programming-guide/events/index.md)
- [Delegáti](../../programming-guide/delegates/index.md)
