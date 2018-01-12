---
title: "F. Nowe funkcje i wyjaśnienia w wersji 2.0 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b9a661f183816fec0f7a71c990f1508338100f4d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Nowe funkcje i wyjaśnienia w wersji 2.0
Ten dodatek zawiera podsumowanie klucza zmiany wprowadzone w specyfikacji OpenMP C/C++ podczas przenoszenia z wersji 1.0 w wersji 2.0. Nowe funkcje dodane w specyfikacji są następujące elementy:  
  
-   Przecinki są dozwolone w OpenMP — dyrektywy ([2.1 sekcji](../../parallel/openmp/2-1-directive-format.md) na stronie 7).  
  
-   Dodanie `num_threads` klauzuli. Klauzulę pozwala użytkownikowi na żądanie określoną liczbę wątków dla konstrukcji równoległe ([2.3 sekcji](../../parallel/openmp/2-3-parallel-construct.md) na stronie 8).  
  
-   `threadprivate` Dyrektywy wzbogacono zmienne statyczne zakresem bloku ([sekcji 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) na stronie 23).  
  
-   C99 zmiennej długości tablic są kompletne typy i w związku z tym można określić dowolne miejsce pełną są dozwolone typy, na przykład w wykazie `private`, `firstprivate`, i `lastprivate` klauzule ([sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25).  
  
-   Zmiennej prywatnej w równoległego regionu można oznaczyć jako prywatny ponownie w zagnieżdżonych dyrektywy ([sekcji 2.7.2.1](../../parallel/openmp/2-7-2-1-private.md) na stronie 25).  
  
-   `copyprivate` Klauzuli został dodany. Zapewnia mechanizm na potrzeby zmiennej prywatnej emisji wartość z jednego członka do zespołu do innych elementów członkowskich. Jest to alternatywa dla użycia udostępniona zmienna wartości, gdy dostarczanie udostępniona zmienna jest trudna (na przykład w rekursją wymagające innej zmiennej na każdym poziomie). `copyprivate` Klauzula może występować tylko w **pojedynczego** — dyrektywa ([sekcji 2.7.2.8](../../parallel/openmp/2-7-2-8-copyprivate.md) na stronie 32).  
  
-   Dodanie procedury chronometrażu `omp_get_wtick` i `omp_get_wtime` podobne do procedury MPI. Funkcje te są niezbędne do wykonywania wall zegara chronometrażu ([sekcji 3.3.1](../../parallel/openmp/3-3-1-omp-get-wtime-function.md) na stronie 44 i [sekcji 3.3.2](../../parallel/openmp/3-3-2-omp-get-wtick-function.md) na stronie 45).  
  
-   Dodatek z listy zdefiniowane w implementacji zachowania w OpenMP C/C++ został dodany. Implementacja jest wymagana do definiowania i jego zachowanie w tych przypadkach dokumentu ([E dodatku](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md) na stronie 97).  
  
-   Następujące zmiany służą do wyjaśnienia lub Popraw funkcje w poprzedniej specyfikacji interfejsu API OpenMP dla C/C++:  
  
    -   Wyjaśniono, że zachowanie `omp_set_nested` i `omp_set_dynamic` podczas `omp_in_parallel` zdefiniowano zwraca różną od zera ([sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39 i [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40).  
  
    -   Wyjaśniono zagnieżdżanie dyrektywy stosowania zagnieżdżonych równoległe ([2.9 sekcji](../../parallel/openmp/2-9-directive-nesting.md) na stronie 33).  
  
    -   Funkcje zniszczenie blokady i inicjowania blokady może zostać wywołany w równoległego regionu ([sekcji 3.2.1](../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md) na stronie 42 i [sekcji 3.2.2](../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md) na stronie 42).  
  
    -   Dodano nowe przykłady ([dodatek a.](../../parallel/openmp/a-examples.md) na stronie 51).