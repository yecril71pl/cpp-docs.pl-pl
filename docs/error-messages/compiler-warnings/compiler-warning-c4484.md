---
title: Ostrzeżenie kompilatora C4484 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b6916bac936ad4b8e67888443f397a4c81c0a956
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022984"
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