---
title: noalias | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 02/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noalias_cpp
dev_langs:
- C++
helpviewer_keywords:
- noalias __declspec keyword
- __declspec keyword [C++], noalias
ms.assetid: efafa8b0-7f39-4edc-a81e-d287ae882c9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 56ee12f65ff9efe9f3b048d061b80aef691eb0f2
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404398"
---
# <a name="noalias"></a>noalias

**Microsoft Specific**

**noalias** oznacza, że wywołanie funkcji nie Modyfikuj lub odwoływać się widoczny stan globalny i modyfikuje tylko wskazywana pamięć *bezpośrednio* przez wskaźnik parametry (pierwszy na poziomie elementów pośrednich).

Jeśli funkcja jest oznaczona jako **noalias**, optymalizator, można założyć, że oprócz parametrów samodzielnie, tylko pierwszy poziom elementów pośrednich, wskaźnik parametrów są przywoływane lub modyfikowane wewnątrz funkcji. Widoczny stan globalny to zestaw wszystkich danych, które nie jest zdefiniowany lub do których odwołuje się poza zakresem kompilacji, a nie wykonują swojego adresu. Zakres kompilacji jest wszystkie pliki źródłowe ([opcję/LTCG (Generowanie kodu Link-time)](../build/reference/ltcg-link-time-code-generation.md) kompilacje) lub w jednym pliku źródłowym (non -**opcję/LTCG** kompilacji).

**Noalias** adnotacja ma zastosowanie tylko w treści funkcji adnotacjami. Oznaczanie funkcję jako **__declspec(noalias)** nie ma wpływu na tworzenie aliasów wskaźników zwróconą przez funkcję.

Aby inną adnotację, które mogą mieć wpływ na tworzenie aliasów, zobacz [__declspec(restrict)](../cpp/restrict.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie **__declspec(noalias)**.

Gdy funkcja `multiply` że dostępy do pamięci jest oznaczona **__declspec(noalias)**, jego informuje kompilator, ta funkcja nie zmodyfikuje stan globalny, z wyjątkiem przez wskaźniki na liście parametrów.

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

## <a name="see-also"></a>Zobacz także
 [__declspec](../cpp/declspec.md)  
 [Słowa kluczowe](../cpp/keywords-cpp.md)  
 [__declspec(restrict)](../cpp/restrict.md)  
