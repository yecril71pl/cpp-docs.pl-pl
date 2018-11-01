---
title: Ostrzeżenie kompilatora C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 71a3d903ba32fecac4b2d8bfc3e0a93f19d0f4ed
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473178"
---
# <a name="compiler-warning-c4484"></a>Ostrzeżenie kompilatora C4484

"override_function": pasuje do metody bazowej klasy referencyjnej "base_class_function", ale nie jest oznaczona "virtual", "new" lub "override"; przyjęto "new" (a nie "virtual")

Podczas kompilowania za pomocą **/CLR**, kompilator niejawnie nie zastępuje funkcję klasy bazowej, która oznacza, że funkcja otrzyma nowe gniazdo w vtable. Aby rozwiązać problem, należy jawnie określić, czy funkcja jest przesłonięciem.

Aby uzyskać więcej informacji, zobacz:

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../windows/override-cpp-component-extensions.md)

- [New (nowe gniazdo w vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 zawsze jest wystawiany jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma może pominąć C4484.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4484.

```
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```