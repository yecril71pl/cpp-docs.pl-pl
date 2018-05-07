---
title: C3019 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3019
dev_langs:
- C++
helpviewer_keywords:
- C3019
ms.assetid: 31a6d9b6-d29f-4499-9ad8-48dd751e87c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 390a05af4c81104c081376d45f12f1a9cd8a91d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3019"></a>C3019 błąd kompilatora
inkrementacja w OpenMP instrukcji "for" posiada niewłaściwy formularz  
  
 Przyrost część OpenMP `for` pętli musi użyć zmiennej index, zarówno po lewej i prawej stronie operatora.  
  
 Poniższy przykład generuje C3019:  
  
```  
// C3019.cpp  
// compile with: /openmp  
int main()  
{  
   int i = 0, j = 1, n = 3;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 10; i = j + n)   // C3019  
      // Try the following line instead:  
      // for (i = 0; i < 10; i++)  
         j *= 2;  
   }  
}  
```