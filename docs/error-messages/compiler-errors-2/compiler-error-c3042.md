---
title: Błąd kompilatora C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: deb3b8d6251316bceb71ce03f2bda88520bbb9b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182590"
---
# <a name="compiler-error-c3042"></a>Błąd kompilatora C3042

klauzule "copyprivate" i "nowait" nie mogą występować razem w dyrektywie OpenMP "dyrektywa"

[Copyprivate](../../parallel/openmp/reference/copyprivate.md) i [nowait](../../parallel/openmp/reference/nowait.md) klauzule są wzajemnie wykluczających się na określonym dyrektywy. Aby naprawić ten błąd, usuń jedną lub obie `copyprivate` lub `nowait` klauzul.

Poniższy przykład spowoduje wygenerowanie C3042:

```
// C3042.cpp
// compile with: /openmp /c
#include <stdio.h>
#include "omp.h"

double d;

int main() {
    #pragma omp parallel private(d)
   {
      #pragma omp single copyprivate(d) nowait   // C3042
      {
      }
   }
}
```