---
title: 3.2.5 funkcje funkcje omp_test_lock i omp_test_nest_lock | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fa340ce56d0e669a40b131a4cb3efbe18fc3c430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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