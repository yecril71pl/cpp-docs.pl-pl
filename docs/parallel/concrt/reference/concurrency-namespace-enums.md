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
ms.openlocfilehash: e3a943ed52ce9653086203713bb98331f809314d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372723"
---
# <a name="concurrency-namespace-enums"></a>Wyliczenia przestrzeni nazw współbieżności

||||
|-|-|-|
|[Agents_EventType](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[Typ regionu krytycznego](#criticalregiontype)|[Typ dynamicznego transferu danych](#dynamicprogressfeedbacktype)|[Klawiatura PolicyElementKey](#policyelementkey)|
|[Rodzaj harmonogramu](#schedulertype)|[PlanowanieProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

## <a name="agent_status-enumeration"></a><a name="agent_status"></a>agent_status Wyliczenie

Prawidłowe stany `agent`dla .

```cpp
enum agent_status;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`agent_canceled`|Został `agent` anulowany.|
|`agent_created`|Został `agent` utworzony, ale nie został uruchomiony.|
|`agent_done`|Gotowy `agent` bez anulowania.|
|`agent_runnable`|Został `agent` uruchomiony, ale nie wszedł `run` w jego metodę.|
|`agent_started`|Rozpoczęto. `agent`|

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Środki asynchroniczne](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="agents_eventtype-enumeration"></a><a name="agents_eventtype"></a>Agents_EventType Wyliczenie

Typy zdarzeń, które można śledzić za pomocą funkcji śledzenia oferowanych przez Bibliotekę agentów

```cpp
enum Agents_EventType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Typ zdarzenia reprezentujący tworzenie obiektu|
|`AGENTS_EVENT_DESTROY`|Typ zdarzenia reprezentujący usunięcie obiektu|
|`AGENTS_EVENT_END`|Typ zdarzenia, który reprezentuje zakończenie niektórych przetwarzania|
|`AGENTS_EVENT_LINK`|Typ zdarzenia reprezentujący łączenie bloków wiadomości|
|`AGENTS_EVENT_NAME`|Typ zdarzenia reprezentujący nazwę obiektu|
|`AGENTS_EVENT_SCHEDULE`|Typ zdarzenia reprezentujący planowanie procesu|
|`AGENTS_EVENT_START`|Typ zdarzenia reprezentujący inicjację niektórych procesów przetwarzania|
|`AGENTS_EVENT_UNLINK`|Typ zdarzenia reprezentujący odłączanie bloków wiadomości|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="concrt_eventtype-enumeration"></a><a name="concrt_eventtype"></a>ConcRT_EventType Wyliczenie

Typy zdarzeń, które mogą być śledzone przy użyciu funkcji śledzenia oferowanych przez środowisko uruchomieniowe współbieżności.

```cpp
enum ConcRT_EventType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Typ zdarzenia, który reprezentuje akt dołączania do harmonogramu.|
|`CONCRT_EVENT_BLOCK`|Typ zdarzenia, który reprezentuje działanie blokowania kontekstu.|
|`CONCRT_EVENT_DETACH`|Typ zdarzenia, który reprezentuje akt odłączania od harmonogramu.|
|`CONCRT_EVENT_END`|Typ zdarzenia, który oznacza początek pary zdarzeń początkowych/końcowych.|
|`CONCRT_EVENT_GENERIC`|Typ zdarzenia używany dla różnych zdarzeń.|
|`CONCRT_EVENT_IDLE`|Typ zdarzenia, który reprezentuje akt kontekstu staje się bezczynny.|
|`CONCRT_EVENT_START`|Typ zdarzenia, który oznacza początek pary zdarzeń początkowych/końcowych.|
|`CONCRT_EVENT_UNBLOCK`|Typ zdarzenia, który reprezentuje akt odblokowywania kontekstu.|
|`CONCRT_EVENT_YIELD`|Typ zdarzenia, który reprezentuje akt kontekstu plonowania.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h **Obszar nazw:** współbieżność

## <a name="concrt_traceflags-enumeration"></a><a name="concrt_traceflags"></a>Concrt_TraceFlags Wyliczenie

Śledzenie flag dla typów zdarzeń

```cpp
enum Concrt_TraceFlags;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`AgentEventFlag`||
|`AllEventsFlag`||
|`ContextEventFlag`||
|`PPLEventFlag`||
|`ResourceManagerEventFlag`||
|`SchedulerEventFlag`||
|`VirtualProcessorEventFlag`||

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="criticalregiontype-enumeration"></a><a name="criticalregiontype"></a>Wyliczanie krytycznego regionu

Typ regionu krytycznego kontekstu znajduje się wewnątrz.

```cpp
enum CriticalRegionType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`InsideCriticalRegion`|Wskazuje, że kontekst znajduje się w regionie krytycznym. W regionie krytycznym zawieszenia asynchroniczne są ukryte w harmonogramie. Jeśli takie zawieszenie się zdarzyć, Menedżer zasobów będzie czekać na wątek, aby stać się możliwe do uruchomienia i po prostu wznowić go zamiast wywoływania harmonogramu ponownie. Wszelkie zamki podjęte wewnątrz takiego regionu muszą być podejmowane ze szczególną ostrożnością.|
|`InsideHyperCriticalRegion`|Wskazuje, że kontekst znajduje się w regionie hiperkrytycznym. W regionie hiperkrytycznym zarówno synchroniczne, jak i asynchroniczne zawieszenia są ukryte w harmonogramie. Jeśli takie zawieszenie lub blokowanie się zdarzyć, Menedżer zasobów będzie czekać na wątek, aby stać się możliwe do uruchomienia i po prostu wznowić go zamiast wywoływania harmonogramu ponownie. Blokady podjęte wewnątrz takiego regionu nigdy nie mogą być współużytkowane z kodem uruchomiony poza takim regionem. Spowoduje to nieprzewidywalny zakleszczenie.|
|`OutsideCriticalRegion`|Wskazuje, że kontekst znajduje się poza dowolnym regionem krytycznym.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

## <a name="dynamicprogressfeedbacktype-enumeration"></a><a name="dynamicprogressfeedbacktype"></a>Wyliczenie dynamicprogressFeedbackType

Używane przez `DynamicProgressFeedback` zasady do opisania, czy zasoby dla harmonogramu zostaną ponownie zrównoważone zgodnie z informacjami statystycznymi zebranymi z harmonogramu lub tylko `Activate` na `Deactivate` podstawie `IVirtualProcessorRoot` procesorów wirtualnych przechodzących i wychodzących ze stanu bezczynności za pośrednictwem wywołań i metod w interfejsie. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Harmonogram nie zbiera informacji o postępie. Ponowne równoważenie odbywa się wyłącznie na podstawie poziomu subskrypcji wątku sprzętu źródłowego. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Ta wartość jest zarezerwowana do użycia przez środowisko wykonawcze.|
|`ProgressFeedbackEnabled`|Harmonogram zbiera informacje o postępie i przekazuje go do menedżera zasobów. Menedżer zasobów będzie korzystać z tych informacji statystycznych, aby zrównoważyć zasoby w imieniu harmonogramu oprócz poziomu subskrypcji wątku sprzętu źródłowego. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|

## <a name="join_type-enumeration"></a><a name="join_type"></a>join_type Wyliczenie

Typ bloku `join` obsługi wiadomości.

```cpp
enum join_type;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`greedy`|Chciwy `join` bloków wiadomości natychmiast zaakceptować wiadomość po propagacji. Jest to bardziej wydajne, ale ma możliwość blokady na żywo, w zależności od konfiguracji sieci.|
|`non_greedy`|Non-chciwy `join` bloki wiadomości odroczyć wiadomości i spróbować i zużywają je po wszystkich przybył. Są one gwarantowane do pracy, ale wolniej.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

## <a name="message_status-enumeration"></a><a name="message_status"></a>Message_status Wyliczenie

Prawidłowe odpowiedzi dla oferty `message` obiektu do bloku.

```cpp
enum message_status;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`accepted`|Obiekt docelowy zaakceptował wiadomość.|
|`declined`|Obiekt docelowy nie zaakceptował wiadomości.|
|`missed`|Obiekt docelowy próbował zaakceptować wiadomość, ale nie była już dostępna.|
|`postponed`|Obiekt docelowy odroczył wiadomość.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

## <a name="policyelementkey-enumeration"></a><a name="policyelementkey"></a>Wyliczenie policyElementKey

Klucze zasad opisujące aspekty zachowania harmonogramu. Każdy element zasad jest opisany przez parę klucz-wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływu na harmonogramy, zobacz [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```cpp
enum PolicyElementKey;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ContextPriority`|Priorytet wątku systemu operacyjnego każdego kontekstu w harmonogramie. Jeśli ten klucz jest `INHERIT_THREAD_PRIORITY` ustawiony na wartość konteksty w harmonogramie odziedziczy priorytet wątku, który utworzył harmonogram.<br /><br /> Prawidłowe wartości: Dowolna z `SetThreadPriority` prawidłowych wartości dla funkcji Systemu Windows i wartość specjalna`INHERIT_THREAD_PRIORITY`<br /><br /> Wartość domyślna:`THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Zarezerwowany rozmiar stosu każdego kontekstu w harmonogramie w kilobajtach.<br /><br /> Prawidłowe wartości : Dodatnie liczby całkowite<br /><br /> Wartość domyślna : `0`, wskazując, że używana jest domyślna wartość procesu dla rozmiaru stosu.|
|`DynamicProgressFeedback`|Określa, czy zasoby dla harmonogramu zostaną ponownie zrównoważone zgodnie z informacjami statystycznymi zebranymi z harmonogramu lub tylko na podstawie poziomu subskrypcji podstawowych wątków sprzętowych. Aby uzyskać więcej informacji, zobacz [DynamicProgressFeedbackType](#dynamicprogressfeedbacktype).<br /><br /> Prawidłowe wartości: Element `DynamicProgressFeedbackType` członkowski wyliczenia, albo `ProgressFeedbackEnabled``ProgressFeedbackDisabled`<br /><br /> Wartość domyślna:`ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Gdy `SchedulingProtocol` klucz zasad jest ustawiony `EnhanceScheduleGroupLocality`na wartość, określa maksymalną liczbę kontekstów, które mogą być buforowane w kolejkach lokalnych procesora wirtualnego. Takie konteksty będą zazwyczaj uruchamiane w kolejności last-in-first-out (LIFO) na procesorze wirtualnym, co spowodowało ich uruchomienie. Należy zauważyć, że ten klucz `SchedulingProtocol` zasad nie ma `EnhanceForwardProgress`znaczenia, gdy klucz jest ustawiony na wartość .<br /><br /> Prawidłowe wartości : Liczby całkowite nieujemne<br /><br /> Wartość domyślna:`8`|
|`MaxConcurrency`|Maksymalny poziom współbieżności żądany przez harmonogram. Menedżer zasobów spróbuje początkowo przydzielić tyle procesorów wirtualnych. Specjalna wartość [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że żądany poziom współbieżności jest taki sam jak liczba wątków sprzętowych na komputerze. Jeśli określona `MinConcurrency` dla siebie wartość jest większa niż liczba `MaxConcurrency` wątków `MaxExecutionResources`sprzętowych `MaxConcurrency` na komputerze i jest `MinConcurrency`określona jako , wartość dla jest wywoływana w celu dopasowania do tego, co jest ustawione dla .<br /><br /> Prawidłowe wartości : Dodatnie liczby całkowite i wartość specjalna`MaxExecutionResources`<br /><br /> Wartość domyślna:`MaxExecutionResources`|
|`MaxPolicyElementKey`|Maksymalny klucz elementu zasad. Nie prawidłowy klucz elementu.|
|`MinConcurrency`|Minimalny poziom współbieżności, który musi być dostarczony do harmonogramu przez menedżera zasobów. Liczba procesorów wirtualnych przypisanych do harmonogramu nigdy nie spadnie poniżej minimum. Specjalna wartość [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że minimalny poziom współbieżności jest taki sam jak liczba wątków sprzętowych na komputerze. Jeśli określona `MaxConcurrency` dla siebie wartość jest mniejsza niż liczba `MinConcurrency` wątków `MaxExecutionResources`sprzętowych `MinConcurrency` na komputerze i jest określona jako , wartość dla jest obniżona, aby dopasować to, co jest ustawione dla `MaxConcurrency`.<br /><br /> Prawidłowe wartości : Nieujemne liczby `MaxExecutionResources`całkowite i wartość specjalna . Należy zauważyć, że dla zasad harmonogramu używane do budowy harmonogramów `0` środowiska uruchomieniowego współbieżności wartość jest nieprawidłowa.<br /><br /> Wartość domyślna:`1`|
|`SchedulerKind`|Typ wątków, które harmonogram będzie wykorzystywać dla kontekstów wykonywania podstawowych. Aby uzyskać więcej informacji, zobacz [SchedulerType](#schedulertype).<br /><br /> Prawidłowe wartości: Element `SchedulerType` członkowski wyliczenia, na przykład`ThreadScheduler`<br /><br /> Wartość domyślna : `ThreadScheduler`. Przekłada się to na wątki Win32 we wszystkich systemach operacyjnych.|
|`SchedulingProtocol`|W tym artykule opisano, który algorytm planowania będzie używany przez harmonogram. Aby uzyskać więcej informacji, zobacz [SchedulingProtocolType](#schedulingprotocoltype).<br /><br /> Prawidłowe wartości: Element `SchedulingProtocolType` członkowski wyliczenia, albo `EnhanceScheduleGroupLocality``EnhanceForwardProgress`<br /><br /> Wartość domyślna:`EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Wstępna liczba procesorów wirtualnych na wątek sprzętowy. Docelowy współczynnik nadsubskrypcji może zostać zwiększony przez Menedżera `MaxConcurrency` zasobów, jeśli to konieczne, aby zaspokoić za pomocą wątków sprzętowych na komputerze.<br /><br /> Prawidłowe wartości : Dodatnie liczby całkowite<br /><br /> Wartość domyślna:`1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="schedulertype-enumeration"></a><a name="schedulertype"></a>Wyliczanie typu harmonogramu

Używane przez `SchedulerKind` zasady do opisania typu wątków, które harmonogram powinien wykorzystać dla kontekstów wykonywania podstawowych. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulerType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ThreadScheduler`|Wskazuje jawne żądanie regularnych wątków Win32.|
|`UmsThreadDefault`|Wątki w trybie użytkownika (UMS) nie są obsługiwane w czasie wykonywania współbieżności w programie Visual Studio 2013. Użycie `UmsThreadDefault` jako wartości `SchedulerType` dla zasad nie spowoduje błędu. Jednak harmonogram utworzony za pomocą tej zasady będzie domyślnie przy użyciu wątków Win32.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="schedulingprotocoltype-enumeration"></a><a name="schedulingprotocoltype"></a>Wyliczanie typu SchedulingProtocolType

Używane przez `SchedulingProtocol` zasady do opisania, który algorytm planowania będą wykorzystywane do harmonogramu. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum SchedulingProtocolType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`EnhanceForwardProgress`|Harmonogram preferuje round-robin za pośrednictwem grup harmonogramu po wykonaniu każdego zadania. Odblokowane konteksty są zazwyczaj planowane w sposób pierwszy w pierwszym na zewnątrz (FIFO). Procesory wirtualne nie buforują odblokowanych kontekstów.|
|`EnhanceScheduleGroupLocality`|Harmonogram woli kontynuować pracę nad zadaniami w ramach bieżącej grupy harmonogramu przed przejściem do innej grupy harmonogramu. Odblokowane konteksty są buforowane na procesor wirtualny i są zazwyczaj planowane w sposób ostatni w pierwszym na zewnątrz (LIFO) przez procesor wirtualny, który je odblokował.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="switchingproxystate-enumeration"></a><a name="switchingproxystate"></a>Wyliczenie SwitchingProxyState

Służy do oznaczania stanu proxy wątku jest w, gdy jest wykonywanie przełączania kontekstu współpracy do innego serwera proxy wątku.

```cpp
enum SwitchingProxyState;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`Blocking`|Wskazuje, że wątek wywołujący jest kooperatywne blokowanie i powinny być wyłącznie własnością obiektu wywołującego, aż następnie uruchomiony ponownie i wykonywania innych akcji.|
|`Idle`|Wskazuje, że wątek wywołujący nie jest już potrzebny przez harmonogram i jest zwracany do Menedżera zasobów. Kontekst, który został wysłany nie jest już w stanie być wykorzystywane przez Menedżera zasobów.|
|`Nesting`|Wskazuje, że wątek wywołujący zagnieżdża harmonogram podrzędny i jest potrzebny przez wywołującego, aby dołączyć do innego harmonogramu.|

### <a name="remarks"></a>Uwagi

Parametr typu `SwitchingProxyState` jest przekazywany `IThreadProxy::SwitchTo` do metody, aby poinstruować Menedżera zasobów, jak traktować serwer proxy wątku, który wykonuje wywołanie.

Aby uzyskać więcej informacji na temat sposobu użycia tego typu, zobacz [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).

## <a name="task_group_status-enumeration"></a><a name="task_group_status"></a>Task_group_status Wyliczenie

Opisuje stan wykonania `task_group` obiektu `structured_task_group` lub obiektu. Wartość tego typu jest zwracana za pomocą wielu metod, które czekają na zadania zaplanowane do ukończenia grupy zadań.

```cpp
enum task_group_status;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`canceled`|Obiekt `task_group` `structured_task_group` lub obiekt został anulowany. Jedno lub więcej zadań może nie zostać wykonane.|
|`completed`|Zadania w kolejce `task_group` `structured_task_group` do obiektu lub obiektu zostały pomyślnie ukończone.|
|`not_complete`|Zadania umieszczone w `task_group` kolejce do obiektu nie zostały ukończone. Należy zauważyć, że ta wartość nie jest obecnie zwracana przez środowisko uruchomieniowe współbieżności.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface.h

## <a name="winrtinitializationtype-enumeration"></a><a name="winrtinitializationtype"></a>Wyliczanie typu WinRTInitializationType

Używane przez `WinRTInitialization` zasady do opisania, czy i jak środowisko wykonawcze systemu Windows zostanie zainicjowane w wątkach harmonogramu dla aplikacji działającej w systemach operacyjnych z wersją systemu Windows 8 lub nowszą. Aby uzyskać więcej informacji na temat dostępnych zasad harmonogramu, zobacz [PolicyElementKey](concurrency-namespace-enums.md).

```cpp
enum WinRTInitializationType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`DoNotInitializeWinRT`|Gdy aplikacja jest uruchamiana w systemach operacyjnych z wersją Systemu Windows 8 lub nowszą, wątki w harmonogramie nie inicjują środowiska wykonawczego systemu Windows .|
|`InitializeWinRTAsMTA`|Gdy aplikacja jest uruchamiana w systemach operacyjnych z wersją systemu Windows 8 lub nowszą, każdy wątek w harmonogramie zaikwuje środowisko wykonawcze systemu Windows i deklaruje, że jest częścią wielowątkowego mieszkania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
