---
title: A.28   Użycie klauzuli num_threads
ms.date: 11/04/2016
ms.assetid: 26238da1-902c-49b4-9559-0fbc9eaf7f36
ms.openlocfilehash: 99dd327d0a97f561107ffaa6a6ed1435e3772a41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492302"
---
# <a name="a28---use-of-numthreads-clause"></a>A.28   Użycie klauzuli num_threads

W poniższym przykładzie pokazano `num_threads` — klauzula ([2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8). Równoległego regionu jest wykonywane przy użyciu maksymalnie 10 wątków.

```
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```