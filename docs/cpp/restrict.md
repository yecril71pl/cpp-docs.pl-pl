---
title: Ogranicz | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- restrict_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], restrict
- restrict __declspec keyword
ms.assetid: f39cf632-68d8-4362-a497-2d4c15693689
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5f91288671eaa3dcf4700ec35dae63ffaef172
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="restrict"></a>ograniczenie

**Microsoft Specific**

Gdy jest stosowany do deklaracji lub definicji funkcji zwracającej typ wskaźnika `restrict` informuje kompilator, że funkcja zwraca obiekt, który nie jest *aliasem*, czyli odwołuje się innych wskaźników. Dzięki temu przeprowadzać dodatkowe optymalizacje kompilatora.

## <a name="syntax"></a>Składnia

> **__declspec(restrict)** *pointer_return_type* *function*();  
  
## <a name="remarks"></a>Uwagi

Propaguje kompilator `__declspec(restrict)`. Na przykład CRT `malloc` funkcja ma `__declspec(restrict)` decoration, dlatego kompilator zakłada zainicjowanej do lokalizacji pamięci przez wskaźniki `malloc` również nie są używane z aliasem uprzednio istniejące wskaźniki.

Kompilator nie sprawdza, czy zwrócony wskaźnik nie jest rzeczywiście aliasu. Odpowiada dewelopera upewnij się, program nie alias jest oznaczony atrybutem wskaźnik `restrict __declspec` modyfikator.  
  
Dla podobnych semantyki na zmiennych, zobacz [__restrict](../cpp/extension-restrict.md).
 
Dla innej adnotacji dotyczy aliasów w funkcji, zobacz [__declspec(noalias)](../cpp/noalias.md).
  
Aby uzyskać informacje o **ograniczyć** Zobacz — słowo kluczowe, który jest częścią C++ AMP [ograniczenie (C++ AMP)](../cpp/restrict-cpp-amp.md).  
 
## <a name="example"></a>Przykład  

W poniższym przykładzie pokazano użycie `__declspec(restrict)`.

Gdy `__declspec(restrict)` jest stosowane do funkcji czy zwraca wskaźnik, to informuje kompilator, że pamięć wskazywana przez wartości zwracanej nie jest aliasem. W tym przykładzie wskaźniki `mempool` i `memptr` są globalne, dlatego kompilator nie może być się upewnić, że odnoszą się do pamięci nie jest używane z aliasem. Jednak są używane w ramach `ma` i swojego obiektu wywołującego `init` w taki sposób, który zwraca pamięci, która nie jest w przeciwnym razie odwołuje się programu, więc `__decslpec(restrict)` służy do optymalizacji. To jest podobny do sposobu nagłówki CRT dekoracji alokacji funkcje takie jak `malloc` przy użyciu `__declspec(restrict)` wskazująca zawsze zwracają pamięci, która nie może mieć aliasu przez istniejące wskaźniki.

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

**KOŃCOWY określonych firmy Microsoft**

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)  
[__declspec](../cpp/declspec.md)  
[__declspec(noalias)](../cpp/noalias.md)  
