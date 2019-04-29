---
title: F. Nowe funkcje i wyjaśnienia w wersji 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362717"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nowe funkcje i wyjaśnienia w wersji 2.0

Ten dodatek zawiera podsumowanie kluczowych zmiany wprowadzone do specyfikacji OpenMP C/C++ podczas przenoszenia w wersji 1.0 do wersji 2.0. Nowe funkcje dodane do specyfikacji są następujące elementy:

- Przecinki są dozwolone w OpenMP [dyrektywy](2-directives.md#21-directive-format).

- Dodanie `num_threads` klauzuli. Ta klauzula pozwala użytkownikowi na określoną liczbę wątków dla żądania [konstrukcja równoległa](2-directives.md#23-parallel-construct).

- [Threadprivate](2-directives.md#271-threadprivate-directive) dyrektywa został rozszerzony o zaakceptowanie zmiennych statycznych zakres bloku.

- C99 zmiennej długości tablice są typami pełnymi i może być określony dowolnym typami pełnymi są dozwolone, takie jak listy `private`, `firstprivate`, i `lastprivate` klauzule (zobacz [sekcji 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Prywatna zmienna w regionie równoległe mogą zostać oznaczone jako [prywatnej](2-directives.md#2721-private) ponownie w dyrektywie zagnieżdżonych.

- `copyprivate` Klauzuli został dodany. Zapewnia mechanizm na potrzeby emisji wartości z jednego członka zespołu do innych członków zmienną prywatną. Jest to alternatywa dla użycia w udostępnionej zmiennej wartości, gdy dostarczanie w udostępnionej zmiennej może sprawiać trudności (na przykład w rekursji, wymagających inną zmienną na każdym poziomie). [Copyprivate](2-directives.md#2728-copyprivate) klauzuli może się pojawić tylko `single` dyrektywy.

- Dodawanie procedury chronometrażu [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) i [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) podobna do procedury MPI. Te funkcje są niezbędne do wall chronometrażu zegara.

- Dodatek z listą [zachowania zdefiniowane w implementacji](e-implementation-defined-behaviors-in-openmp-c-cpp.md) programie OpenMP C/C++ zostały dodane. Implementacja jest wymagana do definiowania i zarządzania dokumentami jego zachowanie w takich przypadkach.

- Następujące zmiany służą do wyjaśnienia lub Popraw funkcji w poprzednim specyfikacji OpenMP API dla języka C/C++:

  - Wyjaśniono, że zachowanie [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) i [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) podczas `omp_in_parallel` zwraca wartość różną od zera jest niezdefiniowana.

  - Wyjaśniono [zagnieżdżanie dyrektywy](2-directives.md#29-directive-nesting) podczas równoległego zagnieżdżone jest używany.

  - [Zablokować inicjowania](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) i [zablokować zniszczenie](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) funkcji może zostać wywołany w równoległego regionu.

  - Dodano nowe przykłady [dodatek a.](a-examples.md).