---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 49f030c05f02280d483ac2a836cbe75716b7b5cc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185051"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ConnectionOrientedTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ConnectionOrientedTransportBindingElement má následující vlastnosti:  
  
### <a name="channelinitializationtimeout"></a>třídě channelInitializationTimeout  
 Datový typ: datum a čas  
  
 Přístup k typu: jen pro čtení  
  
 Časový interval, který určuje, jak dlouho inicializace kanálu má ještě před vypršením časového limitu.  
  
### <a name="connectionbuffersize"></a>connectionBufferSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Velikost vyrovnávací paměti použité k přenosu bloku serializovaných zpráv od klienta nebo služby.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.  
  
### <a name="maxbuffersize"></a>Třída maxBufferSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost vyrovnávací paměti pro použití.  
  
### <a name="maxoutputdelay"></a>maxOutputDelay  
 Datový typ: datum a čas  
  
 Přístup k typu: jen pro čtení  
  
 Maximální interval času, který blok zprávy, nebo celá zpráva může zůstat posláním ve vyrovnávací paměti teprve pak ji bude odeslána.  
  
### <a name="maxpendingaccepts"></a>maxPendingAccepts  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet nevyřízených asynchronních akceptovaných vláken, které jsou k dispozici pro zpracování příchozích připojení ve službě.  
  
### <a name="maxpendingconnections"></a>maxPendingConnections  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet nevyřízených připojení.  
  
### <a name="transfermode"></a>režim přenosu  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány připojením řízenou přepravou.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
