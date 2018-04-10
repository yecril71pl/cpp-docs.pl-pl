---
title: Współbieżność Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
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
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79a6334dae9835901198387d58316ef34e81ce50
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="concurrency-namespace"></a>concurrency — Przestrzeń nazwy
`Concurrency` Przestrzeń nazw zawiera klasy i funkcje, które zapewniają dostęp do współbieżności środowiska wykonawczego, równoczesnych Architektura programowania dla języka C++. Aby uzyskać więcej informacji, zobacz [współbieżność środowiska wykonawczego](../../../parallel/concrt/concurrency-runtime.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
namespace concurrency;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="namespaces"></a>Namespaces  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CONCURRENCY::Extensibility Namespace](http://msdn.microsoft.com/en-us/16a86ff2-128e-4edf-89e4-38aac79c81f9)||  
  
### <a name="typedefs"></a>Typedefs  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`runtime_object_identity`|Każde wystąpienie wiadomości ma tożsamość następującym sklonować i przekazywane między składnikami obsługi wiadomości. Nie może to być adres obiektu komunikatu.|  
|`task_status`|Typ, który reprezentuje terminali stan zadania. Prawidłowe wartości to `completed` i `canceled`.|  
|`TaskProc`|Abstrakcję podstawowe zadania, zdefiniowany jako `void (__cdecl * TaskProc)(void *)`. A `TaskProc` jest wywoływana w celu wywołania treść zadania.|  
|`TaskProc_t`|Abstrakcję podstawowe zadania, zdefiniowany jako `void (__cdecl * TaskProc_t)(void *)`. A `TaskProc` jest wywoływana w celu wywołania treść zadania.|  
  
### <a name="classes"></a>Klasy  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[affinity_partitioner, klasa](affinity-partitioner-class.md)|`affinity_partitioner` Klasy jest podobna do `static_partitioner` klasy, ale zwiększa koligacji pamięci podręcznej przez siebie mapowania podzakresów na wątków roboczych. Go znacznie zwiększyć wydajność podczas pętli jest ponowne wykonanie przez ten sam zestaw danych i danych mieści się w pamięci podręcznej. Należy pamiętać, że takie same `affinity_partitioner` obiektu musi być używany z kolejnych iteracji pętli równoległej wykonywanym dla określonego zestawu danych, do korzystania z danych lokalizacji.|  
|[agent, klasa](agent-class.md)|Klasa przeznaczona do użycia jako klasę podstawową dla wszystkich agentów niezależne. Służy do ukrycia stanu z innych agentów i interakcji, przy użyciu przekazywania wiadomości.|  
|[auto_partitioner, klasa](auto-partitioner-class.md)|`auto_partitioner` Klasa reprezentuje domyślną metodą `parallel_for`, `parallel_for_each` i `parallel_transform` służy do zakresu ich wykonuje iterację na partycji. Ta metoda partycjonowania employes kradzież równoważenia obciążenia w zakresie jak również na — iteracyjne anulowania.|  
|[bad_target, klasa](bad-target-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy blok komunikatów jest wskaźnik do obiektu docelowego, która jest nieprawidłowa dla wykonywanej operacji.|  
|[call, klasa](call-class.md)|A `call` bloku komunikatów jest źródłem wielu uporządkowane `target_block` który wywołuje funkcję podczas odbierania komunikatu.|  
|[cancellation_token, klasa](cancellation-token-class.md)|`cancellation_token` Klasa reprezentuje możliwość określenia, czy zażądano operacji do anulowania. Skojarzono danego tokenu `task_group`, `structured_task_group`, lub `task` zapewnienie niejawne anulowania. Można go również sondowany anulowania lub wywołania zwrotnego zarejestrowany dla przypadku, gdy skojarzony `cancellation_token_source` zostało anulowane.|  
|[cancellation_token_registration, klasa](cancellation-token-registration-class.md)|`cancellation_token_registration` Klasa reprezentuje wywołanie zwrotne powiadomienia `cancellation_token`. Gdy `register` metody na `cancellation_token` służy do odbierania powiadomień o po wystąpieniu anulowania `cancellation_token_registration` obiekt jest zwracany jako dojścia do wywołania zwrotnego, aby element wywołujący może zażądać wywołania zwrotnego nie jest już być wprowadzane za pośrednictwem stosowania `deregister` metody.|  
|[cancellation_token_source, klasa](cancellation-token-source-class.md)|`cancellation_token_source` Klasa reprezentuje możliwości można anulować operacji anulowania.|  
|[choice, klasa](choice-class.md)|A `choice` bloku komunikatów jest blok wielu źródłach, jednego docelowego reprezentuje przepływ sterowania interakcji z zestawu źródeł. Blokowanie wybór będzie czekać do jednego z wielu źródeł, który zwróci komunikat i rozpropaguje indeksu źródła wytworzonego wiadomości.|  
|[combinable, klasa](combinable-class.md)|`combinable<T>` Obiektu mają na celu dostarczenie prywatnego wątku kopie danych, aby wykonać obliczenia podrzędnych lokalnej wątku zwolnienia blokady podczas algorytmy równoległe. Na koniec operacji równoległej obliczenia podrzędne prywatnego wątku można następnie scalić w wynik końcowy. Ta klasa można zamiast udostępnionego zmiennej i może spowodować zwiększenie wydajności, jeśli byłoby wiele rywalizacji udostępnionego zmiennej.|  
|[concurrent_priority_queue, klasa](concurrent-priority-queue-class.md)|`concurrent_priority_queue` Klasy to kontener udostępniający wiele wątków jednocześnie elementów wypychania i pop. Elementy są zdjęte ze stosu w kolejności priorytetu, której priorytet jest określana przez obiekt podana jako argument szablonu.|  
|[concurrent_queue, klasa](concurrent-queue-class.md)|`concurrent_queue` Klasa jest sekwencji kontenera klasy, która umożliwia w pierwszej, FIFO dostęp do swoich elementów. Umożliwia ona ograniczony zestaw operacji bezpieczne współbieżności, takich jak `push` i `try_pop`.|  
|[concurrent_unordered_map, klasa](concurrent-unordered-map-class.md)|`concurrent_unordered_map` Klasy jest kontenerem bezpieczne współbieżności, który określa sekwencję zróżnicowanych długość elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczny współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.|  
|[concurrent_unordered_multimap, klasa](concurrent-unordered-multimap-class.md)|`concurrent_unordered_multimap` Klasy jest kontenerem bezpieczne współbieżności kontrolujące zróżnicowanych długość sekwencję elementów typu `std::pair<const K, _Element_type>`. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczny współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.|  
|[concurrent_unordered_multiset, klasa](concurrent-unordered-multiset-class.md)|`concurrent_unordered_multiset` Klasy jest kontenerem bezpieczne współbieżności kontrolujące zróżnicowanych długość sekwencję elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczny współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.|  
|[concurrent_unordered_set, klasa](concurrent-unordered-set-class.md)|`concurrent_unordered_set` Klasy jest kontenerem bezpieczne współbieżności kontrolujące zróżnicowanych długość sekwencję elementów typu K. Sekwencja jest reprezentowana w sposób umożliwiający bezpieczny współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.|  
|[concurrent_vector, klasa](concurrent-vector-class.md)|`concurrent_vector` Klasa jest klasą kontenerem sekwencji umożliwiająca losowe dostęp do dowolnych. Umożliwia bezpieczne współbieżności dołączenia, element dostępu, dostęp iteratora i operacji przechodzenia iteratora.|  
|[Context, klasa](context-class.md)|Reprezentuje abstrakcję do kontekstu wykonywania.|  
|[context_self_unblock, klasa](context-self-unblock-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `Unblock` metody `Context` obiektu jest wywoływana z tym samym kontekście. Aby odblokować sam to wskazuje próba w danym kontekście.|  
|[context_unblock_unbalanced, klasa](context-unblock-unbalanced-class.md)|Ta klasa opisuje wyjątek zgłoszony podczas wywołania do `Block` i `Unblock` metody `Context` obiektu nie są poprawnie skojarzone.|  
|[critical_section, klasa](critical-section-class.md)|Mutex nie obsługującą, która jawnie rozpoznaje współbieżności środowiska wykonawczego.|  
|[CurrentScheduler, klasa](currentscheduler-class.md)|Reprezentuje abstrakcję dla bieżącego harmonogramu, skojarzone z kontekstem wywołującego.|  
|[default_scheduler_exists, klasa](default-scheduler-exists-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `Scheduler::SetDefaultSchedulerPolicy` metoda jest wywoływana, gdy domyślnego harmonogramu już istnieje w ramach procesu.|  
|[event, klasa](event-class.md)|Zdarzenie resetowania ręcznego, która jawnie rozpoznaje współbieżności środowiska wykonawczego.|  
|[improper_lock, klasa](improper-lock-class.md)|Ta klasa opisuje wyjątek, jeśli blokada jest nakładana nieprawidłowo.|  
|[improper_scheduler_attach, klasa](improper-scheduler-attach-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `Attach` wywoływana jest metoda `Scheduler` obiektu, który jest już dołączony do bieżącego kontekstu.|  
|[improper_scheduler_detach, klasa](improper-scheduler-detach-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `CurrentScheduler::Detach` metoda jest wywoływana w kontekście, który nie został dołączony do dowolnego harmonogramu przy użyciu `Attach` metody `Scheduler` obiektu.|  
|[improper_scheduler_reference, klasa](improper-scheduler-reference-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `Reference` wywoływana jest metoda `Scheduler` obiekt, który jest zamykany, z kontekstu, która nie wchodzi w skład tego harmonogramu.|  
|[invalid_link_target, klasa](invalid-link-target-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `link_target` wywołania metody obsługi komunikatów bloku, blok komunikatów nie może połączyć się z obiektem docelowym. Może to być wynikiem większej niż liczba łącza, które jest dozwolone w bloku komunikatów lub próba połączenia określony element docelowy dwukrotnie do tego samego źródła.|  
|[invalid_multiple_scheduling, klasa](invalid-multiple-scheduling-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `task_handle` obiekt jest zaplanowane wiele razy przy użyciu `run` metody `task_group` lub `structured_task_group` obiektu bez wywołania pośredniczące `wait` lub `run_and_wait` metody.|  
|[invalid_operation, klasa](invalid-operation-class.md)|Ta klasa opisuje Wystąpił wyjątek zgłoszony, gdy ta operacja jest wykonywana, których nie opisano dokładniej przez inny typ wyjątków zgłaszanych przez współbieżności środowiska wykonawczego.|  
|[invalid_oversubscribe_operation, klasa](invalid-oversubscribe-operation-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy `Context::Oversubscribe` metoda jest wywoływana z `_BeginOversubscription` ustawiona `false` bez uprzedniego wywołania `Context::Oversubscribe` metody z `_BeginOversubscription` ustawiono parametr `true`.|  
|[invalid_scheduler_policy_key, klasa](invalid-scheduler-policy-key-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy jest nieprawidłowa lub nieznany klucz jest przekazywana do `SchedulerPolicy` konstruktora obiektów lub `SetPolicyValue` metody `SchedulerPolicy` przekazanego obiektu klucz, który musi zostać zmienione za pomocą innych środków, takich jak `SetConcurrencyLimits` metody.|  
|[invalid_scheduler_policy_thread_specification, klasa](invalid-scheduler-policy-thread-specification-class.md)|Ta klasa opisuje wyjątek podczas próby ustawić limitów współbieżności `SchedulerPolicy` obiektu tak, aby wartość `MinConcurrency` klucza jest mniejsza niż wartość `MaxConcurrency` klucza.|  
|[invalid_scheduler_policy_value, klasa](invalid-scheduler-policy-value-class.md)|Ta klasa opisuje wyjątek po klucz zasad `SchedulerPolicy` obiektu ma ustawioną nieprawidłową wartością dla tego klucza.|  
|[ISource, klasa](isource-class.md)|`ISource` Klasa jest interfejsem źródła wszystkie bloki. Bloki źródła propagację wiadomości `ITarget` bloków.|  
|[ITarget, klasa](itarget-class.md)|`ITarget` Klasy jest interfejs dla wszystkich docelowych bloków. Bloki docelowy korzystać wiadomości oferowane przez `ISource` bloków.|  
|[join, klasa](join-class.md)|A `join` Blok obsługi wiadomości jest element docelowy jednym wielu źródłach, uporządkowanych `propagator_block` które łączy ze sobą komunikaty typu `T` każdego z jego źródła.|  
|[location, klasa](location-class.md)|Abstrakcja lokalizację fizyczną na sprzęcie.|  
|[message, klasa](message-class.md)|Koperty wiadomości podstawowe zawierającego ładunek danych są przekazywane między bloki komunikatów.|  
|[message_not_found, klasa](message-not-found-class.md)|Ta klasa opisuje wyjątek, gdy nie można odnaleźć żądanej wiadomości jest blokiem obsługi wiadomości.|  
|[message_processor, klasa](message-processor-class.md)|`message_processor` Klasa jest abstrakcyjna klasa podstawowa dla przetwarzania `message` obiektów. Nie ma żadnej gwarancji z kolejnością wiadomości.|  
|[missing_wait, klasa](missing-wait-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy nadal zaplanowane zadania `task_group` lub `structured_task_group` obiektów w czasie tego obiektu wykonuje destruktora. Ten wyjątek nigdy nie zostanie wygenerowany, jeśli osiągnięto destruktor ze względu na stosie rozwinięcia wyniku Wystąpił wyjątek.|  
|[multi_link_registry, klasa](multi-link-registry-class.md)|`multi_link_registry` Obiekt jest `network_link_registry` który zarządza wiele bloków źródła lub wiele bloków docelowej.|  
|[multitype_join, klasa](multitype-join-class.md)|A `multitype_join` bloku komunikatów to wielu źródłach, jednego docelowego blok komunikatów łączy ze sobą wiadomości o różnych typach z każdego z jego źródła i oferuje krotka Scalonej wiadomości do jego elementów docelowych.|  
|[nested_scheduler_missing_detach, klasa](nested-scheduler-missing-detach-class.md)|Ta klasa opisuje wyjątek wykrycie współbieżności środowiska wykonawczego nie zwrócił do wywołania `CurrentScheduler::Detach` metody w kontekście dołączonego do drugiego za pomocą harmonogramu `Attach` metody `Scheduler` obiektu.|  
|[network_link_registry, klasa](network-link-registry-class.md)|`network_link_registry` Abstrakcyjna klasa podstawowa zarządza łącza między bloki źródłowe i docelowe.|  
|[operation_timed_out, klasa](operation-timed-out-class.md)|Ta klasa opisuje wyjątek podczas operacji został przekroczony.|  
|[ordered_message_processor, klasa](ordered-message-processor-class.md)|`ordered_message_processor` Jest `message_processor` umożliwiająca bloki komunikatów do przetwarzania komunikatów w kolejności ich zostały odebrane.|  
|[overwrite_buffer, klasa](overwrite-buffer-class.md)|`overwrite_buffer` Blok komunikatów jest wiele docelowych, wielu źródłach, uporządkowanych `propagator_block` można przechowywać w czasie pojedynczym komunikacie. Nowe komunikaty zastąpienie wcześniej przechowywanych z nich.|  
|[progress_reporter, klasa](progress-reporter-class.md)|Klasa osoby zgłaszającej postępu umożliwia raportowanie postępu powiadomienia określonego typu. Każdy obiekt progress_reporter — jest powiązany z określonej akcji asynchronicznej lub operacji.|  
|[propagator_block, klasa](propagator-block-class.md)|`propagator_block` Klasa jest abstrakcyjna klasa podstawowa dla bloków komunikatów, które są źródłowym i docelowym. Łączy funkcje obu `source_block` i `target_block` klasy.|  
|[reader_writer_lock, klasa](reader-writer-lock-class.md)|Składnik zapisywania — preferencji na podstawie kolejki czytnika-blokadę wirowania tylko lokalnie. Blokada najpierw przyznaje - najpierw out (FIFO) dostępu do zapisywania i starves czytników obciążenie ciągłego składników zapisywania.|  
|[ScheduleGroup, klasa](schedulegroup-class.md)|Reprezentuje abstrakcję do grupy harmonogramu. Grupy harmonogramu uporządkowania zbioru powiązanych pracy tego korzyści z planowany blisko siebie tymczasowo, wykonując inne zadanie w tej samej grupy przed przejściem do innej grupy lub od, wykonując wielu elementów w tej samej grupie na tym samym Lub gniazda fizycznego węzła NUMA.|  
|[Scheduler, klasa](scheduler-class.md)|Reprezentuje abstrakcję harmonogramu współbieżność środowiska wykonawczego.|  
|[scheduler_not_attached, klasa](scheduler-not-attached-class.md)|Ta klasa opisuje wyjątek, jeśli operacja została wykonana, co wymaga harmonogramu jest dołączony do bieżącego kontekstu i jedna nie jest.|  
|[scheduler_resource_allocation_error, klasa](scheduler-resource-allocation-error-class.md)|Ta klasa opisuje wyjątek z powodu błędu można uzyskać zasobu krytycznego współbieżność środowiska wykonawczego.|  
|[scheduler_worker_creation_error, klasa](scheduler-worker-creation-error-class.md)|Ta klasa opisuje wyjątek z powodu błędu tworzenia kontekstu wykonywania procesu roboczego współbieżność środowiska wykonawczego.|  
|[SchedulerPolicy, klasa](schedulerpolicy-class.md)|`SchedulerPolicy` Klasa zawiera zbiór pary klucz wartość, po jednej dla każdego elementu zasad, które określają zachowanie wystąpienia harmonogramu.|  
|[simple_partitioner, klasa](simple-partitioner-class.md)|`simple_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu iterowane przez `parallel_for`. Obiekt partitioner dzieli zakres fragmentów tak, aby każdy fragment jest co najmniej liczby iteracji określony przez rozmiar fragmentu.|  
|[single_assignment, klasa](single-assignment-class.md)|A `single_assignment` blok komunikatów jest wiele docelowych, wielu źródłach, uporządkowanych `propagator_block` można przechowywać jeden zapisu — po `message`.|  
|[single_link_registry, klasa](single-link-registry-class.md)|`single_link_registry` Obiekt jest `network_link_registry` który zarządza tylko jeden blok źródłowa lub docelowa.|  
|[source_block, klasa](source-block-class.md)|`source_block` Klasa jest abstrakcyjna klasa podstawowa dla bloków tylko do źródła. Ta klasa dostarcza łącze podstawowe funkcje zarządzania jako również jako wspólne sprawdzanie błędów.|  
|[source_link_manager, klasa](source-link-manager-class.md)|`source_link_manager` Obiektu zarządza komunikatów łączy sieciowych bloku do `ISource` bloków.|  
|[static_partitioner, klasa](static-partitioner-class.md)|`static_partitioner` Klasa reprezentuje partycjonowania statycznego zakresu iterowane przez `parallel_for`. Obiekt partitioner dzieli zakres na tyle fragmenty są dostępne dla harmonogramu underyling pracowników.|  
|[structured_task_group, klasa](structured-task-group-class.md)|`structured_task_group` Klasa reprezentuje kolekcję uporządkowany równoległych pracy. Można dodać do kolejki na poszczególnych zadań równoległych `structured_task_group` przy użyciu `task_handle` obiekty i zaczekaj na ich zakończenie lub kliknij przycisk Anuluj grupy zadań przed ich zakończeniem wykonywania, która spowoduje przerwanie wszystkich zadań, które nie zostały uruchomione wykonywania.|  
|[target_block, klasa](target-block-class.md)|`target_block` Klasa jest abstrakcyjna klasa podstawowa, którego łącze podstawowe funkcje zarządzania i tylko sprawdzanie błędów dla elementu docelowego blokuje.|  
|[task, klasa (środowisko uruchomieniowe współbieżności)](task-class.md)|Biblioteka równoległych wzorców (PLL) `task` klasy. A `task` obiekt reprezentuje pracy, które mogą być wykonywane asynchronicznie, a równocześnie z innymi zadaniami i współbieżność środowiska wykonawczego pracy równoległej utworzonych przez algorytmy równoległe. Tworzy wynik typu `_ResultType` na pomyślne zakończenie. Zadania typu `task<void>` utworzyć żadnego wyniku. Zadania można czas potrzebny na i anulowane niezależnie od innych zadań. Mogą być składane również z innymi zadaniami za pomocą kontynuacje (`then`), a sprzężenia (`when_all`) i wyboru (`when_any`) wzorce.|  
|[task_canceled, klasa](task-canceled-class.md)|Ta klasa opisuje wyjątek zgłoszony przez warstwy zadania PPL, aby wymusić, aby anulować bieżące zadanie. Również jest generowany przez `get()` metoda [zadań](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f), anulowane zadania.|  
|[task_completion_event, klasa](task-completion-event-class.md)|`task_completion_event` Klasa umożliwia opóźnienie wykonania zadania, dopóki spełniony jest warunek lub uruchomić zadanie w odpowiedzi na zdarzenie zewnętrzne.|  
|[task_continuation_context, klasa](task-continuation-context-class.md)|`task_continuation_context` Klasa służy do określenia, gdzie chcesz kontynuacji do wykonania. Jest tylko warto użyć tej klasy z aplikacji platformy uniwersalnej systemu Windows. W przypadku aplikacji z systemem innym niż Windows Runtime kontekstu wykonywania kontynuacji zadań jest określone przez środowisko uruchomieniowe i nie można skonfigurować.|  
|[task_group — klasa](task-group-class.md)|`task_group` Klasa reprezentuje kolekcję równoległych pracy, które mogą być obsługiwane lub anulowane.|  
|[task_handle, klasa](task-handle-class.md)|`task_handle` Klasa reprezentuje element indywidualnej pracy równoległych. Hermetyzuje zgodnie z instrukcjami i dane wymagane do wykonywania pracy.|  
|[task_options, klasa (środowisko uruchomieniowe współbieżności)](task-options-class-concurrency-runtime.md)|Reprezentuje dozwolonych opcje tworzenia zadania|  
|[timer, klasa](timer-class.md)|A `timer` Blok obsługi wiadomości jest element docelowy jednym `source_block` mogą wysyłać wiadomości do jego obiektu docelowego po określonym okresie czasu lub w określonych odstępach czasu.|  
|[transformer, klasa](transformer-class.md)|A `transformer` Blok obsługi wiadomości jest element docelowy jednym wielu źródłach, uporządkowanych `propagator_block` co mogą akceptować wiadomości danego typu i jest w stanie przechowywania niepowiązany liczba wiadomości jest innego typu.|  
|[Klasa unbounded_buffer](unbounded-buffer-class.md)|`unbounded_buffer` Blok komunikatów jest wiele docelowych, wielu źródłach, uporządkowanych `propagator_block` można przechowywać niepowiązany liczba komunikatów.|  
|[unsupported_os, klasa](unsupported-os-class.md)|Ta klasa opisuje wyjątek wywoływany, gdy jest używany nieobsługiwany system operacyjny.|  
  
### <a name="structures"></a>Struktury  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[DispatchState, struktura](dispatchstate-structure.md)|`DispatchState` Struktury jest używana do przesyłania stanu, tak aby `IExecutionContext::Dispatch` metody. Zawiera opis sytuacji, w którym `Dispatch` jest wywoływana metoda `IExecutionContext` interfejsu.|  
|[IExecutionContext, struktura](iexecutioncontext-structure.md)|Interfejs do kontekstu wykonywania, który można uruchomić na danym procesorów wirtualnych i wspólnie można przełączyć kontekstu.|  
|[IExecutionResource, struktura](iexecutionresource-structure.md)|Abstrakcja wątku sprzętu.|  
|[IResourceManager, struktura](iresourcemanager-structure.md)|Interfejs do współbieżności środowiska wykonawczego Resource Manager. Jest to interfejs, za pomocą którego komunikują się z Menedżerem zasobów transfery danych.|  
|[IScheduler, struktura](ischeduler-structure.md)|Interfejs abstrakcję harmonogram pracy. Współbieżność środowiska wykonawczego Resource Manager używa tego interfejsu do komunikowania się z planiści pracy.|  
|[ISchedulerProxy, struktura](ischedulerproxy-structure.md)|Interfejs, za pomocą którego planiści komunikować się z Menedżerem zasobów współbieżność środowiska wykonawczego do negocjowania alokacji zasobów.|  
|[IThreadProxy, struktura](ithreadproxy-structure.md)|Abstrakcja dla wątku wykonywania. W zależności od `SchedulerType` klucza zasad harmonogramu tworzenia, Menedżer zasobów zostanie przyznać użytkownikowi proxy wątku, który nie jest obsługiwana przez regularne wątku Win32 lub schedulable wątku trybu użytkownika (UMS). UMS wątki są obsługiwane w 64-bitowych systemach operacyjnych z wersji Windows 7 lub nowszy.|  
|[ITopologyExecutionResource, struktura](itopologyexecutionresource-structure.md)|Interfejs do zasobu wykonywania zdefiniowanej przez Menedżera zasobów.|  
|[ITopologyNode, struktura](itopologynode-structure.md)|Interfejs do węzła topologii, zgodnie z definicją przez Menedżera zasobów. Węzeł zawiera jeden lub więcej zasobów do wykonania.|  
|[IUMSCompletionList, struktura](iumscompletionlist-structure.md)|Reprezentuje listę uzupełniania UMS. Podczas planowania wyznaczony harmonogramu UMS wątku bloków, aby podjąć decyzję dotyczącą tego, jaki można zaplanować na komputerze podstawowym głównego procesora wirtualnego podczas oryginalnego wątek jest zablokowany wywoływane jest kontekstu. Gdy odblokowuje oryginalnego wątku, system operacyjny kolejek do listy zakończenia, która jest dostępna za pośrednictwem tego interfejsu. Harmonogram można badać listy uzupełniania na wyznaczonych kontekstu planowania lub w innym miejscu przeszukiwanych do pracy.|  
|[IUMSScheduler, struktura](iumsscheduler-structure.md)|Interfejs abstrakcję harmonogram pracy, który chce współbieżność środowiska wykonawczego Resource Manager ręcznie, jego schedulable wątków (UMS) trybu użytkownika. Menedżer zasobów używa tego interfejsu do komunikowania się z planiści wątku UMS. `IUMSScheduler` Dziedziczy interfejs `IScheduler` interfejsu.|  
|[IUMSThreadProxy, struktura](iumsthreadproxy-structure.md)|Abstrakcja dla wątku wykonywania. Jeśli Twoje harmonogramu przyznawane schedulable wątków (UMS) trybu użytkownika, należy ustawić wartość elementu zasad harmonogramu `SchedulerKind` do `UmsThreadDefault`i wdrożenie `IUMSScheduler` interfejsu. Wątki UMS są tylko w obsługiwanych systemach operacyjnych 64-bitowej wersji systemu Windows 7 lub nowszy.|  
|[IUMSUnblockNotification, struktura](iumsunblocknotification-structure.md)|Reprezentuje powiadomienie z Menedżera zasobów czy zablokowane i wyzwalane powrotu do harmonogramu wyznaczony planowania kontekstu serwera proxy wątek został odblokowany i jest gotowy do zaplanowania. Ten interfejs jest nieprawidłowy, kiedy kontekstu wykonywania skojarzony proxy wątku zwrócone z `GetContext` zmiany harmonogramu metody.|  
|[IVirtualProcessorRoot, struktura](ivirtualprocessorroot-structure.md)|Abstrakcja wątku sprzętu, na którym serwer proxy wątek może zostać uruchomiony.|  
|[scheduler_interface, struktura](scheduler-interface-structure.md)|Interfejs harmonogramu|  
|[scheduler_ptr, struktura (środowisko uruchomieniowe współbieżności)](scheduler-ptr-structure-concurrency-runtime.md)|Reprezentuje wskaźnik do harmonogramu. Ta klasa istnieje umożliwia specyfikację udostępnionego okres istnienia przy użyciu shared_ptr lub zwykłe odwołanie przy użyciu wskaźnika raw.|  
  
### <a name="enumerations"></a>Wyliczenia  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[agent_status](concurrency-namespace-enums.md#agent_status)|Nieprawidłowy stan dla `agent`.|  
|[Agents_EventType](concurrency-namespace-enums.md#agents_eventtype)|Typy zdarzeń, które mogą być śledzone korzystanie z funkcji śledzenia biblioteki agentów|  
|[ConcRT_EventType](concurrency-namespace-enums.md#concrt_eventtype)|Typy zdarzeń, które mogą być śledzone korzystanie z funkcji śledzenia współbieżności środowiska wykonawczego.|  
|[Concrt_TraceFlags](concurrency-namespace-enums.md#concrt_traceflags)|Flagi śledzenia dla typów zdarzeń|  
|[CriticalRegionType](concurrency-namespace-enums.md#criticalregiontype)|Typ krytyczne regionie, w którym znajduje się w kontekście.|  
|[DynamicProgressFeedbackType](concurrency-namespace-enums.md#dynamicprogressfeedbacktype)|Używane przez `DynamicProgressFeedback` na podstawie zasad do opisywania, czy zasoby harmonogramu zostanie rebalanced zgodnie z informacje statystyczne zebrane z harmonogramu lub tylko na przechodzenie do i stanu bezczynności za pośrednictwem wywołania procesorówwirtualnych`Activate` i `Deactivate` metody `IVirtualProcessorRoot` interfejsu. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
|[join_type](concurrency-namespace-enums.md#join_type)|Typ `join` bloku obsługi wiadomości.|  
|[message_status](concurrency-namespace-enums.md#message_status)|Nieprawidłowa odpowiedzi dla oferty `message` obiektu do bloku.|  
|[PolicyElementKey](concurrency-namespace-enums.md#policyelementkey)|Klucze zasad opisujące aspekty zachowania harmonogramu. Każdy element zasad jest opisane przez pary klucz wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływ na planiści zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).|  
|[SchedulerType](concurrency-namespace-enums.md#schedulertype)|Używane przez `SchedulerKind` zasad do opisu typu wątków powinien wykorzystujące dla podstawowej kontekstów wykonywania dla harmonogramu. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
|[SchedulingProtocolType](concurrency-namespace-enums.md#schedulingprotocoltype)|Używane przez `SchedulingProtocol` zasad do opisywania, który algorytm planowania, które zostaną użyte dla harmonogramu. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
|[SwitchingProxyState](concurrency-namespace-enums.md#switchingproxystate)|Używany do określenia stanu, w którym jest serwer proxy wątku, podczas jej wykonywania przełączanie kontekstu wspólnych do serwera proxy w innym wątku.|  
|[task_group_status](concurrency-namespace-enums.md#task_group_status)|Opisuje stan wykonywania `task_group` lub `structured_task_group` obiektu. Wartość tego typu jest zwracany przez wiele metod, które oczekiwanie na zadania zaplanowane do grupy zadań do wykonania.|  
|[WinRTInitializationType](concurrency-namespace-enums.md#winrtinitializationtype)|Używane przez `WinRTInitialization` zasad do opisywania, czy i jak środowiska uruchomieniowego systemu Windows zostanie zainicjowana na harmonogram wątków dla aplikacji, która działa w systemach operacyjnych z wersją systemu Windows 8 lub nowszy. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md#policyelementkey).|  
  
### <a name="functions"></a>Funkcje  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[ALLOC — funkcja](concurrency-namespace-functions.md#alloc)|Przydziela bloku pamięci o wielkości określone z Suballocator buforowanie współbieżności środowiska wykonawczego.|  
|[asend — funkcja](concurrency-namespace-functions.md#asend)|Przeciążone. Operacja asynchronicznego wysyłania, która planuje zadania propagację danych blok docelowy.|  
|[cancel_current_task Function](concurrency-namespace-functions.md#cancel_current_task)|Umożliwia anulowanie aktualnie wykonywanego zadania. Ta funkcja może zostać wywołana z w treści zadania do przerwania wykonywania zadań i spowodować, że wprowadzić `canceled` stanu.<br /><br /> Nie jest obsługiwany scenariusz do wywołania tej funkcji, jeśli nie znajdujesz się w treści `task`. W ten sposób spowoduje niezdefiniowane zachowanie, takich jak awarię lub zawieszenie aplikacji.|  
|[create_async Function](concurrency-namespace-functions.md#create_async)|Tworzy konstrukcję asynchroniczne środowiska wykonawczego systemu Windows oparte na obiekt lambda lub funkcja podana przez użytkownika. Zwracany typ `create_async` jest jednym z dwóch `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, lub `IAsyncOperationWithProgress<TResult, TProgress>^` oparte na podpis lambda przekazywany do metody.|  
|[create_task Function](concurrency-namespace-functions.md#create_task)|Przeciążone. Tworzy PPL [zadań](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f) obiektu. `create_task` mogą być używane wszędzie możesz korzystać z konstruktora zadań. Jest udostępniana głównie udogodnienie, ponieważ umożliwia używanie `auto` — słowo kluczowe podczas tworzenia zadania.|  
|[Createresourcemanager — funkcja](concurrency-namespace-functions.md#createresourcemanager)|Zwraca interfejs, który reprezentuje pojedyncze wystąpienie Menedżera zasobów współbieżność środowiska wykonawczego. Menedżer zasobów jest odpowiedzialny za przydzielanie zasobów do transfery danych, które chcesz współpracować ze sobą.|  
|[Disabletracing — funkcja](concurrency-namespace-functions.md#disabletracing)|Wyłącza śledzenie współbieżność środowiska wykonawczego. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest niezarejestrowany domyślnie.|  
|[Enabletracing — funkcja](concurrency-namespace-functions.md#enabletracing)|Umożliwia śledzenie współbieżność środowiska wykonawczego. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest teraz włączona domyślnie.|  
|[Free — funkcja](concurrency-namespace-functions.md#free)|Zwalnia blok pamięci przydzielony wcześniej przez `Alloc` metodę Suballocator buforowanie współbieżności środowiska wykonawczego.|  
|[get_ambient_scheduler — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#get_ambient_scheduler)||  
|[GetExecutionContextId Function](concurrency-namespace-functions.md#getexecutioncontextid)|Zwraca unikatowy identyfikator, który można przypisać do kontekstu wykonywania, który implementuje `IExecutionContext` interfejsu.|  
|[GetOSVersion Function](concurrency-namespace-functions.md#getosversion)|Zwraca informacje o wersji systemu operacyjnego.|  
|[GetProcessorCount Function](concurrency-namespace-functions.md#getprocessorcount)|Zwraca liczbę wątków sprzętu na podstawowym systemie.|  
|[GetProcessorNodeCount Function](concurrency-namespace-functions.md#getprocessornodecount)|Zwraca liczbę węzłów NUMA lub pakietów procesora na podstawowym systemie.|  
|[GetSchedulerId Function](concurrency-namespace-functions.md#getschedulerid)|Zwraca unikatowy identyfikator, który można przypisać do harmonogramu, który implementuje `IScheduler` interfejsu.|  
|[interruption_point Function](concurrency-namespace-functions.md#interruption_point)|Tworzy punkt przerwania do anulowania. Jeśli trwa anulowanie w tym kontekście, w którym ta funkcja jest wywoływana, zgłosi wyjątek wewnętrzny, który przerywa wykonywanie aktualnie wykonywane równolegle pracy. Jeśli anulowania nie jest w toku, funkcja nie działa.|  
|[is_current_task_group_canceling Function](concurrency-namespace-functions.md#is_current_task_group_canceling)|Zwraca wskazaniem, czy zadanie grupy, które jest aktualnie wykonywany wbudowany w bieżącym kontekście jest pośrodku active anulowania (lub zostanie wkrótce). Należy pamiętać, że jeśli grupa zadań wykonywanych aktualnie wbudowany w bieżącym kontekście `false` zostaną zwrócone.|  
|[make_choice — funkcja](concurrency-namespace-functions.md#make_choice)|Przeciążone. Konstruuje `choice` bloku komunikatów z opcjonalną `Scheduler` lub `ScheduleGroup` i dwa lub więcej źródeł danych wejściowych.|  
|[make_greedy_join — funkcja](concurrency-namespace-functions.md#make_greedy_join)|Przeciążone. Konstruuje `greedy multitype_join` bloku komunikatów z opcjonalną `Scheduler` lub `ScheduleGroup` i dwa lub więcej źródeł danych wejściowych.|  
|[make_join — funkcja](concurrency-namespace-functions.md#make_join)|Przeciążone. Konstruuje `non_greedy multitype_join` bloku komunikatów z opcjonalną `Scheduler` lub `ScheduleGroup` i dwa lub więcej źródeł danych wejściowych.|  
|[make_task — funkcja](concurrency-namespace-functions.md#make_task)|Fabryka metodę tworzenia `task_handle` obiektu.|  
|[parallel_buffered_sort Function](concurrency-namespace-functions.md#parallel_buffered_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w kolejności nondescending lub zgodnie z kryterium porządkowania określony przez predykat binarnego, równolegle. Ta funkcja przypomina semantycznie `std::sort` w tym z tą różnicą, że konieczne jest sortowania na podstawie porównania, niestabilny, w miejscu `O(n)` dodatkowe miejsce i wymaga inicjowanie domyślnych elementów sortowane.|  
|[parallel_for — funkcja](concurrency-namespace-functions.md#parallel_for)|Przeciążone. `parallel_for` wykonuje iterację na zakres indeksy i wykonuje funkcję dostarczone przez użytkownika w każdej iteracji równolegle.|  
|[parallel_for_each — funkcja](concurrency-namespace-functions.md#parallel_for_each)|Przeciążone. `parallel_for_each` stosuje funkcję do każdego elementu w zakresie, równolegle. Jest to równoważne semantycznie `for_each` działać w `std` przestrzeni nazw, z wyjątkiem tego iteracji w elementów jest wykonywane równolegle i kolejność iteracji jest nieokreślony. Argument `_Func` musi obsługiwać operator wywołania funkcji w formę `operator()(T)` gdzie parametr `T` jest typem elementu kontenera jest iterowane za pośrednictwem.|  
|[parallel_invoke Function](concurrency-namespace-functions.md#parallel_invoke)|Przeciążone. Wykonuje obiekty funkcji podana jako parametry w równolegle i bloków, dopóki nie zostało ukończone, wykonywania. Każdy obiekt funkcja może być wyrażenie lambda wskaźnika do funkcji, lub dowolnego obiektu spełniającego operator wywołania funkcji z podpisem `void operator()()`.|  
|[parallel_radixsort Function](concurrency-namespace-functions.md#parallel_radixsort)|Przeciążone. Rozmieszcza elementy w określonym zakresie z systemem innym niż malejącej przy użyciu podstawa, algorytm sortowania. Jest to funkcja stabilna sortowania, które wymaga funkcji projekcji, które można wyświetlać elementy, które można sortować według kluczy typu Liczba całkowita bez znaku. Inicjowanie domyślnych jest wymagana dla elementów sortowane.|  
|[parallel_reduce Function](concurrency-namespace-functions.md#parallel_reduce)|Przeciążone. Oblicza sumę wszystkich elementów w określonym zakresie przez obliczanie sum częściowych kolejnych lub oblicza wynik kolejne wyniki częściowe podobnie uzyskany przy użyciu określonej operacji binarnych sumą, równolegle. `parallel_reduce` przypomina semantycznie `std::accumulate`, ale wymaga operację binarną być asocjacyjnej i wymaga wartości tożsamości, zamiast wartości początkowej.|  
|[parallel_sort Function](concurrency-namespace-functions.md#parallel_sort)|Przeciążone. Rozmieszcza elementy w określonym zakresie w kolejności nondescending lub zgodnie z kryterium porządkowania określony przez predykat binarnego, równolegle. Ta funkcja przypomina semantycznie `std::sort` w tym jest sortowania na podstawie porównania, niestabilny, w miejscu.|  
|[parallel_transform — funkcja](concurrency-namespace-functions.md#parallel_transform)|Przeciążone. Dotyczy obiektu o określonej funkcji, do każdego elementu w zakresie źródła lub dwa elementy z dwóch zakresów i kopiuje zwracanych wartości obiektu funkcji do zakresu docelowego równolegle. Tym funkcjonalności jest semantycznie równoważne `std::transform`.|  
|[Receive — funkcja](concurrency-namespace-functions.md#receive)|Przeciążone. Ogólny odbierać implementacji, umożliwiając kontekstu, poczekaj na danych z dokładnie jednego źródła i filtrowanie ich wartości, które są akceptowane.|  
|[run_with_cancellation_token — funkcja](concurrency-namespace-functions.md#run_with_cancellation_token)|Wykonuje obiektem funkcji natychmiast w kontekście token danego anulowania.|  
|[send — funkcja](concurrency-namespace-functions.md#send)|Przeciążone. Operacja synchroniczna wysyłania, która czeka, aż docelowy albo zaakceptuje lub odrzuci komunikat.|  
|[set_ambient_scheduler — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#set_ambient_scheduler)||  
|[set_task_execution_resources Function](concurrency-namespace-functions.md#set_task_execution_resources)|Przeciążone. Ogranicza wykonywania zasoby używane przez współbieżność środowiska wykonawczego wewnętrzny wątków na koligacji określony zestaw.<br /><br /> Jest on prawidłowy aby wywołać tę metodę, tylko przed utworzeniem Resource Manager lub między dwa okresy Menedżera zasobów. Go może być wywoływany wielokrotnie tak długo, jak Menedżer zasobów nie istnieje w tym czasie wywołania. Po ustawieniu limitu koligacji on obowiązuje aż do następnego wywołania prawidłowe `set_task_execution_resources` metody.<br /><br /> Podana maska koligacji nie musi być podzbiorem Maska koligacji procesu. Koligacja procesu zostanie zaktualizowany w razie potrzeby.|  
|[swap — funkcja](concurrency-namespace-functions.md#swap)|Zamienia elementy dwóch `concurrent_vector` obiektów.|  
|[task_from_exception — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#task_from_exception)||  
|[task_from_result — funkcja (współbieżność środowiska wykonawczego)](concurrency-namespace-functions.md#task_from_result)||  
|[Trace_agents_register_name Function](concurrency-namespace-functions.md#trace_agents_register_name)|Kojarzy imię bloku komunikatów lub agenta w śledzenia zdarzeń systemu Windows.|  
|[try_receive — funkcja](concurrency-namespace-functions.md#try_receive)|Przeciążone. Ogólny spróbuj odbierania implementacji, umożliwiając kontekstu wyszukiwać dane z dokładnie jednego źródła i filtrowanie ich wartości, które są akceptowane. W przypadku danych nie jest gotowy, metoda zwraca wartość false.|  
|[WAIT — funkcja](concurrency-namespace-functions.md#wait)|Wstrzymuje bieżącego kontekstu dla określonego przedziału czasu.|  
|[when_all — funkcja](concurrency-namespace-functions.md#when_all)|Tworzy zadanie, które zostanie zakończony pomyślnie, gdy wszystkie zadania podana jako argumenty pomyślnie ukończona.|  
|[when_any Function](concurrency-namespace-functions.md#when_any)|Przeciążone. Tworzy zadanie, które zostanie zakończony pomyślnie, gdy zadań dostarczony jako argumenty zakończy się pomyślnie.|  
  
### <a name="operators"></a>Operatory  
  
|Nazwa|Opis|  
|----------|-----------------| 
|[operator!=](concurrency-namespace-operators.md#operator_neq)|Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora nie jest równa `concurrent_vector` obiektu po prawej stronie.|  
|[Operator & &](concurrency-namespace-operators.md#operator_amp_amp)|Przeciążone. Tworzy zadanie, które zostanie zakończony pomyślnie, gdy oba zadania podana jako argumenty pomyślnie ukończona.|  
|[operator&#124;&#124;](concurrency-namespace-operators.md#operator_lor)|Przeciążone. Tworzy zadanie, które zostanie zakończony pomyślnie, jeśli jedno z zadań dostarczony jako argumenty zakończy się pomyślnie.|  
|[Operator <](concurrency-namespace-operators.md#operator_lt)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejsza niż `concurrent_vector` obiektu po prawej stronie.|  
|[operator<=](concurrency-namespace-operators.md#operator_lt_eq)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest mniejsze niż lub równe `concurrent_vector` obiektu po prawej stronie.|  
|[operator==](concurrency-namespace-operators.md#operator_eq_eq)|Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora jest równa `concurrent_vector` obiektu po prawej stronie.|  
|[operator>](concurrency-namespace-operators.md#operator_gt)|Sprawdza, czy `concurrent_vector` obiektu po lewej stronie operatora jest większa niż `concurrent_vector` obiektu po prawej stronie.|  
|[operator>=](concurrency-namespace-operators.md#operator_lt_eq)|Sprawdza, czy `concurrent_vector` obiekt po lewej stronie operatora jest większa niż lub równa `concurrent_vector` obiektu po prawej stronie.|  
  
### <a name="constants"></a>Stałe  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[AgentEventGuid](concurrency-namespace-constants1.md#agenteventguid)|Kategoria zdarzenia ETW opisujący wywoływane przez biblioteki agentów współbieżność środowiska wykonawczego identyfikatora GUID ({B9B5B78C-0713-4898-A21A-C67949DCED07}).|  
|[ChoreEventGuid](concurrency-namespace-constants1.md#choreeventguid)|Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z zadań i zadań.|  
|[ConcRT_ProviderGuid](concurrency-namespace-constants1.md#concrt_providerguid)|Dostawca ETW identyfikatora GUID dla współbieżności środowiska wykonawczego.|  
|[CONCRT_RM_VERSION_1](concurrency-namespace-constants1.md#concrt_rm_version_1)|Wskazuje obsługi interfejsu Menedżera zasobów zdefiniowane w programie Visual Studio 2010.|  
|[ConcRTEventGuid](concurrency-namespace-constants1.md#concrteventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które nie zostały opisane bardziej szczegółowo w innej kategorii.|  
|[Contexteventguid —](concurrency-namespace-constants1.md#contexteventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z kontekstami.|  
|[COOPERATIVE_TIMEOUT_INFINITE](concurrency-namespace-constants1.md#cooperative_timeout_infinite)|Wartość wskazująca, której oczekiwania nigdy nie ma limitu czasu.|  
|[COOPERATIVE_WAIT_TIMEOUT](concurrency-namespace-constants1.md#cooperative_wait_timeout)|Wartość wskazująca, że oczekiwania upłynął limit czasu.|  
|[INHERIT_THREAD_PRIORITY](concurrency-namespace-constants1.md#inherit_thread_priority)|Specjalna wartość dla klucza zasad `ContextPriority` wskazującą, czy priorytet wątku wszystkie konteksty w harmonogramie powinna być taka sama jak w wątku, w której został utworzony harmonogram.|  
|[LockEventGuid](concurrency-namespace-constants1.md#lockeventguid)|Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z blokad.|  
|[MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources)|Specjalna wartość kluczy zasad `MinConcurrency` i `MaxConcurrency`. Wartość domyślna to liczba wątków sprzętu na komputerze w przypadku braku inne ograniczenia.|  
|[PPLParallelForeachEventGuid](concurrency-namespace-constants1.md#pplparallelforeacheventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z użycie `parallel_for_each` funkcji.|  
|[PPLParallelForEventGuid](concurrency-namespace-constants1.md#pplparallelforeventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z użycie `parallel_for` funkcji.|  
|[PPLParallelInvokeEventGuid](concurrency-namespace-constants1.md#pplparallelinvokeeventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z użycie `parallel_invoke` funkcji.|  
|[ResourceManagerEventGuid](concurrency-namespace-constants1.md#resourcemanagereventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z Menedżera zasobów.|  
|[ScheduleGroupEventGuid](concurrency-namespace-constants1.md#schedulegroupeventguid)|Kategorię GUID opisujące zdarzenia ETW wywoływane przez środowisko uruchomieniowe współbieżności, które są bezpośrednio związane z grupy harmonogramu.|  
|[SchedulerEventGuid](concurrency-namespace-constants1.md#schedulereventguid)|Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z działania harmonogramu.|  
|[VirtualProcessorEventGuid](concurrency-namespace-constants1.md#virtualprocessoreventguid)|Kategoria GUID opisujące zdarzenia ETW wywoływane przez współbieżność środowiska wykonawczego, które są bezpośrednio związane z procesorów wirtualnych.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** agents.h, concrt.h, concrtrm.h, concurrent_priority_queue.h, concurrent_queue.h, concurrent_unordered_map.h, concurrent_unordered_set.h, concurrent_vector.h, internal_concurrent_hash.h, internal_split_ordered_list.h, ppl.h, pplcancellation_token.h, pplconcrt.h, pplinterface.h, ppltasks.h  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](reference-concurrency-runtime.md)

