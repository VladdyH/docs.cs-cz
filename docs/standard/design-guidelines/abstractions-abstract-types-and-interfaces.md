---
title: Abstrakce (abstraktní typy a rozhraní)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: KrzysztofCwalina
ms.openlocfilehash: 4ff79af968c8a0a360cade687b8c60cdd71de192
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149910"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>Abstrakce (abstraktní typy a rozhraní)
Abstrakce je typ, který popisuje kontrakt ale neposkytuje úplnou implementaci kontraktu. Abstrakce jsou obvykle implementovány jako abstraktní třídy nebo rozhraní a začne s kvalitně definované sady referenční dokumentaci popisující požadovaný sémantiku typy implementace kontraktu. Některé z vašich nejdůležitějších abstrakce v rozhraní .NET Framework zahrnují <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, a <xref:System.Object>.  
  
 Architektury můžete rozšířit pomocí implementace konkrétního typu implementujícího typ podporuje smlouvy abstrakci a pomocí rozhraní API náročné (nasazeny na) tento konkrétní typ odběru.  
  
 Smysl a užitečné abstrakce, která dokáže odolat zkušební doba je velmi obtížné navrhnout. Hlavní problémy s dokončením je stále správnou sadu členů, častěji a ne méně. Pokud abstrakci má příliš mnoho členů, bude obtížné či nemožné i k implementaci. Pokud má moc malý počet členů pro funkci přislíbeném, bude v mnoha scénářích zajímavých zbytečná.  
  
 Příliš mnoho odběrů v rámci také negativně ovlivnit využitelnost rozhraní framework. Často je poměrně obtížné porozumět abstrakci bez nutnosti porozumět, jak zapadá do větší přehled o konkrétní implementace a rozhraní API fungujícími v odběru. Názvy abstrakce a jejich členy jsou také nutně abstract, které často jsou nejasné a unapproachable bez první Principy širšího kontextu jejich použití.  
  
 Abstrakce však poskytují velmi výkonné rozšíření, což často nesmí shodovat s další mechanismy rozšiřitelnosti. Jsou základem mnoho vzorech architektury, jako jsou moduly plug-in IOC (Inversion) ovládacího prvku, kanály a tak dále. Jsou také velmi důležité pro testovatelnost architektur. Dobré abstrakce umožňují zástupných procedur si náročné závislosti za účelem testování částí. Stručně řečeno abstrakce zodpovídají za sought-after bohatost moderních architektur objektově orientovaný.  
  
 **X DO NOT** zadejte abstrakce, pokud jsou neotestovali ve vývoji několik rozhraní API využívání abstrakce a konkrétní implementace.  
  
 **✓ DO** zvolit pečlivě abstraktní třídy a rozhraní při navrhování abstrakci.  
  
 **✓ CONSIDER** poskytuje odkaz testy pro konkrétní implementace abstrakce. Tyto testy by měly umožnit uživatelům k ověření, zda jejich implementace správnou implementaci kontraktu.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)  
- [Navrhování pro rozšiřitelnost](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
