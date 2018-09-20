---
title: 3.2.3 omp_set_lock i omp_set_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 792b95baef2821bb693d9a90fc228d2b0c508e1f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420364"
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