---
title: Obecné typy (Obecné) – přehled
description: Zjistěte, jak kód šablony, které umožňují definovat typ vláknově bezpečných datových struktur bez potvrzení do skutečný datový typ plnit obecných typů.
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 1d1899d482738bc6cc9f638b6a74eab8d4ca70c1
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49121178"
---
# <a name="generic-types-overview"></a>Přehled obecných typů

Vývojáři pomocí obecných typů neustále v .NET, zda implicitně nebo explicitně. Při použití LINQ v .NET, Všimli jste si někdy, že pracujete s <xref:System.Collections.Generic.IEnumerable%601>? Nebo pokud jste někdy viděli online ukázky "obecného úložiště" pro komunikaci se databází pomocí Entity Frameworku, nebyla uvidíte, že většina metod vrátí IQueryable<T>? Vám může mít přemýšleli, co **T** je v těchto příkladech a proč je tady.

Poprvé byla představena v rozhraní .NET Framework 2.0, **obecných typů** jsou v podstatě "kód šablony", který umožňuje vývojářům definovat [zajišťující bezpečnost typů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) datové struktury bez potvrzení do skutečný datový typ. Například <xref:System.Collections.Generic.List%601> je [obecné kolekce](xref:System.Collections.Generic) , který můžete deklarovat a používat s libovolného typu, jako například `List<int>`, `List<string>`, nebo `List<Person>`.

Abyste pochopili, proč jsou užitečné obecných typů, Pojďme se podívat na konkrétní třídu před a po přidání obecných typů: <xref:System.Collections.ArrayList>. V rozhraní .NET Framework 1.0 `ArrayList` elementy byly typu <xref:System.Object>. To znamená, že byl tiše převod libovolný prvek přidán `Object`. Stejné by mohlo dojít při čtení prvky ze seznamu. Tento proces se označuje jako [zabalení a rozbalení](../csharp/programming-guide/types/boxing-and-unboxing.md), a to má vliv na výkon. A víc než ale neexistuje žádný způsob, jak určit typ dat v seznamu v době kompilace. Díky tomu pro některé křehké kód. Obecné typy tento problém vyřešit tak, že definujete typ dat, který bude obsahovat každou instanci seznamu. Například můžete přidat pouze celých čísel na `List<int>` a přidávat jenom osoby `List<Person>`.

Obecné typy jsou také k dispozici za běhu. To znamená, že modul runtime ví, jaký typ struktury dat používáte a můžete ho uložit do paměti efektivněji.

V následujícím příkladu je malý program, který ukazuje efektivitu znalost data strukturovat typu za běhu:

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

Tento program vytvoří výstup podobný následujícímu:

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

První věc, kterou si všimnete, že je zde řazení obecného seznamu je výrazně rychlejší než řazení seznamu Obecné. Můžete také všimnout, jestli je typ obecný seznam jedinečných ([System.Int32]), že typ seznamu neobecnou je zobecněný. Vzhledem k tomu, že modul runtime ví Obecné `List<int>` je typu <xref:System.Int32>, může ukládat prvky seznamu v podkladové pole celé číslo v paměti, zatímco neobecné `ArrayList` má převést každý prvek seznamu na objekt. Jak ukazuje tento příklad, navíc přetypování trvat až čas a zpomalit řazení seznamu.

Další výhodou znalost typu vaše obecný modul runtime je lepší možnosti ladění. Při ladění obecný v jazyce C#, víte, jaký typ je každý prvek datové struktury. Bez obecných typů by nemáte představu, jaký typ byl každý prvek.

## <a name="see-also"></a>Viz také:

- [Úvod do obecných typů jazyka C#](https://msdn.microsoft.com/library/ms379564.aspx)
- [Programování průvodce v C# – obecné typy](../../docs/csharp/programming-guide/generics/index.md)
