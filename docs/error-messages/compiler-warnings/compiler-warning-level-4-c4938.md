---
title: Kompilator ostrzeżenie (poziom 4) C4938 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4938
dev_langs:
- C++
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e140f3885aec66d01d5f7e28245c10e952bedde3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46107445"
---
# <a name="compiler-warning-level-4-c4938"></a>Kompilator ostrzeżenie (poziom 4) C4938

"var": zmiennoprzecinkowy zmiennej redukcji punktu może spowodować niespójne wyniki w obszarze/FP: strict lub #pragma fenv_access

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