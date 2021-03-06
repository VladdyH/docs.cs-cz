---
title: Ochrana osobních údajů a zabezpečení dat
ms.date: 03/30/2017
ms.assetid: 46fa5839-adf7-4c7c-bce3-71e941fa7de9
ms.openlocfilehash: 078b5e09e800511c3edfa78596b5bdb67ebcc6d7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194927"
---
# <a name="privacy-and-data-security"></a>Ochrana osobních údajů a zabezpečení dat
Zabezpečení a správa citlivých informací v aplikaci ADO.NET je závislá na základní produkty a technologie používané k jeho vytvoření. ADO.NET neposkytuje služby pro zabezpečení nebo šifrování dat přímo.  
  
## <a name="cryptography-and-hash-codes"></a>Šifrování a Hash kódy  
 Třídy v rozhraní .NET Framework <xref:System.Security.Cryptography> obor názvů je možné z vašich aplikací ADO.NET Chcete-li zabránit číst nebo upravovat neoprávněné třetími stranami. Některé třídy jsou obálky pro nespravované CryptoAPI Microsoft jiné spravované implementace. [Šifrovacím službám](../../../../docs/standard/security/cryptographic-services.md) téma obsahuje základní informace o kryptografických služeb v rozhraní .NET Framework, popisuje, jak je implementovaná cryptograph a jak můžou provádět konkrétní šifrovací úlohy.  
  
 Na rozdíl od šifrování, což umožňuje dat zašifrován a potom dešifrován, generování hodnoty hash dat je jednosměrný proces. Algoritmus hash dat je užitečné, pokud chcete zabránit manipulaci tak, že zkontrolujete, že data nikdo nezměnil: Zadaný vstupní řetězce stejné, algoritmy hash vždy vytvořila identické krátký výstupní hodnoty, které lze snadno porovnat. [Zajištění Integrity dat pomocí hodnot hash](../../../../docs/standard/security/ensuring-data-integrity-with-hash-codes.md) popisuje, jak můžete vytvořit a ověřit hash hodnoty.  
  
## <a name="encrypting-configuration-files"></a>Šifrování konfiguračních souborů  
 Zabezpečení přístupu ke zdroji dat je jedním z nejdůležitějších cílů při zabezpečování aplikace. Připojovací řetězec představuje potenciální ohrožení zabezpečení, není-li zabezpečena. Připojovací řetězce, které jsou uloženy v konfiguračních souborech jsou uloženy v standardní soubory XML, pro které má definované rozhraní .NET Framework společnou sadu elementů. Chráněné konfigurace umožňuje šifrování citlivých informací v konfiguračním souboru. I když primárně určený pro aplikace ASP.NET, chráněné konfigurace lze také k šifrování souborů konfigurační oddíly funkce v aplikacích Windows. Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="securing-string-values-in-memory"></a>Zabezpečení řetězcové hodnoty v paměti  
 Pokud <xref:System.String> objekt obsahuje citlivé informace, jako jsou hesla, číslo platební karty nebo osobní údaje, existuje riziko, že informace může být odhalena po se používá, protože aplikace nemůže odstranit data v paměti počítače.  
  
 A <xref:System.String> je neměnný; jeho hodnotu nelze změnit po vytvoření. Změny, které patrně upravují řetězcové hodnoty ve skutečnosti vytvořit novou instanci třídy <xref:System.String> objektu v paměti, ukládání dat jako prostý text. Kromě toho není možné předpovědět, kdy se odstraní instance řetězce z paměti. Recyklace paměti s řetězci není deterministický. s uvolňování paměti .NET. Byste neměli používat <xref:System.String> a <xref:System.Text.StringBuilder> třídy, pokud je skutečně citlivá data.  
  
 <xref:System.Security.SecureString> Třída poskytuje metody pro šifrování textu s použitím Data Protection API (DPAPI) v paměti. Řetězec je pak odstraněn z paměti, pokud už je nepotřebujete. Neexistuje žádná `ToString` metoda rychle přečíst obsah <xref:System.Security.SecureString>. Můžete inicializovat novou instanci třídy `SecureString` bez hodnot nebo předání ukazatele na pole <xref:System.Char> objekty. Můžete pak použít různé metody třídy pro práci s řetězci. Další informace, stáhněte si [SecureString ukázkovou aplikaci](https://go.microsoft.com/fwlink/?LinkId=120418), které ukazuje, jak používat `SecureString` třídy z.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení aplikací ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server – zabezpečení](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
