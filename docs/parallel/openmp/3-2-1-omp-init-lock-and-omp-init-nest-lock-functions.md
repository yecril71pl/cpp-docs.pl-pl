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
ms.workload: cplusplus
ms.openlocfilehash: 3802822465d6527e4c98a0be6a8c274d767b0f52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 Funkcje omp_init_lock i omp_init_nest_lock
Funkcje te zapewniają jedynym sposobem inicjowania blokady. Każda funkcja inicjuje blokady skojarzonych z parametrem *blokady* do użycia w kolejnych wywołaniach. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Stan początkowy jest odblokowany (oznacza to, że wątek nie jest właścicielem blokady). Dla blokadą liczba początkowa zagnieżdżenia wynosi zero. Jest to niezgodne do wywołań dowolnej z tych procedur ze zmienną blokady, który został już zainicjowany.