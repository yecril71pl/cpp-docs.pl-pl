---
title: Błąd kompilatora C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: ade657f9ada2a2249d2f96b7caada7b9719195d1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759337"
---
# <a name="compiler-error-c2594"></a>Błąd kompilatora C2594

"operator": niejednoznaczne konwersje z "type1" na "type2"

Konwersja z *Type1* na *Type2* była większa od innych. Sugerujemy dwa możliwe rozwiązania do konwersji z *Type1* na *Type2*. Pierwsza opcja polega na zdefiniowaniu bezpośredniej konwersji z *Type1* na *Type2*, a drugiej opcji jest określenie sekwencji konwersji z *Type1* do *Type2*.

Poniższy przykład generuje C2594. Sugerowana rozdzielczość do błędu to sekwencja konwersji:

```cpp
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
