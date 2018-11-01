---
title: Błąd kompilatora C3421
ms.date: 11/04/2016
f1_keywords:
- C3421
helpviewer_keywords:
- C3421
ms.assetid: b52050c6-17a4-424a-8894-337b0cec7010
ms.openlocfilehash: 399224a3d091a26066a03df0c77511997ae2403c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448909"
---
# <a name="compiler-error-c3421"></a>Błąd kompilatora C3421

"type": nie można wywołać finalizatora dla tej klasy, ponieważ jest on niedostępny lub nie istnieje

Finalizator jest niejawnie prywatne, dlatego nie można wywołać z poza jego typie otaczającym.

Aby uzyskać więcej informacji, zobacz [destruktory i finalizatory w instrukcje: Definiowanie oraz stosowanie klas i struktur (C + +/ CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3421.

```
// C3421.cpp
// compile with: /clr
ref class A {};

ref class B {
   !B() {}

public:
   ~B() {}
};

int main() {
   A a;
   a.!A();   // C3421

   B b;
   b.!B();   // C3421
}
```