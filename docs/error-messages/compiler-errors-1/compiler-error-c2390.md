---
title: Błąd kompilatora C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 89f6ebb02326413e8dca67d333e555321da4e645
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595876"
---
# <a name="compiler-error-c2390"></a>Błąd kompilatora C2390

'Identyfikator': niepoprawna Klasa magazynu "specyfikatora"

Klasa magazynu nie jest prawidłowy dla identyfikatora zakresu globalnego. Domyślna klasa magazynu jest używany zamiast nieprawidłowa klasa.

Możliwe rozwiązania:

- Jeśli identyfikator jest funkcją, Zadeklaruj go `extern` magazynu.

- Jeśli identyfikator jest formalny parametr lub zmienna lokalna, Zadeklaruj go z usługą storage automatycznie.

- Jeśli identyfikator jest zmienną globalną, Zadeklaruj go za pomocą nie klasy magazynu (auto magazynu).

## <a name="example"></a>Przykład

- Poniższy przykład spowoduje wygenerowanie C2390:

```
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```