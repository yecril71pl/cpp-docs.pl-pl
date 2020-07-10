---
title: Ostrzeżenie kompilatora (poziom 1) C4750
description: Opisuje MSVC kompilatora ostrzeżeń C4750 o możliwym przepełnieniu stosu.
ms.date: 07/08/2020
f1_keywords:
- C4750
helpviewer_keywords:
- C4750
ms.assetid: b0b2c938-7d2a-4c36-8270-7daee15ffee3
ms.openlocfilehash: 9a22bdda407b02b8723b7198d62289d39f62792d
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180971"
---
# <a name="compiler-warning-level-1-c4750"></a>Ostrzeżenie kompilatora (poziom 1) C4750

> "*Identyfikator*": funkcja zawierająca _alloca () została wbudowana w pętlę

## <a name="remarks"></a>Uwagi

Funkcja "*Identifier*" wymusza rozszerzanie wbudowanej [`_alloca`](../../c-runtime-library/reference/alloca.md) funkcji wewnątrz pętli, co może spowodować przepełnienie stosu podczas wykonywania pętli.

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Upewnij się, że funkcja *'id*nie jest modyfikowana przy użyciu [`__forceinline`](../../cpp/inline-functions-cpp.md) specyfikatora.

1. Upewnij się, że funkcja "*Identifier*" nie zawiera [`_alloca`](../../c-runtime-library/reference/alloca.md) funkcji, która jest zawarta w pętli.

1. Nie określaj [`/O1`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) [`/O2`](../../build/reference/o1-o2-minimize-size-maximize-speed.md) przełącznika,, [`/Ox`](../../build/reference/ox-full-optimization.md) lub [`/Og`](../../build/reference/og-global-optimizations.md) kompilacji.

1. Umieść [`_alloca`](../../c-runtime-library/reference/alloca.md) funkcję w [instrukcji try-except](../../cpp/try-except-statement.md) , która będzie przechwytywać przepełnienie stosu.

## <a name="example"></a>Przykład

Poniższy przykład kodu wywołuje `MyFunction` pętlę i `MyFunction` wywołuje `_alloca` funkcję. `__forceinline`Modyfikator powoduje, że wbudowana ekspansja `_alloca` funkcji.

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

## <a name="see-also"></a>Zobacz też

[_alloca](../../c-runtime-library/reference/alloca.md)
