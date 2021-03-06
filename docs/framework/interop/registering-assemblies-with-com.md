---
title: Registrování sestav pomocí modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92f36488dec113dcffffac3e6cdc0c26a690b5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389158"
---
# <a name="registering-assemblies-with-com"></a>Registrování sestav pomocí modelu COM
Můžete spustit nástroj příkazového řádku volat [nástroj pro registraci sestavení (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) k registraci nebo zrušení registrace sestavení pro použití v modelu COM. RegAsm.exe informace o třídě přidá do registru systému, klienti COM můžete použít třídu rozhraní .NET Framework transparentně. <xref:System.Runtime.InteropServices.RegistrationServices> Třída poskytuje ekvivalentní funkce.  
  
 Spravované součásti musí být zaregistrován v registru systému Windows, než je možné aktivovat z COM klienta. V následující tabulce jsou uvedeny klíčů, které Regasm.exe obvykle přidá do registru systému Windows. (000000 znamená skutečná hodnota GUID.)  
  
|GUID|Popis|Klíč registru|  
|----------|-----------------|------------------|  
|CLSID|Identifikátor třídy|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Identifikátor rozhraní|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|ID KNIHOVNY|Identifikátor knihovny|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|Programový identifikátor|HKEY_CLASSES_ROOT\000…000|  
  
 V části HKCR\CLSID\\{0000... 0000} klíč, výchozí hodnota je nastavena na ProgID třídy a přidají dva nové pojmenovaných hodnot, třídy a sestavení. Modul runtime čte hodnotu sestavení z registru a předá je do překladač sestavení za běhu. Překladač sestavení se pokusí najít sestavení, na základě informací o sestavení, jako je například číslo název a verze. Sestavení pro překladač sestavení, který se má najít sestavení, musí být v jednom z následujících umístění:  
  
-   Globální mezipaměti sestavení (musí být sestavení se silným názvem).  
  
-   V adresáři aplikace. Sestavení ze cesta aplikace načíst jsou přístupné z této aplikace jenom.  
  
-   Společně cesta k souboru zadaným **/ codebase** možnost Regasm.exe.  
  
 RegAsm.exe také vytvoří klíč InProcServer32 pod HKCR\CLSID\\{0000... 0000} klíč. Výchozí hodnota pro klíč nastavena na název knihovny DLL, která inicializuje modul common language runtime (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Ověření položky registru  
 Zprostředkovatel komunikace s objekty COM poskytuje objekt pro vytváření implementaci standardní třídy pro vytvoření instance libovolné třídy rozhraní .NET Framework. Klienti mohou volat **DllGetClassObject** na spravovanou knihovnu DLL získat objekt pro vytváření tříd a vytvořit objekty, stejně jako jakoukoli jinou součástí modelu COM.  
  
 Pro `InprocServer32` podklíč, zobrazí se odkaz na Mscoree.dll místo tradiční knihovny typů COM indikující, že modul common language runtime vytvoří spravovaného objektu.  
  
## <a name="see-also"></a>Viz také  
 [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)  
 [Postupy: Odkazování na typy .NET z modelu COM](how-to-reference-net-types-from-com.md)  
 [Volání metody objekt .NET.](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))  
 [Nasazení aplikace pro přístup COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
