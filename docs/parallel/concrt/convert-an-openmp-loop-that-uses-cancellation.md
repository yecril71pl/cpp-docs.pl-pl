---
title: 'Porady: konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: adde6decc086b883c50e52d12e388197e185fb39
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505944"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze współbieżności środowiska wykonawczego

Niektóre pętle równoległe nie wymagają wykonania wszystkich iteracji. Na przykład algorytm, który wyszukuje wartość można przerwać po znalezieniu wartości. OpenMP nie udostępnia mechanizmu do rozbicia pętli równoległej. Można jednak użyć wartości logicznej lub flagi, aby umożliwić iterację pętli w celu wskazania, że rozwiązanie zostało znalezione. Środowisko uruchomieniowe współbieżności udostępnia funkcje, które umożliwiają jednemu zadaniu anulowanie innych zadań, które nie zostały jeszcze uruchomione.

W tym przykładzie pokazano, jak przekonwertować [równoległą](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)pętlę OpenMP[dla](../openmp/reference/openmp-directives.md#for-openmp) pętli, która nie jest wymagana dla wszystkich iteracji do uruchomienia, aby użyć mechanizmu anulowania środowisko uruchomieniowe współbieżności.

## <a name="example"></a>Przykład

W tym przykładzie używamy OpenMP i środowisko uruchomieniowe współbieżności do implementowania równoległej wersji algorytmu [std:: any_of](../../standard-library/algorithm-functions.md#any_of) . Wersja OpenMP tego przykładu używa flagi do koordynowania wszystkich iteracji pętli równoległej, że warunek został spełniony. Wersja, która używa środowisko uruchomieniowe współbieżności używa metody [concurrency:: structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) do zatrzymania operacji ogólnej, gdy warunek zostanie spełniony.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

W wersji programu, która używa OpenMP, wszystkie iteracje pętli są wykonywane nawet wtedy, gdy flaga jest ustawiona. Ponadto, jeśli zadanie miało jakiekolwiek zadania podrzędne, ta flaga również musi być dostępna dla tych zadań podrzędnych, aby komunikować się z anulowaniem. W środowisko uruchomieniowe współbieżności, gdy grupa zadań zostanie anulowana, środowisko uruchomieniowe anuluje całe drzewo pracy, łącznie z zadaniami podrzędnymi. Algorytm [concurrency::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) używa zadań do wykonania pracy. W związku z tym, gdy jedna iteracja pętli anuluje zadanie główne, całe drzewo obliczeń również zostanie anulowane. Po anulowaniu drzewa pracy środowisko uruchomieniowe nie uruchamia nowych zadań. Jednak środowisko uruchomieniowe umożliwia wykonywanie zadań, które zostały już uruchomione. W związku z tym, w przypadku `parallel_for_each` algorytmu, iteracje pętli aktywne mogą czyścić swoje zasoby.

W obu wersjach tego przykładu, jeśli tablica zawiera więcej niż jedną kopię wartości do wyszukania, wiele iteracji pętli może jednocześnie ustawić wynik i anulować operację ogólną. Możesz użyć pierwotnej synchronizacji, takiej jak Sekcja krytyczna, jeśli problem wymaga, aby tylko jedno zadanie działało, gdy spełniony jest warunek.

Można również użyć obsługi wyjątków, aby anulować zadania korzystające z PPL. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowania w PPL](cancellation-in-the-ppl.md).

Aby uzyskać więcej informacji na temat `parallel_for_each` i innych algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie, `concrt-omp-parallel-any-of.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **cl.exe/EHsc/OpenMP ConcRT-OMP-Parallel-Any-of. cpp**

## <a name="see-also"></a>Zobacz też

[Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)
