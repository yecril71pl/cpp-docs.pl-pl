---
title: Błąd kompilatora C2743
ms.date: 11/04/2016
f1_keywords:
- C2743
helpviewer_keywords:
- C2743
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
ms.openlocfilehash: 03cd7c13e093be5073b3df7e7cf29dda870bc47a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531004"
---
# <a name="compiler-error-c2743"></a>Błąd kompilatora C2743

"type": nie można przechwycić natywnego typu destruktorem __clrcall lub konstruktorem kopiującym

Moduł skompilowany z **/CLR** podjęto próbę wykrycia tego typu natywnego i gdzie używa typu destruktorem lub konstruktorem kopiującym `__clrcall` konwencji wywoływania.

Gdy skompilowano z opcją **/CLR**, obsługa wyjątków oczekuje, że funkcje elementów członkowskich w typie natywnym za [__cdecl](../../cpp/cdecl.md) i nie [__clrcall](../../cpp/clrcall.md). Typy natywne za pomocą funkcji elementów członkowskich przy użyciu `__clrcall` konwencji wywoływania, nie można przechwycić w module, który został skompilowany przy użyciu **/CLR**.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2743.

```
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