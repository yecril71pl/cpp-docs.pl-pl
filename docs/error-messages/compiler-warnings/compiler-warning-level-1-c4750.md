---
title: Kompilator ostrzeżenie (poziom 1) C4750
ms.date: 11/04/2016
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 2a6d83074f180a455e9c305fb4ca8ea270d0a593
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037733"
---
# <a name="compiler-warning-level-1-c4750"></a>Kompilator ostrzeżenie (poziom 1) C4750

'Identyfikator': funkcja zawierająca _alloca() została wbudowana w pętlę

Funkcja 'Identyfikator' Wymusza wbudowane rozwijanie z [_alloca](../../c-runtime-library/reference/alloca.md) funkcji w pętli, która może spowodować przepełnienie stosu podczas wykonywania pętli.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, czy funkcja 'Identyfikator' nie jest modyfikowany za pomocą [__forceinline](../../cpp/inline-functions-cpp.md) specyfikator.

1. Upewnij się, że funkcja 'Identyfikator' nie zawiera [_alloca](../../c-runtime-library/reference/alloca.md) funkcja, która jest zawarta w pętli.

1. Nie określaj [/O1](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md), [ox](../../build/reference/ox-full-optimization.md), lub [/Og](../../build/reference/og-global-optimizations.md) przełącznika kompilacji.

1. Miejsce [_alloca](../../c-runtime-library/reference/alloca.md) działa w programach [spróbuj-except, instrukcja](../../cpp/try-except-statement.md) , będzie przechwytywać przepełnienia stosu.

## <a name="example"></a>Przykład

Poniższy kod wywoła przykład `MyFunction` w pętli, a `MyFunction` wywołania `_alloca` funkcji. `__forceinline` Modyfikator powoduje, że rozszerzenie wbudowane `_alloca` funkcji.

```
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