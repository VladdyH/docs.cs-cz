---
title: Odvození textu elementu
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: b70f76d2702ebcb098c64ea84900b723fbc137ab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516491"
---
# <a name="inferring-element-text"></a>Odvození textu elementu
Pokud element obsahuje text a nemá žádný podřízený element odvození podle tabulky jako je například (elementy s atributy) nebo opakované prvků, nový sloupec s názvem **TableName_Text** se přidá do tabulky, kterou si odvozuje pro element. Text obsažen v elementu bude přidána na řádek v tabulce a uložená v novém sloupci. **ColumnMapping** vlastnost nového sloupce, který bude nastavena na **MappingType.SimpleContent**.  
  
 Zvažte například následující kód XML.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Procesu odvození vytvoří tabulku s názvem **Element1** se dvěma sloupci: **attr1** a **Element1_Text**. **ColumnMapping** vlastnost **attr1** sloupec bude nastaven na **MappingType.Attribute**. **ColumnMapping** vlastnost **Element1_Text** sloupec bude nastaven na **MappingType.SimpleContent**.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|Hodnota1|Text1|  
  
 Pokud element obsahuje text, ale má také podřízené prvky, které obsahují text, nebude na tabulku pro ukládání textu obsaženy v prvku přidán sloupec. Text obsažen v elementu budou ignorovány, zatímco je zahrnut text podřízené elementy v řádku v tabulce. Zvažte například následující kód XML.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Procesu odvození vytvoří tabulku s názvem **Element1** s jedním sloupcem s názvem **ChildElement1**. Text **ChildElement1** element bude obsahovat řádek v tabulce. Další text se bude ignorovat. **ColumnMapping** vlastnost **ChildElement1** sloupec bude nastaven na **MappingType.Element**.  
  
 **Datová sada:** prvek DocumentElement  
  
 **Tabulka:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>Viz také  
 [Odvození relační struktury datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [Načtení datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Načtení informací o schématu datové sady z XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [Datové sady, datové tabulky a datová zobrazení](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
