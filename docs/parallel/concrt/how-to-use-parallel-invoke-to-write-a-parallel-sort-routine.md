---
title: 'Instrukcje: Używanie parallel_invoke do napisania procedury sortowania równoległego'
ms.date: 11/04/2016
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
ms.openlocfilehash: 329cf275f283ba7b57276d06e909905c9a900697
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57284180"
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>Instrukcje: Używanie parallel_invoke do napisania procedury sortowania równoległego

W tym dokumencie opisano, jak używać [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) algorytmu, aby zwiększyć wydajność algorytmu sortowania bitonicznego. Rekursywnie algorytmu sortowania bitonicznego sekwencji wejściowych jest podzielony na mniejsze partycje posortowany. Algorytm bitonicznego sortowania można uruchomić równolegle, ponieważ każda operacja partycja jest niezależna od wszystkich innych operacji.

Mimo że seryjnie bitonicznego sortowania jest przykładem *sortowanie sieci* która sortuje wszystkie kombinacje sekwencji wejściowych, w tym przykładzie sortuje sekwencji, których długości są wartością potęgi liczby dwa.

> [!NOTE]
>  W tym przykładzie użyto procedury sortowania równoległego do celów informacyjnych. Możesz również użyć wbudowanych algorytmów sortowania, które zapewnia PPL: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), i [concurrency::parallel_ radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

##  <a name="top"></a> Sekcje

W tym dokumencie opisano następujące zadania:

- [Szeregowo wykonanie seryjnie Bitonicznego sortowania](#serial)

- [Korzystając z parallel_invoke, aby wykonać Bitoniczne sortowanie równolegle](#parallel)

##  <a name="serial"></a> Szeregowo wykonanie seryjnie Bitonicznego sortowania

Poniższy przykład pokazuje serial wersję algorytmu sortowania bitonicznego. `bitonic_sort` Funkcja dzieli sekwencję na dwie partycje, sortuje tych partycji w przeciwnych kierunkach i następnie scala ich wyniki. Ta funkcja wywołuje cyklicznie dwa razy, aby posortować każda partycja.

[!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]

[[Górnej](#top)]

##  <a name="parallel"></a> Korzystając z parallel_invoke, aby wykonać Bitoniczne sortowanie równolegle

W tej sekcji opisano sposób używania `parallel_invoke` algorytmu, aby wykonać algorytm bitonicznego sortowania równolegle.

### <a name="procedures"></a>Procedury

##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Aby wykonać algorytm bitonicznego sortowania równolegle

1. Dodaj `#include` dyrektywy dla ppl.h pliku nagłówka.

[!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]

1. Dodaj `using` dyrektywy dla `concurrency` przestrzeni nazw.

[!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]

1. Utwórz nową funkcję o nazwie `parallel_bitonic_mege`, który używa `parallel_invoke` algorytmu do scalenia sekwencji w sposób równoległy, jeśli istnieje wystarczająca ilość pracy do wykonania. W przeciwnym razie wywołanie `bitonic_merge` kolejno scalić sekwencji.

[!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]

1. Wykonaj proces opisany w poprzednim kroku, ale w przypadku `bitonic_sort` funkcji.

[!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]

1. Utworzyć przeciążoną wersję `parallel_bitonic_sort` funkcja, która sortuje tablicy w kolejności rosnącej.

[!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]

`parallel_invoke` Algorytm zmniejsza obciążenie, wykonując ostatniego sekwencję zadań na kontekst wywołania. Na przykład w `parallel_bitonic_sort` funkcji, pierwsze zadanie jest uruchamiane w oddzielnych kontekstu, a drugie zadanie jest uruchamiane w kontekście wywoływania.

[!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]

Następujący kompletny przykład wykonuje numer seryjny i równoległych wersje algorytmu sortowania bitonicznego. Przykład drukuje do konsoli również czas, który jest wymagany do wykonywania poszczególnych obliczeń.

[!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]

Następujące przykładowe dane wyjściowe to dla komputera, który ma cztery procesory.

```Output
serial time: 4353
parallel time: 1248
```

[[Górnej](#top)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-bitonic-sort.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych bitonicznego sort.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

W tym przykładzie użyto `parallel_invoke` algorytmu zamiast [concurrency::task_group](reference/task-group-class.md) klasy, ponieważ okres istnienia każda grupa zadań nie wykracza poza funkcją. Firma Microsoft zaleca użycie `parallel_invoke` kiedy to możliwe, ponieważ ma ona mniejsze obciążenie niż `task group` obiektów i w związku z tym umożliwia zapisanie lepiej zachowującego się kodu.

Równoległe wersje niektóre algorytmy działać lepiej tylko wtedy, gdy pracy wystarczające do wykonania. Na przykład `parallel_bitonic_merge` funkcja wywołuje serial wersji `bitonic_merge`, jeśli istnieją 500 lub mniejszą liczbę elementów w sekwencji. Możesz także zaplanować ogólnej strategii sortowania na podstawie ilości pracy. Na przykład może być bardziej efektywne Użyj serial wersję algorytm szybkiego sortowania, jeśli tablica zawiera mniej niż 500 elementów, jak pokazano w poniższym przykładzie:

[!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]

Podobnie jak w przypadku dowolnego algorytmu równoległego, zaleca się, profilowanie i dostrajania kodu zgodnie z potrzebami.

## <a name="see-also"></a>Zobacz także

[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[parallel_invoke Function](reference/concurrency-namespace-functions.md#parallel_invoke)
