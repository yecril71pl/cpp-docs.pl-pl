---
title: Ostrzeżenie kompilatora (poziom 4) C4938
ms.date: 11/04/2016
f1_keywords:
- C4938
helpviewer_keywords:
- C4938
ms.assetid: 6acac81a-9d23-465e-b700-ed4b6e8edcd0
ms.openlocfilehash: c752b5daea42eac7c7dd0e14581d9e781aac9c96
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988738"
---
# <a name="compiler-warning-level-4-c4938"></a>Ostrzeżenie kompilatora (poziom 4) C4938

"var": zmienna redukcji zmiennoprzecinkowej może spowodować niespójne wyniki w obszarze/FP: Strict lub #pragma fenv_access

Nie należy używać [/FP: Strict](../../build/reference/fp-specify-floating-point-behavior.md) ani [fenv_access](../../preprocessor/fenv-access.md) ze zmniejszeniem liczby zmiennoprzecinkowej OpenMP, ponieważ suma jest obliczana w innej kolejności. W rezultacie wyniki mogą różnić się od wyników bez/OpenMP.

Poniższy przykład generuje C4938:

```cpp
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

Bez jawnego przetwarzanie równoległe, suma jest obliczana w następujący sposób:

```
sum = a[first] + a[first + 1] + ... + a[last];
```

W przypadku jawnego przetwarzanie równoległe (i dwóch wątków) suma jest obliczana w następujący sposób:

```
sum1 = a[first] + ... a[first + last / 2];
sum2 = a[(first + last / 2) + 1] + ... a[last];
sum = sum1 + sum2;
```
