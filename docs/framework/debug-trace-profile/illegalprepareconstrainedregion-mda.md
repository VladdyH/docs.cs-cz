---
title: illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4623e8060b93c9331c99f9713598e177b6807472
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131310"
---
# <a name="illegalprepareconstrainedregion-mda"></a>illegalPrepareConstrainedRegion – pomocník spravovaného ladění (MDA)
`illegalPrepareConstrainedRegion` Pomocníka spravovaného ladění (MDA) se aktivuje při <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> volání metody bezprostředně nepředchází `try` příkaz obslužné rutiny výjimky. Toto omezení je na jazyk MSIL úrovně, takže je přípustné, aby bez kódu generování zdroje mezi volání a `try`, například pro komentáře.  
  
## <a name="symptoms"></a>Příznaky  
 Oblasti omezeného provádění (CER), který se nikdy zpracováván jako takové, ale jako jednoduchý výjimka bloku zpracování (`finally` nebo `catch`). V důsledku toho oblast nejde spustit v případě podmínku paměti nebo přerušení vlákna.  
  
## <a name="cause"></a>příčina  
 Vzor přípravy CER nedodrží správně.  Toto je událost chyby. <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> Volání metody používá k označení obslužné rutiny výjimek jako Představujeme CER v jejich `catch` / `finally` / `fault` / `filter` bloky musí být použita bezprostředně před `try` příkazu.  
  
## <a name="resolution"></a>Rozlišení  
 Ujistěte se, že volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se stane, bezprostředně před `try` příkazu.  
  
## <a name="effect-on-the-runtime"></a>Vliv na modul Runtime  
 Toto MDA nemá žádný vliv na CLR.  
  
## <a name="output"></a>Výstup  
 MDA zobrazí název metoda – volání <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> metodu, posun jazyk MSIL a zprávu s oznámením, volání okamžitě nepředchází začátek bloku try.  
  
## <a name="configuration"></a>Konfigurace  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje vzor, který způsobí, že toto MDA aktivaci.  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Zařazování spolupráce](../../../docs/framework/interop/interop-marshaling.md)
