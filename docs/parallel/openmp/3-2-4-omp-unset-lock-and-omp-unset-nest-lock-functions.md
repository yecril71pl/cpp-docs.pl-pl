---
title: 3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 426ac0a5ff974e486f70eed2965fdc27d5acc941
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419116"
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