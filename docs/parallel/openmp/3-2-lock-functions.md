---
title: 3.2 zablokować funkcje | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd788b0ef1c72b1f38a44ee608ce0c7760e24adc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33696256"
---
# <a name="32-lock-functions"></a>3.2 Funkcje blokady
Funkcje opisane w tej sekcji manipulować blokad używane do synchronizacji.  
  
 Dla następujących funkcji zmiennej blokady musi mieć typ **omp_lock_t**. Ta zmienna musi uzyskać tylko za pośrednictwem tych funkcji. Wszystkie funkcje blokady wymagają argument, który zawiera wskaźnik do **omp_lock_t** typu.  
  
-   `omp_init_lock` Funkcja inicjuje proste blokady.  
  
-   `omp_destroy_lock` Funkcja Usuwa blokadę proste.  
  
-   `omp_set_lock` Funkcja oczekuje na prosty blokady jest dostępna.  
  
-   `omp_unset_lock` Funkcja zwalnia blokadę proste.  
  
-   `omp_test_lock` Funkcja testów proste blokady.  
  
 Dla następujących funkcji zmiennej blokady musi mieć typ **omp_nest_lock_t**.  Ta zmienna musi uzyskać tylko za pośrednictwem tych funkcji. Wszystkie funkcje blokadą wymagają argument, który zawiera wskaźnik do **omp_nest_lock_t** typu.  
  
-   `omp_init_nest_lock` Funkcja inicjuje blokadą.  
  
-   `omp_destroy_nest_lock` Funkcja usuwa blokadą.  
  
-   `omp_set_nest_lock` Funkcja oczekiwania do czasu udostępnienia blokadą.  
  
-   `omp_unset_nest_lock` Funkcja zwalnia blokadą.  
  
-   `omp_test_nest_lock` Funkcja testów blokadą.  
  
 OpenMP — funkcje Zablokuj dostęp do zmiennej blokady w taki sposób, że zawsze odczytać i zaktualizować aktualna wartość zmiennej blokady. W związku z tym nie jest konieczne dla programu OpenMP uwzględnić jawne **opróżnić** dyrektywy w celu zapewnienia spójności między inne wątki wartość zmiennej blokady. (Może to być potrzebne **opróżnić** dyrektywy aby wartości innych zmiennych spójne.)