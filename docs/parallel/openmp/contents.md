---
title: Zawartość | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b7858099-7d7f-4cd9-9fa0-fba4832f2dd2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0ed7dd48d496042cb48a8c8054226ec8892ffbc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46432766"
---
# <a name="contents"></a>Spis treści

[1. Wprowadzenie](../../parallel/openmp/1-introduction.md)

[1.1 Zakres](../../parallel/openmp/1-1-scope.md)

[1.2 Definicje terminów](../../parallel/openmp/1-2-definition-of-terms.md)

[1.3 Model wykonania](../../parallel/openmp/1-3-execution-model.md)

[1.4 Zgodność](../../parallel/openmp/1-4-compliance.md)

[1.5 Odwołania normatywne](../../parallel/openmp/1-5-normative-references.md)

[1.6 Organizacja](../../parallel/openmp/1-6-organization.md)

[2. Dyrektywy](../../parallel/openmp/2-directives.md)

[2.1 Format dyrektywy](../../parallel/openmp/2-1-directive-format.md)

[2.2 Kompilacja warunkowa](../../parallel/openmp/2-2-conditional-compilation.md)

[2.3 Konstrukcja równoległa](../../parallel/openmp/2-3-parallel-construct.md)

[2.4 Konstrukcje podziału pracy](../../parallel/openmp/2-4-work-sharing-constructs.md)

[2.4.1 Konstrukcja for](../../parallel/openmp/2-4-1-for-construct.md)

[2.4.2 Konstrukcja sections](../../parallel/openmp/2-4-2-sections-construct.md)

[2.4.3 Konstrukcja single](../../parallel/openmp/2-4-3-single-construct.md)

[2.5 Połączone równoległe konstrukcje podziału pracy](../../parallel/openmp/2-5-combined-parallel-work-sharing-constructs.md)

[2.5.1 Konstrukcja parallel for](../../parallel/openmp/2-5-1-parallel-for-construct.md)

[2.5.2 Konstrukcja parallel sections](../../parallel/openmp/2-5-2-parallel-sections-construct.md)

[2.6 Dyrektywy główna i dotycząca synchronizacji](../../parallel/openmp/2-6-master-and-synchronization-directives.md)

[2.6.1, konstrukcja master](../../parallel/openmp/2-6-1-master-construct.md)

[2.6.2, konstrukcja critical](../../parallel/openmp/2-6-2-critical-construct.md)

[2.6.3, dyrektywa barrier](../../parallel/openmp/2-6-3-barrier-directive.md)

[2.6.4, konstrukcja atomic](../../parallel/openmp/2-6-4-atomic-construct.md)

[2.6.5, dyrektywa flush](../../parallel/openmp/2-6-5-flush-directive.md)

[2.6.6, konstrukcja ordered](../../parallel/openmp/2-6-6-ordered-construct.md)

[2.7 Środowisko danych](../../parallel/openmp/2-7-data-environment.md)

[2.7.1, dyrektywa threadprivate](../../parallel/openmp/2-7-1-threadprivate-directive.md)

[2.7.2, klauzule atrybutu udostępniania danych](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md)

[2.7.2.1 private](../../parallel/openmp/2-7-2-1-private.md)

[2.7.2.2 firstprivate](../../parallel/openmp/2-7-2-2-firstprivate.md)

[2.7.2.3 lastprivate](../../parallel/openmp/2-7-2-3-lastprivate.md)

[2.7.2.4 shared](../../parallel/openmp/2-7-2-4-shared.md)

[2.7.2.5 default](../../parallel/openmp/2-7-2-5-default.md)

[2.7.2.6 reduction](../../parallel/openmp/2-7-2-6-reduction.md)

[2.7.2.7 copyin](../../parallel/openmp/2-7-2-7-copyin.md)

[2.7.2.8 copyprivate](../../parallel/openmp/2-7-2-8-copyprivate.md)

[2.8 Powiązania dyrektywy](../../parallel/openmp/2-8-directive-binding.md)

