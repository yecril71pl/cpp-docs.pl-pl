---
title: Ostrzeżenie kompilatora C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 7138f1a3cecaaf75fbab01fd1aee18529b7a3a84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652473"
---
# <a name="compiler-warning-c4485"></a>Ostrzeżenie kompilatora C4485

"override_function": odpowiada metodzie bazowej klasy referencyjnej "base_class_function", ale nie jest oznaczona "new" ani "override"; przyjęto "new" (i "virtual")

Zastępuje metodę dostępu, z lub bez `virtual` — słowo kluczowe, funkcja dostępu klasy bazowej, ale `override` lub `new` specyfikator nie jest częścią nadrzędnych sygnatura funkcji. Dodaj `new` lub `override` specyfikator w celu rozwiązania tego ostrzeżenia.

Zobacz [zastąpienia](../../windows/override-cpp-component-extensions.md) i [new (nowe gniazdo w vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md) Aby uzyskać więcej informacji.

C4485 zawsze jest wystawiany jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma może pominąć C4485.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4485

```
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```