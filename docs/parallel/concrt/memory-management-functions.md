---
title: "Funkcje zarządzania pamięcią | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 309080a807a1325bbf921657a152cff60e87cb95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-functions"></a>Funkcje zarządzania pamięcią
W tym dokumencie opisano funkcje zarządzania pamięcią, udostępniające Aby przydzielić i zwolnić pamięć, w sposób równoczesnych współbieżności środowiska wykonawczego.  
  
> [!TIP]
>  Współbieżność środowiska wykonawczego zapewnia harmonogram domyślny, i dlatego nie trzeba utworzyć w aplikacji. Harmonogram zadań ułatwia dostrojenie wydajności aplikacji, dlatego zaleca się uruchamiania z [równoległych biblioteki wzorców (PLL)](../../parallel/concrt/parallel-patterns-library-ppl.md) lub [biblioteki agentów asynchronicznych](../../parallel/concrt/asynchronous-agents-library.md) w przypadku jesteś nowym użytkownikiem współbieżności środowiska wykonawczego.  
  
 Współbieżność środowiska wykonawczego zawiera dwie funkcje zarządzania pamięcią, które są zoptymalizowane pod kątem podziału i zwalnianie bloków pamięci w sposób współbieżnych. [Concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) funkcja przydziela bloku pamięci przy użyciu określonego rozmiaru. [Concurrency::Free](reference/concurrency-namespace-functions.md#free) funkcja zwalnia pamięć, która została przydzielona przez `Alloc`.  
  
> [!NOTE]
>  `Alloc` i `Free` funkcje zależne od siebie nawzajem. Użyj `Free` funkcja tylko do wersji pamięci, jaką można przydzielić przy użyciu `Alloc` funkcji. Ponadto, kiedy należy używać `Alloc` funkcji można przydzielić pamięci, należy użyć tylko `Free` funkcji, aby zwolnić pamięci.  
  
 Użyj `Alloc` i `Free` działa podczas alokacji i zwolnij ustalony zbiór rozmiarów alokacji z różnych wątkach lub zadania. Współbieżność środowiska wykonawczego buforuje pamięci przydzielanej ze stosu C Runtime. Współbieżność środowiska wykonawczego zawiera osobne pamięci podręcznej dla każdego uruchomionego wątku; w związku z tym środowiska uruchomieniowego zarządza pamięci bez użycia blokady lub bariery pamięci. Aplikacja przynosi korzyści z jednego z `Alloc` i `Free` funkcje częściej dostępie pamięci podręcznej. Na przykład wątku, który często wywołuje zarówno `Alloc` i `Free` korzyści więcej niż wątek, który wywołuje głównie `Alloc` lub `Free`.  
  
> [!NOTE]
>  Podczas korzystania z tych funkcji zarządzania pamięci i może zawierać wiele zastosowań aplikacji z pamięci, aplikacja niedostatecznej ilości pamięci krócej niż można oczekiwać. Ponieważ bloki pamięci, które są buforowane przez jeden wątek nie są dostępne dla innych wątków, jeśli jeden wątek przechowuje dużej ilości pamięci, że pamięć nie jest dostępna.  
  
## <a name="example"></a>Przykład  
 Na przykład, który używa `Alloc` i `Free` funkcje do poprawiania wydajności pamięci, zobacz [porady: użycie alokacji i wolne do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Instrukcje: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

