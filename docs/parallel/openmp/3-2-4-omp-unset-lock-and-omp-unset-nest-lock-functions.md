---
title: 3.2.4 Funkcje omp_unset_lock i omp_unset_nest_lock
ms.date: 11/04/2016
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
ms.openlocfilehash: b0764e3590f8edb3a3e783d9b5493a64be154401
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607873"
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 Funkcje omp_unset_lock i omp_unset_nest_lock

Te funkcje zapewniają oznacza, że przy zwalnianiu własność blokadę. Format jest następujący:

```
#include <omp.h>
void omp_unset_lock(omp_lock_t *lock);
void omp_unset_nest_lock(omp_nest_lock_t *lock);
```

Argument do każdej z tych funkcji musi wskazywać na zmienną zainicjowane blokady własnością wątku wykonywania funkcji. Zachowanie jest niezdefiniowane, jeśli wątek nie jest właścicielem tego blokady.

Dla prostą blokadą `omp_unset_lock` funkcja zwolni wątek wykonywania funkcji z na własność blokadę.

Na blokadę zagnieżdżalnych `omp_unset_nest_lock` funkcji zmniejsza liczbę zagnieżdżenia i wersji wątek wykonywania funkcji z na własność blokadę, jeśli wynikowy licznik osiągnie wartość zero.