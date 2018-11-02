---
title: A.8   Określanie sekcji równoległych
ms.date: 11/04/2016
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
ms.openlocfilehash: 81eaed920e77b23052ac58c2d0e18fee83c00565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461441"
---
# <a name="a8---specifying-parallel-sections"></a>A.8   Określanie sekcji równoległych

W poniższym przykładzie (dla [sekcji 2.4.2](../../parallel/openmp/2-4-2-sections-construct.md) na stronie 14) funkcje *liczbowa*, *yaxis*, i *zaxis* mogą być wykonywane jednocześnie. Pierwszy `section` dyrektywa jest opcjonalne.  Należy pamiętać, że wszystkie `section` dyrektyw, musi ono być widoczne w zakresie leksykalnym `parallel sections` konstruowania.

```
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```