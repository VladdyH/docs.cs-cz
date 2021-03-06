---
title: Výjimky za běhu v nativních aplikací .NET
ms.date: 03/30/2017
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efb16c1e947cd832da88b53a3522a5928e77ae06
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501708"
---
# <a name="runtime-exceptions-in-net-native-apps"></a>Výjimky za běhu v nativních aplikací .NET
Je důležité, otestovat buildy vydaných verzí vaší aplikace pro univerzální platformu Windows na jejich cílové platformy, protože jsou zcela odlišná konfigurace debug a release. Ve výchozím nastavení konfiguraci ladění používá modul runtime .NET Core pro kompilaci aplikace ale konfiguraci vydané verze používá .NET Native pro kompilaci aplikace do nativního kódu.  
  
> [!IMPORTANT]
>  Informace pro řešení inovací [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, které vám dává možnost Při testování verze vaší aplikace najdete v tématu "krok 4: ručně vyřešit chybějí metadata: v [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md) téma, stejně jako [reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) a [ Odkaz na soubor konfigurace modulu runtime direktivy (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="debug-and-release-builds"></a>Ladění a sestavení pro vydání  
 Když sestavení pro ladění spuštěn proti modulu runtime .NET Core, nebyl byl zkompilován do nativního kódu. Díky tomu všechny služby obvykle poskytuje modul runtime, které jsou k dispozici pro vaši aplikaci.  
  
 Na druhé straně sestavení pro vydání kompiluje do nativního kódu pro jeho cílové platformy, odebere většina závislostí na externí moduly runtime a knihovny a silně optimalizuje kód pro maximální výkon.  
  
 Při ladění buildů vydaných verzí, které jsou kompilovány pomocí .NET Native:  
  
-   Používáte .NET Native ladicího stroje, který se liší od normální .NET nástroje pro ladění.  
  
-   Spustitelný soubor je zmenšení co největší míře. Jedním ze způsobů, .NET Native snižuje velikost spustitelný soubor je výrazně ořezávání zprávy výjimek modulu runtime, větší podrobně popsány v tématu [zprávy výjimek modulu Runtime](#Messages) oddílu.  
  
-   Váš kód je silně optimalizovaná. To znamená, že vkládání se používá, kdykoli je to možné. (Vkládání přesune kódu z externího rutin do volání rutiny.)   Skutečnost, že .NET Native poskytuje specializované modulu runtime a implementuje agresivní vkládání ovlivňuje zásobníku volání, který se zobrazí při ladění.  Další informace najdete v tématu [zásobníku volání modulu Runtime](#CallStack) oddílu.  
  
> [!NOTE]
>  Můžete řídit, zda sestavení ladění a vydání se kompilují pomocí .NET Native řetězce nástrojů zaškrtnutím nebo zrušením zaškrtnutí **kompilovat s .NET Native řetězce nástrojů** pole.   Všimněte si však, že Windows Store vždy kompilovat produkční verzi vaší aplikace pomocí .NET Native řetězec nástroje.  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a>Zprávy výjimek modulu runtime  
 Chcete-li minimalizovat velikost spustitelný soubor aplikace .NET Native neobsahuje celý text zprávy o výjimkách. Modul runtime výjimky vyvolané v sestaveních pro vydání v důsledku toho nemusí zobrazit celý text zprávy o výjimkách. Místo toho může obsahovat text podřetězec spolu s odkazem pro další informace. Informace o výjimce může například zobrazit jako:  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 Pokud je třeba zpráva o výjimce dokončeno, spusťte sestavení pro ladění. Předchozí informace o výjimce ze sestavení pro vydání může například vypadat takto v laděném sestavení:  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a>Zásobník volání modulu runtime  
 Z důvodu vkládání a další optimalizace zásobník volání zobrazí aplikací zkompilován s .NET Native řetězce nástrojů nemusí vám pomohou cestu k výjimku při běhu se tak jasně identifikovat.  
  
 Pokud chcete získat úplný zásobník, spusťte místo toho sestavení pro ladění.  
  
## <a name="see-also"></a>Viz také  
 [Ladění univerzálních aplikací pro .NET Native Windows](https://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [Začínáme](../../../docs/framework/net-native/getting-started-with-net-native.md)
