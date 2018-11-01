---
title: 'Porady: wykonywanie mapowania i zmniejszanie operacji wykonywane równolegle'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: b73e46e63fc1b320a84322bf2b0efd7adf244ccb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50651866"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Porady: wykonywanie mapowania i zmniejszanie operacji wykonywane równolegle

W tym przykładzie pokazano, jak używać [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) i [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorytmów i [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)klasy Liczenie wystąpień słowa w plikach.

A *mapy* operacja dotyczy funkcji każdej wartości w sekwencji. A *zmniejszyć* operacji łączy elementy sekwencji w jedną wartość. Możesz użyć standardowej biblioteki C++ [std::transform](../../standard-library/algorithm-functions.md#transform) i [std::accumulate](../../standard-library/numeric-functions.md#accumulate) funkcji wykonywanie mapowania i zmniejszanie operacji. Jednak aby zwiększyć wydajność wiele problemów, można użyć `parallel_transform` algorytmu do wykonania tej operacji mapy równolegle i `parallel_reduce` algorytmu do wykonania tej operacji Zmniejsz równolegle. W niektórych przypadkach można użyć `concurrent_unordered_map` do wykonania w ramach jednej operacji mapowania i redukcji.

## <a name="example"></a>Przykład

Poniższy przykład zlicza wystąpienia słów w plikach. Używa ona [std::vector](../../standard-library/vector-class.md) do reprezentowania zawartości dwóch plików. Operacja mapy oblicza wystąpień poszczególnych wyrazów w przypadku każdego wektora. Operacja Zmniejsz gromadzi liczba znaków w obu wektorów.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-map-reduce.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych map-reduce.cpp**

## <a name="robust-programming"></a>Niezawodne programowanie

W tym przykładzie można użyć `concurrent_unordered_map` klasy, który jest zdefiniowany w concurrent_unordered_map.h—to wykonywanie mapowania i zmniejszenie w ramach jednej operacji.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

Zazwyczaj zrównoleglić tylko zewnętrznego lub wewnętrznego pętli. Jeśli masz stosunkowo niewielką liczbą plików, a każdy plik zawiera wiele słów, zrównoleglić wewnętrzną pętlę. Jeśli posiadasz stosunkowo wiele plików, a każdy plik zawiera kilka słów, zrównoleglić zewnętrzna pętla.

## <a name="see-also"></a>Zobacz też

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform — funkcja](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce — funkcja](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map, klasa](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
