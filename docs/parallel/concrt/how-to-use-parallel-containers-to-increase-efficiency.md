---
title: 'Porady: korzystanie z kontenerów równoległych do zwiększania wydajności'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: cd120d1fbe0f73ed0974efda5a1aa643a1afde9d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143012"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Porady: korzystanie z kontenerów równoległych do zwiększania wydajności

W tym temacie pokazano, jak używać kontenerów równoległych do wydajnego przechowywania i uzyskiwania dostępu do danych.

Przykładowy kod oblicza zestaw wbudowanych i Carmichael numerów równoległych. Następnie dla każdego numeru Carmichael kod oblicza podstawowe czynniki tej liczby.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano funkcję `is_prime`, która określa, czy wartość wejściowa jest liczbą główną, i funkcję `is_carmichael`, która określa, czy wartość wejściowa jest liczbą Carmichael.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład używa funkcji `is_prime` i `is_carmichael`, aby obliczyć zestawy Carmichael i numery. W przykładzie zastosowano algorytmy [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) i [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) do obliczenia każdego zestawu równolegle. Aby uzyskać więcej informacji na temat algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

W tym przykładzie użyto obiektu [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) do przechowywania zestawu Carmichael Numbers, ponieważ będzie on później używał tego obiektu jako kolejki roboczej. Używa obiektu [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) do przechowywania zestawu numerów pierwszych, ponieważ będzie on później powtarzał się w tym zestawie, aby znaleźć podstawowe czynniki.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje funkcję `prime_factors_of`, która używa dzielenia wersji próbnej, aby znaleźć wszystkie podstawowe czynniki danej wartości.

Ta funkcja używa algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) do iteracji zbioru numerów pierwszych. Obiekt `concurrent_vector` umożliwia pętlę równoległą, aby jednocześnie dodać podstawowe czynniki do wyniku.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>Przykład

Ten przykład przetwarza każdy element w kolejce numerów Carmichael przez wywołanie funkcji `prime_factors_of`, aby obliczyć jej podstawowe czynniki. Używa grupy zadań do równoległego wykonywania tej pracy. Aby uzyskać więcej informacji na temat grup zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Ten przykład drukuje podstawowe czynniki dla każdego numeru Carmichael, jeśli ten numer ma więcej niż cztery podstawowe czynniki.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>Przykład

Poniższy kod przedstawia kompletny przykład, który używa kontenerów równoległych do obliczania zasadniczych czynników numerów Carmichael.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `carmichael-primes.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Carmichael-primes. cpp**

## <a name="see-also"></a>Zobacz też

[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector, klasa](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue, klasa](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[Funkcja parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[Funkcja parallel_for](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group, klasa](reference/task-group-class.md)
