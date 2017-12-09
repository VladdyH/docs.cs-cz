---
title: "Postupy: Instalace a odinstalace služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d52512ef98596e1e3d5f0acb3b1bbc0eebffe867
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-uninstall-services"></a>Postupy: Instalace a odinstalace služeb
Pokud vyvíjíte služby systému Windows s použitím rozhraní .NET Framework, můžete rychle nainstalovat aplikace služby pomocí nástroje příkazového řádku, který volá InstallUtil.exe. Pokud jste vývojář kdo chce verzi služby systému Windows, uživatelé můžou instalovat a odinstalovat jste měli využívají novou technologii. V tématu [nasazení Instalační služby systému Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
> [!WARNING]
>  Pokud chcete odinstalovat službu z počítače, není postupujte podle kroků v tomto článku. Místo toho zjistit balíčky, které program nebo software nainstaloval službu a potom vyberte **přidat nebo odebrat programy** v Ovládacích panelech odinstalujte tohoto programu. Všimněte si, že mnoho služeb jsou nedílnou součástí systému Windows. Pokud je odstraníte, může dojít k nestabilitě systému.  
  
 Chcete-li použít kroky v tomto článku, musíte nejprve přidat instalační program služby k službě systému Windows. V tématu [návod: vytváření Windows aplikace v Návrháři součástí služby](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).  
  
 Projekty služby systému Windows nemůže spustit přímo z vývojovém prostředí sady Visual Studio stisknutím klávesy F5. Je to proto, že před spuštěním projektu, musí být nainstalovaná služba v projektu.  
  
> [!TIP]
>  Můžete spustit **Průzkumníka serveru** a ověřte, že služby byla nainstalována nebo odinstalována. Další informace najdete v tématu Postupy: přístup a inicializaci Průzkumníka databáze Průzkumníka serveru.  
  
### <a name="to-install-your-service-manually"></a>Ruční instalace služby  
  
1.  V systému Windows **spustit** nabídky nebo **spustit** obrazovky, zvolte **Visual Studio** , **nástroje sady Visual Studio**, **vývojáře Příkazový řádek**.  
  
     Zobrazí se příkazový řádek sady Visual Studio.  
  
2.  Přístup k adresáři, kde je umístěn kompilované spustitelný soubor vašeho projektu.  
  
3.  InstallUtil.exe spusťte z příkazového řádku s spustitelný soubor vašeho projektu jako parametr:  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     Pokud používáte příkazového řádku Visual Studia, InstallUtil.exe by měla být na cestě k systému souborů. Pokud ne, přidejte do cesty, nebo použijte plně kvalifikovanou cestu k vyvolání ho. Tento nástroj je nainstalovaný s rozhraním .NET Framework, a jeho cestu `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`. Například pro 32bitovou verzi rozhraní .NET Framework 4 nebo 4.5. *, pokud váš instalační adresář Windows je C:\Windows, cesta je `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`. Pro 64bitové verze rozhraní .NET Framework 4 nebo 4.5. \*, výchozí cesta je `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.  
  
### <a name="to-uninstall-your-service-manually"></a>Chcete-li ručně odinstalovat služby  
  
1.  V systému Windows **spustit** nabídky nebo **spustit** obrazovky, zvolte **Visual Studio**, **nástroje sady Visual Studio**, **vývojáře Příkazový řádek**.  
  
     Zobrazí se příkazový řádek sady Visual Studio.  
  
2.  InstallUtil.exe spusťte z příkazového řádku s výstupem vašeho projektu jako parametr:  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  V některých případech po odstranění je spustitelný soubor pro službu, službu může být v registru. V takovém případě použijte příkaz [sc delete](http://technet.microsoft.com/library/cc742045.aspx) pro odebrání položky pro službu z registru.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikace služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [InstallUtil.exe (instalační nástroj)](../../../docs/framework/tools/installutil-exe-installer-tool.md)