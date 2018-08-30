---
title: Współbieżność Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- Concurrency namespace
ms.assetid: f1d33ca2-679b-4442-b140-22a9d9df61d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 324acb33998246933b0c426357368247c6689c47
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211320"
---
# <a name="concurrency-namespace"></a>concurrency — Przestrzeń nazwy
`Concurrency` Przestrzeń nazw zawiera klasy i funkcje, które zapewniają dostęp do środowiska wykonawczego Concurrency, platformy programowania współbieżnego dla C++. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../../../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace concurrency;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="namespaces"></a>Namespaces  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CONCURRENCY::Extensibility Namespace](https://msdn.microsoft.com/16a86ff2-128e-4edf-89e4-38aac79c81f9)||  
  
### <a name="typedefs"></a>Typedefs  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`runtime_object_identity`|Każde wystąpienie komunikatu ma tożsamość, która po nim następuje sklonowany i przekazywane między składnikami obsługi wiadomości. Nie może to być adres obiektu wiadomości.|  
|`task_status`|Typ, który reprezentuje stan końcowy zadania. Prawidłowe wartości to `completed` i `canceled`.|  
|`TaskProc`|Abstrakcja podstawowe zadania podrzędnego, zdefiniowane jako `void (__cdecl * TaskProc)(void *)`. Element `TaskProc` jest wywoływana w celu wywołania treści zadania.|  
|`TaskProc_t`|Abstrakcja podstawowe zadania podrzędnego, zdefiniowane jako `void (__cdecl * TaskProc_t)(void *)`. Element `TaskProc` jest wywoływana w celu wywołania treści zadania.|  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[affinity_partitioner, klasa](affinity-partitioner-class.md)|`affinity_partitioner` Klasa jest podobna do `static_partitioner` klasy, ale zwiększa koligacji pamięci podręcznej przez siebie mapowania podzakresów na wątki robocze. Go może znacząco zwiększyć wydajność pętli jest ponownie wykonane przez tego samego zestawu danych, gdy dane są dopasowane do pamięci podręcznej. Należy pamiętać, że takie same `affinity_partitioner` obiektu musi być używany z kolejnych iteracjach pętli równoległej, który jest wykonywany dla określonego zestawu danych, aby korzystać z lokalizacja danych.|  
|[agent, klasa](agent-class.md)|Klasa przeznaczona do użycia jako klasę bazową dla wszystkich agentów niezależne. Służy do ukrywania stanu z innych agentów i wchodzić w interakcje przy użyciu przekazywania komunikatów.|  
|[auto_partitioner, klasa](auto-partitioner-class.md)|`auto_partitioner` Klasa reprezentuje domyślną metodę `parallel_for`, `parallel_for_each` i `parallel_transform` służy do partycjonowania zakresu iteruje po nich. Ta metoda partycjonowania employes kradzież do równoważenia obciążenia w zakresie także na iteracji anulowania.|  
|[bad_target, klasa](bad-target-class.md)|Ta klasa opisuje wyjątek generowany, gdy blok obsługi wiadomości podano wskaźnik do obiektu docelowego, która jest nieprawidłowa dla wykonywanej operacji.|  
|[call, klasa](call-class.md)|A `call` blok komunikatów jest wielu źródeł, uporządkowane `target_block` wywołującej określonej funkcji podczas odbierania komunikatu.|  
|[cancellation_token, klasa](cancellation-token-class.md)|`cancellation_token` Klasa reprezentuje zdolność do określenia, czy zażądano operacji anulowania. Dany token może być skojarzony z `task_group`, `structured_task_group`, lub `task` aby zapewnić anulowanie niejawne. Również może być sondowany o wykreślenie lub wywołanie zwrotne zarejestrowane dla przypadku, gdy skojarzony `cancellation_token_source` zostało anulowane.|  
|[cancellation_token_registration, klasa](cancellation-token-registration-class.md)|`cancellation_token_registration` Klasa reprezentuje powiadomienie o wywołaniu zwrotnym od `cancellation_token`. Gdy `register` metody `cancellation_token` umożliwia otrzymywanie powiadomień o czasie wystąpienia anulowania `cancellation_token_registration` obiekt jest zwracany jako uchwyt do funkcji zwrotnej tak, aby obiekt wywołujący może żądać konkretne wywołanie zwrotne nie jest już dokonywane przy użyciu `deregister` metody.|  
|[cancellation_token_source, klasa](cancellation-token-source-class.md)|`cancellation_token_source` Klasa reprezentuje możliwości anulowania pewnej operacji.|  
|[choice, klasa](choice-class.md)|A `choice` blok komunikatów jest wielu źródeł, docelowy pojedynczego bloku, który reprezentuje przepływ sterowania interakcje zestawu źródeł. Blok wyboru będzie czekać na jeden z wielu źródeł, który zwróci komunikat i rozpropaguje indeks źródła, które generowany komunikat.|  
|[combinable, klasa](combinable-class.md)|`combinable<T>` Obiektu mają na celu dostarczenie prywatnego wątku kopie danych w celu wykonywania obliczeń podrzędnych wolne od blokady wątków lokalnych podczas algorytmy równoległe. Na koniec operacji równoległej obliczeń podrzędnych prywatnego wątku może następnie zostać scalony wynik końcowy. Ta klasa można używać zamiast udostępnionej zmiennej i może spowodować zwiększenie wydajności, jeśli w przeciwnym razie będzie wiele rywalizacji o zasoby w tej zmiennej udostępnionych.|  
|[concurrent_priority_queue, klasa](concurrent-priority-queue-class.md)|`concurrent_priority_queue` Klasy jest kontenerem, który zezwala na wiele wątków jednocześnie elementów wypychania i pop. Elementy są zdjęte ze stosu w kolejności priorytetów, których priorytet jest określana przez funktorem dostarczone jako argument szablonu.|  
|[concurrent_queue, klasa](concurrent-queue-class.md)|`concurrent_queue` Klasa jest klasą kontenera sekwencji, umożliwiającym w pierwszym, first-out dostęp do jego elementów. Umożliwia ona ograniczony zestaw operacji bezpieczne pod względem współbieżności, takich jak `push` i `try_pop`.|  
|[concurrent_unordered_map, klasa](concurrent-unordered-map-class.md)|`concurrent_unordered_map` Klasa jest kontenerem bezpieczne pod względem współbieżności, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne pod względem współbieżności dołączyć element dostępu, dostępu do iteratora i operacji przechodzenia iteratora.|  
|[concurrent_unordered_multimap, klasa](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` Klasa jest bezpiecznym pod współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne pod względem współbieżności dołączyć element dostępu do iteratora i operacji przechodzenia iteratora.|  
|[concurrent_unordered_multiset, klasa](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset` Klasa jest bezpiecznym pod współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne pod względem współbieżności dołączyć element dostępu do iteratora i operacji przechodzenia iteratora.|  
|[concurrent_unordered_set, klasa](concurrent-unordered-set-class.md)|`concurrent_unordered_set` Klasa jest bezpiecznym pod współbieżności kontenerem, który kontroluje różnej długości sekwencje elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczne pod względem współbieżności dołączyć element dostępu do iteratora i operacji przechodzenia iteratora.|  
|[concurrent_vector, klasa](concurrent-vector-class.md)|`concurrent_vector` Klasy jest klasą kontenera sekwencji, która zezwala na dostępie do dowolnego elementu. Umożliwia bezpieczne pod względem współbieżności dołączyć element dostępu, dostępu do iteratora i operacji przechodzenia iteratora.|  
|[Context, klasa](context-class.md)|Reprezentuje klasą abstrakcyjną dla kontekstu wykonywania.|  
|[context_self_unblock, klasa](context-self-unblock-class.md)|Ta klasa opisuje wyjątek generowany, gdy `Unblock` metody `Context` obiektu jest wywoływana z tym samym kontekście. To wskazuje w danym kontekście zostanie podjęta próba odblokowania sam.|  
|[context_unblock_unbalanced, klasa](context-unblock-unbalanced-class.md)|Ta klasa opisuje wyjątek generowany, gdy wywołuje w celu `Block` i `Unblock` metody `Context` obiektu nie są prawidłowo skojarzone.|  
|[critical_section, klasa](critical-section-class.md)|Mutex nie obsługującą, które jest jawnie świadome współbieżności środowiska wykonawczego.|  
|[CurrentScheduler, klasa](currentscheduler-class.md)|Reprezentuje klasą abstrakcyjną dla bieżącego harmonogramu skojarzony kontekst wywołania.|  
|[default_scheduler_exists, klasa](default-scheduler-exists-class.md)|Ta klasa opisuje wyjątek generowany, gdy `Scheduler::SetDefaultSchedulerPolicy` metoda jest wywoływana, gdy domyślnego harmonogramu już istnieje w ramach procesu.|  
|[event, klasa](event-class.md)|Zdarzenie resetowania ręcznego, które jest jawnie świadome współbieżności środowiska wykonawczego.|  
|[improper_lock, klasa](improper-lock-class.md)|Ta klasa opisuje wyjątek generowany, gdy jest blokada nieprawidłowo.|  
|[improper_scheduler_attach, klasa](improper-scheduler-attach-class.md)|Ta klasa opisuje wyjątek generowany, gdy `Attach` wywoływana jest metoda `Scheduler` obiektu, który jest już dołączony do bieżącego kontekstu.|  
|[improper_scheduler_detach, klasa](improper-scheduler-detach-class.md)|Ta klasa opisuje wyjątek generowany, gdy `CurrentScheduler::Detach` metoda jest wywoływana w kontekście, który nie został dołączony do dowolnej harmonogramu przy użyciu `Attach` metody `Scheduler` obiektu.|  
|[improper_scheduler_reference, klasa](improper-scheduler-reference-class.md)|Ta klasa opisuje wyjątek generowany, gdy `Reference` wywoływana jest metoda `Scheduler` obiekt, który jest zamykana, z kontekstu, który nie jest częścią tego harmonogramu.|  
|[invalid_link_target, klasa](invalid-link-target-class.md)|Ta klasa opisuje wyjątek generowany, gdy `link_target` zostanie wywołana metoda Blok obsługi wiadomości i bloku obsługi wiadomości nie jest w stanie połączyć się z obiektem docelowym. Może to być wynikiem przekroczenie liczby łącza, blok komunikatów jest dozwolone, czy próba połączyć określony element docelowy dwa razy tego samego źródła.|  
|[invalid_multiple_scheduling, klasa](invalid-multiple-scheduling-class.md)|Ta klasa opisuje wyjątek generowany, gdy `task_handle` obiekt jest zaplanowane wiele razy, używając `run` metody `task_group` lub `structured_task_group` obiekt bez interwencyjnego wywołania `wait` lub `run_and_wait` metody.|  
|[invalid_operation, klasa](invalid-operation-class.md)|Ta klasa opisuje wyjątek generowany, gdy jest wykonywana Nieprawidłowa operacja, która jest dokładniej opisana przez inny typ wyjątku generowanego przez środowisko uruchomieniowe współbieżności.|  
|[invalid_oversubscribe_operation, klasa](invalid-oversubscribe-operation-class.md)|Ta klasa opisuje wyjątek generowany, gdy `Context::Oversubscribe` metoda jest wywoływana z `_BeginOversubscription` parametr `false` bez uprzedniego wywołania do `Context::Oversubscribe` metody z `_BeginOversubscription` parametr `true`.|  
|[invalid_scheduler_policy_key, klasa](invalid-scheduler-policy-key-class.md)|Ta klasa opisuje wyjątek generowany, gdy nieprawidłową lub nieznany klucz zostanie przekazany do `SchedulerPolicy` konstruktora obiektu lub `SetPolicyValue` metody `SchedulerPolicy` obiekt jest przekazywany klucza, które należy zmienić przy użyciu innych metod, takich jak `SetConcurrencyLimits` metody.|  
|[invalid_scheduler_policy_thread_specification, klasa](invalid-scheduler-policy-thread-specification-class.md)|Ta klasa opisuje wyjątek generowany, gdy podejmowana jest próba można ustawić limity współbieżności `SchedulerPolicy` obiektu taki sposób, że wartość `MinConcurrency` klucz jest mniejsza niż wartość `MaxConcurrency` klucza.|  
|[invalid_scheduler_policy_value, klasa](invalid-scheduler-policy-value-class.md)|Ta klasa opisuje wyjątek generowany, gdy klucz zasad `SchedulerPolicy` obiekt jest ustawiony na nieprawidłową wartość dla tego klucza.|  
|[ISource, klasa](isource-class.md)|`ISource` Klasy to interfejs dla wszystkich źródłowych bloków. Bloków źródła Propagacja komunikatów `ITarget` bloków.|  
|[ITarget, klasa](itarget-class.md)|`ITarget` Klasy to interfejs dla wszystkich docelowych bloków. Bloków docelowych używanie wiadomości oferowane przez `ISource` bloków.|  
|[join, klasa](join-class.md)|A `join` blok komunikatów jest docelowy pojedynczego wielu źródeł, uporządkowanych `propagator_block` które łączy ze sobą komunikaty typu `T` z każdej z jej źródła.|  
|[location, klasa](location-class.md)|Abstrakcja fizycznej lokalizacji na sprzęcie.|  
|[message, klasa](message-class.md)|Koperty wiadomości podstawowe zawierającego ładunek danych przekazywany pomiędzy blokami obsługi komunikatów.|  
|[message_not_found, klasa](message-not-found-class.md)|Ta klasa opisuje wyjątek generowany, gdy blok komunikatów jest nie można odnaleźć żądanej wiadomości.|  
|[message_processor, klasa](message-processor-class.md)|`message_processor` Klasa jest abstrakcyjna klasa bazowa dla przetwarzania `message` obiektów. Nie ma żadnej gwarancji, w kolejności wiadomości.|  
|[missing_wait, klasa](missing-wait-class.md)|Ta klasa opisuje wyjątek generowany, gdy istnieją zadania zaplanowane nadal `task_group` lub `structured_task_group` obiektu w czasie tego obiektu wykonuje destruktora. Ten wyjątek nigdy nie zostanie zgłoszony, jeśli zostanie osiągnięty destruktor, ze względu na stosie rozwinięcia jako wynik wyjątku.|  
|[multi_link_registry, klasa](multi-link-registry-class.md)|`multi_link_registry` Obiekt jest `network_link_registry` który zarządza wiele bloków źródła lub wiele bloków docelowych.|  
|[multitype_join, klasa](multitype-join-class.md)|A `multitype_join` blok komunikatów jest wielu źródeł, docelowy pojedynczego blok komunikatów, który łączy ze sobą wiadomości o różnych typach z każdego z jego źródła i oferuje krotki połączone komunikatów do jego obiekty docelowe.|  
|[nested_scheduler_missing_detach, klasa](nested-scheduler-missing-detach-class.md)|Ta klasa opisuje wyjątek generowany, gdy w środowisku uruchomieniowym współbieżności: wykrywa, czy możesz zwrócenia przez niego do wywołania `CurrentScheduler::Detach` metody na poziomie kontekstu, który dołączony do drugiego za pomocą harmonogramu `Attach` metody `Scheduler` obiektu.|  
|[network_link_registry, klasa](network-link-registry-class.md)|`network_link_registry` Abstrakcyjna klasa bazowa zarządza łącza między źródłowym i docelowym bloki.|  
|[operation_timed_out, klasa](operation-timed-out-class.md)|Ta klasa opisuje wyjątek generowany, gdy upłynął limit czasu operacji.|  
|[ordered_message_processor, klasa](ordered-message-processor-class.md)|`ordered_message_processor` Jest `message_processor` umożliwiająca bloki komunikatów do przetwarzania wiadomości w kolejności zostały odebrane.|  
|[overwrite_buffer, klasa](overwrite-buffer-class.md)|`overwrite_buffer` Blok komunikatów jest ona lokalizacją docelową wielu, wielu źródeł, uporządkowanych `propagator_block` można przechowywać pojedynczej wiadomości w czasie. Nowe komunikaty zastąpienie wcześniej konsekwencje na gruncie z nich.|  
|[progress_reporter, klasa](progress-reporter-class.md)|Klasa reportera postępu pozwala raportowania powiadomienia o postępie określonego typu. Każdy obiekt progress_reporter jest powiązany z określoną akcją lub operacją asynchroniczną.|  
|[propagator_block, klasa](propagator-block-class.md)|`propagator_block` Klasa jest abstrakcyjna klasa bazowa dla bloków komunikatów, które są zarówno źródłowy, jak i obiektem docelowym. Łączy ona funkcje zarówno `source_block` i `target_block` klasy.|  
|[reader_writer_lock, klasa](reader-writer-lock-class.md)|Składnik zapisywania preferencji oparte na kolejce czytnika-blokadę przy użyciu lokalnej tylko obrotowych. Blokady przyznaje najpierw w — najpierw out (FIFO) dostęp do składników zapisywania i starves czytelnicy obciążeniem ciągłe składników zapisywania.|  
|[ScheduleGroup, klasa](schedulegroup-class.md)|Reprezentuje klasą abstrakcyjną dla grupy harmonogramów. Harmonogram grup organizuje zestaw powiązanych prac, które mają korzyści z zaplanowane blisko siebie czasowo, przez wykonywanie innego zadania w tej samej grupie przed przeniesieniem do innej grupy lub przestrzennie, wykonując wiele elementów w tej samej grupie na tym samym Węzeł NUMA lub fizycznym gnieździe.|  
|[Scheduler, klasa](scheduler-class.md)|Reprezentuje klasą abstrakcyjną dla harmonogram współbieżność środowiska wykonawczego.|  
|[scheduler_not_attached, klasa](scheduler-not-attached-class.md)|Ta klasa opisuje wyjątek generowany, gdy operacja została wykonana, co wymaga harmonogramu dołączony do bieżącego kontekstu, a nie jest.|  
|[scheduler_resource_allocation_error, klasa](scheduler-resource-allocation-error-class.md)|Ta klasa opisuje wyjątek generowany z powodu błędu można uzyskać krytycznym zasobem w środowisku uruchomieniowym współbieżności.|  
|[scheduler_worker_creation_error, klasa](scheduler-worker-creation-error-class.md)|Ta klasa opisuje wyjątek generowany z powodu błędu tworzenia kontekstu wykonywania procesu roboczego w środowisku uruchomieniowym współbieżności.|  
|[SchedulerPolicy, klasa](schedulerpolicy-class.md)|`SchedulerPolicy` Klasa zawiera zestaw pary klucz/wartość, jeden dla każdego elementu zasad, które kontrolują zachowanie wystąpienia harmonogramu.|  
|[simple_partitioner, klasa](simple-partitioner-class.md)|`simple_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu postanowiliśmy za pośrednictwem przez `parallel_for`. Partycjonera dzieli zakres na fragmenty w taki sposób, że każdy fragment ma co najmniej liczba iteracji, określony przez rozmiar fragmentu.|  
|[single_assignment, klasa](single-assignment-class.md)|A `single_assignment` blok komunikatów jest ona lokalizacją docelową wielu, wielu źródeł, uporządkowanych `propagator_block` można przechowywać jeden zapis — po `message`.|  
|[single_link_registry, klasa](single-link-registry-class.md)|`single_link_registry` Obiekt jest `network_link_registry` który zarządza tylko jeden blok źródłowym lub docelowym.|  
|[source_block, klasa](source-block-class.md)|`source_block` Klasa jest abstrakcyjna klasa bazowa dla bloków tylko do źródła. Klasa oferuje łącze podstawowe funkcje zarządzania jako również jako common sprawdzanie błędów.|  
|[source_link_manager, klasa](source-link-manager-class.md)|`source_link_manager` Obiektu zarządza komunikatów blok połączeń sieciowych z `ISource` bloków.|  
|[static_partitioner, klasa](static-partitioner-class.md)|`static_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu postanowiliśmy za pośrednictwem przez `parallel_for`. Partycjonera dzieli zakres na dowolną liczbę fragmentów są dostępne do harmonogramu underyling procesów roboczych.|  
|[structured_task_group, klasa](structured-task-group-class.md)|`structured_task_group` Klasa reprezentuje uporządkowany zbiór równoległą pracę. Można kolejkować pojedynczych zadań równoległych `structured_task_group` przy użyciu `task_handle` obiekty i zaczekaj na ich zakończenie lub anulować grupę zadań zanim została zakończona, wykonywania, co spowoduje przerwanie wszystkich zadań, które nie zostały rozpoczęte wykonywanie.|  
|[target_block, klasa](target-block-class.md)|`target_block` Klasa jest abstrakcyjna klasa bazowa, zapewniająca łącze podstawowe funkcje zarządzania i tylko sprawdzanie błędów dla elementu docelowego blokuje.|  
|[task, klasa (środowisko uruchomieniowe współbieżności)](task-class.md)|Biblioteka równoległych wzorców (PPL) `task` klasy. A `task` obiekt reprezentuje prac, które mogą być wykonywane asynchronicznie, a równocześnie z innymi zadaniami i w środowisku uruchomieniowym współbieżności: pracy równoległej produkowane przez algorytmy równoległe. Daje wynik o typie `_ResultType` po pomyślnym ukończeniu. Zadania typu `task<void>` nie generują żadnego wyniku. Zadanie można wstrzymywać i anulować niezależnie od innych zadań. Może również składać z innymi zadaniami za pomocą kontynuacji (`then`) i sprzężenia (`when_all`) i wyboru (`when_any`) wzorców.|  
|[task_canceled, klasa](task-canceled-class.md)|Ta klasa opisuje wyjątek generowany przez warstwę zadań PPL, aby wymusić anulowanie bieżącego zadania. Jest to również generowane przez `get()` metody [zadań](https://msdn.microsoft.com/5389e8a5-5038-40b6-844a-55e9b58ad35f), dla anulowanych zadań.|  
|[task_completion_event, klasa](task-completion-event-class.md)|`task_completion_event` Klasa umożliwia opóźnienie wykonania zadania, dopóki nie zostanie spełniony jakiś warunek, lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.|  
|[task_continuation_context, klasa](task-continuation-context-class.md)|`task_continuation_context` Klasy pozwala określić, gdzie chcesz kontynuacji do wykonania. Ta jest przydatna tylko używanie tej klasy z aplikacji platformy uniwersalnej systemu Windows. W przypadku aplikacji innych niż Windows Runtime Kontekst wykonywania kontynuacji zadania jest ustalony w czasie wykonywania i nie można konfigurować.|  
|[task_group — klasa](task-group-class.md)|`task_group` Klasa reprezentuje kolekcję równoległą pracę, która może być oczekiwany lub anulowane.|  
|[task_handle, klasa](task-handle-class.md)|`task_handle` Klasa reprezentuje pojedynczy równoległe element roboczy. Hermetyzuje on instrukcje, jak i dane wymagane do wykonania pracy.|  
|[task_options, klasa (środowisko uruchomieniowe współbieżności)](task-options-class-concurrency-runtime.md)|Reprezentuje dozwolone opcje tworzenia zadania|  
|[timer, klasa](timer-class.md)|A `timer` blok komunikatów jest celu pojedynczego `source_block` zdolne do wysyłania komunikatu do jego element docelowy po określonym okresie czasu lub w określonych odstępach czasu.|  
|[transformer, klasa](transformer-class.md)|A `transformer` blok komunikatów jest docelowy pojedynczego wielu źródeł, uporządkowanych `propagator_block` który może akceptować komunikaty jednego typu i jest można przechowywać nieograniczoną liczbę komunikatów innego typu.|  
|[Klasa unbounded_buffer](unbounded-buffer-class.md)|`unbounded_buffer` Blok komunikatów jest ona lokalizacją docelową wielu, wielu źródeł, uporządkowanych `propagator_block` można przechowywać nieograniczoną liczbę komunikatów.|  
|[unsupported_os, klasa](unsupported-os-class.md)|Ta klasa opisuje wyjątek generowany, gdy jest używany nieobsługiwany system operacyjny.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DispatchState, struktura](dispatchstate-structure.md)|`DispatchState` Struktury służy do transferowania stan `IExecutionContext::Dispatch` metody. Zawiera opis sytuacji, w którym `Dispatch` wywoływana jest metoda `IExecutionContext` interfejsu.|  
|[IExecutionContext, struktura](iexecutioncontext-structure.md)|Interfejs do kontekstu wykonywania, który można uruchomić przy użyciu danego procesora wirtualnego i być wspólne przełączania kontekstu.|  
|[IExecutionResource, struktura](iexecutionresource-structure.md)|Abstrakcja wątku sprzętu.|  
|[IResourceManager, struktura](iresourcemanager-structure.md)|Interfejs do Menedżera zasobów Runtime współbieżności. Jest to interfejs, za pomocą którego lotów komunikować się z usługą Resource Manager.|  
|[IScheduler, struktura](ischeduler-structure.md)|Interfejs abstrakcję harmonogram pracy. Menedżer zasobów w środowisku uruchomieniowym współbieżności używa ten interfejs do komunikacji z harmonogramów pracy.|  
|[ISchedulerProxy, struktura](ischedulerproxy-structure.md)|Interfejs, za pomocą którego lotów komunikować się z Menedżerem zasobów w środowisku uruchomieniowym współbieżności do negocjowania alokacji zasobów.|  
|[IThreadProxy, struktura](ithreadproxy-structure.md)|Abstrakcja wątku wykonywania. W zależności od `SchedulerType` klucza zasad harmonogramu tworzenia, Menedżer zasobów spowoduje przyznanie Ci proxy wątku, która jest wspierana przez regularne wątek Win32 lub wątku (UMS) ustalonych w harmonogramie trybu użytkownika. UMS wątki są obsługiwane w systemie 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszy.|  
|[ITopologyExecutionResource, struktura](itopologyexecutionresource-structure.md)|Interfejs z zasobem wykonywania, zgodnie z definicją przez Menedżera zasobów.|  
|[ITopologyNode, struktura](itopologynode-structure.md)|Interfejs do węzła topologii, zgodnie z definicją przez Menedżera zasobów. Węzeł zawiera jeden lub więcej zasobów do wykonania.|  
|[IUMSCompletionList, struktura](iumscompletionlist-structure.md)|Reprezentuje listę uzupełniania UMS. Podczas planowania wyznaczony harmonogramu UMS bloki wątku, kontekst jest wywoływane w celu podjęcia decyzji o tym, co należy zaplanować na podstawowego procesora wirtualnego katalogu głównego, gdy oryginalny wątek jest zablokowany. Gdy odblokowuje wątek oryginalnej, system operacyjny umieszcza je w kolejce do listy uzupełniania, który jest dostępny za pośrednictwem tego interfejsu. Harmonogram można badać na liście uzupełniania w wyznaczonym Kontekst harmonogramu lub w innym miejscu, przeszukiwanych do pracy.|  
|[IUMSScheduler, struktura](iumsscheduler-structure.md)|Interfejs abstrakcję harmonogram pracy, który chce ze współbieżności środowiska wykonawczego usługi Resource Manager do ręcznego go wątków (UMS) ustalonych w harmonogramie trybu użytkownika. Menedżer zasobów używa tego interfejsu do komunikacji z harmonogramów wątku UMS. `IUMSScheduler` Interfejs dziedziczy z `IScheduler` interfejsu.|  
|[IUMSThreadProxy, struktura](iumsthreadproxy-structure.md)|Abstrakcja wątku wykonywania. Harmonogramu uzyskają wątków (UMS) ustalonych w harmonogramie trybu użytkownika, należy ustawić wartość dla elementu zasad harmonogramu `SchedulerKind` do `UmsThreadDefault`i zaimplementować `IUMSScheduler` interfejsu. UMS wątki są tylko obsługiwane w systemie 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszy.|  
|[IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)|Reprezentuje powiadomienie z Menedżera zasobów, serwer proxy wątku, zablokowany, co wyzwalane powrót do harmonogramu wyznaczony planowania kontekst ma odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, gdy zwróciło kontekstu wykonywania skojarzony wątek serwera proxy, `GetContext` zmiany w harmonogramie metody.|  
|[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)|Abstrakcja wątku sprzętu, na którym można wykonać wątek serwera proxy.|  
|[scheduler_interface, struktura](scheduler-interface-structure.md)|Interfejs harmonogramu|  
|[scheduler_ptr, struktura (środowisko uruchomieniowe współbieżności)](scheduler-ptr-structure-concurrency-runtime.md)|Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje, aby zezwolić na specyfikację wspólnego okresu istnienia przy użyciu wskaźnika shared_ptr lub zwykłe odwołanie za pomocą wskaźnika raw.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[agent_status](concurrency-namespace-enums.md#agent_status)|Prawidłowe stany `agent`.|  
|[Agents_eventtype —](concurrency-namespace-enums.md#agents_eventtype)|Typy zdarzeń, które mogą być śledzone za pomocą funkcji śledzenia oferowane przez biblioteki agentów|  
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy zdarzeń, które mogą być śledzone za pomocą funkcji śledzenia oferowane przez środowisko uruchomieniowe współbieżności.|  
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Flagi śledzenia typy zdarzeń|  
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|Typ regionu krytyczny kontekst znajduje się wewnątrz.|  
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Używane przez `DynamicProgressFeedback` zasady do opisywania, czy zasoby dla harmonogramu zostanie ponownie zbilansowana zgodnie z informacje statystyczne zebrane z harmonogramu lub tylko na podstawie na pracę i w stan bezczynności za pośrednictwem wywołania procesorówwirtualnych`Activate` i `Deactivate` metod `IVirtualProcessorRoot` interfejsu. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
|[join_type](concurrency-namespace-enums.md#join_type)|Typ `join` Blok obsługi wiadomości.|  
|[message_status](concurrency-namespace-enums.md#message_status)|Prawidłowe odpowiedzi na ofertę `message` obiektu do bloku.|  
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Klucze zasad zawierająca opis aspekty zachowania harmonogramu. Każdy element zasad jest opisane pary klucz wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływ na transfery danych zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|  
|[Schedulertype —](concurrency-namespace-enums.md#schedulertype)|Używane przez `SchedulerKind` zasady do opisywania typ wątki, które harmonogram powinni stosować dla podstawowej kontekstów wykonanie. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|Używane przez `SchedulingProtocol` zasady do opisywania, który algorytm planowania, będzie wykorzystywana w przypadku usługi scheduler. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Wykorzystywany w celu określenia stanu w jakim jest wątek serwera proxy, gdy jest wykonywany przełączanie kontekstu współpracy na serwerze proxy w innym wątku.|  
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Opisuje stan wykonania obiektu `task_group` lub `structured_task_group` obiektu. Wartość tego typu jest zwracany przez metod czekających na zadania zaplanowane do grupy zadań do wykonania.|  
|[Winrtinitializationtype —](concurrency-namespace-enums.md#winrtinitializationtype)|Używane przez `WinRTInitialization` zasady do opisywania, czy i jak środowisko wykonawcze Windows będzie zainicjowane na wątki harmonogram dla aplikacji, która działa w systemach operacyjnych z wersji systemu Windows 8 lub nowszy. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ALLOC — funkcja](concurrency-namespace-functions.md#alloc)|Przydziela blok pamięci w procentach rozmiaru określonego z Suballocator buforowania w czasie wykonywania współbieżności.|  
|[asend — funkcja](concurrency-namespace-functions.md#asend)|Przeciążone. Operacja asynchronicznego wysyłania, która planuje zadania propagowanie danych do bloku docelowego.|  
|[cancel_current_task — funkcja](concurrency-namespace-functions.md#cancel_current_task)|Anuluje aktualnie przeprowadzane zadanie. Ta funkcja może zostać wywołana z treści zadania, aby przerwać jego wykonywanie i spowodować wprowadzenie `canceled` stanu.<br /><br /> Nie jest to obsługiwany scenariusz, aby wywołać tę funkcję, jeśli nie jesteś w treści `task`. To spowoduje nieokreślone zachowanie przykład awarię lub zawieszenie aplikacji.|  
|[create_async — funkcja](concurrency-namespace-functions.md#create_async)|Tworzy konstrukcję asynchroniczną środowiska wykonawczego Windows na podstawie podanych przez użytkownika obiektu lambda lub funkcji. Zwracany typ `create_async` jest `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, lub `IAsyncOperationWithProgress<TResult, TProgress>^` zależnie od podpisu wyrażenia lambda przekazanego do metody.|  
|[create_task — funkcja](concurrency-namespace-functions.md#create_task)|Przeciążone. Tworzy PPL [zadań](https://msdn.microsoft.com/5389e8a5-5038-40b6-844a-55e9b58ad35f) obiektu. `create_task` może służyć wszędzie użyto konstruktora zadania. Jest ona udostępniana przede wszystkim dla wygody, ponieważ zezwala ona na korzystanie z `auto` — słowo kluczowe podczas tworzenia zadań.|  
|[Createresourcemanager — funkcja](concurrency-namespace-functions.md#createresourcemanager)|Zwraca interfejs, który reprezentuje wystąpienie singleton Menedżera zasobów Runtime współbieżności. Menedżer zasobów jest odpowiedzialny za przydzielanie zasobów, do których chcesz współpracować ze sobą.|  
|[Disabletracing — funkcja](concurrency-namespace-functions.md#disabletracing)|Wyłącza śledzenie w środowisku uruchomieniowym współbieżności. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest niezarejestrowana domyślnie.|  
|[Enabletracing — funkcja](concurrency-namespace-functions.md#enabletracing)|Umożliwia śledzenie w środowisku uruchomieniowym współbieżności. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest teraz domyślnie włączona.|  
|[Free — funkcja](concurrency-namespace-functions.md#free)|Zwalnia blok pamięci uprzednio przydzielonej przez `Alloc` metodę Suballocator buforowania w czasie wykonywania współbieżności.|  
|[get_ambient_scheduler — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#get_ambient_scheduler)||  
|[GetExecutionContextId Function](concurrency-namespace-functions.md#getexecutioncontextid)|Zwraca unikatowy identyfikator, który można przypisać do kontekstu wykonywania, który implementuje `IExecutionContext` interfejsu.|  
|[Getosversion — funkcja](concurrency-namespace-functions.md#getosversion)|Zwraca wersję systemu operacyjnego.|  
|[Getprocessorcount — funkcja](concurrency-namespace-functions.md#getprocessorcount)|Zwraca liczbę wątków sprzętu w systemie podstawowym.|  
|[Getprocessornodecount — funkcja](concurrency-namespace-functions.md#getprocessornodecount)|Zwraca liczbę węzłów NUMA lub opakowań procesora w systemie podstawowym.|  
|[Getschedulerid — funkcja](concurrency-namespace-functions.md#getschedulerid)|Zwraca unikatowy identyfikator, który można przypisać do harmonogramu, który implementuje `IScheduler` interfejsu.|  
|[interruption_point — funkcja](concurrency-namespace-functions.md#interruption_point)|Tworzy punkt przerwania do anulowania. W przypadku anulowania w toku w kontekście, w których ta funkcja jest wywoływana, zgłosi wyjątek wewnętrzny, który przerywa wykonywanie aktualnie wykonywanej pracy równoległej. Jeśli anulowania nie jest w toku, funkcja nie działa.|  
|[is_current_task_group_canceling Function](concurrency-namespace-functions.md#is_current_task_group_canceling)|Zwraca wskazanie, czy zadanie grupy, która jest aktualnie wykonywana i wbudowana w bieżącym kontekście jest w środku aktywnego anulowania (lub będzie wkrótce). Należy pamiętać, że jeśli żadna grupa zadań aktualnie wykonywana i wbudowana w bieżącym kontekście `false` zostaną zwrócone.|  
|[make_choice — funkcja](concurrency-namespace-functions.md#make_choice)|Przeciążone. Konstruuje `choice` Blok obsługi wiadomości z opcjonalnego `Scheduler` lub `ScheduleGroup` i co najmniej dwóch źródeł danych wejściowych.|  
|[make_greedy_join — funkcja](concurrency-namespace-functions.md#make_greedy_join)|Przeciążone. Konstruuje `greedy multitype_join` Blok obsługi wiadomości z opcjonalnego `Scheduler` lub `ScheduleGroup` i co najmniej dwóch źródeł danych wejściowych.|  
|[make_join — funkcja](concurrency-namespace-functions.md#make_join)|Przeciążone. Konstruuje `non_greedy multitype_join` Blok obsługi wiadomości z opcjonalnego `Scheduler` lub `ScheduleGroup` i co najmniej dwóch źródeł danych wejściowych.|  
|[make_task — funkcja](concurrency-namespace-functions.md#make_task)|Metoda fabryki, do tworzenia `task_handle` obiektu.|  
|[parallel_buffered_sort — funkcja](concurrency-namespace-functions.md#parallel_buffered_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat, jednocześnie. Ta funkcja jest semantycznie podobne do `std::sort` naciśnięcia sortowania na podstawie porównania, niestabilne, w miejscu, z tą różnicą, że potrzebuje `O(n)` dodatkowe miejsce i wymaga domyślna Inicjalizacja elementów posortowana.|  
|[parallel_for — funkcja](concurrency-namespace-functions.md#parallel_for)|Przeciążone. `parallel_for` wykonuje iterację na szeroką gamę indeksów i wykonuje funkcję dostarczone przez użytkownika w każdej iteracji równolegle.|  
|[parallel_for_each — funkcja](concurrency-namespace-functions.md#parallel_for_each)|Przeciążone. `parallel_for_each` stosuje określoną funkcję do każdego elementu w zakresie, w sposób równoległy. Jest to semantycznie równoważne `for_each` działa w programach `std` przestrzeni nazw, z wyjątkiem tej iteracji nad elementami jest wykonywane równolegle i kolejność iteracji jest nieokreślona. Argument `_Func` musi obsługiwać operator wywołania funkcji w postaci `operator()(T)` gdzie parametr `T` jest typem elementu kontenera jest powtarzana.|  
|[parallel_invoke — funkcja](concurrency-namespace-functions.md#parallel_invoke)|Przeciążone. Wykonuje obiektów funkcyjnych, podana jako parametry w równoległych i bloków, dopóki nie została zakończona, wykonywanie. Każdy obiekt funkcji, może być wyrażenie lambda, wskaźnika do funkcji, lub dowolny obiekt obsługujący operator wywołania funkcji z podpisem `void operator()()`.|  
|[parallel_radixsort Function](concurrency-namespace-functions.md#parallel_radixsort)|Przeciążone. Rozmieszcza elementy w określonym zakresie, w innych malejąco według, za pomocą podstawy, algorytm sortowania. To jest funkcja stabilne sortowanie, które wymaga funkcji projekcji, które można poddawać projekcji elementy, które mają być sortowane w niepodpisane klucze podobne do liczby całkowitej. Domyślna Inicjalizacja jest wymagany dla elementów posortowana.|  
|[parallel_reduce — funkcja](concurrency-namespace-functions.md#parallel_reduce)|Przeciążone. Oblicza sumę wszystkich elementów w określonym zakresie przez obliczanie kolejnych sum częściowych, lub oblicza kolejne wyniki częściowe podobnie uzyskanej przy użyciu określonej operacji binarnej sumą, równolegle. `parallel_reduce` przypomina semantycznie `std::accumulate`, z tą różnicą, że wymaga operacja binarna być asocjacyjna i wymaga wartości tożsamości zamiast wartości początkowej.|  
|[parallel_sort — funkcja](concurrency-namespace-functions.md#parallel_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat, jednocześnie. Ta funkcja przypomina semantycznie `std::sort` , jest sortowania na podstawie porównania, niestabilne, w miejscu.|  
|[parallel_transform — funkcja](concurrency-namespace-functions.md#parallel_transform)|Przeciążone. Stosuje określony obiekt funkcji do każdego elementu w zakresie źródłowym lub pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego, równolegle. Tym funkcjonalności są semantycznie równoważne `std::transform`.|  
|[Receive — funkcja](concurrency-namespace-functions.md#receive)|Przeciążone. Ogólny otrzymują implementacji, umożliwiając kontekstu, aby czekać na dane z dokładnie jednego źródła i filtrować wartości, które są akceptowane.|  
|[run_with_cancellation_token — funkcja](concurrency-namespace-functions.md#run_with_cancellation_token)|Wykonuje obiektu funkcyjnego natychmiast w kontekście token danego odwołania.|  
|[send — funkcja](concurrency-namespace-functions.md#send)|Przeciążone. Operacja synchroniczna wysyłania, która czeka, aż element docelowy zaakceptuje lub odrzuci to wiadomość.|  
|[set_ambient_scheduler — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#set_ambient_scheduler)||  
|[set_task_execution_resources Function](concurrency-namespace-functions.md#set_task_execution_resources)|Przeciążone. Ogranicza zasoby wykonywania używane przez środowisko uruchomieniowe współbieżności wewnętrznego wątków na koligacji określony zestaw.<br /><br /> Jest on prawidłowy, aby wywołać tę metodę, tylko, zanim Menedżer zasobów została utworzona lub między dwoma okresy istnienia usługi Resource Manager. Może być wywoływany wielokrotnie tak długo, jak usługi Resource Manager nie istnieje w momencie wywołania. Po ustawieniu limitu koligacji on obowiązuje do następnego wywołania prawidłowy do `set_task_execution_resources` metody.<br /><br /> Maska koligacji nie muszą być podzbiorem Maska koligacji procesu. Koligacja procesu zostanie zaktualizowany, jeśli to konieczne.|  
|[swap — funkcja](concurrency-namespace-functions.md#swap)|Zamienia elementy z dwóch `concurrent_vector` obiektów.|  
|[task_from_exception — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#task_from_exception)||  
|[task_from_result — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#task_from_result)||  
|[Trace_agents_register_name Function](concurrency-namespace-functions.md#trace_agents_register_name)|Kojarzy imię blok komunikatów lub agenta śledzenia zdarzeń systemu Windows.|  
|[try_receive — funkcja](concurrency-namespace-functions.md#try_receive)|Przeciążone. Ogólny spróbuj i odbierania implementacji, umożliwiając kontekstu, aby wyszukiwać dane z dokładnie jednego źródła i filtrować wartości, które są akceptowane. Jeśli dane nie są gotowe, metoda zwróci wartość false.|  
|[WAIT — funkcja](concurrency-namespace-functions.md#wait)|Wstrzymuje działanie bieżącego kontekstu na określoną ilość czasu.|  
|[when_all — funkcja](concurrency-namespace-functions.md#when_all)|Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.|  
|[when_any — funkcja](concurrency-namespace-functions.md#when_any)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie po dowolne zadania dostarczone jako argumenty zakończą się pomyślnie.|  
  
### <a name="operators"></a>Operatory  
  
|Nazwa|Opis|  
|----------|-----------------| 
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora nie jest równa `concurrent_vector` obiektu po prawej stronie.|  
|[Operator & &](concurrency-namespace-operators.md#operator_amp_amp)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy oba zadania dostarczone jako argumenty zakończą się pomyślnie.|  
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Przeciążone. Tworzy zadanie, które zostanie ukończone pomyślnie, gdy jedno z zadań dostarczone jako argumenty zakończą się pomyślnie.|  
|[Operator <](concurrency-namespace-operators.md#operator_lt)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy od `concurrent_vector` obiektu po prawej stronie.|  
|[Operator < =](concurrency-namespace-operators.md#operator_lt_eq)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejszy niż lub równe `concurrent_vector` obiektu po prawej stronie.|  
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest równy `concurrent_vector` obiektu po prawej stronie.|  
|[operator>](concurrency-namespace-operators.md#operator_gt)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest większy niż `concurrent_vector` obiektu po prawej stronie.|  
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora jest większy niż lub równa `concurrent_vector` obiektu po prawej stronie.|  
  
### <a name="constants"></a>Stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|Kategoria zdarzenia ETW opisujący wywoływane przez biblioteki agentów w środowisku uruchomieniowym współbieżności: identyfikator GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07}).|  
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z infrastrukturą lub zadania.|  
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Dostawca ETW identyfikator GUID dla środowiska uruchomieniowego współbieżności.|  
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Wskazuje obsługę interfejsu Menedżera zasobów, zdefiniowane w programie Visual Studio 2010.|  
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|Kategoria GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które nie zostały dokładniej opisane przez inną kategorię.|  
|[ContextEventGuid](concurrency-namespace-constants1.md#contexteventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z kontekstów.|  
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Wartość wskazująca, że oczekiwania nigdy nie powinny wygasać.|  
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Wartość wskazująca, czy upłynął limit czasu oczekiwania.|  
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Specjalna wartość klucza zasad `ContextPriority` wskazujący, że priorytet wątku wszystkie konteksty w ramach harmonogramu zadań powinna być taka sama, jak w przypadku wątku, na którym utworzono harmonogram.|  
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z blokad.|  
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|Specjalna wartość klucza zasad `MinConcurrency` i `MaxConcurrency`. Wartość domyślna to liczba wątków sprzętu na komputerze, w przypadku braku inne ograniczenia.|  
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użytkowania `parallel_for_each` funkcji.|  
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użytkowania `parallel_for` funkcji.|  
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z użytkowania `parallel_invoke` funkcji.|  
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z usługi resource manager.|  
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Kategoria GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z grupy harmonogramu.|  
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z harmonogramu działania.|  
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Kategorię GUID zawierająca opis zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z procesorów wirtualnych.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_list.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](reference-concurrency-runtime.md)

