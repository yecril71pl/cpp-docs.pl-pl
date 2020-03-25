---
title: Błąd kompilatora C3615
ms.date: 10/24/2017
f1_keywords:
- C3615
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
ms.openlocfilehash: c1a5b6edbc87e14de267cf962dc2b1a71dd6be12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200541"
---
# <a name="compiler-error-c3615"></a>Błąd kompilatora C3615

> Funkcja constexpr "*Function*" nie może skutkować wyrażeniem stałym

Nie można ocenić *funkcji* funkcji jako `constexpr` w czasie kompilacji. Aby `constexpr`, funkcja może wywołać tylko inne funkcje `constexpr`.

## <a name="example"></a>Przykład

Program Visual Studio 2017 poprawnie zgłasza błąd, gdy operand po lewej stronie operacji oceniania warunkowego jest nieprawidłowy w kontekście `constexpr`. Poniższy kod kompiluje się w programie Visual Studio 2015, ale nie w programie Visual Studio 2017.

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

Aby rozwiązać ten problem, należy zadeklarować funkcję `array::size()` jako `constexpr` lub usunąć kwalifikator `constexpr` z `f`.
