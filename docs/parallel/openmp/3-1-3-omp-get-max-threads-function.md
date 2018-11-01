---
title: 3.1.3 Funkcja omp_get_max_threads
ms.date: 11/04/2016
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
ms.openlocfilehash: 3f954b5ad75b4bdb4a74323f2ab4e819850269ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50546594"
---
# <a name="313-ompgetmaxthreads-function"></a>3.1.3 Funkcja omp_get_max_threads

**Omp_get_max_threads** funkcji zwraca liczbę całkowitą, która może być przynajmniej tak duże jak liczba wątków, które byłyby używane do utworzenia zespołu, jeśli równoległego regionu bez **num_threads** — klauzula były występujących w tym momencie w kodzie. Format jest następujący:

```
#include <omp.h>
int omp_get_max_threads(void);
```

Następujące określa dolną granicę dla wartości **omp_get_max_threads**:

```

threads-used-for-next-team
<= omp_get_max_threads

```

Należy pamiętać, że jeśli korzysta z kolejnych równoległego regionu **num_threads** klauzuli żądania określoną liczbę wątków, gwarancji na dolnej granicy wynik **omp_get_max_threads** nie przechowuje długie.

**Omp_get_max_threads** wartość zwracaną przez funkcję można dynamicznie przydzielić wystarczającej ilości miejsca dla wszystkich wątków w zespole na kolejne równoległego regionu.

## <a name="cross-references"></a>Odsyłacze:

- **omp_get_num_threads** funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.

- **omp_set_num_threads** funkcji, zobacz [sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36.

- **omp_set_dynamic** funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.

- **num_threads** klauzuli, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.