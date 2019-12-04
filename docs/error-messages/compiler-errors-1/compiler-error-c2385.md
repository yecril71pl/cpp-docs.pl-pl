---
title: Błąd kompilatora C2385
ms.date: 11/04/2016
f1_keywords:
- C2385
helpviewer_keywords:
- C2385
ms.assetid: 6d3dd1f2-e56d-49d7-865c-6a9acdb17417
ms.openlocfilehash: 1247e4da05d65677f602a82591efd3e0c0c374e0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745258"
---
# <a name="compiler-error-c2385"></a>Błąd kompilatora C2385

niejednoznaczny dostęp do elementu "member"

Element członkowski może pochodzić z więcej niż jednego obiektu (jest on Dziedziczony z więcej niż jednego obiektu).  Aby rozwiązać ten problem,

- Ustaw element członkowski jako niejednoznaczny, dostarczając rzutowanie.

- Zmień nazwy niejednoznacznych elementów członkowskich w klasach bazowych.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2385.

```cpp
// C2385.cpp
// C2385 expected
#include <stdio.h>

struct A
{
    void x(int i)
    {
        printf_s("\nIn A::x");
    }
};

struct B
{
    void x(char c)
    {
        printf_s("\nIn B::x");
    }
};

// Delete the following line to resolve.
struct C : A, B {}

// Uncomment the following 4 lines to resolve.
// struct C : A, B
// {
//     using B::x;
//     using A::x;
// };

int main()
{
    C aC;
    aC.x(100);
    aC.x('c');
}

struct C : A, B
{
    using B::x;
    using A::x;
};
```
