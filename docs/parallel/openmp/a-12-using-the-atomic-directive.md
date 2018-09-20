---
title: A.12 użycie dyrektywy niepodzielnej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04daed582cfe87f6e4803b30919af3e07037de7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378751"
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