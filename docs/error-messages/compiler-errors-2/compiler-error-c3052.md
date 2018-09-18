---
title: Błąd kompilatora C3052 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3052
dev_langs:
- C++
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d292087aefcc7bb99e505aefd0534dd018b2725
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049224"
---
# <a name="compiler-error-c3052"></a>Błąd kompilatora C3052

"var": zmienna nie pojawia się w klauzuli udostępniania danych pod klauzulą default(none)

Jeśli [default(none)](../../parallel/openmp/reference/default-openmp.md) jest używany, dowolnej zmiennej używane w strukturze bloku muszą być jawnie określone jako [udostępnionego](../../parallel/openmp/reference/shared-openmp.md) lub [prywatnej](../../parallel/openmp/reference/private-openmp.md).

Poniższy przykład spowoduje wygenerowanie C3052:

```
// C3052.cpp
// compile with: /openmp /c
int main() {
   int n1 = 1;

   #pragma omp parallel default(none) // shared(n1) private(n1)
   {
      n1 = 0;   // C3052 use either a shared or private clause
   }
}
```