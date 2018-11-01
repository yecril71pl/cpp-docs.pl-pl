---
title: 3.1.4 Funkcja omp_get_thread_num
ms.date: 11/04/2016
ms.assetid: 5220402b-c109-4b1f-ba79-002e93d08617
ms.openlocfilehash: eca8522aeab4702be390d98faaf8920f2d732244
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480939"
---
# <a name="314-ompgetthreadnum-function"></a>3.1.4 Funkcja omp_get_thread_num

`omp_get_thread_num` Funkcja zwraca liczbę wątków, w w ramach jego zespołu wątku wykonującego funkcji. Polega liczba wątków między 0 a **omp_get_num_threads()**-1 (włącznie). Główny wątek zespołu znajduje się wątek 0.

Format jest następujący:

```
#include <omp.h>
int omp_get_thread_num(void);
```

Jeśli wywołania będą regionowi serial `omp_get_thread_num` zwraca wartość 0. Wywołane z wnętrza zagnieżdżonych równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 0.

## <a name="cross-references"></a>Odsyłacze:

- `omp_get_num_threads` funkcji, zobacz [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37.