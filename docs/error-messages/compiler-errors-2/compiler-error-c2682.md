---
title: Błąd kompilatora C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: 8a9ec2f59f362df284e9bd5cd8df6ae986d59d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266273"
---
# <a name="compiler-error-c2682"></a>Błąd kompilatora C2682

Nie można użyć casting_operator do konwersji z 'Typ1' na 'type2'

Operator rzutowania nastąpiła próba konwersji między niezgodne typy. Na przykład nie można użyć [dynamic_cast](../../cpp/dynamic-cast-operator.md) operatora, aby przekonwertować wskaźnik do odwołania. `dynamic_cast` Nie można używać operatora w celu rzutowania z kwalifikatorów. Wszystkie kwalifikatory dla typów muszą być zgodne.

Możesz użyć `const_cast` operatora, aby usunąć atrybuty, takie jak `const`, `volatile`, lub `__unaligned`.

Poniższy przykład spowoduje wygenerowanie C2682:

```
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

Poniższy przykład spowoduje wygenerowanie C2682:

```
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```