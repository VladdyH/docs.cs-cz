---
title: 'Postupy: Vytvoření dokumentace XML v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 3dfec94a3dd1b8da5d371529b91b47f018bb3843
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527593"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Postupy: Vytvoření dokumentace XML v jazyce Visual Basic
Tento příklad ukazuje, jak přidat komentáře k dokumentaci XML do kódu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>K vytvoření dokumentace XML pro typ nebo člen  
  
1.  V **Editor kódu**, umístěte kurzor na řádek nad tento typ nebo člen, pro kterou chcete vytvořit dokumentaci.  
  
2.  Typ `'''` (tří jednoduchých uvozovek).  
  
     Kostra XML pro typ nebo člen bude přidán do **Editor kódu**.  
  
3.  Přidáte popisné informace mezi odpovídající značky.  
  
    > [!NOTE]
    >  Pokud chcete přidat další řádky v rámci bloku dokumentace XML, musí začínat každého řádku `'''`.  
  
4.  Přidejte další kód, který používá typ nebo člen pomocí nového komentáře k dokumentaci XML.  
  
     Technologie IntelliSense zobrazí text z \<summary > značky pro tento typ nebo člen.  
  
5.  Zkompilujte kód a vygenerovat soubor XML obsahující komentáře k dokumentaci. Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
