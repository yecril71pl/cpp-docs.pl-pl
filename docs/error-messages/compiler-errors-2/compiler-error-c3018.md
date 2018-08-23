---
title: Błąd kompilatora C3018 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3018
dev_langs:
- C++
helpviewer_keywords:
- C3018
ms.assetid: 685be45f-f116-43a8-a88d-05ab6616e2f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54436aab9ebb7821e33037bc7ec14a43aa20dda8
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42464532"
---
# <a name="compiler-error-c3018"></a>Błąd kompilatora C3018
"var1": OpenMP "for" testu lub inkrementacja musi użyć zmiennej var2 indeksu  
  
 A `for` pętli w instrukcji OpenMP — należy użyć tę samą zmienną na potrzeby jego przyrost i testowania, ponieważ używa ona jego indeksu.  
  
 Poniższy przykład spowoduje wygenerowanie C3018:  
  
```  
// C3018.cpp  
// compile with: /openmp  
int main()  
{  
   int i = 0, j = 5;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; j < 10; ++i)   // C3018  
      // try the following line instead  
      // for (i = 0; i < 10; ++i)  
         j *= 2;  
  
      #pragma omp for  
      for (i = 0; i < 10; j = j + i)   // C3018  
      // try the following line instead  
      // for (i = 0; i < 10; i = j + i)  
         j *= 2;  
   }  
}  
```