---
title: Makra wariadyczne
ms.date: 11/04/2016
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
ms.openlocfilehash: da159ef979ccc38845064debebae55356bc9e9bd
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022843"
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

## <a name="see-also"></a>Zobacz także

[Makra (C/C++)](../preprocessor/macros-c-cpp.md)