---
title: Obsługa wyjątków w współbieżności środowiska wykonawczego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lightweight tasks, exception handling [Concurrency Runtime]
- exception handling [Concurrency Runtime]
- structured task groups, exception handling [Concurrency Runtime]
- agents, exception handling [Concurrency Runtime]
- task groups, exception handling [Concurrency Runtime]
ms.assetid: 4d1494fb-3089-4f4b-8cfb-712aa67d7a7a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5f30c98a8800c3aeaaf5ff1dab5bee9bdba971a6
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="exception-handling-in-the-concurrency-runtime"></a>Obsługa wyjątków we współbieżności środowiska wykonawczego
Współbieżność środowiska wykonawczego używa do komunikacji wiele rodzajów błędy w obsłudze wyjątków C++. Te błędy zawierają nieprawidłowe użycie środowisko uruchomieniowe, błędy wykonania, takie jak niepowodzenia uzyskania zasobu i błędów występujących w funkcjach pracy, które świadczą zadania i grupy zadań. Jeśli zadania lub grupy zadań zgłasza wyjątek, środowiska uruchomieniowego zawiera ten wyjątek i marshals go do kontekstu, która oczekuje na zadanie lub grupy zadań, aby zakończyć. Składniki, takie jak zadania lekkie i agentów środowisko uruchomieniowe nie zarządza wyjątki dla Ciebie. W takich sytuacjach należy zaimplementować własny mechanizm obsługi wyjątków. W tym temacie opisano sposób obsługi wyjątków, które są generowane przez zadania, grupy zadań, zadań lekkich i agentów asynchronicznych przez środowisko uruchomieniowe i odpowiadanie na wyjątków w aplikacji.  
  
## <a name="key-points"></a>Kwestie kluczowe  
  
-   Jeśli zadania lub grupy zadań zgłasza wyjątek, środowiska uruchomieniowego zawiera ten wyjątek i marshals go do kontekstu, która oczekuje na zadanie lub grupy zadań, aby zakończyć.  
  
