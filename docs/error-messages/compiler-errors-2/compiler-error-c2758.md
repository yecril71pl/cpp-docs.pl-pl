---
title: Błąd kompilatora C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c3a86b8b8c7f122929a52221d4f01a17c50395be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257663"
---
# <a name="compiler-error-c2758"></a>Błąd kompilatora C2758

"członek": składowa typu referencyjnego musi zostać zainicjowany

Błąd kompilatora C2758 występuje po konstruktora, nie inicjuje składowej typu odwołania na liście inicjatora. Kompilator pozostawia niezdefiniowane elementu członkowskiego. Odwołanie do elementu członkowskiego musi zmienne inicjowane, gdy zadeklarowane lub należy podać wartość w listy inicjowania konstruktora.

Poniższy przykład spowoduje wygenerowanie C2758:

```
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```