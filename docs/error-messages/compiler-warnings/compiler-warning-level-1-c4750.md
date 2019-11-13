---
title: Ostrzeżenie kompilatora (poziom 1) C4750
ms.date: 11/04/2016
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 35b57cf88bf9f9a170a05af890632316b7030838
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052401"
---
# <a name="compiler-warning-level-1-c4750"></a>Ostrzeżenie kompilatora (poziom 1) C4750

"Identyfikator": funkcja zawierająca _alloca () została wbudowana w pętlę

Funkcja "identifier" wymusza rozszerzanie wbudowanej funkcji [_alloca](../../c-runtime-library/reference/alloca.md) wewnątrz pętli, co może spowodować przepełnienie stosu podczas wykonywania pętli.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że funkcja "identifier" nie jest modyfikowana przy użyciu specyfikatora [__forceinline](../../cpp/inline-functions-cpp.md) .

1. Upewnij się, że funkcja "identifier" nie zawiera funkcji [_alloca](../../c-runtime-library/reference/alloca.md) , która jest zawarta w pętli.

1. Nie określaj przełącznika kompilacji [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/OX](../../build/reference/ox-full-optimization.md)lub [/og](../../build/reference/og-global-optimizations.md) .

1. Umieść funkcję [_alloca](../../c-runtime-library/reference/alloca.md) w [instrukcji try-except](../../cpp/try-except-statement.md) , która będzie przechwytywać przepełnienie stosu.

## <a name="example"></a>Przykład

Poniższy przykład kodu wywołuje `MyFunction` w pętli, a `MyFunction` wywołuje funkcję `_alloca`. Modyfikator `__forceinline` powoduje rozszerzenie wbudowanej funkcji `_alloca`.

```cpp
// c4750.cpp
// compile with: /O2 /W1 /c
#include <intrin.h>

char * volatile newstr;

__forceinline void myFunction(void) // C4750 warning
{
// The _alloca function does not require a __try/__except
// block because the example uses compiler option /c.
    newstr = (char * volatile) _alloca(1000);
}

int main(void)
{
    for (int i=0; i<50000; i++)
       myFunction();
    return 0;
}
```

## <a name="see-also"></a>Zobacz także

[_alloca](../../c-runtime-library/reference/alloca.md)