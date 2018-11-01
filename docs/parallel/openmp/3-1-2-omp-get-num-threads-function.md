---
title: 3.1.2 Funkcja omp_get_num_threads
ms.date: 11/04/2016
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
ms.openlocfilehash: 587b49f70896bcfe8c1a805a4ebb13a11e9bb7d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50465250"
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 Funkcja omp_get_num_threads

**Omp_get_num_threads** funkcja zwraca liczbę wątków obecnie w zespole wykonywania równoległego regionu, w którym jest wywoływana. Format jest następujący:

```
#include <omp.h>
int omp_get_num_threads(void);
```

**Num_threads** klauzuli **omp_set_num_threads** funkcji i **OMP_NUM_THREADS** zmiennej środowiskowej kontrolować liczbę wątków w zespole.

Jeśli liczba wątków nie została jawnie ustawiona przez użytkownika, wartość domyślna to zdefiniowane w implementacji. Ta funkcja jest powiązana najbliższej otaczającej **równoległe** dyrektywy. Wywoływana z serial część programu lub zagnieżdżone równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 1.

## <a name="cross-references"></a>Odsyłacze:

- **OMP_NUM_THREADS** środowiska zmiennych, zobacz [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48.

- **num_threads** klauzuli, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.

- **równoległe** konstruowania, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.