---
title: A.23   Przykłady dyrektyw uporządkowanych
ms.date: 11/04/2016
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
ms.openlocfilehash: 2868b771fd57613981f3c6458b48493a1b26eee4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472283"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Przykłady dyrektyw uporządkowanych

Istnieje możliwość mają wiele uporządkowanych sekcje z `for` określenia `ordered` klauzuli. Pierwszy przykład jest niezgodne, ponieważ interfejs API określa następujące czynności:

"Iteracji pętli za pomocą `for` konstrukcja nie należy wykonać takie same `ordered` dyrektywy więcej niż jeden raz, a nie musisz wykonać więcej niż jedną `ordered` dyrektywy." (Zobacz [sekcji 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stronie 22)

W tym przykładzie niezgodnych wszystkich iteracji, wykonaj 2 uporządkowane sekcje:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

W poniższym przykładzie zgodne przedstawiono `for` z więcej niż jednym uporządkowane sekcji:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```