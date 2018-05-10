---
title: 3.2.5 funkcje funkcje omp_test_lock i omp_test_nest_lock | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5023f0b089d76e92be886f4917905f57dda7a018
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 Funkcje omp_test_lock i omp_test_nest_lock
Nastąpiła próba ustawienia blokady tych funkcji, ale nie blokują wykonanie wątku. Format jest następujący:  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Argument musi wskazywać zmiennej zainicjowane blokady. Nastąpiła próba ustawienia blokady w taki sam sposób jak te funkcje `omp_set_lock` i `omp_set_nest_lock`, ale nie blokują wykonanie wątku.  
  
 Proste blokady `omp_test_lock` funkcja zwraca wartość niezerową, jeśli pomyślnie ustawiono blokady; w przeciwnym razie zwraca wartość zero.  
  
 Dla blokadą `omp_test_nest_lock` funkcja zwraca nowy licznik zagnieżdżenia, jeśli pomyślnie ustawiono blokady; w przeciwnym razie zwraca wartość zero.