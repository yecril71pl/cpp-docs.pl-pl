---
title: A.12   Użycie dyrektywy niepodzielnej
ms.date: 11/04/2016
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
ms.openlocfilehash: 0f75b182e2cae11f0e72d5ca1e67f887294e8f69
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504448"
---
# <a name="a12---using-the-atomic-directive"></a>A.12   Użycie dyrektywy niepodzielnej

Poniższy przykład pozwala uniknąć wyścigu (równoczesnych aktualizacji elementu *x* przez wiele wątków) przy użyciu `atomic` — dyrektywa ([sekcji 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) na stronie 19):

```
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

Zaletą korzystania z `atomic` dyrektywy w tym przykładzie jest możliwość aktualizacji dwóch różnych elementów x są wykonywane równolegle. Jeśli `critical` — dyrektywa ([sekcji 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) na stronie 18) były używane zamiast tego, a następnie aktualizuje wszystkie elementy *x* będą wykonywane szeregowo (choć nie w żadnym gwarantowana kolejność).

Należy pamiętać, że `atomic` dyrektywy dotyczy tylko instrukcja C lub C++ następujący bezpośrednio po nim.  W rezultacie elementy *y* nie zostaną zaktualizowane niepodzielne w tym przykładzie.