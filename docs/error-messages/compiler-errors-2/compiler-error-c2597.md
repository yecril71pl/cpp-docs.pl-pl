---
title: Błąd kompilatora C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: b7bdd10ebd70eb61746690958532854dd98c6429
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228593"
---
# <a name="compiler-error-c2597"></a>Błąd kompilatora C2597

niedozwolone odwołanie do niestatycznej składowej 'Identyfikator'

Możliwe przyczyny:

1. Niestatyczny element członkowski jest określona w statycznej funkcji członkowskiej. Aby uzyskać dostęp do niestatycznego elementu członkowskiego, musi przekazać lub Utwórz lokalne wystąpienie klasy i użyć operatora dostępu do elementu członkowskiego (`.` lub `->`).

1. Określony identyfikator nie jest członkiem klasy, struktury lub Unii. Sprawdź identyfikator pisowni.

1. Operator dostępu do składowej odnosi się do funkcji nie Członkowskich.

1. Poniższy przykład generuje C2597 i pokazuje, jak go naprawić:

```
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