---
title: Błąd kompilatora C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4897512f6bd27465b7281d7a27757918128202d2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50489937"
---
# <a name="compiler-error-c2694"></a>Błąd kompilatora C2694

"override": przesłanianie wirtualnej funkcji ma mniej restrykcyjną specyfikację wyjątku niż klasa bazowa, funkcja wirtualna elementu członkowskiego "base"

Funkcja wirtualna została zastąpiona, ale opcja [/Za](../../build/reference/za-ze-disable-language-extensions.md), przesłanianie funkcji ma mniej restrykcyjną [Specyfikacja wyjątku](../../cpp/exception-specifications-throw-cpp.md).

Poniższy przykład spowoduje wygenerowanie C2694:

```
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```