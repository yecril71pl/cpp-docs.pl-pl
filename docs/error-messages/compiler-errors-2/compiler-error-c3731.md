---
title: Błąd kompilatora C3731
ms.date: 11/04/2016
f1_keywords:
- C3731
helpviewer_keywords:
- C3731
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
ms.openlocfilehash: 5acc33869648f83cd44bc557128c685f521ddf88
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50496060"
---
# <a name="compiler-error-c3731"></a>Błąd kompilatora C3731

niezgodne zdarzenie "function1" i procedury obsługi 'function2'; Źródło zdarzenia i procedury obsługi zdarzeń muszą być tego samego typu

Źródło zdarzeń i odbiorcę zdarzeń musi mieć tego samego typu (na przykład `native` a `com` typy). Aby naprawić ten błąd, należy typów źródła zdarzeń i dopasowania procedury obsługi zdarzeń.

Poniższy przykład spowoduje wygenerowanie C3731:

```
// C3731.cpp
// compile with: /clr
#using <mscorlib.dll>
[event_source(native)]
struct A {
   __event void MyEvent();
};

[event_receiver(managed)]
// try the following line instead
// [event_receiver(native)]
struct B {
   void func();
   B(A a) {
      __hook(&A::MyEvent, &a, &B::func);   // C3731
   }
};

int main() {
}
```