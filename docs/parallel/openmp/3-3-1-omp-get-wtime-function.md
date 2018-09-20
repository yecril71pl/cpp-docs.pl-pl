---
title: 3.3.1 funkcja omp_get_wtime | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ec022e9c7e27c848ef535481993dd18dc45f695
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430777"
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