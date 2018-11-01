---
title: Błąd kompilatora C3047
ms.date: 11/04/2016
f1_keywords:
- C3047
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
ms.openlocfilehash: c73cdce4520b139c872c29b7809a46f55c3bebd1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434934"
---
# <a name="compiler-error-c3047"></a>Błąd kompilatora C3047

Blok strukturalny w regionie "sections" musi być poprzedzony przez "#pragma omp section" OpenMP

Każdy kod w bloku kodu, wprowadzony przez [sekcje](../../parallel/openmp/reference/sections-openmp.md) dyrektywy muszą znajdować się w bloku kodu, wprowadzony przez `section` dyrektywy.

Poniższy przykład spowoduje wygenerowanie C3047:

```
// C3047.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {

         #pragma omp section
         {
            ++n3;
         }

         ++n2;   // C3047 not enclosed in #pragma omp section
      }
   }
}
```