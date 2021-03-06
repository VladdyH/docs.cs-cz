---
title: Přehled správy aplikací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application management [WPF]
ms.assetid: 32b1c054-5aca-423b-b4b5-ed8dc4dc637d
ms.openlocfilehash: ba8d07a26b7e6abc511e5b24db26162b46a2b0a1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042254"
---
# <a name="application-management-overview"></a>Přehled správy aplikací
Všechny aplikace mají tendenci sdílejí společnou sadu funkcí, které se vztahuje na aplikace implementaci a správu. Toto téma obsahuje přehled funkcí v <xref:System.Windows.Application> třídy pro vytváření a správu aplikací.  
   
  
## <a name="the-application-class"></a>Třída aplikace  
 V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], běžné funkce s rozsahem aplikace, je zapouzdřena v <xref:System.Windows.Application> třídy. <xref:System.Windows.Application> Třída zahrnuje následující funkce:  
  
-   Sledování a interakci s dobu životnosti aplikace.  
  
-   Načítání a zpracování parametrů příkazového řádku.  
  
-   Detekce a reakce na neošetřených výjimek.  
  
-   Sdílení vlastností pro rozsah aplikace a prostředky.  
  
-   Správa systému windows v samostatné aplikace.  
  
-   Sledování a správu navigace.  
  
<a name="The_Application_Class"></a>   
## <a name="how-to-perform-common-tasks-using-the-application-class"></a>Jak provádět běžné úlohy pomocí třídy aplikace  
 Pokud si nejste zájem o všechny podrobnosti o <xref:System.Windows.Application> třídy, v následující tabulce jsou uvedeny některé běžné úlohy pro <xref:System.Windows.Application> a způsobu jejich provedení. Zobrazení souvisejících rozhraní API a témata, můžete najít další informace a ukázky kódu.  
  
|Úloha|Přístup|  
|----------|--------------|  
|Získejte objekt, který představuje aktuální aplikace|Použití <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> vlastnost.|  
|Přidání úvodní obrazovky do aplikace|Zobrazit [přidání úvodní obrazovky do aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).|  
|Spuštění aplikace|Použití <xref:System.Windows.Application.Run%2A?displayProperty=nameWithType> metody.|  
|Zastavit aplikaci|Použití <xref:System.Windows.Application.Shutdown%2A> metodu <xref:System.Windows.Application.Current%2A?displayProperty=nameWithType> objektu.|  
|Získat argumenty z příkazového řádku|Zpracování <xref:System.Windows.Application.Startup?displayProperty=nameWithType> událostí a použití <xref:System.Windows.StartupEventArgs.Args%2A?displayProperty=nameWithType> vlastnost. Příklad najdete v tématu <xref:System.Windows.Application.Startup?displayProperty=nameWithType> událostí.|  
|Získání a nastavení ukončovací kód aplikace|Nastavit <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A?displayProperty=nameWithType> vlastnost <xref:System.Windows.Application.Exit?displayProperty=nameWithType> obslužná rutina události nebo volání <xref:System.Windows.Application.Shutdown%2A> a předáte v celé číslo.|  
|Rozpoznání hrozeb a reakce na neošetřené výjimky|Zpracování <xref:System.Windows.Application.DispatcherUnhandledException> událostí.|  
|Získání a nastavení oboru aplikace prostředků|Použití <xref:System.Windows.Application.Resources%2A?displayProperty=nameWithType> vlastnost.|  
|Použití slovníku zdrojů rozsahu aplikace|Zobrazit [použití slovníku zdrojů rozsahu aplikace](../../../../docs/framework/wpf/app-development/how-to-use-an-application-scope-resource-dictionary.md).|  
|GET a set vlastnosti pro obor aplikace|Použití <xref:System.Windows.Application.Properties%2A?displayProperty=nameWithType> vlastnost.|  
|Získání a uložit stav aplikace|Zobrazit [zachování a obnovení vlastností v rozsahu aplikace mezi jednotlivými relacemi aplikace](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).|  
|Správa souborů dat bez kódu, včetně souborů prostředků, soubory obsahu a souborů lokality původu.|Zobrazit [prostředek aplikace WPF, obsah a datové soubory](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).|  
|Správa systému windows v samostatné aplikace|Zobrazit [přehled WPF Windows](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md).|  
|Sledování a správa navigace|Zobrazit [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md).|  
  
