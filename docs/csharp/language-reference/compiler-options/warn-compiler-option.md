---
title: -warn (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 14656fa25ea1d01339bd63efb999e938e1243db8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865605"
---
# <a name="-warn-c-compiler-options"></a>-warn (možnosti kompilátoru C#)
**-Warn** určuje úroveň upozornění kompilátoru k zobrazení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Úroveň pro upozornění, které chcete zobrazit pro kompilaci: nižší číslice zobrazit pouze vysokou závažností upozornění; vyšší čísla popisují další varování. Platné hodnoty jsou 0-4:  
  
|Úroveň upozornění|Význam|  
|-------------------|-------------|  
|0|Vypne emise všechny zprávy upozornění.|  
|1|Zobrazuje závažná upozornění.|  
|2|Zobrazí upozornění úrovně 1 a některé, méně závažných upozornění, jako jsou třeba upozornění o skrývání členů třídy.|  
|3|Zobrazí upozornění úrovně 2 a některé, méně závažných upozornění, jako jsou třeba upozornění, která se vždycky vyhodnotí výrazy `true` nebo `false`.|  
|4 (výchozí)|Zobrazí všechna upozornění úrovně 3 a informační upozornění.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete získat informace o chybě nebo upozornění, můžete vyhledat kód chyby v indexu nápovědy. Další způsoby, jak získat informace o chybě nebo upozornění, najdete v části [chyby kompilátoru jazyka C#](../../../csharp/language-reference/compiler-messages/index.md).  
  
 Použití [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) považovat všechna upozornění jako chyby. Použití [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) zakázat určitá upozornění.  
  
 **-w** je zkratka pro **-warn**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevřete v projektu **vlastnosti** stránky.  
  
2.  Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3.  Upravit **úroveň pro upozornění** vlastnost.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` kompilátor zobrazí pouze upozornění úrovně 1:  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
