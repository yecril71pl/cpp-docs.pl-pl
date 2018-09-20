---
title: A.4 użycie klauzuli nowait | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: da4b69ed8ccf59fb90d17da2b85d7693d661785b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444505"
---
# <a name="a4---using-the-nowait-clause"></a>A.4   Użycie klauzuli nowait

Jeśli istnieje wiele niezależnych pętli w ramach równoległego regionu, możesz użyć `nowait` — klauzula ([sekcji 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stronie 11) w celu uniknięcia dorozumianych barierę na końcu `for` dyrektywy w następujący sposób:

```
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```