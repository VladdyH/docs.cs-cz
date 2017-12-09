---
title: '&lt;serviceSecurityAudit&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f0c708c19761f6086e1b5c2fdd15904c76fe3de9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Určuje nastavení, které povolení auditování událostí zabezpečení během operací služby.  
  
 \<systém. ServiceModel >  
\<chování >  
\<serviceBehaviors >  
\<chování >  
\<serviceSecurityAudit >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessAndFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessAndFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|auditLogLocation|Určuje umístění protokolu auditu. Platné hodnoty patří:<br /><br /> -Výchozí: Zabezpečení události se zapisují do protokolu aplikace v systému Windows XP a do protokolu událostí v systému Windows Server 2003 a Windows Vista.<br />-Aplikace: Auditu události se zapisují do protokolu událostí aplikace.<br />-Zabezpečení: Auditu události se zapisují do protokolu událostí zabezpečení.<br /><br /> Výchozí hodnota je výchozí. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Logická hodnota, která určuje chování pro potlačení chyb při zápisu do protokolu auditování.<br /><br /> Aplikace mají být upozorněni pro chyb při zápisu do protokolu auditování. Pokud vaše aplikace nebyla navržena pro zpracování chyby auditu, měli byste použít tento atribut potlačit selhání při zápisu do protokolu auditování.<br /><br /> Pokud tento atribut je `true`, než OutOfMemoryException, StackOverFlowException, výjimka ThreadAbortException a ArgumentException – výjimky, které jsou výsledkem pokusí zapsat události auditu jsou zpracovány systémem a nejsou rozšíří aplikace. Pokud tento atribut je `false`, aplikace se budou předávat všechny výjimky, které jsou výsledkem pokusí zapsat události auditu.<br /><br /> Výchozí hodnota je `true`.|  
|serviceAuthorizationAuditLevel|Určuje typy událostí autorizace, které se zaznamenávají do protokolu auditování. Platné hodnoty patří:<br /><br /> -None: Auditování událostí autorizace služby není provedeno.<br />-Úspěch: Pouze události autorizace úspěšné služby se auditují.<br />-Chyba: Pouze selhání události autorizace služby se auditují.<br />-SuccessAndFailure: Obě úspěchy a chyby události autorizace služby se auditují.<br /><br /> Výchozí hodnota je žádné. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Určuje typ zprávy ověřování auditovat události přihlášení. Platné hodnoty patří:<br /><br /> -None: Jsou generovány žádné události auditu.<br />-Úspěch: Pouze události (včetně ověřit podpis zprávy, šifrování a ověření tokenu úplného ověření) úspěšné zabezpečení jsou protokolovány.<br />-Chyba: Jsou protokolovány pouze události chyb.<br />-SuccessAndFailure: Obě jsou zaznamenány události úspěchy a chyby.<br /><br /> Výchozí hodnota je žádné. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<chování >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento element zobrazí slouží k provádění kontroly [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] události ověřování. Při auditování je povoleno, můžete auditovat buď ověření úspěšné nebo neúspěšné pokusy o (nebo oba). Události se zapisují na jednu ze tří protokolů událostí: aplikace, zabezpečení nebo v protokolu výchozí verzi operačního systému. Protokoly událostí lze všechny zobrazit pomocí prohlížeče událostí systému Windows.  
  
 Podrobný příklad použití tohoto elementu konfigurace najdete v tématu [chování auditování služby](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Ve výchozím nastavení v systému Windows XP událostí auditu najdete v protokolu aplikace; v systému Windows Server 2003 a Windows Vista, můžete zobrazit události auditu v protokolu zabezpečení. Umístění události auditu lze zadat nastavením `auditLogLocation` atribut "Žádost" nebo "Zabezpečení". Další informace najdete v tématu [postup: události auditu zabezpečení](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Pokud události se zapisují do protokolu zabezpečení, LocalSecurityPolicy -> Povolit přístup k objektu je potřeba nastavit u "ÚSPĚCH" a "Selhání".  
  
 Při vyhledávání v protokolu událostí, zdroj událostí auditu je "ServiceModel auditu 3.0.0.0". Záznamů zprávy o auditu ověřování mají kategorii "MessageAuthentication", zatímco záznamy auditu autorizace služby mají kategorii 'ServiceAuthorization'.  
  
 Události auditu ověřování zpráv tématech, zda zpráva bylo manipulováno, jestli vypršela platnost zprávy a zda může klient ověřit ve službě. Poskytují informace o tom, jestli je ověřování byla úspěšná nebo neúspěšná spolu s identitou klienta a koncový bod zpráva byla odeslána spolu s akce přidružené ke zprávě.  
  
 Události auditu autorizace služby zahrnují rozhodnutí o autorizaci provedené správcem autorizace služby. Poskytují informace o tom, jestli ověření bylo úspěšné systému se nezdařilo spolu s identitou klienta, koncový bod zpráva byla odeslána na akci spojený se zprávou, identifikátor autorizační kontext, který se vygeneroval ze příchozí zprávy a typ Správce autorizací, který se rozhodnete přístup.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Auditování](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Postupy: auditování událostí zabezpečení](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Chování auditování služby](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)