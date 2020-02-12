---
title: 'Porady: korzystanie z parallel_invoke do przeprowadzania operacji równoległych'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: 199b663331e3322601100206f222e80bbb7c8db0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142273"
---
# <a name="how-to-use-parallel_invoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke do przeprowadzania operacji równoległych

Ten przykład pokazuje, jak używać algorytmu [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) , aby zwiększyć wydajność programu wykonującego wiele operacji w udostępnionym źródle danych. Ponieważ żadne operacje nie modyfikują źródła, mogą być wykonywane równolegle w prosty sposób.

## <a name="example"></a>Przykład

Rozważmy następujący przykładowy kod, który tworzy zmienną typu `MyDataType`, wywołuje funkcję w celu zainicjowania tej zmiennej, a następnie wykonuje wiele długotrwałych operacji na tych danych.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Jeśli funkcje `lengthy_operation1`, `lengthy_operation2`i `lengthy_operation3` nie modyfikują zmiennej `MyDataType`, te funkcje mogą być wykonywane równolegle bez dodatkowych modyfikacji.

## <a name="example"></a>Przykład

Poniższy przykład modyfikuje poprzedni przykład, aby uruchomić go równolegle. Algorytm `parallel_invoke` wykonuje każde zadanie równolegle i zwraca po zakończeniu wszystkich zadań.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład pobiera *Iliad* przez homegrouper z Gutenberg.org i wykonuje wiele operacji na tym pliku. Przykład wykonuje najpierw te operacje szeregowo, a następnie wykonuje te same operacje równolegle.

[!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]

Ten przykład generuje następujące przykładowe dane wyjściowe.

```Output
Downloading 'The Iliad'...

Running serial version... took 953 ms.
Running parallel version... took 656 ms.

The most common words that have five or more letters are:
    their (953)
    shall (444)
    which (431)
    great (398)
    Hector (349)
    Achilles (309)
    through (301)
    these (268)
    chief (259)
The longest sequence of words that have the same first letter is:
    through the tempest to the tented
The following palindromes appear in the text:
    spots stops
    speed deeps
    keels sleek
```

W tym przykładzie używamy algorytmu `parallel_invoke` do wywołania wielu funkcji, które działają na tym samym źródle danych. Można użyć algorytmu `parallel_invoke` do wywołania dowolnego zestawu funkcji równolegle, nie tylko tych, które działają na tych samych danych.

Ponieważ algorytm `parallel_invoke` wywołuje każdą funkcję roboczą równolegle, jej wydajność jest ograniczona przez funkcję, która trwa najdłużej (to oznacza, jeśli środowisko uruchomieniowe przetwarza każdą funkcję na osobnym procesorze). Jeśli ten przykład wykonuje więcej zadań równolegle niż liczba dostępnych procesorów, na każdym procesorze można uruchamiać wiele zadań. W takim przypadku wydajność jest ograniczona przez grupę zadań, które trwają najdłużej.

Ponieważ ten przykład wykonuje równolegle trzy zadania, nie należy oczekiwać skalowania wydajności na komputerach, które mają więcej niż trzy procesory. Aby zwiększyć wydajność, można przerwać długotrwałe zadania w mniejszych zadaniach i uruchamiać te zadania równolegle.

Można użyć algorytmu `parallel_invoke` zamiast klas [concurrency:: task_group](reference/task-group-class.md) i [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , jeśli nie jest wymagana obsługa anulowania. Aby zapoznać się z przykładem porównującym użycie algorytmu `parallel_invoke` w porównaniu z grupami zadań, zobacz [How to: Use parallel_invoke by napisać równoległą procedurę sortowania](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować kod, skopiuj go, a następnie wklej w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-word-mining.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc/MD/DUNICODE/D_AFXDLL Parallel-Word-Mining. cpp**

## <a name="see-also"></a>Zobacz też

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Funkcja parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke)
