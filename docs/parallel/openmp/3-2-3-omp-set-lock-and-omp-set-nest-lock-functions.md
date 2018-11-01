---
title: 3.2.3 Funkcje omp_set_lock i omp_set_nest_lock
ms.date: 11/04/2016
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
ms.openlocfilehash: 8efc1f844be2d1b8cf9b15242758914edd0fca14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50617662"
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 Funkcje omp_set_lock i omp_set_nest_lock

Każda z tych funkcji blokuje wątek wykonywania funkcji, dopóki określona blokada jest dostępny, a następnie ustawia blokady. Prostą blokadą jest dostępna, jeśli jest odblokowane. Zagnieżdżalnych blokady jest dostępna, jeśli odblokować lub jest on już własnością wątek wykonywania funkcji. Format jest następujący:

```
#include <omp.h>
void omp_set_lock(omp_lock_t *lock);
void omp_set_nest_lock(omp_nest_lock_t *lock);
```

Dla prostą blokadą argument `omp_set_lock` funkcja musi się odnosić do zmiennej zainicjowane blokady. Własność blokadę zostanie ustanowione wątek wykonywania funkcji.

Dla blokadą argument `omp_set_nest_lock` funkcja musi się odnosić do zmiennej zainicjowane blokady. Zagnieżdżanie licznik jest zwiększany i wątku otrzymuje lub zachowuje własność blokadę.