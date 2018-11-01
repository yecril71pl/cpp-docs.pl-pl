---
title: Błąd kompilatora C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: 75e3b438dd69f8879fdc2273a8f0357229941340
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428288"
---
# <a name="compiler-error-c2594"></a>Błąd kompilatora C2594

'operator': Niejednoznaczne konwersje z 'Typ1' na 'type2'

Brak konwersji z *type1* do *type2* był bardziej bezpośrednie niż inne. Sugerujemy dwa możliwe rozwiązania do konwertowania z *type1* do *type2*. Pierwsza opcja jest zdefiniowanie to bezpośrednia konwersji z *type1* do *type2*, i drugą opcją jest określić kombinację konwersje z *type1* do  *type2*.

Poniższy przykład spowoduje wygenerowanie C2594. Sugerowane rozwiązanie błędu jest sekwencją konwersje:

```
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```