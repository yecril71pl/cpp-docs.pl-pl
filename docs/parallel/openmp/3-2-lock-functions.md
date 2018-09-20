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
ms.openlocfilehash: 97f125129d4b35586111f3d4092d457560aaebec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412278"
---
# <a name="32-lock-functions"></a>3.2 Funkcje blokady

Funkcje opisane w tej sekcji manipulować blokad używane na potrzeby synchronizacji.

Dla następujących funkcji, zmienna blokady musi mieć typ **omp_lock_t**. Ta zmienna musi zostać oceniony jedynie za pomocą tych funkcji. Wszystkie funkcje blokady wymaga argumentu, który zawiera wskaźnik do **omp_lock_t** typu.

- `omp_init_lock` Funkcja inicjuje prostą blokadą.

- `omp_destroy_lock` Funkcja usuwa prostą blokadą.

- `omp_set_lock` Funkcja oczekuje na prostą blokadą dostępne.

- `omp_unset_lock` Funkcja zwolni prostą blokadą.

- `omp_test_lock` Funkcja sprawdza prostą blokadą.

Dla następujących funkcji, zmienna blokady musi mieć typ **omp_nest_lock_t**.  Ta zmienna musi zostać oceniony jedynie za pomocą tych funkcji. Wszystkie funkcje blokadą wymagają argument, który zawiera wskaźnik do **omp_nest_lock_t** typu.

- `omp_init_nest_lock` Funkcja inicjuje blokadą.

- `omp_destroy_nest_lock` Funkcja usuwa blokadą.

- `omp_set_nest_lock` Funkcja oczekuje na blokadę zagnieżdżalnych dostępne.

- `omp_unset_nest_lock` Funkcja zwalnia blokadę zagnieżdżalnych.

- `omp_test_nest_lock` Funkcja sprawdza blokadą.

OpenMP — funkcje Zablokuj dostęp do zmiennej blokady w taki sposób, że mogą zawsze odczytywać i aktualizować aktualna wartość zmiennej blokady. W związku z tym, nie jest konieczne dla programu OpenMP uwzględnić jawne **opróżniania** dyrektywy, aby upewnić się, że wartość zmiennej blokady jest spójna wśród różnych wątkach. (Może to być potrzebne **opróżniania** dyrektywy, aby wartości innych zmiennych były spójne.)