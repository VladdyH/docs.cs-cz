---
title: Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET
description: Zjistěte, jak vypočítat metriky k vyhodnocení a ověření strojového učení modelu kvality pomocí ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149520"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a>Vypočítat metriky k vyhodnocení, machine learning model kvality - ML.NET

Jak při hodnocení kvality po trénování modelu? Každý úkol machine learning poskytuje metriky pro hodnocení kvality.

Odpovídající "kontextu" úlohy můžete použít k vyhodnocení modelu, jako v následujícím příkladu:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```