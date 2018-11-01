---
title: A.20   Powiązanie dyrektyw określających bariery
ms.date: 11/04/2016
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
ms.openlocfilehash: cf6f20a8539c47ca529af93e65f3a5fe244228d8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652949"
---
# <a name="a20---binding-of-barrier-directives"></a>A.20   Powiązanie dyrektyw określających bariery

Powiązania dyrektywy reguł wywołanie **barierę** dyrektywy, aby powiązać najbliższej otaczającej `parallel` dyrektywy. Aby uzyskać więcej informacji na temat powiązania dyrektywy, zobacz [2.8 sekcji](../../parallel/openmp/2-8-directive-binding.md) na stronie 32.

W poniższym przykładzie, wywołanie funkcji z *głównego* do *sub2* jest zgodne, ponieważ **barierę** (w *sub3*) wiąże równoległego regionu w *sub2*. Wywołanie funkcji z *głównego* do *sub1* jest zgodne, ponieważ **barierę** wiąże równoległego regionu w podprocedury *sub2*.  Wywołanie funkcji z *głównego* do *sub3* jest zgodne, ponieważ **barierę** nie jest powiązana z dowolnego regionu równoległe i jest ignorowana. Należy również zauważyć, że **barierę** synchronizuje tylko zespół wątków w otaczającej równoległego regionu i nie wszystkie wątki, które są tworzone w *sub1*.

```
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```