---
title: Funkcje zarządzania pamięcią
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141840"
---
# <a name="memory-management-functions"></a>Funkcje zarządzania pamięcią

W tym dokumencie opisano funkcje zarządzania pamięcią zapewniane przez środowisko uruchomieniowe współbieżności, które ułatwiają przydzielanie i zwalnianie pamięci w sposób współbieżny.

> [!TIP]
> Środowisko uruchomieniowe współbieżności udostępnia domyślny harmonogram i dlatego nie jest konieczne tworzenie go w aplikacji. Ponieważ Harmonogram zadań ułatwia dostosowanie wydajności aplikacji, zalecamy rozpoczęcie od [biblioteki równoległych wzorców (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) , jeśli są one nowe dla środowisko uruchomieniowe współbieżności.

Środowisko uruchomieniowe współbieżności udostępnia dwie funkcje zarządzania pamięcią, które są zoptymalizowane pod kątem przydzielania i zwalniania bloków pamięci w sposób współbieżny. Funkcja [concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc) przypisuje blok pamięci przy użyciu określonego rozmiaru. Funkcja [concurrency:: Free](reference/concurrency-namespace-functions.md#free) zwalnia pamięć, która została przypisana przez `Alloc`.

> [!NOTE]
> `Alloc` i `Free` funkcje są zależne od siebie. Użyj funkcji `Free` tylko w celu zwolnienia pamięci przydzielonej przy użyciu funkcji `Alloc`. Ponadto, korzystając z funkcji `Alloc` w celu przydzielenia pamięci, należy użyć tylko funkcji `Free` do zwolnienia tej pamięci.

Użyj `Alloc` i `Free` funkcji w przypadku przydzielania i zwolnienia ustalonego zestawu rozmiarów alokacji z różnych wątków lub zadań. Środowisko uruchomieniowe współbieżności pamięci podręcznej pamięć podręczna przydzielona ze sterty środowiska uruchomieniowego języka C. Środowisko uruchomieniowe współbieżności przechowuje osobną pamięć podręczną pamięci dla każdego działającego wątku; w związku z tym środowisko uruchomieniowe zarządza pamięcią bez użycia blokad lub barier pamięci. Aplikacja korzysta z dodatkowych funkcji `Alloc` i `Free`, gdy dostęp do pamięci podręcznej jest możliwy częściej. Na przykład wątek, który często wywołuje zarówno `Alloc`, jak i `Free` korzyści więcej niż wątek, który głównie wywołuje `Alloc` lub `Free`.

> [!NOTE]
> W przypadku korzystania z tych funkcji zarządzania pamięcią, gdy aplikacja korzysta z dużej ilości pamięci, aplikacja może bezproblemowo wprowadzić warunek niskiej ilości pamięci niż oczekiwano. Ponieważ bloki pamięci buforowane przez jeden wątek nie są dostępne dla żadnego innego wątku, jeśli jeden wątek zawiera wiele pamięci, ta pamięć jest niedostępna.

## <a name="example"></a>Przykład

Przykład wykorzystujący funkcje `Alloc` i `Free` w celu zwiększenia wydajności pamięci można znaleźć w temacie [How to: use a Free (alokacja i bezpłatna) w celu zwiększenia wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Zobacz też

[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