<a name="The_Application_Definition"></a>   
## <a name="the-application-definition"></a>Definice aplikace  
 Využívání funkce <xref:System.Windows.Application> třídy, je nutné implementovat definici aplikace. A [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definice aplikace je třída, která je odvozena z <xref:System.Windows.Application> a má nakonfigurovanou speciální [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] nastavení.  
  
### <a name="implementing-an-application-definition"></a>Implementace definice aplikace  
 Typické [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] definice aplikace je implementováno pomocí značek a kódu. To umožňuje používat značky a deklarativně nastavte vlastnosti aplikace, prostředky a zaregistrujte události, při zpracování událostí a implementaci chování specifické pro aplikaci v modelu code-behind.  
  
 Následující příklad ukazuje, jak implementovat definici aplikace pomocí značek a kódu:  
  
 [!code-xaml[ApplicationSnippets#ApplicationXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml#applicationxaml)]  
  
 [!code-csharp[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSnippets/CSharp/App.xaml.cs#applicationcodebehind)]
 [!code-vb[ApplicationSnippets#ApplicationCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSnippets/visualbasic/application.xaml.vb#applicationcodebehind)]  
  
 Povolit souboru označení a použití modelu code-behind soubor spolupráce, následující potřeba:  
  
-   V kódu `Application` musí obsahovat element `x:Class` atribut. Když je aplikace sestavená, existenci `x:Class` ve značkách soubor způsobí, že [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] k vytvoření `partial` třídu odvozenou od <xref:System.Windows.Application> a má název, který je určen `x:Class` atribut. To vyžaduje přidání [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] deklarace oboru názvů pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] schématu ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ).  
  
-   V modelu code-behind, musí být třída `partial` třídy se stejným názvem, která je zadána `x:Class` atribut v kódu a musí být odvozen od <xref:System.Windows.Application>. To umožňuje použití modelu code-behind souboru má být spojen s `partial` třídu, která se vygeneruje pro označovacího souboru, když je aplikace sestavená (viz [sestavení aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)).  
  
> [!NOTE]
>  Při vytváření nového projektu aplikace WPF nebo aplikace WPF pro prohlížeč projektu pomocí [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], definice aplikace je zahrnutá ve výchozím nastavení a je definován pomocí značek a kódu.  
  
 Tento kód je minimum, které je potřeba implementovat definici aplikace. Však další [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] konfiguraci je potřeba provést k definici aplikace před sestavovat a spouštět aplikace.  
  
### <a name="configuring-the-application-definition-for-msbuild"></a>Konfigurace definice aplikace pro MSBuild  
 Samostatné aplikace a [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] vyžadovat provedení určité úrovně infrastruktury před spuštěním. Nejdůležitější součást této infrastruktury je vstupním bodem. Při spuštění aplikace uživatelem operační systém zavolá vstupní bod, který je dobře známé funkce pro spouštění aplikací.  
  
 Tradičně vývojáři potřebovali pro zápis některých nebo všech tento kód sami, v závislosti na technologie. Ale [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] generuje tento kód za vás, pokud References souboru definice aplikace je nakonfigurovaná jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition` položky, jak je znázorněno v následujícím [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] souboru projektu:  
  
```xml  
<Project   
  DefaultTargets="Build"  
                        xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  ...  
  <ApplicationDefinition Include="App.xaml" />  
  <Compile Include="App.xaml.cs" />  
  ...  
</Project>  
```  
  
 Protože soubor kódu obsahuje kód, je označen jako [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Compile` položky, jako je normální.  
  
 Používání těchto [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] způsobí, že konfigurace, které soubory značky a modelu code-behind definici aplikace [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] pro generování kódu, jako je následující:  
  
 [!code-csharp[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode1)]
 [!code-vb[AppDefAugSnippets#AppDefAugCODE1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode1)]  
[!code-csharp[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppDefAugSnippets/CSharp/App.cs#appdefaugcode2)]
[!code-vb[AppDefAugSnippets#AppDefAugCODE2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppDefAugSnippets/VisualBasic/App.vb#appdefaugcode2)]  
  
 Výsledný kód argumentech definice aplikace s kódem další infrastrukturu, která zahrnuje metodu vstupního bodu `Main`. <xref:System.STAThreadAttribute> Atributu se použije pro `Main` metoda, která označuje, že hlavní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace je vlákna STA, která je potřebná pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací. Při volání `Main` vytvoří novou instanci třídy `App` před voláním `InitializeComponent` metodu registrace událostí a nastavte vlastnosti, které jsou implementovány v kódu. Protože `InitializeComponent` se vygeneruje, není nutné explicitně volat `InitializeComponent` z definice aplikace stejným způsobem jako <xref:System.Windows.Controls.Page> a <xref:System.Windows.Window> implementace. Nakonec <xref:System.Windows.Application.Run%2A> metoda je volána ke spuštění aplikace.  
  
<a name="Getting_the_Current_Application"></a>   
## <a name="getting-the-current-application"></a>Získávání aktuální aplikace  
 Protože funkce <xref:System.Windows.Application> třídy jsou sdíleny napříč aplikace, může existovat pouze jedna instance <xref:System.Windows.Application> třídy za <xref:System.AppDomain>. Pokud to chcete vynutit <xref:System.Windows.Application> třídy je implementován jako třída singleton (naleznete v tématu [implementace jednotlivý prvek v jazyce C#](https://go.microsoft.com/fwlink/?LinkId=100567)), vytvoří jednu instanci sebe sama a poskytuje sdílený přístup přes `static` <xref:System.Windows.Application.Current%2A> Vlastnost.  
  
 Následující kód ukazuje, jak získat odkaz na <xref:System.Windows.Application> pro aktuální objekt <xref:System.AppDomain>.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getcurrentappcode)]  
  
 <xref:System.Windows.Application.Current%2A> Vrátí odkaz na instanci <xref:System.Windows.Application> třídy. Pokud chcete odkaz na vaši <xref:System.Windows.Application> odvozené třídy musí přetypujte hodnotu <xref:System.Windows.Application.Current%2A> vlastnost, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/MainWindow.xaml.cs#getstcurrentappcode)]
 [!code-vb[ApplicationManagementOverviewSnippets#GetSTCurrentAppCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/VisualBasic/MainWindow.xaml.vb#getstcurrentappcode)]  
  
 Můžete zkontrolovat hodnoty <xref:System.Windows.Application.Current%2A> kdykoli během životnosti <xref:System.Windows.Application> objektu. Nicméně byste měli být opatrní. Po <xref:System.Windows.Application> je vytvořena instance třídy, je období, během které stavu <xref:System.Windows.Application> objektu je nekonzistentní. Během tohoto období <xref:System.Windows.Application> je provádění různých úloh inicializace, které vyžaduje váš kód pro spuštění, včetně vytváření infrastruktury aplikací, nastavení vlastností a registrací událostí. Pokud se pokusíte použít <xref:System.Windows.Application> objektu během tohoto období se váš kód může mít neočekávané výsledky, zejména v případě, že závisí na různých <xref:System.Windows.Application> vlastnosti nastavena.  
  
 Když <xref:System.Windows.Application> dokončí svoji inicializaci svého životního cyklu skutečně začíná.  
  
<a name="Application_Lifetime"></a>   
## <a name="application-lifetime"></a>Doba života aplikace  
 Životnost [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace je označen několika událostem, které jsou generovány <xref:System.Windows.Application> dali vám vědět, kdy byla spuštěna aplikace, má se aktivovat a deaktivovat a vypnul.  
  
  
<a name="Splash_Screen"></a>   
### <a name="splash-screen"></a>Úvodní obrazovka  
 Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], zadáte image, který se má použít v okně spuštění nebo *úvodní obrazovka*. <xref:System.Windows.SplashScreen> Třída usnadňuje zobrazení úvodní okno při načítání vaší aplikace. <xref:System.Windows.SplashScreen> Okno se vytvoří a zobrazí před <xref:System.Windows.Application.Run%2A> je volána. Další informace najdete v tématu [dobu spuštění aplikace](../../../../docs/framework/wpf/advanced/application-startup-time.md) a [přidání úvodní obrazovky do aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-add-a-splash-screen-to-a-wpf-application.md).  
  
<a name="Starting_an_Application"></a>   
### <a name="starting-an-application"></a>Spuštění aplikace  
 Po <xref:System.Windows.Application.Run%2A> nazývá a byla inicializována aplikace, je připraven ke spuštění aplikace. Aktuálně jsou označeny při <xref:System.Windows.Application.Startup> událost se vyvolá:  
  
 [!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind1)]
 [!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind1)]  
[!code-csharp[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#startupcodebehind2)]
[!code-vb[ApplicationStartupSnippets#StartupCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#startupcodebehind2)]  
  
 V tomto okamžiku v životnosti aplikace, je nejčastěji používané krokem je zobrazíte [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  
  
<a name="Showing_a_User_Interface"></a>   
### <a name="showing-a-user-interface"></a>Zobrazení uživatelského rozhraní  
 Většina aplikací Windows samostatné otevřete <xref:System.Windows.Window> když začnou systémem. <xref:System.Windows.Application.Startup> Obslužná rutina události je jedno místo, ze které můžete dělat to, jak je ukázáno v následujícím kódu.  
  
 [!code-xaml[AppShowWindowHardSnippets#StartupEventMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml#startupeventmarkup)]  
  
 [!code-csharp[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AppShowWindowHardSnippets/CSharp/App.xaml.cs#startupeventcodebehind)]
 [!code-vb[AppShowWindowHardSnippets#StartupEventCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AppShowWindowHardSnippets/VisualBasic/Application.xaml.vb#startupeventcodebehind)]  
  
> [!NOTE]
>  První <xref:System.Windows.Window> má být vytvořena v samostatné aplikaci, bude ve výchozím nastavení hlavního okna aplikace. To <xref:System.Windows.Window> objekt odkazují <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> vlastnost. Hodnota <xref:System.Windows.Application.MainWindow%2A> vlastnost lze změnit prostřednictvím kódu programu, pokud jiné okno než první instance <xref:System.Windows.Window> by měl být hlavní okno.  
  
 Když [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] první se spustí, ji budou pravděpodobně přejděte na <xref:System.Windows.Controls.Page>. To je ukázáno v následujícím kódu.  
  
 [!code-xaml[XBAPAppStartupSnippets#StartupXBAPMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml#startupxbapmarkup)]  
  
 [!code-csharp[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppStartupSnippets/CSharp/App.xaml.cs#startupxbapcodebehind)]
 [!code-vb[XBAPAppStartupSnippets#StartupXBAPCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppStartupSnippets/VisualBasic/Application.xaml.vb#startupxbapcodebehind)]  
  
 Pokud zpracováváte <xref:System.Windows.Application.Startup> pouze otevřít <xref:System.Windows.Window> nebo přejděte na <xref:System.Windows.Controls.Page>, můžete nastavit `StartupUri` atribut místo v kódu.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Application.StartupUri%2A> ze samostatné aplikace otevřete <xref:System.Windows.Window>.  
  
 [!code-xaml[ApplicationManagementOverviewSnippets#OverviewStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationManagementOverviewSnippets/CSharp/App.xaml#overviewstartupurimarkup)]  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Application.StartupUri%2A> ze [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] přejít na <xref:System.Windows.Controls.Page>.  
  
 [!code-xaml[PageSnippets#XBAPStartupUriMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PageSnippets/CSharp/App.xaml#xbapstartupurimarkup)]  
  
 Tento kód má stejný účinek jako předchozí kód pro otevření okna.  
  
> [!NOTE]
>  Další informace v navigačním panelu najdete v tématu [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
 Bude potřeba zpracovat <xref:System.Windows.Application.Startup> událostí otevřete <xref:System.Windows.Window> Pokud potřebujete k vytvoření instance pomocí jiného než výchozího konstruktoru, nebo je potřeba nastavit jeho vlastnosti nebo přihlášení k odběru jeho událostí před zobrazením jej nebo potřebujete zpracovávat jakékoli argumenty příkazového řádku, který byly zadány při aplikace se spustila.  
  
<a name="Processing_Command_Line_Arguments"></a>   
### <a name="processing-command-line-arguments"></a>Zpracování argumentů příkazového řádku  
 Ve Windows samostatné aplikace můžete spustit z příkazového řádku nebo plochy. V obou případech můžete předávat argumenty příkazového řádku k aplikaci. Následující příklad ukazuje aplikace, který je spuštěn s jedním argumentem příkazového řádku, "/ StartMinimized":  
  
 `wpfapplication.exe /StartMinimized`  
  
 Během inicializace aplikace [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] načte argumenty příkazového řádku z operačního systému a předává je do <xref:System.Windows.Application.Startup> obslužnou rutinu události prostřednictvím <xref:System.Windows.StartupEventArgs.Args%2A> vlastnost <xref:System.Windows.StartupEventArgs> parametru. Můžete načíst a ukládat pomocí kódu podobně jako následující argumenty příkazového řádku.  
  
 [!code-xaml[ApplicationStartupSnippets#HandleStartupXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml#handlestartupxaml)]  
  
 [!code-csharp[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationStartupSnippets/CSharp/App.xaml.cs#handlestartupcodebehind)]
 [!code-vb[ApplicationStartupSnippets#HandleStartupCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationStartupSnippets/visualbasic/application.xaml.vb#handlestartupcodebehind)]  
  
 Kód obslužné rutiny <xref:System.Windows.Application.Startup> ke kontrole, jestli **/StartMinimized** byl zadán argument příkazového řádku; Pokud ano, otevře se hlavní okno s <xref:System.Windows.WindowState> z <xref:System.Windows.WindowState.Minimized>. Všimněte si, že vzhledem k tomu, <xref:System.Windows.Window.WindowState%2A> musí být nastavena vlastnost prostřednictvím kódu programu, hlavní <xref:System.Windows.Window> musí být otevřený explicitně v kódu.  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] Nelze načíst a zpracovat argumenty příkazového řádku, protože neovlivňuje pomocí [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] nasazení (viz [nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)). Můžete však načíst a zpracovat parametrů řetězce dotazu z adresy URL, které se používají k jejich spuštění.  
  
<a name="Application_Activation_and_Deactivation"></a>   
### <a name="application-activation-and-deactivation"></a>Aplikace aktivace a deaktivace  
 Windows umožňuje uživatelům přepínat mezi aplikacemi. Nejběžnější způsob je pomocí kombinace kláves ALT + TAB. Aplikace lze přepnout pouze na, pokud má viditelné <xref:System.Windows.Window> , který může uživatel vybrat. Aktuálně vybraný <xref:System.Windows.Window> je *aktivní okno* (označované také jako *okno v popředí*) a je <xref:System.Windows.Window> , který přijímá vstup uživatele. Aplikace s aktivní okno *aktivní aplikace* (nebo *popředí aplikace*). Aplikace se stane aktivní aplikaci za následujících okolností:  
  
-   Spuštění a ukazuje <xref:System.Windows.Window>.  
  
-   Uživatel přepíná z jiné aplikace tak, že vyberete <xref:System.Windows.Window> v aplikaci.  
  
 Můžete rozpoznat, kdy se aplikace stane aktivním pomocí manipulace <xref:System.Windows.Application.Activated?displayProperty=nameWithType> událostí.  
  
 Aplikace se může stát, neaktivní v následujících případech:  
  
-   Uživatel přepne na jiná aplikace než je aktuální.  
  
-   Při ukončení aplikace.  
  
 Můžete rozpoznat, kdy se změní na neaktivní aplikace pomocí manipulace <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> událostí.  
  
 Následující kód ukazuje, jak naložit <xref:System.Windows.Application.Activated> a <xref:System.Windows.Application.Deactivated> události a určit, zda je aplikace aktivní.  
  
 [!code-xaml[ApplicationActivationSnippets#DetectActivationStateXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml#detectactivationstatexaml)]  
  
 [!code-csharp[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationActivationSnippets/CSharp/App.xaml.cs#detectactivationstatecodebehind)]
 [!code-vb[ApplicationActivationSnippets#DetectActivationStateCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationActivationSnippets/visualbasic/application.xaml.vb#detectactivationstatecodebehind)]  
  
 A <xref:System.Windows.Window> můžete také aktivovat a deaktivovat. Zobrazit <xref:System.Windows.Window.Activated?displayProperty=nameWithType> a <xref:System.Windows.Window.Deactivated?displayProperty=nameWithType> pro další informace.  
  
> [!NOTE]
>  Ani <xref:System.Windows.Application.Activated?displayProperty=nameWithType> ani <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> se vyvolá pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Application_Shutdown"></a>   
### <a name="application-shutdown"></a>Ukončení aplikace  
 Dobu životnosti aplikace končí, když je vypnutý, kterému může dojít z následujících důvodů:  
  
-   Uživatel zavře každý <xref:System.Windows.Window>.  
  
-   Uživatel zavře hlavní <xref:System.Windows.Window>.  
  
-   Uživatel ukončí relaci Windows odhlášení nebo vypnutí.  
  
-   Byla splněna podmínku specifické pro aplikaci.  
  
 Vám pomohou při správě ukončení aplikace <xref:System.Windows.Application> poskytuje <xref:System.Windows.Application.Shutdown%2A> metody <xref:System.Windows.Application.ShutdownMode%2A> vlastnost a <xref:System.Windows.Application.SessionEnding> a <xref:System.Windows.Application.Exit> události.  
  
> [!NOTE]
>  <xref:System.Windows.Application.Shutdown%2A> lze volat pouze z aplikace, které mají <xref:System.Security.Permissions.UIPermission>. Samostatné [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace vždy mají toto oprávnění. Ale [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] spuštěný v sandboxu částečným vztahem důvěryhodnosti zabezpečení zóně Internet tomu tak není.  
  
#### <a name="shutdown-mode"></a>Ukončení režimu  
 Většina aplikací vypnout když jsou uzavřeny všechny systémy windows nebo při zavření hlavního okna. V některých případech však další podmínky specifické pro aplikaci může zjistit, kdy aplikace ukončí. Můžete určit podmínky, za kterých vaše aplikace se vypne nastavením <xref:System.Windows.Application.ShutdownMode%2A> s jedním z následujících <xref:System.Windows.ShutdownMode> hodnot výčtu:  
  
-   <xref:System.Windows.ShutdownMode.OnLastWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnMainWindowClose>  
  
-   <xref:System.Windows.ShutdownMode.OnExplicitShutdown>  
  
 Výchozí hodnota <xref:System.Windows.Application.ShutdownMode%2A> je <xref:System.Windows.ShutdownMode.OnLastWindowClose>, což znamená, že se aplikace automaticky ukončí při zavření posledního okna v aplikaci uživatele. Ale pokud by měl být vypnut aplikace při hlavní okno uzavření, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dělá, automaticky, pokud jste nastavili <xref:System.Windows.Application.ShutdownMode%2A> k <xref:System.Windows.ShutdownMode.OnMainWindowClose>. To je ukázáno v následujícím příkladu.  
  
 [!code-xaml[ApplicationShutdownModeSnippets#OnMainWindowCloseMARKUP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationShutdownModeSnippets/CS/Page1.xaml#onmainwindowclosemarkup)]  
  
 Až budete mít specifické pro aplikaci vypnout podmínky, nastavíte <xref:System.Windows.Application.ShutdownMode%2A> k <xref:System.Windows.ShutdownMode.OnExplicitShutdown>. V takovém případě je vaší odpovědností, abyste vypnutí aplikace explicitně voláním <xref:System.Windows.Application.Shutdown%2A> metody; v opačném případě bude vaše aplikace dál běžet i v případě, že všechna okna zavřete. Všimněte si, že <xref:System.Windows.Application.Shutdown%2A> je implicitně volána, když <xref:System.Windows.Application.ShutdownMode%2A> je buď <xref:System.Windows.ShutdownMode.OnLastWindowClose> nebo <xref:System.Windows.ShutdownMode.OnMainWindowClose>.  
  
> [!NOTE]
>  <xref:System.Windows.Application.ShutdownMode%2A> můžete nastavit na [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)], ale se ignoruje; [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] se vždy vypne při jeho je opuštění v prohlížeči nebo prohlížeč, který je hostitelem [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je uzavřen. Další informace najdete v tématu [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
#### <a name="session-ending"></a>Ukončení relace  
 Vypnout podmínky, které jsou popsané <xref:System.Windows.Application.ShutdownMode%2A> vlastnosti jsou specifické pro aplikaci. V některých případech však aplikace může vypnout v důsledku externí podmínku. Nejběžnější externí stavu dochází, když uživatel ukončí relaci Windows pomocí následujících akcí:  
  
-   Odhlášení  
  
-   Vypínání  
  
-   Restartování  
  
-   V režimu spánku  
  
 Ke zjištění při ukončení relace Windows, dokáže zpracovat <xref:System.Windows.Application.SessionEnding> události, jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[ApplicationSessionEndingSnippets#HandlingSessionEndingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml#handlingsessionendingxaml)]  
  
 [!code-csharp[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/CSharp/App.xaml.cs#handlingsessionendingcodebehind)]
 [!code-vb[ApplicationSessionEndingSnippets#HandlingSessionEndingCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationSessionEndingSnippets/visualbasic/application.xaml.vb#handlingsessionendingcodebehind)]  
  
 V tomto příkladu zkontroluje kód <xref:System.Windows.SessionEndingCancelEventArgs.ReasonSessionEnding%2A> a určí, jak se ukončuje relace Windows. Tato hodnota používá pro zobrazení zprávy potvrzení pro uživatele. Pokud uživatel nechce relace do konce, kód nastaví <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> k `true` zabránit ukončuje relace Windows.  
  
> [!NOTE]
>  <xref:System.Windows.Application.SessionEnding> není vyvolána pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
#### <a name="exit"></a>Ukončit  
 Při vypnutí aplikace může potřebovat k provedení konečné zpracování, jako je například zachování stavu aplikace. V takových situacích můžete zpracovávat <xref:System.Windows.Application.Exit> událostí.  
  
 [!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml1)]  
[!code-xaml[HOWTOApplicationModelSnippets#PersistRestoreAppScopePropertiesXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml#persistrestoreappscopepropertiesxaml2)]  
  
 [!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind1)]
 [!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind1)]  
[!code-csharp[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/CSharp/App.xaml.cs#persistappscopepropertiescodebehind2)]
[!code-vb[HOWTOApplicationModelSnippets#PersistAppScopePropertiesCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOApplicationModelSnippets/visualbasic/application.xaml.vb#persistappscopepropertiescodebehind2)]  
  
 Kompletní příklad naleznete v tématu [zachovat a obnovit vlastnosti rozsahu aplikace mezi relacemi aplikace](../../../../docs/framework/wpf/app-development/persist-and-restore-application-scope-properties.md).  
  
 <xref:System.Windows.Application.Exit> může být zpracována i samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)], <xref:System.Windows.Application.Exit> dojde v následujících případech:  
  
-   [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Je opuštění.  
  
-   V [!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)], když na kartě, který je hostitelem [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] je zavřený.  
  
-   Při zavření prohlížeče.  
  
#### <a name="exit-code"></a>Ukončovací kód  
 Aplikace je většinou spuštěných podle operačního systému v reakci na žádost uživatele. Ale aplikace může spustit jinou aplikaci k provedení některých konkrétního úkolu. Při vypnutí aplikace spouštění aplikace může chtít vědět podmínka, jejímž ukončení aplikace. V těchto situacích Windows umožňuje aplikacím, které má být vrácen ukončovací kód aplikace při vypnutí. Ve výchozím nastavení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace vrací hodnotu ukončovací kód 0.  
  
> [!NOTE]
>  Při ladění z [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], ukončovací kód aplikace se zobrazí v **výstup** okno při vypnutí aplikace, ve zprávě vypadá podobně jako následující:  
>   
>  `The program '[5340] AWPFApp.vshost.exe: Managed' has exited with code 0 (0x0).`  
>   
>  Otevřete **výstup** okno kliknutím **výstup** na **zobrazení** nabídky.  
  
 Chcete-li změnit ukončovací kód, můžete volat <xref:System.Windows.Application.Shutdown%28System.Int32%29> přetížení, která přebírá celočíselný argument bude ukončovací kód:  
  
 [!code-csharp[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationExitSnippets/CSharp/MainWindow.xaml.cs#appexitcode)]
 [!code-vb[ApplicationExitSnippets#AppExitCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationExitSnippets/visualbasic/mainwindow.xaml.vb#appexitcode)]  
  
 Můžete zjistit hodnotu ukončovacího kódu a změnit, zpracování <xref:System.Windows.Application.Exit> událostí. <xref:System.Windows.Application.Exit> Je předána obslužné rutiny události <xref:System.Windows.ExitEventArgs> poskytující přístup k ukončovací kód s <xref:System.Windows.ExitEventArgs.ApplicationExitCode%2A> vlastnost. Další informace naleznete v tématu <xref:System.Windows.Application.Exit>.  
  
> [!NOTE]
>  Ukončovací kód můžete nastavit v obou samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]. Ale hodnotu ukončovacího kódu se ignoruje pro [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)].  
  
<a name="Unhandled_Exceptions"></a>   
### <a name="unhandled-exceptions"></a>Nezpracované výjimky  
 Aplikace může někdy vypnout podle nestandardní podmínky, třeba když dojde k neočekávané výjimce. V tomto případě aplikace nemusí mít kód ke zjištění a zpracování výjimky. Tento typ výjimka je neošetřená výjimka; Před ukončením aplikace, zobrazí se oznámení podobný tomu je znázorněno na následujícím obrázku.  
  
 ![Neošetřená výjimka oznámení](../../../../docs/framework/wpf/app-development/media/applicationmanagementoverviewfigure2.png "ApplicationManagementOverviewFigure2")  
  
 Z pohledu zkušenosti uživatele je lepší pro aplikaci, aby toto výchozí chování provedením některé nebo všechny z následujících akcí:  
  
-   Zobrazení informací o uživatelsky přívětivé.  
  
-   Pokus zachovat aplikaci spuštěnou.  
  
-   Záznam podrobné, vývojářsky přívětivé, informace o výjimce v protokolu událostí Windows.  
  
 Tato podpora implementace závisí na schopnost rozpoznat neošetřené výjimky, to znamená, co <xref:System.Windows.Application.DispatcherUnhandledException> událost se vyvolá pro.  
  
 [!code-xaml[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml#handledispatcherunhandledexceptionxaml)]  
  
 [!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind1)]
 [!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind1)]  
[!code-csharp[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/CSharp/App.xaml.cs#handledispatcherunhandledexceptioncodebehind2)]
[!code-vb[ApplicationDispatcherUnhandledExceptionSnippets#HandleDispatcherUnhandledExceptionCODEBEHIND2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationDispatcherUnhandledExceptionSnippets/visualbasic/application.xaml.vb#handledispatcherunhandledexceptioncodebehind2)]  
  
 <xref:System.Windows.Application.DispatcherUnhandledException> Obslužná rutina události je předán <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs> parametr, který obsahuje kontextové informace týkající se neošetřená výjimka, včetně výjimek, samotný (<xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Exception%2A?displayProperty=nameWithType>). Tyto informace můžete použít k určení způsobu zpracování výjimky.  
  
 Při zpracování <xref:System.Windows.Application.DispatcherUnhandledException>, byste měli nastavit <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A?displayProperty=nameWithType> vlastnost `true`; v opačném případě [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] stále výjimka, která má neošetřené bere v úvahu a se vrátí do výchozího chování popsané výše. Pokud dojde k neošetřené výjimce a buď <xref:System.Windows.Application.DispatcherUnhandledException> nezpracovává události nebo zpracovává události a <xref:System.Windows.Threading.DispatcherUnhandledExceptionEventArgs.Handled%2A> je nastavena na `false`, okamžitě ukončí aplikaci. Kromě toho žádné jiné <xref:System.Windows.Application> jsou vyvolány události. V důsledku toho je potřeba zpracovat <xref:System.Windows.Application.DispatcherUnhandledException> Pokud aplikace obsahuje kód, který musí spustit před vypnutím aplikace.  
  
 I když může aplikace vypnout v důsledku neošetřené výjimky, aplikace obvykle ukončí v reakci na žádost uživatele, jak je popsáno v další části.  
  
<a name="Application_Lifetime_Events"></a>   
### <a name="application-lifetime-events"></a>Události životního cyklu aplikací  
 Samostatné aplikace a [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] nemají přesně stejný životní cyklus. Následující obrázek znázorňuje klíče události během životnosti samostatné aplikace a zobrazuje pořadí, ve kterém jsou vyvolány.  
  
 ![Samostatná aplikace &#45; události aplikačního objektu](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents.png "ApplicationModelOverview_ApplicationObjectEvents")  
  
 Podobně, následující obrázek ukazuje klíčové události v době životnosti [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]a zobrazuje pořadí, ve kterém jsou vyvolány.  
  
 ![XBAP &#45; události aplikačního objektu](../../../../docs/framework/wpf/app-development/media/applicationmodeloverview-applicationobjectevents-xbap.png "ApplicationModelOverview_ApplicationObjectEvents_xbap")  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Application>  
 [Přehled Windows ve WPF](../../../../docs/framework/wpf/app-development/wpf-windows-overview.md)  
 [Přehled navigace](../../../../docs/framework/wpf/app-development/navigation-overview.md)  
 [Prostředek, obsah a datové soubory aplikace WPF](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)  
 [Sbalení URI v technologii WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Aplikačního modelu: Postupy: témata](https://msdn.microsoft.com/library/76771b09-3688-4d1c-8818-9b3f4cf39a30)  
 [Vývoj aplikací](../../../../docs/framework/wpf/app-development/index.md)
