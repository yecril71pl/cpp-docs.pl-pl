---
title: Makra wariadyczne
ms.date: 11/04/2016
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: 0674359b8f620c2b5023ce2ef75b4e247ae765f1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50547458"
---
# <a name="variadic-macros"></a>Makra wariadyczne

Makra Wariadyczne są funkcyjne makra, które zawierają zmienną liczbę argumentów.

## <a name="remarks"></a>Uwagi

Aby użyć makra wariadyczne, wielokropka może zostać określony jako ostatni argument formalny w definicji makra, a identyfikator zastąpienie `__VA_ARGS__` może służyć w definicji można wstawić dodatkowych argumentów.  `__VA_ARGS__` zastępuje wszystkie argumenty, które odpowiadają wielokropka, w tym oddzielając je przecinkami.

Standard języka C Określa, że co najmniej jednego argumentu, muszą być przekazywane do wielokropka, aby upewnić się, że makra nie rozpoznać wyrażenia z przecinkiem.  Implementacja języka Visual C++ blokuje wyświetlanie przecinkiem, jeśli żadne argumenty są przekazywane do wielokropka.

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

## <a name="see-also"></a>Zobacz też

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)