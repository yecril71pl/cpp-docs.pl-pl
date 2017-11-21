---
title: noalias | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: noalias_cpp
dev_langs: C++
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1b70c5e41b3380de241939249f51449ba65406c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="noalias"></a>noalias

**Dotyczące firmy Microsoft**

`noalias`oznacza, że wywołanie funkcji nie Modyfikuj lub odwołać widoczny stan globalny i tylko modyfikuje pamięci wskazywał *bezpośrednio* przez parametry wskaźnika (pierwszego poziomu elementów pośrednich).

Jeśli funkcja jest oznaczony jako `noalias`, optymalizator może przyjmować, że oprócz parametrów się elementów pośrednich tylko pierwszy poziom parametrów wskaźnika są odwołuje się do lub zmodyfikować wewnątrz funkcji. Zbiór wszystkich danych, które nie jest zdefiniowana lub do których odwołuje się poza zasięgiem kompilacji jest widoczny stan globalny, a ich adres nie jest brana. Zakres kompilacji jest wszystkich plików źródłowych ([opcję/LTCG (Generowanie kodu w czasie Link)](../build/reference/ltcg-link-time-code-generation.md) kompilacje) lub jednym pliku źródłowym (z systemem innym niż**opcję/LTCG** kompilacji).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, za pomocą `__declspec(restrict)` i `__declspec(noalias)`. Zwykle pamięci zwrócony z `malloc` jest `restrict` ponieważ nagłówki CRT są odpowiednio oznaczone.

Jednak w tym przykładzie wskaźniki `mempool` i `memptr` są globalne, więc kompilator nie ma gwarancji, że pamięć nie podlega aliasów. Funkcje, które zwracają wskaźników za pomocą dekoracji `__declspec(restrict)` informuje kompilator pamięć wskazywana przez wartości zwracanej nie jest używane z aliasem.

Funkcja w przykładzie, który uzyskuje dostęp do pamięci z dekoracji `__declspec(noalias)` informuje kompilator, że ta funkcja nie zakłóca stan globalny z wyjątkiem za pośrednictwem wskaźniki na swojej liście parametrów.

```C
// declspec_noalias.c
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

[__declspec](../cpp/declspec.md)  
[Słowa kluczowe](../cpp/keywords-cpp.md)