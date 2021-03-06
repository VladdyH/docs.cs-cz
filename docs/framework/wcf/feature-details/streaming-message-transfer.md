---
title: Streamování přenosu zpráv
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: 340c903e2cb34373514ea2f739cab57dc620df5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499138"
---
# <a name="streaming-message-transfer"></a>Streamování přenosu zpráv
Přenosy Windows Communication Foundation (WCF) podporují dva režimy pro přenos zpráv:  
  
-   Ve vyrovnávací paměti přenosy uložení celé zprávy vyrovnávací paměť v až do dokončení přenosu. Zprávu ve vyrovnávací paměti musí být zcela doručována předtím, než příjemce může číst.  
  
-   Přenášené datovými proudy přenosy vystavit zprávu jako datový proud. Příjemce spustí, než je zcela doručit zpracování zprávy.  
  
-   Přenášené datovými proudy přenosy může zlepšit škálovatelnost služby odstraněním požadavek pro velké paměti vyrovnávací paměti. Zda změna režimu přenosu zlepšuje škálovatelnost, závisí na velikosti přenášených zpráv. Velké zpráva velikosti upřednostnit pomocí přenášené datovými proudy přenosů.  
  
 Ve výchozím nastavení používají ve vyrovnávací paměti přenosy HTTP, TCP/IP a přenosy pojmenovaný kanál. Tento dokument popisuje, jak přepínat těchto přenosů z ve vyrovnávací paměti pro režim přenosu přenášené datovými proudy a důsledky tak.  
  
## <a name="enabling-streamed-transfers"></a>Povolení přenášené datovými proudy přenosů  
 Výběr mezi režimy ve vyrovnávací paměti a přenášené datovými proudy přenos se provádí u prvku vazby přenosu. Obsahuje prvku vazby <xref:System.ServiceModel.TransferMode> vlastnost, která může být nastaven na `Buffered`, `Streamed`, `StreamedRequest`, nebo `StreamedResponse`. Nastavení režimu přenosu `Streamed` umožňuje streamování komunikace v obou směrech. Nastavení režimu přenosu `StreamedRequest` nebo `StreamedResponse` umožňuje streamování komunikace v uvedeném směru.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, A <xref:System.ServiceModel.NetNamedPipeBinding> zveřejněte vazby <xref:System.ServiceModel.TransferMode> vlastnost. Pro ostatní přenosy musíte vytvořit vlastní vazby nastavit režim přenosu.  
  
 Rozhodnutí použít ve vyrovnávací paměti nebo přenášené datovými proudy přenosy je místní rozhodnutí koncového bodu. Pro přenosy protokolu HTTP režim přenosu nešířily přes připojení nebo na servery a jiných zprostředkovatelů. Nastavení režimu přenosu se nereflektují v popisu rozhraní služby. Po generování třídy klienta pro službu, musíte upravit konfigurační soubor pro služby určena pro použití s přenášené datovými proudy přenosy nastavení režimu. TCP a přenosy pojmenovaný kanál režim přenosu rozšířena jako výraz zásad.  
  
 Ukázky kódu, najdete v části [postupy: povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Povolení asynchronní datové proudy  
 Chcete-li povolit asynchronní streamování, přidejte <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> chování koncového bodu do hostitele služby a nastavte její <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> vlastnost `true`.  
  
 Tato verze služby WCF také adde možnosti true asynchronní streamování na straně odeslání. To zlepšuje škálovatelnost služby ve scénářích, kde ji je streamování zprávy na více klientů, z nichž některé jsou pomalé v režimu čtení; pravděpodobně z důvodu zahlcení sítě nebo jsou není čtení vůbec. V těchto scénářích WCF už blokuje jednotlivých vláken ve službě za klienta. Tím se zajistí, že služba je schopna zpracovat mnoho více klientů a zlepšení škálovatelnosti služby.  
  
## <a name="restrictions-on-streamed-transfers"></a>Omezení přenášené datovými proudy převodů  
 Pomocí režimu přenášené datovými proudy přenos způsobí, že čas spuštění vynutit další omezení.  
  
 Operace, které napříč přenášené datovými proudy přenosu může mít kontrakt s maximálně jeden vstupní nebo výstupní parametr. Tento parametr odpovídá celý text zprávy a musí být <xref:System.ServiceModel.Channels.Message>, odvozený typ <xref:System.IO.Stream>, nebo <xref:System.Xml.Serialization.IXmlSerializable> implementace. S návratovou hodnotou pro operace je ekvivalentní s výstupní parametr.  
  
 Některé funkce WCF, například spolehlivého zasílání zpráv a transakce a zabezpečení na úrovni zprávu protokolu SOAP, spoléhají na ukládání do vyrovnávací paměti zpráv pro přenosy. Používání těchto funkcí může omezit nebo odstranit výkonu výhody pomocí vysílání datového proudu. K zabezpečení přenášené datovými proudy přenosu, použijte pouze zabezpečení na úrovni přenosu nebo použijte zabezpečení transportní vrstvy a zabezpečení jen ověřování zpráv.  
  
 Hlavičky SOAP jsou vždy do vyrovnávací paměti, i když přenos režim je nastaven na přenášené datovými proudy. Hlavičky pro zprávu nesmí překročit velikost `MaxBufferSize` kvóty přenosu. Další informace o tomto nastavení najdete v tématu [přenosové kvóty](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Rozdíly mezi přenosy ve vyrovnávací paměti a přenášené datovými proudy  
 Změna režimu přenosu z vyrovnávací paměti pro streamování také změní tvar nativní kanálu TCP a přenosy pojmenovaný kanál. Pro přenosy ve vyrovnávací paměti, je tvar nativní kanálu <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. Pro přenášené datovými proudy přenosy jsou nativní kanály <xref:System.ServiceModel.Channels.IRequestChannel> a <xref:System.ServiceModel.Channels.IReplyChannel>. Změna režimu přenosu v existující aplikaci, která používá tyto přenosy, přímo (tedy ne prostřednictvím smlouvy o poskytování služeb) vyžaduje změna tvaru očekávané kanál pro kanál továrny a naslouchací procesy.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Povolení streamování](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
