---
title: Aktivity zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 3391f7442ef4922a847a58b6316eb177cbcfbd5e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086338"
---
# <a name="messaging-activities"></a>Aktivity zasílání zpráv
Zasílání zpráv aktivity umožňují pracovní postupy pro odesílání a příjem zpráv WCF. Přidáním zasílání zpráv aktivity do pracovního postupu lze modelovat žádné vzory libovolně složité zpráv exchange (MEP).

## <a name="message-exchange-patterns"></a>Vzorky serveru Exchange zprávu
 Existují tři vzory základní zpráv exchange:

-   **Datagram** – při použití datagram MEP klient odešle zprávu do služby, ale služba nereaguje. To se někdy nazývá "vypal a zapomeň". A vypal a zapomeň exchange je ten, který vyžaduje out-of-band potvrzení úspěšné dodání. Zpráva může dojít ke ztrátě během přenosu a nikdy nedorazí služby. Když klient úspěšně pošle zprávu, není zaručeno, že Služba obdržela zprávu. Datagram je základním stavebním blokem pro zasílání zpráv, jak můžete vytvářet vlastní MEPs dojde k jeho zvýraznění.

-   **Odpověď na požadavek** – při použití MEP typu žádost odpověď klientovi odešle zprávy do služby, služby nemá požadované zpracování a pak zasílá odpověď zpět klientovi. Vzor se skládá z dvojice žádost odpověď. Odpověď na požadavek volání příklady vzdálených volání procedur (RPC) a prohlížeč GET požadavky. Tento model se také označuje jako poloduplexní.

-   **Duplexní** – při použití duplexní MEP klient a služba odesílat zprávy do sebe navzájem v libovolném pořadí. Duplexní MEP je jako je telefonní hovor, kde je zpráva každého slova, se kterým se mluví.

 Zasílání zpráv aktivity umožňují provádět některé z těchto základních MEPs stejně jako jakékoli MEP libovolně složité.

## <a name="messaging-activities"></a>Aktivity zasílání zpráv
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Definuje následující zasílání zpráv aktivity:

-   <xref:System.ServiceModel.Activities.Send>– Použijte <xref:System.ServiceModel.Activities.Send> aktivity odeslat zprávu.

-   <xref:System.ServiceModel.Activities.SendReply> – Použijte <xref:System.ServiceModel.Activities.SendReply> aktivitu odeslání odpovědi na přijatou zprávu. Tato aktivita používá služby pracovního postupu při implementaci požadavku/odpovědi MEP.

-   <xref:System.ServiceModel.Activities.Receive>– Použijte <xref:System.ServiceModel.Activities.Receive> aktivity při příjmu zprávy.

-   <xref:System.ServiceModel.Activities.ReceiveReply> – Použijte <xref:System.ServiceModel.Activities.ReceiveReply> aktivity pro příjem zprávy s odpovědí. Tato aktivita používají klienti služby pracovního postupu při implementaci požadavku/odpovědi MEP.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Aktivity zasílání zpráv a vzory zpráv Exchange
 Datagram MEP zahrnuje klient odesílá zprávu a služba příjem zprávy. Pokud je klient použití pracovního postupu <xref:System.ServiceModel.Activities.Send> aktivitu k odeslání zprávy. Pro příjem této zprávy v pracovním postupu, použijte <xref:System.ServiceModel.Activities.Receive> aktivity. <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity každý mají vlastnost s názvem `Content`. Tato vlastnost obsahuje dat odesílaných nebo přijímaných. Při implementaci MEP odpověď na požadavek klienta a služby pomocí dvojice aktivit. Klient použije <xref:System.ServiceModel.Activities.Send> aktivity odeslat zprávu a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity získat odpověď ze služby. Tyto dvě aktivity jsou spojeny s jinými podle <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> vlastnost. Tato vlastnost nastavena <xref:System.ServiceModel.Activities.Send> aktivity, který odeslal původní zprávy. Služba také používá dvojici souvisejících činností: <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>. Tyto dvě aktivity jsou přidružené k podle <xref:System.ServiceModel.Activities.SendReply.Request%2A> vlastnost. Tato vlastnost nastavená na <xref:System.ServiceModel.Activities.Receive> aktivitu, která se zobrazila původní zprávy. <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply> aktivity, jako jsou <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> umožnit si odesílat <xref:System.ServiceModel.Channels.Message> instance nebo typ kontraktu zprávy.

 Vzhledem k povaze pracovních postupů dlouhotrvající je důležité pro duplexní vzor komunikace podporuje taky dlouhotrvající konverzace. Pro podporu dlouhotrvající konverzace, klienti, kteří zahájit konverzaci musíte poskytnout službě příležitost pro zpětné volání na pozdější dobu, kdy budou data k dispozici. Například požadavek nákupní objednávky se odešle ke schválení správcem, ale nemusí být zpracována pro den, týden nebo dokonce i za rok; pracovní postup, který spravuje schválení nákupní objednávky musí znát pokračovat, až se schválení. Tento model duplexní komunikaci se podporuje v pracovních postupech, pomocí korelace. K implementaci vzoru duplexní, použít <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity. Na <xref:System.ServiceModel.Activities.Receive> aktivity, inicializujte korelace pomocí speciální hodnotu klíče <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Na <xref:System.ServiceModel.Activities.Send> popisovače korelace jako sadu aktivit <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> hodnotu vlastnosti. Další informace najdete v tématu [trvalý duplexní](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).

