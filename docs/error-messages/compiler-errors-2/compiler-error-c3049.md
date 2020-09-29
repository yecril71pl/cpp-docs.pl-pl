---
title: Błąd kompilatora C3049
ms.date: 11/04/2016
f1_keywords:
- C3049
helpviewer_keywords:
- C3049
ms.assetid: 6ddf54f6-2c30-4d04-b637-98c6c922c533
ms.openlocfilehash: 21ff04e76c5a58f2ac673d1c4cace16cda388669
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501604"
---
# <a name="compiler-error-c3049"></a>Błąd kompilatora C3049

"ARG": nieprawidłowy argument w klauzuli "default" OpenMP

Niepoprawna wartość została przeniesiona do klauzuli [default](../../parallel/openmp/reference/openmp-clauses.md#default-openmp) .

Poniższy przykład generuje C3049:

```cpp
// C3049.cpp
// compile with: /openmp /c
int main() {
   int n1 = 1;

   #pragma omp parallel default(private)   // C3049
   // try the following line instead
   // #pragma omp parallel default(shared)
   {
      ++n1;
   }
}
```
