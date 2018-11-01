---
title: Błąd kompilatora C3024
ms.date: 11/04/2016
f1_keywords:
- C3024
helpviewer_keywords:
- C3024
ms.assetid: 1c031c28-ce37-4de3-aead-cfe76b261856
ms.openlocfilehash: 46a7385f530742c19c9c586be7a932d0e054b7d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434726"
---
# <a name="compiler-error-c3024"></a>Błąd kompilatora C3024

"schedule(runtime)": wyrażenie chunk_size nie jest dozwolone.

Wartość nie można przekazać do parametru uruchomieniowego klauzuli harmonogramu.

Poniższy przykład spowoduje wygenerowanie C3024:

```
// C3024.cpp
// compile with: /openmp /link vcomps.lib
#include <stdio.h>
#include "omp.h"

int main() {
   int i;

   #pragma omp parallel for schedule(runtime, 10)   // C3024
   for (i = 0; i < 10; ++i) ;

   #pragma omp parallel for schedule(runtime)   // OK
   for (i = 0; i < 10; ++i) ;
}
```