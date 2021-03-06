---
title: Doporučené postupy pro komunikaci ve frontě
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF], best practices
- best practices [WCF], queued communication
ms.assetid: 446a6383-cae3-4338-b193-a33c14a49948
ms.openlocfilehash: b54569ad3d11c3b9b1b96e2738bdf0582b63b0b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495580"
---
# <a name="best-practices-for-queued-communication"></a>Doporučené postupy pro komunikaci ve frontě
Toto téma obsahuje doporučené postupy pro komunikaci ve frontě v systému Windows Communication Foundation (WCF). Následující části popisují doporučené postupy z hlediska scénář.  
  
## <a name="fast-best-effort-queued-messaging"></a>Rychlé a Best Effort zařazených do fronty zasílání zpráv  
 Pro scénáře, které vyžadují poskytuje oddělení, který zařazených do fronty zasílání zpráv a fast, vysoce výkonné zasílání zpráv s best effort záruky netransakční frontu použít a nastavte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> vlastnost `false`.  
  
 Kromě toho můžete není zabývat náklady zápisy na disk nastavením <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> vlastnost `false`.  
  
 Zabezpečení má dopad na výkon. Další informace najdete v tématu [faktory ovlivňující výkon](../../../../docs/framework/wcf/feature-details/performance-considerations.md).  
  
## <a name="reliable-end-to-end-queued-messaging"></a>Spolehlivé začátku do konce zasílání zpráv zařazených do fronty.  
 Následující části popisují doporučené postupy pro scénáře, které vyžadují začátku do konce spolehlivé zasílání zpráv.  
  
### <a name="basic-reliable-transfer"></a>Základní spolehlivé přenosu  
 Spolehlivost začátku do konce, nastavte <xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> vlastnost `true` k zajištění přenosu. <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> Může být nastavena `true` nebo `false` v závislosti na požadavcích (výchozí hodnota je `true`). Obecně platí <xref:System.ServiceModel.MsmqBindingBase.Durable%2A> je nastavena na `true` jako součást spolehlivost začátku do konce. Ohrožení snížení výkonu, ale provádí zpráva trvanlivý tak, aby zpráva není ztraceny, pokud dojde k chybě správce front.  
  
### <a name="use-of-transactions"></a>Použití transakcí  
 Transakce je nutné použít zajistit spolehlivost začátku do konce. `ExactlyOnce` záruky pouze zkontrolujte doručování zpráv do cílové fronty. K zajištění, že se zobrazila zpráva, použijte transakce. Bez transakcí Pokud dojde k chybě služby, přijdete o zprávu, která je doručování, ale ve skutečnosti doručí se do aplikace.  
  
### <a name="use-of-dead-letter-queues"></a>Použití fronty nedoručených zpráv  
 Fronty nedoručených zpráv Ujistěte se, že jsou upozorněni, pokud zpráva se nepodaří doručit do cílové fronty. Můžete použít frontu nedoručených zpráv poskytované systémem nebo vlastní frontu nedoručených zpráv. Obecně platí pomocí vlastní frontu nedoručených zpráv je osvědčených vzhledem k tomu, že umožňuje odesílání zpráv nedoručených zpráv z jedné aplikace do jediné fronty nedoručených zpráv. Všechny zprávy nedoručených zpráv, ke kterým dochází pro všechny aplikace spuštěné v systému, jinak hodnota doručovány do jedné frontě. Každá aplikace musí ale vyhledávat frontu nedoručených zpráv najít nedoručených zpráv, které jsou relevantní pro tuto aplikaci. V některých případech pomocí vlastní frontu nedoručených zpráv není možné, například při použití služby MSMQ 3.0.  
  
 Vypnutí fronty nedoručených zpráv pro komunikaci spolehlivé začátku do konce se nedoporučuje.  
  
 Další informace najdete v tématu [pomocí fronty nedoručených zpráv pro zpracování chyb přenosu zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).  
  
### <a name="use-of-poison-message-handling"></a>Použití zpracování Poison zpráv  
 Zpracování zpráv Poison poskytuje možnost obnovení po selhání zpracování zpráv.  
  
 Když používáte funkci zpracování zpráv poison, ujistěte se, že <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> je nastavena na odpovídající hodnotu. Jeho nastavení na hodnotu <xref:System.ServiceModel.ReceiveErrorHandling.Drop> znamená data budou ztracena. Na druhé straně jeho nastavení na hodnotu <xref:System.ServiceModel.ReceiveErrorHandling.Fault> závady hostitele služby, když zjistí poškozená zpráva. Pomocí služby MSMQ 3.0 <xref:System.ServiceModel.ReceiveErrorHandling.Fault> je nejlepší možnost nedošlo ke ztrátě dat a přesuňte nezpracovatelná zpráva stranou. Pomocí služby MSMQ 4.0 <xref:System.ServiceModel.ReceiveErrorHandling.Move> se o doporučený postup. <xref:System.ServiceModel.ReceiveErrorHandling.Move> Přesune poškozená po zprávu z fronty, tak, aby služba můžou dál zpracovávat nové zprávy. Služba poison zpráva může pak zpracovat nezpracovatelná zpráva samostatně.  
  
 Další informace najdete v tématu [zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md).  
  
## <a name="achieving-high-throughput"></a>Dosahuje vysoké propustnosti  
 K dosažení vysoké propustnosti na jednom koncovém bodě, použijte tento příkaz:  
  
