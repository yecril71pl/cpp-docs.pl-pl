---
title: Błąd kompilatora C2698
ms.date: 11/04/2016
f1_keywords:
- C2698
helpviewer_keywords:
- C2698
ms.assetid: 3ebfe395-c20b-4c56-9980-ca9ed8653382
ms.openlocfilehash: 6129ff691f804b31fdb8cb487ac4609e4bca6ef2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755190"
---
# <a name="compiler-error-c2698"></a>Błąd kompilatora C2698

Deklaracja using dla elementu "Deklaracja 1" nie może współistnieć z istniejącą deklaracją using dla deklaracji 2

Gdy masz [deklarację using](../../cpp/using-declaration.md) dla elementu członkowskiego danych, wszelkie użycie deklaracji w tym samym zakresie, który używa tej samej nazwy, nie jest dozwolone, ponieważ tylko funkcje mogą być przeciążone.

Poniższy przykład generuje C2698:

```cpp
// C2698.cpp
struct A {
   int x;
};

struct B {
   int x;
};

struct C : A, B {
   using A::x;
   using B::x;   // C2698
}
```
