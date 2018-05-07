---
title: C3056 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3056
dev_langs:
- C++
helpviewer_keywords:
- C3056
ms.assetid: 9500173d-870b-49b3-8e88-0ee93586d19a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52ec97865a1aa9c8b6da9b109bf100eb62824a9d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3056"></a>C3056 błąd kompilatora
"symbol": symbol nie jest w tym samym zakresie z dyrektywą "threadprivate"  
  
 Symbolu używany w [threadprivate](../../parallel/openmp/reference/threadprivate.md) klauzuli musi znajdować się w tym samym zakresie co `threadprivate` klauzuli.  
  
 Poniższy przykład generuje C3056:  
  
```  
// C3056.cpp  
// compile with: /openmp  
int x, y;  
void test() {  
   #pragma omp threadprivate(x, y)   // C3056  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C3056b.cpp  
// compile with: /openmp /LD  
int x, y;  
#pragma omp threadprivate(x, y)  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```