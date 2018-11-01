---
title: Błąd kompilatora C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: 9beae880d840f1cd1ac73f51ebeac8883882dd92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50620821"
---
# <a name="compiler-error-c3045"></a>Błąd kompilatora C3045

Oczekiwano złożonej instrukcji po dyrektywie "Sections" OpenMP. Brak "{"

Blok kodu, rozdzielone nawiasów klamrowych musi stosować [sekcje](../../parallel/openmp/reference/sections-openmp.md) dyrektywy.

Poniższy przykład spowoduje wygenerowanie C3045:

```
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```