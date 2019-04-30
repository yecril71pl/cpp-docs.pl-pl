---
title: Błąd kompilatora C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 16fcf15eb29743f74bbf2edcb1016f2e15228e5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385917"
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