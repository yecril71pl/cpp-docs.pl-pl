---
title: 'Porady: pisanie pętli parallel_for_each | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c68afa77c46e4d57ef01984b44ecb6f4951494a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427085"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>Porady: pisanie pętli parallel_for_each

W tym przykładzie pokazano, jak używać [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm obliczania liczby liczb pierwszych w [std::array](../../standard-library/array-class-stl.md) obiektu równolegle.

## <a name="example"></a>Przykład

Poniższy przykład oblicza liczbę elementów w tablicy pierwsze dwa razy. W przykładzie najpierw zastosowano [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorytm obliczania liczby szeregowo. Następnie w przykładzie `parallel_for_each` algorytmu do wykonania tego samego zadania równolegle. Przykład drukuje do konsoli również czas, który jest wymagany do wykonania obu obliczeń.

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

Następujące przykładowe dane wyjściowe to dla komputera, który ma cztery procesory.

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-count-primes.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych — liczba primes.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

Wyrażenie lambda, które przykład przekazuje do `parallel_for_each` algorytm używa `InterlockedIncrement` funkcję, aby włączyć równoległe iteracji pętli, aby zwiększyć licznik jednocześnie. Jeśli używasz funkcji takich jak `InterlockedIncrement` do synchronizowania dostępu do udostępnionych zasobów, może powodować wąskich gardeł wydajności w kodzie. Mechanizm wolne od blokady synchronizacji, można użyć na przykład, [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy, aby wyeliminować jednoczesny dostęp do zasobów udostępnionych. Aby uzyskać przykład, który używa `combinable` w ten sposób, zobacz [porady: Korzystanie z wyników połączonych do poprawiania wydajności](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Zobacz też

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each — funkcja](reference/concurrency-namespace-functions.md#parallel_for_each)

