---
title: Błąd kompilatora C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 44f7988f9fedb882972b2823f2fe70d9512d4e87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484789"
---
# <a name="compiler-error-c2801"></a>Błąd kompilatora C2801

"operator operator" musi być niestatycznego elementu członkowskiego

Następujące operatory mogą być przeciążone tylko jako niestatycznych elementów członkowskich:

- Przypisania `=`

- Dostęp do składowej klasy `->`

- Subscripting `[]`

- Wywołanie funkcji `()`

Możliwe przyczyny C2801:

- Przeciążony operator nie jest klasy, struktury lub Unii.

- Przeciążony operator jest zadeklarowany jako `static`.

- Poniższy przykład spowoduje wygenerowanie C2801:

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```