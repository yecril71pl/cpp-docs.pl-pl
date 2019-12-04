---
title: Błąd kompilatora C3217
ms.date: 11/04/2016
f1_keywords:
- C3217
helpviewer_keywords:
- C3217
ms.assetid: 99070417-c23a-4d82-bdd2-04be1a07adea
ms.openlocfilehash: cb837a42841b2695941d4cd6122d186665d2d7e2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754592"
---
# <a name="compiler-error-c3217"></a>Błąd kompilatora C3217

"param": parametr generyczny nie może być ograniczony w tej deklaracji

Ograniczenie zostało źle sformułowane; parametr generyczny ograniczenia musi zgadzać się z parametrem szablonu klasy ogólnej.

Poniższy przykład generuje C3217:

```cpp
// C3217.cpp
// compile with: /clr
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T : A   // C3217
   void f();
};
```

Poniższy przykład demonstruje możliwe rozwiązanie:

```cpp
// C3217b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
ref class C {
   generic <class T1>
   where T1 : A
   void f();
};
```
