---
title: 'Porady: korzystanie z wyników połączonych w celu łączenia zestawów'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: 7ccbb3e8bad5c4d3b6f4177afbfdba3e200681a5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142130"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Porady: korzystanie z wyników połączonych w celu łączenia zestawów

W tym temacie pokazano, jak użyć klasy [concurrency:: prekombinowanej](../../parallel/concrt/reference/combinable-class.md) do obliczenia zestawu numerów pierwszych.

## <a name="example"></a>Przykład

Poniższy przykład oblicza zestaw liczb pierwszych dwa razy. Każde obliczenie zapisuje wynik w obiekcie [std:: bitset](../../standard-library/bitset-class.md) . Przykład najpierw oblicza zestaw sekwencyjnie, a następnie oblicza równoległie zestaw. W przykładzie pokazano również drukowanie do konsoli programu czas wymagany do wykonania obu obliczeń.

W tym przykładzie jest używany algorytm [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) i obiekt `combinable` do generowania zestawów lokalnych wątków. Następnie używa metody [concurrency:: kombinowane:: combine_each](reference/combinable-class.md#combine_each) do łączenia zestawów lokalnych wątków z zestawem końcowym.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

Następujące przykładowe dane wyjściowe dotyczą komputera, który ma cztery procesory.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-combine-primes.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Parallel-Combine-primes. cpp**

## <a name="see-also"></a>Zobacz też

[Równoległe kontenery oraz obiekty](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, klasa](../../parallel/concrt/reference/combinable-class.md)<br/>
[Metoda kombinowana:: combine_each](reference/combinable-class.md#combine_each)