[2.9 Zagnieżdżanie dyrektywy](../../parallel/openmp/2-9-directive-nesting.md)

[3. Funkcje bibliotek wykonawczych](../../parallel/openmp/3-run-time-library-functions.md)

[3.1 Funkcje środowiska wykonawczego](../../parallel/openmp/3-1-execution-environment-functions.md)

[3.1.1 Funkcja omp_set_num_threads](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)

[3.1.2 Funkcja omp_get_num_threads](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md)

[3.1.3 Funkcja omp_get_max_threads](../../parallel/openmp/3-1-3-omp-get-max-threads-function.md)

[3.1.4 Funkcja omp_get_thread_num](../../parallel/openmp/3-1-4-omp-get-thread-num-function.md)

[3.1.5 Funkcja omp_get_num_procs](../../parallel/openmp/3-1-5-omp-get-num-procs-function.md)

[3.1.6 Funkcja omp_in_parallel](../../parallel/openmp/3-1-6-omp-in-parallel-function.md)

[3.1.7 Funkcja omp_set_dynamic](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)

[3.1.8 Funkcja omp_get_dynamic](../../parallel/openmp/3-1-8-omp-get-dynamic-function.md)

[3.1.9 Funkcja omp_set_nested](../../parallel/openmp/3-1-9-omp-set-nested-function.md)

[3.1.10 Funkcja omp_get_nested](../../parallel/openmp/3-1-10-omp-get-nested-function.md)

[3.2 Funkcje blokady](../../parallel/openmp/3-2-lock-functions.md)

[3.2.1 Funkcje omp_init_lock i omp_init_nest_lock](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md)

[3.2.2 Funkcje omp_destroy_lock i omp_destroy_nest_lock](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)

[3.2.3 Funkcje omp_set_lock i omp_set_nest_lock](../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)

[3.2.4 Funkcje omp_unset_lock i omp_unset_nest_lock](../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)

[3.2.5 Funkcje omp_test_lock i omp_test_nest_lock](../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md)

[3.3 Procedury chronometrażu](../../parallel/openmp/3-3-timing-routines.md)

[3.3.1 Funkcja omp_get_wtime](../../parallel/openmp/3-3-1-omp-get-wtime-function.md)

[3.3.2 Funkcja omp_get_wtick](../../parallel/openmp/3-3-2-omp-get-wtick-function.md)

[4. Zmienne środowiskowe](../../parallel/openmp/4-environment-variables.md)

[4.1 OMP_SCHEDULE](../../parallel/openmp/4-1-omp-schedule.md)

[4.2 OMP_NUM_THREADS](../../parallel/openmp/4-2-omp-num-threads.md)

[4.3 OMP_DYNAMIC](../../parallel/openmp/4-3-omp-dynamic.md)

[4.4 OMP_NESTED](../../parallel/openmp/4-4-omp-nested.md)

[A. Przykłady](../../parallel/openmp/a-examples.md)

[A.1 wykonywanie równoległe prostej pętli](../../parallel/openmp/a-1-executing-a-simple-loop-in-parallel.md)

[A.2 Określanie kompilacji warunkowej](../../parallel/openmp/a-2-specifying-conditional-compilation.md)

[A.3 użycie regionów równoległych](../../parallel/openmp/a-3-using-parallel-regions.md)

[A.4 użycie klauzuli nowait](../../parallel/openmp/a-4-using-the-nowait-clause.md)

[A.5 użycie dyrektywy critical](../../parallel/openmp/a-5-using-the-critical-directive.md)

[A.6 użycie klauzuli lastprivate](../../parallel/openmp/a-6-using-the-lastprivate-clause.md)

[A.7 użycie klauzuli reduction](../../parallel/openmp/a-7-using-the-reduction-clause.md)

[A.8 określanie sekcji równoległych](../../parallel/openmp/a-8-specifying-parallel-sections.md)

