---
title: F. Nowe funkcje i wyjaśnienia w wersji 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 8cd82000992ab957bf2c41f11deccd65e2e6ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215036"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nowe funkcje i wyjaśnienia w wersji 2.0

Ten dodatek podsumowuje kluczowe zmiany wprowadzone w specyfikacji OpenMP C/C++ w przeniesieniu z wersji 1,0 do wersji 2,0. Następujące elementy są nowymi funkcjami dodanymi do specyfikacji:

- W [dyrektywach](2-directives.md#21-directive-format)OpenMP są dozwolone przecinki.

- Dodanie klauzuli `num_threads`. Ta klauzula umożliwia użytkownikowi zażądanie określonej liczby wątków dla [konstrukcji równoległej](2-directives.md#23-parallel-construct).

- Dyrektywa [threadprivate](2-directives.md#271-threadprivate-directive) została rozszerzona w celu akceptowania statycznych zmiennych zakresu bloku.

- Tablice o zmiennej długości C99 są pełnymi typami i można je określić wszędzie tam, gdzie wszystkie kompletne typy są dozwolone, takich jak na listach `private`, `firstprivate`i `lastprivate` klauzule (patrz [sekcja 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Zmienna prywatna w regionie równoległym może być ponownie oznaczona jako [prywatna](2-directives.md#2721-private) w dyrektywie zagnieżdżonej.

- Dodano klauzulę `copyprivate`. Zapewnia mechanizm do użycia zmiennej prywatnej do emisji wartości z jednego członka zespołu do innych członków. Alternatywnym rozwiązaniem jest użycie zmiennej udostępnionej dla wartości, gdy udostępnienie takiej zmiennej udostępnionej byłaby trudne (na przykład w rekursji wymagającej innej zmiennej na każdym poziomie). Klauzula [copyprivate](2-directives.md#2728-copyprivate) może występować tylko w dyrektywie `single`.

- Dodanie procedur czasu [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) i [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) podobne do procedur MPI. Te funkcje są niezbędne do przeprowadzenia chronometrażu zegara ściany.

- Dodatek z listą [zachowań zdefiniowanych w implementacji](e-implementation-defined-behaviors-in-openmp-c-cpp.md) w systemie OpenMP C/C++ został dodany. Implementacja jest wymagana do zdefiniowania i udokumentowania zachowania w takich przypadkach.

- Poniższe zmiany umożliwiają wyjaśnienie lub poprawienie funkcji w poprzedniej specyfikacji interfejsu API OpenMP dla C/C++:

  - Wyjaśniono, że zachowanie [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) i [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) , gdy `omp_in_parallel` zwróci wartość różną od zera, nie jest zdefiniowane.

  - Wyjaśniono [dyrektywę zagnieżdżanie](2-directives.md#29-directive-nesting) w przypadku użycia zagnieżdżonej równoległej.

  - Funkcje [inicjowania blokady](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) i [niszczenia blokady](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions) można wywołać w równoległym regionie.

  - Dodano nowe przykłady do [dodatku A](a-examples.md).
