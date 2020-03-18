---
title: Obsługa wyjątków we współbieżności środowiska wykonawczego
ms.date: 11/04/2016
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
ms.openlocfilehash: 4c7fee363da023b9252471a35aaecd262a55f17c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422249"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Obsługa wyjątków we współbieżności środowiska wykonawczego

Środowisko uruchomieniowe współbieżności używa C++ obsługi wyjątków do komunikacji wielu rodzajów błędów. Te błędy obejmują nieprawidłowe użycie środowiska uruchomieniowego, błędy środowiska uruchomieniowego, takie jak niepowodzenie uzyskania zasobu i błędy występujące w funkcjach roboczych dostarczanych do zadań i grup zadań. Gdy zadanie lub grupa zadań zgłasza wyjątek, środowisko uruchomieniowe utrzymuje ten wyjątek i kierowanie go do kontekstu, który czeka na zakończenie zadania lub grupy zadań. W przypadku składników, takich jak uproszczone zadania i agenci, środowisko uruchomieniowe nie zarządza wyjątkami. W takich przypadkach należy zaimplementować własny mechanizm obsługi wyjątków. W tym temacie opisano, jak środowisko uruchomieniowe obsługuje wyjątki, które są zgłaszane przez zadania, grupy zadań, uproszczone zadania i agenci asynchroniczni oraz jak odpowiadać na wyjątki w aplikacjach.

## <a name="key-points"></a>Kwestie kluczowe

- Gdy zadanie lub grupa zadań zgłasza wyjątek, środowisko uruchomieniowe utrzymuje ten wyjątek i kierowanie go do kontekstu, który czeka na zakończenie zadania lub grupy zadań.

