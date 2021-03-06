---
title: Co&#39;s nové v modelu Windows Workflow Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: d45c16d4f16c239d1c1c8116b4b41dd41f8a953d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518434"
---
# <a name="what39s-new-in-windows-workflow-foundation"></a>Co&#39;s nové v modelu Windows Workflow Foundation
Windows Workflow Foundation (WF) v [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] několik vzorů vývoj změny z předchozích verzí. Pracovní postupy jsou nyní snazší vytvoření, spuštění a udržovat a implementaci hostitel nové funkce. Další informace o migraci rozhraní .NET 3.0 a rozhraní .NET 3.5 pracovního postupu aplikacím používat nejnovější verzi najdete v tématu [migrace pokyny](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Model aktivity pracovního postupu  
 Aktivita je nyní základní jednotka vytvoření pracovního postupu, nikoli pomocí <xref:System.Workflow.Activities.SequentialWorkflowActivity> nebo <xref:System.Workflow.Activities.StateMachineWorkflowActivity> třídy. <xref:System.Activities.Activity> Třída poskytuje základní abstrakci chování pracovního postupu. Autoři aktivity poté můžete implementovat buď <xref:System.Activities.CodeActivity> pro funkce základní vlastní aktivitu, nebo <xref:System.Activities.NativeActivity> pro funkce vlastní aktivity, které používá spektra modulu runtime. <xref:System.Activities.Activity> je třída používaná autory aktivity k express nové chování deklarativně z hlediska dalších <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, nebo <xref:System.Activities.DynamicActivity> objekty, ať už jsou zákaznických nebo součástí [předdefinované aktivity Knihovna](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Složené bohaté možnosti aktivity  
 <xref:System.Activities.Statements.Flowchart> je aktivitu toku řízení pro efektivní nové, který umožňuje autorům model libovolný smyček a větvení. <xref:System.Activities.Statements.Flowchart> poskytuje událostmi řízené programování model, který byl dříve pouze moci být implementováno s <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Procedurální pracovních využívat nové aktivity řízení toku, které model struktury tradiční řízení toku, jako například <xref:System.Activities.Statements.TryCatch> a <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Rozšířená předdefinovaná knihovna aktivit  
 Nové funkce knihovny aktivit:  
  
-   Nové toku řízení aktivity, jako je třeba <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601>, a <xref:System.Activities.Statements.ParallelForEach%601>.  
  
-   Aktivity pro manipulaci s daty členů, jako například <xref:System.Activities.Statements.Assign> a kolekce aktivity, jako <xref:System.Activities.Statements.AddToCollection%601>.  
  
-   Aktivity pro řízení transakcí, jako například <xref:System.Activities.Statements.TransactionScope> a <xref:System.Activities.Statements.Compensate>.  
  
-   Nové aktivity zasílání zpráv, jako <xref:System.ServiceModel.Activities.SendContent> a <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Datový Model explicitní aktivity  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] obsahuje nové možnosti pro ukládání nebo přesun dat. Data se uloží v aktivity pomocí <xref:System.Activities.Variable>. Při přesunu dat do aplikace a z aktivity, typy specializované argumentů se používají k určení směru data, která je přesunutí. Tyto typy jsou <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument>, a <xref:System.Activities.OutArgument>. Další informace najdete v tématu [Windows Workflow Foundation datový Model](../../../docs/framework/windows-workflow-foundation/data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Rozšířené možnosti sledování a hostování, trvalosti,  
 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] obsahuje vylepšení trvalost například následující:  
  
-   Existují další možnosti pro spouštění pracovních postupů, včetně <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication>, a <xref:System.Activities.WorkflowInvoker>.  
  
-   Data stavu pracovního postupu může být explicitně jako trvalý, pomocí <xref:System.Activities.Statements.Persist> aktivity.  
  
-   Můžete zachovat hostitele <xref:System.Activities.ActivityInstance> bez uvolnění ho.  
  
-   Můžete zadat pracovní postup zón bez trvalosti při práci s daty, která nelze nastavit jako trvalý, takže trvalost posunut až do konce no-persist zóny.  
  
-   Transakce mohou být předávány do pracovního postupu pomocí <xref:System.Activities.Statements.TransactionScope>.  
  
-   Sledování je snadno dosáhnout pomocí <xref:System.Activities.Tracking.TrackingParticipant>.  
  
-   Sledování do protokolu událostí systému je prováděno pomocí <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
-   Obnovení čekající pracovního postupu je teď spravované pomocí <xref:System.Activities.Bookmark> objektu.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Snazší možnost rozšíření návrháře WF prostředí  
 Nový návrhář WF je založený na Windows Presentation Foundation (WPF) a nabízí jednodušší model pro použití při opětovném hostování návrháře WF mimo Visual Studio a také nabízí jednodušší mechanismy pro vytváření Návrháře vlastních aktivit. Další informace najdete v tématu [přizpůsobení prostředí návrhu pracovních postupů](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md).
