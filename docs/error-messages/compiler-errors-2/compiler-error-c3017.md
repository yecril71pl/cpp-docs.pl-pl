---
title: Błąd kompilatora C3017
ms.date: 11/04/2016
f1_keywords:
- C3017
helpviewer_keywords:
- C3017
ms.assetid: 12ab2c2a-d0d2-4900-9cbf-39be0af590dd
ms.openlocfilehash: 7172d870c509e79bf0900604302c38bc6ca9cd77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360362"
---
# <a name="compiler-error-c3017"></a>Błąd kompilatora C3017

test końcowy w OpenMP instrukcji "for" posiada niewłaściwy formularz

A `for` pętli w instrukcji OpenMP musi być w pełni i jawnie określona.

Poniższy przykład spowoduje wygenerowanie C3017:

```
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