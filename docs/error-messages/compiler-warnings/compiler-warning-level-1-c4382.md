---
title: Kompilator ostrzeżenie (poziom 1) C4382
ms.date: 11/04/2016
f1_keywords:
- C4382
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
ms.openlocfilehash: cca2f8cc13cc8317bac3736e142ef58e126ed994
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390493"
---
# <a name="compiler-warning-level-1-c4382"></a>Kompilator ostrzeżenie (poziom 1) C4382

> Zgłaszanie "*typu*": typ z destruktorem __clrcall lub konstruktorem kopiującym można tylko przechwycić w/CLR: pure modułu

## <a name="remarks"></a>Uwagi

**/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Gdy skompilowano z opcją **/CLR** (nie **/CLR: pure**), obsługa wyjątków oczekuje, że funkcje elementów członkowskich w typie natywnym za [__cdecl](../../cpp/cdecl.md) i nie [__clrcall](../../cpp/clrcall.md). Typy natywne za pomocą funkcji elementów członkowskich przy użyciu `__clrcall` konwencji wywoływania, nie można przechwycić w module, który został skompilowany przy użyciu **/CLR**.

Jeśli wyjątek zostanie zgłoszony w module, który został skompilowany przy użyciu **/CLR: pure**, można zignorować to ostrzeżenie.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4382.

```cpp
// C4382.cpp
// compile with: /clr /W1 /c
struct S {
   __clrcall ~S() {}
};

struct T {
   ~T() {}
};

int main() {
   S s;
   throw s;   // C4382

   S * ps = &s;
   throw ps;   // OK

   T t;
   throw t;   // OK
}
```