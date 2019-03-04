---
title: Biblioteka równoległych wzorców (PLL)
ms.date: 11/04/2016
helpviewer_keywords:
- Parallel Patterns Library (PPL)
ms.assetid: 40fd86b2-69fa-45e5-93d8-98a75636c242
ms.openlocfilehash: 11440d56b9618d4763e1b7e47a21b365bbdc0c15
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57290719"
---
# <a name="parallel-patterns-library-ppl"></a>Biblioteka równoległych wzorców (PLL)

Biblioteka równoległych wzorców (PPL) zapewnia model programowania na najwyższym skalowalność i łatwość użytkowania umożliwiający projektowanie aplikacji współbieżnych. PPL opiera się na planowanie i składniki zarządzania w czasie wykonywania współbieżności. Uruchamia poziom abstrakcji między kodu aplikacji i podstawowego mechanizmu wątkowości, zapewniając algorytmy rodzajowe, bezpieczny i kontenerów, które działają w przypadku danych w sposób równoległy. PPL pozwala również tworzyć aplikacje, które można skalować, zapewniając alternatywy dla udostępnionego stanu.

PPL oferuje następujące funkcje:

- *Równoległość zadań*: mechanizm, który działa na podstawie puli wątków Windows do równolegle uruchomić kilka elementów roboczych (zadania)

- *Algorytmy równoległe*: algorytmy rodzajowe, które działa na szczycie ze współbieżności środowiska wykonawczego, która będzie działać na zbiory danych w sposób równoległy

- *Równoległe kontenery oraz obiekty*: typy ogólnego kontenera, które zapewniają bezpieczne równoczesny dostęp do swoich elementów

## <a name="example"></a>Przykład

PPL zapewnia model programowania podobny standardowej biblioteki języka C++. W poniższym przykładzie pokazano wiele funkcji PPL. Oblicza kilka liczb Fibonacci szeregowo i równolegle. Zarówno obliczeń zajmującym się [std::array](../../standard-library/array-class-stl.md) obiektu. Przykład drukuje do konsoli również czas, który jest wymagany do wykonania obu obliczeń.

Wersja serial używa standardowej biblioteki C++ [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytmem przechodzenia tablicy i zapisuje wyniki w [std::vector](../../standard-library/vector-class.md) obiektu. Wersja równoległa wykonuje to samo zadanie, ale używa PPL [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu i zapisuje wyniki w parametrze [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) obiektu. `concurrent_vector` Klasa umożliwia każdej iteracji pętli jednocześnie dodać elementy nie wymaga, aby zsynchronizować dostęp do zapisu do kontenera.

Ponieważ `parallel_for_each` działa jednocześnie, równoległe wersja tego przykładu należy sortować `concurrent_vector` działają tak samo jak serial wersja obiektu.

Należy pamiętać, że w przykładzie użyto metody naiwni do obliczenia liczby Fibonacci; Jednak ta metoda ilustruje, jak poprawić wydajność długich obliczeń w czasie wykonywania współbieżności.

[!code-cpp[concrt-parallel-fibonacci#1](../../parallel/concrt/codesnippet/cpp/parallel-patterns-library-ppl_1.cpp)]

Następujące przykładowe dane wyjściowe to dla komputera, który ma cztery procesory.

```Output
serial time: 9250 ms
parallel time: 5726 ms

fib(24): 46368
fib(26): 121393
fib(41): 165580141
fib(42): 267914296
```

Każdej iteracji pętli wymaga inną ilość czasu, aby zakończyć. Wydajność `parallel_for_each` jest ograniczone przez operację, która zakończy się ostatnio. W związku z tym nie powinno ulepszenia wydajności liniowy między wersjami szeregowe i równolegle w tym przykładzie.

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)|W tym artykule opisano rolę grupy zadań i zadania w PPL.|
|[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)|Opisuje sposób używania algorytmy równoległe, takie jak `parallel_for` i `parallel_for_each`.|
|[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)|W tym artykule opisano różne równoległe kontenery oraz obiekty, które są dostarczane przez PPL.|
|[Anulowanie w PPL](cancellation-in-the-ppl.md)|Wyjaśnia, jak można anulować pracy, która jest wykonywana przez algorytm równoległy.|
|[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)|W tym artykule opisano środowisko uruchomieniowe współbieżności, upraszczający Programowanie równoległe i zawiera linki do powiązanych tematów.|
