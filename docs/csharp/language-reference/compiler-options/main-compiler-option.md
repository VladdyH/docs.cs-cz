---
title: -main (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2f3c9daf98bfe77ea9462c8126f7a8368016875c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516663"
---
# <a name="-main-c-compiler-options"></a>-main (možnosti kompilátoru C#)
Tato možnost určuje třídu, která obsahuje položku, přejděte na program, pokud obsahuje více než jedné třídy **hlavní** metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 Typ, který obsahuje **hlavní** metody.  
 Název zadaný třídy musí být plně kvalifikovaný; musí obsahovat úplný obor názvů obsahující třídu, za nímž následuje název třídy. Například, když `Main` metoda se nachází uvnitř `Program` třídy v `MyApplication.Core` obor názvů, parametrem kompilátoru musí být `-main:MyApplication.Core.Program`.
  
## <a name="remarks"></a>Poznámky  
 Pokud kompilace obsahuje více než jeden typ [hlavní](../../../csharp/programming-guide/main-and-command-args/index.md) metodu, můžete určit, jaký typ obsahuje **hlavní** metodu, která chcete použít jako vstupní bod do programu.  
  
 Tato možnost je pro použití při kompilaci souboru .exe.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **aplikace** stránku vlastností.  
  
3.  Upravit **spouštěcí objekt** vlastnost.  
  
     Programové nastavení tohoto parametru kompilátoru, naleznete v tématu <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `t2.cs` a `t3.cs`, určující, který **hlavní** metoda najdete v `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
