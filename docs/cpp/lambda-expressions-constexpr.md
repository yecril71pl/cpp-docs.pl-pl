---
title: wyrażenia lambda constexpr w języku C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: 24c70732093447649b3cfb460f63b2181efdf806
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213349"
---
# <a name="constexpr-lambda-expressions-in-c"></a>wyrażenia lambda constexpr w języku C++

**Visual Studio 2017 w wersji 15,3 lub nowszej** (dostępny w [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)): wyrażenie lambda może być zadeklarowane jako **`constexpr`** lub używane w wyrażeniu stałym, gdy Inicjalizacja każdego elementu członkowskiego, który przechwytuje lub wprowadził, jest dozwolony w wyrażeniu stałym.

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

Wyrażenie lambda jest niejawnie, **`constexpr`** jeśli jego wynik spełnia wymagania **`constexpr`** funkcji:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Jeśli wyrażenie lambda jest niejawnie lub jawnie **`constexpr`** i zostanie przekonwertowane na wskaźnik funkcji, wynikiem funkcji jest również **`constexpr`** :

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Obiekty funkcji w standardowej bibliotece języka C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Wywołanie funkcji](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
