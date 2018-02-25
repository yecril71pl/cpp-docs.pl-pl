---
title: omp_in_parallel | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_in_parallel
dev_langs:
- C++
helpviewer_keywords:
- omp_in_parallel OpenMP function
ms.assetid: 1f01a1b4-78c5-496a-afb7-a43ecdad83d6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 57af15a05d104645de0c52465fa4e31c88466122
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="ompinparallel"></a>omp_in_parallel
Zwraca wartość niezerową, jeśli wywołane z wnętrza równoległego regionu.  
  
## <a name="syntax"></a>Składnia  
  
```  
int omp_in_parallel( );  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [3.1.6 funkcja omp_in_parallel](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_in_parallel.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_in_parallel( ));  
  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_in_parallel( ));  
        }  
}  
```  
  
```Output  
0  
1  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../parallel/openmp/reference/openmp-functions.md)