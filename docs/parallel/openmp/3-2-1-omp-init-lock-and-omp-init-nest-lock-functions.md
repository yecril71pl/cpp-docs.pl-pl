---
title: 3.2.1 funkcje omp_init_lock i omp_init_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f14e182e6c981cd5de7a4cf92d8c285a4b49c66
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Funkcje omp_init_lock i omp_init_nest_lock
Funkcje te zapewniają jedynym sposobem inicjowania blokady. Każda funkcja inicjuje blokady skojarzonych z parametrem *blokady* do użycia w kolejnych wywołaniach. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Stan początkowy jest odblokowany (oznacza to, że wątek nie jest właścicielem blokady). Dla blokadą liczba początkowa zagnieżdżenia wynosi zero. Jest to niezgodne do wywołań dowolnej z tych procedur ze zmienną blokady, który został już zainicjowany.