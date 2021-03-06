---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 8a8068c467f9066af3153434187749fa80d254ca
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048395"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**- Refout** možnost určuje, kde referenční sestavení by mělo být výstupní cestu k souboru.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

 `filepath` Cesta a název souboru referenční sestavení. Obecně by měl být v dílčí složce primární sestavení. Doporučené konvence (používány nástrojem MSBuild), je umístit odkaz na sestavení v "ref /" podsložku vzhledem k primární sestavení. Všechny složky v `filepath` musí existovat; kompilátor nevytvoří je. 

## <a name="remarks"></a>Poznámky

Visual Basic podporuje `-refout` přepnout od verze 15.3.

Referenční sestavení jsou pouze metadata sestavení, která obsahují metadata, ale žádný implementační kód. Patří mezi ně typů a členů informace pro všechno, co s výjimkou anonymních typů. Jejich těla metod jsou nahrazeny jednoho `throw null` příkazu. Důvod pro použití `throw null` těla metod (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).

Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut. Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho). Z důvodu tohoto atributu moduly runtime odmítnout načíst referenční sestavení pro spuštění (ale stále může být načteny v kontextu pouze pro reflexi). Nástroje, které odpovídají na sestavení se muset ujistit, že se načítají referenční sestavení jako pouze pro reflexi; v opačném případě modul runtime vyvolá <xref:System.BadImageFormatException>.

`-refout` a [ `-refonly` ](refonly-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také
[-refout](refonly-compiler-option.md)   
[Kompilátor příkazového řádku jazyka Visual Basic](index.md)  
[Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)  

