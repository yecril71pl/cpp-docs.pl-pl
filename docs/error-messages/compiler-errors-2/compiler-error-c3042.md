---
title: Błąd kompilatora C3042
ms.date: 11/04/2016
f1_keywords:
- C3042
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
ms.openlocfilehash: 8cd27f492a72277c383afa5ca335a073b1a0519c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506400"
---
# <a name="compiler-error-c3042"></a>Błąd kompilatora C3042

klauzule "copyprivate" i "nowait" nie mogą występować razem w dyrektywie "OpenMP" dyrektywy

Klauzule [copyprivate](../../parallel/openmp/reference/openmp-clauses.md#copyprivate) i [nowait](../../parallel/openmp/reference/openmp-clauses.md#nowait) są wzajemnie wykluczane na określonej dyrektywie. Aby naprawić ten błąd, Usuń jedną lub obie `copyprivate` `nowait` klauzulę OR.

Poniższy przykład generuje C3042:

```cpp
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
