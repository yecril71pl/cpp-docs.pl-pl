---
title: Funkcje zarządzania pamięcią
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: d8dfc8bbb200258818c38e931e978cc3be292525
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454085"
---
# <a name="memory-management-functions"></a>Funkcje zarządzania pamięcią

W tym dokumencie opisano funkcje zarządzania pamięcią, udostępnianych przez środowisko uruchomieniowe współbieżności ułatwiające przydzielają i zwalniają pamięć w sposób współbieżnych.

> [!TIP]
>  Środowisko uruchomieniowe współbieżności zawiera domyślnego harmonogramu, a w związku z tym nie należy utworzyć w aplikacji. Ponieważ Harmonogram zadań ułatwia dostrajania wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki wzorców równoległych (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [bibliotekę asynchronicznych agentów](../../parallel/concrt/asynchronous-agents-library.md) przypadku jesteś nowym użytkownikiem w czasie wykonywania współbieżności.

Środowisko uruchomieniowe współbieżności zapewnia dwie funkcje zarządzania pamięcią, które są zoptymalizowane pod kątem przydzielanie i zwalnianie bloki pamięci w sposób współbieżnych. [Concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) funkcja przydziela blok pamięci przy użyciu określonego rozmiaru. [Concurrency::Free](reference/concurrency-namespace-functions.md#free) funkcja zwalnia pamięć, która została przydzielona przez `Alloc`.

> [!NOTE]
>  `Alloc` i `Free` funkcje zależą od siebie nawzajem. Użyj `Free` funkcji tylko, aby zwolnić pamięć, przydzielany przy użyciu `Alloc` funkcji. Ponadto, jeśli używasz `Alloc` funkcję, aby przydzielić pamięci, należy użyć tylko `Free` funkcję, aby zwolnić z pamięci.

Użyj `Alloc` i `Free` działa, gdy możesz przydzielać i zwalniać ustalony zestaw elementów rozmiarów alokacji z różnych wątków lub zadania. Środowisko uruchomieniowe współbieżności buforuje pamięci przydzielanej ze stosu środowiska uruchomieniowego C. Środowisko uruchomieniowe współbieżności przechowuje w oddzielnych pamięci podręcznej dla każdego uruchomionego wątku; w związku z tym środowisko uruchomieniowe zarządza pamięcią bez użycia blokad lub barier pamięci. Aplikacja korzyści płynące z innymi za pomocą `Alloc` i `Free` funkcje pamięci podręcznej pamięci o dostępie częściej. Na przykład wątku, który często wywołuje zarówno `Alloc` i `Free` korzyści z więcej niż wątek, który wywołuje przede wszystkim `Alloc` lub `Free`.

> [!NOTE]
>  Podczas korzystania z tych funkcji zarządzania pamięci i wprowadzić wiele zastosowań aplikacji Twojej pamięci, aplikacji niedostatecznej ilości pamięci szybciej niż można się spodziewać. Ponieważ bloki pamięci, które są buforowane przez jeden wątek nie są dostępne dla innych wątków, jeśli jeden wątek nałoży dużej ilości pamięci, że pamięć nie jest dostępna.

## <a name="example"></a>Przykład

Aby uzyskać przykład, który używa `Alloc` i `Free` funkcje do poprawiania wydajności pamięci, zobacz [porady: Użyj alokacji i bezpłatnie do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

