---
title: Błąd kompilatora C3042 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36fde6251244582a0626c80aa673ed6dd0e559d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045233"
---
# <a name="compiler-error-c3042"></a>Błąd kompilatora C3042

klauzule "copyprivate" i "nowait" nie mogą występować razem w dyrektywie OpenMP "dyrektywa"

[Copyprivate](../../parallel/openmp/reference/copyprivate.md) i [nowait](../../parallel/openmp/reference/nowait.md) klauzule są wzajemnie wykluczających się na określonym dyrektywy. Aby naprawić ten błąd, usuń jedną lub obie `copyprivate` lub `nowait` klauzul.

Poniższy przykład spowoduje wygenerowanie C3042:

```
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