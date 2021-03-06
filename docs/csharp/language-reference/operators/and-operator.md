---
title: '&amp; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510975"
---
# <a name="amp-operator-c-reference"></a>&amp; – Operátor (referenční dokumentace jazyka C#)

`&` Operátor je podporován ve dvou formách: operátor address-of unární nebo binární logický operátor.

## <a name="unary-address-of-operator"></a>Unární operátor address-of

Unární `&` operátor vrátí adresu svého operandu. Další informace najdete v tématu [postupy: získávání adresy proměnné](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).

Operátor address-of `&` vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.

## <a name="integer-logical-bitwise-and-operator"></a>Celé číslo logického bitového operátoru AND

Pro celočíselné typy `&` vypočítá logické bitové operace AND jeho operandy operátoru:

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> V předchozím příkladu binární literály: [zavedený C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) a [rozšířené v C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

Vzhledem k tomu, že operace s celočíselnými typy jsou obecně povoleny na typy výčtu `&` operátor také podporuje [výčtu](../keywords/enum.md) operandy.

## <a name="boolean-logical-and-operator"></a>Logická logického operátoru AND

Pro [bool](../keywords/bool.md) operandy, `&` operátor vypočítá logický operátor AND operandů. Výsledek `x & y` je `true` Pokud mají oba `x` a `y` jsou `true`. V opačném případě je výsledek `false`.

`&` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu druhého operandu. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

[Podmiňovací operátor AND](conditional-and-operator.md) `&&` také vypočítá logické a z operandů, ale je vyhodnocen jako druhý operand pouze v případě, že první operand vyhodnocen jako `true`.

Pro operandy typu s možnou hodnotou Null bool, chování `&` operátor je konzistentní s logikou s hodnotou tři SQL. Další informace najdete v tématu [bool? typ](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) binárního souboru `&` operátor. Když binární soubor `&` je operátor přetížen, [operátor přiřazení AND](and-assignment-operator.md) `&=` je také implicitně přetížená.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátoru address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) a [logické operátory](~/_csharplang/spec/expressions.md#logical-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [| – operátor](or-operator.md)
- [^ – operátor](xor-operator.md)
- [~ – operátor](bitwise-complement-operator.md)
- [& & – operátor](conditional-and-operator.md)
