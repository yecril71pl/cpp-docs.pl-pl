---
title: 'Porady: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: 380a96eedb8a70965197c4a5ce0c5199bc268db5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141814"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie pokazano, jak przekonwertować [równoległą](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)pętlę OpenMP[dla](../../parallel/openmp/reference/for-openmp.md) pętli, która wykonuje obsługę wyjątków w celu używania mechanizmu obsługi wyjątków środowisko uruchomieniowe współbieżności.

W OpenMP wyjątek, który jest generowany w równoległym regionie, musi być przechwycony i obsłużony w tym samym regionie przez ten sam wątek. Wyjątek, który wyprowadza region równoległy, jest przechwytywany przez nieobsłużoną procedurę obsługi wyjątków, która domyślnie kończy proces.

W środowisko uruchomieniowe współbieżności, gdy zgłaszasz wyjątek w treści funkcji służbowej, która została przekazana do grupy zadań, takiej jak concurrency [:: task_group](reference/task-group-class.md) lub [Concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , lub do algorytmu równoległego, takiego jak [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), środowisko uruchomieniowe przechowuje ten wyjątek i przekazuje go do kontekstu, który czeka na zakończenie grupy zadań lub algorytmu. W przypadku grup zadań kontekst oczekujący to kontekst, który wywołuje [concurrency:: task_group:: wait](reference/task-group-class.md#wait), [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait), [concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)lub [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Dla algorytmu równoległego kontekst oczekujący to kontekst, który wywołał ten algorytm. Środowisko uruchomieniowe przerywa również wszystkie aktywne zadania, które znajdują się w grupie zadań, łącznie z tymi w podrzędnych grupach zadań i odrzuca zadania, które nie zostały jeszcze uruchomione.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak obsługiwać wyjątki w regionie `parallel` OpenMP i w wywołaniu `parallel_for`. Funkcja `do_work` wykonuje żądanie alokacji pamięci, które nie powiedzie się i w związku z tym zgłasza wyjątek typu [std:: bad_alloc](../../standard-library/bad-alloc-class.md). W wersji korzystającej ze OpenMP należy również przechwycić wątek, który zgłasza wyjątek. Innymi słowy, każda iteracja pętli równoległej OpenMP musi obsłużyć wyjątek. W wersji, która używa środowisko uruchomieniowe współbieżności, główny wątek przechwytuje wyjątek, który jest generowany przez inny wątek.

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-exception-handling_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
An error of type 'class std::bad_alloc' occurred.
Using the Concurrency Runtime...
An error of type 'class std::bad_alloc' occurred.
```

W wersji tego przykładu, która używa OpenMP, wyjątek występuje w i jest obsługiwany przez każdą iterację pętli. W wersji, która używa środowisko uruchomieniowe współbieżności, środowisko uruchomieniowe przechowuje wyjątek, kończy wszystkie aktywne zadania, odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione i kierujący wyjątek do kontekstu wywołującego `parallel_for`.

Jeśli wymagasz, aby wersja, która używa systemu OpenMP kończy się po wystąpieniu wyjątku, można użyć flagi logicznej do sygnalizowania innych iteracji pętli, które wystąpił błąd. Jak w przykładzie w temacie [jak: konwertowanie pętli OpenMP, która używa anulowania do używania środowisko uruchomieniowe współbieżności](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), kolejne iteracje pętli spowodują, że flaga jest ustawiona. Z drugiej strony, jeśli wymagana jest pętla, która używa środowisko uruchomieniowe współbieżności kontynuuje po wystąpieniu wyjątku, należy obsłużyć wyjątek w samej części pętli równoległej.

Inne składniki środowisko uruchomieniowe współbieżności, takie jak agenci asynchroniczni i uproszczone zadania, nie transportuje wyjątków. Zamiast tego Nieobsłużone wyjątki są przechwytywane przez nieobsłużoną procedurę obsługi wyjątków, która domyślnie kończy proces. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Aby uzyskać więcej informacji na temat `parallel_for` i innych algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-exceptions.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc/OpenMP ConcRT-OMP-Exceptions. cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)