> [!NOTE]
>  Pro pracovní postupy provádění duplexní pomocí zpětného volání korelaci ("trvalý duplexní") je určený pro dlouho běžící konverzací. Toto není stejný jako WCF duplexní s kontrakty zpětného volání kde konverzace je krátce běžící (životnost kanál).

## <a name="message-formatting-and-messaging-activities"></a>Formátování zprávy a zasílání zpráv aktivity
 <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity mají vlastnost s názvem `Content`. Tato vlastnost je typu <xref:System.ServiceModel.Activities.ReceiveContent> a představuje data <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.ReceiveReply> aktivita přijímá. Rozhraní .NET Framework definuje dvě související třídy volá <xref:System.ServiceModel.Activities.ReceiveMessageContent> a <xref:System.ServiceModel.Activities.ReceiveParametersContent> obou z nich jsou odvozeny z <xref:System.ServiceModel.Activities.ReceiveContent>. Nastavte <xref:System.ServiceModel.Activities.Receive> nebo <xref:System.ServiceModel.Activities.ReceiveReply> aktivity `Content` vlastnost na instanci jednoho z těchto typů pro příjem dat do služby pracovního postupu. Typ má být použit závisí na typu dat, která přijímá aktivity. Pokud se aktivita dostane `Message` objektu nebo zpráva typ kontraktu, použijte <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Pokud aktivita přijímá sadu kontraktu dat nebo typy XML, které lze serializovat, použijte <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> umožní vám to poslat více parametrů, zatímco <xref:System.ServiceModel.Activities.ReceiveMessageContent> povoluje jenom jeden objekt odeslat, zprávy (nebo typ kontraktu zprávy).

> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> Můžete také použít s jediným datovým smlouvy nebo typ XML, který lze serializovat. Rozdíl mezi použitím <xref:System.ServiceModel.Activities.ReceiveParametersContent> jeden parametr a objekt předaný přímo <xref:System.ServiceModel.Activities.ReceiveMessageContent> je přenosový formát. Obsah parametru je zabalena v elementu XML, který odpovídá názvu operace a serializovaný objekt je zabalena v elementu XML pomocí názvu parametru (například `<Echo><msg>Hello, World</msg></Echo>`). Obsah zprávy není zabalena podle názvu operace. Místo toho serializovaný objekt je umístěn v rámci elementu XML pomocí názvu typu kvalifikovaného XML (například `<string>Hello, World</string>`).

 <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendReply> aktivity také mají vlastnost s názvem `Content`. Tato vlastnost je typu <xref:System.ServiceModel.Activities.SendContent> a představuje data <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> odešle aktivity. Rozhraní .NET Framework definuje dvě souvisejících typů volá <xref:System.ServiceModel.Activities.SendMessageContent> a <xref:System.ServiceModel.Activities.SendParametersContent> obou z nich jsou odvozeny z <xref:System.ServiceModel.Activities.SendContent>. Nastavte <xref:System.ServiceModel.Activities.Send> nebo <xref:System.ServiceModel.Activities.SendReply> aktivity `Content` vlastnost na instanci jednoho z těchto typů k odesílání dat ze služby pracovních postupů. Typ má být použit závisí na typu dat, které odesílá aktivity. Pokud aktivita odesílá `Message` objektu nebo zpráva typ kontraktu, použijte <xref:System.ServiceModel.Activities.SendMessageContent>. Pokud aktivita odesílá a používá typ kontraktu dat <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> umožní vám to poslat více parametrů, zatímco <xref:System.ServiceModel.Activities.SendMessageContent> umožňuje pouze jeden objekt zpráva (nebo typ kontraktu zprávy).

 Při programování imperativně pomocí zasílání zpráv aktivity, je použít Obecné <xref:System.Activities.InArgument%601> a <xref:System.Activities.OutArgument%601> zabalit objekty přiřadit vlastnosti zprávy nebo parametrů <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>a <xref:System.ServiceModel.Activities.ReceiveReply>aktivity. Použití <xref:System.Activities.InArgument%601> pro <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.SendReply> aktivity a <xref:System.Activities.OutArgument%601> pro <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity. `In` argumenty se používají s aktivity odesílání, protože data je předávána do aktivity. `Out` argumenty se používají s aktivitami receive, protože data je předáván z aktivity, jak je znázorněno v následujícím příkladu.

