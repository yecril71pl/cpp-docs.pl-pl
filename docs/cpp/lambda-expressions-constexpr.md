---
title: wyrażenia constexpr wyrażeń lambda w języku C++
ms.date: 04/08/2019
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
ms.openlocfilehash: d1bc60a6da813e54c857da38b0164f544216be00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62368698"
---
# <a name="constexpr-lambda-expressions-in-c"></a>wyrażenia constexpr wyrażeń lambda w języku C++

**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Wyrażenie lambda może być zadeklarowana jako **constexpr** lub używany w wyrażeniu stałym, podczas inicjowania każdej składowej danych, który przechwytuje, lub wprowadza jest dozwolona w wyrażeniu stałym.

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

Wyrażenie lambda jest niejawnie **constexpr** Jeśli wynik nie spełnia wymagań **constexpr** funkcji:

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

Jeśli wyrażenie lambda jest jawnie lub niejawnie **constexpr**i przekonwertuj go na wskaźnik funkcji, wynikowy funkcja jest również **constexpr**:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Obiekty funkcji w standardowej bibliotece C++](../standard-library/function-objects-in-the-stl.md)<br/>
[Wywołanie funkcji](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)