-   Jeśli to możliwe, należy ująć każdego wywołania [concurrency::task::get](reference/task-class.md#get) i [concurrency::task::wait](reference/task-class.md#wait) z `try` / `catch` bloku do obsługi błędów, które można odzyskać z. Środowisko uruchomieniowe kończy aplikacji, jeśli zadanie zgłasza wyjątek i wyjątek nie zostanie przechwycony przez zadanie, jeden z jego kontynuacje lub głównego aplikacji.  
  
-   Uruchamia zawsze oparty na zadaniach utrzymania; nie ma znaczenia, czy poprzedzających zadanie zakończone pomyślnie, zgłosiło wyjątek lub została anulowana. Utrzymania na podstawie wartości nie zostanie uruchomiony, jeśli zadanie poprzedzających zgłasza wyjątek, lub anuluje.  
  
-   Ponieważ kontynuacje opartego na zadaniach są zawsze uruchamiane, należy rozważyć, czy mają zostać dodane na końcu łańcucha z kontynuacji utrzymania opartego na zadaniach. Ułatwia to zagwarantować, że kod przestrzega wszystkie wyjątki.  
  
-   Środowisko uruchomieniowe zgłasza [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) podczas wywoływania [concurrency::task::get](reference/task-class.md#get) i że zadanie zostało anulowane.  

  
-   Środowisko uruchomieniowe nie zarządza wyjątków dla potrzeb zadań lekkich i agentów.  
  
##  <a name="top"></a> W tym dokumencie  
  
- [Zadania i Kontynuacje](#tasks)  
  
- [Grup zadań i algorytmy równoległe](#task_groups)  
  
- [Wyjątki generowane przez środowisko uruchomieniowe](#runtime)  
  
- [Wiele wyjątków](#multiple)  
  
- [Anulowanie](#cancellation)  
  
- [Zadania lekkie](#lwts)  
  
- [Agenci asynchroniczni](#agents)  
  
##  <a name="tasks"></a> Zadania i Kontynuacje  
 W tej sekcji opisano sposób środowisko uruchomieniowe obsługi wyjątków, które są generowane przez [concurrency::task](../../parallel/concrt/reference/task-class.md) obiektów i ich kontynuacje. Aby uzyskać więcej informacji dotyczących zadań i kontynuacji modelu, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
 Podczas zgłoszenia wyjątku w treści funkcji pracy, który jest przekazywany do `task` obiektu środowiska wykonawczego przechowuje ten wyjątek i marshals go do kontekstu, która wywołuje [concurrency::task::get](reference/task-class.md#get) lub [współbieżności:: Task::wait](reference/task-class.md#wait). Dokument [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) opisuje opartemu na zadaniach i kontynuacje na podstawie wartości, ale aby podsumować, na podstawie wartości utrzymania przyjmuje parametr typu `T` i utrzymania opartego na zadaniach przyjmuje parametr typu `task<T>`. Jeśli zadanie, które generuje ma co najmniej jeden kontynuacje oparte na wartościach, kontynuacje te nie są zaplanowane do uruchomienia. Poniższy przykład przedstawia tego zachowania:  

  
 [!code-cpp[concrt-eh-task#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_1.cpp)]  
  
 Kontynuacja opartego na zadaniach umożliwia obsługi wyjątku zgłoszonego przez poprzedzających zadań. Uruchamia zawsze oparty na zadaniach utrzymania; nie ma znaczenia, czy zadanie zakończone pomyślnie, zgłosiło wyjątek lub została anulowana. Gdy zadanie zgłasza wyjątek, jego kontynuacje opartego na zadaniach są zaplanowane do uruchomienia. W poniższym przykładzie przedstawiono zadania, które zawsze zgłasza wyjątek. Zadanie zostało dwóch kontynuacje; jeden jest oparta na wartości, a drugi to oparty na zadaniach. Wyjątek opartego na zadaniach zawsze działa, a w związku z tym można catch wyjątku zgłoszonego przez poprzedzających zadań. Gdy przykładzie czeka na obu kontynuacje zakończyć, wyjątku ponownie, ponieważ zadanie jest zwracany wyjątek, zawsze gdy `task::get` lub `task::wait` jest wywoływana.  
  
 [!code-cpp[concrt-eh-continuations#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_2.cpp)]  
  
 Zalecane jest użycie opartego na zadaniach kontynuacje przechwytują wyjątki, które mogą obsługiwać. Ponieważ kontynuacje opartego na zadaniach są zawsze uruchamiane, należy rozważyć, czy mają zostać dodane na końcu łańcucha z kontynuacji utrzymania opartego na zadaniach. Ułatwia to zagwarantować, że kod przestrzega wszystkie wyjątki. W poniższym przykładzie przedstawiono łańcuch podstawowych kontynuacji na podstawie wartości. Trzeci zadań w łańcuchu zgłasza wyjątek, a w związku z tym żadnych kontynuacje na podstawie wartości, które po nim nie są uruchamiane. Jednak kontynuacji końcowego jest oparty na zadaniach i w związku z tym zawsze działa. Ten końcowy kontynuacji obsługuje wyjątek zgłaszany przez zadanie trzeci.  
  
 Zaleca się, że zostaną wychwycone specyficzny wyjątki, które można wykonywać następujące czynności. Ten końcowy oparty na zadaniach kontynuacji można pominąć, jeśli nie ma określonych wyjątków do catch. Każdy wyjątek pozostanie nieobsłużony i może zakończyć aplikację.  
  
 [!code-cpp[concrt-eh-task-chain#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_3.cpp)]  
  
> [!TIP]
>  Można użyć [concurrency::task_completion_event::set_exception](../../parallel/concrt/reference/task-completion-event-class.md) do kojarzenia wyjątek z zdarzenie ukończenia zadania. Dokument [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md) opisuje [concurrency::task_completion_event](../../parallel/concrt/reference/task-completion-event-class.md) klasy większej liczby szczegółów.  
  

 [CONCURRENCY::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) ma typ wyjątku ważne środowiska uruchomieniowego, które odnoszą się do `task`. Środowisko uruchomieniowe zgłasza `task_canceled` podczas wywoływania `task::get` i że zadanie zostało anulowane. (Natomiast `task::wait` zwraca [task_status::canceled](reference/concurrency-namespace-enums.md#task_group_status) i nie zgłasza.) Można wychwycić i obsłużyć tego wyjątku z opartego na zadaniach utrzymania lub podczas wywoływania `task::get`. Aby uzyskać więcej informacji na temat anulowanie zadania, zobacz [anulowanie w PPL](cancellation-in-the-ppl.md).  

  
> [!CAUTION]
>  Nigdy nie zgłaszają `task_canceled` w kodzie. Wywołanie [concurrency::cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) zamiast tego.  
  
 Środowisko uruchomieniowe kończy aplikacji, jeśli zadanie zgłasza wyjątek i wyjątek nie zostanie przechwycony przez zadanie, jeden z jego kontynuacje lub głównego aplikacji. Jeśli aplikacja ulegnie awarii, można skonfigurować programu Visual Studio, aby Przerwij, gdy są zgłaszane wyjątki C++. Po zdiagnozowaniu lokalizację nieobsługiwany wyjątek umożliwia jego obsługa utrzymania opartego na zadaniach.  
  
 Sekcja [wyjątki zgłaszane przez środowisko uruchomieniowe](#runtime) w tym dokumencie opisano sposób pracy z obsługi wyjątków bardziej szczegółowo.  
  
 [[Górnej](#top)]  
  
##  <a name="task_groups"></a> Grup zadań i algorytmy równoległe  

 W tej sekcji opisano, jak środowisko uruchomieniowe obsługi wyjątków, które są generowane przez grupy zadań. W tej sekcji dotyczą również algorytmy równoległe takich jak [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for), ponieważ te algorytmy kompilacji na grupy zadań.  
  
> [!CAUTION]
>  Upewnij się, że rozumiesz efekty, których wyjątków na zadania zależne. Zalecane praktyki dotyczące korzystania z zadań lub algorytmy równoległe w obsłudze wyjątków, aby zapoznać [opis sposobu anulowania i wyjątek obsługi wpływają na zniszczeniem obiektu](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md#object-destruction) części najlepsze rozwiązania równolegle Wzorce tematu biblioteki.  
  
 Aby uzyskać więcej informacji na temat grupy zadań, zobacz [równoległość zadań](../../parallel/concrt/task-parallelism-concurrency-runtime.md). Aby uzyskać więcej informacji na temat algorytmy równoległe, zobacz [algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md).  

 Podczas zgłoszenia wyjątku w treści funkcji pracy, który jest przekazywany do [concurrency::task_group](reference/task-group-class.md) lub [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) obiektu środowiska wykonawczego przechowuje ten wyjątek i marshals go w kontekście, który wywołuje [concurrency::task_group::wait](reference/task-group-class.md#wait), [concurrency::structured_task_group::wait](reference/structured-task-group-class.md#wait), [concurrency::task_group::run_and_wait](reference/task-group-class.md#run_and_wait), lub [concurrency::structured_task_group::run_and_wait](reference/structured-task-group-class.md#run_and_wait). Środowisko uruchomieniowe również zatrzymuje wszystkie aktywne zadania, które znajdują się w grupie zadań (włącznie z zawartymi grupy zadań podrzędnych) i odrzuca wszystkie zadania, które nie zostały jeszcze uruchomione.  

  
 Poniższy przykład przedstawia podstawową strukturę funkcji pracy zgłasza wyjątek. W przykładzie użyto `task_group` obiektu wartości dwu `point` obiektów równolegle. `print_point` Pracy funkcja służy do drukowania wartości `point` obiektu do konsoli. Funkcja pracy zgłasza wyjątek, jeśli wartość wejściowa jest `NULL`. Środowisko uruchomieniowe przechowuje ten wyjątek i marshals go do kontekstu, która wywołuje `task_group::wait`.  
  
 [!code-cpp[concrt-eh-task-group#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_4.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
X = 15, Y = 30Caught exception: point is NULL.  
```  
  
 Pełny przykład używającej obsługi wyjątków w grupy zadań, zobacz [porady: Użyj obsługi wyjątków aby przerwać pętlę równoległą](../../parallel/concrt/how-to-use-exception-handling-to-break-from-a-parallel-loop.md).  
  
 [[Górnej](#top)]  
  
##  <a name="runtime"></a> Wyjątki generowane przez środowisko uruchomieniowe  
 Wystąpił wyjątek mogą być wynikiem wywołania do środowiska wykonawczego. Większość typów wyjątków, z wyjątkiem [concurrency::task_canceled](../../parallel/concrt/reference/task-canceled-class.md) i [concurrency::operation_timed_out](../../parallel/concrt/reference/operation-timed-out-class.md), wskazywać na błąd programowania. Te błędy są zwykle nieodwracalny i dlatego nie należy przechwycono ani obsłużony przez kod aplikacji. Zaleca się tylko catch lub dojścia powodujące nieodwracalne błędy w kodzie aplikacji, gdy trzeba diagnozowanie błędów programowania. Jednak opis typów wyjątków, które są zdefiniowane przez środowisko uruchomieniowe ułatwia diagnozowanie błędów programowania.  
  
 Mechanizm obsługi wyjątków jest taki sam dla wyjątków, które są generowane przez środowisko uruchomieniowe jako wyjątki, które są generowane przez funkcje pracy. Na przykład [concurrency::receive](reference/concurrency-namespace-functions.md#receive) funkcji zgłasza `operation_timed_out` po nie otrzyma komunikat w określonym przedziale czasu. Jeśli `receive` zgłasza wyjątek w funkcji pracy przekazujesz do grupy zadań, środowisko uruchomieniowe przechowuje ten wyjątek i marshals go do kontekstu, która wywołuje `task_group::wait`, `structured_task_group::wait`, `task_group::run_and_wait`, lub `structured_task_group::run_and_wait`.  
  
 W poniższym przykładzie użyto [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorytm równolegle dwa zadania. Pierwszym zadaniem oczekuje 5 sekund, a następnie wysyła komunikat do buforu komunikatu. Drugie zadanie używa `receive` funkcja oczekiwania trzy sekundy do odbierania wiadomości z tego samego buforu komunikatu. `receive` Funkcji zgłasza `operation_timed_out` Jeśli otrzymasz komunikat w przedziale czasu.  
  
 [!code-cpp[concrt-eh-time-out#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_5.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
The operation timed out.  
```  
  
 Aby zapobiec przerwania pracy aplikacji, upewnij się, że kod obsługuje wyjątki podczas wywoływanych przez nią w czasie wykonywania. Również obsługa wyjątków w przypadku wywołania do zewnętrznego kodu, który korzysta ze współbieżności środowiska wykonawczego, na przykład biblioteki innych firm.  
  
 [[Górnej](#top)]  
  
##  <a name="multiple"></a> Wiele wyjątków  
 Jeśli algorytm zadań lub równolegle odbiera wiele wyjątków, środowisko uruchomieniowe marshals tylko jeden z tych wyjątków do wywoływania kontekstu. Środowisko uruchomieniowe nie gwarantuje wyjątków marshals go.  
  
 W poniższym przykładzie użyto `parallel_for` algorytm numery do konsoli. Jeśli wartość wejściowa jest mniejsza niż niektórych wartość minimalna lub większa niż niektórych wartość maksymalna, zgłasza wyjątek. W tym przykładzie wiele funkcji pracy może zgłosić wyjątek.  
  
 [!code-cpp[concrt-eh-multiple#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_6.cpp)]  
  
 Poniżej przedstawiono przykładowe dane wyjściowe w tym przykładzie.  
  
```Output  
8293104567Caught exception: -5: the value is less than the minimum.  
```  
  
 [[Górnej](#top)]  
  
##  <a name="cancellation"></a> Anulowanie  
 Nie wszystkie wyjątki oznaczać błąd. Algorytm wyszukiwania może na przykład użyć obsługi wyjątków można zatrzymać jej skojarzonego zadania, gdy znajdzie wynik. Aby uzyskać więcej informacji o sposobie używania mechanizmów anulowania w kodzie, zobacz [anulowanie w PPL](../../parallel/concrt/cancellation-in-the-ppl.md).  
  
 [[Górnej](#top)]  
  
##  <a name="lwts"></a> Zadania lekkie  
 Zadania lekkie to zadanie, które można planować bezpośrednio z [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) obiektu. Zadania lekkie przenosić mniejsze koszty niż zwykłe zadania. Jednak środowiska uruchomieniowego nie przechwytuje wyjątków, które są generowane przez zadania lekkie. Zamiast tego wyjątek zostanie przechwycony przez program obsługi nieobsługiwanego wyjątku, która domyślnie kończy proces. W związku z tym użyj odpowiedni mechanizm obsługi błędów w aplikacji. Aby uzyskać więcej informacji na temat zadań lekkich, zobacz [harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Górnej](#top)]  
  
##  <a name="agents"></a> Agenci asynchroniczni  
 Podobnie jak zadania lekkie środowisko uruchomieniowe nie zarządza wyjątki, które są generowane przez agentów asynchronicznych.  
  
 Poniższy przykład przedstawia sposób obsługi wyjątków w klasie, która jest pochodną [concurrency::agent](../../parallel/concrt/reference/agent-class.md). W tym przykładzie definiuje `points_agent` klasy. `points_agent::run` Metoda odczytuje `point` obiektów z buforu komunikatu i wyświetla je w konsoli. `run` Metoda zgłasza wyjątek, gdy odbierze `NULL` wskaźnika.  
  
 `run` Metody otaczający całą pracę w `try` - `catch` bloku. `catch` Bloku przechowuje wyjątek w buforze wiadomości. Aplikacja sprawdza, czy agent napotkał błąd przez odczyt z buforu, po zakończeniu działania agenta.  
  
 [!code-cpp[concrt-eh-agents#1](../../parallel/concrt/codesnippet/cpp/exception-handling-in-the-concurrency-runtime_7.cpp)]  
  
 W tym przykładzie tworzy następujące dane wyjściowe.  
  
```Output  
X: 10 Y: 20  
X: 20 Y: 30  
error occurred in agent: point must not be NULL  
the status of the agent is: done  
```  
  
 Ponieważ `try` - `catch` blok istnieje poza `while` pętli, agent kończy się przetwarzania po napotkaniu pierwszego błędu. Jeśli `try` - `catch` znajdowało się wewnątrz bloku `while` pętli, agent będzie kontynuował po wystąpieniu błędu.  
  
 W tym przykładzie przechowuje wyjątków w buforze wiadomości, dzięki czemu innego składnika można monitorować agenta błędy podczas jego wykonywania. W tym przykładzie użyto [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) obiekt, aby zapisać błędu. W przypadku, gdy agent obsługuje wiele wyjątków `single_assignment` klasy przechowuje tylko pierwszy komunikat, który jest przekazywany do niego. Aby przechowywać tylko ostatniego wyjątku, użyj [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) klasy. Aby przechowywać wszystkie wyjątki, użyj [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) klasy. Aby uzyskać więcej informacji na temat te bloki komunikatów, zobacz [bloki komunikatów asynchronicznych](../../parallel/concrt/asynchronous-message-blocks.md).  
  
 Aby uzyskać więcej informacji na temat agentów asynchronicznych, zobacz [agentów asynchronicznych](../../parallel/concrt/asynchronous-agents.md).  
  
 [[Górnej](#top)]  
  
##  <a name="summary"></a> Podsumowanie  
 [[Górnej](#top)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współbieżność środowiska wykonawczego](../../parallel/concrt/concurrency-runtime.md)   
 [Równoległość zadania](../../parallel/concrt/task-parallelism-concurrency-runtime.md)   
 [Algorytmy równoległe](../../parallel/concrt/parallel-algorithms.md)   
 [Anulowanie w PPL](cancellation-in-the-ppl.md)   
 [Harmonogram zadań](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Agenci asynchroniczni](../../parallel/concrt/asynchronous-agents.md)

