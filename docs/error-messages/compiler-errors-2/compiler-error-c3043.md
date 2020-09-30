---
title: Błąd kompilatora C3043
ms.date: 11/04/2016
f1_keywords:
- C3043
helpviewer_keywords:
- C3043
ms.assetid: 0ef55e63-e82b-48eb-9d44-690950ac34c6
ms.openlocfilehash: e24d8166a977ab8f16688c8be30e69c7bb616c20
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506373"
---
# <a name="compiler-error-c3043"></a>Błąd kompilatora C3043

Dyrektywa "krytyczna" OpenMP nie może być zagnieżdżona w dyrektywie "krytyczna" o tej samej nazwie

Dyrektywa o [krytycznym znaczeniu](../../parallel/openmp/reference/openmp-directives.md#critical) nie może być zagnieżdżona w `critical` dyrektywie, która używa tej samej nazwy.

Poniższy przykład generuje C3043:

```cpp
// C3043.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n1 = 1, n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp critical(MyTest)
      {
         ++n2;

         #pragma omp critical(MyTest)   // C3043
         // try the following line instead
         // #pragma omp critical(MyTest2)
         {
            ++n3;
         }
      }
   }
}
```
