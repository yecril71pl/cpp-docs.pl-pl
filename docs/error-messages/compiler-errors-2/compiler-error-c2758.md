---
title: Błąd kompilatora C2758
ms.date: 11/04/2016
f1_keywords:
- C2758
helpviewer_keywords:
- C2758
ms.assetid: 1d273034-194c-4926-9869-142d1b219cbe
ms.openlocfilehash: c854aeff1c57b8be6b445bc3615008519ca00af7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759519"
---
# <a name="compiler-error-c2758"></a>Błąd kompilatora C2758

"member": element członkowski typu referencyjnego musi być zainicjowany

Błąd kompilatora C2758 jest spowodowany tym, że Konstruktor nie inicjuje składowej typu referencyjnego na liście inicjatorów. Kompilator opuszcza element członkowski niezdefiniowany. Zmienne składowe odniesienia muszą zostać zainicjowane, gdy zadeklarowane lub mają wartość na liście inicjalizacji konstruktora.

Poniższy przykład generuje C2758:

```cpp
// C2758.cpp
// Compile by using: cl /W3 /c C2758.cpp
struct A {
   const int i;

   A(int n) { };   // C2758
   // try the following line instead
   // A(int n) : i{n} {};
};
```
