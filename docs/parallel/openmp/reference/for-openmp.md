---
title: "Aby uzyskać (OpenMP) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: for
dev_langs: C++
helpviewer_keywords: for OpenMP directive
ms.assetid: 8b54e034-9db2-4c1a-a2b1-72e14e930506
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c1e7f5df003796050958f803cc931a49d2d52d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="for-openmp"></a>for (OpenMP)
Powoduje, że pracy wykonanej dla pętli równoległego regionu do podzielony wątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma omp [parallel] for [clauses]  
   for_statement  
```  
  
## <a name="remarks"></a>Uwagi  
 w przypadku gdy  
  
 `clause`(opcjonalnie)  
 Klauzule zero lub więcej. Zobacz sekcję uwag listę klauzule obsługiwane przez **dla**.  
  
 `for_statement`  
 A pętli for. Niezdefiniowane zachowanie spowoduje, że jeśli kod użytkownika dla zmieni się zmienna index pętli.  
  
## <a name="remarks"></a>Uwagi  
 **Dla** dyrektywy obsługuje następujące klauzule OpenMP:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [NOWAIT](../../../parallel/openmp/reference/nowait.md)  
  
-   [uporządkowane](../../../parallel/openmp/reference/ordered-openmp-directives.md)  
  
-   [prywatne](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [redukcja](../../../parallel/openmp/reference/reduction.md)  
  
-   [Harmonogram](../../../parallel/openmp/reference/schedule.md)  
  
 Jeśli **równoległych** jest określona, `clause` może zostać klauzuli zaakceptowane przez **równoległych** lub **dla** dyrektywy, z wyjątkiem **nowait**.  
  
 Aby uzyskać więcej informacji, zobacz [2.4.1 — dla konstrukcji](../../../parallel/openmp/2-4-1-for-construct.md).  
  
## <a name="example"></a>Przykład  
  
```  
// omp_for.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <math.h>  
#include <omp.h>  
  
#define NUM_THREADS 4  
#define NUM_START 1  
#define NUM_END 10  
  
int main() {  
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;  
   int nThreads = 0, nTmp = nStart + nEnd;  
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *   
                               unsigned(abs(nTmp))) / 2;  
   int nSumCalc = uTmp;  
  
   if (nTmp < 0)  
      nSumCalc = -nSumCalc;  
  
   omp_set_num_threads(NUM_THREADS);  
  
   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)  
   {  
      #pragma omp master  
      nThreads = omp_get_num_threads();  
  
      #pragma omp for  
      for (i=nStart; i<=nEnd; ++i) {  
            #pragma omp atomic  
            nSum += i;  
      }  
   }  
  
   if  (nThreads == NUM_THREADS) {  
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);  
      nRet = 0;  
   }  
   else {  
      printf_s("Expected %d OpenMP threads, but %d were used.\n",  
               NUM_THREADS, nThreads);  
      nRet = 1;  
   }  
  
   if (nSum != nSumCalc) {  
      printf_s("The sum of %d through %d should be %d, "  
               "but %d was reported!\n",  
               NUM_START, NUM_END, nSumCalc, nSum);  
      nRet = 1;  
   }  
   else  
      printf_s("The sum of %d through %d is %d\n",  
               NUM_START, NUM_END, nSum);  
}  
```  
  
```Output  
4 OpenMP threads were used.  
The sum of 1 through 10 is 55  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy](../../../parallel/openmp/reference/openmp-directives.md)