---
title: E. Zachowania w OpenMP C/C++ zdefiniowane w implementacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 598964ec6a12ac4c357efc04df78bfbe3af798a5
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688703"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Zdefiniowane w implementacji zachowania w OpenMP C/C++
Ten dodatek zawiera podsumowanie zachowania, które są nazywane "zdefiniowane w implementacji" w tym interfejsie API.  Każdy zachowanie jest odsyłaczy do jego opis w specyfikacji głównego.  
  
## <a name="remarks"></a>Uwagi  
 Implementacja jest wymagana do definiowania i jego zachowanie w tych przypadkach dokumentu, ale tej listy mogą być niekompletne.  
  
-   **Liczba wątków:** Jeśli okaże się podczas dynamicznego dopasowania liczby wątków jest wyłączone, a liczba wątków żądany równoległego regionu przekracza liczbę, która może dostarczyć systemu środowiska wykonawczego, zachowanie równoległego regionu program jest zdefiniowane w implementacji (patrz strona 9).  
  
     W programie Visual C++ dla-nested równoległego regionu, 64 wątków (maksymalnie) będzie dostępna.  
  
-   **Liczba procesorów:** liczba procesorów fizycznych faktycznie hosting wątki w danym momencie jest zdefiniowane w implementacji (patrz strona 10).  
  
     W programie Visual C++ ta liczba nie jest stały i jest kontrolowany przez system operacyjny.  
  
-   **Tworzenie zespołów wątków:** liczbę wątków w zespole wykonania zagnieżdżonych równoległego regionu jest zdefiniowane w implementacji. () zobacz stronę 10).  
  
     W programie Visual C++ jest to określane przez system operacyjny.  
  
-   **Schedule(Runtime):** decyzji dotyczących planowania została odroczona do czasu wykonywania. Rozmiar typu i fragmentu harmonogramu można wybrać w czasie wykonywania przez ustawienie `OMP_SCHEDULE` zmiennej środowiskowej. Jeśli nie ustawiono tej zmiennej środowiskowej, wynikowy harmonogram jest zdefiniowane w implementacji (patrz strona 13).  
  
     W programie Visual C++, jest typu harmonogramu `static` nie rozmiar fragmentu.  
  
-   **Planowanie domyślne:** w przypadku braku klauzuli harmonogram domyślny harmonogram jest zdefiniowane w implementacji (patrz strona 13).  
  
     W programie Visual C++, domyślnym typem harmonogramu jest `static` z nie rozmiar fragmentu.  
  
-   **Atomowej:** jest zdefiniowane w implementacji czy implementację zastępuje wszystkie `atomic` dyrektywy z **krytyczne** dyrektywy, które mają taką samą nazwę unikatową (patrz strona 20).  
  
     W programie Visual C++, jeśli dane zmodyfikowane przez [atomic](../../parallel/openmp/reference/atomic.md) nie znajduje się na naturalnego wyrównania lub jeśli 1 lub 2 bajty długo wszystkie operacje atomic, które spełniają właściwości używa jednej sekcji krytycznych. W przeciwnym razie nie będzie używane sekcje krytyczne.  
  
-   **omp_get_num_threads:** Jeśli liczba wątków nie zostanie jawnie ustawiona przez użytkownika, wartość domyślna to zdefiniowane w implementacji (zobacz stronę 9 i [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37).  
  
     W programie Visual C++ domyślna liczba wątków jest równa liczbie procesorów.  
  
-   **omp_set_dynamic:** jest ustawieniem domyślnym dla wątku dynamicznego dopasowania zdefiniowane w implementacji (zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39).  
  
     W programie Visual C++, wartość domyślna to `FALSE`.  
  
-   **omp_set_nested:** po włączeniu zagnieżdżonych równoległości liczbę wątków używanych do wykonania zagnieżdżonych regionów równoległe jest zdefiniowane w implementacji (zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40).  
  
     W programie Visual C++ liczba wątków jest określana przez system operacyjny.  
  
-   `OMP_SCHEDULE` Zmienna środowiskowa: domyślna wartość tej zmiennej środowiskowej jest zdefiniowane w implementacji (zobacz [4.1 sekcji](../../parallel/openmp/4-1-omp-schedule.md) na stronie 48).  
  
     W programie Visual C++, jest typu harmonogramu `static` nie rozmiar fragmentu.  
  
-   `OMP_NUM_THREADS` Zmienna środowiskowa: Jeśli nie określono wartości dla `OMP_NUM_THREADS` zmiennej środowiskowej, lub jeśli określona wartość nie jest dodatnią liczbą całkowitą lub jeśli wartość jest większa niż maksymalna liczba wątków systemu może obsługiwać, liczbę wątków używanych jest zdefiniowane w implementacji (zobacz [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48).  
  
     W programie Visual C++ Jeśli określona wartość jest równa zero lub mniej, liczba wątków jest równa liczbie procesorów.  Jeśli wartość jest większa niż 64, liczba wątków to 64.  
  
-   `OMP_DYNAMIC` Zmienna środowiskowa: wartość domyślna to zdefiniowane w implementacji (zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49).  
  
     W programie Visual C++, wartość domyślna to `FALSE`.