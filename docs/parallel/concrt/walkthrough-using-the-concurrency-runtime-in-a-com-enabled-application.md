---
title: 'Wskazówki: korzystanie ze współbieżności środowiska wykonawczego w aplikacji z możliwością korzystania z COM'
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, use with COM
- COM, use with the Concurrency Runtime
ms.assetid: a7c798b8-0fc8-4bee-972f-22ef158f7f48
ms.openlocfilehash: 227d06c74826b8936909b774d1a7e3a222ac8023
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50554937"
---
# <a name="walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application"></a>Wskazówki: korzystanie ze współbieżności środowiska wykonawczego w aplikacji z możliwością korzystania z COM

W tym dokumencie przedstawiono sposób korzystania ze środowiska uruchomieniowego współbieżności w aplikacji, która używa Component Object Model (COM).

## <a name="prerequisites"></a>Wymagania wstępne

Przed rozpoczęciem tego instruktażu, przeczytaj następujące dokumenty:

- [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)

- [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

- [Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)

Aby uzyskać więcej informacji na temat modelu COM, zobacz [składnik modelu COM](/windows/desktop/com/component-object-model--com--portal).

## <a name="managing-the-lifetime-of-the-com-library"></a>Zarządzanie okresem istnienia biblioteki COM

Mimo że korzystanie z modelu COM w środowisku uruchomieniowym współbieżności wykona te same zasady jako innego mechanizmu współbieżności, mogą pomóc poniższe wskazówki, możesz używać tych bibliotek razem skutecznie.

- Wątek musi wywołać [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) używa biblioteki COM.

- Wątek może wywołać `CoInitializeEx` wielokrotnie tak długo, jak zapewnia te same argumenty, aby każde wywołanie.

- Dla każdego wywołania `CoInitializeEx`, wątek musi także wywołać metodę [CoUninitialize](/windows/desktop/api/combaseapi/nf-combaseapi-couninitialize). Innymi słowy, wywołania `CoInitializeEx` i `CoUninitialize` musi być równoważony.

- Aby przełączyć się z typu apartment jeden wątek, wątek musi całkowicie bezpłatne biblioteki COM przed wywołaniem `CoInitializeEx` przy użyciu nowego wątkowości specyfikacji.

Inne zasady COM mają zastosowanie, korzystając z modelu COM w środowisku uruchomieniowym współbieżności. Na przykład aplikacja tworzy obiekt apartamentem jednowątkowym (przedziale STA) i kieruje ten obiekt do innego typu apartment muszą również zapewnić pętlę komunikatów do przetwarzania komunikatów przychodzących. Pamiętaj również, że przekazywanie obiektów między apartamentach może obniżyć wydajność.

### <a name="using-com-with-the-parallel-patterns-library"></a>Korzystając z modelu COM z biblioteką równoległych wzorców

Korzystając z modelu COM za pomocą składnika w równoległych wzorców biblioteki (PPL), na przykład grupa zadań lub algorytmu równoległego, wywołaj `CoInitializeEx` przed przy użyciu biblioteki COM podczas każdego zadania lub iteracji i wywołania `CoUninitialize` przed zakończeniem każdego zadania lub iteracji . Poniższy przykład pokazuje, jak zarządzać okresem istnienia biblioteki COM za pomocą [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu.

[!code-cpp[concrt-parallel-scripts#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_1.cpp)]

Upewnij się, że biblioteki COM poprawnie jest zwalniana, gdy algorytm zadania lub równolegle zostało anulowane lub zgłasza wyjątek, treść zadania. Aby zagwarantować, że zadanie wywołuje `CoUninitialize` przed kończy pracę, użyj `try-finally` bloku lub *inicjowania jest pozyskiwanie zasobów* wzorca (RAII). W poniższym przykładzie użyto `try-finally` bloku, aby zwolnić biblioteki COM, jeśli zadanie zakończy się lub zostało anulowane lub gdy wyjątek jest zgłaszany.

[!code-cpp[concrt-parallel-scripts#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_2.cpp)]

W poniższym przykładzie użyto wzór RAII w celu zdefiniowania `CCoInitializer` klasy, która zarządza czasem istnienia biblioteki COM w danym zakresie.

[!code-cpp[concrt-parallel-scripts#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_3.cpp)]

Możesz użyć `CCoInitializer` klasy automatycznie zwolnienie biblioteki COM, gdy zadanie kończy działanie w następujący sposób.

[!code-cpp[concrt-parallel-scripts#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_4.cpp)]

Aby uzyskać więcej informacji na temat anulowania w środowisku uruchomieniowym współbieżności: zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

### <a name="using-com-with-asynchronous-agents"></a>Korzystając z modelu COM z agentami asynchronicznymi

Korzystając z modelu COM z agentami asynchronicznymi, wywołaj `CoInitializeEx` przed skorzystaniem z biblioteki modelu COM w [concurrency::agent::run](reference/agent-class.md#run) metodę dla agenta. Następnie wywołaj `CoUninitialize` przed `run` metoda zwraca. Nie używaj procedury zarządzania COM w konstruktorze lub destruktorze Twojego agenta, a nie zastępują [concurrency::agent::start](reference/agent-class.md#start) lub [concurrency::agent:: gotowe](reference/agent-class.md#done) metody, ponieważ te metody są wywołuje się w innym wątku niż `run` metody.

W poniższym przykładzie pokazano klasę podstawowe agenta o nazwie `CCoAgent`, która zarządza biblioteki COM w `run` metody.

[!code-cpp[concrt-parallel-scripts#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_5.cpp)]

Pełny przykład znajduje się w dalszej części tego przewodnika.

### <a name="using-com-with-lightweight-tasks"></a>Korzystając z modelu COM z lekkimi zadaniami

Dokument [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md) opisuje rolę klasy zadania lekkie środowisko uruchomieniowe współbieżności. Za pomocą modelu COM lekkie zadanie tak samo jak dowolnej procedury wątku, który jest przekazywany do `CreateThread` funkcji w interfejsie API Windows. Jest to pokazane w poniższym przykładzie.

[!code-cpp[concrt-parallel-scripts#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_6.cpp)]

## <a name="an-example-of-a-com-enabled-application"></a>Przykład aplikacji z możliwością korzystania z COM

W tej sekcji przedstawiono kompletna aplikacja możliwością korzystania z COM, który używa `IScriptControl` interfejsu do uruchomienia skryptu, który oblicza n<sup>th</sup> Fibonacci numer. W tym przykładzie najpierw wywołuje skrypt z wątku głównego, a następnie używa PPL i agentów, aby wywoływać skrypt jednocześnie.

Należy wziąć pod uwagę Poniższa funkcja pomocnicza `RunScriptProcedure`, które wywołuje procedury `IScriptControl` obiektu.

[!code-cpp[concrt-parallel-scripts#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_7.cpp)]

`wmain` Funkcja tworzy `IScriptControl` obiektów, dodaje kod skryptu do niego, które oblicza n<sup>th</sup> Fibonacci numer, a następnie wywołania `RunScriptProcedure` funkcję, aby uruchomić ten skrypt.

[!code-cpp[concrt-parallel-scripts#8](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_8.cpp)]

### <a name="calling-the-script-from-the-ppl"></a>Wywoływanie skryptu z PPL

Poniższa funkcja `ParallelFibonacci`, używa [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorytm wywołanie skryptu w sposób równoległy. Ta funkcja używa `CCoInitializer` klasy w celu zarządzania okresem istnienia biblioteki COM podczas każdej iteracji tego zadania.

[!code-cpp[concrt-parallel-scripts#9](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_9.cpp)]

Aby użyć `ParallelFibonacci` funkcji z przykładem, Dodaj następujący kod przed `wmain` funkcja zwraca.

[!code-cpp[concrt-parallel-scripts#10](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_10.cpp)]

### <a name="calling-the-script-from-an-agent"></a>Wywoływanie skryptu z agenta

W poniższym przykładzie przedstawiono `FibonacciScriptAgent` klasy, która wywołuje procedurę skrypt, aby obliczyć n<sup>th</sup> Fibonacci numer. `FibonacciScriptAgent` Klasa używa komunikatów przekazywania, aby otrzymywać głównego programu wprowadzanie wartości do funkcji skryptu. `run` Metoda zarządza czasem istnienia biblioteki COM w całym zadania.

[!code-cpp[concrt-parallel-scripts#11](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_11.cpp)]

Poniższa funkcja `AgentFibonacci`, tworzy kilka `FibonacciScriptAgent` obiektów i używa komunikatu Przechodzenie do wysyłania kilka wprowadzanie wartości do tych obiektów.

[!code-cpp[concrt-parallel-scripts#12](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_12.cpp)]

Aby użyć `AgentFibonacci` funkcji z przykładem, Dodaj następujący kod przed `wmain` funkcja zwraca.

[!code-cpp[concrt-parallel-scripts#13](../../parallel/concrt/codesnippet/cpp/walkthrough-using-the-concurrency-runtime-in-a-com-enabled-application_13.cpp)]

### <a name="the-complete-example"></a>Kompletny przykład

Poniższy kod przedstawia kompletny przykład, która korzysta z algorytmów równoległych oraz agentów asynchronicznych aby wywołać procedurę skryptu, który oblicza Fibonacci liczb.

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

Kopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `parallel-scripts.cpp` , a następnie uruchom następujące polecenie w oknie wiersza polecenia programu Visual Studio.

**Cl.exe/ehsc/Link scripts.cpp równoległych ole32.lib**

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności — wskazówki](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)<br/>
[Obsługa wyjątków](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)

