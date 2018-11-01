---
title: A.5   Użycie dyrektywy krytycznej
ms.date: 11/04/2016
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
ms.openlocfilehash: 82497d63acc057fbbcf26f585e42fc8611c08ec4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545110"
---
# <a name="a5---using-the-critical-directive"></a>A.5   Użycie dyrektywy krytycznej

Poniższy przykład zawiera kilka `critical` dyrektywy ([sekcji 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stronie 18). W przykładzie pokazano kolejkowania modelu, w którym zadanie jest usuwane z kolejki i pracuje. Aby zabezpieczyć się przed wiele wątków tego samego zadania usuwania z kolejki, operacji usuwania z kolejki musi należeć do `critical` sekcji. Ponieważ dwie kolejki w tym przykładzie są niezależne, są chronione przez `critical` dyrektywy pod różnymi nazwami *liczbowa* i *yaxis*.

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```