---
title: "Jeśli (OpenMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f878a04a7db2243109d034ad93496e860ab1e3c7
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="if-openmp"></a>if (OpenMP)
Określa, czy pętlę powinny być wykonywane równolegle lub kolei.  
  
## <a name="syntax"></a>Składnia  
  
```  
if(expression)  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `expression`  
 Wyrażenie całkowite powodujący, jeśli ją zwraca wartość true (niezerowej), kod w równoległego regionu do wykonywania równoległego. Jeśli wyrażenie ma wartość false (zero), równoległego regionu jest wykonywany w seryjny (przez pojedynczy wątek).  
  
## <a name="remarks"></a>Uwagi  
 `if` ma zastosowanie do następujących dyrektyw:  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)  
  
 Aby uzyskać więcej informacji, zobacz [2.3 konstrukcja równoległa](../../../parallel/openmp/2-3-parallel-construct.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_if.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
void test(int val)  
{  
    #pragma omp parallel if (val)  
    if (omp_in_parallel())  
    {  
        #pragma omp single  
        printf_s("val = %d, parallelized with %d threads\n",  
                 val, omp_get_num_threads());  
    }  
    else  
    {  
        printf_s("val = %d, serialized\n", val);  
    }  
}  
  
int main( )  
{  
    omp_set_num_threads(2);  
    test(0);  
    test(2);  
}  
```  
  
```Output  
val = 0, serialized  
val = 2, parallelized with 2 threads  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)