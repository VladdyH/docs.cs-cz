---
title: Vytvoření třídy GamePieceCollection
ms.date: 03/30/2017
ms.assetid: e4b037ee-1201-4a55-b198-0d6532ed6f35
ms.openlocfilehash: 0a39ca479e9b370b027fcec4bcf76996e6191296
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190577"
---
# <a name="creating-the-gamepiececollection-class"></a>Vytvoření třídy GamePieceCollection
**GamePieceCollection** třídy je odvozen z obecného seznamu třídy a zavádí metody snadněji spravovat více **GamePiece** objekty.  
  
## <a name="creating-the-code"></a>Vytváření kódu  
 Konstruktor třídy **GamePieceCollection** třídy inicializuje soukromému členu *capturedIndex*. Toto pole se používá ke sledování který her kusů má v současné době zachycení myši.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_PrivateMembersAndConstructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_privatemembersandconstructor)]  
  
 **ProcessInertia** a **nakreslit** metody zjednodušit kód, který je potřeba v hry [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) a [Game.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metody výčet všech kameny v kolekci a voláním příslušné metody v každém **GamePiece** objektu.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_ProcessInertiaAndDraw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_processinertiaanddraw)]  
  
 **UpdateFromMouse** metoda se také nazývá během hry aktualizace. Umožňuje pouze jednu část her mít myši zachytit nejdřív zkontrolovali, jestli aktuální snímek (pokud existuje) je stále v platnosti. Pokud ano, žádná část je povolen pro zachycení.  
  
 Pokud žádná část má v současné době zachycení, **UpdateFromMouse** metoda výčet každého jednotlivého her od poslední první, a kontroluje, pokud danou částí sestavy myši zachycení. Pokud ano, tuto část stane aktuální zachycené část a žádné další zpracování probíhá. **UpdateFromMouse** metoda zkontroluje poslední položky v kolekci nejprve tak, že pokud jsou dva kusy overlapped, s vyšší pořadí vykreslování obdrží zachytávání. Pořadí vykreslování není explicitní ani změnit; se řídí jednoduše tak, že pořadí, ve kterém byly přidány kameny do kolekce.  
  
 [!code-csharp[ManipulationXNA#_GamePieceCollection_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiececollection.cs#_gamepiececollection_updatefrommouse)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
 [Vytvoření třídy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
 [Výpis úplného kódu](../../../docs/framework/common-client-technologies/full-code-listings.md)
