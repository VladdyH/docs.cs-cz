---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 572a19723583a6bc717a71b3b46040148f29e1cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="msmqtransportbindingelement"></a>MsmqTransportBindingElement
MsmqTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída prvkem MsmqTransportBindingElement má následující vlastnosti:  
  
### <a name="maxpoolsize"></a>MaxPoolSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.  
  
### <a name="queuetransferprotocol"></a>Třída QueueTransferProtocol  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota výčtu, která určuje přenosu kanál komunikace ve frontě, která používá tuto vazbu.  
  
### <a name="useactivedirectory"></a>Třída UseActiveDirectory  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Vrátí logickou hodnotu, která určuje, zda mají být převedeny fronty adresy pomocí služby Active Directory.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>