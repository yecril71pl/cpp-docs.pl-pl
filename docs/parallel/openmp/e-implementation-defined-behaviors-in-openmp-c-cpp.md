---
title: E. Zachowania zdefiniowane w implementacji programie OpenMP C/C++
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362760"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Zachowania zdefiniowane w implementacji programie OpenMP C/C++

Ten dodatek zawiera podsumowanie zachowań, które są określane jako "zdefiniowane w implementacji" w tym interfejsie API.  Każde działanie jest odsyłaczy do jego opis w głównym specyfikacji.

## <a name="remarks"></a>Uwagi

Implementacja jest wymagana do definiowania i zarządzania dokumentami jego zachowanie w takich przypadkach, ale ta lista może być niekompletna.

- **Liczba wątków:** Jeśli równoległego regionu podczas dynamicznego dostosowania liczby wątków jest wyłączona, a liczba wątków żądany dla równoległego regionu jest większa niż liczba, która może dostarczyć systemu środowiska wykonawczego, jest zachowanie programu zdefiniowane w implementacji (patrz strona 9).

   W programie Visual C++ dla-nested równoległego regionu, 64 wątki (maksymalnie) będzie dostępna.

- **Liczba procesorów:** Liczba procesorów fizycznych, w rzeczywistości hostingu wątki w danym momencie jest zdefiniowane w implementacji (patrz strona 10).

   W programie Visual C++ ta liczba nie jest stała i jest kontrolowana przez system operacyjny.

- **Tworzenie zespołów wątków:** Liczba wątków w zespołach, które są wykonywane zagnieżdżonych równoległego regionu jest zdefiniowane w implementacji (patrz strona 10).

   W programie Visual C++ ta jest określana przez system operacyjny.

- **Schedule(Runtime):** Decyzja o planowaniu jest odroczone do czasu wykonywania. Można wybrać rozmiar typu i fragmentów harmonogramu w czasie wykonywania, ustawiając `OMP_SCHEDULE` zmiennej środowiskowej. Jeśli ta zmienna środowiskowa nie jest ustawiona, wynikowy harmonogram jest zdefiniowane w implementacji (patrz strona 13).

   W programie Visual C++ jest typ harmonogramu `static` o rozmiarze nie fragmentów.

- **Domyślnie, planowania:** W przypadku braku klauzuli harmonogramu domyślnego harmonogramu jest zdefiniowane w implementacji (patrz strona 13).

   W programie Visual C++ jest domyślny typ harmonogramu `static` o rozmiarze nie fragmentów.

- **NIEPODZIELNE:** Jest zdefiniowane w implementacji tego, czy implementacja zastępuje wszystkie `atomic` dyrektyw z `critical` dyrektyw, które mają taką samą unikatową nazwę (patrz strona 20).

   W programie Visual C++, jeśli dane są modyfikowane przez [atomic](reference/openmp-directives.md#atomic) nie znajduje się w naturalnego wyrównania składowej lub jeśli jeden lub dwa bajty jest długi, wszystkie niepodzielne operacje, które spełniają kryteria tej właściwości będzie używać jedna sekcja krytycznego. W przeciwnym razie nie będzie można użyć sekcji krytycznych.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Jeśli liczba wątków nie została jawnie ustawiona przez użytkownika, wartość domyślna jest zdefiniowane w implementacji (patrz strona 9).

   W programie Visual C++ domyślna liczba wątków jest równa liczbie procesorów.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** Wartość domyślna dla wątku dynamicznego dostosowania jest zdefiniowane w implementacji.

   W programie Visual C++, wartość domyślna to `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Po włączeniu zagnieżdżonych równoległości liczba wątków używanych do wykonywania zagnieżdżonych regionów równoległych jest zdefiniowane w implementacji.

   W programie Visual C++ liczba wątków jest określana przez system operacyjny.

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) zmienną środowiskową: Wartością domyślną dla tej zmiennej środowiskowej jest zdefiniowane w implementacji.

   W programie Visual C++ jest typ harmonogramu `static` o rozmiarze nie fragmentów.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) zmienną środowiskową: Jeśli nie określono wartości dla `OMP_NUM_THREADS` zmiennej środowiskowej, czy określona wartość nie jest dodatnią liczbą całkowitą lub jeśli wartość jest większa niż maksymalna liczba wątków, system może obsłużyć, liczbę wątków używanych jest zdefiniowane w implementacji.

   W programie Visual C++ Jeśli określona wartość jest równa zero lub mniej, jest równa liczbie procesorów liczba wątków.  Jeśli wartość jest większa niż 64, liczba wątków to 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) zmienną środowiskową: Wartością domyślną jest zdefiniowane w implementacji.

   W programie Visual C++, wartość domyślna to `FALSE`.