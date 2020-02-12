---
title: 'Porady: Użyj obsługi wyjątków, aby przerwać pętlę równoległą'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: a5576e8f2416804cac89f5ec34005f4e08b99c47
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142110"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Porady: Użyj obsługi wyjątków, aby przerwać pętlę równoległą

W tym temacie pokazano, jak napisać algorytm wyszukiwania dla podstawowej struktury drzewa.

[Anulowanie](cancellation-in-the-ppl.md) tematu wyjaśnia rolę anulowania w bibliotece wzorców równoległych. Korzystanie z obsługi wyjątków jest mniej wydajnym sposobem anulowania równoległej pracy niż użycie metody [concurrency:: task_group:: Cancel](reference/task-group-class.md#cancel) i [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) . Jednak jednym scenariuszem, w którym użycie obsługi wyjątków do anulowania pracy jest odpowiednie, jest wywołanie do biblioteki innej firmy, która korzysta z zadań lub algorytmów równoległych, ale nie zapewnia `task_group` lub `structured_task_group` obiektu do anulowania.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia podstawowy typ `tree`, który zawiera element danych i listę węzłów podrzędnych. W poniższej sekcji przedstawiono treść metody `for_all`, która rekursywnie wykonuje funkcję roboczą w każdym węźle podrzędnym.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład przedstawia metodę `for_all`. Używa algorytmu [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) do wykonywania funkcji pracy w każdym węźle drzewa równolegle.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano funkcję `search_for_value`, która wyszukuje wartość z podanego `tree` obiektu. Ta funkcja przekazuje do `for_all` metodę pracy, która zgłasza, gdy odnajdzie węzeł drzewa zawierający podaną wartość.

Załóżmy, że Klasa `tree` jest udostępniana przez bibliotekę innych firm i nie można jej modyfikować. W takim przypadku użycie obsługi wyjątków jest odpowiednie, ponieważ metoda `for_all` nie udostępnia obiektu wywołującego `task_group` lub `structured_task_group`. W związku z tym funkcja pracy nie może bezpośrednio anulować swojej nadrzędnej grupy zadań.

Gdy funkcja robocza dostarczana do grupy zadań zgłasza wyjątek, środowisko uruchomieniowe przerywa wszystkie zadania, które znajdują się w grupie zadań (w tym wszystkie podrzędne grupy zadań) i odrzuca zadania, które nie zostały jeszcze uruchomione. Funkcja `search_for_value` używa bloku `try`-`catch`, aby przechwycić wyjątek i wydrukować wynik do konsoli.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład tworzy obiekt `tree` i wyszukuje kilka wartości równolegle. Funkcja `build_tree` jest przedstawiona w dalszej części tego tematu.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

W poniższym przykładzie zastosowano algorytm [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) , aby wyszukiwać wartości równolegle. Aby uzyskać więcej informacji na temat tego algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Przykład

W poniższym przykładzie zastosowano obsługę wyjątków w celu wyszukania wartości w podstawowej strukturze drzewa.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `task-tree-search.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Task-Tree-Search. cpp**

## <a name="see-also"></a>Zobacz też

[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group, klasa](reference/task-group-class.md)<br/>
[structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[Funkcja parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each)
