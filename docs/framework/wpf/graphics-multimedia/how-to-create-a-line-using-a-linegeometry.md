---
title: "Postupy: Vytvoření čáry použitím LineGeometry"
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
helpviewer_keywords: graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acb2c3db2027f8a4e9594212d1f5af9ea1c8a43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a>Postupy: Vytvoření čáry použitím LineGeometry
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LineGeometry> třída k popisu řádku. A <xref:System.Windows.Media.LineGeometry> je definován jeho počáteční a koncové body.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.LineGeometry>.  A <xref:System.Windows.Shapes.Path> element slouží k vykreslení řádku.  Vzhledem k tomu, že má řádek žádné oblasti <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> není zadán; místo toho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti se používají.  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![Objekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Objekt LineGeometry čerpají z (10,20) na (100,130)  
  
 Třídy dalších jednoduchý geometrie zahrnují <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>. Tyto geometrie, jakož i složitější těch, můžete také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>. Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Vytváření kompozitních tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [Vytvoření obrazce pomocí Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)