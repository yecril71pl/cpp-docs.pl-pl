---
title: Błąd kompilatora C3053
ms.date: 11/04/2016
f1_keywords:
- C3053
helpviewer_keywords:
- C3053
ms.assetid: ab9a25f3-e341-4f6e-8e69-069b4a963a64
ms.openlocfilehash: cb01207be15a628fb0c6206df3e6a673067f568a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441372"
---
# <a name="compiler-error-c3053"></a>Błąd kompilatora C3053

'symbol': "threadprivate" jest tylko prawidłowy dla globalnych lub statycznych elementów danych

Symbole są przekazywane do [threadprivate](../../parallel/openmp/reference/threadprivate.md) musi mieć globalnych lub statycznych.

Poniższy przykład spowoduje wygenerowanie C3053:

```
// C3053.cpp
// compile with: /openmp
void Test() {
   int x, y;
   #pragma omp threadprivate(x, y)   // C3053
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Możliwe rozwiązanie:

```
// C3053b.cpp
// compile with: /openmp /LD
int x, y;
#pragma omp threadprivate(x, y)

void Test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```