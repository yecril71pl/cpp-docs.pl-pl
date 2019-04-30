---
title: Kompilator ostrzeżenie (poziom 3) C4243
ms.date: 11/04/2016
f1_keywords:
- C4243
helpviewer_keywords:
- C4243
ms.assetid: ca72f9ad-ce0b-43a9-a68c-106e1f8b90ef
ms.openlocfilehash: e08a8538c93681c59779f681812a9ba8f7e316a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402206"
---
# <a name="compiler-warning-level-3-c4243"></a>Kompilator ostrzeżenie (poziom 3) C4243

Konwersja 'conversion type' istnieje z 'Typ1' na 'Typ2', ale jest niedostępna

Wskaźnik do klasy pochodnej jest konwertowany na wskaźnik do klasy bazowej, ale klasa pochodna dziedziczy klasa bazowa z dostępem do prywatnych lub chronionych.

Poniższy przykład spowoduje wygenerowanie C4243:

```
// C4243.cpp
// compile with: /W3
// C4243 expected
struct B {
   int f() {
      return 0;
   };
};

struct D : private B {};
struct E : public B {};

int main() {
   // Delete the following 2 lines to resolve.
   int (D::* d)() = (int(D::*)()) &B::f;
   d;

   int (E::* e)() = (int(E::*)()) &B::f; // OK
   e;
}
```