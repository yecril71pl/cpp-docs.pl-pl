---
title: Błąd kompilatora C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: 17a210e2a514af1ffd62bf38651c4d17bd1fe32b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230795"
---
# <a name="compiler-error-c3615"></a>Błąd kompilatora C3615

> Funkcja constexpr "*Function*" nie może skutkować wyrażeniem stałym

Nie można ocenić *funkcji* funkcji w **`constexpr`** czasie kompilacji. Aby było możliwe **`constexpr`** , funkcja może wywołać tylko inne **`constexpr`** funkcje.

## <a name="example"></a>Przykład

Program Visual Studio 2017 poprawnie zgłasza błąd, gdy operand po lewej stronie operacji oceniania warunkowego jest nieprawidłowy w **`constexpr`** kontekście. Poniższy kod kompiluje się w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

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

Aby rozwiązać ten problem, należy zadeklarować `array::size()` funkcję jako **`constexpr`** lub usunąć **`constexpr`** kwalifikator z elementu `f` .
