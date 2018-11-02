---
title: A.1   Wykonywanie równoległe prostej pętli
ms.date: 11/04/2016
ms.assetid: b8aaacae-b20d-4b16-a540-54ccbf09582b
ms.openlocfilehash: 5bd9a9c8b1d226c67f7e9031a547e551fae3407b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558941"
---
# <a name="a1---executing-a-simple-loop-in-parallel"></a>A.1   Wykonywanie równoległe prostej pętli

Poniższy przykład pokazuje, jak zrównoleglić przy użyciu prostej pętli `parallel for` — dyrektywa ([sekcji 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) na stronie 16). Zmienna iteracji pętli jest domyślnie prywatny, więc nie jawnie określ wartość w klauzuli prywatnej.

```
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```