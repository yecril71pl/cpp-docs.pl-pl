---
title: 'Wskazówki: Korzystanie ze współbieżności środowiska wykonawczego w aplikacji z obsługą COM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1fd9f665f77ca5ae5311b034ee7afef6241ac489
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692551"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Wskazówki: korzystanie ze współbieżności środowiska wykonawczego w aplikacji z możliwością korzystania z COM
Ten dokument przedstawia sposób korzystania ze współbieżności środowiska wykonawczego w aplikacji korzystającej z modelu obiektu składników (COM).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Przeczytaj następujące dokumenty przed skorzystaniem z tego przewodnika:  
  
- [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)  
  
- [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)  
  
- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)  
  
- [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)  
  
 Aby uzyskać więcej informacji na temat modelu COM, zobacz [składnik modelu COM](http://msdn.microsoft.com/library/windows/desktop/ms680573).  
  
## <a name="managing-the-lifetime-of-the-com-library"></a>Zarządzanie okresem istnienia biblioteki COM  
 Mimo że korzystanie z modelu COM z współbieżności środowiska wykonawczego wykonuje te same zasady jako inny mechanizm współbieżności, mogą pomóc poniższe wskazówki można wykorzystywać te biblioteki razem.  
  
-   Wątek należy wywołać [funkcja CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) przed użyciem biblioteki COM.  
  
-   Wątek może wywołać `CoInitializeEx` wiele razy, jak długo zapewnia te same argumenty co wywołanie.  
  
-   Dla każdego wywołania `CoInitializeEx`, wątek należy także wywołać [CoUninitialize](http://msdn.microsoft.com/library/windows/desktop/ms688715). Innymi słowy, wywołań `CoInitializeEx` i `CoUninitialize` musi uwzględniać.  
  
-   Aby przełączyć się z apartamentu jeden wątek, wątek należy całkowicie zwolnić biblioteki COM przed wywołaniem `CoInitializeEx` z nowym wątkowość specyfikacji.  
  
 Inne zasady COM stosowane, gdy używasz modelu COM z współbieżności środowiska wykonawczego. Na przykład aplikacja tworzy obiekt jednowątkowego apartamentu (STA) i marshals tego obiektu do innego apartamentu należy również podać Pętla wiadomości do przetwarzania komunikatów przychodzących. Również należy pamiętać, że przekazywanie obiektów między apartamentach może obniżyć wydajność.  
  
### <a name="using-com-with-the-parallel-patterns-library"></a>Korzystając z modelu COM z biblioteką równoległych wzorców  
 Korzystając z modelu COM ze składnikiem w równoległych wzorców biblioteki (PLL), na przykład grupy zadań lub równoległych algorytm wywołania `CoInitializeEx` przed skorzystaniem z biblioteki modelu COM podczas każdego zadania lub iteracji i wywołanie `CoUninitialize` przed zakończeniem każdego zadania lub iteracji . Poniższy przykład pokazuje, jak zarządzać okresem istnienia biblioteki COM z [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu.  
  
 [!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]  
  
 Należy się upewnić, że biblioteki COM poprawnie zwolniony po anulowaniu algorytm zadań lub równolegle, lub gdy treść zadania zgłasza wyjątek. Aby zagwarantować, że zadanie wywołuje `CoUninitialize` przed kończy pracę, użyj `try-finally` bloku lub *inicjowania jest nabywania zasobów* wzorca (RAII). W poniższym przykładzie użyto `try-finally` bloku zwolnienia biblioteki modelu COM, gdy zadanie zostało anulowane lub zakończeniem lub gdy jest zgłaszany wyjątek.  
  
 [!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]  
  
 Poniższy przykład korzysta ze wzorca RAII do definiowania `CCoInitializer` klasy, która zarządza czasem istnienia biblioteki modelu COM w danym zakresie.  
  
 [!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]  
  
 Można użyć `CCoInitializer` klasy automatycznie zwolnienia biblioteki modelu COM, gdy zadanie kończy w następujący sposób.  
  
 [!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]  
  
 Aby uzyskać więcej informacji na temat anulowania współbieżność środowiska wykonawczego, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  
  
### <a name="using-com-with-asynchronous-agents"></a>Korzystając z modelu COM z agentami asynchronicznymi  

 Korzystając z agentów asynchronicznych modelu COM, wywołanie `CoInitializeEx` przed skorzystaniem z biblioteki modelu COM w [concurrency::agent::run](reference/agent-class.md#run) metodę dla agenta. Następnie wywołaj `CoUninitialize` przed `run` zwraca metody. Nie używaj procedury zarządzania COM w konstruktorze lub destruktorze agenta, a nie zastępują [concurrency::agent::start](reference/agent-class.md#start) lub [concurrency::agent:: gotowe](reference/agent-class.md#done) metody ponieważ te metody są wywoływana z wątku innego niż `run` metody.  

  
 W poniższym przykładzie przedstawiono klasę podstawowe agenta o nazwie `CCoAgent`, która zarządza biblioteki modelu COM w `run` metody.  
  
 [!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]  
  
 Pełny przykład znajduje się w dalszej części tego przewodnika.  
  
### <a name="using-com-with-lightweight-tasks"></a>Korzystając z modelu COM z lekkimi zadaniami  
 Dokument [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md) zawiera opis roli zadań lekkich współbieżność środowiska wykonawczego. Za pomocą modelu COM lekkie zadań tak samo jak dowolnej przekazać do procedury wątku `CreateThread` funkcji interfejsu API systemu Windows. Przedstawiono to w poniższym przykładzie.  
  
 [!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]  
  
## <a name="an-example-of-a-com-enabled-application"></a>Przykład aplikacji z możliwością korzystania z COM  
 W tej sekcji przedstawiono kompletna aplikacja z obsługą COM, który używa `IScriptControl` interfejs do uruchomienia skryptu, który oblicza n<sup>th</sup> Fibonacci numer. W tym przykładzie najpierw wywołuje skrypt z wątku głównego, a następnie używa PPL i agentów równocześnie wywołać skrypt.  
  
 Należy wziąć pod uwagę następujące funkcji pomocnika, `RunScriptProcedure`, który wywołuje procedurę z `IScriptControl` obiektu.  
  
 [!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]  
  
 `wmain` Funkcja tworzy `IScriptControl` obiektów, dodaje kod skryptu do niej, który oblicza n<sup>th</sup> Fibonacci numer, a następnie wywołania `RunScriptProcedure` funkcji, aby uruchomić ten skrypt.  
  
 [!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]  
  
### <a name="calling-the-script-from-the-ppl"></a>Wywoływanie skryptu z PPL  

 Następująca funkcja `ParallelFibonacci`, używa [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm wywołać skrypt równolegle. Funkcja ta używa `CCoInitializer` klasę, aby zarządzać okres istnienia biblioteki modelu COM w każdej iteracji zadania.  

  
 [!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]  
  
 Aby użyć `ParallelFibonacci` działać z przykładem, Dodaj następujący kod przed `wmain` funkcja zwraca.  
  
 [!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]  
  
### <a name="calling-the-script-from-an-agent"></a>Wywoływanie skryptu z agenta  
 W poniższym przykładzie przedstawiono `FibonacciScriptAgent` klasy, która wywołuje procedurę skryptu do obliczenia n<sup>th</sup> Fibonacci numer. `FibonacciScriptAgent` Klasy używa wiadomości, przekazywanie do odbierania z głównego programu wprowadzanie wartości funkcji skryptu. `run` Metody zarządza czasem istnienia biblioteki modelu COM w całym zadania.  
  
 [!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]  
  
 Następująca funkcja `AgentFibonacci`, tworzy kilka `FibonacciScriptAgent` obiekty i używa wiadomości, przekazywanie do wysyłania kilka wprowadzanie wartości do tych obiektów.  
  
 [!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]  
  
 Aby użyć `AgentFibonacci` działać z przykładem, Dodaj następujący kod przed `wmain` funkcja zwraca.  
  
 [!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]  
  
### <a name="the-complete-example"></a>Kompletny przykład  
 Poniższy kod przedstawia pełny przykład w celu wywoływanie procedury skryptu, który oblicza numery Fibonacci wykorzystuje algorytmy równoległe i agentów asynchronicznych.  
  
 [!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]  
  
 Przykład tworzy następujące przykładowe dane wyjściowe.  
  
```Output  
Main Thread:  
fib(15) = 610  
 
Parallel Fibonacci:  
fib(15) = 610  
fib(10) = 55  
fib(16) = 987  
fib(18) = 2584  
fib(11) = 89  
fib(17) = 1597  
fib(19) = 4181  
fib(12) = 144  
fib(13) = 233  
fib(14) = 377  
 
Agent Fibonacci:  
fib(30) = 832040  
fib(22) = 17711  
fib(10) = 55  
fib(12) = 144  
```  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-scripts.cpp` , a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 **Cl.exe/ehsc/Link równoległe scripts.cpp ole32.lib**  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)   
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)   
 [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)

