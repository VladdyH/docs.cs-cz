---
title: 'Postupy: Použití oboru názvů My (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: a8ec3a96534693142d37d26ac0c08eec9298b178
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526203"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a>Postupy: Použití oboru názvů My (Průvodce programováním v C#)
<xref:Microsoft.VisualBasic.MyServices> Obor názvů (`My` v jazyce Visual Basic) poskytuje jednoduché a intuitivní přístup k počtu tříd rozhraní .NET Framework, což umožňuje napsat kód, který komunikuje s počítačem, aplikace, nastavení, prostředky a tak dále. Přestože původně navržený pro použití s jazykem Visual Basic `MyServices` oboru názvů lze použít v aplikacích jazyka C#.  
  
 Další informace o používání `MyServices` oboru názvů z jazyka Visual Basic naleznete v tématu [vývoj aplikací pomocí Moje](../../../visual-basic/developing-apps/development-with-my/index.md).  
  
## <a name="adding-a-reference"></a>Přidání odkazu  
 Než budete moct použít `MyServices` třídy ve vašem řešení, musíte přidat odkaz na knihovnu jazyka Visual Basic.  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a>Chcete-li přidat odkaz na knihovnu jazyka Visual Basic  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem myši **odkazy** uzel a vyberte možnost **přidat odkaz**.  
  
2.  Když **odkazy** se zobrazí dialogové okno, přejděte dolů v seznamu a vyberte Microsoft.VisualBasic.dll.  
  
     Můžete také přidejte následující řádek v `using` části na začátku programu.  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad příkladu volá různých statických metod, které jsou součástí `MyServices` oboru názvů. Pro tento kód zkompilovat musí být odkaz na knihovny Microsoft.VisualBasic.DLL přidat do projektu.  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 Ne všechny třídy v `MyServices` oboru názvů může být volána z aplikace v jazyce C#: například <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> třída není kompatibilní. V tomto konkrétním případě statických metod, které jsou součástí <xref:Microsoft.VisualBasic.FileIO.FileSystem>, které jsou také obsaženy v VisualBasic.dll, lze použít místo toho. Tady je například jak duplikovat adresář pomocí těchto metod:  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Obory názvů](../../../csharp/programming-guide/namespaces/index.md)  
- [Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md)
