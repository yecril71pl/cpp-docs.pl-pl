---
title: Typy wyliczeniowe przestrzeń nazw współbieżności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: a40e3b2d-ad21-4229-9880-2cfa84f7ab8f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 068aa89c10e92203ce0e826e3aaca101f4786cbb
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695265"
---
# <a name="concurrency-namespace-enums"></a>Typy wyliczeniowe przestrzeń nazw współbieżności
||||  
|-|-|-|  
|[Agents_eventtype —](#agents_eventtype)|[ConcRT_EventType](#concrt_eventtype)|[Concrt_TraceFlags](#concrt_traceflags)|  
|[CriticalRegionType](#criticalregiontype)|[DynamicProgressFeedbackType](#dynamicprogressfeedbacktype)|[PolicyElementKey](#policyelementkey)|  
|[Schedulertype —](#schedulertype)|[SchedulingProtocolType](#schedulingprotocoltype)|[SwitchingProxyState](#switchingproxystate)|  
|[Winrtinitializationtype —](#winrtinitializationtype)|[agent_status](#agent_status)|[join_type](#join_type)|  
|[message_status](#message_status)|[task_group_status](#task_group_status)|  
  
##  <a name="agent_status"></a>  agent_status — wyliczenie  
 Nieprawidłowy stan dla `agent`.  
  
```
enum agent_status;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`agent_canceled`|`agent` Zostało anulowane.|  
|`agent_created`|`agent` Została utworzona, ale nie jest uruchomiona.|  
|`agent_done`|`agent` Zostało zakończone bez anulowania.|  
|`agent_runnable`|`agent` Został uruchomiony, ale nie wprowadzono jego `run` metody.|  
|`agent_started`|`agent` Została uruchomiona.|  

### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [agentów asynchronicznych](../../../parallel/concrt/asynchronous-agents.md).  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h

##  <a name="agents_eventtype"></a>  Agents_eventtype — wyliczenie  
 Typy zdarzeń, które mogą być śledzone korzystanie z funkcji śledzenia biblioteki agentów  
  
```
enum Agents_EventType;
```  

### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`AGENTS_EVENT_CREATE`|Typ zdarzenia, który reprezentuje obiekt|  
|`AGENTS_EVENT_DESTROY`|Typ zdarzenia, który reprezentuje usunięcie obiektu|  
|`AGENTS_EVENT_END`|Typ zdarzenia, który reprezentuje zawarcia niektóre przetwarzania|  
|`AGENTS_EVENT_LINK`|Typ zdarzenia, który reprezentuje powiązanie bloki komunikatów|  
|`AGENTS_EVENT_NAME`|Typ zdarzenia, który reprezentuje nazwę dla obiektu|  
|`AGENTS_EVENT_SCHEDULE`|Typ zdarzenia, który reprezentuje planowania procesu|  
|`AGENTS_EVENT_START`|Typ zdarzenia, który reprezentuje inicjowania niektórych przetwarzania|  
|`AGENTS_EVENT_UNLINK`|Typ zdarzenia, który reprezentuje odłączenie bloki komunikatów|  

### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h

##  <a name="concrt_eventtype"></a>  Concrt_eventtype — wyliczenie  
 Typy zdarzeń, które mogą być śledzone korzystanie z funkcji śledzenia współbieżności środowiska wykonawczego.  
  
```
enum ConcRT_EventType;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`CONCRT_EVENT_ATTACH`|Typ zdarzenia, który reprezentuje polega na dołączenie do harmonogramu.|  
|`CONCRT_EVENT_BLOCK`|Typ zdarzenia, który reprezentuje act blokowania kontekstu.|  
|`CONCRT_EVENT_DETACH`|Typ zdarzenia, który reprezentuje czynność odłączanie od harmonogramu.|  
|`CONCRT_EVENT_END`|Typ zdarzenia, który oznacza początek parę zdarzenia rozpoczęcia i zakończenia.|  
|`CONCRT_EVENT_GENERIC`|Typ zdarzenia używane do różnych zdarzeń.|  
|`CONCRT_EVENT_IDLE`|Typ zdarzenia, który reprezentuje act kontekstu przechodzących do stanu bezczynności.|  
|`CONCRT_EVENT_START`|Typ zdarzenia, który oznacza początek parę zdarzenia rozpoczęcia i zakończenia.|  
|`CONCRT_EVENT_UNBLOCK`|Typ zdarzenia, który reprezentuje czynność odblokowywania w kontekście.|  
|`CONCRT_EVENT_YIELD`|Typ zdarzenia, który reprezentuje czynność reaguje kontekstu.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h **Namespace:** współbieżności

##  <a name="concrt_traceflags"></a>  Concrt_traceflags — wyliczenie  
 Flagi śledzenia dla typów zdarzeń  
  
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
 Typ krytyczne regionie, w którym znajduje się w kontekście.  
  
```
enum CriticalRegionType;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`InsideCriticalRegion`|Wskazuje, czy kontekst jest wewnątrz krytyczne regionu. Podczas wewnątrz obszaru krytyczne zawieszeniu asynchroniczne są ukryte z harmonogramu. Należy takiego zawieszenia się zdarzyć Menedżera zasobów będzie oczekiwał na wątku do uruchomienia i po prostu Wznów zamiast wywoływania planista ponownie. Wszystkie blokady podjąć takie obszarze należy z rozwagą.|  
|`InsideHyperCriticalRegion`|Wskazuje, czy kontekst jest wewnątrz funkcji hyper krytyczne regionu. Gdy wewnątrz funkcji hyper krytyczne regionu, zawieszeniu synchroniczne i asynchroniczne są ukryte z harmonogramu. Należy takie zawieszenie lub blokuje wystąpi, Menedżer zasobów będzie oczekiwał na wątku do uruchomienia i po prostu Wznów zamiast wywoływania planista ponownie. Blokad podjąć takie obszarze nigdy nie muszą być udostępnione z kodem działających poza obszarem takie. W ten sposób spowoduje nieprzewidywalne zakleszczenia.|  
|`OutsideCriticalRegion`|Wskazuje, czy kontekst jest poza dowolny region krytyczne.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrtrm.h 

##  <a name="dynamicprogressfeedbacktype"></a>  DynamicProgressFeedbackType Enumeration  
 Używane przez `DynamicProgressFeedback` na podstawie zasad do opisywania, czy zasoby harmonogramu zostanie rebalanced zgodnie z informacje statystyczne zebrane z harmonogramu lub tylko na przechodzenie do i stanu bezczynności za pośrednictwem wywołania procesorówwirtualnych`Activate` i `Deactivate` metody `IVirtualProcessorRoot` interfejsu. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
```
enum DynamicProgressFeedbackType;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ProgressFeedbackDisabled`|Planista nie zbierać informacje o postępie. Ponowne równoważenie odbywa się na podstawie wyłącznie na poziomie subskrypcji źródłowej wątku sprzętu. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).<br /><br /> Ta wartość jest zarezerwowany do użytku przez środowisko uruchomieniowe.|  
|`ProgressFeedbackEnabled`|Planista gromadzi informacje o postępie i przekazuje je do Menedżera zasobów. Menedżer zasobów będzie korzystać z tej informacji statystycznych równoważenie zasobów w imieniu harmonogramu oprócz poziom subskrypcji źródłowej wątku sprzętu. Aby uzyskać więcej informacji na temat poziomów subskrypcji, zobacz [IExecutionResource::CurrentSubscriptionLevel](IExecutionResource-structure.md).|  
##  <a name="join_type"></a>  join_type — wyliczenie  
 Typ `join` bloku obsługi wiadomości.  
  
```
enum join_type;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`greedy`|Zachłanne `join` bloki komunikatów natychmiast zaakceptować komunikat po propagacji. Jest to bardziej wydajne, ale ma możliwość live-lock, w zależności od konfiguracji sieci.|  
|`non_greedy`|Zachłanne inne niż `join` bloki komunikatów odłożyć wiadomości i spróbuj i używanie po wszystkich następować. Te dotrą do pracy, ale wolniej.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  

##  <a name="message_status"></a>  message_status — wyliczenie  
 Nieprawidłowa odpowiedzi dla oferty `message` obiektu do bloku.  
  
```
enum message_status;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`accepted`|Element docelowy akceptowane wiadomości.|  
|`declined`|Element docelowy nie zaakceptowała wiadomości.|  
|`missed`|Element docelowy próbował akceptowanie komunikatu, ale nie jest już dostępne.|  
|`postponed`|Element docelowy odroczone wiadomości.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** agents.h  

##  <a name="policyelementkey"></a>  Policyelementkey — wyliczenie  
 Klucze zasad opisujące aspekty zachowania harmonogramu. Każdy element zasad jest opisane przez pary klucz wartość. Aby uzyskać więcej informacji na temat zasad harmonogramu i ich wpływ na planiści zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
```
enum PolicyElementKey;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ContextPriority`|Priorytet wątku systemu operacyjnego każdy kontekst w harmonogramie. Jeśli ten klucz jest ustawiona na wartość `INHERIT_THREAD_PRIORITY` kontekstów w harmonogramie będzie dziedziczyć priorytet wątek, który utworzył harmonogramu.<br /><br /> Prawidłowe wartości: dowolne prawidłowe wartości dla systemu Windows `SetThreadPriority` funkcji i specjalna wartość `INHERIT_THREAD_PRIORITY`<br /><br /> Wartość domyślna: `THREAD_PRIORITY_NORMAL`|  
|`ContextStackSize`|Rozmiar stosu zastrzeżone każdy kontekst w harmonogramie w kilobajtach.<br /><br /> Prawidłowe wartości: dodatnie liczby całkowite<br /><br /> Wartość domyślna: `0`, wskazujący, że można użyć wartości domyślnych procesu dla rozmiaru stosu.|  
|`DynamicProgressFeedback`|Określa, czy zasoby harmonogram zostanie rebalanced zgodnie z informacje statystyczne zebrane z harmonogramu lub oparty wyłącznie na poziomie subskrypcji źródłowej wątków sprzętu. Aby uzyskać więcej informacji, zobacz [dynamicprogressfeedbacktype —](#dynamicprogressfeedbacktype).<br /><br /> Prawidłowe wartości: członek `DynamicProgressFeedbackType` wyliczenia, albo `ProgressFeedbackEnabled` lub `ProgressFeedbackDisabled`<br /><br /> Wartość domyślna: `ProgressFeedbackEnabled`|  
|`LocalContextCacheSize`|Gdy `SchedulingProtocol` zasad jest ustawiona na wartość `EnhanceScheduleGroupLocality`, określa maksymalną liczbę do uruchomienia kontekstach, które mogą być buforowane w na lokalne kolejki procesora wirtualnego. Takie kontekstów zwykle będą uruchamiane w kolejności (LIFO) ostatnich w pierwszym poza na procesora wirtualnego, który spowodował je, aby stać się do uruchomienia. Należy zauważyć że tego klucza zasad nie ma żadnych oznacza, kiedy `SchedulingProtocol` jest ustawiona na wartość `EnhanceForwardProgress`.<br /><br /> Prawidłowe wartości: — nieujemne liczby całkowite<br /><br /> Wartość domyślna: `8`|  
|`MaxConcurrency`|Współbieżność maksymalny poziom wymaganą przez harmonogram. Menedżer zasobów spróbuje początkowo przydzielić następująca liczba procesorów wirtualnych. Specjalna wartość [maxexecutionresources —](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że poziom żądaną współbieżności jest taka sama jak liczba wątków sprzętu na komputerze. Jeśli wartość określona dla `MinConcurrency` jest większa niż liczba wątków sprzętu na komputerze i `MaxConcurrency` jest określony jako `MaxExecutionResources`, wartość `MaxConcurrency` jest zgłaszane do dopasowania, co jest ustawiony dla `MinConcurrency`.<br /><br /> Prawidłowe wartości: dodatnie liczby całkowite i specjalna wartość `MaxExecutionResources`<br /><br /> Wartość domyślna: `MaxExecutionResources`|  
|`MaxPolicyElementKey`|Klucz elementu maksymalną zasad. Nie klucz prawidłowego elementu.|  
|`MinConcurrency`|Współbieżność minimalny poziom musi być dostarczona do harmonogramu przez Menedżera zasobów. Liczba procesorów wirtualnych przypisanych do harmonogramu nigdy nie przejdzie poniżej wartości minimalnej. Specjalna wartość [maxexecutionresources —](concurrency-namespace-constants1.md#maxexecutionresources) wskazuje, że poziom współbieżności minimalna jest taka sama jak liczba wątków sprzętu na komputerze. Jeśli wartość określona dla `MaxConcurrency` jest mniejsza niż liczba wątków sprzętu na komputerze i `MinConcurrency` jest określony jako `MaxExecutionResources`, wartość `MinConcurrency` jest obniżona do dopasowania, co jest ustawiony dla `MaxConcurrency`.<br /><br /> Prawidłowe wartości: nieujemnymi liczbami całkowitymi i specjalna wartość `MaxExecutionResources`. Należy pamiętać, że zasady harmonogram używany do budowy planiści współbieżność środowiska wykonawczego, wartość `0` jest nieprawidłowa.<br /><br /> Wartość domyślna: `1`|  
|`SchedulerKind`|Typ wątków wykorzystujące harmonogramu dla podstawowej kontekstów wykonywania. Aby uzyskać więcej informacji, zobacz [schedulertype —](#schedulertype).<br /><br /> Prawidłowe wartości: członek `SchedulerType` wyliczenia, na przykład `ThreadScheduler`<br /><br /> Wartość domyślna: `ThreadScheduler`. Umożliwia to Win32 wątki we wszystkich systemach operacyjnych.|  
|`SchedulingProtocol`|W tym artykule opisano, w których planowania algorytm ma zostać użyty przez harmonogram. Aby uzyskać więcej informacji, zobacz [schedulingprotocoltype —](#schedulingprotocoltype).<br /><br /> Prawidłowe wartości: członek `SchedulingProtocolType` wyliczenia, albo `EnhanceScheduleGroupLocality` lub `EnhanceForwardProgress`<br /><br /> Wartość domyślna: `EnhanceScheduleGroupLocality`|  
|`TargetOversubscriptionFactor`|Wstępne liczba procesorów wirtualnych przypadających na wątku sprzętu. Współczynnik nadsubskrypcji docelowych można zwiększyć przez Menedżera zasobów w razie potrzeby można zrealizować `MaxConcurrency` z wątkami sprzętu na komputerze.<br /><br /> Prawidłowe wartości: dodatnie liczby całkowite<br /><br /> Wartość domyślna: `1`|  
|`WinRTInitialization`||  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  

##  <a name="schedulertype"></a>  Schedulertype — wyliczenie  
 Używane przez `SchedulerKind` zasad do opisu typu wątków powinien wykorzystujące dla podstawowej kontekstów wykonywania dla harmonogramu. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
```
enum SchedulerType;
``` 

### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`ThreadScheduler`|Wskazuje jawne żądanie regularne wątków Win32.|  
|`UmsThreadDefault`|Tryb użytkownika schedulable wątków (UMS) nie są obsługiwane w współbieżność środowiska wykonawczego w programie Visual Studio 2013. Przy użyciu `UmsThreadDefault` jako wartość `SchedulerType` zasad nie spowoduje błąd. Jednak harmonogramu utworzone za pomocą tej zasady domyślnie zostanie ustawiona za pomocą wątków Win32.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
  
##  <a name="schedulingprotocoltype"></a>  Schedulingprotocoltype — wyliczenie  
 Używane przez `SchedulingProtocol` zasad do opisywania, który algorytm planowania, które zostaną użyte dla harmonogramu. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
```
enum SchedulingProtocolType;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`EnhanceForwardProgress`|Planista preferuje okrężnego za pośrednictwem grup harmonogramu po wykonaniu każdego zadania. Odblokowany konteksty zwykle są planowane w sposób pierwszy w pierwszym out (FIFO). Procesory wirtualne nie buforują kontekstów odblokowany.|  
|`EnhanceScheduleGroupLocality`|Planista preferuje kontynuować pracę przed przejściem do innej grupy harmonogramu zadań w bieżącej grupie harmonogramu. Odblokowany konteksty są buforowane na procesorów wirtualnych i w czasie ostatnich w pierwszym poza (LIFO) procesorów wirtualnych, które je odblokowany zwykle są zaplanowane.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  
 
##  <a name="switchingproxystate"></a>  Switchingproxystate — wyliczenie  
 Używany do określenia stanu, w którym jest serwer proxy wątku, podczas jej wykonywania przełączanie kontekstu wspólnych do serwera proxy w innym wątku.  
  
```
enum SwitchingProxyState;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`Blocking`|Wskazuje, że wątek wywołujący wspólnie blokuje właścicielem powinien być wyłącznie wywołującego dopiero następnie ponowne uruchomienie i wykonywania innych działań.|  
|`Idle`|Wskazuje, że wątek wywołujący jest już potrzebne przez harmonogram Menedżera zasobów zostały zwrócone. Kontekst, który był wysyłany nie jest już może zostać wykorzystane przez Menedżera zasobów.|  
|`Nesting`|Wskazuje, że wątek wywołujący jest zagnieżdżanie harmonogramu podrzędny i jest wymagane przez obiekt wywołujący, aby można było dołączyć do różnych harmonogramu.|  

### <a name="remarks"></a>Uwagi  
 Parametr typu `SwitchingProxyState` jest przekazywany do metody `IThreadProxy::SwitchTo` nakazać Menedżerowi zasobów sposobu traktowania serwera proxy w wątku, który jest wywołania.  
  
 Aby uzyskać więcej informacji dotyczących korzystania z tego typu, zobacz [IThreadProxy::SwitchTo](ithreadproxy-structure.md#switchto).  
  
##  <a name="task_group_status"></a>  task_group_status — wyliczenie  
 Opisuje stan wykonywania `task_group` lub `structured_task_group` obiektu. Wartość tego typu jest zwracany przez wiele metod, które oczekiwanie na zadania zaplanowane do grupy zadań do wykonania.  
  
```
enum task_group_status;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`canceled`|`task_group` Lub `structured_task_group` obiektu została anulowana. Jedno lub więcej zadań nie mogło zostać wykonane.|  
|`completed`|Zadania w kolejce w celu `task_group` lub `structured_task_group` obiektu została ukończona pomyślnie.|  
|`not_complete`|Zadania w kolejce w celu `task_group` obiektu nie została ukończona. Należy pamiętać, że ta wartość nie jest obecnie zwrócone przez współbieżności środowiska wykonawczego.|  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** pplinterface.h  

##  <a name="winrtinitializationtype"></a>  Winrtinitializationtype — wyliczenie  
 Używane przez `WinRTInitialization` zasad do opisywania, czy i jak środowiska uruchomieniowego systemu Windows zostanie zainicjowana na harmonogram wątków dla aplikacji, która działa w systemach operacyjnych z wersją systemu Windows 8 lub nowszy. Aby uzyskać więcej informacji o zasadach dostępne harmonogramu, zobacz [policyelementkey —](concurrency-namespace-enums.md).  
  
```
enum WinRTInitializationType;
```  
### <a name="values"></a>Wartości  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`DoNotInitializeWinRT`|Gdy aplikacja jest uruchomione w systemach operacyjnych z wersją systemu Windows 8 lub wyższym, wątki w ramach harmonogramu zadań nie zostanie zainicjowana środowiska uruchomieniowego systemu Windows.|  
|`InitializeWinRTAsMTA`|Po uruchomieniu aplikacji w systemach operacyjnych z wersją systemu Windows 8 lub nowszym, każdy wątek w ramach harmonogramu zadań będzie zainicjować środowiska uruchomieniowego systemu Windows i zadeklarować, że jest częścią apartamentu wielowątkowych.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** concrt.h  

## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
