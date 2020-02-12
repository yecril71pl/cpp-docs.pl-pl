---
title: 'Porady: korzystanie z wyników połączonych do poprawiania wydajności'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- improving parallel performance with combinable [Concurrency Runtime]
ms.assetid: fa730580-1c94-4b2d-8aec-57c91dc0497e
ms.openlocfilehash: db27a791b2b92102118606712db4cbd2920f9619
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142439"
---
# <a name="how-to-use-combinable-to-improve-performance"></a>Porady: korzystanie z wyników połączonych do poprawiania wydajności

Ten przykład pokazuje, jak używać klasy [concurrency:: prekombinowanej](../../parallel/concrt/reference/combinable-class.md) do obliczania sumy liczb w obiekcie [std:: Array](../../standard-library/array-class-stl.md) , który jest podstawowy. Klasa `combinable` zwiększa wydajność dzięki wyeliminowaniu stanu udostępnionego.

> [!TIP]
> W niektórych przypadkach mapowanie równoległe ([współbieżność::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform)) i zmniejszenie ([concurrency:: parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce)) może zapewnić lepszą wydajność w porównaniu z `combinable`. Aby uzyskać przykład, który używa operacji map i zmniejsz, aby uzyskać te same wyniki co ten przykład, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="example---accumulate"></a>Przykład — gromadzenie

W poniższym przykładzie zastosowano funkcję [std:: akumulacj](../../standard-library/numeric-functions.md#accumulate) , aby obliczyć sumę elementów w tablicy, która jest podstawowa. W tym przykładzie `a` jest obiektem `array`, a funkcja `is_prime` określa, czy jej wartość wejściowa jest podstawowa.

[!code-cpp[concrt-parallel-sum-of-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_1.cpp)]

## <a name="example---parallel_for_each"></a>Przykład — parallel_for_each

W poniższym przykładzie pokazano algorytmie sposób zrównoleglanie poprzedniego przykładu. W tym przykładzie zastosowano algorytm [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) , aby przetworzyć tablicę równolegle i [concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md) obiektu, aby zsynchronizować dostęp do zmiennej `prime_sum`. Ten przykład nie jest skalowany, ponieważ każdy wątek musi oczekiwać na udostępnienie zasobu udostępnionego.

[!code-cpp[concrt-parallel-sum-of-primes#2](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_2.cpp)]

## <a name="example---combinable"></a>Przykład — do kombinacji

Poniższy przykład używa obiektu `combinable`, aby zwiększyć wydajność poprzedniego przykładu. Ten przykład eliminuje konieczność stosowania obiektów synchronizacji; skaluje się, ponieważ obiekt `combinable` umożliwia każdemu wątkowi wykonywanie zadania niezależnie.

Obiekt `combinable` jest zazwyczaj używany w dwóch krokach. Najpierw należy utworzyć serię szczegółowych obliczeń przez równoległe wykonywanie pracy. Następnie połącz (lub Zmniejsz) obliczenia w końcowym wyniku. W tym przykładzie zastosowano metodę [concurrency:: kombinowane:: local](reference/combinable-class.md#local) , aby uzyskać odwołanie do sumy lokalnej. Następnie używa metody [concurrency:: kombinowane:: łączenie](reference/combinable-class.md#combine) i obiektu [lu std::p](../../standard-library/plus-struct.md) do łączenia lokalnych obliczeń w wyniku końcowym.

[!code-cpp[concrt-parallel-sum-of-primes#3](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_3.cpp)]

## <a name="example---serial-and-parallel"></a>Przykład — serial i Parallel

Poniższy kompletny przykład oblicza sumę liczb pierwszych jednocześnie i jednocześnie. Przykład drukuje do konsoli czas wymagany do wykonania obu obliczeń.

[!code-cpp[concrt-parallel-sum-of-primes#4](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-improve-performance_4.cpp)]

Następujące przykładowe dane wyjściowe dotyczą komputera, który ma cztery procesory.

```Output
1709600813
serial time: 6178 ms

1709600813
parallel time: 1638 ms
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-sum-of-primes.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Parallel-sum-of-primes. cpp**

## <a name="robust-programming"></a>Skuteczne programowanie

Aby uzyskać przykład, który używa operacji map i zmniejsz, aby utworzyć te same wyniki, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="see-also"></a>Zobacz też

[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, klasa](../../parallel/concrt/reference/combinable-class.md)<br/>
[critical_section, klasa](../../parallel/concrt/reference/critical-section-class.md)
