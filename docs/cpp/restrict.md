---
title: ograniczenie
ms.date: 02/09/2018
f1_keywords:
- restrict_cpp
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
ms.openlocfilehash: a0108cff3d6b98fd929b7888d2ad718e7b6b3a64
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213258"
---
# <a name="restrict"></a>ograniczenie

**Specyficzne dla firmy Microsoft**

W przypadku zastosowania do deklaracji lub definicji funkcji, która zwraca typ wskaźnika, **`restrict`** informuje kompilator, że funkcja zwraca obiekt, który nie jest *aliasem*, do którego odwołuje się jakikolwiek inny wskaźnik. Pozwala to kompilatorowi na wykonywanie dodatkowych optymalizacji.

## <a name="syntax"></a>Składnia

> **`__declspec(restrict)`***pointer_return_type* *Funkcja*pointer_return_type ();

## <a name="remarks"></a>Uwagi

Kompilator propaguje **`__declspec(restrict)`** . Na przykład `malloc` Funkcja CRT ma **`__declspec(restrict)`** dekorację i w związku z tym kompilator zakłada, że wskaźniki zainicjowane do lokalizacji pamięci przez `malloc` nie są również aliasem przez poprzednio istniejące wskaźniki.

Kompilator nie sprawdza, czy zwracany wskaźnik nie jest w rzeczywistości aliasem. Jest on odpowiedzialny za Deweloper, aby upewnić się, że program nie ma aliasu wskaźnika oznaczonego modyfikatorem **ogranicz __declspec** .

Aby poznać podobną semantykę zmiennych, zobacz [__restrict](../cpp/extension-restrict.md).

Aby uzyskać kolejną adnotację, która odnosi się do aliasu w funkcji, zobacz [__declspec (noaliasing)](../cpp/noalias.md).

Aby uzyskać informacje na temat **`restrict`** słowa kluczowego, które jest częścią C++ amp, zobacz [ograniczanie (C++ amp)](../cpp/restrict-cpp-amp.md).

## <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie **`__declspec(restrict)`** .

Gdy **`__declspec(restrict)`** jest stosowany do funkcji, która zwraca wskaźnik, informuje kompilator, że pamięć wskazywana przez wartość zwracaną nie jest aliasem. W tym przykładzie wskaźniki `mempool` i `memptr` są globalne, więc kompilator nie może upewnić się, że pamięć, do której się odwołuje, nie jest aliasem. Jednak są one używane w programie `ma` i jego obiekt wywołujący `init` w taki sposób, który zwraca pamięć, do której nie odwołuje się program, dlatego **__decslpec (ograniczenie)** jest używany do ułatwienia Optymalizatorowi. Jest to podobne do tego, jak nagłówki CRT dekorować funkcje alokacji, takie jak przy `malloc` użyciu, **`__declspec(restrict)`** Aby wskazać, że zawsze zwracają pamięć, która nie może być aliasem przez istniejące wskaźniki.

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

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)<br/>
[__declspec](../cpp/declspec.md)<br/>
[__declspec (noalias)](../cpp/noalias.md)
