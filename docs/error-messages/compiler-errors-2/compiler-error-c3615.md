---
title: Błąd kompilatora C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: e966295b5ab63350828ddb73d6791a9e30bb5c59
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652221"
---
# <a name="compiler-error-c3615"></a>Błąd kompilatora C3615

> Funkcja constexpr "*funkcja*" nie może być wyrażeniem stałym

Funkcja *funkcja* nie może być oszacowane jako `constexpr` w czasie kompilacji. Jako `constexpr`, funkcja może wywołać tylko inne `constexpr` funkcji.

## <a name="example"></a>Przykład

Program Visual Studio 2017 niepoprawnie zgłasza błąd, gdy lewostronny operand warunkowo oceny operacji jest nieprawidłowy w `constexpr` kontekstu. Poniższy kod jest kompilowany w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

```cpp
// C3615.cpp
// Compile with: /c

template<int N>
struct myarray
{
    int size() const { return N; }
};

constexpr bool f(const myarray<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615 starting in Visual Studio 2017
}
```

Aby rozwiązać ten problem, albo zadeklarować `array::size()` pełnią `constexpr` lub usuń `constexpr` kwalifikator z `f`.