---
title: 'Instrukcje: Korzystanie z wyników połączonych do poprawiania wydajności'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: c8f4c40be84b2204e5b5632fe6d3d5a5d22b8719
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410009"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Instrukcje: Korzystanie z wyników połączonych do poprawiania wydajności

W tym przykładzie pokazano, jak używać [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, aby obliczyć sumę dwóch liczb w [std::array](../../standard-library/array-class-stl.md) obiekt, który jest pierwsze. `combinable` Klasy zwiększa wydajność, eliminując udostępnionego stanu.

> [!TIP]
>  W niektórych przypadkach równoległe mapy ([concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) i zmniejszyć ([współbieżności:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) zapewniają poprawę wydajności za pośrednictwem `combinable`. Aby uzyskać przykład, że używa operacji mapowania i redukcji do działają tak samo jak w tym przykładzie, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Przykład

W poniższym przykładzie użyto [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcji do obliczania sumy elementów w tablicy, które są pierwsze. W tym przykładzie `a` jest `array` obiektu i `is_prime` funkcji określa, czy jego wartości wejściowej jest pierwsze.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób naiwni zrównoleglić w poprzednim przykładzie. W tym przykładzie użyto [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm przetwarzania tablicy równolegle i [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) obiektu do synchronizowania dostępu do `prime_sum` zmiennej . W tym przykładzie nie działa, ponieważ każdy wątek musi czekać na zasobie udostępnionym staną się dostępne.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `combinable` obiektu, aby zwiększyć wydajność w poprzednim przykładzie. W tym przykładzie eliminuje potrzebę stosowania obiektów synchronizacji; zostanie przeprowadzone skalowanie, ponieważ `combinable` obiektu umożliwia każdego wątku wykonać swoje zadania niezależnie.

A `combinable` obiekt jest zwykle używany w dwóch krokach. Najpierw utworzyć serię szczegółowych obliczeń, wykonując pracę równolegle. Następnie połącz lub Zmniejsz obliczeń na wynik końcowy. W tym przykładzie użyto [concurrency::combinable::local](reference/combinable-class.md#local) metodę, aby uzyskać odwołanie do lokalnej sumy. Następnie używa [concurrency::combinable::combine](reference/combinable-class.md#combine) metody i [std::plus](../../standard-library/plus-struct.md) obiektu do łączenia lokalnych obliczeń na wynik końcowy.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example"></a>Przykład

Następujący kompletny przykład oblicza sumę liczb pierwszych zarówno szeregowo i równolegle. Przykład drukuje do konsoli czas, który jest wymagany do wykonania obu obliczeń.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

Następujące przykładowe dane wyjściowe to dla komputera, który ma cztery procesory.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-sum-of-primes.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych — Suma z primes.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

Aby uzyskać przykład, że używa operacji mapowania i redukcji w celu uzyskania tych samych wyników, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="see-also"></a>Zobacz także

[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, klasa](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section, klasa](../../parallel/concrt/reference/critical-section-class.md)
