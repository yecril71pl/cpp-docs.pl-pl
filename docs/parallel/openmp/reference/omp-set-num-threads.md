---
title: omp_set_num_threads | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 335cb283026a019d6c6a03565c5dbec541140db3
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
Ustawia liczbę wątków w kolejnych regionach równoległe, chyba że zostaną zastąpione [num_threads](../../../parallel/openmp/reference/num-threads.md) klauzuli.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `num_threads`  
 Liczba wątków w równoległego regionu.  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.1.1 funkcja omp_set_num_threads](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).  
  
## <a name="example"></a>Przykład  
 Zobacz [omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md) przykład przy użyciu `omp_set_num_threads`.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)