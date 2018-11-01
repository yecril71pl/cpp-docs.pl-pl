---
title: Błąd kompilatora C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: 0baceeec9911181d9b21c53edf55b73686801316
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642747"
---
# <a name="compiler-error-c3038"></a>Błąd kompilatora C3038

"var": zmienna w klauzuli "private" nie może być zmienną redukcyjną w załączonym kontekście

Zmienne, które pojawiają się w [redukcji](../../parallel/openmp/reference/reduction.md) nie można określić klauzuli równoległe dyrektywy w [prywatnej](../../parallel/openmp/reference/private-openmp.md) klauzuli w dyrektywie podziału pracy, która jest powiązywana z konstrukcja równoległa.

Poniższy przykład spowoduje wygenerowanie C3038:

```
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```