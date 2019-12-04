---
title: Błąd kompilatora C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: aa276ea839f11574609b183d78b46e08581a1b51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743656"
---
# <a name="compiler-error-c2477"></a>Błąd kompilatora C2477

"member": statyczna składowa danych nie może zostać zainicjowana za pośrednictwem klasy pochodnej

Statyczny element członkowski danych klasy Template został zainicjowany nieprawidłowo. Jest to istotna zmiana w wersjach kompilatora firmy Microsoft C++ przed programem Visual Studio .NET 2003 w celu zapewnienia zgodności ze standardem ISO C++ .

Poniższy przykład generuje C2477:

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
