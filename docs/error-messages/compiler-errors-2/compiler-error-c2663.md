---
title: Błąd kompilatora C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f07b63202d8f171dfb69f4bb294b392152b9290b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756035"
---
# <a name="compiler-error-c2663"></a>Błąd kompilatora C2663

"Function": przeciążenia numerów nie mają żadnych dozwolonych konwersji dla wskaźnika "This"

Kompilator nie może skonwertować `this` na żadne przeciążone wersje funkcji składowej.

Ten błąd może być spowodowany wywołaniem funkcji członkowskiej innej niż`const` na obiekcie `const`.  Możliwe rozwiązania:

1. Usuń `const` z deklaracji obiektu.

1. Dodaj `const` do jednego z przeciążeń funkcji składowych.

Poniższy przykład generuje C2663:

```cpp
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
