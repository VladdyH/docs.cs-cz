---
title: "Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DateTimePicker control [Windows Forms], display styles
- examples [Windows Forms], DateTimePicker control
- dates [Windows Forms], displaying in DateTimePicker control
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b92fec7565aad2a881f714f9232eae10bf7633c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-date-in-a-custom-format-with-the-windows-forms-datetimepicker-control"></a>Postupy: Zobrazení data ve vlastním formátu pomocí ovládacího prvku Windows Forms DateTimePicker
Windows Forms <xref:System.Windows.Forms.DateTimePicker> řízení poskytuje flexibilitu při formátování zobrazení data a časy v ovládacím prvku. <xref:System.Windows.Forms.DateTimePicker.Format%2A> Vlastnost umožňuje vybrat z předdefinovaných formátů, uvedené v <xref:System.Windows.Forms.DateTimePickerFormat>. Pokud žádná z nich je dostačující pro vaše záměry, můžete vytvořit vlastní formát styl pomocí formátu znaky uvedené v <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A>.  
  
### <a name="to-display-a-custom-format"></a>Vlastní formát zobrazení  
  
1.  Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost `DateTimePickerFormat.Custom`.  
  
2.  Nastavte <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> vlastnost na řetězci formátu.  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### <a name="to-add-text-to-the-formatted-value"></a>Chcete-li přidat text k formátovanou hodnotu  
  
1.  Pomocí jednoduchých uvozovek uzavřete libovolný znak, který není znak formátu jako "M" nebo oddělovač jako ":". Například řetězec formátu níže zobrazí aktuální datum ve formátu "Dnes je: 05:30:31 pátek 02 března 2012" v Czech (Czech Republic) jazykovou verzi.  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     V závislosti na nastavení jazykové verze, mohou být změněny žádné znaky, není uzavřený v jednoduchých uvozovkách. Například řetězec formátu výše zobrazí aktuální datum ve formátu "Dnes je: 05:30:31 pátek 02 března 2012" v Czech (Czech Republic) jazykovou verzi. Všimněte si, že první dvojtečkou uzavřen v jednoduchých uvozovkách, protože není určen jako rozdělujících znaků, protože je v hh: mm". V jinou jazykovou verzi, může být ve formátu zobrazí jako "Dnes je: 05.30.31 pátek 02 března 2012".  
  
## <a name="see-also"></a>Viz také  
 [DateTimePicker – ovládací prvek](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 [Postupy: nastavení a vracení kalendářních dat pomocí ovládacího prvku Windows Forms DateTimePicker – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)