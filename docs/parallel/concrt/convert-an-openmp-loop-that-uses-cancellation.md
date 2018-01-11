---
title: "Porady: konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, cancellation
- cancellation, converting from OpenMP to the Concurrency Runtime
ms.assetid: 4b0b3c33-bfa9-4e96-ae08-aef245a39cbb
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d3c4d37dfe5182e375e7581d6f5ef8188b922e5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-cancellation-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP stosującej anulowanie do korzystania ze współbieżności środowiska wykonawczego
Niektóre pętle równoległe nie wymagają wykonywane wszystkich iteracji. Algorytm wyszukiwania przez wartość można na przykład przerwanie po znalezieniu wartość. OpenMP nie udostępniają mechanizm break poza równoległej pętli. Jednak można użyć wartość logiczna lub flagę, aby włączyć iteracji pętli, aby wskazać, że rozwiązanie zostało znalezione. Współbieżność środowiska wykonawczego udostępnia funkcje umożliwiające jedno zadanie anulować inne zadania, które nie zostały jeszcze uruchomione.  
  
 W tym przykładzie pokazano, jak przekonwertować OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które nie są wymagane dla wszystkich iteracji, aby uruchomić do używać mechanizmu anulowania współbieżność środowiska wykonawczego.  
  
## <a name="example"></a>Przykład  

 W tym przykładzie użyto zarówno OpenMP, jak i współbieżności środowiska wykonawczego do wdrożenia równoległego wersji [std::any_of](../../standard-library/algorithm-functions.md#any_of) algorytmu. Wersja OpenMP — w tym przykładzie używa flagi do koordynowania wśród wszystkich iteracji pętli równoległej spełnienia warunku. W wersji, który korzysta ze współbieżności środowiska wykonawczego [concurrency::structured_task_group::cancel](reference/structured-task-group-class.md#cancel) metodę, aby zatrzymać operację ogólną, gdy warunek jest spełniony.  

  
 [!code-cpp[concrt-openmp#2](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-cancellation_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
Using OpenMP...  
9114046 is in the array.  
Using the Concurrency Runtime...  
9114046 is in the array.  
```  
  
 W wersji tego używa OpenMP wszystkich iteracji pętli wykonać, nawet wtedy, gdy flaga jest ustawiona. Ponadto gdyby zostały wszystkie zadania podrzędne zadania, flagę również musi być dostępne dla tych zadań podrzędnych do komunikowania się anulowania. Współbieżność środowiska wykonawczego gdy grupy zadanie zostało anulowane, środowisko uruchomieniowe anuluje całe drzewo pracy, w tym zadania podrzędne. [Concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorytm używa zadań do wykonywania pracy. W związku z tym gdy jeden iteracji pętli anuluje zadanie głównego, całe drzewo obliczeń również została anulowana. Gdy drzewa pracy zostało anulowane, środowisko uruchomieniowe nie uruchamia się nowe zadania. Środowisko uruchomieniowe umożliwia jednak programowi zadania, które zostało już rozpoczęte, aby zakończyć. W związku z tym w odniesieniu `parallel_for_each` algorytmu, iteracji pętli active można wyczyścić swoje zasoby.  
  
 W obu wersjach w tym przykładzie Jeśli tablica zawiera więcej niż jedną kopię wartość do wyszukania, przejść przez wiele iteracji pętli można każdego jednocześnie ustawić wynik i Anuluj operację ogólną. Możesz użyć pierwotny synchronizacji, takie jak sekcja krytyczna, jeżeli problem wymaga tylko jednego zadania wykonuje pracę, gdy warunek jest spełniony.  
  
 Można również użyć obsługi wyjątków, aby anulować zadania, które używają PPL. Aby uzyskać więcej informacji na temat anulowania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
 Aby uzyskać więcej informacji na temat `parallel_for_each` i inne algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-parallel-any-of.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc/OpenMP concrt-omp — równoległe any-of.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

