---
title: Błąd kompilatora C3055
ms.date: 11/04/2016
f1_keywords:
- C3055
helpviewer_keywords:
- C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
ms.openlocfilehash: 2a770709b4958f446e8e5a64b245f2932f99460f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540975"
---
# <a name="compiler-error-c3055"></a>Błąd kompilatora C3055

'symbol': symbol nie może być przywoływany, zanim zostaną one użyte w dyrektywie "threadprivate"

Symbol został odwołania i następnie używane podczas [threadprivate](../../parallel/openmp/reference/threadprivate.md) klauzula, która nie jest dozwolona.

Poniższy przykład spowoduje wygenerowanie C3055:

```
// C3055.cpp
// compile with: /openmp
int x, y;
int z = x;
#pragma omp threadprivate(x, y)   // C3055

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```

Możliwe rozwiązanie:

```
// C3055b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }
}
```