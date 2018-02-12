---
title: noalias | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 02/09/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- noalias_cpp
dev_langs:
- C++
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6fd57b10aba4298ff7facd725ab3ce1934ccf1ab
ms.sourcegitcommit: f3c398b1c7dbf36ab71b5ca89d365b1913afa307
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2018
---
# <a name="noalias"></a>noalias

**Microsoft Specific**

`noalias`oznacza, że wywołanie funkcji nie Modyfikuj lub odwołać widoczny stan globalny i tylko modyfikuje pamięci wskazywał *bezpośrednio* przez parametry wskaźnika (pierwszego poziomu elementów pośrednich).

Jeśli funkcja jest oznaczony jako `noalias`, optymalizator może przyjmować, że oprócz parametrów się elementów pośrednich tylko pierwszy poziom parametrów wskaźnika są odwołuje się do lub zmodyfikować wewnątrz funkcji. Zbiór wszystkich danych, które nie jest zdefiniowana lub do których odwołuje się poza zasięgiem kompilacji jest widoczny stan globalny, a ich adres nie jest brana. Zakres kompilacji jest wszystkich plików źródłowych ([opcję/LTCG (Generowanie kodu w czasie Link)](../build/reference/ltcg-link-time-code-generation.md) kompilacje) lub jednym pliku źródłowym (z systemem innym niż**opcję/LTCG** kompilacji).

`noalias` Adnotacja ma zastosowanie tylko w treści funkcji adnotacjami. Funkcja jako oznaczenie `__declspec(noalias)` nie ma wpływu na aliasów wskaźników zwracane przez funkcję.

Dla innej adnotacji może wpłynąć na aliasów, zobacz [słowo kluczowe __declspec(restrict)](../cpp/restrict.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `__declspec(noalias)`.

Gdy funkcja `multiply` odnoszący się uzyskuje dostęp do pamięci `__declspec(noalias)`, informuje kompilator tej funkcji nie modyfikuje stan globalny z wyjątkiem za pośrednictwem wskaźniki w jego listy parametrów.

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

[__declspec](../cpp/declspec.md)  
[Słowa kluczowe](../cpp/keywords-cpp.md)  
[__declspec(restrict)](../cpp/restrict.md)  
