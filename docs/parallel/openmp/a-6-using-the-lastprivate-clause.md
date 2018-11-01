---
title: A.6   Użycie klauzuli ostatniej prywatnej
ms.date: 11/04/2016
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
ms.openlocfilehash: 7d5ba1413827590b7fb3afa0847b9aa1da3c41e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579809"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6   Użycie klauzuli ostatniej prywatnej

Czasami prawidłowe wykonanie zależy od wartości ostatniej iteracji pętli jest przypisywany do zmiennej. Programów, które musi zawierać takich zmiennych jako argumenty `lastprivate` — klauzula ([2.7.2.3 ostatnia sekcja](../../parallel/openmp/2-7-2-3-lastprivate.md) na stronie 27) tak, aby wartości zmiennych są takie same jak kiedy pętla jest wykonywana sekwencyjnie.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

W poprzednim przykładzie wartość `i` na końcu równoległego regionu będzie równa `n-1`, jak w przypadku sekwencyjnych.