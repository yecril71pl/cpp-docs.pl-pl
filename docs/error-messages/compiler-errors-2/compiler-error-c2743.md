---
title: Błąd kompilatora C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: d679ce0df0d43772a6c32aa8e00869ac1a4a082b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759649"
---
# <a name="compiler-error-c2743"></a>Błąd kompilatora C2743

"Type": nie można przechwycić natywnego typu z __clrcall destruktorem lub konstruktorem kopiującym

Moduł skompilowany za pomocą **/CLR** próbował przechwycić wyjątek typu natywnego i gdzie destruktor lub Konstruktor kopiujący typu używa `__clrcall` konwencji wywoływania.

Podczas kompilowania z **/CLR**obsługa wyjątków oczekuje, że funkcje składowe w typie natywnym mają być [__cdecl](../../cpp/cdecl.md) , a nie [__clrcall](../../cpp/clrcall.md). Typy natywne z funkcjami składowymi używającymi konwencji wywoływania `__clrcall` nie mogą być przechwytywane w module skompilowanym za pomocą **/CLR**.

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C2743.

```cpp
// C2743.cpp
// compile with: /clr
public struct S {
   __clrcall ~S() {}
};

public struct T {
   ~T() {}
};

int main() {
   try {}
   catch(S) {}   // C2743
   // try the following line instead
   // catch(T) {}

   try {}
   catch(S*) {}   // OK
}
```
