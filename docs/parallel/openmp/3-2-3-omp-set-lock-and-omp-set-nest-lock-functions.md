---
title: 3.2.3 funkcje omp_set_lock i omp_set_nest_lock funkcje | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: ba24e923051eb887db2a81c1d9765d31a4ef7b24
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 Funkcje omp_set_lock i omp_set_nest_lock
Każda z tych funkcji blokuje wątku wykonywania funkcji, dopóki określona blokada jest dostępne, a następnie ustawia blokady. Proste blokady jest dostępna, gdy jest odblokowana. Blokadą jest dostępna, jeśli odblokować lub jeśli już jest własnością wątku wykonywania funkcji. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Proste blokady, argument `omp_set_lock` funkcja musi wskazywać zmiennej zainicjowane blokady. Własność blokady uzyskuje do wykonywania funkcji wątku.  
  
 Dla blokadą argument `omp_set_nest_lock` funkcja musi wskazywać zmiennej zainicjowane blokady. Zagnieżdżenia licznik jest zwiększany, a wątku otrzymuje lub zachowuje własność blokady.