---
title: A.15   Określanie liczby wykorzystywanych wątków
ms.date: 11/04/2016
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
ms.openlocfilehash: bd5e897eeab35ec73c061d2ae02a4b85772e1255
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50525852"
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15   Określanie liczby wykorzystywanych wątków

Rozważmy następujący przykład niepoprawny (dla [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37):

```
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

`omp_get_num_threads()` Wywołania zwraca 1 serial sekcji kodu, więc *potoki* zawsze będzie równy 1 w powyższym przykładzie. Aby określić liczbę wątków, które zostaną wdrożone do równoległego regionu, wywołanie powinno być w ramach równoległego regionu.

Poniższy przykład pokazuje, jak ponownie zapisać ten program bez uwzględniania zapytanie dotyczące liczby wątków:

```
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```