-   Transakční dávkování. Dávkové zajistí, že mnoho zpráv lze číst v rámci jedné transakce. Tím se optimalizuje potvrzení transakcí, zvýšit celkový výkon. Náklady na dávkování je, že pokud dojde k selhání do jedné zprávy v dávce, pak celý batch je vrácena zpět a zprávy musí být zpracovaná jeden po druhém, dokud je bezpečné batch znovu. Ve většině případů jsou taková situace vzácná, poškozených zpráv, takže dávkování je upřednostňovaný způsob, jak zvýšit výkon systému, zejména v případě, že máte další správci prostředků, které jsou součástí transakce. Další informace najdete v tématu [dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md).  
  
-   Souběžnosti. Concurrency zvyšuje propustnost, ale souběžnosti ovlivní také kolizí ke sdíleným prostředkům. Další informace najdete v tématu [souběžnosti](../../../../docs/framework/wcf/samples/concurrency.md).  
  
-   Omezení šířky pásma. Pro optimální výkon omezit počet zpráv v dispečeru kanálu. Příklad toho, jak to provést, naleznete v části [omezování](../../../../docs/framework/wcf/samples/throttling.md).  
  
 Při použití dávkování, mějte na paměti, že souběžnosti a omezování nepřeloží na souběžných dávky.  
  
 K dosažení vyšší propustnost a dostupnost, použijte farmu služby WCF, které čtou z fronty. To vyžaduje, aby všechny tyto služby vystavit stejné smlouvy na stejný koncový bod. Přístup farmy je nejvhodnější pro aplikace, které mají vysokou produkční počty zpráv, protože umožní několik služeb pro všechny číst ze stejné fronty.  
  
 Při použití farmy, mějte na paměti, že služby MSMQ 3.0 nepodporuje vzdálené zpracovaných čtení. MSMQ 4.0 podporuje vzdálené zpracovaných čtení.  
  
 Další informace najdete v tématu [dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md) a [rozdíly služby Řízení front funkcí v systému Windows Vista, Windows Server 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
## <a name="queuing-with-unit-of-work-semantics"></a>Služba Řízení front s jednotkou pracovní sémantiku  
 V některých případech může souviset skupinu zpráv ve frontě, a proto je důležité pořadí těchto zpráv. V takových případech zpracovat skupinu související zprávy společně jako jednu jednotku: buď všechny zprávy úspěšně zpracovat, nebo žádný. Chcete-li implementovat takové chování, použijte relace s fronty.  
  
 Další informace najdete v tématu [seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).  
  
## <a name="correlating-request-reply-messages"></a>Korelace zprávy požadavku a odpovědi  
 I když fronty jsou obvykle jednosměrné, v některých případech můžete chtít korelovat odpověď přijata na žádost odeslány dříve. Pokud budete potřebovat takové korelace, doporučujeme, abyste použili vlastní záhlaví zprávy protokolu SOAP, který obsahuje informace o korelace se zprávou. Obvykle odesílatel připojí tuto hlavičku se zprávou a příjemce při zpracování zprávy a odeslání odpovědi zpět s novou zprávu ve frontě s odpovědí, připojí záhlaví zprávy odesílatele, obsahující informace o korelace tak, aby odesílatel možné Identifikujte zprávu odpovědi s zprávu požadavku.  
  
## <a name="integrating-with-non-wcf-applications"></a>Integrace s aplikacemi bez WCF  
 Použití `MsmqIntegrationBinding` při integraci služby WCF nebo klientů s bez WCF služby nebo klientů. Aplikace bez WCF může být MSMQ aplikace napsané v System.Messaging modelu COM +, Visual Basic nebo C++.  
  
 Při použití `MsmqIntegrationBinding`, mít na paměti následující:  
  
-   Text zprávy WCF není stejný jako text zprávy služby MSMQ. Při odesílání zprávy WCF pomocí vazbu zařazených do fronty, tělo zprávy WCF je umístěn uvnitř zprávu služby MSMQ. Infrastruktura služby MSMQ je oblivious na tyto doplňující informace; se zobrazí pouze zprávy služby MSMQ.  
  
-   `MsmqIntegrationBinding` podporuje typy oblíbených serializace. Na základě serializace typu, typ těla zprávy obecné zprávy <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, používá jiný typ parametry. Například <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.ByteArray> vyžaduje `MsmqMessage\<byte[]>` a <xref:System.ServiceModel.MsmqIntegration.MsmqMessageSerializationFormat.Stream> vyžaduje `MsmqMessage<Stream>`.  
  
-   S serializace XML, můžete zadat pomocí známého typu `KnownTypes` atributu u [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element, který se pak použije k určení jak k deserializaci. zprávu XML.  
  
## <a name="see-also"></a>Viz také  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Postupy: Výměna zpráv zařazených do fronty s koncovými body WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Seskupování zpráv zařazených do fronty v relaci](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 [Dávkování zpráv v transakci](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 [Zpracování chyb přenosu zpráv pomocí front nedoručených zpráv](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 [Zpracování škodlivých zpráv](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Rozdíly ve funkcích zařazování do front ve Windows Vista, Windows Serveru 2003 a Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Zabezpečení zpráv pomocí zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Zabezpečení zpráv](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 [Řešení problémů se zasíláním zpráv zařazovaných do front](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)
