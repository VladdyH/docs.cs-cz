---
title: 'Postupy: Vyplnění obrazce pomocí textury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: c1eb090bebcced125193c1db16087b6165d27ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523287"
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Postupy: Vyplnění obrazce pomocí textury
Můžete vyplnit uzavřený obrazec texturou pomocí <xref:System.Drawing.Image> třídy a <xref:System.Drawing.TextureBrush> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad doplní elipsy s bitovou kopií. Kód vytvoří <xref:System.Drawing.Image> objektu a pak předá adresu této <xref:System.Drawing.Image> jako argument pro objekt <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktor. Třetí příkaz škáluje bitovou kopii a čtvrtý příkaz výplní se třemi tečkami s opakovaných kopie škálovat bitové kopie.  
  
 V následujícím kódu <xref:System.Drawing.TextureBrush.Transform%2A> vlastnost obsahuje transformace, která je použita pro obrázek předtím, než se nevykreslí. Předpokládejme, že původní bitové kopie má 640 pixelů šířka a výška 480 pixelů. Transformovat zmenší bitovou kopii na 75 × 75 nastavením hodnoty vodorovného a svislého škálování.  
  
> [!NOTE]
>  V následujícím příkladu velikost image je 75 × 75 a velikost elipsy je 150 × 250. Vzhledem k tomu, že bitová kopie je menší, než se třemi tečkami, které je naplnění, se třemi tečkami je rozložen formou dlaždic s bitovou kopií. Je dosaženo dlaždice znamená, že obrázek se opakuje vodorovně a svisle dokud hranice tvaru. Další informace o dlaždice najdete v tématu [postupy: dlaždicové vyplnění obrazce pomocí obrázku](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Použití štětce k vyplnění obrazců](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
