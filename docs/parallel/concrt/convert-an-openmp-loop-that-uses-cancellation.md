---
title: 'Instrukcje: Konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze współbieżności środowiska wykonawczego'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
ms.openlocfilehash: 618e93c18173bfe3e5f5b5f3058a8bb3d61e98ec
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300678"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Instrukcje: Konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze współbieżności środowiska wykonawczego

Niektóre pętlach równoległych nie wymagają wykonania wszystkich iteracji. Na przykład algorytm, który wyszukuje wartość może zakończyć po znajduje się wartość. OpenMP nie zapewnia mechanizm zerwać pętlę równoległą. Jednak można użyć wartość logiczna lub flagi, aby włączyć iteracji pętli, aby wskazać, że wykryto rozwiązania. Środowisko uruchomieniowe współbieżności udostępnia funkcje umożliwiające jedno zadanie anulować inne zadania, które nie zostały rozpoczęte.

W tym przykładzie opisano sposób konwertowania OpenMP [równoległe](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, która nie wymaga dla wszystkich iteracji uruchomić użycie mechanizmu anulowania współbieżność środowiska wykonawczego.

## <a name="example"></a>Przykład

W tym przykładzie używa OpenMP i środowisku uruchomieniowym współbieżności: do implementacji równoległych wersji [std::any_of](../../standard-library/algorithm-functions.md#any_of) algorytmu. Wersja OpenMP — w tym przykładzie używa flagi do zapewnienia koordynacji między wszystkich iteracji pętli równoległej warunek został spełniony. Korzysta z wersji, która używa środowiska uruchomieniowego współbieżności [CONCURRENCY::structured_task_group:: Cancel](reference/structured-task-group-class.md#cancel) metodę, aby zatrzymać operację ogólną, gdy warunek jest spełniony.

[!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
Using OpenMP...
9114046 is in the array.
Using the Concurrency Runtime...
9114046 is in the array.
```

W wersji używającego OpenMP wszystkich iteracji pętli są wykonywane, nawet wtedy, gdy flaga jest ustawiona. Co więcej gdyby zadanie ma żadnych zadań podrzędnych, flagę również musi być dostępne dla tych zadań podrzędnych do komunikowania się anulowania. Po anulowaniu grupy zadań w środowisku uruchomieniowym współbieżności środowiska wykonawczego anuluje całego drzewa pracy, w tym zadań podrzędnych. [Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm używa zadania do wykonywania pracy. W związku z tym po jednej iteracji pętli anuluje zadania głównego, całe drzewo obliczeń również zostało anulowane. Po anulowaniu drzewa pracy środowisko wykonawcze nie można uruchomić nowego zadania. Jednak środowisko uruchomieniowe umożliwia zadania, które zostało już rozpoczęte, aby zakończyć. W związku z tym, w przypadku właściwości `parallel_for_each` algorytm iteracji pętli active można oczyścić swoje zasoby.

W obu wersjach w tym przykładzie Jeśli tablica zawiera więcej niż jedną kopię wartość do wyszukiwania, wiele iteracji pętli można jednocześnie ustawić każdy wynik i anulować operację ogólną. Możesz użyć pierwotny synchronizacji, takie jak sekcję krytyczną, jeśli problem wymaga, że tylko jedno zadanie wykonuje pracę, gdy warunek jest spełniony.

Można również użyć obsługi wyjątków, aby anulować zadania, które używają PPL. Aby uzyskać więcej informacji dotyczących anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

Aby uzyskać więcej informacji na temat `parallel_for_each` i innych równoległych algorytmów, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-parallel-any-of.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc/OpenMP concrt-omp — równoległe any-of.cpp**

## <a name="see-also"></a>Zobacz także

[Migrowanie z OpenMP do środowiska uruchomieniowego współbieżności](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)
