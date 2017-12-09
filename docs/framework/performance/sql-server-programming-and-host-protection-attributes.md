---
title: "Programování serveru SQL Server a atributy ochrany hostitele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server [.NET Framework]
- permission sets, SQL Server
- SQL Server Programming and Host Protection Attributes
- managed code, SQL Server
- reliability [.NET Framework]
- writing reliable code
- hosts, reliability
- host protection attributes
- HostProtectionAttribute class, reliability
ms.assetid: 7dfa36b4-e773-4c75-a3ff-ff1af3ce4c4f
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f163223842acd4539872ad1a0ff228a76e33870d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-programming-and-host-protection-attributes"></a>Programování serveru SQL Server a atributy ochrany hostitele
Možnost načtení a provedení spravovaného kódu v hostitelském systému SQL Server vyžaduje splnění požadavků hostitele pro zabezpečení přístupu kódu a Ochrana prostředků hostitele.  Požadavky na zabezpečení přístupu kódu jsou určené jednou ze tří sad oprávnění systému SQL Server: BEZPEČNÉ, externí přístup nebo UNSAFE. Kód provádění v rámci SAFE nebo sady oprávnění externí přístup musí vyloučit některé typy nebo členy, kteří mají <xref:System.Security.Permissions.HostProtectionAttribute> atribut použitý. <xref:System.Security.Permissions.HostProtectionAttribute> Není oprávnění zabezpečení tolik, kolik spolehlivost záruku v identifikuje konkrétního kódu vytvoří typy nebo metody, že může zakáže hostitele.  Použití <xref:System.Security.Permissions.HostProtectionAttribute> vynucuje programovací model, který pomáhá chránit stabilitu hostitele.  
  
## <a name="host-protection-attributes"></a>Atributy ochrany hostitele  
 Atributy ochrany hostitele identifikujte typy nebo členy, kteří nemají přizpůsobit programovací model hostitele a představují následujících roste úrovní spolehlivosti threat:  
  
-   Jinak jsou neškodné.  
  
-   Může vést k destabilization serveru spravované uživatelského kódu.  
  
-   Může vést k destabilization procesu serveru sám sebe.  
  
 Zakáže použití typ nebo člen, který má SQL Server <xref:System.Security.Permissions.HostProtectionAttribute> určující <xref:System.Security.Permissions.HostProtectionResource> hodnotu <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, <xref:System.Security.Permissions.HostProtectionResource.MayLeakOnAbort>, nebo <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Tím se zabrání sestavení z volání členy, kteří povolit sdílení stav, provádět synchronizaci, může způsobit, že prostředků na ukončení nebo vliv na celistvost procesu systému SQL Server.  
  
### <a name="disallowed-types-and-members"></a>Nepovoleném typů a členů  
 V následující tabulce jsou uvedeny typy a členy jejichž <xref:System.Security.Permissions.HostProtectionResource> hodnoty jsou zakázány na úrovni systému SQL Server.  
  
