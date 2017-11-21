---
title: "Porady: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling, converting from OpenMP to the Concurrency Runtime
- converting from OpenMP to the Concurrency Runtime, exception handling
ms.assetid: 03c28196-21ba-439e-8641-afab1c283e1a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: beac8ca095388428986569433f0461a505f2a7e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-convert-an-openmp-loop-that-uses-exception-handling-to-use-the-concurrency-runtime"></a>Porady: konwertowanie pętli OpenMP używającej obsługi wyjątków do korzystania ze współbieżności środowiska wykonawczego
W tym przykładzie pokazano, jak przekonwertować OpenMP [równoległych](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[dla](../../parallel/openmp/reference/for-openmp.md) pętli, które wykonuje obsługi wyjątków do użycia mechanizmu obsługi wyjątków współbieżności środowiska wykonawczego.  
  
 W OpenMP wyjątek zgłaszany w równoległego regionu należy przechwycony i obsługiwane w tym samym regionie, w tym samym wątku. Wyjątek specjalne równoległego regionu zostanie przechwycony przez program obsługi nieobsługiwanego wyjątku, który kończy proces domyślnie.  
  

 Współbieżność środowiska wykonawczego, gdy zgłoszenia wyjątku w treści funkcji pracy, który jest przekazywany do grupy zadań takich jak [concurrency::task_group](reference/task-group-class.md) lub [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiekt, lub równoległe algorytm, takich jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), środowisko uruchomieniowe przechowuje ten wyjątek i marshals go do kontekstu, która oczekuje na grupy zadań lub algorytmu, aby zakończyć. Dla grup zadań kontekst oczekiwania jest kontekstu, która wywołuje [concurrency::task_group::wait](reference/task-group-class.md#wait), [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and _wait](reference/task-group-class.md#run_and_wait), lub [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait). Równoległe algorytmu kontekst oczekiwania jest kontekstu, która wywołuje tego algorytmu. Środowisko uruchomieniowe również zatrzymuje wszystkie aktywne zadania, które znajdują się w grupie zadań, włącznie z zawartymi w grupach zadań podrzędnych i odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione.  


  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób obsługi wyjątków w OpenMP `parallel` regionu w wywołaniu `parallel_for`. `do_work` Funkcja wykonuje żądanie alokacji pamięci, który nie powiedzie się i dlatego zgłasza wyjątek typu [std::bad_alloc](../../standard-library/bad-alloc-class.md). W wersji używającej OpenMP wątku, który zgłasza wyjątek musi również catch go. Innymi słowy każdej iteracji pętli parallel OpenMP musi obsługiwać wyjątek. W wersji, która używa współbieżności środowiska wykonawczego wątku głównego połowy wyjątku zgłoszonego przez inny wątek.  
  
 [!code-cpp[concrt-openmp#3](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that uses-exception-handling_1.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
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
  
 W wersji w tym przykładzie, który używa OpenMP wyjątek występuje w i odbywa się przy każdej iteracji pętli. W wersji, która używa współbieżności środowiska wykonawczego, środowisko uruchomieniowe przechowuje wyjątek, zatrzymuje wszystkie aktywne zadania odrzuca wszystkie zadania, które nie zostały uruchomione i marshals wyjątek do kontekstu, która wywołuje `parallel_for`.  
  
 Jeśli potrzebujesz przerwanie wersji, która używa OpenMP po wystąpieniu wyjątku, można użyć Flaga wartości logicznej sygnalizują do innych iteracji pętli, że wystąpił błąd. Jak pokazano w przykładzie w temacie [porady: konwertowanie pętli OpenMP tego używa anulowanie do korzystania ze współbieżności środowiska wykonawczego](../../parallel/concrt/convert-an-openmp-loop-that-uses-cancellation.md), iteracji pętli kolejnych czy nic nie rób Jeśli flaga jest ustawiona. Z drugiej strony Jeśli potrzebujesz, że pętli, który korzysta ze współbieżności środowiska wykonawczego ma kontynuować działanie po wystąpieniu wyjątku, obsługi wyjątków w treści pętli równoległej sam.  
  
 Inne składniki ze współbieżności środowiska wykonawczego, takie jak agentów asynchronicznych i zadań lekkich transportu nie wyjątków. Zamiast tego nieobsługiwane wyjątki są przechwytywane przez program obsługi nieobsługiwanego wyjątku, który kończy proces domyślnie. Aby uzyskać więcej informacji na temat obsługi wyjątków, zobacz [obsługi wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).  
  
 Aby uzyskać więcej informacji na temat `parallel_for` i inne algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `concrt-omp-exceptions.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc/OpenMP concrt-omp — exceptions.cpp**  
  
## <a name="see-also"></a>Zobacz też  
 [Migrowanie z OpenMP do współbieżności środowiska wykonawczego](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)   
 [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

