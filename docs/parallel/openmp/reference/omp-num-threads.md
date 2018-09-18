---
title: OMP_NUM_THREADS | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OMP_NUM_THREADS
dev_langs:
- C++
helpviewer_keywords:
- OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39f45b9c81d5339b2b6afe4c77fdc9bac6b5d731
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091169"
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Ustawia maksymalną liczbę wątków w równoległego regionu, chyba że zostaną zastąpione [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) lub [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
### <a name="parameters"></a>Parametry
  
*num*<br/>
Maksymalna liczba wątków w równoległego regionu, maksymalnie 64 w implementacji Visual C++.  
  
## <a name="remarks"></a>Uwagi  
 **OMP_NUM_THREADS** zmiennej środowiskowej, może zostać przesłonięta przez [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) funkcji lub [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 Wartość domyślna `num` w programie Visual C++ implementacja standardu OpenMP jest liczba procesorów wirtualnych, w tym procesory CPU wielowątkowość.  
  
 Aby uzyskać więcej informacji, zobacz [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie ustawia **OMP_NUM_THREADS** zmiennej środowiskowej 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 Następujące polecenie wyświetla bieżące ustawienie **OMP_NUM_THREADS** zmienną środowiskową:  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)