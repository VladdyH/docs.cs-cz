---
title: "Postupy: Vykreslení obrázku v oblasti"
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
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3edbe30347580bb4f9677d7fb98d3b4fd8b92cff
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-an-image"></a>Postupy: Vykreslení obrázku v oblasti
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ImageBrush> třídy Malování oblast s bitovou kopií. <xref:System.Windows.Media.ImageBrush> Zobrazí jeden obrázek, který je určený jeho <xref:System.Windows.Media.ImageBrush.ImageSource%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad barvy <xref:System.Windows.Controls.Control.Background%2A> tlačítka pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Ve výchozím nastavení <xref:System.Windows.Media.ImageBrush> roztahovány jeho image na nejbližší k oblasti, která jsou vykreslování. V předchozím příkladu obrázek je roztažen tak k vyplnění tlačítko, případně narušují bitovou kopii. Toto chování můžete ovládat nastavením <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.TileBrush> k <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>, což způsobí, že štětce k zachová poměr stran obrázku.  
  
 Pokud nastavíte <xref:System.Windows.Media.TileBrush.Viewport%2A> a <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti <xref:System.Windows.Media.ImageBrush>, můžete vytvořit opakující se vzorek. Následující příklad vybarví tlačítko pomocí vzor, který je vytvořený z image.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> třídy najdete v tématu [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Tento příklad kódu je součástí většího příkladu vztahujícího se k <xref:System.Windows.Media.ImageBrush> třídy. Kompletní příklad, najdete v části [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Viz také  
 [Malování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)