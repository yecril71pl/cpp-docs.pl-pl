---
title: Błąd kompilatora C3052
ms.date: 11/04/2016
f1_keywords:
- C3052
helpviewer_keywords:
- C3052
ms.assetid: 87480c42-1ceb-4775-8d20-88c54a7bb6a6
ms.openlocfilehash: ed9c27e1602f9372cb9137615ef66932a8df960c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62265779"
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