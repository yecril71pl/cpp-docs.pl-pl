---
title: 'Instrukcje: Korzystanie z kontenerów równoległych do zwiększania wydajności'
ms.date: 11/04/2016
helpviewer_keywords:
- increasing efficiency with parallel containers [Concurrency Runtime]
- concurrent_queue class, examples
- concurrent_vector class, examples
ms.assetid: bd00046d-e9b6-4ae1-b661-3995f671b867
ms.openlocfilehash: 2479915b167ee3dbc2ce43d9c2733efc74818bbe
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300638"
---
# <a name="how-to-use-parallel-containers-to-increase-efficiency"></a>Instrukcje: Korzystanie z kontenerów równoległych do zwiększania wydajności

W tym temacie pokazano, jak za pomocą kontenerów równoległych wydajne magazynowanie i uzyskać dostęp do danych w sposób równoległy.

Przykładowy kod oblicza zestawu iloczyn i numery Carmichael równolegle. Następnie dla każdego numeru Carmichael kod oblicza główne czynniki tej liczby.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `is_prime` funkcji, która określa, czy wartości wejściowej jest liczba pierwsza, a `is_carmichael` funkcji, która określa, czy wartość wejściowa jest liczbą Carmichael.

[!code-cpp[concrt-carmichael-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_1.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `is_prime` i `is_carmichael` funkcji do obliczenia zestawy prime i Carmichael liczb. W przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) i [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmów w celu obliczenia każdego zestawu równoległego. Aby uzyskać więcej informacji dotyczących algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

W tym przykładzie użyto [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) obiekt do przechowywania zbiór Carmichael liczby, ponieważ później będą używać tego obiektu jako kolejki. Używa ona [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) obiekt zawiera zbiór liczb pierwszych, ponieważ później będą Iterowanie za pomocą tego ustawienia, aby znaleźć główne czynniki.

[!code-cpp[concrt-carmichael-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_2.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `prime_factors_of` funkcji, która korzysta z wersji próbnej dzielenia można znaleźć wszystkie główne czynniki danej wartości.

Ta funkcja używa [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytmu do iterowania po kolekcji liczby pierwsze. `concurrent_vector` Obiekt umożliwia pętli równoległej jednocześnie dodać główne czynniki do wyniku.

[!code-cpp[concrt-carmichael-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_3.cpp)]

## <a name="example"></a>Przykład

W tym przykładzie przetwarza każdy element w kolejce Carmichael liczb, wywołując `prime_factors_of` funkcji do obliczania jego główne czynniki. Używa grupy zadań, aby wykonać tę pracę równolegle. Aby uzyskać więcej informacji o grupach zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Jeśli ta liczba ma więcej niż cztery podstawowe czynniki, w tym przykładzie drukuje główne czynniki dla każdego numeru Carmichael.

[!code-cpp[concrt-carmichael-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_4.cpp)]

## <a name="example"></a>Przykład

Poniższy kod przedstawia kompletny przykład, który używa kontenerów równoległych do obliczenia główne czynniki liczb Carmichael.

[!code-cpp[concrt-carmichael-primes#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-containers-to-increase-efficiency_5.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
Prime factors of 9890881 are: 7 11 13 41 241.
Prime factors of 825265 are: 5 7 17 19 73.
Prime factors of 1050985 are: 5 13 19 23 37.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `carmichael-primes.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc carmichael-primes.cpp**

## <a name="see-also"></a>Zobacz także

[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[concurrent_vector, klasa](../../parallel/concrt/reference/concurrent-vector-class.md)<br/>
[concurrent_queue, klasa](../../parallel/concrt/reference/concurrent-queue-class.md)<br/>
[parallel_invoke Function](reference/concurrency-namespace-functions.md#parallel_invoke)<br/>
[parallel_for Function](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[task_group, klasa](reference/task-group-class.md)
