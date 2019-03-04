---
title: 'Instrukcje: Korzystanie z wyników połączonych w celu łączenia zestawów'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: bf8a5bee65ea0ba1718c1d4d436b6af3e0b95961
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296101"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Instrukcje: Korzystanie z wyników połączonych w celu łączenia zestawów

W tym temacie pokazano, jak używać [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) klasy w celu obliczenia zbiór liczb pierwszych.

## <a name="example"></a>Przykład

Poniższy przykład oblicza zestaw liczby pierwsze dwa razy. Każdy obliczeń zapisuje wynik w [std::bitset](../../standard-library/bitset-class.md) obiektu. Przykład najpierw szeregowo oblicza zestaw, a następnie oblicza zestawu równoległego. Przykład drukuje do konsoli również czas, który jest wymagany do wykonania obu obliczeń.

W tym przykładzie użyto [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytmu i `combinable` obiektu umożliwiającą wygenerowanie wątków lokalnych zestawów. Następnie używa [concurrency::combinable::combine_each](reference/combinable-class.md#combine_each) metodę, aby połączyć zestawy wątków lokalnych w końcowym zestawie.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

Następujące przykładowe dane wyjściowe to dla komputera, który ma cztery procesory.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-combine-primes.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc równoległych — łączenie primes.cpp**

## <a name="see-also"></a>Zobacz także

[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, klasa](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable::combine_each — metoda](reference/combinable-class.md#combine_each)
