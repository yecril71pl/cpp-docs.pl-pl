---
title: Kompilator ostrzeżenie (poziom 4) C4481
ms.date: 11/04/2016
f1_keywords:
- C4481
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
ms.openlocfilehash: f88a61a40a789c31e80875d785b95136ac69253c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466940"
---
# <a name="compiler-warning-level-4-c4481"></a>Kompilator ostrzeżenie (poziom 4) C4481

użyte rozszerzenie niestandardowe: specyfikator "— słowo kluczowe" override

Słowo kluczowe użyto nie znajduje się w C++, standardowa, na przykład jeden specyfikatorów przesłonięć, które działa także w ramach/CLR.  Aby uzyskać więcej informacji, zobacz,

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Specyfikatory przesłonięć](../../windows/override-specifiers-cpp-component-extensions.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4481.

```
// C4481.cpp
// compile with: /W4 /c
class B {
   virtual void f(unsigned);
};

class C : B {
   void f(unsigned) override;   // C4481
   void f2(unsigned);
};
```