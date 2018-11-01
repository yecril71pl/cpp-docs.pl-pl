---
title: A.24   Przykład klauzuli prywatnej
ms.date: 11/04/2016
ms.assetid: f90a5b49-81ff-4746-ae03-37bbd33f6c08
ms.openlocfilehash: facf5b953b26d284f6bfed4f35a9162f6d2bf212
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552961"
---
# <a name="a24---example-of-the-private-clause"></a>A.24   Przykład klauzuli prywatnej

`private` — Klauzula ([sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25) równoległego regionu działa tylko w dla zakresu leksykalne regionu, a nie dla zakresu dynamicznego regionu.  W związku z tym w następującym przykładzie, wszelkie używa zmiennej *a* w `for` pętli w procedurze *f* odwołuje się do prywatnej kopii *a*, podczas użycia w Procedura *g* odwołuje się do globalnej *a*.

```
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```