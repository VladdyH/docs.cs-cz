---
title: 'Postupy: zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 357cc488705ec3dab66543fa4814dbe3e6a22777
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562304"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Postupy: zápis smyčky Parallel.ForEach pomocí proměnných v místním oddílu
Následující příklad ukazuje, jak psát <xref:System.Threading.Tasks.Parallel.ForEach%2A> metodu, která používá oddíl místní proměnné. Při provedení smyčky <xref:System.Threading.Tasks.Parallel.ForEach%2A> dochází k rozdělení kolekce prostředků na několik oddílů. Každý oddíl má svou vlastní kopii oddílu místní proměnné. Oddíl místní proměnné je podobný [místní proměnné vlákna](xref:System.Threading.ThreadLocal%601), s tím rozdílem, že několik oddílů můžete spustit v jednom vlákně.
  
 Kód a parametry uvedené v tomto příkladu se velmi podobají příslušné metodě <xref:System.Threading.Tasks.Parallel.For%2A>. Další informace najdete v tématu [postupy: zápis smyčky Parallel.for pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Použití oddílu místní proměnné v <xref:System.Threading.Tasks.Parallel.ForEach%2A> smyčky, musíte volat jeden z přetížení metody, které přebírá dva parametry typu. První parametr typu `TSource`, určuje typ zdrojového prvku a druhý parametr typu `TLocal`, určuje typ oddílu místní proměnné.  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> přetížení pro výpočet součtu pole jednoho milionu prvků. Toto přetížení má čtyři parametry:  
  
-   `source`, který je zdrojem dat. Musí implementovat <xref:System.Collections.Generic.IEnumerable%601>. Zdroj dat v našem příkladu je člen jednoho milionu `IEnumerable<Int32>` vrácený <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> metody.  
  
-   `localInit`, nebo funkci, která inicializuje oddílu místní proměnné. Tato funkce se volá jednou pro každý oddíl, ve kterém <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> provede operaci. Náš příklad inicializuje proměnnou místní oddíl na hodnotu nula.  
  
-   `body`, <xref:System.Func%604> , který je vyvolán paralelní smyčkou při každé iteraci smyčky. Jeho podpis je `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Zadejte kód pro delegáta, a smyčka předá vstupní parametry, které jsou:  
  
    -   Aktuální prvek <xref:System.Collections.Generic.IEnumerable%601>.
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> proměnné, že vám pomůže v kódu tohoto delegáta zkontrolovat stav smyčky.  
  
    -   Proměnná místního oddílu.  
  
     Delegát vrátí oddílu místní proměnné, který se potom předá další iteraci smyčky, která se spustí v této konkrétní oddíl. Každý oddíl smyčky udržuje samostatnou instanci této proměnné.  
  
     V tomto příkladu přidá delegáta hodnotu každé celé číslo oddílu místní proměnné, která udržuje průběžný součet hodnot celočíselné prvky v tomto oddílu.  
  
-   `localFinally`, `Action<TLocal>` delegáta, který <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> vyvolá při opakování operace v každém oddílu byly dokončeny. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Metoda předá vaší `Action<TLocal>` delegovat konečnou hodnotu proměnná místního oddílu pro tento oddíl smyčky, a vy pak poskytnete kód, který provádí potřebné akce pro kombinace výsledku oddílu s výsledky z Další oddíly. Tento delegát lze vyvolat souběžně s několika úkoly. Z toho důvodu v příkladu se používá <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> metoda k synchronizaci přístupu k `total` proměnné. Vzhledem k tomu, že delegát je typu <xref:System.Action%601>, neexistuje žádná návratová hodnota.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Viz také:

- [Datový paralelismus](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [Postupy: Zápis smyčky Parallel.For pomocí proměnných v místním vláknu](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
- [Výrazy lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
