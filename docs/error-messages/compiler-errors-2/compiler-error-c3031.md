---
title: Błąd kompilatora C3031
ms.date: 11/04/2016
f1_keywords:
- C3031
helpviewer_keywords:
- C3031
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
ms.openlocfilehash: a892ff2bdbefbf6034da58c45c499fd6f65ad965
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748323"
---
# <a name="compiler-error-c3031"></a>Błąd kompilatora C3031

"var": zmienna w klauzuli "redukcyjn" musi mieć skalarny typ arytmetyczny

Zmienna niewłaściwego typu została przeniesiona do klauzuli redukcyjnej.

Poniższy przykład generuje C3031:

```cpp
// C3031.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

typedef struct {
   int n;
} Incomplete;

extern Incomplete inc;
int i = 9;

int main() {
   #pragma omp parallel reduction(+: inc)   // C3031
      ;

   #pragma omp parallel reduction(+: i)     // OK
      ;
}
```
