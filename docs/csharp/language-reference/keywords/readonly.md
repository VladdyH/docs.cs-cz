---
title: ReadOnly – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: b50d3b571afb3128c973baaf7d7178da705382bd
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146167"
---
# <a name="readonly-c-reference"></a>readonly – modifikátor (Referenční dokumentace jazyka C#)

`readonly` – Klíčové slovo je modifikátor, který je možné ve třech kontextech:

- V [pole deklarace](#readonly-field-example), `readonly` označuje, že přiřazení pro pole může probíhat jenom jako součást deklarace nebo v konstruktoru ve stejné třídě.
- V [ `readonly struct` definice](#readonly-struct-example), `readonly` znamená, že `struct` je neměnný.
- V [ `ref readonly` metoda návratový](#ref-readonly-return-example), `readonly` modifikátor označuje, že metoda vrátí odkaz a zápisu nejsou povoleny na tento odkaz.

Poslední dvě kontexty byly přidány v jazyce C# 7.2.

## <a name="readonly-field-example"></a>Pole určené jen pro čtení, například

V tomto příkladu je hodnota pole `year` nelze změnit v metodě `ChangeYear`, i když je k ní přiřadí hodnota v konstruktoru třídy:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Můžete přiřadit hodnoty k `readonly` pouze v následujících kontextů:

- Pokud je proměnná inicializována v deklaraci, například:

```csharp
public readonly int y = 5;
```

- V konstruktoru instance třídy, která obsahuje deklaraci pole instance.
- V statický konstruktor třídy, která obsahuje deklaraci statického pole.

Kontexty konstruktoru jsou také pouze kontextech, ve kterých je možné předat `readonly` jako pole [si](out-parameter-modifier.md) nebo [ref](ref.md) parametru.

> [!NOTE]
> `readonly` – Klíčové slovo se liší od [const](const.md) – klíčové slovo. A `const` pole mohou být inicializovány pouze v deklaraci pole. A `readonly` pole je možné přiřadit více než jednou v deklaraci pole nebo v jakékoli konstruktoru. Proto `readonly` pole může mít různé hodnoty v závislosti na použitém konstruktoru. Také, zatímco `const` pole je konstantu kompilace `readonly` pole lze použít pro konstanty runtime jako v následujícím příkladu:

```csharp
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:

`p2.y = 66;        // Error`

Zobrazí se chybová zpráva kompilátoru:

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a>Příklad struktury jen pro čtení

`readonly` Modifikátor `struct` definice deklaruje, že struktura **neměnné**. Každé pole instance `struct` musí být označen `readonly`, jak je znázorněno v následujícím příkladu:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

V předchozím příkladu [automatické vlastnosti jen pro čtení](../../properties.md#read-only) k deklaraci jeho úložiště. Který dává pokyn kompilátoru k vytvoření `readonly` pomocná pole pro tyto vlastnosti. Můžete také deklarovat `readonly` přímo pole:

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

Přidání pole nejsou označeny `readonly` vygeneruje Chyba kompilátoru `CS8340`: "Pole instancí struktur jen pro čtení musí být jen pro čtení."

## <a name="ref-readonly-return-example"></a>Příklad vrácené REF jen pro čtení

`readonly` Modifikátor `ref return` označuje, že výsledný odkaz nelze upravit. Následující příklad vrátí odkaz na počátku. Používá `readonly` modifikátor označuje, že volající nelze měnit původu:

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
Typ vrácený nemusí být `readonly struct`. Libovolný typ, který může být vrácen `ref` může být vrácen `ref readonly`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](modifiers.md)
- [const](const.md)
- [Pole](../../programming-guide/classes-and-structs/fields.md)
