---
title: CType – funkce (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 7b1c7ae2a0126bf7cd487df4e9a7364c98e1c695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603016"
---
# <a name="ctype-function-visual-basic"></a>CType – funkce (Visual Basic)
Vrátí výsledek převodu explicitně výraz zadaný datový typ, objekt, struktura, třídu nebo rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>Součásti  
 `expression`  
 Jakýkoli platný výraz. Pokud hodnota `expression` je mimo povolený rozsah `typename`, vyvolá výjimku, Visual Basic.  
  
 `typename`  
 Libovolný výraz, který je právní v rámci `As` klauzuli v `Dim` prohlášení, to znamená, název žádné datový typ, objekt, struktura, třída nebo rozhraní.  
  
## <a name="remarks"></a>Poznámky  
  
> [!TIP]
>  Následující funkce můžete využít taky k převodu typu:  
>   
>  -   Zadejte například funkce pro převod `CByte`, `CDbl`, a `CInt` , proveďte převod na typ konkrétní. Další informace najdete v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md). Tyto operátory požadovat, aby jeden typ dědí nebo implementovat v případě druhého typu. Poskytují poněkud lepší výkon než `CType` při převodu do a z `Object` datového typu.  
  
 `CType` je zkompilovaná vložená, což znamená, že převod kódu je součástí kód, který se vyhodnotí výraz. V některých případech kód spustí rychleji, protože žádné procedury se nazývají provést převod.  
  
 Pokud je definovaný žádný převod z `expression` k `typename` (například z `Integer` k `Date`), Visual Basic zobrazí kompilaci chybová zpráva.  
  
 Pokud se nezdaří převod za běhu, je vyvolána příslušné výjimky. Pokud se zužující převod nezdaří, <xref:System.OverflowException> nejběžnější výsledek. Pokud není definován, převod <xref:System.InvalidCastException> v vyvolána. Například k tomu může dojít, pokud `expression` je typu `Object` a její typ spuštění nemá žádný převod do `typename`.  
  
 Pokud datový typ `expression` nebo `typename` je třídu nebo strukturu, které jste definovali, můžete definovat `CType` na tuto třídu nebo strukturu jako operátor převodu. Díky tomu `CType` fungovat jako *přetížený operátor*. Pokud to uděláte, můžete řídit chování převod na a z třídy nebo struktura, včetně výjimky, které může být vyvolána.  
  
## <a name="overloading"></a>Přetížení  
 `CType` Operátor mohou být přetíženy také na třídu nebo strukturu definované mimo váš kód. Pokud váš kód převede do nebo z takových třídu nebo strukturu, ujistěte se, pochopit chování jeho `CType` operátor. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Převedení dynamických objektů  
 Převody typů objektů dynamické provádí dynamické převody definovaný uživatelem, které používají <xref:System.Dynamic.DynamicObject.TryConvert%2A> nebo <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody. Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> způsobů, jak převést dynamický objekt.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `CType` funkce pro převod výraz, který se `Single` datového typu.  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 Další příklady najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Převodní funkce](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Postupy: Definice operátoru převodu](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Převod typů v rozhraní .NET Framework](../../../standard/base-types/type-conversion.md)
