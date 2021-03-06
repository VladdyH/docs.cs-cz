---
title: Obecní delegáti (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 7596ace0ea404cc345d73c0979fa7bd03a26b047
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857533"
---
# <a name="generic-delegates-c-programming-guide"></a>Obecní delegáti (Průvodce programováním v C#)
A [delegovat](../../../csharp/language-reference/keywords/delegate.md) můžete definovat vlastní parametry typu. Kód, že odkazy obecného delegátu možné zadat argument typu k vytvoření uzavřený konstruovaný typ., stejně jako při vytvoření instance generické třídy nebo volání obecné metody, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C# verze 2.0 obsahuje novou funkci s názvem metody skupiny převod, který se vztahuje na typy konkrétní, jakož i obecných delegátů a umožňuje zapisovat na předchozí řádek s této zjednodušenou syntaxi:  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Delegáti definované v rámci obecné třídy můžete použít parametry typu obecné třídy v stejným způsobem jako metody třídy.  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 Argument typu obsahující třídy, musíte zadat kód, který odkazuje na delegáta následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Obecní delegáti jsou zvláště užitečné při definování události založen na typické návrhový vzor, protože argument odesílatele, mohou být silného typu a už musí být převeden do a z <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Obecné metody](../../../csharp/programming-guide/generics/generic-methods.md)  
- [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
- [Obecná rozhraní](../../../csharp/programming-guide/generics/generic-interfaces.md)  
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)  
- [Obecné typy](~/docs/standard/generics/index.md)
