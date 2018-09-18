---
title: Błąd kompilatora C3015 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3015
dev_langs:
- C++
helpviewer_keywords:
- C3015
ms.assetid: d5e8e50b-7542-4b2d-8665-1b22072a5bc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fa6b6d102f78de7d834a0c7d9fc16cfb85833fd1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46023973"
---
# <a name="compiler-error-c3015"></a>Błąd kompilatora C3015

inicjujące instrukcji "for" OpenMP posiada niewłaściwy formularz

A `for` pętli w instrukcji OpenMP musi być w pełni i jawnie określona.

Poniższy przykład spowoduje wygenerowanie C3015:

```
// C3015.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (; i < 0; i += j)   // C3015
      // Try the following line instead:
      // for (i = 0; i < 0; i++)
         --j;
   }
}
```