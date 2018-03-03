---
title: 3.1.2 funkcja omp_get_num_threads | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: bcdd76e2-d96b-4884-ac8f-e55fc0c42801
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d595fd47b87bbc3fd7701fc847821c73169a23e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="312-ompgetnumthreads-function"></a>3.1.2 Funkcja omp_get_num_threads
**Omp_get_num_threads** funkcja zwraca liczbę wątków obecnie w zespole wykonywania równoległego regionu, w którym jest wywoływana. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_get_num_threads(void);  
```  
  
 **Num_threads** klauzuli **omp_set_num_threads** funkcji i **OMP_NUM_THREADS** zmiennej środowiskowej decydują o liczbie wątków w zespole.  
  
 Jeśli liczba wątków nie zostanie jawnie ustawiona przez użytkownika, wartość domyślna to zdefiniowane w implementacji. Ta funkcja jest powiązany z najbliższej otaczającej **równoległych** dyrektywy. Wywoływana z serial część programu lub zagnieżdżone równoległego regionu, który jest serializowany, ta funkcja zwraca wartość 1.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **OMP_NUM_THREADS** środowiska zmiennych, zobacz [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48.  
  
-   **num_threads** klauzuli, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.  
  
-   **równoległe** utworzyć, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8.