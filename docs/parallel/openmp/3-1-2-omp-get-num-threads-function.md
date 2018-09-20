---
title: 3.1.2 funkcja omp_get_num_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 512c09b0cf71a7fd9c7438b6f9cceb9f16126718
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424987"
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