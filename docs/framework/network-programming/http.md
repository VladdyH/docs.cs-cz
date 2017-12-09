---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 701ff252380ef93dbe3668c8aca73f08a8425d6b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="http"></a>HTTP
Rozhraní .NET Framework poskytuje komplexní podporu pro protokol HTTP, který tvoří většina všechny přenosy z Internetu, se <xref:System.Net.HttpWebRequest> a <xref:System.Net.HttpWebResponse> třídy. Tyto třídy odvozené od <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse>, jsou vráceny ve výchozím nastavení vždy, když statickou metodu <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> zaznamená identifikátor URI začínající "http" nebo "https". Ve většině případů **WebRequest** a **WebResponse** třídy poskytují všechny možnosti, které je potřeba provést žádost, ale pokud budete potřebovat přístup k funkce specifické pro HTTP, které jsou zveřejněné jako vlastnosti, které přiřazení typu Tyto třídy **HttpWebRequest** nebo **HttpWebResponse**.  
  
 **HttpWebRequest** a **HttpWebResponse** zapouzdřují standardní transakce požadavku a odpovědi HTTP a poskytovat přístup k společné hlavičky HTTP. Tyto třídy také podporují většinu funkcí HTTP 1.1, včetně zřetězení příkazů, odesílání a přijímání dat v bloky dat, ověřování, předběžné ověření, šifrování, podpora proxy, se ověřování certifikátu serveru a správu připojení. Vlastní hlavičky a není zajišťováno prostřednictvím vlastnosti můžete ukládat a přistupovat prostřednictvím **hlavičky** vlastnost.  
  
 **HttpWebRequest** je výchozí třídy používané **WebRequest** a není potřeba před můžete předat identifikátor URI pro být zaregistrován **WebRequest.Create** metoda.  
  
 Můžete použít aplikaci držet se přesměrování HTTP automaticky nastavením <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> vlastnost **true** (výchozí). Aplikace bude přesměrovávat požadavky a <xref:System.Net.HttpWebResponse.ResponseUri%2A> vlastnost **HttpWebResponse** bude obsahovat skutečné webového prostředku, který odpověděl na žádost. Pokud nastavíte **AllowAutoRedirect** k **false**, aplikace musí být schopna zpracovávat přesměrování jako chyby protokolu HTTP.  
  
 Aplikace obdrží zachytávání chyb protokolu HTTP <xref:System.Net.WebException> s <xref:System.Net.WebException.Status%2A> nastavena na <xref:System.Net.WebExceptionStatus>. <xref:System.Net.WebException.Response%2A> Vlastnost obsahuje **WebResponse** odeslaných serverem a označuje skutečného došlo k chybě protokolu HTTP.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k Internetu prostřednictvím proxy serveru](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Pomocí protokolů aplikací](../../../docs/framework/network-programming/using-application-protocols.md)  
 [Postupy: přístup k vlastnosti specifické pro protokol HTTP](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)