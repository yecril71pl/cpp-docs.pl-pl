---
title: A.18   Zagnieżdżenia dla dyrektyw
ms.date: 11/04/2016
ms.assetid: ae2b2e0b-ec94-43f8-928c-6d621b51f0df
ms.openlocfilehash: dbebcd88489c6fdb00011531e7b74b27ee154b4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554300"
---
# <a name="a18---nested-for-directives"></a>A.18   Zagnieżdżenia dla dyrektyw

Poniższy przykład `for` zagnieżdżanie dyrektywy ([2.9 sekcji](../../parallel/openmp/2-9-directive-nesting.md) na stronie 33) jest zgodne, ponieważ wewnętrznych i zewnętrznych `for` dyrektywy powiązać z różnych regionów równoległych:

```
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

Następujące zmiany powyższego przykładu jest również zgodne:

```
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```