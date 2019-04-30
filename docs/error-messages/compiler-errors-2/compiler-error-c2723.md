---
title: Błąd kompilatora C2723
ms.date: 11/04/2016
f1_keywords:
- C2723
helpviewer_keywords:
- C2723
ms.assetid: 86925601-2297-4cfd-94e2-2caf27c474c4
ms.openlocfilehash: bc07a99f12ed0e447427990969e54f7f3d3d3b7f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383025"
---
# <a name="compiler-error-c2723"></a>Błąd kompilatora C2723

'Funkcja': "specyfikatora" niedozwolony specyfikator w definicji funkcji

Specyfikator nie może występować poza deklaracją klasy definicje funkcji. `virtual` Specyfikator może być określony tylko na deklarację funkcji członkowskiej w obrębie deklaracji klasy.

Poniższy przykład generuje C2723 i pokazuje, jak go naprawić:

```
// C2723.cpp
struct X {
   virtual void f();
   virtual void g();
};

virtual void X::f() {}   // C2723

// try the following line instead
void X::g() {}
```