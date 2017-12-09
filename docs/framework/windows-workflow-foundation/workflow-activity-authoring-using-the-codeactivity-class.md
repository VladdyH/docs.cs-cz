---
title: "Používání třídy CodeActivity vytváření aktivit pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 675997cdf44992d4eaad5cb4595fe28d3de436d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Používání třídy CodeActivity vytváření aktivit pracovního postupu
Aktivity vytvořené pomocí dědění z <xref:System.Activities.CodeActivity> můžete implementovat základní imperativní chování přepsáním <xref:System.Activities.CodeActivity.Execute%2A> metoda.  
  
## <a name="using-codeactivitycontext"></a>Pomocí CodeActivityContext  
 Funkce modulu runtime pracovního postupu je přístupná prostřednictvím <xref:System.Activities.CodeActivity.Execute%2A> metoda pomocí členy `context` parametr typu <xref:System.Activities.CodeActivityContext>. Funkcí dostupných prostřednictvím <xref:System.Activities.CodeActivityContext> patří:  
  
-   Získání a nastavení hodnoty proměnné a argumenty.  
  
-   Vlastní sledování funkce pomocí <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Přístup k vlastnostem provádění aktivity pomocí <xref:System.Activities.CodeActivityContext.GetProperty%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Chcete-li vytvořit vlastní aktivitu, která dědí z CodeActivity  
  
1.  Otevřete[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Vyberte **soubor**, **nové**a potom **projektu**. Vyberte **Workflow 4.0** pod **Visual C#** v **typy projektů** a vyberte **v2010** uzlu. Vyberte **knihovna aktivit** v **šablony** okno. Název nového projektu HelloActivity.  
  
3.  Klikněte pravým tlačítkem na Activity1.xaml v HelloActivity projektu a vyberte **odstranit**.  
  
4.  Klikněte pravým tlačítkem na projekt HelloActivity a vyberte **přidat** a potom **třída**. Pojmenujte novou třídu HelloActivity.cs.  
  
5.  V souboru HelloActivity.cs, přidejte následující `using` direktivy.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Ujistěte se, nové třídy dědí <xref:System.Activities.CodeActivity> přidáním základní třídu pro deklaraci třídy.  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  Přidání funkce do třídy přidáním <xref:System.Activities.CodeActivity.Execute%2A> metoda.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Použití <xref:System.Activities.CodeActivityContext> vytvoření záznamu sledování.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```