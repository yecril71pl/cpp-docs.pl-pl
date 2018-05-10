---
title: 'Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0be6fa309975663126331a7e38be0f2bea7dcf17
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Porady: używanie z funkcji Alloc i Free do poprawiania wydajności pamięci

Ten dokument przedstawia sposób użycia [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) i [concurrency::Free](reference/concurrency-namespace-functions.md#free) funkcje do poprawiania wydajności pamięci. Czas, który jest wymagany, aby odwrócić elementów tablicy równolegle na trzy różne typy, które są porównywane każdego określ `new` i `delete` operatorów.  

  
 `Alloc` i `Free` funkcje są najbardziej przydatne, gdy wiele wątków często wywołać metodę `Alloc` i `Free`. Środowisko uruchomieniowe zawiera osobne pamięci podręcznej dla każdego wątku; w związku z tym środowiska uruchomieniowego zarządza pamięci bez użycia blokady lub bariery pamięci.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono trzy typy każdego określ `new` i `delete` operatorów. `new_delete` Klasa korzysta z globalnej `new` i `delete` operatorów, `malloc_free` klasy używa środowiska wykonawczego C [— funkcja malloc](../../c-runtime-library/reference/malloc.md) i [wolnego](../../c-runtime-library/reference/free.md) funkcje i `Alloc_Free` Klasa korzysta ze współbieżności środowiska wykonawczego `Alloc` i `Free` funkcji.  
  
 [!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `swap` i `reverse_array` funkcji. `swap` Funkcja wymiany zawartości tablicy w określonej indeksów. Przydzielania pamięci sterty dla zmiennej tymczasowej. `reverse_array` Funkcja tworzy dużą tablicę i oblicza czas, który jest wymagany, aby odwrócić tablicy w równolegle.  
  
 [!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `wmain` funkcji, która oblicza czas, który jest wymagany dla `reverse_array` funkcji, które działają na `new_delete`, `malloc_free`, i `Alloc_Free` typów, z których każdy wykorzystuje schemat alokacji pamięci inny.  
  
 [!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]  
  
## <a name="example"></a>Przykład  
 Pełny przykład jest zgodna.  
  
 [!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe dla komputera, który ma cztery procesory.  
  
```Output  
Took 2031 ms with new/delete.  
Took 1672 ms with malloc/free.  
Took 656 ms with Alloc/Free.  
```  
  
 W tym przykładzie typ, który używa `Alloc` i `Free` funkcje zapewnia najlepszą wydajność, ponieważ `Alloc` i `Free` funkcje są zoptymalizowane często podziału i zwalnianie bloków pamięci z wielu wątki.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `allocators.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe allocators.cpp/ehsc**  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje zarządzania pamięcią](../../parallel/concrt/memory-management-functions.md)   
 [ALLOC — funkcja](reference/concurrency-namespace-functions.md#alloc)   
 [Free — funkcja](reference/concurrency-namespace-functions.md#free)

