---
title: Kdy použít výčet (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: e50057e114abae9fbf05c94ef0b60cf94b033a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647302"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>Kdy použít výčet (Visual Basic)
Výčty nabízí snadný způsob, jak pracovat s sady souvisejících konstanty. Na výčtu nebo `Enum`, je symbolický název pro sadu hodnot. Výčty jsou považovány za datové typy a můžete je použít k vytvoření sad konstanty pro použití s proměnnými a vlastnosti.  
  
## <a name="when-to-use-an-enumeration"></a>Kdy použít výčet  
 Vždy, když procedury přijímá omezenou sadu proměnných, zvažte použití výčet. Výčty zajistěte pro jasnější a srozumitelnější kód, zvláště pokud smysluplný názvy jsou použity.  
  
 Mezi výhody používání výčty patří:  
  
-   Snižuje chyby způsobené transpozice nebo chybným zadáním čísla.  
  
-   Lze snadno ke změně hodnot v budoucnu.  
  
-   Díky kód snadněji číst, což znamená, že je méně pravděpodobné, že se do ní ovládat chyby.  
  
-   Zajišťuje kompatibilitu. Váš kód s výčty, je méně pravděpodobné, že nezdaří, pokud v budoucnu někdo změní hodnoty odpovídající názvy členů.  
  
## <a name="naming-enumerations"></a>Pojmenování výčty  
 Použijte zásady vytváření názvů pro členy výčtu. Když Visual Basic dojde název člena výčtu, může být vyvolána výjimka, pokud obsahovat další odkazovaného typu knihovny se stejným názvem. Použijte jedinečnou předponu, která identifikuje hodnoty z vaší aplikace nebo součásti.  
  
 K odkazování na člena výčtu, je nutné kvalifikaci název člena s názvem výčtu jinak použít `Imports` příkaz. Další informace najdete v tématu [výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).  
  
## <a name="predefined-enumerations"></a>Předdefinované výčty  
 Visual Basic poskytuje řadu předdefinovaných výčty, jako například `FirstDayOfWeek` a `MsgBoxResult`, aby se usnadnilo kódu. Seznam naleznete v části [konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Postupy: Odkazování na člena výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Postupy: iterace výčet v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [Postupy: Určení řetězce spojeného s hodnotou výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Příkaz Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
