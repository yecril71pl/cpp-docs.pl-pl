---
title: Błąd kompilatora C2663
ms.date: 11/04/2016
f1_keywords:
- C2663
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
ms.openlocfilehash: f9746ecb41e873fb1d929a939c78f1817dc0e2f9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220278"
---
# <a name="compiler-error-c2663"></a>Błąd kompilatora C2663

"Function": przeciążenia numerów nie mają żadnych dozwolonych konwersji dla wskaźnika "This"

Kompilator nie może wykonać konwersji **`this`** do żadnej ze przeciążonych wersji funkcji składowej.

Ten błąd może być spowodowany wywoływaniem **`const`** funkcji nienależącej do elementu członkowskiego w **`const`** obiekcie.  Możliwe rozwiązania:

1. Usuń **`const`** z deklaracji Object.

1. Dodaj **`const`** do jednego z przeciążeń funkcji składowych.

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
