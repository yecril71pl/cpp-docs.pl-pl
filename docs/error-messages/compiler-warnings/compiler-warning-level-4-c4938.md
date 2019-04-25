---
title: Kompilator ostrzeżenie (poziom 4) C4938
ms.date: 11/04/2016
f1_keywords:
- C4938
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
ms.openlocfilehash: da2725a398a99b5943e128038e75622115a9e34f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280207"
---
# <a name="compiler-warning-level-4-c4938"></a>Kompilator ostrzeżenie (poziom 4) C4938

"var": Zmiennoprzecinkowe zmiennej redukcji punktu może spowodować niespójne wyniki w obszarze/FP: strict lub #pragma fenv_access

Nie należy używać [/FP: strict](../../build/reference/fp-specify-floating-point-behavior.md) lub [fenv_access](../../preprocessor/fenv-access.md) z OpenMP redukcji zmiennoprzecinkowych, ponieważ suma jest obliczana w innej kolejności. W związku z tym wyniki mogą różnić się od wyników, bez/OpenMP.

Poniższy przykład spowoduje wygenerowanie C4938:

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