---
title: Błąd kompilatora C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: 680268948f8642b02768bd4b3092666982e14eb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759311"
---
# <a name="compiler-error-c2597"></a>Błąd kompilatora C2597

niedozwolone odwołanie do niestatycznego elementu członkowskiego "identifier"

Możliwe przyczyny:

1. Niestatyczny element członkowski jest określony w statycznej funkcji członkowskiej. Aby uzyskać dostęp do niestatycznej składowej, należy przekazać lub utworzyć lokalne wystąpienie klasy i użyć operatora dostępu do składowych (`.` lub `->`).

1. Określony identyfikator nie jest elementem członkowskim klasy, struktury lub Unii. Sprawdź pisownię identyfikatorów.

1. Operator dostępu do składowej odwołuje się do funkcji nienależącej do elementu członkowskiego.

1. Poniższy przykład generuje C2597 i pokazuje, jak to naprawić:

```cpp
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```
