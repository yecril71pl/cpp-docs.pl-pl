---
title: "Porady: używanie parallel_invoke do napisania procedury sortowania równoległego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- task_handle class, example
- task_group class, example
- make_task function, example
- structured_task_group class, example
- improving parallel performance with task groups [Concurrency Runtime]
ms.assetid: 53979a2a-525d-4437-8952-f1ff85b37673
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ff14294236efc26b83d31ad185dc1cfd6329dbe9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-parallelinvoke-to-write-a-parallel-sort-routine"></a>Porady: używanie parallel_invoke do napisania procedury sortowania równoległego
W tym dokumencie opisano sposób użycia [parallel_invoke](../../parallel/concrt/parallel-algorithms.md#parallel_invoke) algorytmu, aby poprawić wydajność bitonic algorytm sortowania. Rekursywnie algorytm sortowania bitonic dzieli sekwencji wejściowych na mniejsze partycje posortowane. Algorytm sortowania bitonic może działać równolegle, ponieważ każda operacja partycja jest niezależna od innych operacji.  
  
 Mimo że sortowanie bitonic jest przykładem *sortowanie sieci* który sortuje wszystkich kombinacji sekwencji wejściowych, w tym przykładzie sortuje sekwencji, których długości są potęgą liczby dwa.  
  
> [!NOTE]
>  W tym przykładzie użyto procedury sortowania równoległego ilustracyjną. Można również użyć wbudowanych algorytmów sortowania, które zapewnia PPL: [concurrency::parallel_sort](reference/concurrency-namespace-functions.md#parallel_sort), [concurrency::parallel_buffered_sort](reference/concurrency-namespace-functions.md#parallel_buffered_sort), i [concurrency::parallel_ radixsort](reference/concurrency-namespace-functions.md#parallel_radixsort). Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="top"></a>Sekcje  
 W tym dokumencie opisano następujące zadania:  
  
- [Sposób wykonywania Bitonic sortowania](#serial)  
  
- [Przy użyciu parallel_invoke do wykonania sortowania Bitonic równolegle](#parallel)  
  
##  <a name="serial"></a>Sposób wykonywania Bitonic sortowania  
 Poniższy przykład przedstawia serial wersji bitonic algorytm sortowania. `bitonic_sort` Funkcja sekwencji jest podzielony na dwie partycje, sortuje te partycje w przeciwną kierunkach i następnie scala wyniki. Ta funkcja wymaga rekursywnie dwa razy, aby posortować każdej partycji.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_1.cpp)]  
  
 [[Górnej](#top)]  
  
##  <a name="parallel"></a>Przy użyciu parallel_invoke do wykonania sortowania Bitonic równolegle  
 W tej sekcji opisano sposób użycia `parallel_invoke` algorytm algorytm sortowania bitonic równolegle.  
  
### <a name="procedures"></a>Procedury  
  
##### <a name="to-perform-the-bitonic-sort-algorithm-in-parallel"></a>Aby wykonać algorytm bitonicznego sortowania równolegle  
  
1.  Dodaj `#include` dyrektywy dla ppl.h pliku nagłówka.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#10](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_2.cpp)]  
  
2.  Dodaj `using` dyrektywy dla `concurrency` przestrzeni nazw.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#11](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_3.cpp)]  
  
3.  Utwórz nową funkcję o nazwie `parallel_bitonic_mege`, który korzysta z `parallel_invoke` algorytmu do scalenia sekwencji równolegle, jeśli istnieje wystarczająca ilość pracy. W przeciwnym razie wywołać `bitonic_merge` do scalenia sekwencji pojedynczo.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_4.cpp)]  
  
4.  Wykonaj proces opisany w poprzednim kroku, ale dla `bitonic_sort` funkcji.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_5.cpp)]  
  
5.  Utwórz przeciążone wersję `parallel_bitonic_sort` funkcja sortujące tablicy w kolejności rosnącej.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#4](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_6.cpp)]  
  
 `parallel_invoke` Algorytmu zmniejsza obciążenie związane z przez wykonanie ostatniego sekwencję zadań w kontekście wywołującego. Na przykład w `parallel_bitonic_sort` funkcji, pierwszy zadanie jest uruchamiane w kontekście oddzielne i drugi zadanie jest uruchamiane w kontekście wywołującego.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#5](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_7.cpp)]  
  
 Poniższy przykład pełną wykonuje zarówno wersji równoległych algorytm sortowania bitonic, jak i numer seryjny. Przykład drukuje do konsoli również czas, który jest wymagany do wykonania poszczególnych obliczeń.  
  
 [!code-cpp[concrt-parallel-bitonic-sort#8](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_8.cpp)]  
  
 Następujące przykładowe dane wyjściowe jest dla komputera, który ma cztery procesory.  
  
```Output  
serial time: 4353  
parallel time: 1248  
```  
  
 [[Górnej](#top)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-bitonic-sort.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc równoległe bitonic-sort.cpp**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 W tym przykładzie użyto `parallel_invoke` algorytmu zamiast [concurrency::task_group](reference/task-group-class.md) klasy, ponieważ okres istnienia dla każdej grupy zadań nie wykracza poza funkcją. Firma Microsoft zaleca użycie `parallel_invoke` po można ponieważ ma ona wykonywania mniejszy narzut niż `task group` obiekty i w związku z tym umożliwia zapisanie lepsze wykonywanie kodu.  
  
 Równoległe wersje niektóre algorytmy działać lepiej tylko wtedy, gdy istnieje wystarczająca pracy. Na przykład `parallel_bitonic_merge` funkcja wywołuje wersji serial `bitonic_merge`, jeśli istnieją 500 lub mniejszą liczbę elementów w sekwencji. Można również zaplanować ogólna strategia sortowania na podstawie ilości pracy. Na przykład może być bardziej wydajne, można użyć serial wersji algorytm szybkiego sortowania, jeśli tablica zawiera mniej niż 500 elementów, jak pokazano w poniższym przykładzie:  
  
 [!code-cpp[concrt-parallel-bitonic-sort#9](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine_9.cpp)]  
  
 Podobnie jak w przypadku dowolnego algorytmu równoległe, zaleca się, profile i dostosowywać kod zależnie od potrzeb.  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [parallel_invoke — funkcja](reference/concurrency-namespace-functions.md#parallel_invoke)

