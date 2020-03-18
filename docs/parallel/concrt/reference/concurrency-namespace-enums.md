---
title: Wyliczenia przestrzeni nazw współbieżności
ms.date: 11/04/2016
f1_keywords:
- CONCRT/concurrency::Agents_EventType
- CONCRT/concurrency::Concrt_TraceFlags
- CONCRT/concurrency::CriticalRegionType
- CONCRT/concurrency::PolicyElementKey
- CONCRT/concurrency::SchedulerType
- CONCRT/concurrency::SwitchingProxyState
- CONCRT/concurrency::WinRTInitializationType
- CONCRT/concurrency::join_type
- CONCRT/concurrency::message_status Enumeration
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
ms.openlocfilehash: 716c2d03e6d1ff67566bd28e5931996ea2d400af
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422235"
---
# <a name="concurrency-namespace-enums"></a>Wyliczenia przestrzeni nazw współbieżności

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType —](#criticalregiontype)|[DynamicProgressFeedbackType —](#dynamicprogressfeedbacktype)|[PolicyElementKey —](#policyelementkey)|
|[SchedulerType —](#schedulertype)|[SchedulingProtocolType —](#schedulingprotocoltype)|[SwitchingProxyState —](#switchingproxystate)|
|[WinRTInitializationType —](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status"></a>agent_status, Wyliczenie

Prawidłowe Stany `agent`.

```cpp
enum agent_status;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`agent_canceled`|`agent` zostało anulowane.|
|`agent_created`|`agent` został utworzony, ale nie został uruchomiony.|
|`agent_done`|`agent` zakończono bez anulowania.|
|`agent_runnable`|`agent` zostało uruchomione, ale nie wprowadzono jej `run` metodzie.|
|`agent_started`|`agent` został uruchomiony.|

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [agenci asynchroniczni](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="agents_eventtype"></a>Agents_EventType, Wyliczenie

Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanej przez bibliotekę agentów

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Typ zdarzenia, który reprezentuje Tworzenie obiektu|
|`AGENTS_EVENT_DESTROY`|Typ zdarzenia, który reprezentuje usunięcie obiektu|
|`AGENTS_EVENT_END`|Typ zdarzenia, który reprezentuje zakończenie niektórych operacji przetwarzania|
|`AGENTS_EVENT_LINK`|Typ zdarzenia, który reprezentuje powiązanie bloków komunikatów|
|`AGENTS_EVENT_NAME`|Typ zdarzenia, który reprezentuje nazwę obiektu|
|`AGENTS_EVENT_SCHEDULE`|Typ zdarzenia, który reprezentuje planowanie procesu|
|`AGENTS_EVENT_START`|Typ zdarzenia, który reprezentuje inicjację pewnego przetwarzania|
|`AGENTS_EVENT_UNLINK`|Typ zdarzenia, który reprezentuje odłączenie bloków komunikatów|

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="concrt_eventtype"></a>ConcRT_EventType, Wyliczenie

Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanej przez środowisko uruchomieniowe współbieżności.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Typ zdarzenia, który reprezentuje czynność dołączenia do harmonogramu.|
|`CONCRT_EVENT_BLOCK`|Typ zdarzenia, który reprezentuje czynność blokowania kontekstu.|
|`CONCRT_EVENT_DETACH`|Typ zdarzenia, który reprezentuje czynność odłączenia od harmonogramu.|
|`CONCRT_EVENT_END`|Typ zdarzenia, który oznacza początek pary zdarzeń początek/koniec.|
|`CONCRT_EVENT_GENERIC`|Typ zdarzenia używany dla różnych zdarzeń.|
|`CONCRT_EVENT_IDLE`|Typ zdarzenia, który reprezentuje czynność kontekstu, która staje się bezczynna.|
|`CONCRT_EVENT_START`|Typ zdarzenia, który oznacza początek pary zdarzeń początek/koniec.|
|`CONCRT_EVENT_UNBLOCK`|Typ zdarzenia, który reprezentuje czynność odblokowywania kontekstu.|
|`CONCRT_EVENT_YIELD`|Typ zdarzenia, który reprezentuje czynność dla kontekstu.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h **przestrzeń nazw:** współbieżność

## <a name="concrt_traceflags"></a>Concrt_TraceFlags, Wyliczenie

Flagi śledzenia dla typów zdarzeń

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="criticalregiontype"></a>CriticalRegionType —, Wyliczenie

Typ regionu krytycznego, w którym znajduje się kontekst.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`InsideCriticalRegion`|Wskazuje, że kontekst znajduje się w regionie krytycznym. W ramach regionu krytycznego zawieszenia asynchroniczne są ukrywane w harmonogramie. W przypadku takiego zawieszenia Menedżer zasobów będzie oczekiwać, aż wątek stanie się możliwy do uruchomienia i po prostu wznowić go zamiast wywoływania harmonogramu. Wszelkie blokady w tym regionie muszą być podejmowane z najwyższą starannością.|
|`InsideHyperCriticalRegion`|Wskazuje, że kontekst znajduje się w regionie krytycznym dla funkcji Hyper. W regionie krytycznym funkcji Hyper-w przypadku zawieszania synchroniczne i asynchroniczne są ukrywane w harmonogramie. W przypadku takiego zawieszenia lub zablokowania Menedżer zasobów czeka na możliwy do uruchomienia wątku, a następnie po prostu wznowić go zamiast wywoływania harmonogramu. Blokady wykonywane wewnątrz tego regionu nigdy nie mogą być współużytkowane z kodem uruchomionym poza takim regionem. Wykonanie tej czynności spowoduje nieprzewidywalne zakleszczenie.|
|`OutsideCriticalRegion`|Wskazuje, że kontekst znajduje się poza jakimkolwiek regionem krytycznym.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm. h

## <a name="dynamicprogressfeedbacktype"></a>DynamicProgressFeedbackType —, Wyliczenie

Używane przez zasady `DynamicProgressFeedback` do opisywania, czy zasoby dla harmonogramu będą ponownie równoważone zgodnie z informacjami statystycznymi zebranymi na podstawie harmonogramu, czy tylko na podstawie procesorów wirtualnych przechodzących i z stanu bezczynności przez wywołania do `Activate` i `Deactivate` metod w interfejsie `IVirtualProcessorRoot`. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Harmonogram nie zbiera informacji o postępie. Ponowne równoważenie jest wykonywane wyłącznie na poziomie subskrypcji bazowego wątku sprzętowego. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](IExecutionResource-structure.md).<br /><br /> Ta wartość jest zarezerwowana do użycia przez środowisko uruchomieniowe.|
|`ProgressFeedbackEnabled`|Harmonogram zbiera informacje o postępie i przekazuje je do usługi Resource Manager. Usługa Resource Manager będzie korzystać z tych informacji statystycznych w celu ponownego zrównoważenia zasobów w imieniu harmonogramu oraz poziomu subskrypcji bazowego wątku sprzętowego. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource:: CurrentSubscriptionLevel —](IExecutionResource-structure.md).|

## <a name="join_type"></a>join_type, Wyliczenie

Typ bloku komunikatów `join`.

```cpp
enum join_type;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`greedy`|Zachłanne `join` bloku komunikatów natychmiast akceptują komunikat po propagacji. Jest to wydajniejsze, ale ma możliwość korzystania z blokady na żywo, w zależności od konfiguracji sieci.|
|`non_greedy`|Bloki komunikatów, które nie są zachłanne `join`, blokują komunikaty i próbują wykorzystać je po odebraniu. Te zadania są gwarantowane, ale wolniejsze.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

## <a name="message_status"></a>message_status, Wyliczenie

Prawidłowe odpowiedzi dla oferty `message` obiektu na blok.

```cpp
enum message_status;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`accepted`|Element docelowy zaakceptował wiadomość.|
|`declined`|Element docelowy nie zaakceptował wiadomości.|
|`missed`|Miejsce docelowe próbowało zaakceptować komunikat, ale nie jest już dostępne.|
|`postponed`|Obiekt docelowy przełożył komunikat.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** agenci. h

## <a name="policyelementkey"></a>PolicyElementKey —, Wyliczenie

Klucze zasad opisujące aspekty zachowania usługi Scheduler. Każdy element zasad jest opisywany przez parę klucz-wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływu na harmonogramy, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`ContextPriority`|Priorytet wątku systemu operacyjnego każdego kontekstu w harmonogramie. Jeśli ten klucz jest ustawiony na wartość `INHERIT_THREAD_PRIORITY` konteksty w harmonogramie odziedziczą priorytet wątku, który utworzył harmonogram.<br /><br /> Prawidłowe wartości: dowolna z prawidłowych wartości funkcji `SetThreadPriority` systemu Windows i wartości specjalnej `INHERIT_THREAD_PRIORITY`<br /><br /> Wartość domyślna: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Zarezerwowany rozmiar stosu każdego kontekstu w harmonogramie w kilobajtach.<br /><br /> Prawidłowe wartości: dodatnie liczby całkowite<br /><br /> Wartość domyślna: `0`, wskazujący, że zostanie użyta wartość domyślna procesu dla rozmiaru stosu.|
|`DynamicProgressFeedback`|Określa, czy zasoby dla harmonogramu zostaną ponownie zrównoważone według informacji statystycznych zebranych z harmonogramu, czy tylko na podstawie poziomu subskrypcji bazowych wątków sprzętowych. Aby uzyskać więcej informacji, zobacz [DynamicProgressFeedbackType —](#dynamicprogressfeedbacktype).<br /><br /> Prawidłowe wartości: element członkowski wyliczenia `DynamicProgressFeedbackType`, `ProgressFeedbackEnabled` lub `ProgressFeedbackDisabled`<br /><br /> Wartość domyślna: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Jeśli klucz zasad `SchedulingProtocol` jest ustawiony na wartość `EnhanceScheduleGroupLocality`, określa maksymalną liczbę kontekstów możliwy do uruchomienia, które mogą być buforowane w ramach poszczególnych kolejek lokalnych procesora wirtualnego. Takie konteksty są zwykle uruchamiane w kolejności Last-in-First-Out (LIFO) w procesorze wirtualnym, który spowodował, że stają się one możliwy do uruchomienia. Należy pamiętać, że ten klucz zasad nie ma znaczenia, gdy klucz `SchedulingProtocol` jest ustawiony na wartość `EnhanceForwardProgress`.<br /><br /> Prawidłowe wartości: nieujemne liczby całkowite<br /><br /> Wartość domyślna: `8`|
|`MaxConcurrency`|Maksymalny poziom współbieżności wymagany przez harmonogram. Menedżer zasobów podejmie próbę wstępnego przydzielenia tego wielu procesorów wirtualnych. Wartość specjalna [MaxExecutionResources —](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że żądany poziom współbieżności jest taki sam jak liczba wątków sprzętowych na komputerze. Jeśli wartość określona dla `MinConcurrency` jest większa niż liczba wątków sprzętowych na komputerze i `MaxConcurrency` została określona jako `MaxExecutionResources`, wartość dla `MaxConcurrency` zostanie podniesiona w celu dopasowania do wartości ustawionej dla `MinConcurrency`.<br /><br /> Prawidłowe wartości: dodatnie liczby całkowite i wartość specjalna `MaxExecutionResources`<br /><br /> Wartość domyślna: `MaxExecutionResources`|
|`MaxPolicyElementKey`|Maksymalny klucz elementu zasad. Nieprawidłowy klucz elementu.|
|`MinConcurrency`|Minimalny poziom współbieżności, który musi zostać udostępniony harmonogramowi przez Menedżera zasobów. Liczba procesorów wirtualnych przypisanych do harmonogramu nigdy nie będzie mniejsza niż wartość minimalna. Wartość specjalna [MaxExecutionResources —](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że minimalny poziom współbieżności jest taki sam jak liczba wątków sprzętowych na komputerze. Jeśli wartość określona dla `MaxConcurrency` jest mniejsza niż liczba wątków sprzętowych na maszynie i `MinConcurrency` została określona jako `MaxExecutionResources`, wartość dla `MinConcurrency` jest niższa, aby odpowiadała wartości ustawionej dla `MaxConcurrency`.<br /><br /> Prawidłowe wartości: nieujemne liczby całkowite i wartość specjalna `MaxExecutionResources`. Należy pamiętać, że w przypadku zasad usługi Scheduler używanych na potrzeby konstruowania środowisko uruchomieniowe współbieżności harmonogramów wartość `0` jest nieprawidłowa.<br /><br /> Wartość domyślna: `1`|
|`SchedulerKind`|Typ wątków, które będą używane przez harmonogram dla podstawowych kontekstów wykonywania. Aby uzyskać więcej informacji, zobacz [SchedulerType](#schedulertype).<br /><br /> Prawidłowe wartości: element członkowski wyliczenia `SchedulerType`, na przykład `ThreadScheduler`<br /><br /> Wartość domyślna: `ThreadScheduler`. Powoduje to przetłumaczenie na wątki Win32 we wszystkich systemach operacyjnych.|
|`SchedulingProtocol`|Opisuje, który algorytm planowania będzie używany przez harmonogram. Aby uzyskać więcej informacji, zobacz [SchedulingProtocolType —](#schedulingprotocoltype).<br /><br /> Prawidłowe wartości: element członkowski wyliczenia `SchedulingProtocolType`, `EnhanceScheduleGroupLocality` lub `EnhanceForwardProgress`<br /><br /> Wartość domyślna: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Liczba wstępnie zaakceptowanych procesorów wirtualnych na wątek sprzętowy. Docelowy współczynnik nadsubskrypcji może zostać zwiększony przez Menedżer zasobów, w razie potrzeby, do zaspokojenia `MaxConcurrency` z wątkami sprzętowymi na komputerze.<br /><br /> Prawidłowe wartości: dodatnie liczby całkowite<br /><br /> Wartość domyślna: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="schedulertype"></a>Usługa SchedulerType — Wyliczenie

Używane przez zasady `SchedulerKind` do opisywania typu wątków, których harmonogram ma używać dla podstawowych kontekstów wykonywania. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`ThreadScheduler`|Wskazuje jawne żądanie zwykłych wątków Win32.|
|`UmsThreadDefault`|Wątki harmonogramie w trybie użytkownika (UMS) nie są obsługiwane w środowisko uruchomieniowe współbieżności w Visual Studio 2013. Użycie `UmsThreadDefault` jako wartości dla zasad `SchedulerType` nie spowoduje błędu. Jednak harmonogram utworzony przy użyciu tych zasad będzie domyślnie używać wątków Win32.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="schedulingprotocoltype"></a>SchedulingProtocolType —, Wyliczenie

Używane przez zasady `SchedulingProtocol` do opisywania, który algorytm planowania będzie używany do harmonogramu. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`EnhanceForwardProgress`|Harmonogram jest preferowany przez grupy harmonogramu po wykonaniu każdego zadania. Niezablokowane konteksty są zwykle planowane jako pierwszy w pierwszej kolejności (FIFO). Procesory wirtualne nie buforują nieblokowanych kontekstów.|
|`EnhanceScheduleGroupLocality`|Przed przejściem do innej grupy harmonogramu usługa Scheduler zaleca kontynuowanie pracy nad zadaniami w bieżącej grupie harmonogramu. Zablokowane konteksty są buforowane na procesory wirtualne i są zwykle planowane na czas ostatniego użycia (LIFO) przez procesor wirtualny, który odblokowany.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="switchingproxystate"></a>SwitchingProxyState —, Wyliczenie

Służy do oznaczania stanu, w którym znajduje się serwer proxy wątku, gdy wykonuje przełączenie kontekstu do innego serwera proxy wątku.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`Blocking`|Wskazuje, że wywoływany wątek jest w pełni blokowany i powinien być własnością obiektu wywołującego, dopóki nie zostanie ponownie uruchomiony i zostanie wykonana inna akcja.|
|`Idle`|Wskazuje, że wywoływany wątek nie jest już wymagany przez harmonogram i jest zwracany do Menedżer zasobów. Nie można już użyć kontekstu, który został wysłany przez Menedżer zasobów.|
|`Nesting`|Wskazuje, że wątek wywołujący jest zagnieżdżony w harmonogramie podrzędnym i jest wymagany przez obiekt wywołujący, aby dołączyć do innego harmonogramu.|

### <a name="remarks"></a>Uwagi

Parametr typu `SwitchingProxyState` jest przekazywane do metody `IThreadProxy::SwitchTo`, aby nawiązać Menedżer zasobów jak traktować serwer proxy wątku wykonujący wywołanie.

Aby uzyskać więcej informacji na temat sposobu użycia tego typu, zobacz [IThreadProxy:: SwitchTo —](ithreadproxy-structure.md#switchto).

## <a name="task_group_status"></a>task_group_status, Wyliczenie

Opisuje stan wykonywania obiektu `task_group` lub `structured_task_group`. Wartość tego typu jest zwracana przez wiele metod, które oczekują na ukończenie zadań zaplanowanych dla grupy zadań.

```cpp
enum task_group_status;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`canceled`|Obiekt `task_group` lub `structured_task_group` został anulowany. Co najmniej jedno zadanie mogło nie zostać wykonane.|
|`completed`|Zadania w kolejce do obiektu `task_group` lub `structured_task_group` zostały wykonane pomyślnie.|
|`not_complete`|Zadania w kolejce do obiektu `task_group` nie zostały ukończone. Należy zauważyć, że ta wartość nie jest obecnie zwracana przez środowisko uruchomieniowe współbieżności.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface. h

## <a name="winrtinitializationtype"></a>WinRTInitializationType —, Wyliczenie

Używane przez zasady `WinRTInitialization` do opisywania, czy i w jaki sposób środowisko wykonawcze systemu Windows zostanie zainicjowany w wątkach usługi Scheduler dla aplikacji działającej w systemach operacyjnych z wersją systemu Windows 8 lub nowszą. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey —](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Wartości

|Name (Nazwa)|Opis|
|----------|-----------------|
|`DoNotInitializeWinRT`|Gdy aplikacja jest uruchamiana w systemach operacyjnych z wersji systemu Windows 8 lub nowszej, wątki w ramach harmonogramu nie inicjują środowisko wykonawcze systemu Windows.|
|`InitializeWinRTAsMTA`|Gdy aplikacja jest uruchamiana w systemach operacyjnych z wersji systemu Windows 8 lub nowszej, każdy wątek w ramach harmonogramu inicjuje środowisko wykonawcze systemu Windows i deklaruje, że jest częścią apartamentu wielowątkowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** ConcRT. h

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
