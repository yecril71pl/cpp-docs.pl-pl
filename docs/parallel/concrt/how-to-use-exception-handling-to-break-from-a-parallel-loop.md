---
title: 'Instrukcje: Użyj wyjątków, obsługa aby przerwać pętlę równoległą'
ms.date: 11/04/2016
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
ms.openlocfilehash: 19d732d98f24172471d96cd5e2962b2a99ab0203
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57262314"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Instrukcje: Użyj wyjątków, obsługa aby przerwać pętlę równoległą

W tym temacie pokazano, jak napisać algorytm wyszukiwania w strukturze drzewa podstawowe.

Temat [anulowania](cancellation-in-the-ppl.md) opisano rolę anulowania biblioteki wzorców równoległych. Korzystanie z obsługi wyjątków jest mniej skuteczny sposób, aby anulować czynność równoległą niż korzystanie z [concurrency::task_group::cancel](reference/task-group-class.md#cancel) i [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metody. Jeden scenariusz, w których korzystanie z obsługi wyjątków można anulować pracy jest właściwe jest jednak po wywołaniu do biblioteki innej firmy, która używa zadania lub algorytmów równoległych, ale nie zapewnia `task_group` lub `structured_task_group` obiektu, aby anulować.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia podstawowe `tree` typu, który zawiera element danych i listę węzłów podrzędnych. W poniższej sekcji pokazano treści `for_all` metody cyklicznie, która wykonuje funkcję pracy w każdym węźle podrzędnych.

[!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `for_all` metody. Używa ona [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm funkcja pracy w każdym węźle drzewa równolegle.

[!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono `search_for_value` funkcji, która wyszukuje wartość w określonych `tree` obiektu. Tę funkcję, przekazuje do `for_all` metoda funkcję pracy, która zgłasza wyjątek, gdy znajdzie węzeł drzewa zawierający podanej wartości.

Przyjęto założenie, że `tree` klasy są dostarczane przez biblioteki innej firmy, a nie można go modyfikować. W tym przypadku jest korzystanie z obsługi wyjątków ponieważ `for_all` metoda nie dostarcza `task_group` lub `structured_task_group` obiektu do obiektu wywołującego. W związku z tym funkcja pracy nie może bezpośrednio anulować jej nadrzędnej grupy zadań.

Gdy ta funkcja pracy, które zapewniają do grupy zadań zgłasza wyjątek, środowisko uruchomieniowe zatrzymuje wszystkie zadania, które znajdują się w grupie zadań (w tym wszystkie grupy zadań podrzędnych) i odrzuca wszelkie zadania, które nie zostały rozpoczęte. `search_for_value` Używa funkcji `try` - `catch` bloku, aby przechwycić wyjątek i wydrukować wynik do konsoli.

[!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład tworzy `tree` obiekt i wyszukuje kilka wartości równolegle. `build_tree` Funkcji jest przedstawiony w dalszej części tego tematu.

[!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]

W tym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu wyszukiwania wartości w sposób równoległy. Aby uzyskać więcej informacji na temat tego algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pełną użyto obsługi wyjątków do wyszukiwania wartości w postaci struktury drzewiastej podstawowe.

[!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
Found a node with value 32614.
Found a node with value 86131.
Did not find node with value 17522.
```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `task-tree-search.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc zadań drzewa search.cpp**

## <a name="see-also"></a>Zobacz także

[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[task_group, klasa](reference/task-group-class.md)<br/>
[structured_task_group, klasa](../../parallel/concrt/reference/structured-task-group-class.md)<br/>
[parallel_for_each Function](reference/concurrency-namespace-functions.md#parallel_for_each)
