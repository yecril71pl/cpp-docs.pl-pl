---
title: 'Porady: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
ms.openlocfilehash: f47beb7deffa0511e707768d2a1a84f47e489d5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608406"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze współbieżności środowiska wykonawczego

W tym przykładzie opisano sposób konwertowania OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, która wykonuje obsługi wyjątków do użycia mechanizm obsługi wyjątków współbieżność środowiska wykonawczego.

OpenMP wyjątek, który jest zgłaszany w równoległego regionu musi być przechwycony i obsługiwane w tym samym regionie, w tym samym wątku. Wyjątek, który specjalne równoległego regionu zostanie przechwycony przez program obsługi nieobsługiwanego wyjątku, który kończy proces domyślnie.

W środowisku uruchomieniowym współbieżności, gdy zgłoszenie wyjątku w treści funkcji roboczych, które przechodzą do grupy zadań takich jak [concurrency::task_group](reference/task-group-class.md) lub [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu, lub do algorytmu równoległego, takie jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), środowisko uruchomieniowe przechowuje ten wyjątek i kieruje je do kontekstu, która czeka, aż grupy zadań lub algorytm, aby zakończyć. Dla grup zadań kontekst oczekiwania jest kontekst, który wywołuje [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait), [CONCURRENCY::structured_task_group:: wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and _wait](reference/task-group-class.md#run_and_wait), lub [CONCURRENCY::structured_task_group::](reference/structured-task-group-class.md#run_and_wait). Dla algorytmu równoległego kontekst oczekiwania jest kontekst, który wywołuje się, że algorytm. Środowisko uruchomieniowe również zatrzymuje wszystkie aktywne zadania, które należą do grupy zadań, włącznie z zawartymi na grupy zadań podrzędnych, i odrzuca wszelkie zadania, które nie zostały rozpoczęte.

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak obsługa wyjątków w OpenMP `parallel` regionu, w wywołaniu `parallel_for`. `do_work` Funkcja wykonuje żądanie alokacji pamięci, która kończy się niepowodzeniem i zgłasza wyjątek typu, w związku z tym [std::bad_alloc](../../standard-library/bad-alloc-class.md). W wersji, która używa OpenMP wątek, który zgłasza wyjątek również należy wyłapać go. Innymi słowy w każdej iteracji pętli równoległej OpenMP musi obsłużyć wyjątek. W wersji, która używa środowiska uruchomieniowego współbieżności wątek główny przechwytuje wyjątek, który jest generowany przez inny wątek.

[!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]

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

W wersji tego przykładu, który używa OpenMP wyjątek występuje w i odbywa się przy każdej iteracji pętli. W wersji, która używa środowiska uruchomieniowego współbieżności, środowisko uruchomieniowe przechowuje wyjątek, zatrzymuje wszystkie aktywne zadania, odrzuca wszelkie zadania, które nie zostały uruchomione i kieruje wyjątku do kontekstu, który wywołuje `parallel_for`.

Jeśli potrzebujesz, wersji, która używa OpenMP kończy działanie po wystąpieniu wyjątku, można użyć Flaga wartości logicznej do sygnalizowania innych iteracji pętli, że wystąpił błąd. Tak jak w przykładzie w tym temacie [porady: konwertowanie pętli OpenMP tego używa anulowanie do korzystania ze współbieżności środowiska wykonawczego](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), iteracji pętli kolejnych będzie nic nie rób, jeśli flaga jest ustawiona. Z drugiej strony Jeśli potrzebujesz, że pętli, która korzysta ze współbieżności środowiska wykonawczego ma kontynuować działanie po wystąpieniu wyjątku, obsługiwać wyjątek w ciele pętli równoległej sam.

Inne składniki środowiska uruchomieniowego współbieżności, np. agentów asynchronicznych i zadań lekkich nie transportować. Zamiast tego nieobsłużone wyjątki są przechwytywane przez program obsługi nieobsługiwanego wyjątku, który kończy proces domyślnie. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

Aby uzyskać więcej informacji na temat `parallel_for` i innych równoległych algorytmów, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-exceptions.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc/OpenMP concrt-omp — exceptions.cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

