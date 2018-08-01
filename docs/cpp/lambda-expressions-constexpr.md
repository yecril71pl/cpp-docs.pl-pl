---
title: constexpr, wyrażenia Lambda w języku C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/19/2017
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78fa3de7777ffc6702902cf967a405595caf12f
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39408206"
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr, wyrażenia Lambda w języku C++
**Visual Studio 2017 w wersji 15.3 lub nowszej** (udostępniono [/STD: c ++ 17](../build/reference/std-specify-language-standard-version.md)): Wyrażenie lambda może być zadeklarowana jako **constexpr** lub używana w wyrażeniu zawartość podczas inicjowania każdego z nich element członkowski danych przechwytuje, lub wprowadza jest dozwolona w wyrażeniu stałym.  

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
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Obiekty funkcji w standardowej bibliotece C++](../standard-library/function-objects-in-the-stl.md)   
 [Wywołanie funkcji](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)