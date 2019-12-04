---
title: Błąd kompilatora C3035
ms.date: 11/04/2016
f1_keywords:
- C3035
helpviewer_keywords:
- C3035
ms.assetid: af34fad2-2b45-42d0-a9ff-04eab3e91c37
ms.openlocfilehash: 0064d07d0e6d8adaa41d81272e315685dd32a74f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755021"
---
# <a name="compiler-error-c3035"></a>Błąd kompilatora C3035

Dyrektywa "ordered" OpenMP musi powiązać bezpośrednio z dyrektywą "for" lub "Parallel for" z klauzulą "ordered"

Klauzula uporządkowana jest źle sformułowana.

Poniższy przykład generuje C3035:

```cpp
// C3035.cpp
// compile with: /openmp /link vcomps.lib
int main() {
   int n = 0, x, i;

   #pragma omp parallel private(n)
   {
      #pragma omp ordered   // C3035
      // Try the following line instead:
      // #pragma omp for ordered
       for (i = 0 ; i < 10 ; ++i)
         ;
   }
}
```
