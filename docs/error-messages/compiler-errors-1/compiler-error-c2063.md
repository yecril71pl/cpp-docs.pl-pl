---
title: Błąd kompilatora C2063
ms.date: 11/04/2016
f1_keywords:
- C2063
helpviewer_keywords:
- C2063
ms.assetid: 0a90c18f-4029-416a-9128-e8713b53e6f1
ms.openlocfilehash: 5d91dc595798793899eb8ac33e2a6c71cabad02a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444372"
---
# <a name="compiler-error-c2063"></a>Błąd kompilatora C2063

'Identyfikator': nie jest funkcją

Identyfikator jest używany w funkcji, ale nie zadeklarowano jako funkcja.

Poniższy przykład spowoduje wygenerowanie C2063:

```
// C2063.c
int main() {
   int i, j;
   j = i();    // C2063, i is not a function
}
```

Możliwe rozwiązanie:

```
// C2063b.c
int i() { return 0;}
int main() {
   int j;
   j = i();
}
```