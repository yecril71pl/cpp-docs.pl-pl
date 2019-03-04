---
title: wyliczenia przestrzeni nazw współbieżności
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
ms.openlocfilehash: d3eb49cd1555f23cc83efb0d8d912998295b3c55
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271193"
---
# <a name="concurrency-namespace-enums"></a>wyliczenia przestrzeni nazw współbieżności

||||
|-|-|-|
|[Agents_eventtype —](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|
|[Schedulertype —](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|
|[WinRTInitializationType](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|
|[message_status](#message_status)|[task_group_status](#task_group_status)|

##  <a name="agent_status"></a>  agent_status — wyliczenie

Prawidłowe stany `agent`.

```
enum agent_status;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`agent_canceled`|`agent` Zostało anulowane.|
|`agent_created`|`agent` Została utworzona, ale nie uruchomiony.|
|`agent_done`|`agent` Zostało zakończone bez zostanie ono anulowane.|
|`agent_runnable`|`agent` Pracę, ale nie wprowadzono jego `run` metody.|
|`agent_started`|`agent` Została uruchomiona.|

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [agentów asynchronicznych](../../../parallel/concrt/asynchronous-agents.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

##  <a name="agents_eventtype"></a>  Agents_eventtype — wyliczenie

Typy zdarzeń, które mogą być śledzone za pomocą funkcji śledzenia oferowane przez biblioteki agentów

```
enum Agents_EventType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`AGENTS_EVENT_CREATE`|Typ zdarzenia, który reprezentuje obiekt|
|`AGENTS_EVENT_DESTROY`|Typ zdarzenia, który reprezentuje usunięcie obiektu|
|`AGENTS_EVENT_END`|Typ zdarzenia, który reprezentuje zawarcia niektóre przetwarzania|
|`AGENTS_EVENT_LINK`|Typ zdarzenia, który reprezentuje łączenie bloków komunikatów|
|`AGENTS_EVENT_NAME`|Typ zdarzenia, który reprezentuje nazwę dla obiektu|
|`AGENTS_EVENT_SCHEDULE`|Typ zdarzenia, który reprezentuje planowania procesu|
|`AGENTS_EVENT_START`|Typ zdarzenia, który reprezentuje część rozpoczęcia przetwarzania|
|`AGENTS_EVENT_UNLINK`|Typ zdarzenia, który reprezentuje odłączanie bloki komunikatów|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

##  <a name="concrt_eventtype"></a>  Concrt_eventtype — wyliczenie

Typy zdarzeń, które mogą być śledzone za pomocą funkcji śledzenia oferowane przez środowisko uruchomieniowe współbieżności.

```
enum ConcRT_EventType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`CONCRT_EVENT_ATTACH`|Typ zdarzenia, który reprezentuje act dołączenia do harmonogramu.|
|`CONCRT_EVENT_BLOCK`|Typ zdarzenia, który reprezentuje act blokujących kontekstu.|
|`CONCRT_EVENT_DETACH`|Typ zdarzenia, który reprezentuje czynność odłączanie od harmonogramu.|
|`CONCRT_EVENT_END`|Typ zdarzenia, który oznacza początek parę rozpoczęcia/zakończenia zdarzenia.|
|`CONCRT_EVENT_GENERIC`|Typ zdarzenia, używane dla różnych zdarzeń.|
|`CONCRT_EVENT_IDLE`|Typ zdarzenia, który reprezentuje act kontekstu staje się bezczynności.|
|`CONCRT_EVENT_START`|Typ zdarzenia, który oznacza początek parę rozpoczęcia/zakończenia zdarzenia.|
|`CONCRT_EVENT_UNBLOCK`|Typ zdarzenia, który reprezentuje czynność odblokowywania kontekstu.|
|`CONCRT_EVENT_YIELD`|Typ zdarzenia, który reprezentuje czynność reaguje kontekstu.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h **Namespace:** współbieżności

##  <a name="concrt_traceflags"></a>  Concrt_traceflags — wyliczenie

Flagi śledzenia typy zdarzeń

```
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

##  <a name="criticalregiontype"></a>  Criticalregiontype — wyliczenie

Typ regionu krytyczny kontekst znajduje się wewnątrz.

```
enum CriticalRegionType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`InsideCriticalRegion`|Wskazuje, że kontekst znajduje się wewnątrz regionu krytycznych. Gdy wewnątrz regionu krytycznych, zawieszenia asynchroniczne są ukryte przed harmonogramu. Ma takie zawieszenie się zdarzyć, usługi Resource Manager będzie czekać, aż wątek stanie się możliwe do uruchomienia i po prostu Wznów zamiast wywoływania harmonogram ponownie. Wszystkie blokady podjęte w obrębie regionu świadczenia muszą zostać pobrane z rozwagą.|
|`InsideHyperCriticalRegion`|Wskazuje, że kontekst znajduje się wewnątrz funkcji hyper krytyczny regionu. Gdy wewnątrz funkcji hyper krytyczny regionu, zawieszenia synchroniczne i asynchroniczne są ukryte przed harmonogramu. Takie zawieszenie powinno lub blokuje się stało, Menedżer zasobów będzie czekać, aż wątek stanie się możliwe do uruchomienia i po prostu Wznów zamiast wywoływania harmonogram ponownie. Blokady podjęte w obrębie regionu świadczenia nigdy nie musi być udostępniane innym kod działający poza obszarem takie. Ten sposób spowoduje zakleszczenia nieprzewidywalne.|
|`OutsideCriticalRegion`|Wskazuje, że kontekst znajduje się poza dowolny region krytyczne.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrtrm.h

##  <a name="dynamicprogressfeedbacktype"></a>  DynamicProgressFeedbackType Enumeration

Używane przez `DynamicProgressFeedback` zasady do opisywania, czy zasoby dla harmonogramu zostanie ponownie zbilansowana zgodnie z informacje statystyczne zebrane z harmonogramu lub tylko na podstawie na pracę i w stan bezczynności za pośrednictwem wywołania procesorówwirtualnych`Activate` i `Deactivate` metod `IVirtualProcessorRoot` interfejsu. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).

```
enum DynamicProgressFeedbackType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ProgressFeedbackDisabled`|Harmonogram nie zbierać informacje o postępie. Ponowne równoważenie odbywa się na podstawie wyłącznie na poziomie subskrypcji podstawowej wątku sprzętu. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](IExecutionResource-structure.md).<br /><br /> Ta wartość jest zarezerwowana do użytku w czasie wykonywania.|
|`ProgressFeedbackEnabled`|Harmonogram zbiera informacje o postępie i przekazuje je do usługi resource manager. Te informacje statystyczne na ponowne zrównoważenie zasobów w imieniu harmonogramu oprócz poziom subskrypcji w podstawowym wątku sprzętu będzie korzystać z usługi resource manager. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [iexecutionresource::currentsubscriptionlevel —](IExecutionResource-structure.md).|

##  <a name="join_type"></a>  join_type — wyliczenie

Typ `join` Blok obsługi wiadomości.

```
enum join_type;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`greedy`|Zachłanne `join` bloków komunikatów natychmiast zaakceptować komunikat po propagacji. Jest to bardziej wydajne, ale ma możliwość live-lock, w zależności od konfiguracji sieci.|
|`non_greedy`|Inne niż zachłanne `join` bloków komunikatów odroczyć wiadomości i spróbuj i korzystać z nich po wszystkich już korzystać z. Te jest gwarantowane, ale wolniej.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

##  <a name="message_status"></a>  message_status — wyliczenie

Prawidłowe odpowiedzi na ofertę `message` obiektu do bloku.

```
enum message_status;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`accepted`|Element docelowy zaakceptować komunikat.|
|`declined`|Element docelowy nie zaakceptował wiadomości.|
|`missed`|Element docelowy próbował zaakceptować komunikat, ale nie jest już dostępna.|
|`postponed`|Element docelowy odroczony komunikat.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

##  <a name="policyelementkey"></a>  Policyelementkey — wyliczenie

Klucze zasad zawierająca opis aspekty zachowania harmonogramu. Każdy element zasad jest opisane pary klucz wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływ na transfery danych zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

```
enum PolicyElementKey;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ContextPriority`|Priorytet wątku systemu operacyjnego w każdym kontekście, w ramach harmonogramu zadań. Jeśli ten klucz jest ustawiony na wartość `INHERIT_THREAD_PRIORITY` kontekstów w ramach harmonogramu zadań będzie dziedziczyć priorytet wątku, który utworzony harmonogram.<br /><br /> Prawidłowe wartości: Dowolne prawidłowe wartości dla Windows `SetThreadPriority` funkcji i specjalna wartość `INHERIT_THREAD_PRIORITY`<br /><br /> Wartość domyślna: `THREAD_PRIORITY_NORMAL`|
|`ContextStackSize`|Rozmiar stosu zarezerwowane w każdym kontekście, w ramach harmonogramu zadań w kilobajtach.<br /><br /> Prawidłowe wartości: Dodatnie liczby całkowite<br /><br /> Wartość domyślna: `0`, wskazujący, że można użyć wartości domyślnych procesu dla rozmiaru stosu.|
|`DynamicProgressFeedback`|Określa, czy zasoby dla harmonogramu zostanie ponownie zbilansowana zgodnie z informacje statystyczne zebrane z harmonogramu lub tylko zależnie od poziomu subskrypcji źródłowej wątków sprzętu. Aby uzyskać więcej informacji, zobacz [dynamicprogressfeedbacktype —](#dynamicprogressfeedbacktype).<br /><br /> Prawidłowe wartości: Członek `DynamicProgressFeedbackType` wyliczenia, albo `ProgressFeedbackEnabled` lub `ProgressFeedbackDisabled`<br /><br /> Wartość domyślna: `ProgressFeedbackEnabled`|
|`LocalContextCacheSize`|Gdy `SchedulingProtocol` zasad jest ustawiona na wartość `EnhanceScheduleGroupLocality`, określa maksymalną liczbę kontekstów możliwy do uruchomienia, mogą być buforowane w na procesor wirtualny lokalnych kolejek. Takie kontekstów zazwyczaj będzie działał w ostatniej wejściu — pierwszy na wyjściu (LIFO) kolejności dla wirtualnego procesora, który spowodował by możliwy do uruchomienia. Należy pamiętać, że ten klucz zasad ma, nie oznacza, kiedy `SchedulingProtocol` jest ustawiona na wartość `EnhanceForwardProgress`.<br /><br /> Prawidłowe wartości: Nieujemne liczby całkowite<br /><br /> Wartość domyślna: `8`|
|`MaxConcurrency`|Współbieżność maksymalny poziom żądanego przez harmonogram. Usługi resource manager podejmie próbę można wstępnie przydzielić następująca liczba procesorów wirtualnych. Specjalna wartość [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że poziom współbieżności żądany jest taka sama jak liczba wątków sprzętu na komputerze. Jeśli wartość określona dla `MinConcurrency` jest większa niż liczba wątków sprzętu na komputerze i `MaxConcurrency` jest określony jako `MaxExecutionResources`, wartość `MaxConcurrency` zostanie zaokrąglona do dopasowania, co jest ustawiona dla `MinConcurrency`.<br /><br /> Prawidłowe wartości: Dodatnie liczby całkowite i specjalna wartość `MaxExecutionResources`<br /><br /> Wartość domyślna: `MaxExecutionResources`|
|`MaxPolicyElementKey`|Klucz elementu maksymalna zasad. Nie klucz prawidłowego elementu.|
|`MinConcurrency`|Poziom minimalnej współbieżności, który jest wymagany do harmonogramu przez Menedżera zasobów. Liczba procesorów wirtualnych przypisanych do harmonogramu nigdy nie zaczną się poniżej minimum. Specjalna wartość [MaxExecutionResources](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że poziom współbieżności minimalna jest taka sama jak liczba wątków sprzętu na komputerze. Jeśli wartość określona dla `MaxConcurrency` jest mniejsza niż liczba wątków sprzętu na komputerze i `MinConcurrency` jest określony jako `MaxExecutionResources`, wartość `MinConcurrency` jest obniżony do dopasowania, co jest ustawiona dla `MaxConcurrency`.<br /><br /> Prawidłowe wartości: Nieujemne liczby całkowite i specjalna wartość `MaxExecutionResources`. Należy pamiętać, że harmonogram zasad używany do budowy transfery danych w środowisku uruchomieniowym współbieżności, wartość `0` jest nieprawidłowy.<br /><br /> Wartość domyślna: `1`|
|`SchedulerKind`|Typ wątki, które używają harmonogramu dla podstawowej kontekstów wykonanie. Aby uzyskać więcej informacji, zobacz [schedulertype —](#schedulertype).<br /><br /> Prawidłowe wartości: Członek `SchedulerType` wyliczenia, na przykład `ThreadScheduler`<br /><br /> Wartość domyślna: `ThreadScheduler`. Przekłada się to Win32 wątki we wszystkich systemach operacyjnych.|
|`SchedulingProtocol`|W tym artykule opisano, w których planowania algorytm będzie używany przez harmonogram. Aby uzyskać więcej informacji, zobacz [schedulingprotocoltype —](#schedulingprotocoltype).<br /><br /> Prawidłowe wartości: Członek `SchedulingProtocolType` wyliczenia, albo `EnhanceScheduleGroupLocality` lub `EnhanceForwardProgress`<br /><br /> Wartość domyślna: `EnhanceScheduleGroupLocality`|
|`TargetOversubscriptionFactor`|Wstępne liczba procesorów wirtualnych przypadających na wątek sprzętu. Czynnik nadsubskrypcji docelowy może być zwiększana przez Menedżera zasobów Jeśli jest to niezbędne do spełnienia `MaxConcurrency` z wątków sprzętu na komputerze.<br /><br /> Prawidłowe wartości: Dodatnie liczby całkowite<br /><br /> Wartość domyślna: `1`|
|`WinRTInitialization`||

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

##  <a name="schedulertype"></a>  Schedulertype — wyliczenie

Używane przez `SchedulerKind` zasady do opisywania typ wątki, które harmonogram powinni stosować dla podstawowej kontekstów wykonanie. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).

```
enum SchedulerType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`ThreadScheduler`|Wskazuje żądanie jawne regularne wątków Win32.|
|`UmsThreadDefault`|Wątków (UMS) ustalonych w harmonogramie trybu użytkownika nie są obsługiwane w środowisku uruchomieniowym współbieżności w programie Visual Studio 2013. Za pomocą `UmsThreadDefault` jako wartość `SchedulerType` zasad nie powoduje wystąpienie błędu. Jednak przy użyciu wątków Win32 domyślnie harmonogram utworzony z tą zasadą.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

##  <a name="schedulingprotocoltype"></a>  Schedulingprotocoltype — wyliczenie

Używane przez `SchedulingProtocol` zasady do opisywania, który algorytm planowania, będzie wykorzystywana w przypadku usługi scheduler. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).

```
enum SchedulingProtocolType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`EnhanceForwardProgress`|Harmonogram preferuje okrężnego za pośrednictwem grupy harmonogramu po wykonaniu każdego zadania. Odblokowany konteksty są zwykle zaplanowane w sposób pierwszy wejściu — pierwszy na wyjściu (FIFO). Procesory wirtualne nie buforują kontekstów odblokowane.|
|`EnhanceScheduleGroupLocality`|Harmonogram preferuje kontynuować pracę nad zadaniami w bieżącej grupie harmonogram przed przeniesieniem do innej grupy harmonogramu. Odblokowany konteksty są buforowane na procesor wirtualny i odbywa się zwykle w czasie ostatniego wejściu — pierwszy na wyjściu (LIFO) przy procesora wirtualnego, który je odblokowane.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

##  <a name="switchingproxystate"></a>  Switchingproxystate — wyliczenie

Wykorzystywany w celu określenia stanu w jakim jest wątek serwera proxy, gdy jest wykonywany przełączanie kontekstu współpracy na serwerze proxy w innym wątku.

```
enum SwitchingProxyState;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`Blocking`|Wskazuje, że wątek wywołujący wspólne blokuje powinna być wyłącznie własnością wywołującego do momentu później ponowne uruchomienie i wykonywania innych działań.|
|`Idle`|Wskazuje, że wątek wywołujący nie jest już potrzebna przez harmonogram jest zwracany do usługi Resource Manager. Kontekst, który był wysyłany nie jest już mógł być wykorzystywane przez Menedżera zasobów.|
|`Nesting`|Wskazuje, że wątek wywołujący jest zagnieżdżanie harmonogramu podrzędne są wymagane przez obiekt wywołujący, aby dołączyć do innej usługi scheduler.|

### <a name="remarks"></a>Uwagi

Parametr typu `SwitchingProxyState` jest przekazywany do metody `IThreadProxy::SwitchTo` się poinstruowanie Menedżera zasobów, jak ma traktować proxy wątku, który wykonuje wywołanie.

Aby uzyskać więcej informacji na temat korzystania z tego typu, zobacz [ithreadproxy::switchto —](ithreadproxy-structure.md#switchto).

##  <a name="task_group_status"></a>  task_group_status — wyliczenie

Opisuje stan wykonania obiektu `task_group` lub `structured_task_group` obiektu. Wartość tego typu jest zwracany przez metod czekających na zadania zaplanowane do grupy zadań do wykonania.

```
enum task_group_status;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`canceled`|`task_group` Lub `structured_task_group` obiektu zostało anulowane. Jedno lub więcej zadań nie mogło zostać wykonane.|
|`completed`|Zadania w kolejce do `task_group` lub `structured_task_group` zostały ukończone pomyślnie.|
|`not_complete`|Zadania w kolejce do `task_group` obiektu nie została ukończona. Należy pamiętać, że ta wartość nie jest obecnie zwracana w czasie wykonywania współbieżności.|

### <a name="requirements"></a>Wymagania

**Nagłówek:** pplinterface.h

##  <a name="winrtinitializationtype"></a>  Winrtinitializationtype — wyliczenie

Używane przez `WinRTInitialization` zasady do opisywania, czy i jak środowisko wykonawcze Windows będzie zainicjowane na wątki harmonogram dla aplikacji, która działa w systemach operacyjnych z wersji systemu Windows 8 lub nowszy. Aby uzyskać więcej informacji na temat dostępnych polityk harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).

```
enum WinRTInitializationType;
```

### <a name="values"></a>Wartości

|Nazwa|Opis|
|----------|-----------------|
|`DoNotInitializeWinRT`|Gdy aplikacja działających w systemach operacyjnych z wersji systemu Windows 8 lub wyższym, wątki w obrębie harmonogramu, nie będą inicjowały środowiska wykonawczego Windows.|
|`InitializeWinRTAsMTA`|Gdy aplikacja jest uruchamiana w systemach operacyjnych z wersji systemu Windows 8 lub wyższej, każdy wątek w obrębie harmonogramu, spowoduje zainicjowanie środowiska wykonawczego Windows i zadeklarować, że jest on częścią apartamentu wielowątkowych.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** concrt.h

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