- Gdy to możliwe, należy ująć każde wywołanie metody [concurrency:: Task:: Get](reference/task-class.md#get) i [concurrency:: Task:: wait](reference/task-class.md#wait) z `try`/`catch` Block, aby obsługiwały błędy, z których można wykonać odzyskiwanie. Środowisko uruchomieniowe kończy działanie aplikacji, jeśli zadanie zgłosi wyjątek, a ten wyjątek nie jest przechwytywany przez zadanie, jedną z jej kontynuacji lub główną aplikację.

- Kontynuacja oparta na zadaniach zawsze jest uruchamiana; nie ma znaczenia, czy zadanie poprzedzające zostało ukończone pomyślnie, wywołało wyjątek lub zostało anulowane. Kontynuacja oparta na wartości nie działa, jeśli zadanie poprzedzające zostanie wyrzucane lub anulowane.

- Ponieważ kontynuacje oparte na zadaniach są zawsze uruchamiane, należy rozważyć, czy należy dodać kontynuację opartą na zadaniach na końcu łańcucha kontynuacji. Może to pomóc zagwarantować, że kod będzie obserwować wszystkie wyjątki.

- Środowisko uruchomieniowe zgłasza [współbieżność:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) w przypadku wywołania [concurrency:: Task:: Get](reference/task-class.md#get) , a zadanie zostało anulowane.

- Środowisko uruchomieniowe nie zarządza wyjątkami dla uproszczonych zadań i agentów.

## <a name="top"></a>W tym dokumencie

- [Zadania i kontynuacje](#tasks)

- [Grupy zadań i algorytmy równoległe](#task_groups)

- [Wyjątki zgłoszone przez środowisko uruchomieniowe](#runtime)

- [Wiele wyjątków](#multiple)

- [Anulowanie](#cancellation)

- [Zadania lekkie](#lwts)

- [Agenci asynchroniczni](#agents)

## <a name="tasks"></a>Zadania i kontynuacje

W tej sekcji opisano, jak środowisko uruchomieniowe obsługuje wyjątki, które są zgłaszane przez [współbieżne:: Task](../../parallel/concrt/reference/task-class.md) Objects i ich kontynuacje. Aby uzyskać więcej informacji na temat zadania i modelu kontynuacji, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Gdy zgłaszasz wyjątek w treści funkcji służbowej przekazanej do obiektu `task`, środowisko uruchomieniowe przechowuje ten wyjątek i przekazuje go do kontekstu, który wywołuje [concurrency:: Task:: Get](reference/task-class.md#get) lub [concurrency:: Task:: wait](reference/task-class.md#wait). [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md) dokumentu zawiera opis kontynuacji opartych na zadaniach i wartościach, ale podsumowujących, kontynuacja oparta na wartościach przyjmuje parametr typu `T`, a kontynuacja oparta na zadaniach przyjmuje parametr typu `task<T>`. Jeśli zadanie, które zgłosi, ma co najmniej jedną kontynuację opartą na wartościach, te kontynuacje nie są zaplanowane do uruchomienia. Poniższy przykład ilustruje to zachowanie:

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Kontynuacja oparta na zadaniach umożliwia obsługę dowolnego wyjątku, który jest generowany przez zadanie poprzedzające. Kontynuacja oparta na zadaniach zawsze jest uruchamiana; nie ma znaczenia, czy zadanie zostało ukończone pomyślnie, wywołało wyjątek lub zostało anulowane. Gdy zadanie zgłosi wyjątek, jego kontynuacje oparte na zadaniach są zaplanowane do uruchomienia. Poniższy przykład pokazuje zadanie, które zawsze zgłasza. Zadanie ma dwie kontynuacje; Jedna z nich jest oparta na wartości, a druga — oparta na zadaniach. Wyjątek oparty na zadaniach jest zawsze uruchamiany i w związku z tym może przechwytywać wyjątek, który jest generowany przez zadanie poprzedzające. Gdy przykład czeka na zakończenie obu kontynuacji, wyjątek jest zgłaszany ponownie, ponieważ wyjątek zadania jest zawsze generowany w przypadku wywołania `task::get` lub `task::wait`.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Zalecamy używanie kontynuacji opartych na zadaniach do przechwytywania wyjątków, które można obsłużyć. Ponieważ kontynuacje oparte na zadaniach są zawsze uruchamiane, należy rozważyć, czy należy dodać kontynuację opartą na zadaniach na końcu łańcucha kontynuacji. Może to pomóc zagwarantować, że kod będzie obserwować wszystkie wyjątki. Poniższy przykład przedstawia podstawowy łańcuch kontynuacji oparty na wartości. Trzecie zadanie w łańcuchu zgłasza i dlatego wszelkie kontynuacje oparte na wartościach, które po nim nie są uruchamiane. Ostatnia kontynuacja jest jednak oparta na zadaniach i dlatego jest zawsze wykonywana. Ta ostatnia kontynuacja obsługuje wyjątek, który jest generowany przez trzecie zadanie.

Zalecamy przechwycenie najbardziej konkretnych wyjątków. Możesz pominąć końcową kontynuację opartą na zadaniach, jeśli nie masz określonych wyjątków do przechwycenia. Każdy wyjątek pozostanie nieobsłużony i będzie mógł zakończyć działanie aplikacji.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
> Można użyć metody [concurrency:: task_completion_event:: set_exception](../../parallel/concrt/reference/task-completion-event-class.md) , aby skojarzyć wyjątek z zdarzeniem ukończenia zadania. [Równoległe zadanie](../../parallel/concrt/task-parallelism-concurrency-runtime.md) dokumentu zawiera bardziej szczegółowe informacje o klasie [concurrency:: task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) .

[concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) jest ważnym typem wyjątku środowiska uruchomieniowego, który odnosi się do `task`. Środowisko uruchomieniowe zgłasza `task_canceled` po wywołaniu `task::get`, a zadanie zostało anulowane. (Odwrotnie, `task::wait` zwraca [task_status:: anulowane](reference/concurrency-namespace-enums.md#task_group_status) i nie throw). Możesz przechwytywać i obsługiwać ten wyjątek z kontynuacji opartej na zadaniach lub podczas wywoływania `task::get`. Aby uzyskać więcej informacji o anulowaniu zadania, zobacz [Anulowanie w PPL](cancellation-in-the-ppl.md).

> [!CAUTION]
> Nigdy nie Generuj `task_canceled` w kodzie. W zamian wywołaj metodę [concurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) .

Środowisko uruchomieniowe kończy działanie aplikacji, jeśli zadanie zgłosi wyjątek, a ten wyjątek nie jest przechwytywany przez zadanie, jedną z jej kontynuacji lub główną aplikację. Jeśli aplikacja ulegnie awarii, można skonfigurować program Visual Studio do przerwania C++ , gdy zostaną zgłoszone wyjątki. Po zdiagnozowaniu lokalizacji nieobsłużonego wyjątku Użyj kontynuacji opartej na zadaniach, aby go obsłużyć.

W sekcji [wyjątki zgłoszone przez środowisko uruchomieniowe](#runtime) w tym dokumencie opisano sposób pracy z wyjątkami w czasie wykonywania.

[[Top](#top)]

## <a name="task_groups"></a>Grupy zadań i algorytmy równoległe

W tej sekcji opisano, jak środowisko uruchomieniowe obsługuje wyjątki, które są zgłaszane przez grupy zadań. Ta sekcja ma zastosowanie również do algorytmów równoległych, takich jak [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for), ponieważ te algorytmy są kompilowane w grupach zadań.

> [!CAUTION]
> Upewnij się, że rozumiesz wpływ wyjątków na zadania zależne. Aby zapoznać się z zalecanymi praktykami dotyczącymi używania wyjątków z zadaniami lub algorytmami równoległymi, zobacz sekcję [Informacje o sposobie anulowania i obsługi wyjątków, które mają wpływ na niszczenie obiektów](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) w najlepszych rozwiązaniach w temacie Biblioteka wzorców równoległych.

Aby uzyskać więcej informacji na temat grup zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji na temat algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

W przypadku zgłaszania wyjątku w treści funkcji służbowej przekazywanej do obiektu [concurrency:: task_group](reference/task-group-class.md) lub [concurrency:: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , środowisko uruchomieniowe przechowuje ten wyjątek i przekazuje go do kontekstu, który wywołuje [współbieżność:: task_group:: wait](reference/task-group-class.md#wait), [concurrency:: structured_task_group:: wait](reference/structured-task-group-class.md#wait), [concurrency:: task_group:: run_and_wait](reference/task-group-class.md#run_and_wait)lub [concurrency:: structured_task_group:: run_and_wait](reference/structured-task-group-class.md#run_and_wait). Środowisko uruchomieniowe przerywa również wszystkie aktywne zadania, które znajdują się w grupie zadań (w tym w podrzędnych grupach zadań) i odrzuca zadania, które nie zostały jeszcze uruchomione.

Poniższy przykład pokazuje podstawową strukturę funkcji służbowej, która zgłasza wyjątek. W przykładzie zastosowano obiekt `task_group`, aby drukować wartości dwóch obiektów `point` równolegle. Funkcja pracy `print_point` drukuje wartości obiektu `point` do konsoli. Funkcja Work zgłasza wyjątek, jeśli wartość wejściowa jest `NULL`. Środowisko uruchomieniowe przechowuje ten wyjątek i kierowanie go do kontekstu, który wywołuje `task_group::wait`.

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Aby zapoznać się z kompletnym przykładem korzystającym z obsługi wyjątków w grupie zadań, zobacz [How to: use Exception obsługi wyjątków, aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Top](#top)]

## <a name="runtime"></a>Wyjątki zgłoszone przez środowisko uruchomieniowe

Wyjątek może wynikać z wywołania środowiska uruchomieniowego. Większość typów wyjątków, z wyjątkiem [concurrency:: task_canceled](../../parallel/concrt/reference/task-canceled-class.md) i [concurrency:: operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), wskazuje na błąd programowania. Te błędy są zwykle nieodwracalne i dlatego nie powinny być przechwytywane ani obsługiwane przez kod aplikacji. Zaleca się, aby przechwytywać i obsługiwać nieodwracalne błędy w kodzie aplikacji, gdy konieczne jest zdiagnozowanie błędów programistycznych. Jednak zrozumienie typów wyjątków, które są zdefiniowane przez środowisko uruchomieniowe, może ułatwić zdiagnozowanie błędów programistycznych.

Mechanizm obsługi wyjątków jest taki sam dla wyjątków, które są zgłaszane przez środowisko uruchomieniowe jako wyjątki, które są zgłaszane przez funkcje pracy. Na przykład funkcja [concurrency:: Receive](reference/concurrency-namespace-functions.md#receive) zwraca `operation_timed_out`, gdy nie otrzyma komunikatu w określonym przedziale czasu. Jeśli `receive` zgłasza wyjątek w funkcji służbowej przekazanej do grupy zadań, środowisko uruchomieniowe przechowuje ten wyjątek i przekazuje go do kontekstu, który wywołuje `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`lub `structured_task_group::run_and_wait`.

W poniższym przykładzie zastosowano algorytm [concurrency::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) w celu równoległego uruchamiania dwóch zadań. Pierwsze zadanie czeka pięć sekund, a następnie wysyła komunikat do buforu komunikatów. Drugie zadanie używa funkcji `receive`, aby czekać trzy sekundy na odebranie komunikatu z tego samego buforu komunikatów. Funkcja `receive` zgłasza `operation_timed_out`, jeśli nie otrzyma komunikatu w danym okresie czasu.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
The operation timed out.
```

Aby zapobiec nienormalnemu zakończeniu aplikacji, upewnij się, że kod obsługuje wyjątki, gdy wywołuje do środowiska uruchomieniowego. Obsługa wyjątków w przypadku wywołania w zewnętrznym kodzie, który używa środowisko uruchomieniowe współbieżności, na przykład biblioteki innej firmy.

[[Top](#top)]

## <a name="multiple"></a>Wiele wyjątków

Jeśli zadanie lub algorytm równoległy odbierze wiele wyjątków, środowisko uruchomieniowe będzie kierować tylko jeden z tych wyjątków do kontekstu wywołującego. Środowisko uruchomieniowe nie gwarantuje, który wyjątek jest organizowany.

W poniższym przykładzie jest używany algorytm `parallel_for` do drukowania numerów w konsoli programu. Zgłasza wyjątek, jeśli wartość wejściowa jest mniejsza niż minimalna wartość lub większa niż wartość maksymalna. W tym przykładzie wiele funkcji roboczych może zgłosić wyjątek.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

Poniżej przedstawiono przykładowe dane wyjściowe dla tego przykładu.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Top](#top)]

## <a name="cancellation"></a>Anulowania

Nie wszystkie wyjątki wskazują na błąd. Na przykład algorytm wyszukiwania może korzystać z obsługi wyjątków w celu zatrzymywania skojarzonego z nim zadania po znalezieniu wyniku. Aby uzyskać więcej informacji na temat sposobu używania mechanizmów anulowania w kodzie, zobacz [Anulowanie w PPL](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Top](#top)]

## <a name="lwts"></a>Zadania lekkie

Lekkie zadanie to zadanie, które można zaplanować bezpośrednio z obiektu [concurrency:: Scheduler](../../parallel/concrt/reference/scheduler-class.md) . Lekkie zadania zajmują mniej nakładów niż zwykłe zadania. Jednak środowisko uruchomieniowe nie przechwytuje wyjątków zgłaszanych przez uproszczone zadania. Zamiast tego wyjątek jest przechwytywany przez nieobsłużoną procedurę obsługi wyjątków, która domyślnie kończy proces. W związku z tym należy użyć odpowiedniego mechanizmu obsługi błędów w aplikacji. Aby uzyskać więcej informacji na temat uproszczonych zadań, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Top](#top)]

## <a name="agents"></a>Agenci asynchroniczni

Podobnie jak w przypadku uproszczonych zadań, środowisko uruchomieniowe nie zarządza wyjątkami zgłoszonymi przez agentów asynchronicznych.

W poniższym przykładzie pokazano jeden ze sposobów obsługi wyjątków w klasie, która wynika z [concurrency:: Agent](../../parallel/concrt/reference/agent-class.md). W tym przykładzie zdefiniowano klasę `points_agent`. Metoda `points_agent::run` odczytuje `point` obiektów z buforu komunikatów i drukuje je do konsoli programu. Metoda `run` zgłasza wyjątek, Jeśli odbierze wskaźnik `NULL`.

Metoda `run` otacza wszystkie prace w bloku `try`-`catch`. Blok `catch` przechowuje wyjątek w buforze komunikatów. Aplikacja sprawdza, czy Agent napotkał błąd przez odczyt z tego buforu po zakończeniu działania agenta.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Ponieważ blok `try`-`catch` istnieje poza pętlą `while`, Agent skończy przetwarzanie po napotkaniu pierwszego błędu. Jeśli blok `try`-`catch` był wewnątrz pętli `while`, Agent kontynuował działanie po wystąpieniu błędu.

W tym przykładzie są przechowywane wyjątki w buforze komunikatów, dzięki czemu inny składnik może monitorować agenta pod kątem błędów podczas jego działania. Ten przykład używa obiektu [concurrency:: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) do przechowywania błędu. W przypadku, gdy Agent obsługuje wiele wyjątków, Klasa `single_assignment` przechowuje tylko pierwszy komunikat, który jest do niego przesłany. Aby zachować tylko ostatni wyjątek, użyj klasy [concurrency:: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) . Aby przechowywać wszystkie wyjątki, użyj klasy [concurrency:: unbounded_buffer](reference/unbounded-buffer-class.md) . Aby uzyskać więcej informacji na temat tych bloków komunikatów, zobacz [asynchroniczne bloki komunikatów](../../parallel/concrt/asynchronous-message-blocks.md).

Aby uzyskać więcej informacji na temat agentów asynchronicznych, zobacz [agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md).

[[Top](#top)]

## <a name="summary"></a>Podsumowanie

[[Top](#top)]

## <a name="see-also"></a>Zobacz też

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
[Równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)
