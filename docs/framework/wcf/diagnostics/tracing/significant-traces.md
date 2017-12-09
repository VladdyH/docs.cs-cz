---
title: "Významná trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40a1770e-3b09-4142-b0dd-f9ef73642074
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 95b4794848927b9319ddb07d75461f5d5e71e1f5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="significant-traces"></a>Významná trasování
Toto téma uvádí některé z hlavních trasování vysílaných [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="significant-traces"></a>Významná trasování  
  
|trasování|Popis|  
|-----------|-----------------|  
|Zprávy protokolu trasování|Trasování je vygenerované při [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zaznamenána podle protokolování zpráv funkci, kdy `System.ServiceModel.MessageLogging` zdroj trasování je povoleno. Kliknutím na toto trasování zobrazí zprávu. Existují čtyři body konfigurovat protokolování pro zprávu: `ServiceLevelSendRequest`, `TransportSend`, `TransportReceive`, `ServiceLevelReceiveRequest`, také označené atributem zdroj zprávy v protokolu trasování zpráv.|  
|Přijatá zpráva trasování|Trasování je vygenerované při [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] je přijatá zpráva, pokud `System.ServiceModel` zdroj trasování je povoleno na podrobné úrovni nebo informace. Trasování je nutné zobrazíte šipka korelace zprávy v zobrazení grafu aktivity.|  
|Zpráva byla odeslána trasování|Trasování je vygenerované při [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] je odeslána zpráva, pokud `System.ServiceModel` zdroj trasování je povoleno na podrobné úrovni nebo informace. Trasování je nutné zobrazíte šipka korelace zprávy v zobrazení grafu aktivity.|  
|Získat prvek ChannelEndpointElement|Trasování jsou vydávány v konstrukce kanálu, na úrovni informace. Nabízí že popis koncového bodu, klient je rozhovoru (vzdálené adresy, vazby, název kontraktu).|  
|Získat prvek ServiceElement|Trasování jsou vydávány v hostitele služby konstrukce, na úrovni informace. Poskytuje popis kontrakt služby a vazby.|  
|Vytvoření připojení SocketConnection|Trasování jsou vydávány v první akce proces prováděných klientem a přijímání bajtů aktivity ve službě. Poskytuje místní a vzdálené IP adresy. Na úrovni informace jsou vydávány ho.|