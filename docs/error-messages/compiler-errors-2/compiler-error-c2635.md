---
title: Błąd kompilatora C2635
ms.date: 11/04/2016
f1_keywords:
- C2635
helpviewer_keywords:
- C2635
ms.assetid: 9deca2a8-2d61-42eb-9783-6578132ee3fb
ms.openlocfilehash: 0c31bcc4062aec1d939c801f9b5ee420f2f4fcb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367853"
---
# <a name="compiler-error-c2635"></a>Błąd kompilatora C2635

Nie można przekonwertować "identifier1*" na "identifier2\*"; technicznego konwersję z wirtualnej klasy podstawowej

Konwersja wymaga rzutowania z `virtual` podstawowej klasy do klasy pochodnej, która nie jest dozwolona.

Poniższy przykład spowoduje wygenerowanie C2635:

```
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