---
title: "Deklarace a odepření přístupu k prostředkům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 00d6a797b8099313c15d075457ee757c1f22f744
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="claims-and-denying-access-to-resources"></a>Deklarace a odepření přístupu k prostředkům
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]podporuje mechanismus ověřování založené na deklaracích identity. A také povolení přístup k prostředkům na základě přítomnosti deklarací identity, systémy často odepřít přístup k prostředkům na základě přítomnosti deklarací identity. Tyto systémy měli zkontrolovat <xref:System.IdentityModel.Policy.AuthorizationContext> pro deklarace identity, jejichž výsledkem je před hledáním deklarace identity, jejichž výsledkem je povolen přístup odepřen přístup.  
  
 Například může systém odepřít přístup k prostředku na každý, kdo má deklarace identity s typem z `Age`, napravo od <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>a hodnota prostředků `Under 21` pouze když tuto identitu má také deklarace identity typu `Name`, napravo od <xref:System.IdentityModel.Claims.Rights.Identity%2A>, a hodnota prostředků `Mallory`. Jinými slovy, systém odepře přístup všem uživatelům, kteří je do 21 let a udělí přístup, pokud je název Mallory. Toto správně implementovat sémantického, je důležité Hledat `Age` nejprve deklarace identity a určit, zda je stáří do 21 let. Jinak, pokud Mallory je v části 21, pak prostředku může mít udělen přístup výhradně na základě těchto `Name` deklarací identity.  
  
## <a name="see-also"></a>Viz také  
 [Správa deklarací a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Deklarace a tokeny](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)