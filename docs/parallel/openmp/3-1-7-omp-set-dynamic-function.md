---
title: 3.1.7 Funkcja omp_set_dynamic
ms.date: 11/04/2016
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
ms.openlocfilehash: 641b2ecfdb19aec9387aa299d22a041f25b22929
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492940"
---
# <a name="317-ompsetdynamic-function"></a>3.1.7 Funkcja omp_set_dynamic

**Omp_set_dynamic** funkcji włącza lub wyłącza dynamiczne Dostosowywanie liczby dostępnych do wykonania regionów równoległych wątków. Format jest następujący:

```
#include <omp.h>
void omp_set_dynamic(int dynamic_threads);
```

Jeśli *dynamic_threads* oblicza wartość różną od zera, liczba wątków, które są używane do wykonywania kolejnych regionów równoległych mogą być automatycznie dostosowywane przez środowisko wykonawcze najlepsze wykorzystanie zasobów systemowych. W konsekwencji liczbę wątków, określone przez użytkownika jest maksymalnej liczby wątków. Liczba wątków w zespole wykonywania równoległego regionu pozostaje stały czas trwania tego równoległego regionu i zgłoszonych przez **omp_get_num_threads** funkcji.

Jeśli *dynamic_threads* ocenia 0, dynamiczne Dostosowywanie jest wyłączona.

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość zero. Jeśli zostanie wywołana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

Wywołanie **omp_set_dynamic** ma pierwszeństwo przed **OMP_DYNAMIC** zmiennej środowiskowej.

Wartość domyślna dla dynamicznego dostosowania wątków jest zdefiniowane w implementacji. W rezultacie kody użytkownika, które są zależne od określonej liczby wątków do wykonania poprawne jawnie Wyłącz dynamiczne wątków. Implementacje nie są wymagane, aby zapewnić możliwość dynamicznego dostosowania liczby wątków, ale są wymagane, zapewniając interfejs w celu obsługi przenoszenia na wszystkich platformach.

## <a name="cross-references"></a>Odsyłacze:

- **omp_get_num_threads** funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.

- **OMP_DYNAMIC** środowiska zmiennych, zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49.

- **omp_in_parallel** funkcji, zobacz [sekcji 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stronie 38.