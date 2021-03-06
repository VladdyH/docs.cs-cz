---
title: 'Postupy: Vytvoření jednosměrného kontraktu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85084cd9-31cc-4e95-b667-42ef01336622
ms.openlocfilehash: 80cab35b14dd3b7663405038f2afdea362cdb792
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490770"
---
# <a name="how-to-create-a-one-way-contract"></a>Postupy: Vytvoření jednosměrného kontraktu
Toto téma ukazuje základní kroky pro vytvoření metody, které používají jednosměrného kontraktu. Tyto metody vyvolání operací ve službě Windows Communication Foundation (WCF) od klienta, ale Nečekejte na odpověď. Tento typ smlouvy můžete použít například k publikování oznámení pro mnoho odběratele. Jednosměrné kontrakty můžete také použít při vytváření duplexního kontraktu (obousměrné), která umožňuje klientům a serverům ke komunikaci mezi sebou nezávisle tak, aby buď můžete spustit volání na druhý. Můžete to umožní na konkrétní server jednosměrný volání klientovi, který klient může považovat za události. Podrobné informace o zadávání jednosměrné metody najdete v tématu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost a <xref:System.ServiceModel.OperationContractAttribute> třídy.  
  
 Další informace o vytváření klientskou aplikaci pro duplexního kontraktu najdete v tématu [postupy: přístup ke službě pomocí jednosměrných kontraktů a kontraktů požadavek-odpověď](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md). Ukázku práce, najdete [jednosměrný](../../../../docs/framework/wcf/samples/one-way.md) ukázka.  
  
### <a name="to-create-a-one-way-contract"></a>K vytvoření jednosměrného kontraktu  
  
1.  Vytvoření kontrakt služby s použitím <xref:System.ServiceModel.ServiceContractAttribute> třídy rozhraní, které definuje metody, služba je k implementaci.  
  
2.  Označuje, které metody v rozhraní klienta můžete vyvolat použití <xref:System.ServiceModel.OperationContractAttribute> třída k nim.  
  
3.  Určit operace, které musí mít žádný výstup (žádnou návratovou hodnotu a žádné na víc systémů nebo parametry ref) jako jednosměrný nastavením <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true`. Všimněte si, že operace, která provádění <xref:System.ServiceModel.OperationContractAttribute> třída splnit kontraktu požadavku a odpovědi ve výchozím nastavení, protože <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost je `false` ve výchozím nastavení. Proto je nutné explicitně zadat hodnotu atributu vlastnost, která má být `true` Pokud chcete pro metodu jednosměrného kontraktu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje kontrakt služby, který obsahuje několik metod, jednosměrná. Všechny metody mít jednosměrné kontrakty s výjimkou `Equals`, který použije se výchozí hodnota požadavku a odpovědi a vrátí výsledek.  
  
 [!code-csharp[S_Service_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Postupy: Definování kontraktu služby](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [Relace](../../../../docs/framework/wcf/samples/session.md)  
 [Postupy: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
