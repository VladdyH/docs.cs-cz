---
title: 'Postupy: Nastavení vlastnosti po animaci pomocí scénáře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: b8e9c08075b13f8d6f701d5ac6ae4f8ea8949184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562258"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>Postupy: Nastavení vlastnosti po animaci pomocí scénáře
V některých případech může vypadat, že po byla animovaný nelze změnit hodnotu vlastnosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> se používá k animace barva <xref:System.Windows.Media.SolidColorBrush>. Při kliknutí na tlačítko, aktivuje se scénáři. <xref:System.Windows.Media.Animation.Timeline.Completed> Událost je zpracovávána tak, aby program obdrží oznámení při <xref:System.Windows.Media.Animation.ColorAnimation> dokončení.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>Příklad  
 Po <xref:System.Windows.Media.Animation.ColorAnimation> dokončí, program se pokusí změnit barvu stopy na modrou.  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 Předchozí kód nezobrazí žádnou: poskytl žlutý, štětce zůstanou, které je hodnota <xref:System.Windows.Media.Animation.ColorAnimation> který animovaný stopy. Základní hodnota vlastnosti (základní hodnota) je ve skutečnosti změnit na modrou. Ale zůstává žlutý hodnota efektivní nebo aktuální, protože <xref:System.Windows.Media.Animation.ColorAnimation> stále přepisují základní hodnota. Pokud chcete hodnotu opět efektivní hodnota, je nutné zastavit animace z ovlivňující vlastnost. Existují tři způsoby, jak to provést pomocí animací scénáře:  
  
-   Nastavení animace <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnosti <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   Odeberte celý scénáře.  
  
-   Odeberte animace z dané vlastnosti.  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Nastavte vlastnost FillBehavior má animace na zastavení  
 Nastavením <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> k <xref:System.Windows.Media.Animation.FillBehavior.Stop>, řekněte animace zastavit, které mají vliv na jeho vlastnost target po ukončení jeho aktivní období.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>Odeberte celý scénáře  
 Pomocí <xref:System.Windows.Media.Animation.RemoveStoryboard> aktivační události nebo <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> metoda, řekněte animací storyboard zastavit, které mají vliv na jejich vlastnosti cíle. Rozdíl mezi tento přístup a nastavení <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost je, že můžete odebrat scénáři v kdykoli, při <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> vlastnost má vliv pouze v případě animace dosáhne konce své aktivní období.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>Odebrání animace jednotlivé vlastnosti  
 Jiné technik zastavit animace neovlivňovaly vlastnost je použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> metodu objektu se animace. Určete vlastnost probíhá animovaný jako první parametr a `null` jako druhý.  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 Tento postup funguje i pro jiné scénáře animace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.Animation.RemoveStoryboard>  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
