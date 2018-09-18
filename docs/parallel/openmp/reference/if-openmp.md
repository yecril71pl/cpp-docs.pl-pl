---
title: Jeśli (OpenMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- if OpenMP clause
ms.assetid: db5940b6-2414-4bf8-934d-3edd8393c0f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 83e1920ab2cb44815e9547e4f7f4a07999c1c588
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020956"
---
# <a name="if-openmp"></a>if (OpenMP)
Określa, czy pętla powinny być wykonywane równolegle lub w seryjny.  
  
## <a name="syntax"></a>Składnia  
  
```  
if(expression)  
```  
  
### <a name="parameters"></a>Parametry
  
*Wyrażenie*<br/>
Wyrażenie typu całkowitego, jeśli ma wartość true (niezerową) powoduje, że kod w równoległego regionu można wykonać równolegle. Jeśli wyrażenie ma wartość false (zero), równoległego regionu jest wykonywany w seryjny (przez pojedynczy wątek).  
  
## <a name="remarks"></a>Uwagi  
 `if` mają zastosowanie do następujących dyrektywach:  
  
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