---
title: E. Zdefiniowane w implementacji zachowania programie OpenMP C/C++ | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 6e2e8360dbb2c8851a0ac1c09767928703708a97
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46405011"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Zachowania zdefiniowane w implementacji programie OpenMP C/C++

Ten dodatek zawiera podsumowanie zachowań, które są określane jako "zdefiniowane w implementacji" w tym interfejsie API.  Każde działanie jest odsyłaczy do jego opis w głównym specyfikacji.

## <a name="remarks"></a>Uwagi

Implementacja jest wymagana do definiowania i zarządzania dokumentami jego zachowanie w takich przypadkach, ale ta lista może być niekompletna.

- **Liczba wątków:** Jeśli okaże się podczas dynamicznego dostosowania liczby wątków jest wyłączona, a liczba wątków żądany dla równoległego regionu przekracza liczbę, która może dostarczyć systemu w czasie wykonywania, zachowanie równoległego regionu program jest zdefiniowane w implementacji (patrz strona 9).

     W programie Visual C++ dla-nested równoległego regionu, 64 wątki (maksymalnie) będzie dostępna.

- **Liczba procesorów:** liczby procesorów fizycznych, w rzeczywistości hostingu wątki w danym momencie jest zdefiniowane w implementacji (patrz strona 10).

     W programie Visual C++ ta liczba nie jest stały i jest kontrolowana przez system operacyjny.

- **Tworzenie zespołów wątków:** liczbę wątków w zespołach, które są wykonywane zagnieżdżonych równoległego regionu jest zdefiniowane w implementacji. () zobacz stronę 10).

     W programie Visual C++ jest to określane przez system operacyjny.

- **Schedule(Runtime):** decyzji dotyczących planowania jest odroczone do czasu wykonywania. Można wybrać rozmiar typu i fragmentów harmonogramu w czasie wykonywania, ustawiając `OMP_SCHEDULE` zmiennej środowiskowej. Jeśli nie ustawiono tej zmiennej środowiskowej, wynikowy harmonogram jest zdefiniowane w implementacji (patrz strona 13).

     W programie Visual C++ jest typ harmonogramu `static` o rozmiarze nie fragmentów.

- **Planowanie domyślne:** w przypadku braku klauzuli harmonogramu domyślnego harmonogramu jest zdefiniowane w implementacji (patrz strona 13).

     W programie Visual C++ jest domyślny typ harmonogramu `static` o rozmiarze nie fragmentów.

- **Atomowej:** jest zdefiniowane w implementacji tego, czy implementacja zastępuje wszystkie `atomic` dyrektyw z **krytyczne** dyrektyw, które mają taką samą unikatową nazwę (patrz strona 20).

     W programie Visual C++, jeśli dane są modyfikowane przez [atomic](../../parallel/openmp/reference/atomic.md) nie znajduje się na naturalnego wyrównania składowej lub jeśli 1 lub 2 bajtów długo wszystkich niepodzielne operacje, które spełniają tę właściwość używa jedna sekcja krytycznego. W przeciwnym razie nie będą używane sekcje krytyczne.

- **omp_get_num_threads:** Jeśli liczba wątków nie została jawnie ustawiona przez użytkownika, wartość domyślna to zdefiniowane w implementacji (zobacz stronę 9, a [sekcji 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) na stronie 37).

     W programie Visual C++ domyślna liczba wątków jest równa liczbie procesorów.

- **omp_set_dynamic:** domyślne dla wątku dynamicznego dostosowania jest zdefiniowane w implementacji (zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39).

     W programie Visual C++, wartość domyślna to `FALSE`.

- **omp_set_nested:** po włączeniu zagnieżdżonych równoległości liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest zdefiniowane w implementacji (zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40).

     W programie Visual C++ liczba wątków jest określana przez system operacyjny.

- `OMP_SCHEDULE` Zmienna środowiskowa: wartość domyślna tej zmiennej środowiskowej jest zdefiniowane w implementacji (zobacz [sekcji 4.1](../../parallel/openmp/4-1-omp-schedule.md) na stronie 48).

     W programie Visual C++ jest typ harmonogramu `static` o rozmiarze nie fragmentów.

- `OMP_NUM_THREADS` Zmienna środowiskowa: Jeśli nie określono wartości dla `OMP_NUM_THREADS` zmiennej środowiskowej, lub jeśli określona wartość nie jest dodatnią liczbą całkowitą lub jeśli wartość jest większa niż maksymalna liczba wątków, system może obsłużyć, liczbę wątków używanych zdefiniowane w implementacji (zobacz [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48).

     W programie Visual C++ Jeśli określona wartość jest równa zero lub mniej, jest równa liczbie procesorów liczba wątków.  Jeśli wartość jest większa niż 64, liczba wątków to 64.

- `OMP_DYNAMIC` Zmienna środowiskowa: wartość domyślna to zdefiniowane w implementacji (zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49).

     W programie Visual C++, wartość domyślna to `FALSE`.