---
title: A.3   Użycie regionów równoległych
ms.date: 11/04/2016
ms.assetid: 575216a1-960a-47f7-9c82-7f660291fcfe
ms.openlocfilehash: 573c4f7c47c90bc6d567c4640360aa6abee5a48c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458997"
---
# <a name="a3---using-parallel-regions"></a>A.3   Użycie regionów równoległych

`parallel` — Dyrektywa ([2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8) mogą być używane w zgrubnym ziarna programów do równoległego przetwarzania. W poniższym przykładzie każdy wątek w równoległego regionu decyduje, jaka część globalnej tablicy `x` do pracy, na podstawie liczby wątków:

```
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```