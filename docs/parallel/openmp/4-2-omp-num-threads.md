---
title: 4.2 OMP_NUM_THREADS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 49dd55dd-25d5-4a5a-a998-cc7f47b2dae2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6b4208d7fe7d453dd1f701d820a85fce5cd68ba
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS
**OMP_NUM_THREADS** zmiennej środowiskowej ustawia domyślną liczbę wątków używanych podczas wykonywania, chyba że ten numer zostanie jawnie zmieniona przez wywołanie metody **omp_set_num_threads** procedury biblioteki lub przez jawne **num_threads** klauzula w **równoległych** dyrektywy.  
  
 Wartość **OMP_NUM_THREADS** zmiennej środowiskowej musi być dodatnią liczbą całkowitą. Jego wpływ zależy od tego, czy jest włączone dynamiczne Dostosowywanie to liczba wątków. Kompleksowy zestaw reguł o interakcji między **OMP_NUM_THREADS** środowiska zmiennej i dynamicznego dopasowania wątków, patrz sekcja 2.3 na stronie 8.  
  
 Jeśli nie określono wartości dla **OMP_NUM_THREADS** zmiennej środowiskowej, lub jeśli określona wartość nie jest dodatnią liczbą całkowitą lub jeśli wartość jest większa niż maksymalna liczba wątków systemu można obsługiwać, liczbę wątków używanych jest zdefiniowane w implementacji.  
  
 Przykład:  
  
```  
setenv OMP_NUM_THREADS 16  
```  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **num_threads** klauzuli, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.  
  
-   **omp_set_num_threads** funkcji, zobacz [sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36.  
  
-   **omp_set_dynamic** funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.