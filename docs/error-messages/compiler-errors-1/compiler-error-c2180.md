---
title: Błąd kompilatora C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 16fcf15eb29743f74bbf2edcb1016f2e15228e5a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553325"
---
# <a name="compiler-error-c2180"></a>Błąd kompilatora C2180

wyrażenie kontrolne jest typu "type"

Wyrażenie kontrolujące w `if`, `while`, `for`, lub `do` instrukcja jest rzutowanie wyrażenia na `void`. Aby rozwiązać ten problem, zmień wyrażenie kontrolujące na taki, który tworzy `bool` lub typ, który może zostać przekonwertowany na `bool`.

Poniższy przykład spowoduje wygenerowanie C2180:

```
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```