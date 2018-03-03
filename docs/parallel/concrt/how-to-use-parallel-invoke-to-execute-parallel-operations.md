---
title: "Porady: Korzystanie z parallel_invoke do przeprowadzania operacji równoległych | Dokumentacja firmy Microsoft"
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
- parallel_invoke function, example
- calling multiple functions in parallel [Concurrency Runtime]
ms.assetid: a6aea69b-d647-4b7e-bf3b-e6a6a9880072
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cefabd21e04c4c3cc39934de111fe94151317ca5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Porady: korzystanie z parallel_invoke do przeprowadzania operacji równoległych
Ten przykład przedstawia sposób użycia [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu, aby poprawić wydajność program, który wykonuje wiele operacji na udostępnione źródło danych. Ponieważ nie ma operacji zmodyfikować źródło, mogą być wykonywane równolegle w sposób proste.  

  
## <a name="example"></a>Przykład  
 Należy wziąć pod uwagę Poniższy przykładowy kod, który tworzy zmienną typu `MyDataType`, wywołuje funkcję zainicjować tej zmiennej, a następnie oblicza wiele długich operacji na danych.  
  
 [!code-cpp[concrt-parallel-word-mining#1](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_1.cpp)]  
  
 Jeśli `lengthy_operation1`, `lengthy_operation2`, i `lengthy_operation3` funkcji nie należy modyfikować `MyDataType` zmiennej, te funkcje mogą być wykonywane równolegle bez dodatkowych modyfikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład modyfikuje poprzedni przykład, aby uruchomić równolegle. `parallel_invoke` Algorytmu wykonuje każde zadanie równoległe i zwraca po zakończeniu wszystkich zadań.  
  
 [!code-cpp[concrt-parallel-word-mining#2](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_2.cpp)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera *Iliad* przez Homer z gutenberg.org i wykonuje wiele operacji dla tego pliku. Przykład najpierw szeregowo wykonuje te operacje, a następnie wykonuje te same operacje równoległe.  
  
 [!code-cpp[concrt-parallel-word-mining#3](../../parallel/concrt/codesnippet/cpp/how-to-use-parallel-invoke-to-execute-parallel-operations_3.cpp)]  
  
 W tym przykładzie tworzy następujące przykładowe dane wyjściowe.  
  
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
  
 W tym przykładzie użyto `parallel_invoke` algorytmu do wywołania wiele funkcji działań na tym samym źródle danych. Można użyć `parallel_invoke` algorytmu do wywołania dowolny zbiór funkcji równolegle, nie tylko te, które działają na tych samych danych.  
  
 Ponieważ `parallel_invoke` algorytm wywołuje funkcję każdej pracy równolegle, jego wydajność jest ograniczone przez funkcję, która ma najdłuższy czas do zakończenia (Jeśli środowisko uruchomieniowe przetwarza każdej funkcji na oddzielnych procesora). Jeśli w tym przykładzie przeprowadza więcej zadań równolegle niż liczba dostępnych procesorów, wiele zadań można uruchamiać na każdy procesor. W takim przypadku wydajności jest ograniczone przez grupy zadań wykorzystującej najdłużej, aby zakończyć.  
  
 Ponieważ w tym przykładzie przeprowadza trzy zadania równolegle, nie spodziewać wydajności można skalować na komputerach wyposażonych w procesory więcej niż trzy. Aby zwiększyć wydajność więcej, można przerwać zadania najdłużej działających na mniejsze zadania i równolegle tych zadań.  
  
 Można użyć `parallel_invoke` algorytmu zamiast [concurrency::task_group](reference/task-group-class.md) i [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) klasy, jeśli nie jest wymagana obsługa anulowania. Na przykład, który porównuje użycie `parallel_invoke` algorytmu w porównaniu z grupy zadań, zobacz [porady: używanie parallel_invoke do napisania procedury sortowania równoległego](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby skompilować kod, skopiuj go i następnie wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-word-mining.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc / / MD/DUNICODE /D_AFXDLL równoległe word-mining.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [parallel_invoke — funkcja](reference/concurrency-namespace-functions.md#parallel_invoke)


