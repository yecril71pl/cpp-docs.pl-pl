---
title: Błąd kompilatora C2597 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2597
dev_langs:
- C++
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9f8deb325ae54393518698263f3ca93ca88ca48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114452"
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