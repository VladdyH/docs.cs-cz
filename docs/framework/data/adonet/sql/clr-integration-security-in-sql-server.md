---
title: "CLR Integration zabezpečení v systému SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: de4f4b1ae5ba252778d9463cba43a9ccb419600a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="clr-integration-security-in-sql-server"></a>CLR Integration zabezpečení v systému SQL Server
Microsoft SQL Server poskytuje integraci součást společné language runtime (CLR) rozhraní .NET Framework. Integrace modulu CLR umožňuje psát uložené procedury, triggery, uživatelem definované typy, uživatelem definované funkce, uživatelem definovaných agregacích a streamování funkce vracející tabulku, pomocí žádný jazyk rozhraní .NET Framework, jako je například Microsoft Visual Basic .NET nebo Microsoft Visual C#.  
  
 Modul CLR podporuje model zabezpečení pro spravovaný kód volat zabezpečení přístupu kódu (CAS). V tomto modelu jsou udělena oprávnění pro sestavení založená na důkaz, kód v metadatech. SQL Server integruje model zabezpečení založený na uživatele systému SQL Server s modelem zabezpečení přístupu kódu modulu CLR.  
  
## <a name="external-resources"></a>Externí zdroje  
 Další informace o integraci modulu CLR s SQL serverem najdete v následujících zdrojích informací.  
  
|Prostředek|Popis|  
|--------------|-----------------|  
|[Zabezpečení přístupu kódu](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03)|Obsahuje témata s popisem certifikační Autority v rozhraní .NET Framework.|  
|[Zabezpečení integrace modulu CLR](http://go.microsoft.com/fwlink/?LinkId=59998)|Popisuje model zabezpečení pro spravovaný kód provádění v systému SQL Server.|  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Scénáře zabezpečení aplikací v systému SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server Common Language Runtime Integration](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)