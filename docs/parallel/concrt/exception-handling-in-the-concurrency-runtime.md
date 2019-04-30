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
ms.openlocfilehash: 8239913c369605503134a9ea4c99789528911868
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413934"
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Obsługa wyjątków we współbieżności środowiska wykonawczego

Środowisko uruchomieniowe współbieżności używa C++ obsługi wyjątków, aby komunikować się wiele rodzajów błędów. Te błędy zawierają nieprawidłowe użycie środowisko uruchomieniowe, błędy czasu wykonywania, np. nie można uzyskać zasobu i błędów występujących w przypadku funkcji roboczych, które zapewniają do grupy zadań i. Gdy zadania lub grupy zadań zgłasza wyjątek, środowisko uruchomieniowe przechowuje ten wyjątek i kieruje go do kontekstu, która czeka zadania lub grupy zadań, aby zakończyć. Składników, takich jak lekkie zadanie i agentów środowisko wykonawcze nie zarządza wyjątków dla Ciebie. W takich przypadkach należy zaimplementować własny mechanizm obsługi wyjątków. W tym temacie opisano, jak środowisko wykonawcze obsługuje wyjątki wyrzucane przez zadania, grupy zadań, lekkie zadanie i agentów asynchronicznych i odpowiadania na wyjątki w aplikacjach.

## <a name="key-points"></a>Kwestie kluczowe

- Gdy zadania lub grupy zadań zgłasza wyjątek, środowisko uruchomieniowe przechowuje ten wyjątek i kieruje go do kontekstu, która czeka zadania lub grupy zadań, aby zakończyć.

