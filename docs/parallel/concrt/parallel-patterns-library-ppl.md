---
title: "Równoległe Biblioteka wzorców (PLL) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
caps.latest.revision: "27"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4a13acdf07e2f6055326aea2097cb923baa153a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="parallel-patterns-library-ppl"></a>Biblioteka równoległych wzorców (PLL)
Biblioteka równoległych wzorców (PLL) zapewnia imperatywnych model programowania wspiera skalowalność i łatwość użycia dla tworzenie współbieżnych aplikacji. PPL opiera się na planowanie i składniki zarządzania współbieżności środowiska wykonawczego. Uruchamia poziom abstrakcji między kod aplikacji i wątków podstawowy mechanizm przez podanie ogólnych, bezpieczne algorytmy i kontenerów, które działają na danych równolegle. PPL umożliwia również tworzenie aplikacji, które zapewniając alternatyw do stanu udostępnionego.  
  
 PPL zapewnia następujące funkcje:  
  
- *Równoległość zadań*: mechanizm, który działa na górze pozostawiło systemu Windows można wykonać kilka elementów roboczych (zadania) równolegle  
  
- *Algorytmy równoległe*: Ogólne algorytmów działa na górze współbieżność środowiska wykonawczego do działania w zbiorach danych równolegle  
  
- *Równoległe kontenery i obiekty*: typy ogólne kontenera, które udostępniają bezpieczne równoczesny dostęp do swoich elementów  
  
## <a name="example"></a>Przykład  
 PPL zapewnia model programowania podobny standardowa biblioteka C++. W poniższym przykładzie pokazano wiele funkcji PPL. Oblicza kilka numerów Fibonacci szeregowe i równolegle. Zarówno obliczenia działają na [std::array](../../standard-library/array-class-stl.md) obiektu. Przykład drukuje do konsoli również czasu wymaganego do wykonania obu obliczenia.  
  
 Serial wersji jest używana standardowa biblioteka C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytm przechodzenia tablicy i przechowuje wyniki w [std::vector](../../standard-library/vector-class.md) obiektu. Wersja równoległa wykonuje to samo zadanie, ale używa PPL [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu i przechowuje wyniki w [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) obiektu. `concurrent_vector` Klasa umożliwia każdej iteracji pętli jednocześnie dodać elementy, bez konieczności synchronizacji dostęp do zapisu do kontenera.  
  
 Ponieważ `parallel_for_each` czynności jednocześnie, wersja równoległa w tym przykładzie należy sortować `concurrent_vector` obiektu działają tak samo jak wersja serial.  
  
 Należy pamiętać, że w przykładzie użyto metody prostego do obliczenia liczb Fibonacci; Jednak ta metoda przedstawiono, jak współbieżności środowiska wykonawczego może poprawić wydajność obliczenia długo.  
  
 [!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]  
  
 Następujące przykładowe dane wyjściowe jest dla komputera, który ma cztery procesory.  
  
```Output  
serial time: 9250 ms  
parallel time: 5726 ms  
 
fib(24): 46368  
fib(26): 121393  
fib(41): 165580141  
fib(42): 267914296  
```  
  
 Każdej iteracji pętli wymaga innej ilość czasu, aby zakończyć. Wydajność `parallel_for_each` jest ograniczone przez zakończeniu ostatniej operacji. W związku z tym nie należy oczekiwać ulepszenia wydajności liniowej między wersjami szeregowe i równoległe, w tym przykładzie.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|Zawiera opis roli zadań i grupy zadań w PPL.|  
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)|Informacje dotyczące używania algorytmy równoległe, takich jak `parallel_for` i `parallel_for_each`.|  
|[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)|Zawiera opis różnych równoległe kontenery oraz obiekty, które są udostępniane przez PPL.|  
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Wyjaśniono, jak można anulować pracy, która jest wykonywana przez algorytm równoległych.|  
|[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)|W tym artykule opisano współbieżność środowiska wykonawczego, co upraszcza Programowanie równoległe i zawiera linki do powiązanych tematów.|

