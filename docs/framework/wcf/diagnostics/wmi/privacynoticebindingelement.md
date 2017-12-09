---
title: PrivacyNoticeBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0cf110b1-e25b-4d67-986b-10cb04dc4826
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4406253225bd851ca5472de786c30e696a9b4d78
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="privacynoticebindingelement"></a>PrivacyNoticeBindingElement
PrivacyNoticeBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class PrivacyNoticeBindingElement : BindingElement  
{  
  sint32 PrivacyNoticeVersion;  
  string Url;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída PrivacyNoticeBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída PrivacyNoticeBindingElement má následující vlastnosti:  
  
### <a name="privacynoticeversion"></a>PrivacyNoticeVersion  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Verze oznámení o ochraně osobních údajů.  
  
### <a name="url"></a>Adresa URL  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Adresa URL, ve kterém se nachází v oznámení o ochraně osobních údajů.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>