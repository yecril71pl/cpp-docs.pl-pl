---
title: 'Wskazówki: korzystanie ze współbieżności środowiska wykonawczego w aplikacji z możliwością korzystania z COM'
ms.date: 04/25/2019
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: faa072ab2b5973ace0f0ca138dcedffa56044213
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140624"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Wskazówki: korzystanie ze współbieżności środowiska wykonawczego w aplikacji z możliwością korzystania z COM

W tym dokumencie przedstawiono sposób użycia środowisko uruchomieniowe współbieżności w aplikacji, która używa Component Object Model (COM).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu zapoznaj się z następującymi dokumentami:

- [Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

Aby uzyskać więcej informacji na temat modelu COM, zobacz [Component Object Model (com)](/windows/win32/com/component-object-model--com--portal).

## <a name="managing-the-lifetime-of-the-com-library"></a>Zarządzanie okresem istnienia biblioteki COM

Chociaż użycie modelu COM z środowisko uruchomieniowe współbieżności jest zgodne z takimi samymi zasadami jak każdy inny mechanizm współbieżności, następujące wskazówki mogą pomóc w efektywnym użyciu tych bibliotek.

- Wątek musi wywołać [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) przed użyciem biblioteki com.

- Wątek może wywoływać `CoInitializeEx` wiele razy, dopóki zawiera te same argumenty dla każdego wywołania.

- Dla każdego wywołania `CoInitializeEx`wątek musi również wywołać [CoUninitialize](/windows/win32/api/combaseapi/nf-combaseapi-couninitialize). Innymi słowy, wywołania `CoInitializeEx` i `CoUninitialize` muszą być zrównoważone.

- Aby przełączyć się z jednego wątku do innego, wątek musi całkowicie zwolnić bibliotekę COM przed wywołaniem `CoInitializeEx` z nową specyfikacją wątkowości.

Inne zasady COM stosują się w przypadku używania modelu COM z środowisko uruchomieniowe współbieżności. Na przykład aplikacja, która tworzy obiekt w jednowątkowym apartamentie (STA) i kierujący do tego obiektu, musi również udostępnić pętlę komunikatów, aby przetwarzać komunikaty przychodzące. Pamiętaj również, że kierowanie obiektów między apartamentach może obniżyć wydajność.

### <a name="using-com-with-the-parallel-patterns-library"></a>Korzystając z modelu COM z biblioteką równoległych wzorców

Jeśli używasz modelu COM ze składnikiem w bibliotece równoległych wzorców (PPL), na przykład grupy zadań lub algorytmu równoległego, wywołaj `CoInitializeEx` przed użyciem biblioteki COM podczas każdego zadania lub iteracji, a następnie Wywołaj `CoUninitialize` przed ukończeniem każdego zadania lub iteracji. Poniższy przykład pokazuje, jak zarządzać okresem istnienia biblioteki COM przy użyciu obiektu [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) .

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Należy upewnić się, że biblioteka COM została prawidłowo zwolniona, gdy zadanie lub algorytm równoległy został anulowany, lub gdy treść zadania zgłasza wyjątek. Aby zagwarantować, że zadanie wywołuje `CoUninitialize` przed zakończeniem, użyj bloku `try-finally` lub wzorca *pozyskiwania zasobów* (RAII). Poniższy przykład używa bloku `try-finally`, aby zwolnić bibliotekę COM, gdy zadanie zostanie ukończone lub zostało anulowane, lub gdy zostanie zgłoszony wyjątek.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

W poniższym przykładzie używany jest wzorzec RAII do definiowania klasy `CCoInitializer`, która zarządza okresem istnienia biblioteki COM w danym zakresie.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

Korzystając z klasy `CCoInitializer`, można automatycznie zwolnić bibliotekę COM po zakończeniu zadania w następujący sposób.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Aby uzyskać więcej informacji na temat anulowania w środowisko uruchomieniowe współbieżności, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Korzystając z modelu COM z agentami asynchronicznymi

Jeśli używasz modelu COM z agentami asynchronicznymi, wywołaj `CoInitializeEx` przed użyciem biblioteki COM w metodzie [concurrency:: Agent:: Run](reference/agent-class.md#run) dla agenta. Następnie Wywołaj `CoUninitialize` przed zwróceniem metody `run`. Nie należy używać procedur zarządzania modelu COM w konstruktorze lub destruktorze agenta ani nie przesłaniać [concurrency:: Agent:: Start](reference/agent-class.md#start) ani [concurrency:: Agent::d jedną](reference/agent-class.md#done) metodę, ponieważ te metody są wywoływane z innego wątku niż Metoda `run`.

Poniższy przykład przedstawia podstawową klasę agenta o nazwie `CCoAgent`, która zarządza biblioteką COM w metodzie `run`.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Pełny przykład jest dostępny w dalszej części tego przewodnika.

### <a name="using-com-with-lightweight-tasks"></a>Korzystając z modelu COM z lekkimi zadaniami

Dokument [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md) opisuje rolę uproszczonych zadań w środowisko uruchomieniowe współbieżności. Możesz użyć modelu COM z uproszczonym zadaniem tak samo jak w przypadku każdej procedury wątku przekazanej do funkcji `CreateThread` w interfejsie API systemu Windows. Pokazano to w poniższym przykładzie.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Przykład aplikacji z możliwością korzystania z COM

W tej sekcji przedstawiono kompletną aplikację obsługującą COM, która używa interfejsu `IScriptControl` do wykonywania skryptu, który oblicza n-<sup>ty</sup> numer Fibonacci. Ten przykład najpierw wywołuje skrypt z wątku głównego, a następnie używa PPL i agentów do wywołania skryptu współbieżnie.

Rozważmy następującą funkcję pomocnika, `RunScriptProcedure`, która wywołuje procedurę w obiekcie `IScriptControl`.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

Funkcja `wmain` tworzy obiekt `IScriptControl`, dodaje do niego kod skryptu, który<sup>oblicza n numer</sup> Fibonacci, a następnie wywołuje funkcję `RunScriptProcedure`, aby uruchomić ten skrypt.

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Wywoływanie skryptu z PPL

Poniższa funkcja, `ParallelFibonacci`używa algorytmu [współbieżności:p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) do wywołania skryptu równolegle. Ta funkcja używa klasy `CCoInitializer` do zarządzania okresem istnienia biblioteki COM podczas każdej iteracji zadania.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Aby użyć funkcji `ParallelFibonacci` z przykładem, Dodaj następujący kod przed zwróceniem funkcji `wmain`.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Wywoływanie skryptu z agenta

Poniższy przykład pokazuje klasę `FibonacciScriptAgent`, która wywołuje procedurę skryptu, aby obliczyć n-<sup>ty</sup> numer Fibonacci. Klasa `FibonacciScriptAgent` używa przekazywania komunikatów do odbioru, z głównego programu, wartości wejściowych do funkcji skryptu. Metoda `run` zarządza okresem istnienia biblioteki COM w ramach zadania.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

Następująca funkcja, `AgentFibonacci`, tworzy kilka obiektów `FibonacciScriptAgent` i używa przekazywania komunikatów do wysyłania kilku wartości wejściowych do tych obiektów.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Aby użyć funkcji `AgentFibonacci` z przykładem, Dodaj następujący kod przed zwróceniem funkcji `wmain`.

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>Kompletny przykład

Poniższy kod przedstawia kompletny przykład, który używa algorytmów równoległych i agentów asynchronicznych do wywoływania procedury skryptu, która oblicza liczby Fibonacci.

[!code-cpp[concrt-parallel-scripts#14](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_14.cpp)]

Przykład generuje następujące przykładowe dane wyjściowe.

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

Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-scripts.cpp` a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

> **CL. exe/EHsc Parallel-scripts. cpp/link ole32. lib**

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)
