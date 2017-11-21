---
title: OMP_NUM_THREADS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NUM_THREADS
dev_langs: C++
helpviewer_keywords: OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2139ecfc719bd6e5836a67d9387b3ff2f4289bc6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
Ustawia maksymalną liczbę wątków w równoległego regionu, chyba że zostaną zastąpione [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) lub [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `num`  
 Maksymalna liczba wątków w równoległego regionu, maksymalnie 64 w implementacji Visual C++.  
  
## <a name="remarks"></a>Uwagi  
 **OMP_NUM_THREADS** zmiennej środowiskowej może zostać przesłonięta przez [omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) funkcji lub [num_threads](../../../parallel/openmp/reference/num-threads.md).  
  
 Wartość domyślna `num` w programie Visual C++ implementacja standardu OpenMP jest liczba procesorów wirtualnych, w tym wielowątkowość procesorów.  
  
 Aby uzyskać więcej informacji, zobacz [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie ustawia **OMP_NUM_THREADS** zmiennej środowiskowej 16:  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 Następujące polecenie wyświetla bieżące ustawienie **OMP_NUM_THREADS** zmiennej środowiskowej:  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne środowiskowe](../../../parallel/openmp/reference/openmp-environment-variables.md)