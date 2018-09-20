---
title: A.23 przykłady dyrektyw uporządkowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ec609a77e9bdc7cbdbb0822dfde0a88110ce0244
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405973"
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23   Przykłady dyrektyw uporządkowanych

Istnieje możliwość mają wiele uporządkowanych sekcje z `for` określenia `ordered` klauzuli. Pierwszy przykład jest niezgodne, ponieważ interfejs API określa następujące czynności:

"Iteracji pętli za pomocą `for` konstrukcja nie należy wykonać takie same `ordered` dyrektywy więcej niż jeden raz, a nie musisz wykonać więcej niż jedną `ordered` dyrektywy." (Zobacz [sekcji 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) na stronie 22)

W tym przykładzie niezgodnych wszystkich iteracji, wykonaj 2 uporządkowane sekcje:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

W poniższym przykładzie zgodne przedstawiono `for` z więcej niż jednym uporządkowane sekcji:

```
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```