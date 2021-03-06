---
title: Potíže s vlákny při automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, threading issues
- threading issues with UI Automation
ms.assetid: 0ab8d42c-5b8b-481b-b788-2caecc2f0191
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 7d8df325d18c3657d4955fa534d29bb7fdbc595c
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846497"
---
# <a name="ui-automation-threading-issues"></a>Potíže s vlákny při automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Vzhledem ke způsobu [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] používá Windows zprávy, je v konfliktu může dojít, pokud klientská aplikace pokusí o interakci se vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákna. Tyto konflikty mohou vést k velmi nízký výkon nebo dokonce způsobit, že aplikace přestane reagovat.  
  
 Pokud vaše klientská aplikace pro interakci s všechny prvky v klientských počítačích, včetně jeho vlastní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], měli byste si všechny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volá na samostatném vlákně. Jedná se o vyhledání prvky (například pomocí <xref:System.Windows.Automation.TreeWalker> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metoda) a pomocí vzorů ovládacích prvků.  
  
 Je bezpečné, aby [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] volání v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obslužná rutina události, protože obslužná rutina události je volána vždy na non -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákna. Ale při přihlášení k odběru událostí, které mohou pocházet z klientské aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], je třeba volání <xref:System.Windows.Automation.Automation.AddAutomationEventHandler%2A>, nebo související metody na non -[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] vlákna. Odebrání obslužných rutin událostí ve stejném vlákně.
