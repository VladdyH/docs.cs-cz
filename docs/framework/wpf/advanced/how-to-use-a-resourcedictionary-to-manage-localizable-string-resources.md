---
title: 'Postupy: Správa zdrojů lokalizovatelných řetězců pomocí ResourceDictionary'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
ms.openlocfilehash: 76ff3f688b5d3e7122254990076edb21fe6ae119
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544495"
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Postupy: Správa zdrojů lokalizovatelných řetězců pomocí ResourceDictionary
Tento příklad ukazuje, jak používat <xref:System.Windows.ResourceDictionary> k prostředkům lokalizovatelný řetězec balíčku pro aplikace Windows Presentation Foundation (WPF).  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a>Použít ResourceDictionary ke správě prostředků lokalizovatelný řetězec  
  
1.  Vytvoření <xref:System.Windows.ResourceDictionary> obsahující řetězce, které byste chtěli lokalizaci. Následující kód ukazuje příklad.  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Tento kód definuje prostředek řetězce `localizedMessage`, typu <xref:System.String>, z <xref:System> oboru názvů v mscorlib.dll.  
  
2.  Přidat <xref:System.Windows.ResourceDictionary> k vaší aplikaci, pomocí následujícího kódu.  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Použít řetězec prostředku z kódu, pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] podobně jako následující.  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Pomocí řetězce prostředků z kódu, pomocí kódu podobně jako tento.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Lokalizace aplikace. Další informace najdete v tématu [lokalizaci aplikace](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).
