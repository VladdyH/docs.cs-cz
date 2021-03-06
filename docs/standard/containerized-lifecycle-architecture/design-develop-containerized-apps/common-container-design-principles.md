---
title: Běžné zásady návrhu kontejneru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8aa388c7c19f532829d64208a48b6e556e43d802
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152874"
---
# <a name="common-container-design-principles"></a>Běžné zásady návrhu kontejneru

Dopředu získání do procesu vývoje existuje pár základních konceptů stojí za zmínku s ohledem na použití kontejnerů.

## <a name="container-equals-a-process"></a>Kontejner se rovná procesu

V kontejneru modelu kontejner představuje jeden proces. Definuje kontejner jako hranice procesu, začněte vytvářet primitivy používá k škálování, nebo vypnutí dávkové procesy. Při spuštění kontejneru Dockeru, zobrazí se vám [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#/entrypoint) definice. Definuje procesu a životnosti kontejneru. Po dokončení procesu kontejneru životní cyklus se ukončí. Dlouho běžící procesy, jako jsou webové servery a krátkodobou procesy, jako jsou dávkové úlohy, které mohou u je implementovaná jako Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Pokud proces selže, konce kontejneru a orchestrátor převezme. Pokud orchestrátoru dostal zachovat spuštěných 5 instancí a jeden server selže, vytvoří orchestrátoru jiný kontejner k nahrazení procesu, který selhal. V rámci úlohy služby batch je proces spuštěn s parametry. Po dokončení procesu je práce dokončena.

Může pro vás scénář, ve kterém chcete více procesů spuštěných ve jedním kontejnerem. V libovolném dokumentu architektura neexistuje nikdy "," ani není vždy na "always". Pro scénáře, které vyžadují více procesů, je použít běžný vzor [Supervisor](http://supervisord.org/).

>[!div class="step-by-step"]
>[Předchozí](design-docker-applications.md)
>[další](monolithic-applications.md)