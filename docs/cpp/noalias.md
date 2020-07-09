---
title: noalias
ms.date: 07/07/2020
f1_keywords:
- noalias_cpp
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
ms.openlocfilehash: 70c1f4e8bfa426e858014a78febc424b473a89ae
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127875"
---
# `noalias`

**specyficzne dla firmy Microsoft**

**`noalias`** oznacza, że wywołanie funkcji nie modyfikuje lub nie odwołuje się do widocznego stanu globalnego i tylko modyfikuje pamięć wskazywaną *bezpośrednio* przez parametry wskaźnika (pośrednicy pierwszego poziomu).

Jeśli funkcja jest oznaczona jako adnotacja **`noalias`** , Optymalizator może założyć, że tylko te parametry i tylko wartości pośrednie pierwszego poziomu parametrów wskaźnika, są przywoływane lub modyfikowane wewnątrz funkcji.

**`noalias`** Adnotacja ma zastosowanie tylko w treści funkcji z adnotacjami. Oznaczanie funkcji jako **`__declspec(noalias)`** nie wpływa na aliasy wskaźników zwracanych przez funkcję.

Aby uzyskać kolejną adnotację, która może mieć wpływ na aliasy, zobacz [`__declspec(restrict)`](../cpp/restrict.md) .

## <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie **`__declspec(noalias)`** .

Gdy funkcja `multiply` , która uzyskuje dostęp do pamięci ma adnotacje **`__declspec(noalias)`** , informuje kompilator, że ta funkcja nie modyfikuje stanu globalnego z wyjątkiem wskaźników na liście parametrów.

```C
// declspec_noalias.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1/k++;
    return a;
}

__declspec(noalias) void multiply(float * a, float * b, float * c)
{
    int i, j, k;

    for (j=0; j<P; j++)
        for (i=0; i<M; i++)
            for (k=0; k<N; k++)
                c[i * P + j] =
                          a[i * N + k] *
                          b[k * P + j];
}

int main()
{
    float * a, * b, * c;

    mempool = (float *) malloc(sizeof(float) * (M*N + N*P + M*P));

    if (!mempool)
    {
        puts("ERROR: Malloc returned null");
        exit(1);
    }

    memptr = mempool;
    a = init(M, N);
    b = init(N, P);
    c = init(M, P);

    multiply(a, b, c);
}
```

## <a name="see-also"></a>Zobacz też

[`__declspec`](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[`__declspec(restrict)`](../cpp/restrict.md)