[A.9 użycie pojedynczej dyrektywy](../../parallel/openmp/a-9-using-single-directives.md)

[A.10 określenie porządku sekwencyjnego](../../parallel/openmp/a-10-specifying-sequential-ordering.md)

[A.11 Określanie stałej liczby wątków](../../parallel/openmp/a-11-specifying-a-fixed-number-of-threads.md)

[A.12 użycie dyrektywy niepodzielnej](../../parallel/openmp/a-12-using-the-atomic-directive.md)

[A.13 użycie dyrektywy flush z listą](../../parallel/openmp/a-13-using-the-flush-directive-with-a-list.md)

[A.14 użycie dyrektywy flush bez listy](../../parallel/openmp/a-14-using-the-flush-directive-without-a-list.md)

[A.15 Określanie liczby wykorzystywanych wątków](../../parallel/openmp/a-15-determining-the-number-of-threads-used.md)

[A.16 użycie blokad](../../parallel/openmp/a-16-using-locks.md)

[A.17 użycie Zagnieżdżalnych blokad](../../parallel/openmp/a-17-using-nestable-locks.md)

[A.18 zagnieżdżenia dla dyrektyw](../../parallel/openmp/a-18-nested-for-directives.md)

[A.19 przykłady pokazujące nieprawidłowe zagnieżdżanie dyrektyw podziału pracy](../../parallel/openmp/a-19-examples-showing-incorrect-nesting-of-work-sharing-directives.md)

[A.20 powiązanie dyrektyw bariery](../../parallel/openmp/a-20-binding-of-barrier-directives.md)

[A.21 zmienne zakresowe z klauzulą prywatną](../../parallel/openmp/a-21-scoping-variables-with-the-private-clause.md)

[A.22 przy użyciu default(none) — klauzula](../../parallel/openmp/a-22-using-the-default-none-clause.md)

[A.23 przykłady dyrektyw uporządkowanych](../../parallel/openmp/a-23-examples-of-the-ordered-directive.md)

[A.24 przykład klauzuli prywatnej](../../parallel/openmp/a-24-example-of-the-private-clause.md)

[A.25 przykłady klauzuli atrybutu danych prywatnej kopii](../../parallel/openmp/a-25-examples-of-the-copyprivate-data-attribute-clause.md)

[A.26 użycie dyrektywy threadprivate](../../parallel/openmp/a-26-using-the-threadprivate-directive.md)

[A.27 Użycie tablic C99 o zmiennej długości](../../parallel/openmp/a-27-use-of-c99-variable-length-arrays.md)

[A.28 użycie klauzuli num_threads](../../parallel/openmp/a-28-use-of-num-threads-clause.md)

[A.29 podziału Użyj pracy konstrukcje w konstrukcji krytycznej](../../parallel/openmp/a-29-use-of-work-sharing-constructs-inside-a-critical-construct.md)

[A.30 użycie reprywatyzacji](../../parallel/openmp/a-30-use-of-reprivatization.md)

[A.31 funkcje blokady](../../parallel/openmp/a-31-thread-safe-lock-functions.md)

[B. Wycinki funkcji bibliotek wykonawczych](../../parallel/openmp/b-stubs-for-run-time-library-functions.md)

[C. OpenMP C i gramatyka C++](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)

[C.1 Notacja](../../parallel/openmp/c-1-notation.md)

[C.2 Reguły](../../parallel/openmp/c-2-rules.md)

[D. Użycie klauzuli harmonogramu](../../parallel/openmp/d-using-the-schedule-clause.md)

[E. Zachowania zdefiniowane w implementacji in programie OpenMP C/C++](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)

[F. Nowe funkcje i wyjaśnienia w wersji 2.0](../../parallel/openmp/f-new-features-and-clarifications-in-version-2-0.md)

## <a name="see-also"></a>Zobacz też

[Interfejs aplikacji C++ i C](../../parallel/openmp/openmp-c-and-cpp-application-program-interface.md)