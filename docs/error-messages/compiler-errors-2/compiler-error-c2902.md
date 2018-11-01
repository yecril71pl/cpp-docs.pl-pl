---
title: Błąd kompilatora C2902
ms.date: 11/04/2016
f1_keywords:
- C2902
helpviewer_keywords:
- C2902
ms.assetid: 89d78d0e-78e5-4c2c-a0f9-a60110e9395e
ms.openlocfilehash: 09a418d5a6f8b95ed55f1dc5d573b2176d0d0ccf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450144"
---
# <a name="compiler-error-c2902"></a>Błąd kompilatora C2902

"token": nieoczekiwany token następujący "template", oczekiwano identyfikatora

Token, po słowie kluczowym `template` nie jest identyfikatorem.

Poniższy przykład spowoduje wygenerowanie C2902:

```
// C2902.cpp
// compile with: /c
namespace N {
   template<class T> class X {};
   class Y {};
}
void g() {
   N::template + 1;   // C2902
}

void f() {
   N::template X<int> x1;   // OK
}
```

C2902 może również wystąpić, gdy za pomocą typów ogólnych:

```
// C2902b.cpp
// compile with: /clr /c
namespace N {
   generic<class T> ref class GC {};
}

void f() {
   N::generic + 1;   // C2902
   N::generic GC<int>^ x;
}
```