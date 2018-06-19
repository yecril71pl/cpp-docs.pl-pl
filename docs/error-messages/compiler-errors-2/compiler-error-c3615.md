---
title: C3615 błąd kompilatora | Dokumentacja firmy Microsoft
ms.date: 10/24/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3615
dev_langs:
- C++
helpviewer_keywords:
- C3615
ms.assetid: 5ce96ba9-3d31-49f3-9aa8-24e5cdf6dcfc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1ab43f8e15535614cedf43dba42fef882bf87a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33253397"
---
# <a name="compiler-error-c3615"></a>C3615 błąd kompilatora

> Funkcja constexpr "*funkcja*" nie może być wyrażeniem stałym

Funkcja *funkcja* nie można obliczyć jako `constexpr` w czasie kompilacji. Być `constexpr`, funkcję można wywołać tylko innych `constexpr` funkcji.

## <a name="example"></a>Przykład

2017 usługi Visual Studio niepoprawnie zgłasza błąd, gdy lewostronny operand warunkowo oszacowania operacji jest nieprawidłowy w `constexpr` kontekstu. Poniższy kod tworzy w programie Visual Studio 2015, ale nie w programie Visual Studio 2017 r.

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

Aby rozwiązać ten problem, albo zadeklarować `array::size()` działać jako `constexpr` lub usuń `constexpr` kwalifikator z `f`.