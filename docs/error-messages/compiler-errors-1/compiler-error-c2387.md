---
title: Błąd kompilatora C2387
ms.date: 11/04/2016
f1_keywords:
- C2387
helpviewer_keywords:
- C2387
ms.assetid: 6847b8e1-ffac-458d-ab88-0c92f72f2527
ms.openlocfilehash: df9e92bfa333be88e860bbdecd5acaa64ec80440
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629310"
---
# <a name="compiler-error-c2387"></a>Błąd kompilatora C2387

"type": niejednoznaczna klasa bazowa

Kompilator nie można jednoznacznie rozpoznać wywołania funkcji, ponieważ funkcja istnieje w więcej niż jednej klasy bazowej.

Aby rozwiązać ten problem, usuń jedną z klas bazowych z dziedziczenia lub kwalifikuj jawnie wywołania funkcji.

Poniższy przykład spowoduje wygenerowanie C2387:

```
// C2387.cpp
namespace N1 {
   struct B {
      virtual void f() {
      }
   };
}

namespace N2 {
   struct B {
      virtual void f() {
      }
   };
}

struct D : N1::B, N2::B {
   virtual void f() {
      B::f();   // C2387
      // try the following line instead
      // N1::B::f();
   }
};

int main() {
   D aD;
   aD.f();
}
```