---
title: OpenMP — funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a39fe44ff053a2e49a1067d0af071353e0a50ece
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-functions"></a>OpenMP — Funkcje
Zawiera łącza do funkcji używanych w interfejsie API OpenMP.  
  
 Visual C++ stosowania standardowych OpenMP obejmuje następujące funkcje.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)|Uninitializes blokady.|  
|[omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)|Uninitializes blokadą.|  
|[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)|Zwraca wartość wskazującą, czy liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.|  
|[omp_get_max_threads](../../../parallel/openmp/reference/omp-get-max-threads.md)|Zwraca liczbę całkowitą, która jest równa lub większa niż liczba wątków, które są dostępne w przypadku równoległego regionu bez [num_threads](../../../parallel/openmp/reference/num-threads.md) zostały zdefiniowane w tym momencie w kodzie.|  
|[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)|Zwraca wartość wskazującą, czy włączono równoległości zagnieżdżonych.|  
|[omp_get_num_procs](../../../parallel/openmp/reference/omp-get-num-procs.md)|Zwraca liczbę procesorów, które są dostępne po wywołaniu funkcji.|  
|[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)|Zwraca liczbę wątków w równoległego regionu.|  
|[omp_get_thread_num](../../../parallel/openmp/reference/omp-get-thread-num.md)|Zwraca liczbę wątków wykonywania wątku w jego zespołu wątku.|  
|[omp_get_wtick](../../../parallel/openmp/reference/omp-get-wtick.md)|Zwraca liczbę sekund między Takty zegara procesora.|  
|[omp_get_wtime](../../../parallel/openmp/reference/omp-get-wtime.md)|Zwraca wartość w sekundach czas, jaki upłynął od pewnym momencie.|  
|[omp_in_parallel](../../../parallel/openmp/reference/omp-in-parallel.md)|Zwraca wartość niezerową, jeśli wywołane z wnętrza równoległego regionu.|  
|[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)|Inicjuje proste blokady.|  
|[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)|Inicjuje blokady.|  
|[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)|Wskazuje, że liczba wątków, które są dostępne w kolejnych równoległego regionu można dostosować w czasie wykonywania.|  
|[omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)|Bloki wątków wykonywania, dopóki blokada jest dostępna.|  
|[omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)|Bloki wątków wykonywania, dopóki blokada jest dostępna.|  
|[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)|Umożliwia równoległości zagnieżdżonych.|  
|[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)|Ustawia liczbę wątków w kolejnych regionach równoległe, chyba że zostaną zastąpione [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzuli.|  
|[omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)|Próbuje ustawić blokady, ale nie blokuje wykonywania wątku.|  
|[omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)|Próbuje ustawić blokadą, ale nie blokuje wykonywania wątku.|  
|[omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)|Zwalnia blokadę.|  
|[omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)|Zwalnia blokadą.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do biblioteki](../../../parallel/openmp/reference/openmp-library-reference.md)