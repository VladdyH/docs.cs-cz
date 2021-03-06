---
title: 'Postupy: práce se slovníky pomocí LINQ to XML (C#)'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: afe4fafb9963b4fc429f441349f8190c9a1e5bac
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739890"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a>Postupy: práce se slovníky pomocí LINQ to XML (C#)
Často je vhodné převést zpět na další datové struktury typy prvků datové struktury do XML a XML. Toto téma popisuje konkrétní implementaci tohoto přístupu obecné převedením <xref:System.Collections.Generic.Dictionary%602> XML a naopak.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá určitou formu funkční konstrukce, ve kterém dotaz nové projekty <xref:System.Xml.Linq.XElement> objekty a výsledné kolekce je předán jako argument pro konstruktor kořenové <xref:System.Xml.Linq.XElement> objektu.  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří slovník ze souboru XML.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 Tento kód vytvoří následující výstup:  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>Viz také

- [Projekce a transformace (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
