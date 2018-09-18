---
title: Błąd kompilatora C3047 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3047
dev_langs:
- C++
helpviewer_keywords:
- C3047
ms.assetid: 91c14566-5958-433d-8549-0e8bc3196f76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ecc39ae2659416def6faf9903efb66a75e0afcc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105482"
---
# <a name="compiler-error-c3047"></a>Błąd kompilatora C3047

Blok strukturalny w regionie "sections" musi być poprzedzony przez "#pragma omp section" OpenMP

Każdy kod w bloku kodu, wprowadzony przez [sekcje](../../parallel/openmp/reference/sections-openmp.md) dyrektywy muszą znajdować się w bloku kodu, wprowadzony przez `section` dyrektywy.

Poniższy przykład spowoduje wygenerowanie C3047:

```
// C3047.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
      {

         #pragma omp section
         {
            ++n3;
         }

         ++n2;   // C3047 not enclosed in #pragma omp section
      }
   }
}
```