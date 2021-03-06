---
title: 'Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: 7638c6c9af5394838ac584e4dd9a9ca4cfbf8af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547924"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Postupy: Konfigurace služeb IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF
Můžete nasadit [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace z většina webové servery jsou nakonfigurovány s příslušnou [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typy. Ve výchozím nastavení [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] je nakonfigurována pomocí těchto [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy, ale [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nejsou.  
  
 Toto téma popisuje postup konfigurace [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] a [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] nasazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
  
> [!NOTE]
>  Můžete zkontrolovat *UserAgent* řetězec v registru na určit, zda má systém nainstalováno rozhraní .NET Framework. Podrobnosti a skript, který ověřuje, zda *UserAgent* řetězec zjistit, zda je v systému nainstalována rozhraní .NET Framework, najdete v článku [zjistit, zda rozhraní .NET Framework 3.0 je nainstalována](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a>Upravit nastavení doby platnosti obsahu  
 Má upravit nastavení doby platnosti obsahu na 1 minutu. Následující postup popisuje, jak to provést pomocí [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].  
  
1.  Klikněte na tlačítko **spustit** nabídky, přejděte na příkaz **nástroje pro správu**a klikněte na tlačítko **Správce Internetové informační služby (IIS)**. Můžete také spustit tuto aplikaci z příkazového řádku s "% SystemRoot%\system32\inetsrv\iis.msc".  
  
2.  Rozbalte [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] stromu až naleznete **výchozí web** uzlu.  
  
3.  Klikněte pravým tlačítkem na **výchozí web** a vyberte **vlastnosti** v místní nabídce.  
  
4.  Vyberte **hlavičky protokolu HTTP** kartě a klikněte na možnost "Povolit vypršení platnosti obsahu".  
  
5.  Nastavte obsah vyprší za 1 minutu.  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a>Typy MIME registrace a přípony souborů  
 Je nutné zaregistrovat několik [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy a přípony souborů, aby prohlížeč v systému klienta můžete načíst obslužnou rutinu správné. Je nutné přidat následující typy:  
  
|Rozšíření|Typ MIME|  
|---------------|---------------|  
|manifest|/ manifest aplikace|  
|XAML|aplikace nebo xaml + xml|  
|.Application|Application/x-ms-application|  
|.XBAP|Application/x-ms-xbap|  
|.deploy|application/octet-stream|  
|XPS|aplikace nebo vnd.ms-xpsdocument|  
  
> [!NOTE]
>  Není potřeba zaregistrovat [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy a přípony souborů v systémech klientů. Jsou registrované automaticky při instalaci rozhraní Microsoft .NET Framework.  
  
 Následující ukázka Microsoft Visual Basic Scripting Edition (VBScript) automaticky přidá nezbytné [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typů, který [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]. Chcete-li použít skript, zkopírujte kód do souboru .vbs na vašem serveru. Spusťte skript spuštěný soubor z příkazového řádku nebo dvojitým kliknutím na soubor v [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  Spuštěním tohoto skriptu vícekrát vytváří více [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] mapování položek v [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.  
  
 Po spuštění tohoto skriptu nemusíte vidět další [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy z [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)]. Ale tyto [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy jsou přidané do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze. Následující skript se zobrazí všechny [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] typy, které do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabáze.  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 Uložte skript pod názvem `.vbs` souboru (například `DiscoverIISMimeTypes.vbs`) a potom ho spusťte z příkazového řádku pomocí následujícího příkazu:  
  
 `cscript DiscoverIISMimeTypes.vbs`
