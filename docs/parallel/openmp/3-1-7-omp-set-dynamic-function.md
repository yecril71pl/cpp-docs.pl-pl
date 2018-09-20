---
title: 3.1.7 funkcja omp_set_dynamic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 1fba961b-b82c-4a1e-ab0f-e4be826e50ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 807e5739c571f7aa8e9f723a0a48c8c46f1e6d09
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441567"
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