|Obor názvů|Typ nebo člen|  
|---------------|--------------------|  
|`Microsoft.Win32`|<xref:Microsoft.Win32.PowerModeChangedEventArgs>– Třída<br /><br /> <xref:Microsoft.Win32.PowerModeChangedEventHandler>Delegát<br /><br /> <xref:Microsoft.Win32.SessionEndedEventArgs>– Třída<br /><br /> <xref:Microsoft.Win32.SessionEndedEventHandler>Delegát<br /><br /> <xref:Microsoft.Win32.SessionEndingEventArgs>– Třída<br /><br /> <xref:Microsoft.Win32.SessionEndingEventHandler>Delegát<br /><br /> <xref:Microsoft.Win32.SessionSwitchEventArgs>– Třída<br /><br /> <xref:Microsoft.Win32.SessionSwitchEventHandler>Delegát<br /><br /> <xref:Microsoft.Win32.SystemEvents>– Třída<br /><br /> <xref:Microsoft.Win32.TimerElapsedEventArgs>– Třída<br /><br /> <xref:Microsoft.Win32.TimerElapsedEventHandler>Delegát<br /><br /> <xref:Microsoft.Win32.UserPreferenceChangedEventArgs>– Třída<br /><br /> <xref:Microsoft.Win32.UserPreferenceChangingEventArgs>– Třída|  
|`System.Collections`|<xref:System.Collections.ArrayList.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Collections.Hashtable.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Collections.Queue.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Collections.SortedList.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Collections.Stack.Synchronized%2A?displayProperty=nameWithType>– Metoda|  
|`System.ComponentModel`|<xref:System.ComponentModel.AddingNewEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.AddingNewEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.ArrayConverter>– Třída<br /><br /> <xref:System.ComponentModel.AsyncCompletedEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.AsyncCompletedEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.AsyncOperation>– Třída<br /><br /> <xref:System.ComponentModel.AsyncOperationManager>– Třída<br /><br /> <xref:System.ComponentModel.AttributeCollection>– Třída<br /><br /> <xref:System.ComponentModel.BackgroundWorker>– Třída<br /><br /> <xref:System.ComponentModel.BaseNumberConverter>– Třída<br /><br /> <xref:System.ComponentModel.BindingList%601>– Třída<br /><br /> <xref:System.ComponentModel.BooleanConverter>– Třída<br /><br /> <xref:System.ComponentModel.ByteConverter>– Třída<br /><br /> <xref:System.ComponentModel.CancelEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.CancelEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.CharConverter>– Třída<br /><br /> <xref:System.ComponentModel.CollectionChangeEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.CollectionChangeEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.CollectionConverter>– Třída<br /><br /> <xref:System.ComponentModel.ComponentCollection>– Třída<br /><br /> <xref:System.ComponentModel.ComponentConverter>– Třída<br /><br /> <xref:System.ComponentModel.ComponentEditor>– Třída<br /><br /> <xref:System.ComponentModel.ComponentResourceManager>– Třída<br /><br /> <xref:System.ComponentModel.Container>– Třída<br /><br /> <xref:System.ComponentModel.ContainerFilterService>– Třída<br /><br /> <xref:System.ComponentModel.CultureInfoConverter>– Třída<br /><br /> <xref:System.ComponentModel.CustomTypeDescriptor>– Třída<br /><br /> <xref:System.ComponentModel.DateTimeConverter>– Třída<br /><br /> <xref:System.ComponentModel.DecimalConverter>– Třída<br /><br /> <xref:System.ComponentModel.Design.ActiveDesignerEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.ActiveDesignerEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.CheckoutException>– Třída<br /><br /> <xref:System.ComponentModel.Design.CommandID>– Třída<br /><br /> <xref:System.ComponentModel.Design.ComponentChangedEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.ComponentChangedEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.ComponentChangingEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.ComponentChangingEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.ComponentEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.ComponentEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.ComponentRenameEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.ComponentRenameEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.DesignerCollection>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesignerEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesignerEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.DesignerOptionService>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesignerTransaction>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesignerTransactionCloseEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesignerTransactionCloseEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.DesignerVerb>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesignerVerbCollection>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesigntimeLicenseContext>– Třída<br /><br /> <xref:System.ComponentModel.Design.DesigntimeLicenseContextSerializer>– Třída<br /><br /> <xref:System.ComponentModel.Design.MenuCommand>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.ComponentSerializationService>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.ContextStack>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.DesignerLoader>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.InstanceDescriptor>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.MemberRelationshipService>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.ResolveNameEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.Design.Serialization.ResolveNameEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.Design.Serialization.SerializationStore>– Třída<br /><br /> <xref:System.ComponentModel.Design.ServiceContainer>– Třída<br /><br /> <xref:System.ComponentModel.Design.ServiceCreatorCallback>Delegát<br /><br /> <xref:System.ComponentModel.Design.StandardCommands>– Třída<br /><br /> <xref:System.ComponentModel.Design.StandardToolWindows>– Třída<br /><br /> <xref:System.ComponentModel.DoubleConverter>– Třída<br /><br /> <xref:System.ComponentModel.DoWorkEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.DoWorkEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.EnumConverter>– Třída<br /><br /> <xref:System.ComponentModel.EventDescriptor>– Třída<br /><br /> <xref:System.ComponentModel.EventDescriptorCollection>– Třída<br /><br /> <xref:System.ComponentModel.EventHandlerList>– Třída<br /><br /> <xref:System.ComponentModel.ExpandableObjectConverter>– Třída<br /><br /> <xref:System.ComponentModel.HandledEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.HandledEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.InstanceCreationEditor>– Třída<br /><br /> <xref:System.ComponentModel.Int16Converter>– Třída<br /><br /> <xref:System.ComponentModel.Int32Converter>– Třída<br /><br /> <xref:System.ComponentModel.Int64Converter>– Třída<br /><br /> <xref:System.ComponentModel.InvalidAsynchronousStateException>– Třída<br /><br /> <xref:System.ComponentModel.InvalidEnumArgumentException>– Třída<br /><br /> <xref:System.ComponentModel.ISynchronizeInvoke.BeginInvoke%2A>– Metoda<br /><br /> <xref:System.ComponentModel.License>– Třída<br /><br /> <xref:System.ComponentModel.LicenseContext>– Třída<br /><br /> <xref:System.ComponentModel.LicenseException>– Třída<br /><br /> <xref:System.ComponentModel.LicenseManager>– Třída<br /><br /> <xref:System.ComponentModel.LicenseProvider>– Třída<br /><br /> <xref:System.ComponentModel.LicFileLicenseProvider>– Třída<br /><br /> <xref:System.ComponentModel.ListChangedEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.ListChangedEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.ListSortDescription>– Třída<br /><br /> <xref:System.ComponentModel.ListSortDescriptionCollection>– Třída<br /><br /> <xref:System.ComponentModel.MaskedTextProvider>– Třída<br /><br /> <xref:System.ComponentModel.MemberDescriptor>– Třída<br /><br /> <xref:System.ComponentModel.MultilineStringConverter>– Třída<br /><br /> <xref:System.ComponentModel.NestedContainer>– Třída<br /><br /> <xref:System.ComponentModel.NullableConverter>– Třída<br /><br /> <xref:System.ComponentModel.ProgressChangedEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.ProgressChangedEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.PropertyChangedEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.PropertyChangedEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.PropertyDescriptor>– Třída<br /><br /> <xref:System.ComponentModel.PropertyDescriptorCollection>– Třída<br /><br /> <xref:System.ComponentModel.ReferenceConverter>– Třída<br /><br /> <xref:System.ComponentModel.RefreshEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.RefreshEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.RunWorkerCompletedEventArgs>– Třída<br /><br /> <xref:System.ComponentModel.RunWorkerCompletedEventHandler>Delegát<br /><br /> <xref:System.ComponentModel.SByteConverter>– Třída<br /><br /> <xref:System.ComponentModel.SingleConverter>– Třída<br /><br /> <xref:System.ComponentModel.StringConverter>– Třída<br /><br /> <xref:System.ComponentModel.SyntaxCheck>– Třída<br /><br /> <xref:System.ComponentModel.TimeSpanConverter>– Třída<br /><br /> <xref:System.ComponentModel.TypeConverter>– Třída<br /><br /> <xref:System.ComponentModel.TypeDescriptionProvider>– Třída<br /><br /> <xref:System.ComponentModel.TypeDescriptor>– Třída<br /><br /> <xref:System.ComponentModel.TypeListConverter>– Třída<br /><br /> <xref:System.ComponentModel.UInt16Converter>– Třída<br /><br /> <xref:System.ComponentModel.UInt32Converter>– Třída<br /><br /> <xref:System.ComponentModel.UInt64Converter>– Třída<br /><br /> <xref:System.ComponentModel.WarningException>– Třída<br /><br /> <xref:System.ComponentModel.Win32Exception>– Třída|  
|`System.Diagnostics`|<xref:System.Diagnostics.Debug.Listeners%2A?displayProperty=nameWithType>Vlastnost<br /><br /> <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>Vlastnost<br /><br /> <xref:System.Diagnostics.EventLog.SynchronizingObject%2A?displayProperty=nameWithType>Vlastnost<br /><br /> <xref:System.Diagnostics.ConsoleTraceListener>– Třída<br /><br /> <xref:System.Diagnostics.DefaultTraceListener>– Třída<br /><br /> <xref:System.Diagnostics.DelimitedListTraceListener>– Třída<br /><br /> <xref:System.Diagnostics.EventLogTraceListener>– Třída<br /><br /> <xref:System.Diagnostics.PerformanceCounter>– Třída<br /><br /> <xref:System.Diagnostics.PerformanceCounterCategory>– Třída<br /><br /> <xref:System.Diagnostics.Process>– Třída<br /><br /> <xref:System.Diagnostics.ProcessStartInfo>– Třída<br /><br /> <xref:System.Diagnostics.TextWriterTraceListener>– Třída<br /><br /> <xref:System.Diagnostics.TraceListener>– Třída<br /><br /> <xref:System.Diagnostics.XmlWriterTraceListener>– Třída<br /><br /> <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>Vlastnost|  
|`System.IO`|<xref:System.IO.Stream.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.IO.TextReader.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.IO.TextWriter.Synchronized%2A?displayProperty=nameWithType>– Metoda|  
|`System.Reflection.Emit`|<xref:System.Reflection.Emit.ConstructorBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.EventBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.FieldBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.MethodBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.CustomAttributeBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.MethodRental>– Třída<br /><br /> <xref:System.Reflection.Emit.ModuleBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.PropertyBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.TypeBuilder>– Třída<br /><br /> <xref:System.Reflection.Emit.UnmanagedMarshal>– Třída|  
|`System.Text`|<xref:System.Text.RegularExpressions.Group.Synchronized%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Text.RegularExpressions.Match.Synchronized%2A?displayProperty=nameWithType>– Metoda|  
|`System.Threading`|<xref:System.Threading.AutoResetEvent>– Třída<br /><br /> <xref:System.Threading.EventWaitHandle>– Třída<br /><br /> <xref:System.Threading.ManualResetEvent>– Třída<br /><br /> <xref:System.Threading.Monitor>– Třída<br /><br /> <xref:System.Threading.Mutex>– Třída<br /><br /> <xref:System.Threading.ReaderWriterLock>– Třída<br /><br /> <xref:System.Threading.Semaphore>– Třída<br /><br /> <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.BeginCriticalRegion%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.EndCriticalRegion%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.FreeNamedDataSlot%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.SetApartmentState%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.SpinWait%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.Thread.TrySetApartmentState%2A?displayProperty=nameWithType>– Metoda<br /><br /> <xref:System.Threading.ThreadPool>– Třída<br /><br /> <xref:System.Threading.Timer>– Třída|  
|`System.Timers`|<xref:System.Timers.Timer>– Třída|  
|`System.Web.Configuration`|<xref:System.Web.Configuration.MachineKeyValidationConverter>– Třída|  
|`System.Windows.Forms`|<xref:System.Windows.Forms.AutoCompleteStringCollection.SyncRoot%2A?displayProperty=nameWithType>Vlastnost|  
  
