---
title: "Postup kanálu a mezipaměť"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 954f030e-091c-4c0e-a7a2-10f9a6b1f529
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b06d290760afa9a52274c30899e25f00bc18af2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="channel-factory-and-caching"></a>Postup kanálu a mezipaměť
Pomocí klientských aplikací WCF <xref:System.ServiceModel.ChannelFactory%601> třída k vytvoření kanálu komunikace se službou WCF.  Vytváření <xref:System.ServiceModel.ChannelFactory%601> instance způsobuje zvýšení zatížení, protože se týká následující operace:  
  
-   Vytváření <xref:System.ServiceModel.Description.ContractDescription> stromu  
  
-   Odrážející všechny požadované typy CLR  
  
-   Vytváření kanálu zásobníku  
  
-   Uvolnění prostředků  
  
 Abyste minimalizovali Tato dodatečná režie, můžete WCF mezipaměti objektů Factory kanál, když používáte proxy server klienta WCF.  
  
> [!TIP]
>  Máte přímou kontrolu nad vytvoření objektu pro vytváření kanálu při použití <xref:System.ServiceModel.ChannelFactory%601> přímo třídu.  
  
 Proxy klienta WCF vygeneroval s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jsou odvozeny od <xref:System.ServiceModel.ClientBase%601>. <xref:System.ServiceModel.ClientBase%601>Definuje statického <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> vlastnost, která definuje chování ukládání do mezipaměti objekt pro vytváření kanálu. Nastavení mezipaměti jsou vytvářeny pro konkrétní typ. Například nastavení `ClientBase<ITest>.CacheSettings` na jednu z hodnot fronty definovaných níže ovlivní pouze ty proxy nebo třídu ClientBase typu `ITest`. Nastavení mezipaměti pro konkrétní <xref:System.ServiceModel.ClientBase%601> se nedá změnit, jakmile se vytvoří první instance proxy nebo třídu ClientBase.  
  
## <a name="specifying-caching-behavior"></a>Určení chování ukládání do mezipaměti  
 Chování ukládání do mezipaměti je určený nastavením <xref:System.ServiceModel.ClientBase%601.CacheSetting> vlastnost na jednu z následujících hodnot.  
  
|Nastavení hodnoty do mezipaměti|Popis|  
|-------------------------|-----------------|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOn>|Všechny instance <xref:System.ServiceModel.ClientBase%601> v rámci domény aplikace mohou být součástí ukládání do mezipaměti. Vývojář bylo zjištěno, že neexistují žádné negativní zabezpečení dopady na ukládání do mezipaměti. Ukládání do mezipaměti nebude to i v případě "citlivé na zabezpečení" vlastnosti na vypnout <xref:System.ServiceModel.ClientBase%601> ke kterým se přistupuje. Vlastnosti "citlivé na zabezpečení" <xref:System.ServiceModel.ClientBase%601> jsou <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>, <xref:System.ServiceModel.ClientBase%601.Endpoint%2A> a <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A>.|  
|<xref:System.ServiceModel.CacheSetting.Default>|Pouze instance <xref:System.ServiceModel.ClientBase%601> vytvořené z koncové body definované v konfiguraci soubory účastnit ukládání do mezipaměti v rámci domény aplikace. Všechny instance <xref:System.ServiceModel.ClientBase%601> vytvořit prostřednictvím kódu programu v této doméně aplikace se neúčastní ukládání do mezipaměti. Navíc ukládání do mezipaměti bude zakázán pro instanci <xref:System.ServiceModel.ClientBase%601> po některou z jejích vlastností "citlivé na zabezpečení" přistupuje.|  
|<xref:System.ServiceModel.CacheSetting.AlwaysOff>|Ukládání do mezipaměti je vypnuté pro všechny instance <xref:System.ServiceModel.ClientBase%601> určitého typu v rámci dotyčném domény aplikace.|  
  
 Následující fragmenty kódu ukazují, jak používat <xref:System.ServiceModel.ClientBase%601.CacheSetting%2A> vlastnost.  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase<ITest>.CacheSettings = CacheSettings.AlwaysOn;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient (new BasicHttpBinding(), new EndpointAddress(address)))   
         {   
            // ...  
            proxy.Test(msg);   
            // ...  
         }   
      }   
   }   
}  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest { }  
```  
  
 Ve výše uvedeném kódu, všechny instance `TestClient` bude používat stejné kanálu.  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.Default;   
      int i = 1;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            if (i == 4)   
            {   
               ServiceEndpoint endpoint = proxy.Endpoint;   
               ... // use endpoint in some way   
            }   
            proxy.Test(msg);   
         }   
         i++;   
   }   
}   
  
// Generated by SvcUtil.exe     
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 V příkladu výše, všechny instance `TestClient` byste použili stejné kanálu s výjimkou instanci #4. Instance #4 využije kanálu, který je vytvořena speciálně pro jeho použití. Toto nastavení by fungovat pro scénáře, kde konkrétní koncový bod potřebuje jiné bezpečnostní nastavení z dalších koncových bodů stejný typ objektu pro vytváření kanálu (v tomto případě `ITest`).  
  
```  
class Program   
{   
   static void Main(string[] args)   
   {   
      ClientBase.CacheSettings = CacheSettings.AlwaysOff;   
      foreach (string msg in messages)   
      {   
         using (TestClient proxy = new TestClient ("MyEndpoint", new EndpointAddress(address)))   
         {   
            proxy.Test(msg);   
         }           
      }   
   }  
}  
  
// Generated by SvcUtil.exe   
public partial class TestClient : System.ServiceModel.ClientBase, ITest {}  
```  
  
 V příkladu výše, všechny instance `TestClient` byste použili jiný kanál objekty pro vytváření. To je užitečné, když každý koncový bod má jiné požadavky na zabezpečení a nemá smysl do mezipaměti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ClientBase%601>  
 [Sestavování klientů](../../../../docs/framework/wcf/building-clients.md)  
 [Klienti](../../../../docs/framework/wcf/feature-details/clients.md)  
 [Přístup ke službám pomocí klienta WCF](../../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [Postupy: použití třídy ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)