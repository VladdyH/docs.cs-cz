---
title: 'Postupy: Transformace štětce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: ebc8d4c6cb36d76b70691cce183f9e6070d19822
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507044"
---
# <a name="how-to-transform-a-brush"></a>Postupy: Transformace štětce
Tento příklad ukazuje, jak transformovat <xref:System.Windows.Media.Brush> objektů pomocí jejich transformaci dvě vlastnosti: <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A>.  
  
 Následující příklady používají <xref:System.Windows.Media.RotateTransform> obměna obsah <xref:System.Windows.Media.ImageBrush> o 45 stupňů.  
  
 Je vidět na následujícím obrázku <xref:System.Windows.Media.ImageBrush> bez <xref:System.Windows.Media.RotateTransform>, s <xref:System.Windows.Media.RotateTransform> u <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost a s <xref:System.Windows.Media.RotateTransform> u <xref:System.Windows.Media.Brush.Transform%2A> vlastnost.  
  
 ![Štětec RelativeTransform workflow a transformovat nastavení](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>Příklad  
 V prvním příkladu se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost <xref:System.Windows.Media.ImageBrush>. <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> objektu jsou nastaveny na 0,5, která je relativní souřadnice středový bod tohoto obsahu. V důsledku toho <xref:System.Windows.Media.ImageBrush> obsah otočí o jeho střed.  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 V druhém příkladu platí také <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.Media.ImageBrush>, nicméně v tomto příkladu <xref:System.Windows.Media.Brush.Transform%2A> vlastnost místo <xref:System.Windows.Media.Brush.RelativeTransform%2A> vlastnost.  
  
 Otočit štětec o jeho střed, příklad nastaví <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti <xref:System.Windows.Media.RotateTransform> objektu na absolutní souřadnice. Vzhledem k tomu, že štětec jsou vykreslovány obdélníku, který je 175 o 90 pixelů, je středový bod obdélníku (87.5, 45).  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 Popis toho, jak <xref:System.Windows.Media.Brush.RelativeTransform%2A> a <xref:System.Windows.Media.Brush.Transform%2A> vlastnosti fungují, najdete v článku [přehled transformace štětce](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md).  
  
 Úplnou ukázku najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o štětcích najdete v tématu [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled transformace štětce](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
