---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 1459484b858137836fcfdcd9db46d8e99a06e9c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185206"
---
# <a name="-delaysign"></a>-delaysign
Určuje, zda bude sestavení zcela nebo částečně podepsáno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. Použití `-delaysign-` potřebujete-li plně podepsané sestavení. Použití `-delaysign+` Pokud chcete umístit veřejný klíč v sestavení a rezervy místa pro podepsané hash. Výchozí hodnota je `-delaysign-`.  
  
## <a name="remarks"></a>Poznámky  
 `-delaysign` Možnost nemá žádný vliv, pokud nejsou použity s [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) nebo [- keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).  
  
 Pokud budete požadovat plně podepsané sestavení, kompilátor vytvoří hodnotu hash souboru, který obsahuje manifest (metadata sestavení) a podepíše tuto hodnotu hash pomocí soukromého klíče. Výsledný digitální podpis je uložen do souboru obsahujícího manifest. Pokud je sestavení podepisováno, kompilátor a neukládá podpis, ale rezervy místa v souboru tak, že podpis se dají přidat později.  
  
 Například s použitím `-delaysign+`, vývojář v organizaci můžete distribuovat bez znaménka testovací verze sestavení, které testerů můžete zaregistrovat do globální mezipaměti sestavení a použít. Po dokončení práce na sestavení je osoba zodpovědná za soukromého klíče organizace plně podepsat sestavení. Tento takové chrání privátní klíče organizace před vyzrazením, zároveň umožní všem vývojářům umožňuje pracovat na sestavení.  
  
 Zobrazit [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Chcete-li nastavit - delaysign v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.   
  
2.  Klikněte na tlačítko **podepisování** kartu.  
  
3.  Nastavte hodnotu **zpoždění podepsání** pole.  
  
## <a name="see-also"></a>Viz také  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
