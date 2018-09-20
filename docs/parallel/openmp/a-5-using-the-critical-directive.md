---
title: A.5 użycie dyrektywy critical | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 99f9ab513ae1df5a7e1e62cfefcefe404637c063
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444570"
---
# <a name="a5---using-the-critical-directive"></a>A.5   Użycie dyrektywy krytycznej

Poniższy przykład zawiera kilka `critical` dyrektywy ([sekcji 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stronie 18). W przykładzie pokazano kolejkowania modelu, w którym zadanie jest usuwane z kolejki i pracuje. Aby zabezpieczyć się przed wiele wątków tego samego zadania usuwania z kolejki, operacji usuwania z kolejki musi należeć do `critical` sekcji. Ponieważ dwie kolejki w tym przykładzie są niezależne, są chronione przez `critical` dyrektywy pod różnymi nazwami *liczbowa* i *yaxis*.

```
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```