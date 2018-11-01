---
title: Błąd kompilatora C3060
ms.date: 11/04/2016
f1_keywords:
- C3060
helpviewer_keywords:
- C3060
ms.assetid: 6282bb92-0546-4b59-9435-d3840bf93bdb
ms.openlocfilehash: c77af7fa1220aa5211d480cddf3bf0979c642ade
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515404"
---
# <a name="compiler-error-c3060"></a>Błąd kompilatora C3060

"członek": funkcja zaprzyjaźniona nie może być zdefiniowana wewnątrz klasy przy użyciu kwalifikowanej nazwy (go może być tylko zadeklarowana)

Funkcja zaprzyjaźniona został zdefiniowany przy użyciu kwalifikowanej nazwy, co jest niedozwolone.

Poniższy przykład spowoduje wygenerowanie C3060:

```
// C3060.cpp
class A {
public:
   void func();
};

class C {
public:
   friend void A::func() { }   // C3060
   // Try the following line and the out of class definition:
   // friend void A::func();
};

// void A::func(){}
```