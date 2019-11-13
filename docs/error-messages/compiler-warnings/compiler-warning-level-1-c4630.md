---
title: Ostrzeżenie kompilatora (poziom 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 893364183594782b825377f57fa4e525338d62d8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052555"
---
# <a name="compiler-warning-level-1-c4630"></a>Ostrzeżenie kompilatora (poziom 1) C4630

"symbol": specyfikator klasy magazynu "extern" jest niedozwolony w definicji składowej

Element członkowski danych lub funkcja członkowska jest definiowana jako `extern`. Elementy członkowskie nie mogą być zewnętrzne, chociaż mogą to być wszystkie obiekty. Kompilator ignoruje słowo kluczowe `extern`. Poniższy przykład generuje C4630:

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```