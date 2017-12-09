---
title: "Zpracování událostí datové sady"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 54edefe0-bc38-419b-b486-3d8a0c356f13
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cfe9d9c9f1442d3577772dde1ff33a7807394019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="handling-dataset-events"></a>Zpracování událostí datové sady
<xref:System.Data.DataSet> Objekt poskytuje tři události: <xref:System.ComponentModel.MarshalByValueComponent.Disposed>, <xref:System.Data.DataSet.Initialized>, a <xref:System.Data.DataSet.MergeFailed>.  
  
## <a name="the-mergefailed-event"></a>Událost MergeFailed  
 Nejčastěji používá události `DataSet` objekt `MergeFailed`, která se vyvolá, když schéma `DataSet` slučování objekty jsou v konfliktu. K tomu dojde, pokud zdrojové a cílové <xref:System.Data.DataRow> mají stejnou hodnotu primárního klíče a <xref:System.Data.DataSet.EnforceConstraints%2A> je nastavena na `true`. Například pokud slučování primární klíčové sloupce tabulky identická mezi tabulkami ve dvou `DataSet` objekty, je vyvolána výjimka a `MergeFailed` událost se vyvolá. <xref:System.Data.MergeFailedEventArgs> Byl předán objekt `MergeFailed` událost mít <xref:System.Data.MergeFailedEventArgs.Conflict%2A> vlastnost, která identifikuje konflikt ve schématu mezi těmito dvěma `DataSet` objekty a <xref:System.Data.MergeFailedEventArgs.Table%2A> vlastnost, která identifikuje název tabulky v konfliktu.  
  
 Následující fragment kódu ukazuje, jak přidat obslužné rutiny události pro `MergeFailed` událostí.  
  
```vb  
AddHandler workDS.MergeFailed, New MergeFailedEventHandler( _  
  AddressOf DataSetMergeFailed)  
  
Private Shared Sub DataSetMergeFailed(  _  
  sender As Object,args As MergeFailedEventArgs)  
  Console.WriteLine("Merge failed for table " & args.Table.TableName)  
  Console.WriteLine("Conflict = " & args.Conflict)  
End Sub  
```  
  
```csharp  
workDS.MergeFailed += new MergeFailedEventHandler(DataSetMergeFailed);  
  
private static void DataSetMergeFailed(  
  object sender, MergeFailedEventArgs args)  
{  
  Console.WriteLine("Merge failed for table " + args.Table.TableName);  
  Console.WriteLine("Conflict = " + args.Conflict);  
}  
```  
  
## <a name="the-initialized-event"></a>Inicializovanou událost  
 <xref:System.Data.DataSet.Initialized> Události dojde po `DataSet` konstruktor inicializuje novou instanci třídy `DataSet`.  
  
 <xref:System.Data.DataSet.IsInitialized%2A> Vlastnost vrátí `true` Pokud `DataSet` dokončení inicializace; v opačném případě vrátí `false`. <xref:System.Data.DataSet.BeginInit%2A> Metodu, která začíná inicializace `DataSet`, nastaví <xref:System.Data.DataSet.IsInitialized%2A> k `false`. <xref:System.Data.DataSet.EndInit%2A> Metoda, což ukončí inicializace `DataSet`, nastaví na `true`. Tyto metody jsou používány [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] prostředí návrhu k chybě při inicializaci `DataSet` který se používá jinou součástí. Nebudete používat běžně je ve vašem kódu.  
  
## <a name="the-disposed-event"></a>Uvolněné událostí  
 `DataSet`je odvozený od <xref:System.ComponentModel.MarshalByValueComponent> třídy, která zpřístupňuje jak <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda a <xref:System.ComponentModel.MarshalByValueComponent.Disposed> událostí. <xref:System.ComponentModel.MarshalByValueComponent.Disposed> Událost přidá obslužnou rutinu události pro naslouchání na uvolněné událostí na komponentu. Můžete použít <xref:System.ComponentModel.MarshalByValueComponent.Disposed> události `DataSet` Pokud chcete provést kódu, kdy <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A> metoda je volána. <xref:System.ComponentModel.MarshalByValueComponent.Dispose%2A>uvolní prostředky používané <xref:System.ComponentModel.MarshalByValueComponent>.  
  
> [!NOTE]
>  `DataSet` a `DataTable` objekty dědí <xref:System.ComponentModel.MarshalByValueComponent> a podporovat <xref:System.Runtime.Serialization.ISerializable> rozhraní pro vzdálenou komunikaci. Jedná se o pouze ADO.NET objekty, které se dají používat vzdáleně. Další informace najdete v tématu [vzdálených objektů](http://msdn.microsoft.com/en-us/515686e6-0a8d-42f7-8188-73abede57c58).  
  
 Informace o dalších událostí, které jsou k dispozici při práci se službou `DataSet`, najdete v části [zpracování události DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md) a [zpracování události DataAdapter](../../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Viz také  
 [Datové sady, DataTables a DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Ověřování dat](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 [Načítání a upravovat Data v technologii ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)