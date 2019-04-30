---
title: ograniczenie
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: 40c1c05ca72f639829f2d3658497b0e9f3199640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403376"
---
# <a name="restrict"></a>ograniczenie

**Microsoft Specific**

W przypadku zastosowania do deklaracji lub definicji funkcji zwracającej wskaźnik typu **ograniczyć** informuje kompilator, że funkcja zwraca obiekt, który nie jest *aliasem*, oznacza to, że przywoływany przez inne wskaźniki. Dzięki temu kompilator, aby wykonać dodatkowe optymalizacje.

## <a name="syntax"></a>Składnia

> **__declspec(restrict)** *pointer_return_type* *function*();

## <a name="remarks"></a>Uwagi

Kompilator propaguje **__declspec(restrict)**. Na przykład CRT `malloc` funkcja ma **__declspec(restrict)** dekoracji i dlatego kompilator zakłada, zainicjowanej do lokalizacji pamięci przez wskaźniki `malloc` nie jest także aliasowany przez wcześniej istniejące wskaźniki.

Kompilator nie sprawdza, że zwrócony wskaźnik nie jest faktycznie aliasem. Jest odpowiedzialność deweloperów, aby upewnić się, program nie alias jest oznaczona za pomocą wskaźnika **ograniczyć __declspec** modyfikator.

Aby uzyskać podobną semantyką zmiennych, zobacz [element __restrict](../cpp/extension-restrict.md).

Dla innego adnotacji stosowaną w przypadku aliasów w funkcji, zobacz [__declspec(noalias)](../cpp/noalias.md).

Aby uzyskać informacje o **ograniczyć** Zobacz — słowo kluczowe, który jest częścią C++ AMP [ograniczenie (C++ AMP)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie **__declspec(restrict)**.

Gdy **__declspec(restrict)** jest stosowany do funkcji, zwraca wskaźnik, to informuje kompilator, że pamięci wskazywany przez wartość zwracana nie jest aliasem. W tym przykładzie wskaźników `mempool` i `memptr` są globalne, dlatego kompilator nie może być się, że pamięć odnoszą się do nie jest aliasem. Jednak są one używane w ramach `ma` i obiektu wywołującego `init` w sposób, który zwraca pamięci, która nie jest w przeciwnym razie odwołuje się programu, więc **__decslpec(restrict)** umożliwiają Optymalizator. Jest to podobne do jak nagłówki CRT dekoracji funkcji alokacji takich jak `malloc` przy użyciu **__declspec(restrict)** do wskazania, zawsze zwracają pamięć, która nie może być aliasowany przez istniejące wskaźników.

```C
// declspec_restrict.c
// Compile with: cl /W4 declspec_restrict.c
#include <stdio.h>
#include <stdlib.h>

#define M 800
#define N 600
#define P 700

float * mempool, * memptr;

__declspec(restrict) float * ma(int size)
{
    float * retval;
    retval = memptr;
    memptr += size;
    return retval;
}

__declspec(restrict) float * init(int m, int n)
{
    float * a;
    int i, j;
    int k=1;

    a = ma(m * n);
    if (!a) exit(1);
    for (i=0; i<m; i++)
        for (j=0; j<n; j++)
            a[i*n+j] = 0.1f/k++;
    return a;
}

void multiply(float * a, float * b, float * c)
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

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec(noalias)](../cpp/noalias.md)
