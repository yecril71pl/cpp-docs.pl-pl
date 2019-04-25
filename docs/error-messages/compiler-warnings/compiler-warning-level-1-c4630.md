---
title: Kompilator ostrzeżenie (poziom 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 98ea72bef0cb95163604144c1069a13c3b27d81c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324535"
---
# <a name="compiler-warning-level-1-c4630"></a>Kompilator ostrzeżenie (poziom 1) C4630

'symbol': Specyfikator klasy magazynu "extern" niedozwolony w definicji składowej

Element członkowski danych lub funkcji składowej jest zdefiniowany jako `extern`. Składowe nie mogą być zewnętrznych, mimo że można całe obiekty. Kompilator ignoruje `extern` — słowo kluczowe. Poniższy przykład spowoduje wygenerowanie C4630:

```
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```