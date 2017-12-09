---
title: "Použití atributů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e23649c5d833bef8b74ec5d3b9c22235756580e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="applying-attributes"></a>Použití atributů
Na základě následujícího postupu použijte atribut na prvek kódu.  
  
1.  Definujte nový atribut nebo použijte stávající atribut importováním oboru názvů z rozhraní .NET Framework.  
  
2.  Použijte atribut na prvek kódu tak, že ho umístíte bezprostředně před prvek.  
  
     Jednotlivé jazyky mají vlastní syntaxi atributů. V jazyce C++ a jazyce C# je atribut ohraničen hranatými závorkami a oddělen od prvku prázdným znakem, který může obsahovat konec řádku. V jazyce Visual Basic je atribut ohraničen ostrými závorkami a musí být umístěn na stejném logickém řádku. Znak pro pokračování řádku lze použít v případě, že je vyžadován konec řádku.
  
3.  Zadejte poziční parametry a pojmenované parametry atributu.  
  
     Poziční parametry jsou povinné a musí předcházet jakýmkoli pojmenovaným parametrům – odpovídají parametrům jednoho z konstruktorů atributu. Pojmenované parametry jsou volitelné a odpovídají vlastnostem atributu pro čtení a zápis. V C++ a C#, zadejte `name` = `value` pro každý volitelný parametr, kde `name` je název vlastnosti. V jazyce Visual Basic zadejte `name`:=`value`.  
  
 Atribut je při kompilaci kódu vložen do metadat a je k dispozici pro modul CLR (Common Language Runtime) a vlastní nástroje nebo aplikace prostřednictvím služeb reflexe runtime.  
  
 Na základě pravidel zadávání názvů končí všechny názvy atributů slovem Attribute. Avšak několik jazyků, které používají modul runtime, jako jsou například Visual Basic a C#, nevyžadují zadávání úplného názvu atributu. Například, pokud chcete inicializovat <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, stačí ho jako referenční **zastaralé**.  
  
## <a name="applying-an-attribute-to-a-method"></a>Použití atributu na metodu  
 Následující příklad kódu ukazuje, jak deklarovat **System.ObsoleteAttribute**, které značky kódu jako zastaralé. Řetězec `"Will be removed in next version"` je předán atributu. Tento atribut vygeneruje upozornění kompilátoru, které zobrazí předaný řetězec, pokud je volán kód popisovaný atributem.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Používání atributů na úrovni sestavení  
 Pokud chcete použít atribut na úrovni sestavení, použijte **sestavení** (`Assembly` v jazyce Visual Basic) – klíčové slovo. Následující kód ukazuje **AssemblyTitleAttribute** použít na úrovni sestavení.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Pokud použijete tento atribut, bude řetězec `"My Assembly"` umístěn v manifestu sestavení v části souboru s metadaty. Můžete zobrazit atribut buď pomocí [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nebo tak, že vytvoříte vlastní program načíst atribut.  
  
## <a name="see-also"></a>Viz také  
 [Atributy](../../../docs/standard/attributes/index.md)  
 [Načítání informací uložených v atributech](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Koncepty](/cpp/windows/attributed-programming-concepts)  
 [Atributy](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)