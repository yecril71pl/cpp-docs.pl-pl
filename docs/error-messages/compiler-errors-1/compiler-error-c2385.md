---
title: Błąd kompilatora C2385
ms.date: 11/04/2016
f1_keywords:
- C2385
helpviewer_keywords:
- C2385
ms.assetid: 6d3dd1f2-e56d-49d7-865c-6a9acdb17417
ms.openlocfilehash: bffb4c1088c41832e69b0c6f161b47f6f9f08d06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571395"
---
# <a name="compiler-error-c2385"></a>Błąd kompilatora C2385

niejednoznaczne dostęp do 'składowa'

Element członkowski może pochodzić z więcej niż jeden obiekt (jest dziedziczone z więcej niż jeden obiekt).  Aby rozwiązać ten problem

- Element członkowski upewnij się jednoznaczna, zapewniając rzutowania.

- Zmień nazwę niejednoznaczne elementy członkowskie w klasach bazowych.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2385.

```
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