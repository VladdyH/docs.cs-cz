---
title: Tabulka předdefinovaných typů (referenční dokumentace jazyka C#)
description: Klíčová slova pro předdefinované typy jazyka C#
ms.date: 08/17/2018
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: fd9ba878d77bdb219542db55bb38023c60c7bec4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507309"
---
# <a name="built-in-types-table-c-reference"></a>Tabulka předdefinovaných typů (referenční dokumentace jazyka C#)

V následující tabulce jsou uvedeny klíčová slova pro vestavěné C# typy, které jsou aliasy předdefinovaných typů v <xref:System> oboru názvů.  
  
|Typ jazyka C#|Typ formátu .NET|  
|--------------|-------------------------|  
|[bool](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|  
|[byte](byte.md)|<xref:System.Byte?displayProperty=nameWithType>|  
|[sbyte](sbyte.md)|<xref:System.SByte?displayProperty=nameWithType>|  
|[char](char.md)|<xref:System.Char?displayProperty=nameWithType>|  
|[decimal](decimal.md)|<xref:System.Decimal?displayProperty=nameWithType>|  
|[double](double.md)|<xref:System.Double?displayProperty=nameWithType>|  
|[float](float.md)|<xref:System.Single?displayProperty=nameWithType>|  
|[int](int.md)|<xref:System.Int32?displayProperty=nameWithType>|  
|[uint](uint.md)|<xref:System.UInt32?displayProperty=nameWithType>|  
|[long](long.md)|<xref:System.Int64?displayProperty=nameWithType>|  
|[ulong](ulong.md)|<xref:System.UInt64?displayProperty=nameWithType>|  
|[object](object.md)|<xref:System.Object?displayProperty=nameWithType>|  
|[short](short.md)|<xref:System.Int16?displayProperty=nameWithType>|  
|[ushort](ushort.md)|<xref:System.UInt16?displayProperty=nameWithType>|  
|[string](string.md)|<xref:System.String?displayProperty=nameWithType>|  
  
## <a name="remarks"></a>Poznámky

Všechny typy v tabulce, s výjimkou `object` a `string`, jsou označovány jako jednoduché typy.  
  
Jazyce C# zadejte klíčová slova a jejich aliasy jsou zaměnitelné. Například je možné deklarovat celočíselné proměnné pomocí některé z následující deklarace:  

```csharp
int x = 123;
System.Int32 y = 123;
```

Použití [typeof](typeof.md) operátor zobrazíte <xref:System.Type?displayProperty=nameWithType> instanci, která představuje zadaný typ:

```csharp
Type stringType = typeof(string);
Console.WriteLine(stringType.FullName);

Type doubleType = typeof(System.Double);
Console.WriteLine(doubleType.FullName);

// Output:
// System.String
// System.Double
```

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Referenční tabulky pro typy](reference-tables-for-types.md)
- [Typy hodnot](value-types.md)
- [Odkazové typy](reference-types.md)
- [Tabulka výchozích hodnot](default-values-table.md)
- [dynamic](dynamic.md)
