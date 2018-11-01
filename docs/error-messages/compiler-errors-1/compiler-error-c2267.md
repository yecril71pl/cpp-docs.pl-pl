---
title: Błąd kompilatora C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: 5ff8b0bee1f79d9534841e4368fd5a5249cbb413
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534852"
---
# <a name="compiler-error-c2267"></a>Błąd kompilatora C2267

'Funkcja': funkcje statyczne w zakresie bloku są niedozwolone

Funkcja lokalna jest zadeklarowana `static`. Statyczne funkcje muszą mieć zakresu globalnego.

Poniższy przykład spowoduje wygenerowanie C2267:

```
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```