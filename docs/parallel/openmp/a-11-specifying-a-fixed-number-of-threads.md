---
title: A.11   Określanie stałej liczby wątków
ms.date: 11/04/2016
ms.assetid: 1d06b142-4c35-44b8-994b-20f2aed5462b
ms.openlocfilehash: 832afac9abc7edd03d3af6f567657aefd596aae0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492051"
---
# <a name="a11---specifying-a-fixed-number-of-threads"></a>A.11   Określanie stałej liczby wątków

Niektóre programy, zależy od stałej, prespecified liczbę wątków jest wykonywany poprawnie.  Ustawieniem domyślnym dla dynamicznego dostosowania liczby wątków jest zdefiniowane w implementacji, programów, które można wyłączyć możliwość dynamicznego wątków i ustaw liczbę wątków, które jawnie, aby zapewnić Przenoszalność. Poniższy przykład pokazuje, jak to zrobić za pomocą `omp_set_dynamic` ([sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39), a `omp_set_num_threads` ([sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36):

```
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

W tym przykładzie program będzie działać prawidłowo tylko wtedy, gdy jest wykonywana przez 16 wątki. Jeśli wdrożenia nie jest zdolny do obsługi 16 wątków, zachowanie w tym przykładzie jest zdefiniowane w implementacji.

Pamiętaj, że liczba wątków wykonywania równoległego regionu pozostaje stała podczas równoległego regionu, niezależnie od tego, wątki dynamicznej, ustawienie. Mechanizm dynamiczne wątków określa liczbę wątków używanych podczas uruchamiania równoległego regionu i utrzymuje stały czas trwania regionu.