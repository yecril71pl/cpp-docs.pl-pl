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
ms.openlocfilehash: 66c2e6e323ed9f12f30e9392ec7afe431fc2138b
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446743"
---
# <a name="concurrency-namespace"></a>concurrency — Przestrzeń nazwy

`Concurrency`Przestrzeń nazw zawiera klasy i funkcje, które zapewniają dostęp do środowisko uruchomieniowe współbieżności, współbieżne środowisko programistyczne dla języka C++. Aby uzyskać więcej informacji, zobacz [środowisko uruchomieniowe współbieżności](../../../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Składnia

```cpp
namespace concurrency;
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`runtime_object_identity`|Każde wystąpienie komunikatu ma tożsamość, która następuje po jej sklonowaniu i przekazaniu między składnikami obsługi komunikatów. Nie może to być adres obiektu wiadomości.|
|`task_status`|Typ, który reprezentuje stan terminalu zadania. Prawidłowe wartości to `completed` i `canceled` .|
|`TaskProc`|Podstawowe streszczenie dla zadania, zdefiniowane jako `void (__cdecl * TaskProc)(void *)` . `TaskProc`Jest wywoływana, aby wywołać treść zadania.|
|`TaskProc_t`|Podstawowe streszczenie dla zadania, zdefiniowane jako `void (__cdecl * TaskProc_t)(void *)` . `TaskProc`Jest wywoływana, aby wywołać treść zadania.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|----------|-----------------|
|[Klasa affinity_partitioner](affinity-partitioner-class.md)|`affinity_partitioner`Klasa jest podobna do `static_partitioner` klasy, ale zwiększa koligację pamięci podręcznej przez wybór zakresu mapowania na wątki robocze. Może znacząco poprawić wydajność, gdy pętla jest ponownie wykonywana nad tym samym zestawem danych, a dane pasują do pamięci podręcznej. Należy zauważyć, że ten sam `affinity_partitioner` obiekt musi być używany z kolejnymi iteracjami pętli równoległej, która jest wykonywana w określonym zestawie danych, aby można było skorzystać z lokalizacji danych.|
|[Agent — Klasa](agent-class.md)|Klasa przeznaczona do użycia jako klasa bazowa dla wszystkich niezależnych agentów. Służy do ukrycia stanu od innych agentów i korzystania z przekazywania komunikatów.|
|[Klasa auto_partitioner](auto-partitioner-class.md)|`auto_partitioner`Klasa reprezentuje metodę domyślną `parallel_for` `parallel_for_each` i `parallel_transform` służy do partycjonowania zakresu, w którym się powtarza. Ta metoda partycjonowania wykorzystuje funkcję kradzieży zakresu na potrzeby równoważenia obciążenia, a także anulowania dla iteracji.|
|[Klasa bad_target](bad-target-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy blok komunikatów otrzymuje wskaźnik do obiektu docelowego, który jest nieprawidłowy dla wykonywanej operacji.|
|[Call, Klasa](call-class.md)|`call`Blok komunikatów to wiele źródeł uporządkowane, `target_block` które wywołuje określoną funkcję podczas otrzymywania wiadomości.|
|[Klasa cancellation_token](cancellation-token-class.md)|`cancellation_token`Klasa reprezentuje możliwość ustalenia, czy żądanie zostało anulowane przez pewne operacje. Dany token może być skojarzony z `task_group` , `structured_task_group` lub `task` w celu zapewnienia niejawnego anulowania. Może być również sondowany w celu anulowania lub mieć zarejestrowane wywołanie zwrotne dla if i po `cancellation_token_source` anulowaniu skojarzonego elementu.|
|[Klasa cancellation_token_registration](cancellation-token-registration-class.md)|`cancellation_token_registration`Klasa reprezentuje powiadomienie wywołania zwrotnego z `cancellation_token` . Gdy `register` Metoda w `cancellation_token` jest używana do otrzymywania powiadomień o wystąpieniu anulowania, `cancellation_token_registration` obiekt jest zwracany jako dojście do wywołania zwrotnego, aby obiekt wywołujący mógł zażądać określonego wywołania zwrotnego za pomocą `deregister` metody.|
|[Klasa cancellation_token_source](cancellation-token-source-class.md)|`cancellation_token_source`Klasa reprezentuje możliwość anulowania niektórych operacji do anulowania.|
|[Choice — Klasa](choice-class.md)|`choice`Blok komunikatów jest blokiem pojedynczego źródła, który reprezentuje interakcję przepływu sterowania z zestawem źródeł. Blok wyboru czeka na jedno z wielu źródeł, aby utworzyć komunikat i propaguje indeks źródła, który wygenerował komunikat.|
|[Klasa z kombinacją](combinable-class.md)|`combinable<T>`Obiekt jest przeznaczony do dostarczania prywatnych kopii wątku danych w celu wykonania niezależnych od siebie podobliczeń wątku podczas równoległych algorytmów. Na końcu operacji równoległej podobliczenia wątku i prywatnego mogą zostać następnie scalone w wynik końcowy. Ta klasa może być używana zamiast zmiennej udostępnionej i może skutkować zwiększeniem wydajności, jeśli w przeciwnym razie będzie wiele rywalizacji dotyczących tej zmiennej udostępnionej.|
|[Klasa concurrent_priority_queue](concurrent-priority-queue-class.md)|`concurrent_priority_queue`Klasa jest kontenerem, który umożliwia wielu wątkom równoczesne wypychanie i wypunktowanie elementów. Elementy są zdjęte w kolejności priorytetu, gdzie priorytet jest określany przez Funktor dostarczone jako argument szablonu.|
|[Klasa concurrent_queue](concurrent-queue-class.md)|`concurrent_queue`Klasa jest klasą kontenera sekwencji, która umożliwia pierwszy i pierwszy dostęp do jego elementów. Umożliwia ograniczony zestaw operacji związanych z współbieżnością, takich jak `push` i `try_pop` .|
|[Klasa concurrent_unordered_map](concurrent-unordered-map-class.md)|`concurrent_unordered_map`Klasa jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>` . Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne wykonywanie operacji dołączania, dostęp do elementów, dostęp iteratora i przechodzenie iteratora.|
|[Klasa concurrent_unordered_multimap](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap`Klasa jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>` . Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[Klasa concurrent_unordered_multiset](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset`Klasa jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[Klasa concurrent_unordered_set](concurrent-unordered-set-class.md)|`concurrent_unordered_set`Klasa jest bezpiecznym pod kątem współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[Klasa concurrent_vector](concurrent-vector-class.md)|`concurrent_vector`Klasa jest klasą kontenera sekwencji, która umożliwia losowy dostęp do dowolnego elementu. Umożliwia ona bezpieczne łączenie, dostęp do elementów, dostęp iteratora i operacje przechodzenia iteratora.|
|[Context — Klasa](context-class.md)|Reprezentuje streszczenie dla kontekstu wykonania.|
|[Klasa context_self_unblock](context-self-unblock-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `Unblock` Metoda `Context` obiektu jest wywoływana z tego samego kontekstu. Spowoduje to wskazanie próby odblokowania przez dany kontekst.|
|[Klasa context_unblock_unbalanced](context-unblock-unbalanced-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy wywołania `Block` `Unblock` metod i `Context` obiektu nie są prawidłowo sparowane.|
|[Klasa critical_section](critical-section-class.md)|Niewspółpracujący obiekt mutex, który jest jawnie świadomy środowisko uruchomieniowe współbieżności.|
|[Klasa CurrentScheduler](currentscheduler-class.md)|Reprezentuje abstrakcję bieżącego harmonogramu skojarzonego z kontekstem wywołującym.|
|[Klasa default_scheduler_exists](default-scheduler-exists-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `Scheduler::SetDefaultSchedulerPolicy` Metoda jest wywoływana, gdy domyślny harmonogram już istnieje w ramach procesu.|
|[Event — Klasa](event-class.md)|Zdarzenie resetowania ręcznego, które jest jawnie świadome środowisko uruchomieniowe współbieżności.|
|[Klasa improper_lock](improper-lock-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy blokada jest pobrana nieprawidłowo.|
|[Klasa improper_scheduler_attach](improper-scheduler-attach-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `Attach` Metoda jest wywoływana w `Scheduler` obiekcie, który jest już dołączony do bieżącego kontekstu.|
|[Klasa improper_scheduler_detach](improper-scheduler-detach-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `CurrentScheduler::Detach` Metoda jest wywoływana w kontekście, który nie został dołączony do żadnego harmonogramu przy użyciu `Attach` metody `Scheduler` obiektu.|
|[Klasa improper_scheduler_reference](improper-scheduler-reference-class.md)|Ta klasa opisuje wyjątek zgłoszony `Reference` , gdy metoda jest wywoływana w obiekcie, `Scheduler` który jest zamykany, z kontekstu, który nie jest częścią tego harmonogramu.|
|[Klasa invalid_link_target](invalid-link-target-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `link_target` wywoływana jest metoda bloku komunikatów i blok komunikatów nie może połączyć się z obiektem docelowym. Może to wynikać z przekroczenia liczby linków, do których blok komunikatów jest dozwolony, lub próba łączenia określonego elementu docelowego dwa razy do tego samego źródła.|
|[Klasa invalid_multiple_scheduling](invalid-multiple-scheduling-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `task_handle` obiekt jest zaplanowany wiele razy przy użyciu `run` metody `task_group` lub `structured_task_group` obiektu bez wywołania wywołującego do albo `wait` `run_and_wait` metody.|
|[Klasa invalid_operation](invalid-operation-class.md)|Ta klasa opisuje wyjątek zgłoszony w przypadku wykonania nieprawidłowej operacji, która nie jest dokładniej opisana przez inny typ wyjątku zgłoszony przez środowisko uruchomieniowe współbieżności.|
|[Klasa invalid_oversubscribe_operation](invalid-oversubscribe-operation-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy `Context::Oversubscribe` Metoda jest wywoływana z `_BeginOversubscription` parametrem ustawionym na `false` bez wcześniejszego wywołania `Context::Oversubscribe` metody z `_BeginOversubscription` parametrem ustawionym na `true` .|
|[Klasa invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy nieprawidłowy lub nieznany klucz jest przesyłany do `SchedulerPolicy` konstruktora obiektów lub `SetPolicyValue` Metoda `SchedulerPolicy` obiektu jest przenoszona jako klucz, który należy zmienić przy użyciu innych metod, takich jak `SetConcurrencyLimits` Metoda.|
|[Klasa invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy podejmowana jest próba ustawienia limitów współbieżności obiektu w `SchedulerPolicy` taki sposób, że wartość `MinConcurrency` klucza jest mniejsza niż wartość `MaxConcurrency` klucza.|
|[Klasa invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy klucz zasad `SchedulerPolicy` obiektu jest ustawiony na nieprawidłową wartość dla tego klucza.|
|[Klasa ISource](isource-class.md)|`ISource`Klasa jest interfejsem dla wszystkich bloków źródłowych. Bloki źródłowe propagują komunikaty do `ITarget` bloków.|
|[Klasa ITarget](itarget-class.md)|`ITarget`Klasa jest interfejsem dla wszystkich bloków docelowych. Bloki docelowe zużywają komunikaty oferowane im przez `ISource` bloki.|
|[join — Klasa](join-class.md)|`join`Blok komunikatów jest jednym z obiektów docelowych, które są uporządkowane, `propagator_block` które łączą komunikaty typu `T` z poszczególnych źródeł.|
|[Location — Klasa](location-class.md)|Abstrakcja fizycznej lokalizacji na sprzęcie.|
|[Message — Klasa](message-class.md)|Podstawowa koperta komunikatów zawierająca ładunek danych przesyłanych między blokami obsługi komunikatów.|
|[Klasa message_not_found](message-not-found-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy blok komunikatów nie może znaleźć żądanego komunikatu.|
|[Klasa message_processor](message-processor-class.md)|`message_processor`Klasa jest abstrakcyjną klasą bazową do przetwarzania `message` obiektów. Nie ma gwarancji dotyczącej kolejności komunikatów.|
|[Klasa missing_wait](missing-wait-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy istnieją zadania, które w dalszym ciągu zaplanowano do `task_group` `structured_task_group` obiektu lub w momencie wykonania destruktora obiektu. Ten wyjątek nigdy nie zostanie wygenerowany, jeśli destruktor zostanie osiągnięty z powodu odwinięcia stosu w wyniku wyjątku.|
|[Klasa multi_link_registry](multi-link-registry-class.md)|`multi_link_registry`Obiekt jest `network_link_registry` zarządza wieloma blokami źródłowymi lub wieloma blokami docelowymi.|
|[Klasa multitype_join](multitype-join-class.md)|`multitype_join`Blok komunikatów to wieloźródłowy blok komunikatów z jednym elementem docelowym, który łączy połączenia różnych typów z poszczególnych źródeł i oferuje spójną kolekcję komunikatów z obiektami docelowymi.|
|[Klasa nested_scheduler_missing_detach](nested-scheduler-missing-detach-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy środowisko uruchomieniowe współbieżności wykryje, że pozostało wywołanie `CurrentScheduler::Detach` metody w kontekście dołączonym do drugiego harmonogramu przy użyciu `Attach` metody `Scheduler` obiektu.|
|[Klasa network_link_registry](network-link-registry-class.md)|`network_link_registry`Abstrakcyjna klasa bazowa zarządza łączami między blokami źródłowymi i docelowymi.|
|[Klasa operation_timed_out](operation-timed-out-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy upłynął limit czasu operacji.|
|[Klasa ordered_message_processor](ordered-message-processor-class.md)|`ordered_message_processor`Jest to element `message_processor` , który umożliwia blokom komunikatów przetwarzanie komunikatów w kolejności, w jakiej zostały odebrane.|
|[Klasa overwrite_buffer](overwrite-buffer-class.md)|`overwrite_buffer`Blok komunikatów to wiele obiektów docelowych, uporządkowanych `propagator_block` z możliwością przechowywania pojedynczej wiadomości w danym momencie. Nowe wiadomości zastępują wcześniej przechowywane.|
|[Klasa progress_reporter](progress-reporter-class.md)|Klasa raportów postępu umożliwia raportowanie powiadomień o postępie określonego typu. Każdy obiekt progress_reporter jest powiązany z określoną akcją asynchroniczną lub operacją.|
|[Klasa propagator_block](propagator-block-class.md)|`propagator_block`Klasa jest abstrakcyjną klasą bazową dla bloków komunikatów, które są zarówno źródłowym, jak i docelowym. Łączy ona funkcje obu `source_block` `target_block` klas i.|
|[Klasa reader_writer_lock](reader-writer-lock-class.md)|Blokada modułu zapisywania czytnika z preferencjami dla programu zapisywania z użyciem tylko lokalnego. Blokada przydaje pierwszy dostęp (FIFO) do składników zapisywania i starves w ramach ciągłego ładowania modułów zapisujących.|
|[Schedule — Klasa](schedulegroup-class.md)|Reprezentuje streszczenie dla grupy harmonogramów. Grupy harmonogramu organizują zestaw pokrewnych zadań, które nie mogą być wykonywane równolegle, przez wykonywanie innego zadania w tej samej grupie przed przechodzeniem do innej grupy lub w dowolnym miejscu, przez wykonanie wielu elementów w tej samej grupie w tym samym węźle NUMA lub gnieździe fizycznym.|
|[Scheduler — Klasa](scheduler-class.md)|Reprezentuje streszczenie dla środowisko uruchomieniowe współbieżności Scheduler.|
|[Klasa scheduler_not_attached](scheduler-not-attached-class.md)|Ta klasa opisuje wyjątek zgłoszony podczas wykonywania operacji, który wymaga dołączenia harmonogramu do bieżącego kontekstu, a jeden nie jest.|
|[Klasa scheduler_resource_allocation_error](scheduler-resource-allocation-error-class.md)|Ta klasa opisuje wyjątek zgłoszony z powodu niepowodzenia uzyskania zasobu krytycznego w środowisko uruchomieniowe współbieżności.|
|[Klasa scheduler_worker_creation_error](scheduler-worker-creation-error-class.md)|Ta klasa opisuje wyjątek zgłoszony z powodu błędu tworzenia kontekstu wykonywania procesu roboczego w środowisko uruchomieniowe współbieżności.|
|[Klasa SchedulerPolicy](schedulerpolicy-class.md)|`SchedulerPolicy`Klasa zawiera zestaw par klucz/wartość, jeden dla każdego elementu zasad, kontrolujący zachowanie wystąpienia harmonogramu.|
|[Klasa simple_partitioner](simple-partitioner-class.md)|`simple_partitioner`Klasa reprezentuje statyczne partycjonowanie zakresu powtarzanego przez `parallel_for` . Program Partitioner dzieli zakres na fragmenty w taki sposób, że każdy fragment ma co najmniej liczbę iteracji określoną przez rozmiar fragmentu.|
|[Klasa single_assignment](single-assignment-class.md)|`single_assignment`Blok komunikatów to wiele obiektów docelowych, uporządkowanych `propagator_block` z możliwością przechowywania jednego, jednokrotnego zapisu `message` .|
|[Klasa single_link_registry](single-link-registry-class.md)|`single_link_registry`Obiekt jest `network_link_registry` , który zarządza tylko pojedynczym blokiem źródłowym lub docelowym.|
|[Klasa source_block](source-block-class.md)|`source_block`Klasa jest abstrakcyjną klasą bazową dla bloków przeznaczonych tylko do źródła. Klasa zawiera podstawowe funkcje zarządzania łączami oraz typowe kontrole błędów.|
|[Klasa source_link_manager](source-link-manager-class.md)|`source_link_manager`Obiekt zarządza łączami sieci bloku komunikatów do `ISource` bloków.|
|[Klasa static_partitioner](static-partitioner-class.md)|`static_partitioner`Klasa reprezentuje statyczne partycjonowanie zakresu powtarzanego przez `parallel_for` . Partycja dzieli zakres na tyle fragmentów, ile jest dostępnych dla pracowników w źródłowym harmonogramie.|
|[Klasa structured_task_group](structured-task-group-class.md)|`structured_task_group`Klasa reprezentuje wysoce strukturalną kolekcję równoległych zadań. Można kolejkować poszczególne równoległe zadania do `structured_task_group` obiektów przy użyciu `task_handle` i zaczekać na ich zakończenie lub anulować grupę zadań przed zakończeniem wykonywania, co spowoduje przerwanie wszystkich zadań, które nie rozpoczęły wykonania.|
|[Klasa target_block](target-block-class.md)|`target_block`Klasa jest abstrakcyjną klasą bazową, która zapewnia podstawowe funkcje zarządzania łączami i sprawdzanie błędów tylko dla bloków docelowych.|
|[Task — Klasa (środowisko uruchomieniowe współbieżności)](task-class.md)|Klasa Parallel wzorców Library (PPL) `task` . `task`Obiekt reprezentuje zadanie, które może być wykonywane asynchronicznie i współbieżnie z innymi zadaniami i równoległą działaniem wytwarzanym przez algorytmy równoległe w środowisko uruchomieniowe współbieżności. Generuje wynik typu `_ResultType` po pomyślnym zakończeniu. Zadania typu `task<void>` nie generują żadnego wyniku. Zadanie może być odczekane i anulowane niezależnie od innych zadań. Może być również tworzony z innymi zadaniami przy użyciu wzorców kontynuacji ( `then` ) i sprzężeń ( `when_all` ) i wyboru ( `when_any` ).|
|[Klasa task_canceled](task-canceled-class.md)|Ta klasa opisuje wyjątek zgłoszony przez warstwę zadań PPL w celu wymuszenia anulowania bieżącego zadania. Jest on również generowany przez `get()` metodę w [zadaniu](task-class.md)dla anulowanego zadania.|
|[Klasa task_completion_event](task-completion-event-class.md)|`task_completion_event`Klasa pozwala opóźnić wykonywanie zadania do momentu spełnienia warunku lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.|
|[Klasa task_continuation_context](task-continuation-context-class.md)|`task_continuation_context`Klasa pozwala określić, gdzie mają być kontynuowane. Jest to przydatne tylko w przypadku używania tej klasy z poziomu aplikacji platformy UWP. W przypadku aplikacji innych niż środowisko wykonawcze systemu Windows kontekst wykonywania kontynuacji zadania jest określany przez środowisko uruchomieniowe i nie można go konfigurować.|
|[Klasa task_group](task-group-class.md)|`task_group`Klasa reprezentuje kolekcję równoległych zadań, które mogą być oczekiwane lub anulowane.|
|[Klasa task_handle](task-handle-class.md)|`task_handle`Klasa reprezentuje pojedynczy równoległy element roboczy. Hermetyzuje instrukcje i dane wymagane do wykonania zadania.|
|[Klasa task_options (środowisko uruchomieniowe współbieżności)](task-options-class-concurrency-runtime.md)|Reprezentuje dozwolone opcje tworzenia zadania|
|[Timer — Klasa](timer-class.md)|`timer`Blok komunikatów to jeden obiekt docelowy, który `source_block` umożliwia wysyłanie wiadomości do jej obiektu docelowego po upływie określonego czasu lub w określonych odstępach czasu.|
|[transformator — Klasa](transformer-class.md)|`transformer`Blok obsługi komunikatów to jeden obiekt docelowy, który jest uporządkowany, `propagator_block` który może akceptować komunikaty jednego typu, i umożliwia przechowywanie nieograniczonej liczby komunikatów innego typu.|
|[Klasa unbounded_buffer](unbounded-buffer-class.md)|`unbounded_buffer`Blok komunikatów to wiele obiektów docelowych, uporządkowanych `propagator_block` z możliwością przechowywania nieograniczonej liczby komunikatów.|
|[Klasa unsupported_os](unsupported-os-class.md)|Ta klasa opisuje wyjątek zgłoszony, gdy używany jest nieobsługiwany system operacyjny.|

### <a name="structures"></a>Struktury

|Nazwa|Opis|
|----------|-----------------|
|[DispatchState — Struktura](dispatchstate-structure.md)|`DispatchState`Struktura służy do transferowania stanu do `IExecutionContext::Dispatch` metody. Opisano w nim sytuacje, w których `Dispatch` Metoda jest wywoływana w `IExecutionContext` interfejsie.|
|[IExecutionContext — Struktura](iexecutioncontext-structure.md)|Interfejs do kontekstu wykonywania, który może być uruchamiany w danym procesorze wirtualnym i być przełączany w ramach współdziałania z podsiecią.|
|[IExecutionResource — Struktura](iexecutionresource-structure.md)|Abstrakcja wątku sprzętowego.|
|[IResourceManager — Struktura](iresourcemanager-structure.md)|Interfejs Menedżer zasobów środowisko uruchomieniowe współbieżności. Jest to interfejs, za pomocą którego harmonogramy komunikują się z Menedżer zasobów.|
|[Struktura IScheduler](ischeduler-structure.md)|Interfejs do abstrakcji harmonogramu pracy. Menedżer zasobów środowisko uruchomieniowe współbieżności używa tego interfejsu do komunikowania się z harmonogramami służbowymi.|
|[ISchedulerProxy — Struktura](ischedulerproxy-structure.md)|Interfejs, za pomocą którego program Schedules komunikuje się z Menedżer zasobów środowisko uruchomieniowe współbieżności w celu negocjowania alokacji zasobów.|
|[IThreadProxy — Struktura](ithreadproxy-structure.md)|Abstrakcja wątku wykonania. W zależności od `SchedulerType` klucza zasad utworzonego przez Ciebie harmonogramu Menedżer zasobów przyznaje Ci serwer proxy wątków, który jest obsługiwany przez zwykły wątek Win32 lub wątek harmonogramie (UMS) trybu użytkownika. Wątki UMS są obsługiwane w 64-bitowych systemach operacyjnych z wersją Windows 7 i nowszą.|
|[ITopologyExecutionResource — Struktura](itopologyexecutionresource-structure.md)|Interfejs do zasobu wykonywania określony przez Menedżer zasobów.|
|[ITopologyNode — Struktura](itopologynode-structure.md)|Interfejs do węzła topologii zdefiniowany przez Menedżer zasobów. Węzeł zawiera jeden lub więcej zasobów wykonawczych.|
|[IUMSCompletionList — Struktura](iumscompletionlist-structure.md)|Reprezentuje listę uzupełniania UMS. Po zablokowaniu wątku UMS, wyznaczoną w harmonogramie kontekst planowania jest wysyłany w celu podjęcia decyzji o tym, co należy zaplanować na źródłowym głównym procesorze wirtualnym, gdy oryginalny wątek jest zablokowany. Gdy oryginalny wątek zostanie odblokowany, system operacyjny kolejkuje go do listy uzupełniania dostępnej za pomocą tego interfejsu. Harmonogram może wysyłać zapytania do listy uzupełniania w wydzielonym kontekście planowania lub innym miejscu, w którym szuka pracy.|
|[Struktura IUMSScheduler](iumsscheduler-structure.md)|Interfejs służący do abstrakcji harmonogramu pracy, który chce, aby środowisko uruchomieniowe współbieżności Menedżer zasobów do harmonogramie wątków w trybie użytkownika (UMS). Menedżer zasobów używa tego interfejsu do komunikowania się z harmonogramami wątków UMS. `IUMSScheduler`Interfejs dziedziczy po `IScheduler` interfejsie.|
|[IUMSThreadProxy — Struktura](iumsthreadproxy-structure.md)|Abstrakcja wątku wykonania. Jeśli chcesz, aby harmonogram przyznał wątki harmonogramie (UMS), ustaw wartość dla elementu zasady harmonogramu `SchedulerKind` na `UmsThreadDefault` , a następnie Zaimplementuj `IUMSScheduler` interfejs. Wątki UMS są obsługiwane tylko w 64-bitowych systemach operacyjnych z wersją Windows 7 i nowszą.|
|[IUMSUnblockNotification — Struktura](iumsunblocknotification-structure.md)|Reprezentuje powiadomienie z Menedżer zasobów, że serwer proxy wątku, który został zablokowany i wyzwolony powrót do wyznaczonego kontekstu planowania harmonogramu został odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, gdy kontekst wykonywania skojarzony z serwerem proxy wątku został zwrócony z `GetContext` metody, został ponownie zaplanowany.|
|[IVirtualProcessorRoot — Struktura](ivirtualprocessorroot-structure.md)|Abstrakcja wątku sprzętowego, w którym może być wykonywany serwer proxy wątku.|
|[scheduler_interface — Struktura](scheduler-interface-structure.md)|Interfejs usługi Scheduler|
|[scheduler_ptr, struktura (środowisko uruchomieniowe współbieżności)](scheduler-ptr-structure-concurrency-runtime.md)|Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje, aby zezwolić na specyfikację wspólnego okresu istnienia przy użyciu shared_ptr lub tylko zwykłego odwołania przy użyciu wskaźnika RAW.|

### <a name="enumerations"></a>Wyliczenia

|Nazwa|Opis|
|----------|-----------------|
|[agent_status](concurrency-namespace-enums.md#agent_status)|Prawidłowe Stany elementu `agent` .|
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanej przez bibliotekę agentów|
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanej przez środowisko uruchomieniowe współbieżności.|
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Flagi śledzenia dla typów zdarzeń|
|[CriticalRegionType —](concurrency-namespace-enums.md#criticalregiontype)|Typ regionu krytycznego, w którym znajduje się kontekst.|
|[DynamicProgressFeedbackType —](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Używane przez `DynamicProgressFeedback` zasady do opisywania, czy zasoby dla harmonogramu będą ponownie zrównoważenia według informacji statystycznych zebranych z harmonogramu lub tylko na podstawie procesorów wirtualnych przechodzących i wychodzących ze stanu bezczynności przez wywołania `Activate` metod i `Deactivate` w `IVirtualProcessorRoot` interfejsie. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|
|[join_type](concurrency-namespace-enums.md#join_type)|Typ `join` bloku obsługi komunikatów.|
|[message_status](concurrency-namespace-enums.md#message_status)|Prawidłowe odpowiedzi dla oferty `message` obiektu do bloku.|
|[PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey)|Klucze zasad opisujące aspekty zachowania usługi Scheduler. Każdy element zasad jest opisywany przez parę klucz-wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływu na harmonogramy, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|
|[SchedulerType —](concurrency-namespace-enums.md#schedulertype)|Używane przez `SchedulerKind` zasady do opisywania typu wątków, których harmonogram powinien używać dla podstawowych kontekstów wykonywania. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|
|[SchedulingProtocolType —](concurrency-namespace-enums.md#schedulingprotocoltype)|Używane przez `SchedulingProtocol` zasady do opisywania, który algorytm planowania będzie używany do harmonogramu. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|
|[SwitchingProxyState —](concurrency-namespace-enums.md#switchingproxystate)|Służy do oznaczania stanu, w którym znajduje się serwer proxy wątku, gdy wykonuje przełączenie kontekstu do innego serwera proxy wątku.|
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Opisuje stan wykonania `task_group` `structured_task_group` obiektu lub. Wartość tego typu jest zwracana przez wiele metod, które oczekują na ukończenie zadań zaplanowanych dla grupy zadań.|
|[WinRTInitializationType —](concurrency-namespace-enums.md#winrtinitializationtype)|Używane przez `WinRTInitialization` zasady do opisywania, czy i w jaki sposób środowisko wykonawcze systemu Windows zostanie zainicjowany w wątkach usługi Scheduler dla aplikacji działającej w systemach operacyjnych z wersją systemu Windows 8 lub nowszą. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md#policyelementkey).|

### <a name="functions"></a>Funkcje

|Nazwa|Opis|
|----------|-----------------|
|[Alloc — funkcja](concurrency-namespace-functions.md#alloc)|Przydziela blok pamięci o rozmiarze określonym na podstawie podprzydziału buforowania środowisko uruchomieniowe współbieżności.|
|[asend, funkcja](concurrency-namespace-functions.md#asend)|Przeciążone. Asynchroniczna operacja wysyłania, która planuje zadanie propagacji danych do docelowego bloku.|
|[Funkcja cancel_current_task](concurrency-namespace-functions.md#cancel_current_task)|Anuluje aktualnie wykonywane zadanie. Ta funkcja może zostać wywołana z poziomu treści zadania, aby przerwać wykonywanie zadania i spowodować, że `canceled` przestanie on działać.<br /><br /> Nie jest to obsługiwany scenariusz do wywołania tej funkcji, jeśli nie znajdujesz się w treści `task` . Wykonanie tej czynności spowoduje niezdefiniowane zachowanie, takie jak awaria lub brak odpowiedzi w aplikacji.|
|[Funkcja create_async](concurrency-namespace-functions.md#create_async)|Tworzy środowisko wykonawcze systemu Windows asynchronicznej na podstawie podanego przez użytkownika obiektu lambda lub funkcji. Zwracany typ `create_async` to jeden z `IAsyncAction^` , `IAsyncActionWithProgress<TProgress>^` , `IAsyncOperation<TResult>^` , lub `IAsyncOperationWithProgress<TResult, TProgress>^` na podstawie podpisu wyrażenia lambda przesłanego do metody.|
|[Funkcja create_task](concurrency-namespace-functions.md#create_task)|Przeciążone. Tworzy obiekt [zadania](task-class.md) PPL. `create_task`mogą być używane wszędzie, gdzie użyto konstruktora zadań. Jest ona świadczona głównie dla wygody, ponieważ umożliwia użycie `auto` słowa kluczowego podczas tworzenia zadań.|
|[Serviceresourcemanager — funkcja](concurrency-namespace-functions.md#createresourcemanager)|Zwraca interfejs, który reprezentuje pojedyncze wystąpienie Menedżer zasobów środowisko uruchomieniowe współbieżności. Menedżer zasobów jest odpowiedzialny za przypisywanie zasobów do harmonogramów, które chcą współpracować ze sobą.|
|[DisableTracing —, funkcja](concurrency-namespace-functions.md#disabletracing)|Wyłącza śledzenie w środowisko uruchomieniowe współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest domyślnie wyrejestrowane.|
|[EnableTracing —, funkcja](concurrency-namespace-functions.md#enabletracing)|Włącza śledzenie w środowisko uruchomieniowe współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest teraz domyślnie włączone.|
|[Free — funkcja](concurrency-namespace-functions.md#free)|Zwalnia blok pamięci, który został wcześniej przydzielony przez `Alloc` metodę do podalokacji środowisko uruchomieniowe współbieżności buforowania.|
|[Funkcja get_ambient_scheduler (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#get_ambient_scheduler)||
|[GetExecutionContextId —, funkcja](concurrency-namespace-functions.md#getexecutioncontextid)|Zwraca unikatowy identyfikator, który można przypisać do kontekstu wykonywania, który implementuje `IExecutionContext` interfejs.|
|[GetOSVersion —, funkcja](concurrency-namespace-functions.md#getosversion)|Zwraca wersję systemu operacyjnego.|
|[GetProcessorCount —, funkcja](concurrency-namespace-functions.md#getprocessorcount)|Zwraca liczbę wątków sprzętowych w źródłowym systemie.|
|[GetProcessorNodeCount —, funkcja](concurrency-namespace-functions.md#getprocessornodecount)|Zwraca liczbę węzłów NUMA lub pakietów procesorów w źródłowym systemie.|
|[GetSchedulerId —, funkcja](concurrency-namespace-functions.md#getschedulerid)|Zwraca unikatowy identyfikator, który można przypisać do harmonogramu, który implementuje `IScheduler` interfejs.|
|[Funkcja interruption_point](concurrency-namespace-functions.md#interruption_point)|Tworzy punkt przerwania do anulowania. Jeśli anulowanie jest w toku w kontekście, w którym ta funkcja jest wywoływana, spowoduje to zgłoszenie wyjątku wewnętrznego, który przerywa wykonywanie aktualnie wykonywanej pracy równoległej. Jeśli anulowanie nie jest w toku, funkcja nic nie robi.|
|[Funkcja is_current_task_group_canceling](concurrency-namespace-functions.md#is_current_task_group_canceling)|Zwraca wskazanie, czy grupa zadań, która jest aktualnie uruchamiana w bieżącym kontekście, znajduje się w pośrodku aktywnego anulowania (lub będzie wkrótce). Należy pamiętać, że jeśli w bieżącym kontekście nie ma żadnej grupy zadań, która jest aktualnie wykonywana, `false` zostanie zwrócona wartość.|
|[Funkcja make_choice](concurrency-namespace-functions.md#make_choice)|Przeciążone. Konstruuje `choice` blok komunikatów z opcjonalnych `Scheduler` lub co najmniej `ScheduleGroup` dwóch źródeł danych wejściowych.|
|[Funkcja make_greedy_join](concurrency-namespace-functions.md#make_greedy_join)|Przeciążone. Konstruuje `greedy multitype_join` blok komunikatów z opcjonalnych `Scheduler` lub co najmniej `ScheduleGroup` dwóch źródeł danych wejściowych.|
|[Funkcja make_join](concurrency-namespace-functions.md#make_join)|Przeciążone. Konstruuje `non_greedy multitype_join` blok komunikatów z opcjonalnych `Scheduler` lub co najmniej `ScheduleGroup` dwóch źródeł danych wejściowych.|
|[Funkcja make_task](concurrency-namespace-functions.md#make_task)|Metoda fabryki służąca do tworzenia `task_handle` obiektu.|
|[Funkcja parallel_buffered_sort](concurrency-namespace-functions.md#parallel_buffered_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w kolejności niemalejącej lub zgodnie z kryterium porządkowania określonym przez Predykat binarny równolegle. Ta funkcja jest semantyką podobną do `std::sort` w przypadku, gdy jest to porównanie, niestabilne, w miejscu, z wyjątkiem tego, że wymaga `O(n)` dodatkowego miejsca, i wymaga inicjalizacji domyślnej dla elementów, które są sortowane.|
|[Funkcja parallel_for](concurrency-namespace-functions.md#parallel_for)|Przeciążone. `parallel_for`wykonuje iterację w zakresie indeksów i wykonuje funkcję dostarczoną przez użytkownika w każdej iteracji równolegle.|
|[Funkcja parallel_for_each](concurrency-namespace-functions.md#parallel_for_each)|Przeciążone. `parallel_for_each`stosuje określoną funkcję do każdego elementu w obrębie zakresu równolegle. Jest semantycznie odpowiednikiem `for_each` funkcji w `std` przestrzeni nazw, z tą różnicą, że iteracja w elementach jest wykonywana równolegle, a kolejność iteracji nie została określona. Argument `_Func` musi obsługiwać operator wywołania funkcji w formularzu, `operator()(T)` gdzie parametr `T` jest typem elementu kontenera, w którym jest wykonywane iteracja.|
|[Funkcja parallel_invoke](concurrency-namespace-functions.md#parallel_invoke)|Przeciążone. Wykonuje obiekty funkcji dostarczone jako parametry równolegle i bloki do momentu zakończenia wykonywania. Każdy obiekt funkcji może być wyrażeniem lambda, wskaźnikiem do funkcji lub dowolnym obiektem, który obsługuje operator wywołania funkcji z sygnaturą `void operator()()` .|
|[Funkcja parallel_radixsort](concurrency-namespace-functions.md#parallel_radixsort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności przy użyciu algorytmu sortowania podstawy. Jest to stabilna funkcja sortowania, która wymaga funkcji projekcji, która może projektować elementy do posortowania na klucze podobne do liczby całkowitej. Dla elementów, które są sortowane, wymagana jest Inicjalizacja domyślna.|
|[Funkcja parallel_reduce](concurrency-namespace-functions.md#parallel_reduce)|Przeciążone. Oblicza sumę wszystkich elementów w określonym zakresie przez Obliczanie kolejnych sum częściowych lub oblicza wynik kolejnych częściowe wyniki, podobnie jak w przypadku użycia określonej operacji binarnej innej niż suma, równolegle. `parallel_reduce`jest semantycznie podobny do `std::accumulate` , z tą różnicą, że wymaga skojarzenia operacji binarnej i wymaga wartości tożsamości zamiast początkowej wartości.|
|[Funkcja parallel_sort](concurrency-namespace-functions.md#parallel_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w kolejności niemalejącej lub zgodnie z kryterium porządkowania określonym przez Predykat binarny równolegle. Ta funkcja jest semantyką podobną do `std::sort` w przypadku, gdy jest to porównanie, niestabilne i w miejscu.|
|[Funkcja parallel_transform](concurrency-namespace-functions.md#parallel_transform)|Przeciążone. Stosuje określony obiekt Function do każdego elementu w zakresie źródłowym lub do pary elementów z dwóch zakresów źródłowych i kopiuje wartości zwracane obiektu Function do zakresu docelowego równolegle. Ta funkcjonalność jest semantycznie równoważna z `std::transform` .|
|[Funkcja Receive](concurrency-namespace-functions.md#receive)|Przeciążone. Ogólna implementacja odbierania, która zezwala na kontekst oczekiwania na dane z dokładnie jednego źródła i filtruje akceptowane wartości.|
|[Funkcja run_with_cancellation_token](concurrency-namespace-functions.md#run_with_cancellation_token)|Wykonuje obiekt funkcji natychmiast i synchronicznie w kontekście danego tokenu anulowania.|
|[send — Funkcja](concurrency-namespace-functions.md#send)|Przeciążone. Synchroniczna operacja wysyłania, która czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat.|
|[Funkcja set_ambient_scheduler (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#set_ambient_scheduler)||
|[Funkcja set_task_execution_resources](concurrency-namespace-functions.md#set_task_execution_resources)|Przeciążone. Ogranicza zasoby wykonywania używane przez środowisko uruchomieniowe współbieżności wewnętrznych wątków roboczych do określonego zestawu koligacji.<br /><br /> Ta metoda jest prawidłowa do wywołania tej metody tylko przed utworzeniem Menedżer zasobów lub między dwoma Menedżer zasobów okresów istnienia. Może być wywoływana wiele razy, dopóki Menedżer zasobów nie istnieje w czasie wywołania. Po ustawieniu limitu koligacji nadal obowiązuje do następnego prawidłowego wywołania `set_task_execution_resources` metody.<br /><br /> Podana maska koligacji nie musi być podzbiorem maski koligacji procesu. Koligacja procesu będzie aktualizowana w razie potrzeby.|
|[Swap — Funkcja](concurrency-namespace-functions.md#swap)|Wymienia elementy dwóch `concurrent_vector` obiektów.|
|[Funkcja task_from_exception (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#task_from_exception)||
|[Funkcja task_from_result (środowisko uruchomieniowe współbieżności)](concurrency-namespace-functions.md#task_from_result)||
|[Funkcja Trace_agents_register_name](concurrency-namespace-functions.md#trace_agents_register_name)|Kojarzy daną nazwę z blokiem komunikatów lub agentem w śledzeniu ETW.|
|[Funkcja try_receive](concurrency-namespace-functions.md#try_receive)|Przeciążone. Ogólna implementacja try-Receive, umożliwiająca kontekstowi wyszukiwanie danych z dokładnie jednego źródła i filtrowanie wartości, które są akceptowane. Jeśli dane nie są gotowe, metoda zwróci wartość false.|
|[wait — Funkcja](concurrency-namespace-functions.md#wait)|Wstrzymuje bieżący kontekst przez określony czas.|
|[Funkcja when_all](concurrency-namespace-functions.md#when_all)|Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.|
|[Funkcja when_any](concurrency-namespace-functions.md#when_any)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|----------|-----------------|
|[operator! =](concurrency-namespace-operators.md#operator_neq)|Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora nie jest równy `concurrent_vector` obiektowi po prawej stronie.|
|[&&operatora](concurrency-namespace-operators.md#operator_amp_amp)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy oba zadania dostarczone jako argumenty zakończą się pomyślnie.|
|[&#124;&#124;operatora](concurrency-namespace-operators.md#operator_lor)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy jedno z zadań dostarczonych jako argumenty zakończy się pomyślnie.|
|[<operatora](concurrency-namespace-operators.md#operator_lt)|Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy od `concurrent_vector` obiektu po prawej stronie.|
|[<operatora =](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy od lub równy `concurrent_vector` obiektowi po prawej stronie.|
|[operator = =](concurrency-namespace-operators.md#operator_eq_eq)|Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest równy `concurrent_vector` obiektowi po prawej stronie.|
|[>operatora](concurrency-namespace-operators.md#operator_gt)|Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest większy niż `concurrent_vector` obiekt po prawej stronie.|
|[>operatora =](concurrency-namespace-operators.md#operator_lt_eq)|Testuje, czy `concurrent_vector` obiekt po lewej stronie operatora jest większy niż lub równy `concurrent_vector` obiektowi po prawej stronie.|

### <a name="constants"></a>Stałe

|Nazwa|Opis|
|----------|-----------------|
|[AgentEventGuid —](concurrency-namespace-constants1.md#agenteventguid)|Identyfikator GUID kategorii ({B9B5B78C-0713-4898-A21A-C67949DCED07}) opisujący zdarzenia ETW wywoływane przez bibliotekę agentów w środowisko uruchomieniowe współbieżności.|
|[ChoreEventGuid —](concurrency-namespace-constants1.md#choreeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z zadaniami lub zadań.|
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Identyfikator GUID dostawcy ETW dla środowisko uruchomieniowe współbieżności.|
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Wskazuje obsługę interfejsu Menedżer zasobów zdefiniowanego w programie Visual Studio 2010.|
|[ConcRTEventGuid —](concurrency-namespace-constants1.md#concrteventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które nie są dokładniej opisane przez inną kategorię.|
|[ContextEventGuid —](concurrency-namespace-constants1.md#contexteventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio powiązane z kontekstami.|
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Wartość wskazująca, że oczekiwania nigdy nie powinien przekraczać limitu czasu.|
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Wartość wskazująca, że upłynął limit czasu oczekiwania.|
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Specjalna wartość dla klucza zasad `ContextPriority` wskazująca, że priorytet wątku dla wszystkich kontekstów w harmonogramie powinien być taki sam jak w przypadku wątku, który utworzył harmonogram.|
|[LockEventGuid —](concurrency-namespace-constants1.md#lockeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio powiązane z blokadami.|
|[MaxExecutionResources —](concurrency-namespace-constants1.md#maxexecutionresources)|Specjalna wartość dla kluczy zasad `MinConcurrency` i `MaxConcurrency` . Wartość domyślna to liczba wątków sprzętowych na komputerze w przypadku braku innych ograniczeń.|
|[PPLParallelForeachEventGuid —](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użyciem `parallel_for_each` funkcji.|
|[PPLParallelForEventGuid —](concurrency-namespace-constants1.md#pplparallelforeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użyciem `parallel_for` funkcji.|
|[PPLParallelInvokeEventGuid —](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użyciem `parallel_invoke` funkcji.|
|[ResourceManagerEventGuid —](concurrency-namespace-constants1.md#resourcemanagereventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio powiązane z Menedżerem zasobów.|
|[ScheduleGroupEventGuid —](concurrency-namespace-constants1.md#schedulegroupeventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z grupami harmonogramu.|
|[SchedulerEventGuid —](concurrency-namespace-constants1.md#schedulereventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z działaniem usługi Scheduler.|
|[VirtualProcessorEventGuid —](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Identyfikator GUID kategorii opisujący zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z procesorami wirtualnymi.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h, ConcRT. h, concrtrm. h, concurrent_priority_queue. h, concurrent_queue. h, concurrent_unordered_map. h, concurrent_unordered_set. h, concurrent_vector. h, internal_concurrent_hash. h, internal_split_ordered_list. h, PPL. h, pplcancellation_token. h, pplconcrt. h, pplinterface. h, ppltasks. h

## <a name="see-also"></a>Zobacz także

[Dokumentacja](reference-concurrency-runtime.md)
