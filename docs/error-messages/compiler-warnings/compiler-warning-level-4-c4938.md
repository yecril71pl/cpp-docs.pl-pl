---
title: Kompilatora (poziom 4) ostrzeżenie C4938 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4938
dev_langs:
- C++
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b069e233072e653f848da61423411875d817cef0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4938"></a>Kompilator C4938 ostrzegawcze (poziom 4)
"var": zmienna reduktywna przestawne może spowodować niespójne wyniki z opcją/FP: strict lub dyrektywą #pragma fenv_access  
  
 Nie należy używać [/FP: strict](../../build/reference/fp-specify-floating-point-behavior.md) lub [fenv_access](../../preprocessor/fenv-access.md) z OpenMP redukcji liczb zmiennoprzecinkowych, ponieważ suma jest obliczana w innej kolejności. W związku z tym wyniki mogą być różne od wyników bez/OpenMP.  
  
 Poniższy przykład generuje C4938:  
  
```  
// C4938.cpp  
// compile with: /openmp /W4 /fp:strict /c  
// #pragma fenv_access(on)  
extern double *a;   
  
double test(int first, int last) {   
   double sum = 0.0;   
   #pragma omp parallel for reduction(+: sum)   // C4938  
   for (int i = first ; i <= last ; ++i)   
      sum += a[i];   
   return sum;   
}  
```  
  
 Bez jawna paralelizacja suma jest obliczana w następujący sposób:  
  
```  
sum = a[first] + a[first + 1] + ... + a[last];   
```  
  
 Jawna paralelizacja (i dwoma wątkami) suma jest obliczana w następujący sposób:  
  
```  
sum1 = a[first] + ... a[first + last / 2];   
sum2 = a[(first + last / 2) + 1] + ... a[last];   
sum = sum1 + sum2;  
```