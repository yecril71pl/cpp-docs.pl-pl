---
title: 3.1.9 Funkcja omp_set_nested
ms.date: 11/04/2016
ms.assetid: e4afc3aa-bb96-4314-9849-fd5df5f437d9
ms.openlocfilehash: 683c2cf684aa7212b8323fda9f748812fa9c3359
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648009"
---
# <a name="319-ompsetnested-function"></a>3.1.9 Funkcja omp_set_nested

**Omp_set_nested** funkcji włącza lub wyłącza równoległości zagnieżdżonych. Format jest następujący:

```
#include <omp.h>
void omp_set_nested(int nested);
```

Jeśli *zagnieżdżonych* wynikiem jest 0, zagnieżdżone równoległości jest wyłączone, co jest ustawieniem domyślnym i zagnieżdżone regionów równoległych są serializowane i wykonywane przez bieżący wątek. Jeśli *zagnieżdżonych* oblicza wartość różną od zera, zagnieżdżonych równoległości jest włączona i regionów równoległych, które są zagnieżdżone mogą wdrażać dodatkowe wątki w celu utworzenia zagnieżdżonych zespołów.

Funkcja ta ma wpływ opisanych powyżej, gdy wywoływana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość zero. Jeśli zostanie wywołana z części programu gdzie **omp_in_parallel** funkcja zwraca wartość różną od zera, zachowanie tej funkcji jest niezdefiniowane.

To wywołanie ma pierwszeństwo przed **OMP_NESTED** zmiennej środowiskowej.

Po włączeniu zagnieżdżonych równoległości liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest zdefiniowane w implementacji. Co w efekcie CLS OpenMP implementacje są dozwolone do serializacji zagnieżdżonych regionów równoległych, nawet wtedy, gdy zagnieżdżony równoległości jest włączona.

## <a name="cross-references"></a>Odsyłacze:

- **OMP_NESTED** środowiska zmiennych, zobacz [4.4 sekcji](../../parallel/openmp/4-4-omp-nested.md) na stronie 49.

- **omp_in_parallel** funkcji, zobacz [sekcji 3.1.6](../../parallel/openmp/3-1-6-omp-in-parallel-function.md) na stronie 38.