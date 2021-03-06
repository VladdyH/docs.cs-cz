---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: f64e47922aea35ac9ddf51428107af0d4002d33e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185820"
---
# <a name="-keycontainer"></a>-keycontainer
Určuje název kontejneru klíčů pro dvojice klíčů poskytnout sestavení silným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`container`|Požadováno. Soubor kontejneru, který obsahuje klíč. Název souboru uzavřete do uvozovek ("") Pokud název obsahuje mezery.|  
  
## <a name="remarks"></a>Poznámky  
 Kompilátor vytvoří komponentu sdílet tak, že vloží veřejný klíč do manifestu sestavení a podepíše konečné sestavení soukromým klíčem. Chcete-li generovat soubor s klíčem, zadejte `sn -k file` na příkazovém řádku. `-i` Možnost nainstaluje pár klíčů do kontejneru. Další informace najdete v tématu [Sn.exe (nástroj Strong Name)][Sn.exe (nástroj Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 Pokud kompilujete s `-target:module`, je název souboru klíče uložené v modulu a součástí sestavení, které se vytvoří, když kompilujete sestavení s [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Tuto možnost lze také nastavit jako vlastní atribut (<xref:System.Reflection.AssemblyKeyNameAttribute>) ve zdrojovém kódu pro jakýkoli modul Microsoft intermediate language (MSIL).  
  
 Můžete také předat údaje o šifrování pro kompilátor [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Použití [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) potřebujete částečně podepsaného sestavení.  
  
 Zobrazit [vytvoření a použití sestavení](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) Další informace o podepisování sestavení.  
  
> [!NOTE]
>  `-keycontainer` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.  
  
## <a name="example"></a>Příklad  
 Následující kód se zkompiluje zdrojový soubor `Input.vb` a Určuje kontejner klíče.  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Sestavení a globální mezipaměť sestavení (GAC)](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
