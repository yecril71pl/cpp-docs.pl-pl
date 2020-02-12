---
title: 'Porady: pisanie pętli parallel_for_each'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: 10c281b7db92e2706b20a1c7377fcdb9d924152d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141873"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>Porady: pisanie pętli parallel_for_each

Ten przykład pokazuje, jak używać algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) do obliczania liczby pierwszych liczb w obiekcie [std:: Array](../../standard-library/array-class-stl.md) równolegle.

## <a name="example"></a>Przykład

Poniższy przykład oblicza liczbę pierwszych liczb w tablicy dwa razy. W przykładzie najpierw jest używany algorytm [std:: for_each](../../standard-library/algorithm-functions.md#for_each) w celu obliczenia liczby seryjnie. Przykład używa algorytmu `parallel_for_each`, aby wykonać to samo zadanie równolegle. W przykładzie pokazano również drukowanie do konsoli programu czas wymagany do wykonania obu obliczeń.

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

Następujące przykładowe dane wyjściowe dotyczą komputera, który ma cztery procesory.

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-count-primes.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Parallel-Count-primes. cpp**

## <a name="robust-programming"></a>Skuteczne programowanie

Wyrażenie lambda, które przykład przekazuje do algorytmu `parallel_for_each` używa funkcji `InterlockedIncrement` do włączenia równoległych iteracji pętli w celu jednoczesnego zwiększenia licznika. Jeśli używasz funkcji, takich jak `InterlockedIncrement`, aby synchronizować dostęp do udostępnionych zasobów, możesz przedstawić wąskie gardła wydajności w kodzie. Można użyć mechanizmu synchronizacji bez blokady, na przykład klasy [concurrency::Binding](../../parallel/concrt/reference/combinable-class.md) , aby wyeliminować jednoczesny dostęp do udostępnionych zasobów. Aby zapoznać się z przykładem, który używa klasy `combinable` w ten sposób, zobacz [How to: use by Performance by zwiększyć wydajność](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Zobacz też

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Funkcja parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)
