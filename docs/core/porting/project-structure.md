---
title: Uspořádání projektů pro rozhraní .NET Framework a .NET Core
description: Nápovědu k projektu vlastníky, kteří chtějí kompilaci své řešení pro rozhraní .NET Framework a .NET Core side-by-side.
author: conniey
ms.date: 04/06/2017
ms.custom: seodec18
ms.openlocfilehash: 97673e1ccaeb094bf8c7cb835a84ae9389fac502
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169128"
---
# <a name="organize-your-project-to-support-both-net-framework-and-net-core"></a>Uspořádání vašeho projektu pro podporu rozhraní .NET Framework a .NET Core

Zjistěte, jak vytvořit řešení, které zkompiluje pro rozhraní .NET Framework a .NET Core – souběžně. Zobrazit několik možností, jak uspořádat projektech při dosažení tohoto cíle. Tady jsou některé typické scénáře, které je třeba zvážit, když jste rozhodování o tom, jak nastavit rozložení projektu s .NET Core. V seznamu nemusí zahrnovat všechno, co chcete, aby; prioritizujte podle potřeb vašeho projektu.

* [**Existující projekty a projekty .NET Core zkombinovat do jedné projekty**][option-csproj]

  *Co to platí pro:*
  * Zjednodušení procesu sestavení kompilaci jednoho projektu, spíše než sestavování více projektů, každý cílí na různé verze rozhraní .NET Framework nebo platformu.
  * Protože je třeba spravovat jediného souboru projektu, která zjednodušuje jejich správa zdrojového souboru pro více cílových projekty. Při přidávání nebo odebírání zdrojových souborů, alternativ vyžadují ruční synchronizaci těchto s vašimi projekty.
  * Snadno generování balíčku NuGet pro spotřebu.
  * Umožňuje napsat kód pro konkrétní verzi rozhraní .NET Framework ve vašich knihovnách pomocí direktivy kompilátoru.

  *Nepodporované scénáře:*
  * Vyžaduje, aby pomocí sady Visual Studio 2017 otevřete existující projekty vývojáři. Pro podporu starších verzích sady Visual Studio [uchovávání souborů projektu v různých složkách](#support-vs) je lepší volbou.

* <a name="support-vs"></a>[**Oddělovat existující projekty a nové projekty .NET Core**][option-csproj-folder]

  *Co to platí pro:*
  * Pokračování pro podporu vývoje na existující projekty bez nutnosti upgradu pro vývojáře/přispěvatele, kteří nemají Visual Studio 2017.
  * Snižuje možnost vytvářet nové chyby v existujících projektů, protože vyžaduje žádné změny kódu v těchto projektech.

## <a name="example"></a>Příklad

Vezměte v úvahu následující úložiště:

![Existující projekt][example-initial-project]

[**Zdrojový kód**][example-initial-project-code]

Následující část popisuje několik způsobů, jak přidat podporu pro .NET Core pro toto úložiště v závislosti na tom, omezení a složitosti existujících projektů.

## <a name="replace-existing-projects-with-a-multi-targeted-net-core-project"></a>Nahraďte existující projekty cílené více projektu .NET Core

Uspořádání úložiště tak, že všechny existující  *\*.csproj* soubory jsou odebrané a jednu  *\*.csproj* se vytvoří soubor, který cílí na více platforem. To je skvělá možnost, protože jednoho projektu je schopen kompilace pro různá rozhraní. Má také výkon pro zpracování různých kompilace možností a závislosti na cílové rozhraní.

![Vytvoření csproj, který cílí na více platforem][example-csproj]

[**Zdrojový kód**][example-csproj-code]

Všimněte si změny jsou:

* Nahrazení *souboru packages.config* a  *\*.csproj* s novou [.NET Core  *\*.csproj* ] [ example-csproj-netcore]. Balíčky NuGet jsou zadány s `<PackageReference> ItemGroup`.

## <a name="keep-existing-projects-and-create-a-net-core-project"></a>Zachovat existující projekty a vytvořte projekt .NET Core

Pokud je existující projekty, které jsou cíleny na starší rozhraní, můžete ponechat beze změny těchto projektů a používat projekt .NET Core pro budoucí platforem.

![Projekt .NET core s existující projekt do jiné složky][example-csproj-different-folder]

[**Zdrojový kód**][example-csproj-different-code]

Všimněte si změny jsou:

* Existující projekty .NET Core a jsou uchovávány v oddělených složek.
  * Udržování projektů do samostatné složky zabraňuje vynucení, abyste měli Visual Studio 2017. Můžete vytvořit samostatné řešení, které otevře pouze starých projektů.

## <a name="see-also"></a>Viz také

* Podrobnosti najdete [portování dokumentace k .NET Core] [ porting-doc] další pokyny k migraci až po .NET Core.

[porting-doc]: index.md
[example-initial-project]: media/project-structure/project.png "Existující projekt"
[example-initial-project-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library/

[example-csproj]: media/project-structure/project.csproj.png "Vytvoření souboru csproj, který cílí na více platforem"
[example-csproj-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/
[example-csproj-netcore]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj/src/Car/Car.csproj

[example-csproj-different-folder]: media/project-structure/project.csproj.different.png "Projekt .NET core s existující PCL do jiné složky"
[example-csproj-different-code]: https://github.com/dotnet/samples/tree/master/framework/libraries/migrate-library-csproj-keep-existing/

[option-csproj]: #replace-existing-projects-with-a-multi-targeted-net-core-project
[option-csproj-folder]: #keep-existing-projects-and-create-a-net-core-project
