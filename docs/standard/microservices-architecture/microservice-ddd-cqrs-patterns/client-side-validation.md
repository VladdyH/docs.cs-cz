---
title: Ověřování na straně klienta (ověřování v prezentačních vrstvách)
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Seznamte se s klíčové koncepty ověřování na straně klienta.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 3ec8ca932924c1b1b6750dd30750e3c1e56b7538
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130075"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Ověřování na straně klienta (ověřování v prezentačních vrstvách)

I v případě, že je zdroj pravdivých informací doménový model a nakonec musí mít ověření na úrovni modelu domény, můžete ověření dosud zpracovány na úrovni modelu domény (na straně serveru) a uživatelského rozhraní (na straně klienta).

Ověřování na straně klienta je skvělé usnadnění práce pro uživatele. To šetří čas, který byste jinak strávili čekání na odezvu na server, který může vrátit chyby ověření. V obchodní termíny dokonce i pár zlomky sekund vynásobené opakovaném každý den dohromady tvoří spoustu času, expense a frustrace. Jednoduché a okamžité ověřování umožňuje uživatelům vyšší efektivity práce a vytvářet lepší kvalitu vstupu a výstupu.

Stejně jako model zobrazení a modelu domény se liší, ověření modelu zobrazení a ověření modelu domény může být podobné, ale pro jiný účel. Pokud máte obavy o zkušební (není opakujte sami zásada), vezměte v úvahu, že v tomto případě opakované využívání kódu může také znamenat párování a v oddílu podnikové aplikace je více důležité, abyste na straně klienta než postupujte podle principu suchého spárovat na straně serveru.

I při použití ověřování na straně klienta, by měla vždy ověřování příkazům nebo vstupní DTO v serverovém kódu, protože server rozhraní API jsou možné útoku. Provádění obou je obvykle nejlepší tip vzhledem k tomu, že pokud máte klientské aplikace z pohledu uživatelského prostředí, je nejlepší a provádět proaktivně, aby uživatel zadal neplatné informace.

Proto v kódu na straně klienta je obvykle ověřit modely ViewModel. Může také ověřit klienta výstup DTO nebo příkazy před jejich odesláním do služby.

Implementace ověřování na straně klienta, závisí na druhu klientskou aplikaci, kterou vytváříte. Bude jiný, jsou ověřování dat ve webovém webové aplikace MVC s největším počtem kód v .NET, webové aplikace SPA pomocí tohoto ověřování je zakódovaný v jazyce JavaScript nebo TypeScript, nebo kódované mobilní aplikace pomocí Xamarinu a C#.

## <a name="additional-resources"></a>Další zdroje

### <a name="validation-in-xamarin-mobile-apps"></a>Ověření v mobilních aplikacích Xamarin

- **Ověření textový vstup a zobrazit chyby** \
  [*https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

- **Zpětné volání pro ověření** \
  [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Ověření v aplikacích ASP.NET Core

- **Rick Anderson. Přidání ověřování** \
  [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Ověřování do aplikace SPA webové aplikace (Angular 2, TypeScript, JavaScript)

- **ADO Kukic. Ověřování angular 2 formuláře** \
  [*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

- **Ověření formuláře** \
  [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

- **Ověření.** Dokumentace k podrobným. \
  [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

Stručně řečeno jedná se ty nejdůležitější koncepty související s ověření:

- Entity a agregace by měl vynutit vlastní konzistenci a "vždy platný". Agregační kořeny zodpovídají za víc entitami konzistenci v rámci stejné agregace.

- Pokud se domníváte, že entita musí zadat neplatném stavu, zvažte použití jiného objektu modelu, například pomocí dočasný objekt DTO, dokud nevytvoříte entita domény posledním.

- Pokud je potřeba vytvořit několik souvisejících objektů, jako jsou agregace, a že jsou platné jenom po jejich vytvoření, zvažte použití vzoru objekt pro vytváření.

- Ve většině případů redundantní ověřování na straně klienta je dobré, vzhledem k tomu, že aplikace může být aktivní.

>[!div class="step-by-step"]
>[Předchozí](domain-model-layer-validations.md)
>[další](domain-events-design-implementation.md)