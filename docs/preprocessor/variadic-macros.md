---
title: Makra wariadyczne
ms.date: 08/29/2019
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: 171ea797adc1e407a8b7ef0592508653f758df64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216520"
---
# <a name="variadic-macros"></a>Makra wariadyczne

Makra wariadyczne są makrami podobnymi do funkcji, które zawierają zmienną liczbę argumentów.

## <a name="remarks"></a>Uwagi

Aby można było używać makr wariadyczne, wielokropek może być określony jako ostatni argument formalny w definicji makra, a identyfikator `__VA_ARGS__` zastępczy może być używany w definicji w celu wstawienia dodatkowych argumentów.  `__VA_ARGS__`jest zastępowany przez wszystkie argumenty, które pasują do wielokropka, w tym przecinki między nimi.

Standard C określa, że co najmniej jeden argument musi być przekazywać do wielokropka, aby upewnić się, że makro nie jest rozpoznawane jako wyrażenie z końcowym przecinkiem. Tradycyjna implementacja C++ firmy Microsoft pomija końcowy przecinek, jeśli żadne argumenty nie są przekazane do wielokropka.

## <a name="example"></a>Przykład

```cpp
// variadic_macros.cpp
#include <stdio.h>
#define EMPTY

#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }
#define CHECK3(...) { printf(__VA_ARGS__); }
#define MACRO(s, ...) printf(s, __VA_ARGS__)

int main() {
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print

    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");

    // always invokes printf in the macro
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");

    MACRO("hello, world\n");

    MACRO("error\n", EMPTY); // would cause error C2059, except VC++
                             // suppresses the trailing comma
}
```

```Output
here are some varargs1(1)
here are some varargs2(4)
here are some varargs3(5)
hello, world
error
```

## <a name="see-also"></a>Zobacz także

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)
