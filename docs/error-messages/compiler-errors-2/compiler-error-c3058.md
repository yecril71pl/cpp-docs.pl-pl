---
title: Błąd kompilatora C3058
ms.date: 11/04/2016
f1_keywords:
- C3058
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
ms.openlocfilehash: 2c0615f78bf9068311ec691f70c4c1a60ef728b0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501478"
---
# <a name="compiler-error-c3058"></a>Błąd kompilatora C3058

"symbol": symbol nie został zadeklarowany jako "threadprivate" przed jego użyciem w klauzuli "Copy"

Symbol musi być zadeklarowany jako [threadprivate](../../parallel/openmp/reference/openmp-directives.md#threadprivate) , zanim będzie można go użyć w klauzuli [copy](../../parallel/openmp/reference/openmp-clauses.md#copyin) .

Poniższy przykład generuje C3058:

```cpp
// C3058.cpp
// compile with: /openmp
int x, y, z;
#pragma omp threadprivate(x, z)

void test() {
   #pragma omp parallel copyin(x, y)   // C3058
   {
   }
}
```

Możliwe rozwiązanie:

```cpp
// C3058b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
   }
}
```
