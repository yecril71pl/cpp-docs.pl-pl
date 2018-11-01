---
title: 3.1.1 Funkcja omp_set_num_threads
ms.date: 11/04/2016
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
ms.openlocfilehash: 20b6b6ced2b4031696f1d019604842ae9b91bda2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663284"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 Funkcja omp_set_num_threads

`omp_set_num_threads` Funkcja ustawia domyślną liczbę wątków używanych na potrzeby kolejnych regionów równoległych, które nie określają `num_threads` klauzuli. Format jest następujący:

```
#include <omp.h>
void omp_set_num_threads(int num_threads);
```

Wartość parametru *num_threads* musi być dodatnią liczbą całkowitą. Jego efektem zależy od tego, czy włączona jest dynamiczne Dostosowywanie liczby wątków. Kompleksowy zbiór reguł o interakcji między `omp_set_num_threads` funkcji i dynamiczne Dostosowywanie wątków, patrz sekcja 2.3 na stronie 8.

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość zero. Jeśli zostanie wywołana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed `OMP_NUM_THREADS` zmiennej środowiskowej. Wartość domyślna liczba wątków, które mogą być ustanowione przez wywołanie metody `omp_set_num_threads` lub poprzez skonfigurowanie `OMP_NUM_THREADS` zmiennej środowiskowej, może być jawnie przesłonięte na pojedynczym **równoległe** dyrektywy, określając `num_threads` klauzuli.

## <a name="cross-references"></a>Odsyłacze:

- `omp_set_dynamic` funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.

- `omp_get_dynamic` funkcji, zobacz [sekcji 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) na stronie 40.

- `OMP_NUM_THREADS` Zobacz zmiennej środowiska [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48 i 2.3 sekcji na stronie 8.

- `num_threads` Klauzula, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8