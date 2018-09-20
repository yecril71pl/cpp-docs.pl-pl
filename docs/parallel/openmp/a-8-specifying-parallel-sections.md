---
title: A.8 określanie sekcji równoległych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf399304-121e-4c07-9829-47e0dbc2ef10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9d969f1a0e9d9b282104ee00a3b2d06610533ad4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46440423"
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