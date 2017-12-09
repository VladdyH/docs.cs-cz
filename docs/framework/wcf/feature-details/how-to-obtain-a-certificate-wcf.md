---
title: "Postupy: získání certifikátu (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1b7ab4ed91487965ac8b0d78a9a44818cfee9eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Postupy: získání certifikátu (WCF)
K používání některé z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkce, které používají certifikáty X.509, je právě nejprve získat certifikáty.  
  
### <a name="to-obtain-an-x509-certificate"></a>K získání certifikátu X.509  
  
1.  Vyberte jednu z následujících možností:  
  
    -   Koupit certifikát od certifikační autority, jako je například VeriSign, Inc.  
  
    -   Nastavení certifikátu služby a mít podepsání certifikátů certifikační autority. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, Windows 2000 Server Datacenter a systém Windows 2000 Datacenter zahrnují certifikační služby, které podporují infrastruktury veřejných klíčů (PKI). V systému Windows Server 2008, použijte [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) rolí ke správě certifikační autority.  
  
    -   Nastavení certifikátu služby a provést není mít certifikáty podepsané.  
  
    > [!NOTE]
    >  V obou případech můžete využít, příjemce žádosti SOAP, který obsahuje certifikát X.509 musí důvěřovat certifikátu X.509. To znamená, že certifikát X.509 nebo vystavitele v řetězu certifikátů je v úložišti certifikátů důvěryhodných osob a zda není v úložišti nedůvěryhodné certifikáty certifikátu X.509.  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: vytváření dočasných certifikátů pro použití při vývoji](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)