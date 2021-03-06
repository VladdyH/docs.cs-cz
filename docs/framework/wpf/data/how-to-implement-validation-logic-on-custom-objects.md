---
title: 'Postupy: Implementace logiky ověření na vlastních objektech'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: dbeddb5eb6996d5758717ddd2d4d5af0b6f57f3c
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "33555961"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Postupy: Implementace logiky ověření na vlastních objektech
Tento příklad ukazuje způsob implementace logiky ověření na vlastní objekt a připojit se k němu.  
  
## <a name="example"></a>Příklad  
 V obchodní vrstvě můžete poskytnout logiku ověřování, pokud zdrojový objekt implementuje <xref:System.ComponentModel.IDataErrorInfo>, jako v následujícím příkladu, který definuje `Person` objekt, který implementuje <xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 V následujícím příkladu se vlastnost text textového pole vytvoří vazbu `Person.Age` vlastnosti, která je k dispozici pro vazbu prostřednictvím deklarace prostředků, která je přidělena `x:Key` `data`. <xref:System.Windows.Controls.DataErrorValidationRule> Kontroluje výskyt chyb ověření vyvoláno <xref:System.ComponentModel.IDataErrorInfo> implementace.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 Alternativně namísto použití <xref:System.Windows.Controls.DataErrorValidationRule>, můžete nastavit <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnost `true`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [Implementace ověření vazby](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
