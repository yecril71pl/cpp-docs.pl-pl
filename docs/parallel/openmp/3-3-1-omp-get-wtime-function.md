---
title: 3.3.1 Funkcja omp_get_wtime
ms.date: 11/04/2016
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
ms.openlocfilehash: 544a1bc9a613a2888cb7c5e68e54fdfae1b1c333
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50460570"
---
# <a name="331-ompgetwtime-function"></a>3.3.1 Funkcja omp_get_wtime

`omp_get_wtime` Funkcja zwraca wartość punktu zmiennoprzecinkową podwójnej precyzji równa czas zegarowy upłynęło w ciągu kilku sekund, ponieważ niektóre "godziny w przeszłości".  Rzeczywisty "czas w przeszłości" jest określana, ale ma żadnej gwarancji, nie należy zmieniać podczas wykonywania programu, aplikacji. Format jest następujący:

```
#include <omp.h>
double omp_get_wtime(void);
```

Przewiduje się, że funkcja będzie służyć do pomiaru czas, jak pokazano w poniższym przykładzie:

```
double start;
double end;
start = omp_get_wtime();
... work to be timed ...
end = omp_get_wtime();
printf_s("Work took %f sec. time.\n", end-start);
```

Zwracane są "Patrol wątku", który składający się nie muszą być globalnie spójne we wszystkich wątkach uczestniczących w aplikacji.