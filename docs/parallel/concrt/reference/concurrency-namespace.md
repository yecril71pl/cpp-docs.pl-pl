---
title: concurrency — Przestrzeń nazwy
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue/concurrency
- agents/concurrency
- concurrent_vector/concurrency
- concrt/concurrency
- internal_split_ordered_list/concurrency
- concurrent_queue/concurrency
- pplcancellation_token/concurrency
- pplinterface/concurrency
- ppltasks/concurrency
- ppl/concurrency
- concurrent_unordered_map/concurrency
- concrtrm/concurrency
- concurrent_unordered_set/concurrency
- pplconcrt/concurrency
- internal_concurrent_hash/concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
ms.openlocfilehash: 06134838494e38c182d7c8328497666862f40fd6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143225"
---
# <a name="concurrency-namespace"></a>concurrency — Przestrzeń nazwy

Przestrzeń nazw `Concurrency` zawiera klasy i funkcje, które zapewniają dostęp do środowisko uruchomieniowe współbieżności, współbieżne platformy programistyczne dla C++programu. Aby uzyskać więcej informacji, zobacz [środowisko uruchomieniowe współbieżności](../../../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Składnia

```cpp
namespace concurrency;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedefs

|Name (Nazwa)|Opis|
|----------|-----------------|
|`runtime_object_identity`|Każde wystąpienie komunikatu ma tożsamość, która następuje po jej sklonowaniu i przekazaniu między składnikami obsługi komunikatów. Nie może to być adres obiektu wiadomości.|
|`task_status`|Typ, który reprezentuje stan terminalu zadania. Prawidłowe wartości to `completed` i `canceled`.|
|`TaskProc`|Podstawowe streszczenie dla zadania, zdefiniowane jako `void (__cdecl * TaskProc)(void *)`. `TaskProc` jest wywoływana, aby wywołać treść zadania.|
|`TaskProc_t`|Podstawowe streszczenie dla zadania, zdefiniowane jako `void (__cdecl * TaskProc_t)(void *)`. `TaskProc` jest wywoływana, aby wywołać treść zadania.|

### <a name="classes"></a>Klasy

|Name (Nazwa)|Opis|
|----------|-----------------|
|[affinity_partitioner, klasa](affinity-partitioner-class.md)|Klasa `affinity_partitioner` jest podobna do klasy `static_partitioner`, ale zwiększa koligację pamięci podręcznej przez wybór zakresu mapowania na wątki robocze. Może znacząco poprawić wydajność, gdy pętla jest ponownie wykonywana nad tym samym zestawem danych, a dane pasują do pamięci podręcznej. Należy zauważyć, że ten sam obiekt `affinity_partitioner` musi być używany z kolejnymi iteracjami pętli równoległej, który jest wykonywany w określonym zestawie danych, aby można było korzystać z lokalizacji danych.|
|[agent, klasa](agent-class.md)|Klasa przeznaczona do użycia jako klasa bazowa dla wszystkich niezależnych agentów. Służy do ukrycia stanu od innych agentów i korzystania z przekazywania komunikatów.|
|[auto_partitioner, klasa](auto-partitioner-class.md)|Klasa `auto_partitioner` reprezentuje domyślną metodę `parallel_for`, `parallel_for_each` i `parallel_transform` użyć do partycjonowania zakresu, w którym się powtarza. Ta metoda partycjonowania wykorzystuje funkcję kradzieży zakresu na potrzeby równoważenia obciążenia, a także anulowania dla iteracji.|
|[bad_target, klasa](bad-target-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy blok komunikatów otrzymuje wskaźnik do obiektu docelowego, który jest nieprawidłowy dla wykonywanej operacji.|
|[call, klasa](call-class.md)|Blok komunikatów `call` to wiele źródeł uporządkowanych `target_block`, które wywołuje określoną funkcję podczas otrzymywania wiadomości.|
|[cancellation_token, klasa](cancellation-token-class.md)|Klasa `cancellation_token` reprezentuje możliwość ustalenia, czy żądana operacja została anulowana. Dany token może być skojarzony z `task_group`, `structured_task_group`lub `task` w celu zapewnienia niejawnego anulowania. Może być również sondowany w celu anulowania lub mieć zarejestrowane wywołanie zwrotne dla if i po anulowaniu skojarzonego `cancellation_token_source`.|
|[cancellation_token_registration, klasa](cancellation-token-registration-class.md)|Klasa `cancellation_token_registration` reprezentuje powiadomienie wywołania zwrotnego z `cancellation_token`. Gdy metoda `register` na `cancellation_token` jest używana do otrzymywania powiadomień o wystąpieniu anulowania, obiekt `cancellation_token_registration` jest zwracany jako dojście do wywołania zwrotnego, dzięki czemu obiekt wywołujący może zażądać określonego wywołania zwrotnego za pomocą metody `deregister`.|
|[cancellation_token_source, klasa](cancellation-token-source-class.md)|Klasa `cancellation_token_source` reprezentuje możliwość anulowania niektórych operacji do anulowania.|
|[choice, klasa](choice-class.md)|Blok komunikatów `choice` jest blokiem pojedynczego źródła, który reprezentuje interakcję przepływu sterowania z zestawem źródeł. Blok wyboru czeka na jedno z wielu źródeł, aby utworzyć komunikat i propaguje indeks źródła, który wygenerował komunikat.|
|[combinable, klasa](combinable-class.md)|Obiekt `combinable<T>` jest przeznaczony do dostarczania prywatnych kopii wątku danych w celu wykonania niezależnych od siebie podobliczeń wątku podczas równoległych algorytmów. Na końcu operacji równoległej podobliczenia wątku i prywatnego mogą zostać następnie scalone w wynik końcowy. Ta klasa może być używana zamiast zmiennej udostępnionej i może skutkować zwiększeniem wydajności, jeśli w przeciwnym razie będzie wiele rywalizacji dotyczących tej zmiennej udostępnionej.|
|[concurrent_priority_queue, klasa](concurrent-priority-queue-class.md)|Klasa `concurrent_priority_queue` jest kontenerem, który umożliwia wielu wątkom równoczesne wypychanie i wypunktowanie elementów. Elementy są zdjęte w kolejności priorytetu, gdzie priorytet jest określany przez Funktor dostarczone jako argument szablonu.|
|[concurrent_queue, klasa](concurrent-queue-class.md)|Klasa `concurrent_queue` jest klasą kontenera sekwencji, która umożliwia pierwszy i pierwszy dostęp do jego elementów. Umożliwia ograniczony zestaw operacji związanych z współbieżnością, takich jak `push` i `try_pop`.|
|[concurrent_unordered_map, klasa](concurrent-unordered-map-class.md)|Klasa `concurrent_unordered_map` jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne wykonywanie operacji dołączania, dostęp do elementów, dostęp iteratora i przechodzenie iteratora.|
|[concurrent_unordered_multimap, klasa](concurrent-unordered-multimap-class.md)|Klasa `concurrent_unordered_multimap` jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[concurrent_unordered_multiset, klasa](concurrent-unordered-multiset-class.md)|Klasa `concurrent_unordered_multiset` jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[concurrent_unordered_set, klasa](concurrent-unordered-set-class.md)|Klasa `concurrent_unordered_set` jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[concurrent_vector, klasa](concurrent-vector-class.md)|Klasa `concurrent_vector` jest klasą kontenera sekwencji, która umożliwia losowy dostęp do dowolnego elementu. Umożliwia ona bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[Context, klasa](context-class.md)|Reprezentuje streszczenie dla kontekstu wykonania.|
|[context_self_unblock, klasa](context-self-unblock-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Unblock` obiektu `Context` jest wywoływana z tego samego kontekstu. Spowoduje to wskazanie próby odblokowania przez dany kontekst.|
|[context_unblock_unbalanced, klasa](context-unblock-unbalanced-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy wywołania metod `Block` i `Unblock` obiektu `Context` nie są prawidłowo sparowane.|
|[critical_section, klasa](critical-section-class.md)|Niewspółpracujący obiekt mutex, który jest jawnie świadomy środowisko uruchomieniowe współbieżności.|
|[CurrentScheduler, klasa](currentscheduler-class.md)|Reprezentuje abstrakcję bieżącego harmonogramu skojarzonego z kontekstem wywołującym.|
|[default_scheduler_exists, klasa](default-scheduler-exists-class.md)|Ta klasa opisuje wyjątek zgłoszony w przypadku wywołania metody `Scheduler::SetDefaultSchedulerPolicy`, gdy domyślny harmonogram już istnieje w ramach procesu.|
|[event, klasa](event-class.md)|Zdarzenie resetowania ręcznego, które jest jawnie świadome środowisko uruchomieniowe współbieżności.|
|[improper_lock, klasa](improper-lock-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy blokada jest pobrana nieprawidłowo.|
|[improper_scheduler_attach, klasa](improper-scheduler-attach-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Attach` jest wywoływana w obiekcie `Scheduler`, który jest już dołączony do bieżącego kontekstu.|
|[improper_scheduler_detach, klasa](improper-scheduler-detach-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy metoda `CurrentScheduler::Detach` jest wywoływana w kontekście, który nie został dołączony do żadnego harmonogramu przy użyciu metody `Attach` obiektu `Scheduler`.|
|[improper_scheduler_reference, klasa](improper-scheduler-reference-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Reference` jest wywoływana w obiekcie `Scheduler`, który jest zamykany, z kontekstu, który nie jest częścią tego harmonogramu.|
|[invalid_link_target, klasa](invalid-link-target-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy wywoływana jest metoda `link_target` bloku komunikatów, a blok komunikatów nie może połączyć się z obiektem docelowym. Może to wynikać z przekroczenia liczby linków, do których blok komunikatów jest dozwolony, lub próba łączenia określonego elementu docelowego dwa razy do tego samego źródła.|
|[invalid_multiple_scheduling, klasa](invalid-multiple-scheduling-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `task_handle` obiektu jest zaplanowana wiele razy przy użyciu metody `run` obiektu `task_group` lub `structured_task_group` bez wywoływania wywołującego metody `wait` lub `run_and_wait`.|
|[invalid_operation, klasa](invalid-operation-class.md)|Ta klasa opisuje wyjątek zgłoszony w przypadku wykonania nieprawidłowej operacji, która nie jest dokładniej opisana przez inny typ wyjątku zgłoszony przez środowisko uruchomieniowe współbieżności.|
|[invalid_oversubscribe_operation, klasa](invalid-oversubscribe-operation-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy metoda `Context::Oversubscribe` jest wywoływana z parametrem `_BeginOversubscription` ustawionym na `false` bez wcześniejszego wywołania metody `Context::Oversubscribe` z parametrem `_BeginOversubscription` ustawionym na `true`.|
|[invalid_scheduler_policy_key, klasa](invalid-scheduler-policy-key-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy nieprawidłowy lub nieznany klucz jest przesyłany do konstruktora obiektu `SchedulerPolicy` lub metoda `SetPolicyValue` obiektu `SchedulerPolicy` jest przenoszona jako klucz, który należy zmienić przy użyciu innych metod, takich jak Metoda `SetConcurrencyLimits`.|
|[invalid_scheduler_policy_thread_specification, klasa](invalid-scheduler-policy-thread-specification-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy podejmowana jest próba ustawienia limitów współbieżności obiektu `SchedulerPolicy` w taki sposób, że wartość klucza `MinConcurrency` jest mniejsza niż wartość klucza `MaxConcurrency`.|
|[invalid_scheduler_policy_value, klasa](invalid-scheduler-policy-value-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy klucz zasad obiektu `SchedulerPolicy` jest ustawiony na nieprawidłową wartość dla tego klucza.|
|[ISource, klasa](isource-class.md)|Klasa `ISource` jest interfejsem dla wszystkich bloków źródłowych. Bloki źródłowe propagują komunikaty do bloków `ITarget`.|
|[ITarget, klasa](itarget-class.md)|Klasa `ITarget` jest interfejsem dla wszystkich bloków docelowych. Bloki docelowe zużywają komunikaty oferowane przez `ISource` bloków.|
|[join, klasa](join-class.md)|Blok komunikatów `join` to Jednoelementowy, uporządkowany `propagator_block`, który łączy razem komunikaty typu `T` z każdego ze źródeł.|
|[location, klasa](location-class.md)|Abstrakcja fizycznej lokalizacji na sprzęcie.|
|[message, klasa](message-class.md)|Podstawowa koperta komunikatów zawierająca ładunek danych przesyłanych między blokami obsługi komunikatów.|
|[message_not_found, klasa](message-not-found-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy blok komunikatów nie może znaleźć żądanego komunikatu.|
|[message_processor, klasa](message-processor-class.md)|Klasa `message_processor` jest abstrakcyjną klasą bazową do przetwarzania obiektów `message`. Nie ma gwarancji dotyczącej kolejności komunikatów.|
|[missing_wait, klasa](missing-wait-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy istnieją zadania, które są nadal zaplanowane do `task_group` lub `structured_task_group` obiektu w czasie wykonywania destruktora obiektu. Ten wyjątek nigdy nie zostanie wygenerowany, jeśli destruktor zostanie osiągnięty z powodu odwinięcia stosu w wyniku wyjątku.|
|[multi_link_registry, klasa](multi-link-registry-class.md)|Obiekt `multi_link_registry` jest `network_link_registry`, który zarządza wieloma blokami źródłowymi lub wieloma blokami docelowymi.|
|[multitype_join, klasa](multitype-join-class.md)|Blok komunikatów `multitype_join` to wieloźródłowy blok komunikatów z pojedynczym miejscem, który łączy połączenia różnych typów z poszczególnych źródeł i oferuje spójną kolekcję komunikatów z obiektami docelowymi.|
|[nested_scheduler_missing_detach, klasa](nested-scheduler-missing-detach-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy środowisko uruchomieniowe współbieżności wykryje, że wywołała metodę `CurrentScheduler::Detach` w kontekście dołączonym do drugiego harmonogramu przy użyciu metody `Attach` obiektu `Scheduler`.|
|[network_link_registry, klasa](network-link-registry-class.md)|Abstrakcyjna klasa bazowa `network_link_registry` zarządza łączami między blokami źródłowymi i docelowymi.|
|[operation_timed_out, klasa](operation-timed-out-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy upłynął limit czasu operacji.|
|[ordered_message_processor, klasa](ordered-message-processor-class.md)|`ordered_message_processor` to `message_processor`, która umożliwia blokom komunikatów przetwarzanie komunikatów w kolejności, w jakiej zostały odebrane.|
|[overwrite_buffer, klasa](overwrite-buffer-class.md)|Blok komunikatów `overwrite_buffer` to wiele obiektów, które mają uporządkowane `propagator_block` z możliwością jednoczesnego przechowywania pojedynczej wiadomości. Nowe wiadomości zastępują wcześniej przechowywane.|
|[progress_reporter, klasa](progress-reporter-class.md)|Klasa raportów postępu umożliwia raportowanie powiadomień o postępie określonego typu. Każdy obiekt progress_reporter jest powiązany z określoną akcją asynchroniczną lub operacją.|
|[propagator_block, klasa](propagator-block-class.md)|Klasa `propagator_block` jest abstrakcyjną klasą bazową dla bloków komunikatów, które są zarówno źródłowym, jak i docelowym. Łączy ona funkcje obu klas `source_block` i `target_block`.|
|[reader_writer_lock, klasa](reader-writer-lock-class.md)|Blokada modułu zapisywania czytnika z preferencjami dla programu zapisywania z użyciem tylko lokalnego. Blokada przydaje pierwszy dostęp (FIFO) do składników zapisywania i starves w ramach ciągłego ładowania modułów zapisujących.|
|[ScheduleGroup, klasa](schedulegroup-class.md)|Reprezentuje streszczenie dla grupy harmonogramów. Grupy harmonogramu organizują zestaw pokrewnych zadań, które nie mogą być wykonywane równolegle, przez wykonywanie innego zadania w tej samej grupie przed przechodzeniem do innej grupy lub w dowolnym miejscu, przez wykonanie wielu elementów w tej samej grupie Węzeł NUMA lub gniazdo fizyczne.|
|[Scheduler, klasa](scheduler-class.md)|Reprezentuje streszczenie dla środowisko uruchomieniowe współbieżności Scheduler.|
|[scheduler_not_attached, klasa](scheduler-not-attached-class.md)|Ta klasa opisuje wyjątek zgłoszony podczas wykonywania operacji, który wymaga dołączenia harmonogramu do bieżącego kontekstu, a jeden nie jest.|
|[scheduler_resource_allocation_error, klasa](scheduler-resource-allocation-error-class.md)|Ta klasa opisuje wyjątek zgłoszony z powodu niepowodzenia uzyskania zasobu krytycznego w środowisko uruchomieniowe współbieżności.|
|[scheduler_worker_creation_error, klasa](scheduler-worker-creation-error-class.md)|Ta klasa opisuje wyjątek zgłoszony z powodu błędu tworzenia kontekstu wykonywania procesu roboczego w środowisko uruchomieniowe współbieżności.|
|[SchedulerPolicy, klasa](schedulerpolicy-class.md)|Klasa `SchedulerPolicy` zawiera zestaw par klucz/wartość, jeden dla każdego elementu zasad, kontrolujący zachowanie wystąpienia harmonogramu.|
|[simple_partitioner, klasa](simple-partitioner-class.md)|Klasa `simple_partitioner` reprezentuje statyczne partycjonowanie zakresu powtarzanego przez `parallel_for`. Program Partitioner dzieli zakres na fragmenty w taki sposób, że każdy fragment ma co najmniej liczbę iteracji określoną przez rozmiar fragmentu.|
|[single_assignment, klasa](single-assignment-class.md)|Blok obsługi komunikatów `single_assignment` to wieloobiektowa, uporządkowana `propagator_block`, która umożliwia przechowywanie pojedynczego `message`jednokrotnego zapisu.|
|[single_link_registry, klasa](single-link-registry-class.md)|Obiekt `single_link_registry` jest `network_link_registry`, który zarządza tylko pojedynczym blokiem źródłowym lub docelowym.|
|[source_block, klasa](source-block-class.md)|Klasa `source_block` jest abstrakcyjną klasą bazową dla bloków tylko do źródła. Klasa zawiera podstawowe funkcje zarządzania łączami oraz typowe kontrole błędów.|
|[source_link_manager, klasa](source-link-manager-class.md)|Obiekt `source_link_manager` zarządza łączami sieci bloku komunikatów do bloków `ISource`.|
|[static_partitioner, klasa](static-partitioner-class.md)|Klasa `static_partitioner` reprezentuje statyczne partycjonowanie zakresu powtarzanego przez `parallel_for`. Partycja dzieli zakres na tyle fragmentów, ile jest dostępnych dla pracowników w źródłowym harmonogramie.|
|[structured_task_group, klasa](structured-task-group-class.md)|Klasa `structured_task_group` reprezentuje wysoce strukturalną kolekcję równoległych zadań. Można kolejkować poszczególne równoległe zadania do `structured_task_group` przy użyciu obiektów `task_handle` i poczekać na ich zakończenie lub anulować grupę zadań przed zakończeniem wykonywania, co spowoduje przerwanie wszystkich zadań, które nie rozpoczęły wykonania.|
|[target_block, klasa](target-block-class.md)|Klasa `target_block` jest abstrakcyjną klasą bazową, która zapewnia podstawowe funkcje zarządzania łączami i sprawdzanie błędów tylko dla bloków docelowych.|
|[task, klasa (środowisko uruchomieniowe współbieżności)](task-class.md)|Biblioteka równoległych wzorców (PPL) — Klasa `task`. Obiekt `task` reprezentuje zadanie, które może być wykonywane asynchronicznie i współbieżnie z innymi zadaniami i równoległą działaniem tworzonym przez algorytmy równoległe w środowisko uruchomieniowe współbieżności. Generuje wynik typu `_ResultType` po pomyślnym zakończeniu. Zadania typu `task<void>` nie generują żadnego wyniku. Zadanie może być odczekane i anulowane niezależnie od innych zadań. Może być również tworzony z innymi zadaniami przy użyciu wzorców kontynuacji (`then`) i sprzężeń (`when_all`) i wyboru (`when_any`).|
|[task_canceled, klasa](task-canceled-class.md)|Ta klasa opisuje wyjątek zgłoszony przez warstwę zadań PPL w celu wymuszenia anulowania bieżącego zadania. Jest on również generowany przez metodę `get()` w [zadaniu](task-class.md)dla anulowanego zadania.|
|[task_completion_event, klasa](task-completion-event-class.md)|Klasa `task_completion_event` pozwala opóźniać wykonywanie zadania do momentu spełnienia warunku lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.|
|[task_continuation_context, klasa](task-continuation-context-class.md)|Klasa `task_continuation_context` pozwala określić, gdzie mają być kontynuowane. Jest to przydatne tylko w przypadku używania tej klasy z poziomu aplikacji platformy UWP. W przypadku aplikacji innych niż środowisko wykonawcze systemu Windows kontekst wykonywania kontynuacji zadania jest określany przez środowisko uruchomieniowe i nie można go konfigurować.|
|[task_group, klasa](task-group-class.md)|Klasa `task_group` reprezentuje kolekcję równoległych zadań, które mogą być oczekiwane lub anulowane.|
|[task_handle, klasa](task-handle-class.md)|Klasa `task_handle` reprezentuje pojedynczy równoległy element roboczy. Hermetyzuje instrukcje i dane wymagane do wykonania zadania.|
|[task_options, klasa (środowisko uruchomieniowe współbieżności)](task-options-class-concurrency-runtime.md)|Reprezentuje dozwolone opcje tworzenia zadania|
|[timer, klasa](timer-class.md)|Blok komunikatów `timer` jest `source_block`, który umożliwia wysyłanie wiadomości do jej obiektu docelowego po upływie określonego czasu lub w określonych odstępach czasu.|
|[transformer, klasa](transformer-class.md)|Blok komunikatów `transformer` to Jednoelementowy, uporządkowany `propagator_block`, który może akceptować komunikaty jednego typu, i umożliwia przechowywanie nieograniczonej liczby komunikatów innego typu.|
|[unbounded_buffer, klasa](unbounded-buffer-class.md)|Blok komunikatów `unbounded_buffer` to wiele obiektów, które mają uporządkowane `propagator_block` z możliwością przechowywania nieograniczonej liczby komunikatów.|
|[unsupported_os, klasa](unsupported-os-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy używany jest nieobsługiwany system operacyjny.|

### <a name="structures"></a>Struktury

|Name (Nazwa)|Opis|
|----------|-----------------|
|[DispatchState, struktura](dispatchstate-structure.md)|Struktura `DispatchState` jest używana do transferowania stanu do metody `IExecutionContext::Dispatch`. Opisano w nim sytuacje, w których Metoda `Dispatch` jest wywoływana w interfejsie `IExecutionContext`.|
|[IExecutionContext, struktura](iexecutioncontext-structure.md)|Interfejs do kontekstu wykonywania, który może być uruchamiany w danym procesorze wirtualnym i być przełączany w ramach współdziałania z podsiecią.|
|[IExecutionResource, struktura](iexecutionresource-structure.md)|Abstrakcja wątku sprzętowego.|
|[IResourceManager, struktura](iresourcemanager-structure.md)|Interfejs Menedżer zasobów środowisko uruchomieniowe współbieżności. Jest to interfejs, za pomocą którego harmonogramy komunikują się z Menedżer zasobów.|
|[IScheduler, struktura](ischeduler-structure.md)|Interfejs do abstrakcji harmonogramu pracy. Menedżer zasobów środowisko uruchomieniowe współbieżności używa tego interfejsu do komunikowania się z harmonogramami służbowymi.|
|[ISchedulerProxy, struktura](ischedulerproxy-structure.md)|Interfejs, za pomocą którego program Schedules komunikuje się z Menedżer zasobów środowisko uruchomieniowe współbieżności w celu negocjowania alokacji zasobów.|
|[IThreadProxy, struktura](ithreadproxy-structure.md)|Abstrakcja wątku wykonania. W zależności od klucza zasad `SchedulerType` utworzonego przez użytkownika harmonogramu Menedżer zasobów przyznaje Ci wątek proxy wątku, który jest obsługiwany przez zwykły wątek Win32 lub wątek harmonogramie (UMS) w trybie użytkownika. Wątki UMS są obsługiwane w 64-bitowych systemach operacyjnych z wersją Windows 7 i nowszą.|
|[ITopologyExecutionResource, struktura](itopologyexecutionresource-structure.md)|Interfejs do zasobu wykonywania określony przez Menedżer zasobów.|
|[ITopologyNode, struktura](itopologynode-structure.md)|Interfejs do węzła topologii zdefiniowany przez Menedżer zasobów. Węzeł zawiera jeden lub więcej zasobów wykonawczych.|
|[IUMSCompletionList, struktura](iumscompletionlist-structure.md)|Reprezentuje listę uzupełniania UMS. Po zablokowaniu wątku UMS, wyznaczoną w harmonogramie kontekst planowania jest wysyłany w celu podjęcia decyzji o tym, co należy zaplanować na źródłowym głównym procesorze wirtualnym, gdy oryginalny wątek jest zablokowany. Gdy oryginalny wątek zostanie odblokowany, system operacyjny kolejkuje go do listy uzupełniania dostępnej za pomocą tego interfejsu. Harmonogram może wysyłać zapytania do listy uzupełniania w wydzielonym kontekście planowania lub innym miejscu, w którym szuka pracy.|
|[IUMSScheduler, struktura](iumsscheduler-structure.md)|Interfejs służący do abstrakcji harmonogramu pracy, który chce, aby środowisko uruchomieniowe współbieżności Menedżer zasobów do harmonogramie wątków w trybie użytkownika (UMS). Menedżer zasobów używa tego interfejsu do komunikowania się z harmonogramami wątków UMS. Interfejs `IUMSScheduler` dziedziczy po interfejsie `IScheduler`.|
|[IUMSThreadProxy, struktura](iumsthreadproxy-structure.md)|Abstrakcja wątku wykonania. Jeśli chcesz, aby harmonogram przyznał wątki harmonogramie (UMS), ustaw wartość dla elementu zasad harmonogramu `SchedulerKind` na `UmsThreadDefault`i zaimplementuj interfejs `IUMSScheduler`. Wątki UMS są obsługiwane tylko w 64-bitowych systemach operacyjnych z wersją Windows 7 i nowszą.|
|[IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)|Reprezentuje powiadomienie z Menedżer zasobów, że serwer proxy wątku, który został zablokowany i wyzwolony powrót do wyznaczonego kontekstu planowania harmonogramu został odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, gdy kontekst wykonywania skojarzony z serwerem proxy wątku zwrócony przez metodę `GetContext` jest ponownie zaplanowany.|
|[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)|Abstrakcja wątku sprzętowego, w którym może być wykonywany serwer proxy wątku.|
|[scheduler_interface, struktura](scheduler-interface-structure.md)|Interfejs usługi Scheduler|
|[scheduler_ptr, struktura (środowisko uruchomieniowe współbieżności)](scheduler-ptr-structure-concurrency-runtime.md)|Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje, aby zezwolić na specyfikację wspólnego okresu istnienia przy użyciu shared_ptr lub tylko zwykłego odwołania przy użyciu wskaźnika RAW.|

### <a name="enumerations"></a>Wyliczenia

|Name (Nazwa)|Opis|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|Prawidłowe Stany `agent`.|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanej przez bibliotekę agentów|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanej przez środowisko uruchomieniowe współbieżności.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Flagi śledzenia dla typów zdarzeń|
|[CriticalRegionType —](concurrency-namespace-enums.md#criticalregiontype)|Typ regionu krytycznego, w którym znajduje się kontekst.|
|[DynamicProgressFeedbackType —](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Używane przez zasady `DynamicProgressFeedback` do opisywania, czy zasoby dla harmonogramu będą ponownie równoważone zgodnie z informacjami statystycznymi zebranymi na podstawie harmonogramu, czy tylko na podstawie procesorów wirtualnych przechodzących i z stanu bezczynności przez wywołania do `Activate` i `Deactivate` metod w interfejsie `IVirtualProcessorRoot`. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|
|[join_type](concurrency-namespace-enums.md#join_type)|Typ bloku komunikatów `join`.|
|[message_status](concurrency-namespace-enums.md#message_status)|Prawidłowe odpowiedzi dla oferty `message` obiektu na blok.|
|[PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey)|Klucze zasad opisujące aspekty zachowania usługi Scheduler. Każdy element zasad jest opisywany przez parę klucz-wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływu na harmonogramy, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|
|[SchedulerType —](concurrency-namespace-enums.md#schedulertype)|Używane przez zasady `SchedulerKind` do opisywania typu wątków, których harmonogram ma używać dla podstawowych kontekstów wykonywania. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|
|[SchedulingProtocolType —](concurrency-namespace-enums.md#schedulingprotocoltype)|Używane przez zasady `SchedulingProtocol` do opisywania, który algorytm planowania będzie używany do harmonogramu. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|
|[SwitchingProxyState —](concurrency-namespace-enums.md#switchingproxystate)|Służy do oznaczania stanu, w którym znajduje się serwer proxy wątku, gdy wykonuje przełączenie kontekstu do innego serwera proxy wątku.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Opisuje stan wykonywania obiektu `task_group` lub `structured_task_group`. Wartość tego typu jest zwracana przez wiele metod, które oczekują na ukończenie zadań zaplanowanych dla grupy zadań.|
|[WinRTInitializationType —](concurrency-namespace-enums.md#winrtinitializationtype)|Używane przez zasady `WinRTInitialization` do opisywania, czy i w jaki sposób środowisko wykonawcze systemu Windows zostanie zainicjowany w wątkach usługi Scheduler dla aplikacji działającej w systemach operacyjnych z wersją systemu Windows 8 lub nowszą. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|

### <a name="functions"></a>Funkcje

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Alloc — funkcja](concurrency-namespace-functions.md#alloc)|Przydziela blok pamięci o rozmiarze określonym na podstawie podprzydziału buforowania środowisko uruchomieniowe współbieżności.|
|[asend, funkcja](concurrency-namespace-functions.md#asend)|Przeciążone. Asynchroniczna operacja wysyłania, która planuje zadanie propagacji danych do docelowego bloku.|
|[Funkcja cancel_current_task](concurrency-namespace-functions.md#cancel_current_task)|Anuluje aktualnie wykonywane zadanie. Ta funkcja może zostać wywołana z poziomu treści zadania, aby przerwać wykonywanie zadania i spowodować, że będzie ona wprowadzać stan `canceled`.<br /><br /> Nie jest to obsługiwany scenariusz do wywołania tej funkcji, jeśli nie znajdujesz się w treści `task`. Wykonanie tej czynności spowoduje niezdefiniowane zachowanie, takie jak awaria lub zawieszenie aplikacji.|
|[Funkcja create_async](concurrency-namespace-functions.md#create_async)|Tworzy środowisko wykonawcze systemu Windows asynchronicznej na podstawie podanego przez użytkownika obiektu lambda lub funkcji. Zwracany typ `create_async` jest jedną z `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`lub `IAsyncOperationWithProgress<TResult, TProgress>^` na podstawie podpisu wyrażenia lambda przekazaną do metody.|
|[Funkcja create_task](concurrency-namespace-functions.md#create_task)|Przeciążone. Tworzy obiekt [zadania](task-class.md) PPL. `create_task` można używać wszędzie tam, gdzie użyto konstruktora zadań. Jest ona świadczona głównie dla wygody, ponieważ umożliwia użycie słowa kluczowego `auto` podczas tworzenia zadań.|
|[Serviceresourcemanager — funkcja](concurrency-namespace-functions.md#createresourcemanager)|Zwraca interfejs, który reprezentuje pojedyncze wystąpienie Menedżer zasobów środowisko uruchomieniowe współbieżności. Menedżer zasobów jest odpowiedzialny za przypisywanie zasobów do harmonogramów, które chcą współpracować ze sobą.|
|[DisableTracing —, funkcja](concurrency-namespace-functions.md#disabletracing)|Wyłącza śledzenie w środowisko uruchomieniowe współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest domyślnie wyrejestrowane.|
|[EnableTracing —, funkcja](concurrency-namespace-functions.md#enabletracing)|Włącza śledzenie w środowisko uruchomieniowe współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest teraz domyślnie włączone.|
|[Free — funkcja](concurrency-namespace-functions.md#free)|Zwalnia blok pamięci, który został wcześniej przydzielony przez metodę `Alloc` do podprzydzielania środowisko uruchomieniowe współbieżności buforowania.|
|[Funkcja get_ambient_scheduler (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId —, funkcja](concurrency-namespace-functions.md#getexecutioncontextid)|Zwraca unikatowy identyfikator, który można przypisać do kontekstu wykonywania implementującego interfejs `IExecutionContext`.|
|[GetOSVersion —, funkcja](concurrency-namespace-functions.md#getosversion)|Zwraca wersję systemu operacyjnego.|
|[GetProcessorCount —, funkcja](concurrency-namespace-functions.md#getprocessorcount)|Zwraca liczbę wątków sprzętowych w źródłowym systemie.|
|[GetProcessorNodeCount —, funkcja](concurrency-namespace-functions.md#getprocessornodecount)|Zwraca liczbę węzłów NUMA lub pakietów procesorów w źródłowym systemie.|
|[GetSchedulerId —, funkcja](concurrency-namespace-functions.md#getschedulerid)|Zwraca unikatowy identyfikator, który można przypisać do harmonogramu implementującego interfejs `IScheduler`.|
|[Funkcja interruption_point](concurrency-namespace-functions.md#interruption_point)|Tworzy punkt przerwania do anulowania. Jeśli anulowanie jest w toku w kontekście, w którym ta funkcja jest wywoływana, spowoduje to zgłoszenie wyjątku wewnętrznego, który przerywa wykonywanie aktualnie wykonywanej pracy równoległej. Jeśli anulowanie nie jest w toku, funkcja nic nie robi.|
|[Funkcja is_current_task_group_canceling](concurrency-namespace-functions.md#is_current_task_group_canceling)|Zwraca wskazanie, czy grupa zadań, która jest aktualnie uruchamiana w bieżącym kontekście, znajduje się w pośrodku aktywnego anulowania (lub będzie wkrótce). Należy pamiętać, że jeśli w bieżącym kontekście nie ma obecnie uruchomionej grupy zadań, `false` zostanie zwrócona.|
|[Funkcja make_choice](concurrency-namespace-functions.md#make_choice)|Przeciążone. Konstruuje blok `choice` Messaging z opcjonalnego `Scheduler` lub `ScheduleGroup` oraz co najmniej dwóch źródeł danych wejściowych.|
|[Funkcja make_greedy_join](concurrency-namespace-functions.md#make_greedy_join)|Przeciążone. Konstruuje blok `greedy multitype_join` Messaging z opcjonalnego `Scheduler` lub `ScheduleGroup` oraz co najmniej dwóch źródeł danych wejściowych.|
|[Funkcja make_join](concurrency-namespace-functions.md#make_join)|Przeciążone. Konstruuje blok `non_greedy multitype_join` Messaging z opcjonalnego `Scheduler` lub `ScheduleGroup` oraz co najmniej dwóch źródeł danych wejściowych.|
|[Funkcja make_task](concurrency-namespace-functions.md#make_task)|Metoda fabryki służąca do tworzenia obiektu `task_handle`.|
|[Funkcja parallel_buffered_sort](concurrency-namespace-functions.md#parallel_buffered_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w kolejności niemalejącej lub zgodnie z kryterium porządkowania określonym przez Predykat binarny równolegle. Ta funkcja jest semantycznie podobna do `std::sort` w tym, że jest to porównanie, niestabilne, w miejscu, z wyjątkiem sytuacji, gdy wymaga `O(n)` dodatkowe miejsce, i wymaga domyślnej inicjalizacji dla sortowanych elementów.|
|[Funkcja parallel_for](concurrency-namespace-functions.md#parallel_for)|Przeciążone. `parallel_for` wykonuje iterację w zakresie indeksów i wykonuje funkcję dostarczoną przez użytkownika w każdej iteracji równolegle.|
|[Funkcja parallel_for_each](concurrency-namespace-functions.md#parallel_for_each)|Przeciążone. `parallel_for_each` stosuje określoną funkcję do każdego elementu w obrębie zakresu równolegle. Jest semantycznie odpowiednikiem funkcji `for_each` w przestrzeni nazw `std`, z tą różnicą, że iteracja w elementach jest wykonywana równolegle, a kolejność iteracji nie została określona. Argument `_Func` musi obsługiwać operator wywołania funkcji w formularzu `operator()(T)` gdzie `T` jest typem elementu kontenera, w którym jest wykonywane powtarzanie.|
|[Funkcja parallel_invoke](concurrency-namespace-functions.md#parallel_invoke)|Przeciążone. Wykonuje obiekty funkcji dostarczone jako parametry równolegle i bloki do momentu zakończenia wykonywania. Każdy obiekt funkcji może być wyrażeniem lambda, wskaźnikiem do funkcji lub dowolnym obiektem, który obsługuje operator wywołania funkcji z sygnaturą `void operator()()`.|
|[Funkcja parallel_radixsort](concurrency-namespace-functions.md#parallel_radixsort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności przy użyciu algorytmu sortowania podstawy. Jest to stabilna funkcja sortowania, która wymaga funkcji projekcji, która może projektować elementy do posortowania na klucze podobne do liczby całkowitej. Dla elementów, które są sortowane, wymagana jest Inicjalizacja domyślna.|
|[Funkcja parallel_reduce](concurrency-namespace-functions.md#parallel_reduce)|Przeciążone. Oblicza sumę wszystkich elementów w określonym zakresie przez Obliczanie kolejnych sum częściowych lub oblicza wynik kolejnych częściowe wyniki, podobnie jak w przypadku użycia określonej operacji binarnej innej niż suma, równolegle. `parallel_reduce` jest semantycznie podobna do `std::accumulate`, z tą różnicą, że wymaga skojarzenia operacji binarnej i wymaga wartości tożsamości zamiast początkowej wartości.|
|[Funkcja parallel_sort](concurrency-namespace-functions.md#parallel_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w kolejności niemalejącej lub zgodnie z kryterium porządkowania określonym przez Predykat binarny równolegle. Ta funkcja jest semantycznie podobna do `std::sort` w tym, że jest to porównanie, niestabilne i w miejscu.|
|[Funkcja parallel_transform](concurrency-namespace-functions.md#parallel_transform)|Przeciążone. Stosuje określony obiekt Function do każdego elementu w zakresie źródłowym lub do pary elementów z dwóch zakresów źródłowych i kopiuje wartości zwracane obiektu Function do zakresu docelowego równolegle. Ta funkcjonalność jest semantycznie równoważna z `std::transform`.|
|[Funkcja Receive](concurrency-namespace-functions.md#receive)|Przeciążone. Ogólna implementacja odbierania, która zezwala na kontekst oczekiwania na dane z dokładnie jednego źródła i filtruje akceptowane wartości.|
|[Funkcja run_with_cancellation_token](concurrency-namespace-functions.md#run_with_cancellation_token)|Wykonuje obiekt funkcji natychmiast i synchronicznie w kontekście danego tokenu anulowania.|
|[send — Funkcja](concurrency-namespace-functions.md#send)|Przeciążone. Synchroniczna operacja wysyłania, która czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat.|
|[Funkcja set_ambient_scheduler (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[Funkcja set_task_execution_resources](concurrency-namespace-functions.md#set_task_execution_resources)|Przeciążone. Ogranicza zasoby wykonywania używane przez środowisko uruchomieniowe współbieżności wewnętrznych wątków roboczych do określonego zestawu koligacji.<br /><br /> Ta metoda jest prawidłowa do wywołania tej metody tylko przed utworzeniem Menedżer zasobów lub między dwoma Menedżer zasobów okresów istnienia. Może być wywoływana wiele razy, dopóki Menedżer zasobów nie istnieje w czasie wywołania. Po ustawieniu limitu koligacji nadal obowiązuje do następnego prawidłowego wywołania metody `set_task_execution_resources`.<br /><br /> Podana maska koligacji nie musi być podzbiorem maski koligacji procesu. Koligacja procesu będzie aktualizowana w razie potrzeby.|
|[Swap — Funkcja](concurrency-namespace-functions.md#swap)|Wymienia elementy dwóch `concurrent_vector` obiektów.|
|[Funkcja task_from_exception (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#task_from_exception)||
|[Funkcja task_from_result (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#task_from_result)||
|[Funkcja Trace_agents_register_name](concurrency-namespace-functions.md#trace_agents_register_name)|Kojarzy daną nazwę z blokiem komunikatów lub agentem w śledzeniu ETW.|
|[Funkcja try_receive](concurrency-namespace-functions.md#try_receive)|Przeciążone. Ogólna implementacja try-Receive, umożliwiająca kontekstowi wyszukiwanie danych z dokładnie jednego źródła i filtrowanie wartości, które są akceptowane. Jeśli dane nie są gotowe, metoda zwróci wartość false.|
|[wait — Funkcja](concurrency-namespace-functions.md#wait)|Wstrzymuje bieżący kontekst przez określony czas.|
|[Funkcja when_all](concurrency-namespace-functions.md#when_all)|Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.|
|[Funkcja when_any](concurrency-namespace-functions.md#when_any)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.|

### <a name="operators"></a>Operatory

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora nie jest równy obiektowi `concurrent_vector` po prawej stronie.|
|[& operatora &](concurrency-namespace-operators.md#operator_amp_amp)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy oba zadania dostarczone jako argumenty zakończą się pomyślnie.|
|[zakład&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy jedno z zadań dostarczonych jako argumenty zakończy się pomyślnie.|
|[< operatora](concurrency-namespace-operators.md#operator_lt)|Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest mniejszy niż obiekt `concurrent_vector` po prawej stronie.|
|[< operatora =](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest mniejszy niż lub równy obiektowi `concurrent_vector` po prawej stronie.|
|[operator = =](concurrency-namespace-operators.md#operator_eq_eq)|Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest równy obiektowi `concurrent_vector` po prawej stronie.|
|[> operatora](concurrency-namespace-operators.md#operator_gt)|Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest większy niż obiekt `concurrent_vector` po prawej stronie.|
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, czy obiekt `concurrent_vector` po lewej stronie operatora jest większy niż lub równy obiektowi `concurrent_vector` po prawej stronie.|

### <a name="constants"></a>{1&gt;Stałe&lt;1}

|Name (Nazwa)|Opis|
|----------|-----------------|
|[AgentEventGuid —](concurrency-namespace-constants1.md#agenteventguid)|Identyfikator GUID kategorii ({B9B5B78C-0713-4898-A21A-C67949DCED07}) opisujący zdarzenia ETW wywoływane przez bibliotekę agentów w środowisko uruchomieniowe współbieżności.|
|[ChoreEventGuid —](concurrency-namespace-constants1.md#choreeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z zadaniami lub zadań.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Identyfikator GUID dostawcy ETW dla środowisko uruchomieniowe współbieżności.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Wskazuje obsługę interfejsu Menedżer zasobów zdefiniowanego w programie Visual Studio 2010.|
|[ConcRTEventGuid —](concurrency-namespace-constants1.md#concrteventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które nie są dokładniej opisane przez inną kategorię.|
|[ContextEventGuid —](concurrency-namespace-constants1.md#contexteventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio powiązane z kontekstami.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Wartość wskazująca, że oczekiwania nigdy nie powinien przekraczać limitu czasu.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Wartość wskazująca, że upłynął limit czasu oczekiwania.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Specjalna wartość dla klucza zasad `ContextPriority` wskazujący, że priorytet wątku dla wszystkich kontekstów w harmonogramie powinien być taki sam jak w przypadku wątku, który utworzył harmonogram.|
|[LockEventGuid —](concurrency-namespace-constants1.md#lockeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio powiązane z blokadami.|
|[MaxExecutionResources —](concurrency-namespace-constants1.md#maxexecutionresources)|Specjalna wartość dla kluczy zasad `MinConcurrency` i `MaxConcurrency`. Wartość domyślna to liczba wątków sprzętowych na komputerze w przypadku braku innych ograniczeń.|
|[PPLParallelForeachEventGuid —](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użyciem funkcji `parallel_for_each`.|
|[PPLParallelForEventGuid —](concurrency-namespace-constants1.md#pplparallelforeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użyciem funkcji `parallel_for`.|
|[PPLParallelInvokeEventGuid —](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użyciem funkcji `parallel_invoke`.|
|[ResourceManagerEventGuid —](concurrency-namespace-constants1.md#resourcemanagereventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio powiązane z Menedżerem zasobów.|
|[ScheduleGroupEventGuid —](concurrency-namespace-constants1.md#schedulegroupeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z grupami harmonogramu.|
|[SchedulerEventGuid —](concurrency-namespace-constants1.md#schedulereventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z działaniem usługi Scheduler.|
|[VirtualProcessorEventGuid —](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z procesorami wirtualnymi.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h, ConcRT. h, concrtrm. h, concurrent_priority_queue. h, concurrent_queue. h, concurrent_unordered_map. h, concurrent_unordered_set. h, concurrent_vector. h, internal_concurrent_hash. h, internal_split_ordered_list. h, PPL. h, pplcancellation_token. h, pplconcrt. h, pplinterface. h, ppltasks. h

## <a name="see-also"></a>Zobacz też

[Dokumentacja](reference-concurrency-runtime.md)
