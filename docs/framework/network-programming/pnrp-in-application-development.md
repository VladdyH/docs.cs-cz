---
title: PNRP ve vývoji aplikací
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: b19138c43185f4d31bef4fe67af48f89dc03eba4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180430"
---
# <a name="pnrp-in-application-development"></a>PNRP ve vývoji aplikací
Ve Windows Vista, síťové aplikace můžou k název publikace a funkce řešení prostřednictvím zjednodušené PNRP aplikačního programovacího rozhraní (API).  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementace protokolu Peer Name Resolution Protocol  
 Zjednodušené rozhraní API PNRP nejsou explicitně zadané cloudy registrace názvu a adresy; komponenta PNRP automaticky určuje odpovídající cloudy spojení a adresy, které mají publikovat v rámci cloudy.  
  
 Pro velmi zjednodušené PNRP překlad ve Windows Vista PNRP názvy jsou teď integrovaná v getaddrinfo() – funkce rozhraní Windows Sockets. Pomocí protokolu PNRP přeložit název na adresu IPv6, aplikace můžou využít funkci getaddrinfo() vyřešit name.prnp.net plně kvalifikovaný název domény (FQDN), který název je název partnerského zařízení probíhá řešení. Doména pnrp.net je vyhrazené domény ve Windows Vista k rozlišení názvu PNRP.  
  
 Předávání mezi aplikacemi PeerToPeer zpráv stále zpracovává základní architektury, jako je například kanál PeerChannel a WCF [velkých objemů dat a datových proudů](https://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.PeerToPeer>
