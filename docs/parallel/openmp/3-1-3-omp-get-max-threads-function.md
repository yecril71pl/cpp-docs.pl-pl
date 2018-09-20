---
title: 3.1.3 funkcja omp_get_max_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5548897c-546e-4d19-b37b-a76f6b30a0a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c439dc0203fa3435c62e9669da40b5b092556492
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400825"
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