---
title: 3.2.1 funkcje omp_init_lock i omp_init_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e00772d4abb7fc72827a116d18c30940ade499db
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Funkcje omp_init_lock i omp_init_nest_lock
Funkcje te zapewniają jedynym sposobem inicjowania blokady. Każda funkcja inicjuje blokady skojarzonych z parametrem *blokady* do użycia w kolejnych wywołaniach. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Stan początkowy jest odblokowany (oznacza to, że wątek nie jest właścicielem blokady). Dla blokadą liczba początkowa zagnieżdżenia wynosi zero. Jest to niezgodne do wywołań dowolnej z tych procedur ze zmienną blokady, który został już zainicjowany.