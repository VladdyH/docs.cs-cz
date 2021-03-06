---
title: Vstupní bod (F#)
description: Zjistěte, jak nastavit vstupní bod do programu F#, zkompilovaný jako spustitelný soubor, ve kterém formálně spuštění.
ms.date: 05/16/2016
ms.openlocfilehash: 298500931d49c891a7a243295333df3a9f5d413e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45698376"
---
# <a name="entry-point"></a>Vstupní bod

Toto téma popisuje metody, která se používá k nastavení vstupní bod do programu F#.

## <a name="syntax"></a>Syntaxe

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *vazba funkce umožňují* je definice funkce v `let` vazby.

Vstupní bod programu, který je zkompilován je spustitelný soubor, ve kterém formálně spuštění. Zadejte vstupní bod do aplikace F# s použitím `EntryPoint` atribut programu `main` funkce. Tato funkce (vytvořené využitím `let` vazby) musí být poslední funkci v poslední zkompilovaný soubor. Poslední zkompilovaný soubor je poslední soubor v projektu nebo poslední soubor, který je předán do příkazového řádku.

Funkci vstupního bodu má typ `string array -> int`. Argumenty příkazového řádku k dispozici jsou předány `main` funkce v poli řetězců. Prvním prvkem pole je první argument; název spustitelného souboru, který není zahrnutý v poli, je to v některých jiných jazycích. Návratová hodnota se používá jako ukončovací kód procesu. Nula obvykle znamená úspěšné nenulové hodnoty udávající chybu. Neexistuje žádné vytváření názvů pro zvláštní význam nenulové návratové kódy; význam návratové kódy jsou specifické pro aplikaci.

Následující příklad ukazuje jednoduchý `main` funkce.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

Při spuštění tohoto kódu s příkazovým řádkem `EntryPoint.exe 1 2 3`, výstup je následující.

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a>Implicitní vstupní bod

Pokud program nemá žádné **EntryPoint** atribut, který explicitně určuje vstupní bod vazeb nejvyšší úrovně v posledním souboru ke kompilaci se používají jako vstupní bod.

## <a name="see-also"></a>Viz také:

- [Funkce](index.md)
- [Vazby let](let-bindings.md)
