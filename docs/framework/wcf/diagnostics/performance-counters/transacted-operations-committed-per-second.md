---
title: Počet potvrzených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856319"
---
# <a name="transacted-operations-committed-per-second"></a>Počet potvrzených zpracovaných operací za sekundu
Název čítače: Počet potvrzených zpracovaných operací za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakční operace, které byly v této službě potvrzen za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
