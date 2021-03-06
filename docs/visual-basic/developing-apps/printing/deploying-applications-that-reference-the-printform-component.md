---
title: Nasazení aplikací odkazujících na součást PrintForm (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
ms.openlocfilehash: 6384ad6e3bf0520362267eddc8f7bbb05b37f283
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787643"
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Nasazení aplikací odkazujících na součást PrintForm (Visual Basic)
Pokud chcete nasadit aplikaci, která odkazuje <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu, komponenty musí být nainstalován v cílovém počítači.  
  
 Ovládací prvky PowerPack již nejsou zahrnuty v sadě Visual Studio, ale můžete stáhnout z [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Jako předpoklad instalace PrintForm  
 K úspěšnému nasazení aplikace, je nutné nasadit také všechny součásti, které se příslušná aplikace odkazuje. Proces instalace požadovaných součástí se označuje jako *spuštění*.  
  
 Když <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> ve svém vývojovém počítači je nainstalována součást, balíček zaváděcího nástroje Microsoft Visual Basic Power Pack se přidá do adresáře zaváděcí nástroj Visual Studio. Tento balíček bude k dispozici, pokud dodržíte postupy pro přidání požadavky pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo nasazení Instalační služby systému Windows.  
  
 Ve výchozím nastavení se nasazují se spustil součásti ze stejného umístění jako instalační balíček. Alternativně můžete nasadit komponenty z adresy URL nebo sdíleného umístění, ze kterého uživatelé si je stáhnout podle potřeby.  
  
> [!NOTE]
>  K instalaci součásti se spustil, uživatel může být nutné oprávnění správce nebo podobné uživatele v počítači. Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikací, to znamená, že uživatel bude potřebovat oprávnění správce k instalaci aplikace bez ohledu na úroveň zabezpečení, která je určená aplikací. Po nainstalování aplikace uživatel můžete spustit aplikaci bez oprávnění správce.  
  
 Během instalace, budou uživatelé vyzváni k instalaci <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenty, pokud není k dispozici na cílovém počítači.  
  
 Jako alternativu k spuštění, můžete předem nasadit <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponentu pomocí systém distribuce elektronické softwaru jako je Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Instalace předpokladů s aplikací ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)
