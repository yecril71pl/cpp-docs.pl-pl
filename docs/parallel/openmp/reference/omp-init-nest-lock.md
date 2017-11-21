---
title: omp_init_nest_lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_init_nest_lock
dev_langs: C++
helpviewer_keywords: omp_init_nest_lock OpenMP function
ms.assetid: cf749ec5-de78-4186-9588-ac7c42b02463
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 911fd8069041135f20e8a7924cf5d943abcc2978
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ompinitnestlock"></a>omp_init_nest_lock
Inicjuje blokady.  
  
## <a name="syntax"></a>Składnia  
  
```  
void omp_init_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `lock`  
 Zmienna typu [omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md).  
  
## <a name="remarks"></a>Uwagi  
 Początkowa liczba zagnieżdżenia wynosi zero.  
  
 Aby uzyskać więcej informacji, zobacz [3.2.1 funkcje omp_init_lock i omp_init_nest_lock](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_init_nest_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_nest_lock_t my_lock;  
  
void Test() {  
   int tid = omp_get_thread_num( );  
   omp_set_nest_lock(&my_lock);  
   printf_s("Thread %d - starting nested locked region\n", tid);  
   printf_s("Thread %d - ending nested locked region\n", tid);  
   omp_unset_nest_lock(&my_lock);  
}  
  
int main() {  
   omp_init_nest_lock(&my_lock);  
  
   #pragma omp parallel num_threads(4)  
   {  
      int i, j;  
  
      for (i = 0; i < 5; ++i) {  
         omp_set_nest_lock(&my_lock);  
            if (i % 3)   
               Test();  
            omp_unset_nest_lock(&my_lock);  
        }  
    }  
  
    omp_destroy_nest_lock(&my_lock);  
}  
```  
  
```Output  
Thread 0 - starting nested locked region  
Thread 0 - ending nested locked region  
Thread 0 - starting nested locked region  
Thread 0 - ending nested locked region  
Thread 3 - starting nested locked region  
Thread 3 - ending nested locked region  
Thread 3 - starting nested locked region  
Thread 3 - ending nested locked region  
Thread 3 - starting nested locked region  
Thread 3 - ending nested locked region  
Thread 2 - starting nested locked region  
Thread 2 - ending nested locked region  
Thread 2 - starting nested locked region  
Thread 2 - ending nested locked region  
Thread 2 - starting nested locked region  
Thread 2 - ending nested locked region  
Thread 1 - starting nested locked region  
Thread 1 - ending nested locked region  
Thread 1 - starting nested locked region  
Thread 1 - ending nested locked region  
Thread 1 - starting nested locked region  
Thread 1 - ending nested locked region  
Thread 0 - starting nested locked region  
Thread 0 - ending nested locked region  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)