```
Receive reserveSeat = new Receive
{
    ...
    Content = new ReceiveParametersContent
    {
        Parameters =
        {
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }
        }
    }
};
SendReply reserveSeat = new SendReply
{
    ...
    Request = reserveSeat,
    Content = new SendParametersContent
    {
        Parameters =
        {
            { "ReservationId", new InArgument<string>(reservationId) }
        }
    },
};
```

 Při implementaci služby pracovního postupu, který definuje operace požadavku/odpovědi, která vrací typ void, musíte vytvořit instanci <xref:System.ServiceModel.Activities.SendReply> aktivity a nastavte <xref:System.ServiceModel.Activities.SendReply.Content%2A> vlastnost na prázdnou instanci jednoho z typů obsahu (<xref:System.ServiceModel.Activities.SendMessageContent> nebo <xref:System.ServiceModel.Activities.SendParametersContent>) jak je znázorněno v následujícím příkladu.

```
Receive rcv = new Receive()
{
ServiceContractName = "IService",
OperationName = "NullReturningContract",
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )
};
SendReply sr = new SendReply()
{
Request = rcv
   Content = new SendParametersContent();
};
```

## <a name="add-service-reference"></a>Přidání odkazu na službu
 Při volání služby pracovních postupů z aplikace pracovního postupu, Visual Studio 2012 vygeneruje vlastní zasílání zpráv aktivity, které provádí zapouzdření obvyklého <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> aktivit používaných v požadavku/odpovědi MEP. Chcete-li tuto funkci použít, klikněte pravým tlačítkem na klientský projekt v sadě Visual Studio a vyberte **přidat** > **odkaz na službu**. Do pole Adresa zadejte základní adresu služby a klikněte na Přejít. Dostupné služby jsou zobrazeny v **služby:** pole. Rozbalte uzel služby pro zobrazení smluv podporována. Vyberte smlouvy, kterou chcete volat a zobrazí se v seznamu dostupných operací **operace** pole. Potom můžete zadat obor názvů pro generovaný aktivitu a klikněte na tlačítko **OK**. Zobrazí se dialogové okno, která uvádí, že operace byla úspěšně dokončena a, které jsou generované vlastní aktivity v sadě nástrojů po mít znovu sestavit projekt. Je jedna aktivita pro všechny operace definované v kontraktu služby. Po projekt znovu sestavit lze přetáhnout a vyřadit vlastní aktivity do pracovního postupu a nastavte požadované vlastnosti v okně Vlastnosti.

<!--## Messaging Activity Templates
 To make setting up a request/response MEP on the client and service easier, Visual Studio 2012 provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.
-->
## <a name="messaging-activities-and-transactions"></a>Aktivity zasílání zpráv a transakce
 Pokud je provedeno volání služby pracovního postupu můžete chtít transakce pro operace služby. Provedete toto místo <xref:System.ServiceModel.Activities.Receive> aktivitu v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Obsahuje aktivity `Receive` aktivity a tělo. Byly převedeny do služby zůstane během provádění těla okolí transakce <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Transakce je dokončena, když text dokončí provádění. Další informace o pracovních postupů a transakcích najdete v části [pracovního postupu transakce](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Viz také
- [Postup při odesílání a přijímání chyb ve službách pracovních postupů](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Vytvoření dlouhodobé služby pracovního postupu](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
