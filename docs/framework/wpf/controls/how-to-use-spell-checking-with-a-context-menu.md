---
title: "Postupy: Použití kontroly pravopisu s místní nabídkou"
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
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 257f343a7fa01e251159797a83e89b533292b6b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a>Postupy: Použití kontroly pravopisu s místní nabídkou
Ve výchozím nastavení, když povolíte v ovládacím prvku úprav kontrolu pravopisu jako <xref:System.Windows.Controls.TextBox> nebo <xref:System.Windows.Controls.RichTextBox>, získat volby kontrola pravopisu v místní nabídce. Například pokud uživatelé klikněte pravým tlačítkem chybně, získají sadu pravopis návrhy či možnost **ignorovat všechny**. Ale když můžete přepsat výchozí místní nabídku s vlastními vlastní kontextové nabídky, tato funkce dojde ke ztrátě a budete muset napsat kód pro znovu povolit funkci Kontrola pravopisu v místní nabídce. Následující příklad ukazuje, jak povolit na <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvářející <xref:System.Windows.Controls.TextBox> s některé události, které se používají k implementaci v místní nabídce.  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód, který implementuje v místní nabídce.  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 Kód použitý pro to s <xref:System.Windows.Controls.RichTextBox> je podobný. Hlavní rozdíl je v parametru předaný `GetSpellingError` metoda. Pro <xref:System.Windows.Controls.TextBox>, předat celočíselný index pozice pomocí kurzoru:  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 Pro <xref:System.Windows.Controls.RichTextBox>, předat <xref:System.Windows.Documents.TextPointer> určující pozici pomocí kurzoru:  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a>Viz také  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [Povolit kontrolu ovládací prvek pro úpravy textu pravopisu](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [Použití vlastní Kontextová nabídka s textové pole](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)