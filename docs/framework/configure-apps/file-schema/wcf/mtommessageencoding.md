---
title: '&lt;mtomMessageEncoding&gt;'
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 380aa162d2bb55ac968bdd057a4bb45b2ea6abfe
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45689207"
---
# <a name="ltmtommessageencodinggt"></a>&lt;mtomMessageEncoding&gt;
Určuje kódování a správu verzí zpráv protokolu SOAP zprávy přenosu optimalizace mechanismus (MTOM) na základě zpráv.  
  
 \<system.serviceModel>  
\<vazby >  
\<třídě customBinding >  
\<Vytvoření vazby >  
\<mtomMessageEncoding >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<mtomMessageEncoding   
   maxBufferSize="Integer"  
      maxReadPoolSize="Integer"  
   maxWritePoolSize="Integer"  
   messageVersion="Soap11Addressing1/Soap12Addressing10"  
      writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|Třída maxBufferSize|Celé číslo, které určuje maximální velikost vyrovnávací paměti, kterou lze použít.|  
|maxReadPoolSize|Celé číslo, které určuje, kolik zpráv lze souběžně číst bez přidělení nových čtecích zařízení. Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu. Výchozí hodnota je 64.|  
|maxWritePoolSize|Celé číslo, které určuje, kolik zpráv lze souběžně odesílat bez přidělení nových modulů pro zápis. Větší velikosti fondů byl systém odolnější vůči špičky aktivity za cenu větší pracovní sadu. Výchozí hodnota je 16.|  
|verze messageVersion|Určuje verzi protokolu SOAP zprávy odesílané pomocí vazby. Platné hodnoty jsou<br /><br /> -Soap11Addressing1<br />-Soap12Addressing10<br /><br /> Výchozí hodnota je Soap12Addressing10. Tento atribut je typu <xref:System.ServiceModel.Channels.MessageVersion>.|  
|writeEncoding|Určuje znakovou sadu kódování pro vysílání zpráv z vazby. Platné hodnoty jsou<br /><br /> -UnicodeFffeTextEncoding: Kódování BigEndian kódování Unicode<br />-Utf16TextEncoding: Kódování Unicode<br />-Utf8TextEncoding: kódování 8bitové<br /><br /> Výchozí hodnota je Utf8TextEncoding. Tento atribut je typu <xref:System.Text.Encoding>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<readerQuotas>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou. Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)|Definuje všechny možnosti vázání pro vlastní vazbu.|  
  
## <a name="remarks"></a>Poznámky  
 Kódování je proces transformace zprávu do sekvence bajtů. Dekódování je opačný proces. Windows Communication Foundation (WCF) zahrnuje tři typy kódování zprávy protokolu SOAP: Text, binární soubor a zpráv přenosu optimalizace mechanismus (MTOM).  
  
 `MtomMessageEncoding` Prvek určuje na znak kódování a správu verzí zpráv a další nastavení pro zprávy pomocí kódování zpráv přenosu optimalizace mechanismus (MTOM). MTOM je efektivní technologie pro přenos zpráv WCF binární data. Kodér MTOM se pokusí vytvořit rovnováhu mezi efektivitu a vzájemná funkční spolupráce. Kódování MTOM přenáší většina XML v textové formě, ale optimalizuje velkých bloků binárních dat jako ušetřený přenosem-je, bez převodu na jejich formát kódování base64.  
  
## <a name="example"></a>Příklad  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"  
    maxWritePoolSize="2132"  
    messageVersion="Soap11Addressing10"  
    textEncoding="utf-8" />  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
 [Kódování zpráv](../../../../../docs/framework/configure-apps/file-schema/wcf/message-encoding.md)  
 [Výběr kodéru zprávy](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<třídě customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