- Jeśli to możliwe, należy otoczyć każde wywołanie [CONCURRENCY::Task](reference/task-class.md#get) i [CONCURRENCY::Task](reference/task-class.md#wait) z `try` / `catch` bloku do obsługi błędów, które można odzyskać z usługi. Środowisko uruchomieniowe kończy aplikację, jeśli zadanie zgłasza wyjątek, a wyjątek nie zostanie przechwycony przez zadanie podrzędne, jeden z jego kontynuacji lub głównej aplikacji.

- Kontynuację opartą na zadaniach zawsze uruchamia; nie ma znaczenia, czy zadanie poprzedzające zostało ukończone pomyślnie, wyjątek lub została anulowana. Kontynuacja oparta na wartościach nie działa, jeśli zadanie poprzedzające zgłasza lub anuluje.

- Ponieważ kontynuacji opartych na zadaniach zawsze działa, rozważ, czy można dodać kontynuacja oparta na zadaniach na końcu swój łańcuch kontynuacji. Pozwoli to zagwarantować, że Twój kod rejestruje wszystkie wyjątki.

- Środowisko wykonawcze zgłasza [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) podczas wywoływania [CONCURRENCY::Task](reference/task-class.md#get) i to zadanie zostanie anulowane.

- Środowisko wykonawcze nie zarządza wyjątki lekkie zadanie i agentów.

##  <a name="top"></a> W tym dokumencie

- [Zadania i Kontynuacje](#tasks)

- [Grupy zadań i algorytmów równoległych](#task_groups)

- [Wyjątki generowane przez środowisko uruchomieniowe](#runtime)

- [Wiele wyjątków](#multiple)

- [Anulowanie](#cancellation)

- [Zadania lekkie](#lwts)

- [Agenci asynchroniczni](#agents)

##  <a name="tasks"></a> Zadania i Kontynuacje

W tej sekcji opisano, jak środowisko wykonawcze obsługuje wyjątki wyrzucane przez [concurrency::task](../../parallel/concrt/reference/task-class.md) obiektów i ich kontynuacji. Aby uzyskać więcej informacji na temat zadań i kontynuacji model zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

Kiedy zgłoszenie wyjątku w treści funkcji pracy, który jest przekazywany do `task` obiektu środowisko uruchomieniowe przechowuje ten wyjątek i kieruje je do kontekstu, który wywołuje [CONCURRENCY::Task](reference/task-class.md#get) lub [współbieżności:: Task::wait —](reference/task-class.md#wait). Dokument [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) opisano na podstawie zadania i kontynuacje na podstawie wartości, ale aby podsumować, kontynuacja oparta na wartościach przyjmuje parametr typu `T` i kontynuacja oparta na zadaniach przyjmuje parametr typu `task<T>`. Jeśli zadanie, które zgłasza ma co najmniej jeden kontynuacja oparta na wartościach, tych kontynuacji nie są planowane do uruchomienia. Poniższy przykład ilustruje ten problem:

[!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]

Kontynuacja oparta na zadaniach umożliwia obsługę każdego wyjątku, który jest generowany przez zadanie poprzedzające. Kontynuację opartą na zadaniach zawsze uruchamia; nie ma znaczenia, czy zadanie zakończyło się pomyślnie, wyjątek lub została anulowana. Gdy zadanie zgłasza wyjątek, jego kontynuacji opartych na zadaniach są zaplanowane do uruchomienia. Poniższy przykład przedstawia zadanie, które zawsze zgłasza wyjątek. Zadanie ma dwa kontynuacji; jeden jest oparta na wartościach, a drugi to oparta na zadaniach. Wyjątek opartego na zadaniach zawsze działa, a w związku z tym może przechwycić wyjątek, który jest generowany przez zadanie poprzedzające. Gdy przykład czeka dla obu kontynuacji zakończyć, wyjątek jest zgłaszany ponownie, ponieważ wyjątek zadania jest generowany zawsze, gdy `task::get` lub `task::wait` jest wywoływana.

[!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]

Zalecamy użycie kontynuacji opartych na zadaniach przechwytują wyjątki, które mogą obsługiwać. Ponieważ kontynuacji opartych na zadaniach zawsze działa, rozważ, czy można dodać kontynuacja oparta na zadaniach na końcu swój łańcuch kontynuacji. Pozwoli to zagwarantować, że Twój kod rejestruje wszystkie wyjątki. Poniższy przykład pokazuje podstawową na podstawie wartości kontynuację łańcucha. Trzecie zadanie w łańcuchu zgłasza, a w związku z tym nie są uruchamiane wszelkie kontynuacje na podstawie wartości, które występują po nim. Jednak końcowym kontynuacji jest oparta na zadaniach i w związku z tym zawsze działa. Końcowe kontynuacji obsługuje wyjątek, który jest generowany przez zadanie trzeci.

Zaleca się, że zostaną wychwycone najbardziej określone wyjątki, które możesz. Jeśli nie masz określonych wyjątków w celu przechwytywania, możesz pominąć ten ostateczny kontynuację opartą na zadaniach. Dowolny wyjątek pozostanie nieobsłużony i może zakończyć aplikację.

[!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]

> [!TIP]
>  Możesz użyć [concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md) metodę, aby skojarzyć wyjątek z zdarzenie zakończenia zadania. Dokument [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) opisuje [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) klasy bardziej szczegółowo.

[CONCURRENCY::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) jest typem wyjątku ważne środowiska uruchomieniowego, które odnoszą się do `task`. Środowisko wykonawcze zgłasza `task_canceled` podczas wywoływania `task::get` i to zadanie zostanie anulowane. (I odwrotnie, `task::wait` zwraca [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) i nie generuje.) Można przechwycić i obsłużyć wyjątek z kontynuacja oparta na zadaniach, lub gdy wywołujesz `task::get`. Aby uzyskać więcej informacji na temat anulowania zadania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).

> [!CAUTION]
>  Nigdy nie zgłaszają `task_canceled` w kodzie. Wywołaj [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) zamiast tego.

Środowisko uruchomieniowe kończy aplikację, jeśli zadanie zgłasza wyjątek, a wyjątek nie zostanie przechwycony przez zadanie podrzędne, jeden z jego kontynuacji lub głównej aplikacji. Jeśli aplikacja ulegnie awarii, można skonfigurować program Visual Studio, Przerwij, gdy są zgłaszane wyjątki C++. Po zdiagnozowaniu lokalizacji nieobsługiwany wyjątek, należy użyć kontynuacja oparta na zadaniach do jego obsługi.

Sekcja [wyjątki zgłoszone przez środowisko uruchomieniowe](#runtime) w tym dokumencie opisano sposób pracy z wyjątki środowiska uruchomieniowego, które bardziej szczegółowo.

[[Górnej](#top)]

##  <a name="task_groups"></a> Grupy zadań i algorytmów równoległych

W tej sekcji opisano, jak środowisko wykonawcze obsługuje wyjątki wyrzucane przez grupy zadań. W tej sekcji dotyczą również algorytmów równoległych taką jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), ponieważ te algorytmy tworzenie grup zadań.

> [!CAUTION]
>  Upewnij się, że rozumiesz, jakie wyjątki mają zadania zależne efekty. Aby uzyskać zalecane praktyki o sposobie używania obsługi wyjątków za pomocą zadania lub algorytmów równoległych, zobacz [omówienie jak anulowania i wyjątków obsługi wpływają na zniszczenie obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) sekcji najlepszych rozwiązań w sposób równoległy Temat Biblioteka wzorców.

Aby uzyskać więcej informacji o grupach zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji dotyczących algorytmów równoległych, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).

Kiedy zgłoszenie wyjątku w treści funkcji pracy, który jest przekazywany do [concurrency::task_group](reference/task-group-class.md) lub [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu środowisko uruchomieniowe przechowuje ten wyjątek i kieruje je kontekst, który wywołuje [CONCURRENCY::task_group:: wait](reference/task-group-class.md#wait), [CONCURRENCY::structured_task_group:: wait](reference/structured-task-group-class.md#wait), [CONCURRENCY::task_group:: run_and_wait](reference/task-group-class.md#run_and_wait), lub [CONCURRENCY::structured_task_group::](reference/structured-task-group-class.md#run_and_wait). Środowisko uruchomieniowe również zatrzymuje wszystkie aktywne zadania, które znajdują się w grupie zadań (włączając te w podrzędnych grupach zadań) i odrzuca wszelkie zadania, które nie zostały rozpoczęte.

Poniższy przykład pokazuje strukturę podstawowych funkcji pracy, która zgłosiła wyjątek. W przykładzie użyto `task_group` obiektu do wyświetlania wartości z dwóch `point` obiektów równolegle. `print_point` Funkcja pracy drukuje wartości `point` obiekcie do konsoli. Ta funkcja pracy zgłasza wyjątek, jeśli wartość wejściowa jest `NULL`. Środowisko uruchomieniowe przechowuje ten wyjątek i kieruje je do kontekstu, który wywołuje `task_group::wait`.

[!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
X = 15, Y = 30Caught exception: point is NULL.
```

Aby uzyskać kompletny przykład używającej obsługi wyjątków w grupy zadań, zobacz [jak: Użyj wyjątków, obsługa aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).

[[Górnej](#top)]

##  <a name="runtime"></a> Wyjątki generowane przez środowisko uruchomieniowe

Wyjątek może wynikać z wywołaniem do środowiska uruchomieniowego. Większość typów wyjątków, z wyjątkiem [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) i [concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), wskazywać na błąd programowania. Te błędy są zazwyczaj nieodwracalny i w związku z tym nie należy przechwycono ani obsłużony przez kod aplikacji. Sugerujemy tylko przechwytywać i obsługiwać nieodwracalne błędy w kodzie aplikacji, jeśli musisz zdiagnozować błędy programowania. Jednak zrozumienie typów wyjątków, które są zdefiniowane przez środowisko uruchomieniowe może pomóc zdiagnozować błędy programowania.

Mechanizm obsługi wyjątków jest taka sama dla wyjątki wyrzucane przez środowisko uruchomieniowe jako wyjątki wyrzucane przez funkcje robocze. Na przykład [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcja zgłasza `operation_timed_out` kiedy nie otrzyma komunikat w określonym przedziale czasu. Jeśli `receive` zgłasza wyjątek w funkcji pracy można przekazać do grupy zadań, środowisko uruchomieniowe przechowuje ten wyjątek i kieruje je do kontekstu, który wywołuje `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`, lub `structured_task_group::run_and_wait`.

W poniższym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytmu do równoległego uruchamiania dwa zadania. Pierwsze zadanie oczekuje na pięć sekund, a następnie wysyła wiadomość do buforu komunikatu. Drugie zadanie używa `receive` funkcja oczekiwania trzy sekundy do odbierania wiadomości z tego samego buforu komunikatu. `receive` Funkcja zgłasza `operation_timed_out` Jeśli otrzymasz komunikat w przedziale czasu.

[!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
The operation timed out.
```

Aby zapobiec Nienormalne zakończenie aplikacji, upewnij się, że kod obsługuje wyjątki podczas wywoływanych przez nią w czasie wykonywania. Również obsługiwać wyjątki, gdy wywołujesz do zewnętrznego kodu, który korzysta ze współbieżności środowiska wykonawczego, na przykład biblioteki innej firmy.

[[Górnej](#top)]

##  <a name="multiple"></a> Wiele wyjątków

Jeśli algorytm zadania lub równolegle odbierze wiele wyjątków, środowisko uruchomieniowe kieruje tylko jeden z tych wyjątków do wywoływania kontekstu. Środowisko wykonawcze nie gwarantuje wyjątek, który kieruje go.

W poniższym przykładzie użyto `parallel_for` algorytm numery do konsoli. Zgłasza wyjątek, jeśli wartość wejściowa jest mniejsza niż niektóre minimalne wartości lub większa od niektórych wartość maksymalna. W tym przykładzie wiele funkcji roboczych może zgłosić wyjątek.

[!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]

Poniżej przedstawiono przykładowe dane wyjściowe, w tym przykładzie.

```Output
8293104567Caught exception: -5: the value is less than the minimum.
```

[[Górnej](#top)]

##  <a name="cancellation"></a> Unieważnieniu

Nie wszystkie wyjątki wskazywać na błąd. Algorytm wyszukiwania może na przykład użyć obsługi wyjątków można zatrzymać jej skojarzone zadania, gdy znajdzie wynik. Aby uzyskać więcej informacji o sposobie używania mechanizmów anulowania w kodzie, zobacz [anulowanie w PPL](../../parallel/concrt/cancellation-in-the-ppl.md).

[[Górnej](#top)]

##  <a name="lwts"></a> Zadania lekkie

Lekkie zadanie jest zadaniem, która jest zaplanowania bezpośrednio z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) obiektu. Zadania lekkie mają mniejsze obciążenie niż zwykłe zadania. Jednakże środowisko uruchomieniowe nie może przechwytywać wyjątków, które są generowane przez zadania lekkie. Zamiast tego wyjątku jest przechwycony przez program obsługi nieobsługiwanego wyjątku, który domyślnie kończy proces. W związku z tym należy użyć odpowiedniego mechanizmu obsługi błędów w aplikacji. Aby uzyskać więcej informacji na temat zadań lekkich zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Górnej](#top)]

##  <a name="agents"></a> Agenci asynchroniczni

Podobnie jak lżejsze zadania środowisko uruchomieniowe nie zarządza wyjątki wyrzucane przez agentów asynchronicznych.

Poniższy przykład przedstawia sposób obsługi wyjątków w klasie, która pochodzi od klasy [concurrency::agent](../../parallel/concrt/reference/agent-class.md). Ten przykład definiuje `points_agent` klasy. `points_agent::run` Odczyty metoda `point` z buforu komunikatu obiekty i ich drukuje do konsoli. `run` Metoda zgłasza wyjątek, jeśli odbierze `NULL` wskaźnika.

`run` Metoda otacza całą pracę w `try` - `catch` bloku. `catch` Bloku przechowuje wyjątek w buforu komunikatu. Aplikacja sprawdza, czy agent napotkał błąd, czytając od tego buforu, po zakończeniu działania agenta.

[!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]

Ten przykład generuje następujące dane wyjściowe.

```Output
X: 10 Y: 20
X: 20 Y: 30
error occurred in agent: point must not be NULL
the status of the agent is: done
```

Ponieważ `try` - `catch` bloku istnieje poza `while` agenta pętli, kończy przetwarzanie po napotkaniu pierwszego błędu. Jeśli `try` - `catch` znajdowało się wewnątrz bloku `while` pętli, agent będzie przeprowadzany ciągły po wystąpieniu błędu.

W tym przykładzie przechowuje wyjątki w buforze wiadomości, dzięki czemu innego składnika można monitorować agenta błędy podczas jej działania. W tym przykładzie użyto [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) obiekt ma być przechowywany ten błąd. W przypadku, gdy agent obsługuje wiele wyjątków `single_assignment` klasa przechowuje tylko pierwszy komunikat, który jest przekazywany do niego. Aby przechowywać tylko ostatni wyjątek, należy użyć [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) klasy. Aby przechowywać wszystkie wyjątki, należy użyć [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) klasy. Aby uzyskać więcej informacji na temat tych bloków wiadomości, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).

Aby uzyskać więcej informacji na temat agentów asynchronicznych, zobacz [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md).

[[Górnej](#top)]

##  <a name="summary"></a> Podsumowanie

[[Górnej](#top)]

## <a name="see-also"></a>Zobacz także

[Środowisko uruchomieniowe współbieżności](../../parallel/concrt/concurrency-runtime.md)<br/>
[Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)<br/>
[Anulowanie w PPL](cancellation-in-the-ppl.md)<br/>
[Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)
