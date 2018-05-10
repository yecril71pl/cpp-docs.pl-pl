---
title: 3.2.2 funkcje omp_destroy_lock i omp_destroy_nest_lock funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: d334907d-94f7-4bbf-b20e-41d53484cbff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33c21ec9ca07651480748ac705ea6b9e4dcf8e94
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="322-ompdestroylock-and-ompdestroynestlock-functions"></a>3.2.2 Funkcje omp_destroy_lock i omp_destroy_nest_lock
Te funkcje upewnij się, że wskazywany do zmiennej blokady *blokady* nie został zainicjowany. Format jest następujący:  
  
```  
#include <omp.h>  
void omp_destroy_lock(omp_lock_t *lock);  
void omp_destroy_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Jest niezgodne do wywołań dowolnej z tych procedur z zmiennej blokady, która jest niezainicjowana lub odblokować.