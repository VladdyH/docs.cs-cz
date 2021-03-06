---
title: příkaz DotNet add příkaz balíčku
description: Příkaz "se příkaz dotnet add package" poskytuje vhodnou možnost Přidat odkaz na balíček NuGet do projektu.
ms.date: 12/04/2018
ms.openlocfilehash: 159b208feafb82e267629ea47dcef02d6b575055
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169999"
---
# <a name="dotnet-add-package"></a>příkaz DotNet add package

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet add package` -Přidá odkaz na balíček do souboru projektu.

## <a name="synopsis"></a>Souhrn

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Popis

`dotnet add package` Příkaz poskytuje vhodnou možnost Přidat odkaz na balíček do souboru projektu. Po spuštění příkazu je kontrolu kompatibility a ujistěte se, že balíček je kompatibilní s architekturami, které v projektu. Pokud je kontrola proběhne úspěšně, `<PackageReference>` element je přidat do souboru projektu a [dotnet restore](dotnet-restore.md) běží.

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Například přidáním `Newtonsoft.Json` k *ToDo.csproj* vytváří výstup podobný následujícímu příkladu:

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

*ToDo.csproj* nyní obsahuje soubor [ `<PackageReference>` ](/nuget/consume-packages/package-references-in-project-files) – element pro odkazované balíčku.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Určuje soubor projektu. Pokud není zadán, příkaz vyhledá v aktuálním adresáři pro jeden.

* **`PACKAGE_NAME`**

  Odkaz na balíček pro přidání.

## <a name="options"></a>Možnosti

* **`-f|--framework <FRAMEWORK>`**

  Přidá odkaz na balíček pouze v případě cílení na konkrétní [framework](../../standard/frameworks.md).

* **`-h|--help`**

  Vytiskne krátký nápovědy pro příkaz.

* **`--interactive`**

  Povoluje příkazu zastavit a počkat na vstup uživatele nebo akci (třeba k dokončení ověřování). Dostupné od verze rozhraní .NET Core 2.1 SDK verze 2.1.400 nebo novější.

* **`-n|--no-restore`**

  Přidá odkaz na balíček bez provedení kontroly obnovení ve verzi preview a kompatibility.

* **`--package-directory <PACKAGE_DIRECTORY>`**

  Obnoví balíčku do zadaného adresáře.

* **`-s|--source <SOURCE>`**

  Během operace obnovení používá konkrétní zdroj balíčku NuGet.

* **`-v|--version <VERSION>`**

  Verze balíčku.

## <a name="examples"></a>Příklady

* Přidat `Newtonsoft.Json` balíček NuGet do projektu:

  ```console
  dotnet add package Newtonsoft.Json
  ```

* Přidání konkrétní verzi balíčku do projektu:

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* Přidání balíčku pomocí konkrétního zdroje NuGet:

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```