## <a name="sql-server-permission-sets"></a>Sady oprávnění serveru SQL  
 SQL Server umožňuje uživatelům zadejte požadavky na spolehlivost kód nasazen do databáze. Při sestavení jsou uloženy v databázi, Autor sestavení můžete určit jednu z tři sady oprávnění pro toto sestavení: BEZPEČNÉ, externí přístup nebo UNSAFE.  
  
|Sady oprávnění|BEZPEČNÉ|EXTERNÍ PŘÍSTUP|NEZABEZPEČENÝ|  
|--------------------|----------|----------------------|------------|  
|Zabezpečení přístupu kódu|Spustit pouze|Spuštění a přístup k externím prostředkům|Bez omezení|  
|Omezení modelu programování|Ano|Ano|Bez omezení|  
|Požadavek ověřitelnosti|Ano|Ano|Ne|  
|Možnost volání nativního kódu|Ne|Ne|Ano|  
  
 BEZPEČNÉ je nejvíce spolehlivou a zabezpečenou režim přidružené omezení z hlediska povolené programovací model. BEZPEČNÉ kódu má vysokou funkce zabezpečení a spolehlivost. BEZPEČNÁ sestavení mají dostatečná oprávnění k spouštět, provádění výpočtů a mít přístup k místní databázi. BEZPEČNÁ sestavení musí být prokazatelně typově bezpečné a není povoleno volat nespravovaný kód.  
  
 EXTERNÍ přístup nabízí možnost zprostředkující zabezpečení, povolení kód pro přístup k prostředkům externí k databázi, ale i nadále s spolehlivost a bezpečnosti BEZPEČNÉ.  
  
 UNSAFE je pro vysoce důvěryhodný kód, který lze vytvářet pouze správce databáze. Tento kód důvěryhodné má žádná omezení přístupu kódu a ho můžete volat nespravovaný kód (nativní).  
  
 Nastavte zásady hostitele, která uděluje jeden ze tří sady oprávnění na základě oprávnění k nastavení uložená v katalozích systému SQL Server používá systém SQL Server vrstva zásad zabezpečení přístupu kódu na úrovni hostitele. Spravovaný kód běží uvnitř databáze vždy získá některé z těchto sad oprávnění přístupu kódu.  
  
## <a name="programming-model-restrictions"></a>Omezení modelu programování  
 Programovací model pro spravovaný kód v systému SQL Server vyžaduje funkce, postupy a typy, které nevyžadují použití stavu uchovávat napříč více volání nebo sdílení stavu napříč více uživatelských relací. Další jak je popsáno výše, přítomnost sdílený stav může způsobit kritické výjimky, které mají vliv na škálovatelnost a spolehlivost aplikace.  
  
 Zadané těchto aspektů, SQL Server zakáže použití statické proměnné a členy statických dat. Pro BEZPEČNÉ a externí přístup sestavení SQL Server prozkoumá metadata sestavení v době vytvoření sestavení a vytvoření takové sestavení se nezdaří, pokud najde použití členy statických dat a proměnné.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>