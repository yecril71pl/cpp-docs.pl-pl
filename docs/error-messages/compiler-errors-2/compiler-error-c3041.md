---
title: Błąd kompilatora C3041 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3041
dev_langs:
- C++
helpviewer_keywords:
- C3041
ms.assetid: 9df1ae44-3ac7-4c6c-899f-f35ffe7ccf0d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc19c13804eefe88b20542d4eb8c9bc8ead101e4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066924"
---
# <a name="compiler-error-c3041"></a>Błąd kompilatora C3041

"var": zmienna w klauzuli "copyprivate" musi być prywatna w załączonym kontekście

Zmienna jest przekazywana do [copyprivate](../../parallel/openmp/reference/copyprivate.md) nie może być współużytkowana w otaczającym kontekście.

Poniższy przykład spowoduje wygenerowanie C3041:

```
// C3041.cpp
// compile with: /openmp /c
#include "omp.h"
double d;
int main() {
   #pragma omp parallel shared(d)
   // try the following line instead
   // #pragma omp parallel private(d)
   {
      // or don't make d copyprivate
      #pragma omp single copyprivate(d)   // C3041
      {
      }
   }
}
```