---
title: F. Nowe funkcje i wyjaśnienia w wersji 2.0 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d15cbbf60609208a200bd73536d0ebdc8a714f7e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373506"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nowe funkcje i wyjaśnienia w wersji 2.0

Ten dodatek zawiera podsumowanie kluczowych zmiany wprowadzone do specyfikacji OpenMP C/C++ podczas przenoszenia w wersji 1.0 do wersji 2.0. Nowe funkcje dodane do specyfikacji są następujące elementy:

- Przecinki są dozwolone w OpenMP — dyrektywy ([sekcji 2.1](../../parallel/openmp/2-1-directive-format.md) na stronie 7).

- Dodanie `num_threads` klauzuli. Ta klauzula pozwala użytkownikowi na żądanie po upływie określonej liczby wątków równoległych konstrukcji ([2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8).

- `threadprivate` Dyrektywa został rozszerzony o zaakceptowanie zmiennych statycznych zasięgiem bloku ([sekcji 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) na stronie 23).

- C99 zmiennej długości tablice są typami pełnymi i ten sposób można określić dowolnym typami pełnymi są dozwolone, na przykład na liście `private`, `firstprivate`, i `lastprivate` klauzule ([sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25).

- Prywatna zmienna w regionie równoległe mogą zostać oznaczone jako prywatne ponownie w ramach zagnieżdżonych — dyrektywa ([sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25).

- `copyprivate` Klauzuli został dodany. Zapewnia mechanizm na potrzeby emisji wartości z jednego członka zespołu do innych członków zmienną prywatną. Jest to alternatywa dla użycia w udostępnionej zmiennej wartości, gdy dostarczanie w udostępnionej zmiennej może sprawiać trudności (na przykład w rekursji, wymagających inną zmienną na każdym poziomie). `copyprivate` Klauzuli może się pojawić tylko **pojedynczego** — dyrektywa ([sekcji 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stronie 32).

- Dodawanie procedury chronometrażu `omp_get_wtick` i `omp_get_wtime` podobna do procedury MPI. Te funkcje są niezbędne do wykonywania chronometrażu zegara tablicy ([sekcji 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) na stronie 44 i [sekcji 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) na stronie 45 dni).

- Dodano załącznik z listą zachowania zdefiniowane w implementacji programie OpenMP C/C++. Implementacja jest wymagana do definiowania i zarządzania dokumentami jego zachowanie w takich przypadkach ([dodatku E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) na stronie 97).

- Następujące zmiany służą do wyjaśnienia lub Popraw funkcji w poprzednim specyfikacji OpenMP API dla języka C/C++:

   - Wyjaśniono, że zachowanie `omp_set_nested` i `omp_set_dynamic` podczas `omp_in_parallel` zwraca wartość różną od zera jest niezdefiniowana ([sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39 i [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40).

   - Wyjaśniono zagnieżdżanie dyrektywy stosowania zagnieżdżonych równoległego ([2.9 sekcji](../../parallel/openmp/2-9-directive-nesting.md) na stronie 33).

   - Funkcje zniszczenie inicjowania i blokadę przy użyciu blokady może zostać wywołany w równoległego regionu ([sekcji 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) na stronie 42 i [sekcji 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) na stronie 42).

   - Dodano nowe przykłady ([dodatek a.](../../parallel/openmp/a-examples.md) na stronie 51).