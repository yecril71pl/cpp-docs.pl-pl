---
title: "2.3 konstrukcja równoległa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 190eacdf-2c16-4c06-8cb7-ac60eb211425
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 89167547085682a81cc1d281f4f32ab55022d27c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="23-parallel-construct"></a>2.3 Konstrukcja równoległa
Następujące dyrektywa definiuje równoległego regionu to region program, który ma być wykonane przez wiele wątków jednocześnie. Jest to konstrukcja podstawowych, która rozpoczyna się wykonywanie równoległe.  
  
```  
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block  
```  
  
 *Klauzuli* jest jednym z następujących czynności:  
  
 **Jeśli (** *scalar expression* **)**  
  
 **prywatne (** *zmiennej listy* **)**  
  
 **firstprivate (** *zmiennej listy* **)**  
  
 **domyślne (udostępnionego &#124; none)**  
  
 **udostępnione (** *zmiennej listy* **)**  
  
 **copyin (** *zmiennej listy* **)**  
  
 **redukcja (** *operator* **:***zmiennej listy* **)**   
  
 **num_threads (** *wyrażenie całkowite* **)**  
  
 Podczas wątek napotka konstrukcję równoległe, zespół wątków jest tworzony, jeśli spełniony jest jeden z następujących przypadków:  
  
-   Nie **Jeśli** klauzuli jest obecny.  
  
-   **Jeśli** wyrażenie ma wartość różną od zera.  
  
 Ten wątek staje się głównym wątku zespołu, o liczbie wątków 0, i wszystkie wątki w zespole, łącznie z wątku głównego, wykonaj region równolegle. Jeśli wartość **Jeśli** wyrażenie wynosi zero, region jest serializowany.  
  
 Aby określić liczbę wątków, które są wymagane, uznaje się następujące reguły w kolejności. Pierwsza reguła, której warunek jest spełniony będą stosowane:  
  
1.  Jeśli **num_threads** klauzula jest obecne, a następnie wartość wyrażenia całkowitoliczbowego jest to liczba wątków żądanie.  
  
2.  Jeśli **omp_set_num_threads** została wywołana funkcja biblioteki, a następnie wartość argumentu w wywołaniu ostatnio wykonanej jest to liczba wątków żądanie.  
  
3.  Jeśli zmienna środowiskowa **OMP_NUM_THREADS** jest zdefiniowana, wartość tej zmiennej środowiskowej to liczba wątków żądanie.  
  
4.  Jeśli żadna z metod powyżej użyto to liczba wątków, wymagane jest zdefiniowane w implementacji.  
  
 Jeśli **num_threads** klauzula jest obecne, a następnie zastępuje to liczba wątków zażądał **omp_set_num_threads** funkcja biblioteki lub **OMP_NUM_THREADS** Zmienna środowiskowa tylko w przypadku równoległego regionu jest stosowany do. Kolejnych regionach równoległych nie dotyczy on.  
  
 Liczba wątków, które są wykonywane równoległego regionu zależy również czy dynamiczne Dostosowywanie to liczba wątków jest włączona. Po wyłączeniu dynamiczne Dostosowywanie żądana liczba wątków wykona równoległego regionu. Po włączeniu dynamiczne Dostosowywanie żądana liczba wątków jest maksymalną liczbę wątków, które mogą być wykonywane równoległego regionu.  
  
 Jeśli równoległego regionu podczas dynamicznego dopasowania liczby wątków jest wyłączone, a liczba wątków żądany równoległego regionu przekracza liczbę, która może dostarczyć środowiska wykonawczego systemu, jest zachowanie programu zdefiniowane w implementacji. Implementacja na przykład może przerwać wykonywanie programu, lub może serializować równoległego regionu.  
  
 **Omp_set_dynamic** funkcja biblioteki i **OMP_DYNAMIC** zmiennej środowiskowej, można włączać i wyłączać dynamiczne Dostosowywanie to liczba wątków.  
  
 Liczba procesorów fizycznych faktycznie hosting wątki w danym momencie jest zdefiniowane w implementacji. Po utworzeniu na czas trwania tego równoległego regionu pozostaje stała liczba wątków w zespole. Można zmienić, jawnie przez użytkownika lub automatycznie przez system środowiska wykonawczego z jednego regionu równoległych do innego.  
  
 Instrukcje zawarte w ramach równoległego regionu zakres dynamiczny są wykonywane przez poszczególne wątki, a każdy wątek może zostać wykonany ścieżki instrukcji, która różni się od innych wątków. Dyrektywy napotkano poza zakres leksykalne równoległego regionu są określane jako oddzielone dyrektywy.  
  
 Brak domyślnych bariery na końcu równoległego regionu. Tylko główny wątek zespołu kontynuuje wykonywanie na końcu równoległego regionu.  
  
 Jeśli wątek w zespole wykonywania równoległego regionu napotka innej konstrukcji równoległe, tworzy nowy zespół, a staje się głównym tego nowego zespołu. Zagnieżdżone regiony równoległe są serializowane domyślnie. W związku z tym domyślnie zagnieżdżonych równoległego regionu jest wykonywane przez zespół złożony z jednego wątku. Domyślne zachowanie może można zmieniać za pomocą obu funkcja biblioteki wykonawczej **omp_set_nested** lub zmiennej środowiskowej **OMP_NESTED**. Jednak liczbę wątków w zespole wykonania zagnieżdżonych równoległego regionu jest zdefiniowane w implementacji.  
  
 Ograniczenia **równoległych** dyrektywy są następujące:  
  
-   Co najwyżej jeden **Jeśli** klauzula może występować w dyrektywie.  
  
-   Nieokreślony jest, czy dowolne po stronie efekty w przypadku wyrażenia lub **num_threads** występować wyrażenie.  
  
-   A **throw** wykonywana wewnątrz równoległego regionu może spowodować wykonanie wznowienia w ramach dynamicznej zakres tego samego strukturalnego bloku, a musi być przechwycony przez ten sam wątek, która zgłosiła wyjątek.  
  
-   Tylko jeden **num_threads** klauzula może występować w dyrektywie. **Num_threads** wyrażenie jest obliczane poza kontekstem równoległego regionu i musi być dodatnią liczbą całkowitą.  
  
-   Kolejność obliczania **Jeśli** i **num_threads** klauzule jest nieokreślony.  
  
## <a name="cross-references"></a>Odsyłacze:  
  
-   **prywatne**, **firstprivate**, **domyślne**, **udostępnionego**, **copyin**, i **redukcji**klauzule, zobacz [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.  
  
-   **OMP_NUM_THREADS** zmiennej środowiskowej [4.2 sekcji](../../parallel/openmp/4-2-omp-num-threads.md) na stronie 48.  
  
-   **omp_set_dynamic** funkcja biblioteki, zobacz [sekcji 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) na stronie 39.  
  
-   **OMP_DYNAMIC** środowiska zmiennych, zobacz [4.3 sekcji](../../parallel/openmp/4-3-omp-dynamic.md) na stronie 49.  
  
-   **omp_set_nested** funkcji, zobacz [sekcji 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) na stronie 40.  
  
-   **OMP_NESTED** środowiska zmiennych, zobacz [4.4 sekcji](../../parallel/openmp/4-4-omp-nested.md) na stronie 49.  
  
-   **omp_set_num_threads** funkcja biblioteki, zobacz [sekcji 3.1.1](../../parallel/openmp/3-1-1-omp-set-num-threads-function.md) na stronie 36.