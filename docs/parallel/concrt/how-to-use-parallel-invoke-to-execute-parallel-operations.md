---
title: 'Instrukcje: Korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
ms.openlocfilehash: d618b5f202c6aaf454a60f4f37211d9000600562
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293527"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Instrukcje: Korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych

W tym przykładzie pokazano, jak używać [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu, aby zwiększyć wydajność programu, który wykonuje wiele operacji na udostępnione źródło danych. Ponieważ żadne operacje zmodyfikować źródło, mogą być wykonywane równolegle w prosty sposób.

## <a name="example"></a>Przykład

Należy wziąć pod uwagę poniższy kod, który tworzy zmienną typu `MyDataType`, wywołuje funkcję, aby zainicjować tę zmienną i następnie wykonuje wiele operacji długotrwałej na tych danych.

[!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]

Jeśli `lengthy_operation1`, `lengthy_operation2`, i `lengthy_operation3` funkcji nie należy modyfikować `MyDataType` zmiennej, te funkcje mogą być wykonywane równolegle, bez dodatkowych modyfikacji.

## <a name="example"></a>Przykład

Poniższy przykład modyfikuje poprzedni przykład do równoległego uruchamiania. `parallel_invoke` Algorytmu każde zadanie jest wykonywane równolegle i zwraca po zakończeniu wszystkich zadań.

[!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]

## <a name="example"></a>Przykład

Poniższy przykład pobiera *Iliad* przez Homer z gutenberg.org i wykonuje wiele operacji na pliku. Przykład najpierw szeregowo wykonuje te operacje, a następnie wykonuje te same operacje równoległe.

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

W tym przykładzie użyto `parallel_invoke` algorytm wywołać wiele funkcje, które działają na tym samym źródle danych. Możesz użyć `parallel_invoke` algorytm wywołać dowolny zbiór funkcji w sposób równoległy, nie tylko te, które działają w tych samych danych.

Ponieważ `parallel_invoke` algorytm wywołania każdej funkcji roboczych równolegle, jego wydajność jest ograniczone przez funkcję, która zajmuje najwięcej czasu na zakończenie (to znaczy, jeśli środowisko wykonawcze przetwarza każdej funkcji przy użyciu oddzielnych procesora). Jeśli w tym przykładzie wykonuje większej liczby zadań w sposób równoległy niż liczba dostępnych procesorów, wiele zadań można uruchomić na każdy procesor. W tym przypadku wydajności jest ograniczone przez grupy zadań, która zajmuje najwięcej czasu, aby zakończyć.

Bo w tym przykładzie trzy zadania w sposób równoległy, nie należy się spodziewać wydajność skalowania na komputerach, które mają więcej niż trzy procesory. W celu poprawy wydajności więcej można przerwać zadania najdłużej działających na mniejsze zadania i uruchamiania tych zadań w sposób równoległy.

Możesz użyć `parallel_invoke` algorytmu zamiast [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy, jeśli nie jest wymagana obsługa anulowania. Aby uzyskać przykład, który porównuje użycie `parallel_invoke` algorytmu i grupy zadań, zobacz [jak: Używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).

## <a name="compiling-the-code"></a>Kompilowanie kodu

Aby skompilować ten kod, skopiuj go a następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-word-mining.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc/MD/DUNICODE /D_AFXDLL równoległych word-mining.cpp**

## <a name="see-also"></a>Zobacz także

[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_invoke Function](reference/concurrency-namespace-functions.md#parallel_invoke)
