---
title: 3.2.3 funkcje omp_set_lock i omp_set_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e709e43a0b32b68bc34c4e76e8680ae371e30670
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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