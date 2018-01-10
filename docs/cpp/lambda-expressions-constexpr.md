---
title: "Wyrażenia Lambda w języku C++ constexpr | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 07/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: lambda expressions [C++], constexpr
ms.assetid: b56346cd-fbff-475f-aeaa-ed2010c6d6f7
caps.latest.revision: "0"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 307ce6ab87ca36de561ebcf1ad8bd30eb73e4192
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="constexpr-lambda-expressions-in-c"></a>constexpr wyrażenia Lambda w języku C++
**Visual Studio 2017 wersji 15.3 i nowszych** (dostępnych z [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): wyrażenia lambda, może być zadeklarowana jako `constexpr` lub użyć w wyrażeniu zawartość podczas inicjowania dla każdego elementu członkowskiego danych it Przechwytuje lub wprowadza jest dozwolona w wyrażeniu stałym.  

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
Wyrażenie lambda jest niejawnie `constexpr` Jeśli wynik spełnia wymagania `constexpr` funkcji:
```cpp
    auto answer = [](int n) 
    {
        return 32 + n; 
    };

    constexpr int response = answer(10);
``` 
Jeśli wyrażenie lambda jest jawnie lub niejawnie `constexpr`i przekonwertować go na wskaźnik funkcji, wynikowa funkcja jest również `constexpr`:

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Obiekty funkcji w standardowej bibliotece C++](../standard-library/function-objects-in-the-stl.md)   
 [Wywołania funkcji](../cpp/function-call-cpp.md)   
 [for_each](../standard-library/algorithm-functions.md#for_each)