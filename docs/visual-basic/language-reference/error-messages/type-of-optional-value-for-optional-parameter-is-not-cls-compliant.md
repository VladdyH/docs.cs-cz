---
title: Typ nepovinné hodnoty pro nepovinný parametr &lt;parametername&gt; není kompatibilní se Specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: dd77cd8cbd36f7681e2597d908dd8e55bf249392
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960346"
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a>Typ nepovinné hodnoty pro nepovinný parametr &lt;parametername&gt; není kompatibilní se Specifikací CLS
Postup je označen jako `<CLSCompliant(True)>` deklaruje, ale [volitelné](../../../visual-basic/language-reference/modifiers/optional.md) parametr s výchozí hodnotou typu nedodržující předpisy.  
  
 Postup, který má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS. To platí pro typy parametrů, návratový typ a typy všech místních proměnných. Platí také pro výchozími hodnotami nepovinných parametrů.  
  
 Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:  
  
-   [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Pokud použijete <xref:System.CLSCompliantAttribute> atribut na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů. Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.  
  
 Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40042  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud volitelný parametr musí mít výchozí hodnotu tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>. Procedura nemůže být kompatibilní se Specifikací CLS.  
  
-   Pokud procedura musí být kompatibilní se Specifikací CLS, změňte typ tuto výchozí hodnotu na nejbližší typ. kompatibilní se Specifikací CLS. Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647. Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.  
  
-   Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Například `int` je často 16 bitů v jiných prostředích. Pokud přijímáte 16bitové celé číslo z takové součásti, deklarujte ho jako `Short` místo `Integer` v spravovaného kódu jazyka Visual Basic.