---
title: uporządkowane (dyrektywy OpenMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- ordered
dev_langs:
- C++
helpviewer_keywords:
- ordered OpenMP directive
ms.assetid: e1aa703e-d07d-4f6a-9b2a-f4f25203d850
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48bf2ec3362a1053cf2fd14cb6a066aaa3d370af
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="ordered-openmp-directives"></a>uporządkowane (dyrektywy OpenMP)
Określa ten kod w obszarze zrównoleglone pętli powinna zostać wykonana w takich jak loop sekwencyjnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp ordered  
   structured-block  
```  
  
## <a name="remarks"></a>Uwagi  
 **Uporządkowane** dyrektywa musi być wewnątrz zakresu dynamicznego [dla](../../../parallel/openmp/reference/for-openmp.md) lub **równoległe w** skonstruować z **uporządkowane** klauzuli.  
  
 **Uporządkowane** dyrektywy obsługuje nie klauzule OpenMP.  
  
 Aby uzyskać więcej informacji, zobacz [2.6.6 konstrukcja uporządkowana](../../../parallel/openmp/2-6-6-ordered-construct.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_ordered.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
static float a[1000], b[1000], c[1000];  
  
void test(int first, int last)   
{  
    #pragma omp for schedule(static) ordered  
    for (int i = first; i <= last; ++i) {  
        // Do something here.  
        if (i % 2)   
        {  
            #pragma omp ordered   
            printf_s("test() iteration %d\n", i);  
        }  
    }  
}  
  
void test2(int iter)   
{  
    #pragma omp ordered  
    printf_s("test2() iteration %d\n", iter);  
}  
  
int main( )   
{  
    int i;  
    #pragma omp parallel  
    {  
        test(1, 8);  
        #pragma omp for ordered  
        for (i = 0 ; i < 5 ; i++)  
            test2(i);  
    }  
}  
```  
  
```Output  
test() iteration 1  
test() iteration 3  
test() iteration 5  
test() iteration 7  
test2() iteration 0  
test2() iteration 1  
test2() iteration 2  
test2() iteration 3  
test2() iteration 4  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)