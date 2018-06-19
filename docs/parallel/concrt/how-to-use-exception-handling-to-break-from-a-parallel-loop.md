---
title: 'Porady: Użyj obsługi aby przerwać pętlę równoległą wyjątków | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search algorithm, writing [Concurrency Runtime]
- writing a search algorithm [Concurrency Runtime]
ms.assetid: 16d7278c-2d10-4014-9f58-f1899e719ff9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6bacb9ea6a451026f7a515878cb649090ed9cbf4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691849"
---
# <a name="how-to-use-exception-handling-to-break-from-a-parallel-loop"></a>Porady: Użyj obsługi wyjątków, aby przerwać pętlę równoległą
W tym temacie przedstawia sposób zapisania algorytmu wyszukiwania dla struktury drzewa podstawowe.  
  
 Temat [anulowania](cancellation-in-the-ppl.md) wyjaśniono roli anulowania Biblioteka wzorów równoległych. Korzystanie z obsługi wyjątków jest mniej wydajne sposób anulowania pracy równoległej niż użycie [concurrency::task_group::cancel](reference/task-group-class.md#cancel) i [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metody. Jednak jeden scenariusz, w którym korzystanie z obsługi wyjątków, aby anulować pracy jest odpowiednie jest podczas wywołania do biblioteki innej firmy, która używa zadań lub algorytmy równoległe, ale nie zapewnia `task_group` lub `structured_task_group` obiekt, aby anulować.  

  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia podstawowy `tree` typu, który zawiera element danych i listy węzłów podrzędnych. W poniższej sekcji przedstawiono treści `for_all` metody, które rekursywnie pełni funkcję pracy na każdy węzeł podrzędny.  
  
 [!code-cpp[concrt-task-tree-search#2](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_1.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `for_all` metody. Używa [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm funkcji pracy w każdym węźle drzewa równolegle.  
  
 [!code-cpp[concrt-task-tree-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_2.cpp)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `search_for_value` funkcji, która wyszukuje wartość w określonych `tree` obiektu. Ta funkcja przekazuje do `for_all` metody, a funkcja pracy, która zgłasza, gdy znajdzie węzła drzewa, który zawiera podana wartość.  
  
 Przyjęto założenie, że `tree` klasy są dostarczane przez bibliotekę innych firm, a nie można go modyfikować. W takim przypadku korzystanie z obsługi wyjątków jest odpowiednie ponieważ `for_all` metoda nie dostarcza `task_group` lub `structured_task_group` obiektu do obiektu wywołującego. W związku z tym funkcja pracy nie może bezpośrednio anulować jej nadrzędnej grupy zadań.  
  
 Funkcji pracy, które świadczą grupy zadań zgłasza wyjątek, środowisko uruchomieniowe zatrzyma wszystkie zadania, które znajdują się w grupie zadań (łącznie z wszelkich podrzędnych grup zadań) i odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione. `search_for_value` Używa `try` - `catch` blok do przechwycenia wyjątek i wydrukować wynik do konsoli.  
  
 [!code-cpp[concrt-task-tree-search#3](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_3.cpp)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy `tree` obiektu i wyszukuje kilka wartości równolegle. `build_tree` Funkcja przedstawiono w dalszej części tego tematu.  
  
 [!code-cpp[concrt-task-tree-search#4](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_4.cpp)]  
  
 W tym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu wyszukiwania wartości równolegle. Aby uzyskać więcej informacji dotyczących tego algorytmu, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pełną użyto obsługi wyjątków do wyszukiwania wartości w postaci struktury drzewiastej podstawowe.  
  
 [!code-cpp[concrt-task-tree-search#5](../../parallel/concrt/codesnippet/cpp/how-to-use-exception-handling-to-break-from-a-parallel-loop_5.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe.  
  
```Output  
Found a node with value 32614.  
Found a node with value 86131.  
Did not find node with value 17522.  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `task-tree-search.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc zadania drzewa search.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [task_group — klasa](reference/task-group-class.md)   
 [structured_task_group — klasa](../../parallel/concrt/reference/structured-task-group-class.md)   
 [parallel_for_each — funkcja](reference/concurrency-namespace-functions.md#parallel_for_each)


