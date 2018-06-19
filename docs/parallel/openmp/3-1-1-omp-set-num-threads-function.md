---
title: 3.1.1 funkcja omp_set_num_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b94cf2b5-8011-4a3b-ba56-676982642857
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99c82ff324cbf21612d2459511877d152e2757f5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688443"
---
# <a name="311-ompsetnumthreads-function"></a>3.1.1 Funkcja omp_set_num_threads
`omp_set_num_threads` Funkcja ustawia domyślną liczbę wątków używanych podczas kolejnych równoległych regionów, które nie określają `num_threads` klauzuli. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_set_num_threads(int num_threads);  
```  
  
 Wartość parametru *num_threads* musi być dodatnią liczbą całkowitą. Jego wpływ zależy od tego, czy jest włączone dynamiczne Dostosowywanie to liczba wątków. Kompleksowy zestaw reguł o interakcji między `omp_set_num_threads` funkcji i dynamiczne Dostosowywanie wątków, patrz sekcja 2.3 na stronie 8.  
  
 Ta funkcja ma wpływ opisane powyżej, gdy wywoływana z części programu gdzie `omp_in_parallel` funkcja zwraca wartość zero. Jeśli jest ona wywoływana z części program gdzie `omp_in_parallel` funkcja zwraca wartość niezerową, działanie tej funkcji jest niezdefiniowany.  
  
 To wywołanie ma pierwszeństwo przed `OMP_NUM_THREADS` zmiennej środowiskowej. Wartość domyślna to liczba wątków, które mogą być ustanowione przez wywołanie metody `omp_set_num_threads` lub przez ustawienie `OMP_NUM_THREADS` zmiennej środowiskowej, może być jawnie przesłonięte w ramach jednej **równoległych** dyrektywy określając `num_threads` klauzuli.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   `omp_set_dynamic` funkcji, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.  
  
-   `omp_get_dynamic` funkcji, zobacz [sekcji 3.1.8](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md) na stronie 40.  
  
-   `OMP_NUM_THREADS` środowisko zmiennych, zobacz [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48 i sekcja 2.3 na stronie 8.  
  
-   `num_threads` Klauzula, zobacz [2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8