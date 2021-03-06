---
title: Analytické trasování s ETW
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 210418b8a8765a1fc59658e9df57c92ce087c95f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809261"
---
# <a name="analytic-tracing-with-etw"></a>Analytické trasování s ETW
Analytické trasování Windows Communication Foundation (WCF) nabízí způsob, jak zachytit diagnostické informace během provádění služby WCF. Události analytické trasování WCF jsou vydávány v klíčové body v zásobníku WCF umožňuje řešení potíží s služby WCF v produkčním prostředí. Analytické trasování pro služby WCF má minimální dopad na výkon produktu serveru, který je hostitelem [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] služeb WCF, jak tyto události jsou velmi efektivně vygenerované relaci události trasování událostí pro Windows (ETW).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled analytického trasování](../../../../../docs/framework/wcf/diagnostics/etw/analytic-tracing-overview.md)  
 Popisuje, jak funguje analytické trasování WCF [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)].  
  
 [Dynamické povolování analytického sledování](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md)  
 Popisuje, jak povolit nebo zakázat trasování dynamicky pomocí trasování událostí pro Windows.  
  
 [Konfigurace trasování toku zpráv](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)  
 Popisuje postup konfigurace trasování toku zpráv.  
  
 [Události analytického trasování – přehled](../../../../../docs/framework/wcf/diagnostics/etw/analytic-trace-event-reference.md)  
 Příklad ID událostí s úrovní událostí, zprávy o událostech a klíčová slova.  
  
## <a name="see-also"></a>Viz také  
 [Služby WCF a Trasování událostí pro Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)  
 [Sledování událostí v Trasování událostí ve Windows](../../../../../docs/framework/windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
