---
title: Błąd kompilatora C2051
ms.date: 11/04/2016
f1_keywords:
- C2051
helpviewer_keywords:
- C2051
ms.assetid: 81c0469a-78e2-49fa-bd76-97cdb135e3ea
ms.openlocfilehash: e6b0d95628a1b4e7f9707202d57d29b906b1b96d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532711"
---
# <a name="compiler-error-c2051"></a>Błąd kompilatora C2051

wyrażenie CASE nie jest stałą

Wyrażenia CASE muszą być stałe całkowite.

Poniższy przykład spowoduje wygenerowanie C2051:

```
// C2051.cpp
class X {};

int main() {
   static X x;
   int i = 0;

   switch (i) {
      case x:   // C2051 use constant expression to resolve error
         break;
      default:
         break;
   }
}
```

Możliwe rozwiązanie:

```
// C2051b.cpp
class X {};

int main() {
   static X x;
   int i = 0;

   switch (i) {
      case 1:
         break;
      default:
         break;
   }
}
```