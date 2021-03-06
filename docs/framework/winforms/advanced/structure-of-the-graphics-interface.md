---
title: Struktura rozhraní grafiky
ms.date: 03/30/2017
helpviewer_keywords:
- GDI+, using managed interface
- graphics [Windows Forms], class structure
ms.assetid: 010a1e46-656b-40a1-8d5d-87aa05ee1243
ms.openlocfilehash: 625bd5818d58fd659af69d4985d629f055123e54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525899"
---
# <a name="structure-of-the-graphics-interface"></a>Struktura rozhraní grafiky
Spravované třídy rozhraní pro [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsahuje o 60 třídy, 50 výčty a struktury 8. <xref:System.Drawing.Graphics> Třída je základem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] funkce; je třída, která ve skutečnosti nevykresluje čar, křivek, obrázky, bitové kopie a text.  
  
## <a name="important-classes"></a>Důležité třídy  
 Mnoho tříd pracovat společně <xref:System.Drawing.Graphics> třídy. Například <xref:System.Drawing.Graphics.DrawLine%2A> metoda obdrží <xref:System.Drawing.Pen> objekt, který obsahuje atributy (barvu, šířku, přerušovaná čára a podobně) na řádku, které se mají vykreslovat. <xref:System.Drawing.Graphics.FillRectangle%2A> Metoda může přijímat ukazatel na <xref:System.Drawing.Drawing2D.LinearGradientBrush> objekt, který pracuje <xref:System.Drawing.Graphics> objekt vyplníte obdélníku postupně Změna barev. <xref:System.Drawing.Font> a <xref:System.Drawing.StringFormat> objekty ovlivnit způsob <xref:System.Drawing.Graphics> objekt nevykresluje text. A <xref:System.Drawing.Drawing2D.Matrix> objekt ukládá a zpracovává Světové transformace <xref:System.Drawing.Graphics> objekt, který se používá k otočit, škálovat a překlopit bitové kopie.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje několik struktury (například <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Point>, a <xref:System.Drawing.Size>) pro uspořádání dat grafiky. Navíc určité třídy slouží především strukturované datové typy. Například <xref:System.Drawing.Imaging.BitmapData> třída je Pomocník pro <xref:System.Drawing.Bitmap> třída a <xref:System.Drawing.Drawing2D.PathData> třída je Pomocník pro <xref:System.Drawing.Drawing2D.GraphicsPath> třídy.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] definuje několik výčty, které jsou kolekce související konstanty. Například <xref:System.Drawing.Drawing2D.LineJoin> výčet obsahuje prvky <xref:System.Drawing.Drawing2D.LineJoin.Bevel>, <xref:System.Drawing.Drawing2D.LineJoin.Miter>, a <xref:System.Drawing.Drawing2D.LineJoin.Round>, který zadejte stylů, které umožňuje připojit dva řádky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled grafiky](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [Informace o spravovaném kódu GDI+](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [Použití spravovaných grafických tříd](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
