---
title: Błąd kompilatora C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 90bc30460cb578d1ed2812e40907a361eeb3b039
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748427"
---
# <a name="compiler-error-c2635"></a>Błąd kompilatora C2635

nie można skonwertować elementu "Identifier1 *" na "identifier2\*"; Konwersja z wirtualnej klasy bazowej jest implikowana

Konwersja wymaga rzutowania z klasy bazowej `virtual` na klasę pochodną, co jest niedozwolone.

Poniższy przykład generuje C2635:

```cpp
// C2635.cpp
class B {};
class D : virtual public B {};
class E : public B {};

int main() {
   B b;
   D d;
   E e;

   D * pD = &d;
   E * pE = &e;
   pD = (D*)&b;   // C2635
   pE = (E*)&b;   // OK
}
```
