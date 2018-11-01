---
title: Błąd kompilatora C2332
ms.date: 11/04/2016
f1_keywords:
- C2332
helpviewer_keywords:
- C2332
ms.assetid: fb05cd68-e271-4bea-9fb7-ef4edb0a26ac
ms.openlocfilehash: c9b8fe3665199e4a502de965fd1e592252e97bf2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500311"
---
# <a name="compiler-error-c2332"></a>Błąd kompilatora C2332

"typedef": Brak nazwy tagu

Kompilator znaleźć definicję niekompletnego typu.

Poniższy przykład spowoduje wygenerowanie C2332:

```
// C2332.cpp
// compile with: /c
struct S {
   int i;
};

typedef struct * pS;   // C2332
typedef struct S* pS;   // OK

int get_S_i(pS p) {
   return p->i;
}
```