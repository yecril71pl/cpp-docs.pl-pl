---
title: Błąd kompilatora C3736
ms.date: 11/04/2016
f1_keywords:
- C3736
helpviewer_keywords:
- C3736
ms.assetid: 579b773c-41e7-40ea-8382-2e3ce2667f4c
ms.openlocfilehash: e31d68a13ebd9c5267fd285d43ebc66ae8b53182
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584200"
---
# <a name="compiler-error-c3736"></a>Błąd kompilatora C3736

"event": musi być metodą lub, w przypadku zarządzanych zdarzeń, opcjonalnie składową danych

Natywne i zdarzenia COM muszą być metody. Zdarzenia .NET może być również elementy członkowskie danych.

Poniższy przykład spowoduje wygenerowanie C3736:

```
// C3736.cpp
struct A {
   __event int e();
};

struct B {
   int f;   // C3736
   // The following line resolves the error.
   // int f();
   B(A* a) {
      __hook(&A::e, a, &B::f);
   }
};

int main() {
}
```