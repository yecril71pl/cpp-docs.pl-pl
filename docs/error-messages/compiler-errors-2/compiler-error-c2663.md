---
title: Błąd kompilatora C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: d74326e49edd980896276e2c6e67526d8d769cb7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50644343"
---
# <a name="compiler-error-c2663"></a>Błąd kompilatora C2663

'Funkcja': liczba przeciążenia mają prawne konwersji dla wskaźnika "this"

Kompilator nie może przekonwertować `this` do dowolnego przeciążone wersje funkcji elementu członkowskiego.

Ten błąd może być spowodowany przez wywołanie innej niż`const` funkcja elementu członkowskiego na `const` obiektu.  Możliwe rozwiązania:

1. Usuń `const` z deklaracja obiektu.

1. Dodaj `const` do jednego z przeciążeń funkcji elementu członkowskiego.

Poniższy przykład spowoduje wygenerowanie C2663:

```
// C2663.cpp
struct C {
   void f() volatile {}
   void f() {}
};

struct D {
   void f() volatile;
   void f() const {}
};

const C *pcc;
const D *pcd;

int main() {
   pcc->f();    // C2663
   pcd->f();    // OK
}
```