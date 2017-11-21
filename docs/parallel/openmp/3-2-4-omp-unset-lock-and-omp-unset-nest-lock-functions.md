---
title: 3.2.4 funkcje omp_unset_lock i omp_unset_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c7a3aebc404205c85627820188e137713317eb7d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 Funkcje omp_unset_lock i omp_unset_nest_lock
Funkcje te pozwalają zwalniania własność blokady. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Argument każda z tych funkcji musi wskazywać zmiennej zainicjowane blokady należących do wykonywania funkcji wątku. Zachowanie jest niezdefiniowana, jeśli wątek nie jest właścicielem tego blokady.  
  
 Proste blokady `omp_unset_lock` funkcja zwalnia wątku wykonywania funkcji z własność blokady.  
  
 Dla blokadą `omp_unset_nest_lock` działanie zmniejsza liczbę zagnieżdżenia i wersjach wątku wykonywania funkcji z własność blokady, jeśli wynikowa liczba wynosi zero.