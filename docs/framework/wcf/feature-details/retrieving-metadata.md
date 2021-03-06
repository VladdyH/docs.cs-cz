---
title: Načítání metadat
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 1f0665b4f0fb91b102ef1d5b75a5433992f5a6e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493599"
---
# <a name="retrieving-metadata"></a>Načítání metadat
Načtení metadat je proces požaduje a načítání metadat z koncového bodu metadat, jako je koncový bod metadat WS-MetadataExchange (MEX) nebo koncový bod HTTP nebo získat metadata.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Načítání metadat z příkazového řádku pomocí Svcutil.exe  
 Můžete načíst metadata služby pomocí protokolu WS-MetadataExchange nebo protokolu HTTP nebo získat požadavků pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj a předávání `/target:metadata` přepínač a adresu. Svcutil.exe metadata na zadané adrese stáhne a uloží soubor na disk. Používá svcutil.exe <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance interně a načte z konfigurace <xref:System.ServiceModel.Description.IMetadataExchange> konfigurace koncového bodu, jejíž název odpovídá schéma adresy předaný Svcutil.exe jako vstup.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Načítání metadat programově pomocí Třída MetadataExchangeClient  
 Windows Communication Foundation (WCF) můžete načíst metadata služby pomocí standardizovaných protokolů, jako je WS-MetadataExchange a požadavky HTTP/GET. Obě tyto protokoly jsou podporovány <xref:System.ServiceModel.Description.MetadataExchangeClient> typu. Načtení služby metadat pomocí <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> typ poskytnutím adresa pro koncový bod metadat a volitelné vazby. Vazby používané <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance může být jedna z vazeb výchozí z <xref:System.ServiceModel.Description.MetadataExchangeBindings> statická třída, vazbu uživatelem zadané nebo vazbu načtené ze konfigurace koncového bodu pro `IMetadataExchange` kontrakt. <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Můžete také vyřešit odkazy na základní adresy URL metadat pomocí <xref:System.Net.HttpWebRequest> typu.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instance je vázaný na jednu <xref:System.ServiceModel.ChannelFactory> instance. Můžete změnit nebo nahradit <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> virtuální metoda. Podobně můžete změnit nebo nahradit <xref:System.Net.HttpWebRequest> instanci použitou <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> provádět požadavky HTTP/GET přepsáním <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> virtuální metoda.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Stažení dokumentů metadat pomocí nástroje Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Demonstruje použití Svcutil.exe stažení dokumentů metadat.  
  
 [Postupy: Použití MetadataResolver k dynamickému získání metadat vazby](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Ukazuje, jak používat <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> k získání metadat vazby dynamicky za běhu.  
  
 [Postupy: Načítání metadat pomocí MetadataExchangeClient](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Ukazuje, jak používat <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> třídy ke stažení souborů metadat do <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objekt, který obsahuje <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> objekty pro zápis do souborů nebo pro jiné účely.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>
