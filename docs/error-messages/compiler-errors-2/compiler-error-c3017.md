---
title: Błąd kompilatora C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: 34347abffd91246ada080d19fee88ee09c8fce99
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232069"
---
# <a name="compiler-error-c3017"></a>Błąd kompilatora C3017

test zakończenia w instrukcji "for" OpenMP posiada niewłaściwy formularz

**`for`** Pętla w instrukcji OpenMP musi być w pełni i jawnie określona.

Poniższy przykład generuje C3017:

```cpp
// C3017.cpp
// compile with: /openmp
int main()
{
   int i = 0, j = 10;

   #pragma omp parallel
   {
      #pragma omp for
      for (i = 0; i; ++i)   // C3017
      // Try the following line instead:
      // for (i = 0; i < 10; ++i)
         ;
   }
}
```
