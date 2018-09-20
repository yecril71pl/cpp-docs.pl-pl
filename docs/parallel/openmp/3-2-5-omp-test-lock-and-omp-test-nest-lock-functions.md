---
title: 3.2.5 funkcje omp_test_lock i omp_test_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5349134bf92f407d4b65df9b92e3eebe87c097c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426149"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 Funkcje omp_test_lock i omp_test_nest_lock

Spróbuj ustawić blokadę tych funkcji, ale nie blokują wykonanie wątku. Format jest następujący:

```
#include <omp.h>
int omp_test_lock(omp_lock_t *lock);
int omp_test_nest_lock(omp_nest_lock_t *lock);
```

Argument musi wskazywać na zmienną zainicjowane blokady. Tych funkcji, spróbuj ustawić blokadę w taki sam sposób jak `omp_set_lock` i `omp_set_nest_lock`, z tą różnicą, że nie blokują wykonanie wątku.

Dla prostą blokadą `omp_test_lock` funkcja zwraca wartość różną od zera, jeśli pomyślnie ustawiono blokady; w przeciwnym razie zwraca wartość zero.

Na blokadę zagnieżdżalnych `omp_test_nest_lock` funkcja zwraca nową liczbę zagnieżdżenia, jeśli pomyślnie ustawiono blokady; w przeciwnym razie zwraca wartość zero.