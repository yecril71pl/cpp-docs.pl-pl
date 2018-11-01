---
title: 4.2 OMP_NUM_THREADS
ms.date: 11/04/2016
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
ms.openlocfilehash: 88ddfc226b8ae905e026e2f0979e07581d1ae83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668212"
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

**OMP_NUM_THREADS** zmiennej środowiskowej ustawia domyślną liczbę wątków używanych w czasie wykonywania, chyba że ten numer jest jawnie zmieniona przez wywołanie metody **omp_set_num_threads** procedury biblioteki lub przez jawną **num_threads** klauzuli w **równoległe** dyrektywy.

Wartość **OMP_NUM_THREADS** zmiennej środowiskowej musi być dodatnią liczbą całkowitą. Jego efektem zależy od tego, czy włączona jest dynamiczne Dostosowywanie liczby wątków. Aby uzyskać kompleksowy zestaw reguł o interakcji między **OMP_NUM_THREADS** środowiska zmiennych i dynamicznego dostosowania wątków, patrz sekcja 2.3 na stronie 8.

Jeśli nie określono wartości dla **OMP_NUM_THREADS** zmiennej środowiskowej, lub jeśli określona wartość nie jest dodatnią liczbą całkowitą, jeśli wartość jest większa niż maksymalna liczba wątków system może obsługiwać, liczbę wątków używanych jest zdefiniowane w implementacji.

Przykład:

```
setenv OMP_NUM_THREADS 16
```

## <a name="cross-references"></a>Odsyłacze:

- **num_threads** klauzuli, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.

- **omp_set_num_threads** funkcji, zobacz [sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36.

- **omp_set_dynamic** funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.