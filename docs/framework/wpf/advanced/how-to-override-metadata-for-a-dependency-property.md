---
title: "Postupy: Přetížení metadat pro vlastnost závislosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [WPF], overriding for dependency properties
- dependency properties [WPF], overriding metadata for
- overriding metadata for dependency properties [WPF]
ms.assetid: f90f026e-60d8-428a-933d-edf0dba4441f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e7cb01c81b5fb24830cbe0cc39befbadaf4405e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-metadata-for-a-dependency-property"></a>Postupy: Přetížení metadat pro vlastnost závislosti
Tento příklad ukazuje, jak lze přepsat výchozí metadat vlastností závislostí, který přichází z zděděná třída, voláním <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> metoda a poskytuje metadata pro konkrétní typ.  
  
## <a name="example"></a>Příklad  
 Definováním jeho <xref:System.Windows.PropertyMetadata>, třídu můžete definovat chování, vlastnost závislosti, například jeho výchozí hodnotu a vlastnost systému zpětných volání. Mnoho závislostí vlastnosti třídy již máte výchozí metadata navázat součástí jejich procesu registrace. Jedná se o vlastnostech závislostí, které jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]. Třídu, která dědí vlastnost závislosti prostřednictvím jeho dědičnosti tříd můžete přepsat původní metadata, tak, aby charakteristiky vlastnosti, která může být změněna pomocí metadat bude shodovat s požadavky na žádné konkrétní podtřídy.  
  
 Přepsání metadata na vlastnost závislosti je třeba provést před tuto vlastnost je uskutečnění používá vlastnost systémem (Tato hodnota rovná čas, které jsou vytvářeny instance určité instance objektů, které registrují vlastnost). Volání <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> musí provést v rámci statické konstruktory typu, který poskytuje sám sebe jako `forType` parametr <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>. Pokud se pokusíte změnit metadata po existovat instance typu vlastníka, to nevydá výjimky, ale způsobí nekonzistentní chování systému vlastnost. Navíc metadata lze pouze přepsat jednou podle typu. Následné pokusy o přepsání metadata stejného typu, vyvolá výjimku.  
  
 V následujícím příkladu, vlastní třídu `MyAdvancedStateControl` přepsání zadaná pro metadata `StateProperty` podle `MyAdvancedStateControl` s novými metadaty vlastnost. Například výchozí hodnota `StateProperty` je nyní `true` Pokud je vlastnost dotazován na nově vytvořený `MyAdvancedStateControl` instance.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#myadvancedstatecontrol)]
[!code-vb[PropertySystemEsoterics#MyAdvancedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#myadvancedstatecontrol)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.DependencyProperty>  
 [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastnosti vlastní závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Postupy: témata](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)