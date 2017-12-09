---
title: Migrace a interoperabilita
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AutoGeneratedOrientationPage
helpviewer_keywords:
- Windows Presentation Foundation [WPF], interoperability
- WPF [WPF], migration
- Windows Forms controls [WPF interoperability]
- controls [WPF interoperability]
- Windows Presentation Foundation [WPF], migration
- interoperability [WPF]
- WPF [WPF], interoperability
- migration [WPF]
ms.assetid: d655de05-bf63-4814-bc64-6b3be01c70a2
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d469d5f53b97ec05e8714cff1ea663dda827a1a
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="migration-and-interoperability"></a>Migrace a interoperabilita
Tato stránka obsahuje odkazy na dokumenty, které popisují, jak implementovat vzájemná spolupráce mezi [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací a dalších typů [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [WPF a vzájemná spolupráce Windows Forms](../../../../docs/framework/wpf/advanced/wpf-and-windows-forms-interoperation.md)  
 [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [WPF a vzájemná spolupráce procesu Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)  
  
## <a name="reference"></a>Odkaz  
  
|Termín|Definice|  
|----------|----------------|  
|<xref:System.Windows.Forms.Integration.WindowsFormsHost>|Element, který můžete použít k hostiteli [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek jako prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.|  
|<xref:System.Windows.Forms.Integration.ElementHost>|A [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který můžete použít k hostiteli [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ovládacího prvku.|  
|<xref:System.Windows.Interop.HwndSource>|Hostitelé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oblast v rámci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace.|  
|<xref:System.Windows.Interop.HwndHost>|Základní třída pro <xref:System.Windows.Forms.Integration.WindowsFormsHost>, definuje některé základní funkce, které všechny na základě HWND technologie použijte, pokud hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Podtřída to k hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.|  
|<xref:System.Windows.Interop.BrowserInteropHelper>|Pomocná třída pro podmínky prohlížeče prostředí pro vytváření sestav [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, která je hostovaná v prohlížeči.|  
  
## <a name="related-sections"></a>Související oddíly