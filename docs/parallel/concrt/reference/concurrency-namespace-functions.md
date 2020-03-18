---
title: Funkcje przestrzeni nazw współbieżności
ms.date: 11/04/2016
f1_keywords:
- concrt/concurrency::Alloc
- concrt/concurrency::DisableTracing
- concrt/concurrency::EnableTracing
- concrtrm/concurrency::GetExecutionContextId
- concrtrm/concurrency::GetOSVersion
- concrtrm/concurrency::GetProcessorNodeCount
- concrtrm/concurrency::GetSchedulerId
- agents/concurrency::asend
- ppltasks/concurrency::cancel_current_task
- ppltasks/concurrency::create_async
- ppltasks/concurrency::create_task
- concurrent_vector/concurrency::internal_assign_iterators
- ppl/concurrency::interruption_point
- agents/concurrency::make_choice
- agents/concurrency::make_greedy_join
- ppl/concurrency::make_task
- ppl/concurrency::parallel_buffered_sort
- ppl/concurrency::parallel_for_each
- ppl/concurrency::parallel_invoke
- ppl/concurrency::parallel_reduce
- ppl/concurrency::parallel_sort
- agents/concurrency::receive
- ppl/concurrency::run_with_cancellation_token
- pplconcrt/concurrency::set_ambient_scheduler
- concrt/concurrency::set_task_execution_resources
- ppltasks/concurrency::task_from_exception
- ppltasks/concurrency::task_from_result
- concrt/concurrency::wait
- ppltasks/concurrency::when_all
- ppltasks/concurrency::when_any
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
ms.openlocfilehash: 4005ae888511ec987fe83ab3d616aa0fc3675a22
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419141"
---
# <a name="concurrency-namespace-functions"></a>Funkcje przestrzeni nazw współbieżności

||||
|-|-|-|
|[Alokacj](#alloc)|[CreateResourceManager —](#createresourcemanager)|[DisableTracing —](#disabletracing)|
|[EnableTracing —](#enabletracing)|[Bezpłatna](#free)|[GetExecutionContextId —](#getexecutioncontextid)|
|[GetOSVersion —](#getosversion)|[GetProcessorCount —](#getprocessorcount)|[GetProcessorNodeCount —](#getprocessornodecount)|
|[GetSchedulerId —](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[Wyczyść](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[przyjęte](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[Wyślij](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[wymiany](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[trwa](#wait)|
|[when_all](#when_all)|[when_any](#when_any)|

## <a name="alloc"></a>Alokacj

Przydziela blok pamięci o rozmiarze określonym na podstawie podprzydziału buforowania środowisko uruchomieniowe współbieżności.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parametry

*_NumBytes*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik do nowo przydzieloną pamięć.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o tym, które scenariusze w aplikacji mogą skorzystać z używania podprzydziału buforowania, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a>asend

Asynchroniczna operacja wysyłania, która planuje zadanie propagacji danych do docelowego bloku.

```cpp
template <class T>
bool asend(
    _Inout_ ITarget<T>* _Trg,
    const T& _Data);

template <class T>
bool asend(
    ITarget<T>& _Trg,
    const T& _Data);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych do wysłania.

*_Trg*<br/>
Wskaźnik lub odwołanie do elementu docelowego, do którego są wysyłane dane.

*_Data*<br/>
Odwołanie do danych do wysłania.

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli wiadomość została zaakceptowana przed zwróceniem metody, w przeciwnym razie **false** .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a>cancel_current_task

Anuluje aktualnie wykonywane zadanie. Ta funkcja może zostać wywołana z poziomu treści zadania, aby przerwać wykonywanie zadania i spowodować, że będzie ona wprowadzać stan `canceled`.

Nie jest to obsługiwany scenariusz do wywołania tej funkcji, jeśli nie znajdujesz się w treści `task`. Wykonanie tej czynności spowoduje niezdefiniowane zachowanie, takie jak awaria lub zawieszenie aplikacji.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a>Wyczyść

Czyści kolejkę współbieżną, zniszczyć wszystkie elementy znajdujące się w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parametry

*&*<br/>

*_Ax*<br/>

## <a name="create_async"></a>create_async

Tworzy środowisko wykonawcze systemu Windows asynchronicznej na podstawie podanego przez użytkownika obiektu lambda lub funkcji. Zwracany typ `create_async` jest jedną z `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`lub `IAsyncOperationWithProgress<TResult, TProgress>^` na podstawie podpisu wyrażenia lambda przekazaną do metody.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ.

*_Func*<br/>
Obiekt lambda lub Function, z którego ma zostać utworzona konstrukcja asynchroniczna środowisko wykonawcze systemu Windows.

### <a name="return-value"></a>Wartość zwrócona

Konstrukcja asynchroniczna reprezentowana przez IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^ lub IAsyncOperationWithProgress\<TResult, TProgress > ^. Zwracany interfejs zależy od podpisu wyrażenia lambda przekazana do funkcji.

### <a name="remarks"></a>Uwagi

Zwracany typ wyrażenia lambda określa, czy konstrukcja jest akcją czy operacją.

Wyrażenia lambda zwracające wartość void powodują utworzenie akcji. Wyrażenia lambda zwracające wynik typu `TResult` powodują utworzenie operacji TResult.

Wyrażenie lambda może również zwracać `task<TResult>`, która hermetyzuje aysnchronous w sobie lub jest kontynuacją łańcucha zadań, które reprezentują czas pracy asynchronicznej. W takim przypadku samo wyrażenie lambda jest wykonywane w tekście, ponieważ zadania są tymi, które są wykonywane asynchronicznie, a zwracany typ Lambda jest nieopakowany w celu utworzenia konstrukcji asynchronicznej zwróconej przez `create_async`. Oznacza to, że wyrażenie lambda zwracające zadanie\<void > spowoduje utworzenie akcji, a wyrażenie lambda zwracające zadanie\<TResult > spowoduje utworzenie operacji TResult.

Wyrażenie lambda może przyjmować zero, jeden lub dwa argumenty. Prawidłowe argumenty są `progress_reporter<TProgress>` i `cancellation_token`w tej kolejności, jeśli oba są używane. Wyrażenie lambda bez argumentów powoduje utworzenie konstrukcji asynchronicznej bez możliwości raportowania postępu. Wyrażenie lambda, które przyjmuje progress_reporter\<TProgress > spowoduje zwrócenie przez `create_async` asynchronicznej konstrukcji, która raportuje postęp typu TProgress przy każdym wywołaniu metody `report` obiektu progress_reporter. Lambda, która pobiera cancellation_token może użyć tego tokenu do sprawdzenia anulowania lub przekazania go do zadań, które tworzy, tak aby anulowanie konstrukcji asynchronicznej spowodowało anulowanie tych zadań.

Jeśli treść obiektu lambda lub funkcji zwraca wynik (a nie zadanie\<TResult >), lamdba będzie wykonywany asynchronicznie w ramach procesu MTA w kontekście zadania, które jest niejawnie tworzone dla tego elementu. Metoda `IAsyncInfo::Cancel` spowoduje anulowanie zadania niejawnego.

Jeśli treść wyrażenia lambda zwraca zadanie, mięso jagnięce wykonuje wbudowaną i deklarując wyrażenie lambda do wykonania argumentu typu `cancellation_token` można wyzwolić anulowanie wszystkich zadań tworzonych w ramach lambda przez przekazanie tego tokenu podczas tworzenia. Możesz również użyć metody `register_callback` na tokenie, aby spowodować wywołanie wywołania zwrotnego przez środowisko uruchomieniowe w przypadku wywołania `IAsyncInfo::Cancel` operacji asynchronicznej lub wygenerowanej akcji.

Ta funkcja jest dostępna tylko dla środowisko wykonawcze systemu Windows aplikacji.

## <a name="createresourcemanager"></a>CreateResourceManager —

Zwraca interfejs, który reprezentuje pojedyncze wystąpienie Menedżer zasobów środowisko uruchomieniowe współbieżności. Menedżer zasobów jest odpowiedzialny za przypisywanie zasobów do harmonogramów, które chcą współpracować ze sobą.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Wartość zwrócona

Interfejs `IResourceManager`.

### <a name="remarks"></a>Uwagi

Wiele kolejnych wywołań tej metody zwróci to samo wystąpienie Menedżer zasobów. Każde wywołanie metody zwiększa liczbę odwołań na Menedżer zasobów i musi być zgodne z wywołaniem metody [IResourceManager:: Release](iresourcemanager-structure.md) , gdy harmonogram przeprowadza komunikację z Menedżer zasobów.

[unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="create_task"></a>create_task

Tworzy obiekt [zadania](task-class.md) PPL. `create_task` można używać wszędzie tam, gdzie użyto konstruktora zadań. Jest ona świadczona głównie dla wygody, ponieważ umożliwia użycie słowa kluczowego `auto` podczas tworzenia zadań.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ parametru, z którego ma zostać wykonane zadanie.

*_ReturnType*<br/>
Typ.

*_Param*<br/>
Parametr, z którego ma zostać wykonane zadanie. Może to być obiekt lambda lub Function, obiekt `task_completion_event`, inny obiekt `task` lub interfejs Windows:: Foundation:: IAsyncInfo, jeśli używasz zadań w aplikacji platformy UWP.

*_TaskOptions*<br/>
Opcje zadania.

*_Task*<br/>
Zadanie, które ma zostać utworzone.

### <a name="return-value"></a>Wartość zwrócona

Nowe zadanie typu `T`, które jest wywnioskowane z `_Param`.

### <a name="remarks"></a>Uwagi

Pierwsze Przeciążenie zachowuje się jak Konstruktor zadań, który przyjmuje jeden parametr.

Drugie przeciążenie kojarzy token anulowania dostarczony z nowo utworzonym zadaniem. W przypadku użycia tego przeciążenia nie można przekazać innego obiektu `task` jako pierwszego parametru.

Typ zwracanego zadania jest wywnioskowany na podstawie pierwszego parametru do funkcji. Jeśli `_Param` jest `task_completion_event<T>`, `task<T>`lub Funktor, które zwraca `T` typu lub `task<T>`, typ utworzonego zadania jest `task<T>`.

W aplikacji platformy UWP, jeśli `_Param` jest typu Windows:: Foundation:: IAsyncOperation\<T > ^ lub Windows:: Foundation:: IAsyncOperationWithProgress\<T, P > ^ lub Funktor, który zwraca jeden z tych typów, utworzone zadanie będzie typu `task<T>`. Jeśli `_Param` jest typu Windows:: Foundation:: IAsyncAction ^ lub Windows:: Foundation:: IAsyncActionWithProgress\<P > ^ lub Funktor, który zwraca jeden z tych typów, utworzone zadanie będzie miało typ `task<void>`.

## <a name="disabletracing"></a>DisableTracing —

Wyłącza śledzenie w środowisko uruchomieniowe współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest domyślnie wyrejestrowane.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli śledzenie zostało prawidłowo wyłączone, `S_OK` jest zwracana. Jeśli nie zainicjowano wcześniej śledzenia, `E_NOT_STARTED` jest zwracana

## <a name="enabletracing"></a>EnableTracing —

Włącza śledzenie w środowisko uruchomieniowe współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest teraz domyślnie włączone.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Wartość zwrócona

Jeśli śledzenie zostało prawidłowo zainicjowane, zwracany jest `S_OK`. w przeciwnym razie zostanie zwrócona `E_NOT_STARTED`.

## <a name="free"></a>Zwolniony

Zwalnia blok pamięci, który został wcześniej przydzielony przez metodę `Alloc` do podprzydzielania środowisko uruchomieniowe współbieżności buforowania.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parametry

*_PAllocation*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez metodę `Alloc`, która ma zostać zwolniona. Jeśli parametr `_PAllocation` jest ustawiony na wartość `NULL`, ta metoda zignoruje ją i zwróci natychmiast.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o tym, które scenariusze w aplikacji mogą skorzystać z używania podprzydziału buforowania, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Wartość zwrócona

## <a name="getexecutioncontextid"></a>GetExecutionContextId —

Zwraca unikatowy identyfikator, który można przypisać do kontekstu wykonywania implementującego interfejs `IExecutionContext`.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator kontekstu wykonywania.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby uzyskać identyfikator kontekstu wykonywania przed przekazaniem `IExecutionContext` interfejsu jako parametru do dowolnej metody oferowanej przez Menedżer zasobów.

## <a name="getosversion"></a>GetOSVersion —

Zwraca wersję systemu operacyjnego.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Wartość zwrócona

Wartość wyliczana reprezentująca system operacyjny.

### <a name="remarks"></a>Uwagi

[unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="getprocessorcount"></a>GetProcessorCount —

Zwraca liczbę wątków sprzętowych w źródłowym systemie.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Wartość zwrócona

Liczba wątków sprzętowych.

### <a name="remarks"></a>Uwagi

[unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="getprocessornodecount"></a>GetProcessorNodeCount —

Zwraca liczbę węzłów NUMA lub pakietów procesorów w źródłowym systemie.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Wartość zwrócona

Liczba węzłów NUMA lub pakietów procesora.

### <a name="remarks"></a>Uwagi

Jeśli system zawiera więcej węzłów NUMA niż pakiety procesorów, zwracana jest liczba węzłów NUMA. w przeciwnym razie zwracana jest liczba pakietów procesora.

[unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="getschedulerid"></a>GetSchedulerId —

Zwraca unikatowy identyfikator, który można przypisać do harmonogramu implementującego interfejs `IScheduler`.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Wartość zwrócona

Unikatowy identyfikator dla harmonogramu.

### <a name="remarks"></a>Uwagi

Użyj tej metody, aby uzyskać identyfikator dla harmonogramu przed przekazaniem `IScheduler` interfejsu jako parametru do dowolnej metody oferowanej przez Menedżer zasobów.

## <a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parametry

*&*<br/>

*_Ax*<br/>

*_I*<br/>

*pierwszego*<br/>

*ostatniego*<br/>

## <a name="interruption_point"></a>interruption_point

Tworzy punkt przerwania do anulowania. Jeśli anulowanie jest w toku w kontekście, w którym ta funkcja jest wywoływana, spowoduje to zgłoszenie wyjątku wewnętrznego, który przerywa wykonywanie aktualnie wykonywanej pracy równoległej. Jeśli anulowanie nie jest w toku, funkcja nic nie robi.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Uwagi

Nie należy przechwytywać wewnętrznego wyjątku anulowania zgłoszonego przez funkcję `interruption_point()`. Wyjątek zostanie przechwycony i obsłużony przez środowisko uruchomieniowe, a jego przechwycenie może spowodować nienormalne zachowanie programu.

## <a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Zwraca wskazanie, czy grupa zadań, która jest aktualnie uruchamiana w bieżącym kontekście, znajduje się w pośrodku aktywnego anulowania (lub będzie wkrótce). Należy pamiętać, że jeśli w bieżącym kontekście nie ma obecnie uruchomionej grupy zadań, `false` zostanie zwrócona.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli obecnie wykonywana jest grupa zadań, w przeciwnym razie **false** .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a>make_choice

Konstruuje blok `choice` Messaging z opcjonalnego `Scheduler` lub `ScheduleGroup` oraz co najmniej dwóch źródeł danych wejściowych.

```cpp
template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    Scheduler& _PScheduler,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    ScheduleGroup& _PScheduleGroup,
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
choice<std::tuple<T1, T2, Ts...>> make_choice(
    T1  _Item1,
    T2  _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parametry

*Połączeń*<br/>
Typ bloku komunikatu pierwszego źródła.

*T2*<br/>
Typ bloku komunikatu drugiego źródła.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `choice`.

*_Item1*<br/>
Pierwsze źródło.

*_Item2*<br/>
Drugie źródło.

*_Items*<br/>
Dodatkowe źródła.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `choice`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="return-value"></a>Wartość zwrócona

Blok komunikatów `choice` z co najmniej dwoma źródłami wejściowymi.

## <a name="make_greedy_join"></a>make_greedy_join

Konstruuje blok `greedy multitype_join` Messaging z opcjonalnego `Scheduler` lub `ScheduleGroup` oraz co najmniej dwóch źródeł danych wejściowych.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>,greedy> make_greedy_join(
    Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>, greedy> make_greedy_join(
    T1 _Item1,
    T2 _Items,
    Ts... _Items);
```

### <a name="parameters"></a>Parametry

*Połączeń*<br/>
Typ bloku komunikatu pierwszego źródła.

*T2*<br/>
Typ bloku komunikatu drugiego źródła.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `multitype_join`.

*_Item1*<br/>
Pierwsze źródło.

*_Item2*<br/>
Drugie źródło.

*_Items*<br/>
Dodatkowe źródła.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `multitype_join`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="return-value"></a>Wartość zwrócona

Blok komunikatów `greedy multitype_join` z co najmniej dwoma źródłami wejściowymi.

## <a name="make_join"></a>make_join

Konstruuje blok `non_greedy multitype_join` Messaging z opcjonalnego `Scheduler` lub `ScheduleGroup` oraz co najmniej dwóch źródeł danych wejściowych.

```cpp
template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>>
    make_join(
Scheduler& _PScheduler,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
ScheduleGroup& _PScheduleGroup,
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);

template<typename T1, typename T2, typename... Ts>
multitype_join<std::tuple<T1, T2, Ts...>> make_join(
    T1 _Item1,
    T2 _Item2,
    Ts... _Items);
```

### <a name="parameters"></a>Parametry

*Połączeń*<br/>
Typ bloku komunikatu pierwszego źródła.

*T2*<br/>
Typ bloku komunikatu drugiego źródła.

*_PScheduler*<br/>
Obiekt `Scheduler`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `multitype_join`.

*_Item1*<br/>
Pierwsze źródło.

*_Item2*<br/>
Drugie źródło.

*_Items*<br/>
Dodatkowe źródła.

*_PScheduleGroup*<br/>
Obiekt `ScheduleGroup`, w ramach którego zaplanowano zadanie propagacji dla bloku obsługi komunikatów `multitype_join`. Używany obiekt `Scheduler` jest implikowany przez grupę harmonogramów.

### <a name="return-value"></a>Wartość zwrócona

Blok komunikatów `non_greedy multitype_join` z co najmniej dwoma źródłami wejściowymi.

## <a name="make_task"></a>make_task

Metoda fabryki służąca do tworzenia obiektu `task_handle`.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany do wykonania pracy reprezentowanej przez obiekt `task_handle`.

*_Func*<br/>
Funkcja, która będzie wywoływana w celu wykonania pracy reprezentowanej przez obiekt `task_handle`. Może to być Funktor lambda, wskaźnik do funkcji lub dowolny obiekt obsługujący wersję operatora wywołania funkcji z podpisem `void operator()()`.

### <a name="return-value"></a>Wartość zwrócona

Obiekt `task_handle`.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna, gdy konieczne jest utworzenie obiektu `task_handle` z wyrażeniem lambda, ponieważ umożliwia utworzenie obiektu bez znajomości prawdziwego typu lambda Funktor.

## <a name="parallel_buffered_sort"></a>parallel_buffered_sort

Rozmieszcza elementy w określonym zakresie w kolejności niemalejącej lub zgodnie z kryterium porządkowania określonym przez Predykat binarny równolegle. Ta funkcja jest semantycznie podobna do `std::sort` w tym, że jest to porównanie, niestabilne, w miejscu, z wyjątkiem sytuacji, gdy wymaga `O(n)` dodatkowe miejsce, i wymaga domyślnej inicjalizacji dla sortowanych elementów.

```cpp
template<typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator,
    typename _Random_iterator>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_buffered_sort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parametry

*_Random_iterator*<br/>
Typ iteratora zakresu wejściowego.

*_Allocator*<br/>
Typ programu przydzielania C++ pamięci w standardowej bibliotece.

*_Function*<br/>
Typ komparator binarnego.

*_Begin*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać posortowany.

*_End*<br/>
Iterator dostępu swobodnego, odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać posortowany.

*_Alloc*<br/>
Wystąpienie programu przydzielania C++ pamięci w standardowej bibliotece.

*_Func*<br/>
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony. Ta funkcja komparator musi nałożyć ścisłe słabe porządkowanie dla par elementów z sekwencji.

*_Chunk_size*<br/>
Minimalny rozmiar fragmentu, który zostanie podzielony na dwa na potrzeby wykonywania równoległego.

### <a name="remarks"></a>Uwagi

Wszystkie przeciążenia wymagają `n * sizeof(T)` dodatkowej przestrzeni, gdzie `n` jest liczbą elementów do posortowania, a `T` jest typem elementu. W większości przypadków parallel_buffered_sort będzie pokazywać zwiększenie wydajności nad [parallel_sort](concurrency-namespace-functions.md)i należy go używać w parallel_sort, jeśli dostępna jest pamięć.

Jeśli nie podasz binarnego komparator `std::less` jest używany jako domyślny, który wymaga, aby typ elementu zapewniał operator `operator<()`.

Jeśli nie podasz typu lub wystąpienia alokatora, do przydzielenia buforu zostanie użyta `std::allocator<T>` alokatora pamięci biblioteki C++ standardowej.

Algorytm dzieli zakres wejściowy na dwa fragmenty i stopniowo dzieli każdy fragment na dwa fragmenty podrzędne do wykonania równolegle. Opcjonalnego argumentu `_Chunk_size` można użyć, aby wskazać algorytm, który powinien obsługiwać fragmenty rozmiaru < `_Chunk_size` szeregowo.

## <a name="parallel_for"></a>parallel_for

`parallel_for` wykonuje iterację w zakresie indeksów i wykonuje funkcję dostarczoną przez użytkownika w każdej iteracji równolegle.

```cpp
template <typename _Index_type, typename _Function, typename _Partitioner>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func,
    _Partitioner&& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    _Index_type _Step,
    const _Function& _Func);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const static_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    const simple_partitioner& _Part);

template <typename _Index_type, typename _Function>
void parallel_for(
    _Index_type first,
    _Index_type last,
    const _Function& _Func,
    affinity_partitioner& _Part);
```

### <a name="parameters"></a>Parametry

*_Index_type*<br/>
Typ indeksu używanego do iteracji.

*_Function*<br/>
Typ funkcji, która będzie wykonywana w każdej iteracji.

*_Partitioner*<br/>
Typ partycji używany do partycjonowania podanego zakresu.

*pierwszego*<br/>
Pierwszy indeks, który ma zostać uwzględniony w iteracji.

*ostatniego*<br/>
Indeks po ostatnim indeksie, który ma zostać uwzględniony w iteracji.

*_Step*<br/>
Wartość, według której należy wykonać iterację z `first`, aby `last`. Ten krok musi być dodatni. [invalid_argument](../../../standard-library/invalid-argument-class.md) jest generowany, jeśli krok jest mniejszy od 1.

*_Func*<br/>
Funkcja, która ma być wykonywana w każdej iteracji. Może to być wyrażenie lambda, wskaźnik funkcji lub dowolny obiekt obsługujący wersję operatora wywołania funkcji z podpisem `void operator()(_Index_type)`.

*_Part*<br/>
Odwołanie do obiektu Partitioner. Argument może być jednym z `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`, `const`[simple_partitioner](simple-partitioner-class.md)`&` lub [affinity_partitioner](affinity-partitioner-class.md)`&`, jeśli używany jest obiekt [affinity_partitioner](affinity-partitioner-class.md) , odwołanie musi być niestałym odwołaniem l-wartości, dzięki czemu algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a>parallel_for_each

`parallel_for_each` stosuje określoną funkcję do każdego elementu w obrębie zakresu równolegle. Jest semantycznie odpowiednikiem funkcji `for_each` w przestrzeni nazw `std`, z tą różnicą, że iteracja w elementach jest wykonywana równolegle, a kolejność iteracji nie została określona. Argument `_Func` musi obsługiwać operator wywołania funkcji w formularzu `operator()(T)` gdzie `T` jest typem elementu kontenera, w którym jest wykonywane powtarzanie.

```cpp
template <typename _Iterator, typename _Function>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func);

template <typename _Iterator, typename _Function, typename _Partitioner>
void parallel_for_each(
    _Iterator first,
    _Iterator last,
    const _Function& _Func,
    _Partitioner&& _Part);
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iteratora używanego do iteracji kontenera.

*_Function*<br/>
Typ funkcji, która zostanie zastosowana do każdego elementu w zakresie.

*_Partitioner*<br/>
*pierwszego*<br/>
Iterator odnoszący się do pozycji pierwszego elementu, który ma zostać uwzględniony w iteracji równoległej.

*ostatniego*<br/>
Iterator odnoszący się do pozycji jednej poza końcowym elementem, który ma zostać uwzględniony w iteracji równoległej.

*_Func*<br/>
Obiekt funkcji zdefiniowany przez użytkownika, który jest stosowany do każdego elementu w zakresie.

*_Part*<br/>
Odwołanie do obiektu Partitioner. Argument może być jednym z `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`, `const`[simple_partitioner](simple-partitioner-class.md)`&` lub [affinity_partitioner](affinity-partitioner-class.md)`&`, jeśli używany jest obiekt [affinity_partitioner](affinity-partitioner-class.md) , odwołanie musi być niestałym odwołaniem l-wartości, dzięki czemu algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia.

### <a name="remarks"></a>Uwagi

[auto_partitioner](auto-partitioner-class.md) będą używane do przeciążenia bez jawnego partycjonowania.

W przypadku iteratorów, które nie obsługują dostępu losowego, obsługiwane są tylko [auto_partitioner](auto-partitioner-class.md) .

Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a>parallel_invoke

Wykonuje obiekty funkcji dostarczone jako parametry równolegle i bloki do momentu zakończenia wykonywania. Każdy obiekt funkcji może być wyrażeniem lambda, wskaźnikiem do funkcji lub dowolnym obiektem, który obsługuje operator wywołania funkcji z sygnaturą `void operator()()`.

```cpp
template <typename _Function1, typename _Function2>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2);

template <typename _Function1, typename _Function2, typename _Function3>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9);

template <typename _Function1,
    typename _Function2,
    typename _Function3,
    typename _Function4,
    typename _Function5,
    typename _Function6,
    typename _Function7,
    typename _Function8,
    typename _Function9,
    typename _Function10>
void parallel_invoke(
    const _Function1& _Func1,
    const _Function2& _Func2,
    const _Function3& _Func3,
    const _Function4& _Func4,
    const _Function5& _Func5,
    const _Function6& _Func6,
    const _Function7& _Func7,
    const _Function8& _Func8,
    const _Function9& _Func9,
    const _Function10& _Func10);
```

### <a name="parameters"></a>Parametry

*_Function1*<br/>
Typ pierwszego obiektu funkcji, który ma być wykonywany równolegle.

*_Function2*<br/>
Typ drugiego obiektu funkcji, który ma być wykonywany równolegle.

*_Function3*<br/>
Typ trzeciego obiektu funkcji, który ma być wykonywany równolegle.

*_Function4*<br/>
Typ czwartego obiektu funkcji, który ma być wykonywany równolegle.

*_Function5*<br/>
Typ piątego obiektu funkcji, który ma być wykonywany równolegle.

*_Function6*<br/>
Typ szóstego obiektu funkcji, który ma być wykonywany równolegle.

*_Function7*<br/>
Typ siódmego obiektu funkcji, który ma być wykonywany równolegle.

*_Function8*<br/>
Typ ósmego obiektu funkcji, który ma być wykonywany równolegle.

*_Function9*<br/>
Typ dziewiątego obiektu funkcji, który ma być wykonywany równolegle.

*_Function10*<br/>
Typ dziesiątego obiektu funkcji, który ma być wykonywany równolegle.

*_Func1*<br/>
Pierwszy obiekt funkcji, który ma być wykonywany równolegle.

*_Func2*<br/>
Drugi obiekt funkcji, który ma być wykonywany równolegle.

*_Func3*<br/>
Trzeci obiekt funkcji, który ma być wykonywany równolegle.

*_Func4*<br/>
Czwarty obiekt funkcji, który ma być wykonywany równolegle.

*_Func5*<br/>
Piąty obiekt funkcji, który ma być wykonywany równolegle.

*_Func6*<br/>
Szósty obiekt funkcji, który ma być wykonywany równolegle.

*_Func7*<br/>
Obiekt funkcji siódmej, który ma być wykonywany równolegle.

*_Func8*<br/>
Obiekt funkcji ósmej, który ma być wykonywany równolegle.

*_Func9*<br/>
Dziewiąty obiekt funkcji, który ma być wykonywany równolegle.

*_Func10*<br/>
Obiekt funkcji dziesiątej, który ma być wykonywany równolegle.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że co najmniej jeden obiekt funkcji dostarczony jako parametry może wykonać wbudowaną w kontekście wywołującym.

Jeśli co najmniej jeden obiekt funkcji przeszedł jako parametry do tej funkcji zgłasza wyjątek, środowisko uruchomieniowe wybierze jeden z tych wyjątków i propaguje go z wywołania do `parallel_invoke`.

Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a>parallel_radixsort

Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności przy użyciu algorytmu sortowania podstawy. Jest to stabilna funkcja sortowania, która wymaga funkcji projekcji, która może projektować elementy do posortowania na klucze podobne do liczby całkowitej. Dla elementów, które są sortowane, wymagana jest Inicjalizacja domyślna.

```cpp
template<typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Allocator, typename _Random_iterator>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator, typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator, typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);

template<typename _Allocator,
    typename _Random_iterator,
    typename _Function>
inline void parallel_radixsort(
    const _Allocator& _Alloc,
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Proj_func,
    const size_t _Chunk_size = 256* 256);
```

### <a name="parameters"></a>Parametry

*_Random_iterator*<br/>
Typ iteratora zakresu wejściowego.

*_Allocator*<br/>
Typ programu przydzielania C++ pamięci w standardowej bibliotece.

*_Function*<br/>
Typ funkcji projekcji.

*_Begin*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać posortowany.

*_End*<br/>
Iterator dostępu swobodnego, odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać posortowany.

*_Alloc*<br/>
Wystąpienie programu przydzielania C++ pamięci w standardowej bibliotece.

*_Proj_func*<br/>
Zdefiniowany przez użytkownika obiekt funkcji projekcji, który konwertuje element na wartość całkowitą.

*_Chunk_size*<br/>
Minimalny rozmiar fragmentu, który zostanie podzielony na dwa na potrzeby wykonywania równoległego.

### <a name="remarks"></a>Uwagi

Wszystkie przeciążenia wymagają `n * sizeof(T)` dodatkowej przestrzeni, gdzie `n` jest liczbą elementów do posortowania, a `T` jest typem elementu. Funktor projekcja Jednoargumentowa z podpisem `I _Proj_func(T)` jest wymagana do zwrócenia klucza, gdy podano element, gdzie `T` jest typem elementu, a `I` jest typem nieoznaczonej liczby całkowitej przypominającej.

Jeśli nie podasz funkcji projekcji, domyślną funkcją projekcji, która po prostu zwraca element jest używany dla typów całkowitych. Kompilacja nie powiedzie się, jeśli element nie jest typem całkowitym w przypadku braku funkcji projekcji.

Jeśli nie podasz typu lub wystąpienia alokatora, do przydzielenia buforu zostanie użyta `std::allocator<T>` alokatora pamięci biblioteki C++ standardowej.

Algorytm dzieli zakres wejściowy na dwa fragmenty i stopniowo dzieli każdy fragment na dwa fragmenty podrzędne do wykonania równolegle. Opcjonalnego argumentu `_Chunk_size` można użyć, aby wskazać algorytm, który powinien obsługiwać fragmenty rozmiaru < `_Chunk_size` szeregowo.

## <a name="parallel_reduce"></a>parallel_reduce

Oblicza sumę wszystkich elementów w określonym zakresie przez Obliczanie kolejnych sum częściowych lub oblicza wynik kolejnych częściowe wyniki, podobnie jak w przypadku użycia określonej operacji binarnej innej niż suma, równolegle. `parallel_reduce` jest semantycznie podobna do `std::accumulate`, z tą różnicą, że wymaga skojarzenia operacji binarnej i wymaga wartości tożsamości zamiast początkowej wartości.

```cpp
template<typename _Forward_iterator>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity);

template<typename _Forward_iterator, typename _Sym_reduce_fun>
inline typename std::iterator_traits<_Forward_iterator>::value_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const typename std::iterator_traits<_Forward_iterator>::value_type& _Identity,
    _Sym_reduce_fun _Sym_fun);

template<typename _Reduce_type,
    typename _Forward_iterator,
    typename _Range_reduce_fun,
    typename _Sym_reduce_fun>
inline _Reduce_type parallel_reduce(
    _Forward_iterator _Begin,
    _Forward_iterator _End,
    const _Reduce_type& _Identity,
    const _Range_reduce_fun& _Range_fun,
    const _Sym_reduce_fun& _Sym_fun);
```

### <a name="parameters"></a>Parametry

*_Forward_iterator*<br/>
Typ iteratora zakresu wejściowego.

*_Sym_reduce_fun*<br/>
Typ funkcji redukcji symetrycznej. Musi to być typ funkcji z sygnaturą `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, gdzie _Reduce_type jest taka sama jak typ tożsamości i typ wyniku redukcji. W przypadku trzeciego przeciążenia należy zachować zgodność z typem danych wyjściowych `_Range_reduce_fun`.

*_Reduce_type*<br/>
Typ, do którego zostaną zredukowane dane wejściowe, co może być inne niż typ elementu wejściowego. Wartość zwracana i tożsamość będą mieć ten typ.

*_Range_reduce_fun*<br/>
Typ funkcji ograniczania zakresu. Musi to być typ funkcji z sygnaturą `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type jest taka sama jak typ tożsamości i typ wyniku redukcji.

*_Begin*<br/>
Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie, który ma zostać zmniejszony.

*_End*<br/>
Iterator danych wejściowych odnoszący się do elementu, który znajduje się w jednej pozycji poza elementem końcowym w zakresie, który ma zostać zmniejszony.

*_Identity*<br/>
Wartość tożsamości `_Identity` jest tego samego typu co typ wyniku redukcji, a także `value_type` iteratora dla pierwszego i drugiego przeciążenia. W przypadku trzeciego przeciążenia wartość tożsamości musi być tego samego typu co typ wyniku redukcji, ale może się różnić od `value_type` iteratora. Musi mieć odpowiednią wartość, taką jak operator redukcji zakresu `_Range_fun`, w przypadku zastosowania do zakresu pojedynczego elementu typu `value_type` i wartości tożsamości, zachowuje się jak rzutowanie typu wartości z typu `value_type` na typ tożsamości.

*_Sym_fun*<br/>
Funkcja symetryczna, która będzie używana w drugim zmniejszeniu. Aby uzyskać więcej informacji, zobacz uwagi.

*_Range_fun*<br/>
Funkcja, która będzie używana w pierwszej fazie zmniejszania. Aby uzyskać więcej informacji, zobacz uwagi.

### <a name="return-value"></a>Wartość zwrócona

Wynik redukcji.

### <a name="remarks"></a>Uwagi

Aby przeprowadzić równoległą redukcję, funkcja dzieli zakres na fragmenty w oparciu o liczbę procesów roboczych dostępnych dla odpowiedniego harmonogramu. Obniżka odbywa się w dwóch fazach, a Pierwsza faza wykonuje obniżkę w każdym fragmencie, a druga faza wykonuje redukcję między częściowymi wynikami każdego fragmentu.

Pierwsze Przeciążenie wymaga, aby `value_type`iteratora, `T`, być taka sama jak typ wartości tożsamości, a także typ wyniku redukcji. Typ elementu T musi dostarczyć operatora `T T::operator + (T)`, aby zmniejszyć liczbę elementów w każdym fragmencie. Ten sam operator jest używany również w drugiej fazie.

Drugie Przeciążenie wymaga również, aby `value_type` iteratora była taka sama jak typ wartości tożsamości, a także typ wyniku redukcji. Dostarczony `_Sym_fun` operatora binarnego jest używany w obu fazach zmniejszania, z wartością tożsamości jako początkową wartością dla pierwszej fazy.

W przypadku trzeciego przeciążenia typ wartości tożsamości musi być taki sam jak typ wyniku redukcji, ale `value_type` iteratora może się różnić od obu. Funkcja redukcji zakresu `_Range_fun` jest używana w pierwszej fazie z wartością tożsamości jako wartość początkową, a funkcja binarna `_Sym_reduce_fun` jest stosowana do wyników podrzędnych w drugiej fazie.

## <a name="parallel_sort"></a>parallel_sort

Rozmieszcza elementy w określonym zakresie w kolejności niemalejącej lub zgodnie z kryterium porządkowania określonym przez Predykat binarny równolegle. Ta funkcja jest semantycznie podobna do `std::sort` w tym, że jest to porównanie, niestabilne i w miejscu.

```cpp
template<typename _Random_iterator>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End);

template<typename _Random_iterator,typename _Function>
inline void parallel_sort(
    const _Random_iterator& _Begin,
    const _Random_iterator& _End,
    const _Function& _Func,
    const size_t _Chunk_size = 2048);
```

### <a name="parameters"></a>Parametry

*_Random_iterator*<br/>
Typ iteratora zakresu wejściowego.

*_Function*<br/>
Typ porównania binarnego Funktor.

*_Begin*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie, który ma zostać posortowany.

*_End*<br/>
Iterator dostępu swobodnego, odnoszący się do jednej z elementów znajdujących się poza ostatnim elementem w zakresie, który ma zostać posortowany.

*_Func*<br/>
Zdefiniowany przez użytkownika obiekt funkcji predykatu, który definiuje kryterium porównania do spełnienia przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true** , jeśli jest spełniony, i **wartość false** , gdy nie jest spełniony. Ta funkcja komparator musi nałożyć ścisłe słabe porządkowanie dla par elementów z sekwencji.

*_Chunk_size*<br/>
Minimalny rozmiar fragmentu, który zostanie podzielony na dwa na potrzeby wykonywania równoległego.

### <a name="remarks"></a>Uwagi

Pierwsze Przeciążenie używa binarnego komparator `std::less`.

Drugi przeciążony używa dostarczonych komparator binarnych, które powinny mieć sygnaturę `bool _Func(T, T)`, gdzie `T` jest typem elementów w zakresie wejściowym.

Algorytm dzieli zakres wejściowy na dwa fragmenty i stopniowo dzieli każdy fragment na dwa fragmenty podrzędne do wykonania równolegle. Opcjonalnego argumentu `_Chunk_size` można użyć, aby wskazać algorytm, który powinien obsługiwać fragmenty rozmiaru < `_Chunk_size` szeregowo.

## <a name="parallel_transform"></a>parallel_transform

Stosuje określony obiekt Function do każdego elementu w zakresie źródłowym lub do pary elementów z dwóch zakresów źródłowych i kopiuje wartości zwracane obiektu Function do zakresu docelowego równolegle. Ta funkcjonalność jest semantycznie równoważna z `std::transform`.

```cpp
template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const auto_partitioner& _Part = auto_partitioner());

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const static_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    const simple_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Output_iterator,
    typename _Unary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Output_iterator _Result,
    const _Unary_operator& _Unary_op,
    affinity_partitioner& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator,
    typename _Partitioner>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op,
    _Partitioner&& _Part);

template <typename _Input_iterator1,
    typename _Input_iterator2,
    typename _Output_iterator,
    typename _Binary_operator>
_Output_iterator parallel_transform(
    _Input_iterator1 first1,
    _Input_iterator1 last1,
    _Input_iterator2
first2,
    _Output_iterator _Result,
    const _Binary_operator& _Binary_op);
```

### <a name="parameters"></a>Parametry

*_Input_iterator1*<br/>
Typ pierwszego lub tylko iteratora wejściowego.

*_Output_iterator*<br/>
Typ iteratora danych wyjściowych.

*_Unary_operator*<br/>
Typ jednoargumentowej Funktor, który ma być wykonywany na każdym elemencie w zakresie wejściowym.

*_Input_iterator2*<br/>
Typ drugiego iteratora wejściowego.

*_Binary_operator*<br/>
Typ Funktor binarnego wykonała buforowanie dla elementów z dwóch zakresów źródłowych.

*_Partitioner*<br/>
*first1*<br/>
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w pierwszym lub tylko zakresie źródłowym, w którym mają być obsługiwane.

*last1*<br/>
Iterator danych wejściowych odnoszący się do pozycji jednej poza ostatnim elementem w pierwszym lub tylko zakresem źródłowym, na którym ma być wykonywane.

*_Result*<br/>
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym.

*_Unary_op*<br/>
Zdefiniowany przez użytkownika obiekt funkcji jednoargumentowej, który jest stosowany do każdego elementu w zakresie źródłowym.

*_Part*<br/>
Odwołanie do obiektu Partitioner. Argument może być jednym z `const`[auto_partitioner](auto-partitioner-class.md)`&`, `const`[static_partitioner](static-partitioner-class.md)`&`, `const`[simple_partitioner](simple-partitioner-class.md)`&` lub [affinity_partitioner](affinity-partitioner-class.md)`&`, jeśli używany jest obiekt [affinity_partitioner](affinity-partitioner-class.md) , odwołanie musi być niestałym odwołaniem l-wartości, dzięki czemu algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia.

*first2*<br/>
Iterator danych wejściowych odnoszący się do pozycji pierwszego elementu w drugim zakresie źródłowym, w którym mają być obsługiwane.

*_Binary_op*<br/>
Zdefiniowany przez użytkownika obiekt funkcji binarnej, który stosuje buforowanie w kolejności przesyłania dalej do dwóch zakresów źródłowych.

### <a name="return-value"></a>Wartość zwrócona

Iterator danych wyjściowych odnoszący się do pozycji jednej poza ostatnim elementem w zakresie docelowym, który otrzymuje elementy wyjściowe przekształcone przez obiekt Function.

### <a name="remarks"></a>Uwagi

[auto_partitioner](auto-partitioner-class.md) będą używane dla przeciążenia bez argumentu jawnego partycji.

W przypadku iteratorów, które nie obsługują dostępu losowego, obsługiwane są tylko [auto_partitioner](auto-partitioner-class.md) .

Przeciążenia, które przyjmują argument `_Unary_op` przekształcić zakres wejściowy do zakresu wyjściowego, stosując jednoargumentowy Funktor do każdego elementu w zakresie wejściowym. `_Unary_op` musi obsługiwać operator wywołania funkcji z sygnaturą `operator()(T)`, gdzie `T` jest typem wartości zakresu, w którym jest wykonywane powtarzanie.

Przeciążenia, które przyjmują argument `_Binary_op` przekształcić dwa zakresy wejściowe do zakresu wyjściowego, stosując Funktor binarny do jednego elementu z pierwszego zakresu wejściowego i jeden element z drugiego zakresu wejściowego. `_Binary_op` musi obsługiwać operator wywołania funkcji z sygnaturą `operator()(T, U)` gdzie `T`, `U` są typami wartości dwóch iteratorów wejściowych.

Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a>przyjęte

Ogólna implementacja odbierania, która zezwala na kontekst oczekiwania na dane z dokładnie jednego źródła i filtruje akceptowane wartości.

```cpp
template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    _Inout_ ISource<T>* _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);

template <class T>
T receive(
    ISource<T>& _Src,
    typename ITarget<T>::filter_method const& _Filter_proc,
    unsigned int _Timeout = COOPERATIVE_TIMEOUT_INFINITE);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku.

*_Src*<br/>
Wskaźnik lub odwołanie do źródła, z którego są oczekiwane dane.

*_Timeout*<br/>
Maksymalny czas, przez który Metoda powinna być dla danych (w milisekundach).

*_Filter_proc*<br/>
Funkcja filtru określająca, czy komunikaty powinny być akceptowane.

### <a name="return-value"></a>Wartość zwrócona

Wartość ze źródła typu ładunku.

### <a name="remarks"></a>Uwagi

Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, zostanie zgłoszony wyjątek [operation_timed_out](operation-timed-out-class.md) w przypadku upływu określonego czasu przed odebraniem wiadomości. Jeśli chcesz przekroczyć limit czasu o zerowej długości, użyj funkcji [try_receive](concurrency-namespace-functions.md) , w przeciwieństwie do wywoływania `receive` z limitem czasu `0` (zero), ponieważ jest bardziej wydajny i nie zgłasza wyjątków dla limitów czasu.

Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a>run_with_cancellation_token

Wykonuje obiekt funkcji natychmiast i synchronicznie w kontekście danego tokenu anulowania.

```cpp
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany.

*_Func*<br/>
Obiekt funkcji, który zostanie wykonany. Ten obiekt musi obsługiwać operator wywołania funkcji z podpisem void (void).

*_Ct*<br/>
Token anulowania, który będzie kontrolować niejawne anulowanie obiektu funkcji. Użyj `cancellation_token::none()`, jeśli chcesz, aby funkcja była wykonywana bez możliwości niejawnego anulowania z nadrzędnej grupy zadań, która jest anulowana.

### <a name="remarks"></a>Uwagi

Wszystkie punkty przerwania w obiekcie funkcji zostaną wyzwolone po anulowaniu `cancellation_token`. Jawny token `_Ct` będzie izolować ten `_Func` od anulowania nadrzędnego, jeśli element nadrzędny ma inny token lub żaden token.

## <a name="send"></a>Wyślij

Synchroniczna operacja wysyłania, która czeka, aż obiekt docelowy zaakceptuje lub odrzuci komunikat.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku.

*_Trg*<br/>
Wskaźnik lub odwołanie do elementu docelowego, do którego są wysyłane dane.

*_Data*<br/>
Odwołanie do danych do wysłania.

### <a name="return-value"></a>Wartość zwrócona

**prawda** , jeśli wiadomość została zaakceptowana, w przeciwnym razie **false** .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parametry

*_Scheduler*<br/>
Harmonogram otoczenia, który ma zostać ustawiony.

## <a name="set_task_execution_resources"></a>set_task_execution_resources

Ogranicza zasoby wykonywania używane przez środowisko uruchomieniowe współbieżności wewnętrznych wątków roboczych do określonego zestawu koligacji.

Ta metoda jest prawidłowa do wywołania tej metody tylko przed utworzeniem Menedżer zasobów lub między dwoma Menedżer zasobów okresów istnienia. Może być wywoływana wiele razy, dopóki Menedżer zasobów nie istnieje w czasie wywołania. Po ustawieniu limitu koligacji nadal obowiązuje do następnego prawidłowego wywołania metody `set_task_execution_resources`.

Podana maska koligacji nie musi być podzbiorem maski koligacji procesu. Koligacja procesu będzie aktualizowana w razie potrzeby.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parametry

*_ProcessAffinityMask*<br/>
Maska koligacji, do której mają być ograniczone wątki robocze środowisko uruchomieniowe współbieżności. Tej metody należy użyć w systemie z więcej niż 64 wątków sprzętowych tylko wtedy, gdy chcesz ograniczyć środowisko uruchomieniowe współbieżności do podzbioru bieżącej grupy procesorów. Ogólnie rzecz biorąc należy użyć wersji metody, która akceptuje tablicę koligacji grup jako parametr, aby ograniczyć koligację na maszynach z ponad 64 wątkami sprzętowymi.

*count*<br/>
Liczba wpisów `GROUP_AFFINITY` w tablicy określonej przez `_PGroupAffinity`parametru.

*_PGroupAffinity*<br/>
Tablica wpisów `GROUP_AFFINITY`.

### <a name="remarks"></a>Uwagi

Metoda zgłosi wyjątek [invalid_operation](invalid-operation-class.md) , jeśli Menedżer zasobów jest obecny w momencie wywołania, a [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli określona koligacja spowoduje, że jest to pusty zestaw zasobów.

Wersja metody, która pobiera tablicę koligacji grup jako parametr, należy używać tylko w systemach operacyjnych w wersji Windows 7 lub nowszej. W przeciwnym razie zostanie zgłoszony wyjątek [invalid_operation](invalid-operation-class.md) .

Programistyczne modyfikowanie koligacji procesu po wywołaniu tej metody nie spowoduje, że Menedżer zasobów ponownie oceni koligację, do której jest ograniczone. W związku z tym przed wywołaniem tej metody należy wykonać wszystkie zmiany koligacji procesu.

## <a name="swap"></a>wymiany

Wymienia elementy dwóch `concurrent_vector` obiektów.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ danych elementów przechowywanych w wektorach współbieżnych.

*_Ax*<br/>
Typ alokatora współbieżnych wektorów.

*_A*<br/>
Współbieżny wektor, którego elementy są wymieniane z elementami współbieżnych `_B`wektorów.

*_B*<br/>
Współbieżny wektor zapewniający elementy do zamiany lub wektor, którego elementy mają być wymieniane z elementami współbieżnych `_A`wektorów.

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytm wyspecjalizowany dla klasy kontenera `concurrent_vector` do wykonywania funkcji składowej `_A`. [concurrent_vector:: swap](concurrent-vector-class.md#swap)(`_B`). Są to wystąpienia częściowego uporządkowania szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, `template <class T> void swap(T&, T&)`w klasie algorytmu działa przez przypisanie i jest operacją powolne. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy Container.

Ta metoda nie jest bezpieczna pod kątem współbieżności. Należy upewnić się, że żadne inne wątki nie wykonują operacji na żadnym z współbieżnych wektorów podczas wywoływania tej metody.

## <a name="task_from_exception"></a>task_from_exception

```cpp
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parametry

*_TaskType*<br/>

*_ExType*<br/>

*_Exception*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Wartość zwrócona

## <a name="task_from_result"></a>task_from_result

```cpp
template<typename T>
task<T> task_from_result(
    T _Param,
    const task_options& _TaskOptions = task_options());

inline task<bool> task_from_result(ool _Param);

inline task<void> task_from_result(
    const task_options& _TaskOptions = task_options());
```

### <a name="parameters"></a>Parametry

*&*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Wartość zwrócona

## <a name="trace_agents_register_name"></a>Trace_agents_register_name

Kojarzy daną nazwę z blokiem komunikatów lub agentem w śledzeniu ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ obiektu. Zwykle jest to blok komunikatów lub Agent.

*_PObject*<br/>
Wskaźnik do bloku komunikatów lub agenta, który jest nazwany w śladzie.

*_Name*<br/>
Nazwa danego obiektu.

## <a name="try_receive"></a>try_receive

Ogólna implementacja try-Receive, umożliwiająca kontekstowi wyszukiwanie danych z dokładnie jednego źródła i filtrowanie wartości, które są akceptowane. Jeśli dane nie są gotowe, metoda zwróci **wartość false**.

```cpp
template <class T>
bool try_receive(_Inout_ ISource<T>* _Src, T& _value);

template <class T>
bool try_receive(
    _Inout_ ISource<T>* _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);

template <class T>
bool try_receive(ISource<T>& _Src, T& _value);

template <class T>
bool try_receive(
    ISource<T>& _Src,
    T& _value,
    typename ITarget<T>::filter_method const& _Filter_proc);
```

### <a name="parameters"></a>Parametry

*&*<br/>
Typ ładunku

*_Src*<br/>
Wskaźnik lub odwołanie do źródła, z którego są oczekiwane dane.

*_value*<br/>
Odwołanie do lokalizacji, w której zostanie umieszczony wynik.

*_Filter_proc*<br/>
Funkcja filtru określająca, czy komunikaty powinny być akceptowane.

### <a name="return-value"></a>Wartość zwrócona

Wartość `bool` wskazująca, czy ładunek został umieszczony w `_value`.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a>trwa

Wstrzymuje bieżący kontekst przez określony czas.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parametry

*_Milliseconds*<br/>
Liczba milisekund, dla których należy wstrzymać bieżący kontekst. Jeśli parametr `_Milliseconds` jest ustawiony na `0`wartość, bieżący kontekst powinien dać wykonanie do innych kontekstów możliwy do uruchomienia przed kontynuowaniem.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda jest wywoływana w kontekście harmonogramu środowisko uruchomieniowe współbieżności, w harmonogramie znajdą się różne konteksty do uruchomienia na bazowym zasobie. Ponieważ harmonogram ma charakter spółdzielni, ten kontekst nie może zostać wznowiony dokładnie po określonej liczbie milisekund. Jeśli harmonogram jest zajęty wykonywaniem innych zadań, które nie współpracowały wspólnie z harmonogramem, okres oczekiwania może być nieokreślony.

## <a name="when_all"></a>when_all

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.

```cpp
template <typename _Iterator>
auto when_all(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options()) ->
    decltype (details::_WhenAllImpl<typename std::iterator_traits<_Iterator>::value_type::result_type,
    _Iterator>::_Perform(_TaskOptions, _Begin,  _End));
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iteratora wejściowego.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, który ma zostać połączony z wynikiem zadania.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają być połączone w zadanie w wyniku.

*_TaskOptions*<br/>
Obiekt `task_options`.

### <a name="return-value"></a>Wartość zwrócona

Zadanie, które zakończyło się pomyślnie, gdy wszystkie zadania wejściowe zostały zakończone pomyślnie. Jeśli zadania wejściowe są typu `T`, dane wyjściowe tej funkcji będą `task<std::vector<T>>`. Jeśli zadania wejściowe są typu `void` zadanie wyjściowe będzie również `task<void>`.

### <a name="remarks"></a>Uwagi

`when_all` jest funkcją nieblokującą, która generuje `task` jako wynik. W przeciwieństwie do [zadania:: czekaj](task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy UWP w wątku ASTA (Application sta).

Jeśli jedno z zadań zostanie anulowane lub zgłosi wyjątek, zwrócone zadanie zakończy się wcześnie, w stanie anulowanym, a wyjątek, jeśli wystąpi, zostanie zgłoszony w przypadku wywołania [zadania:: Get](task-class.md#get) lub `task::wait` dla tego zadania.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a>when_any

Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.

```cpp
template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    const task_options& _TaskOptions = task_options())
    -> decltype (
        details::_WhenAnyImpl<
            typename std::iterator_traits<_Iterator>::value_type::result_type,
            _Iterator>::_Perform(_TaskOptions, _Begin, _End));

template<typename _Iterator>
auto when_any(
    _Iterator _Begin,
    _Iterator _End,
    cancellation_token _CancellationToken)
       -> decltype (
           details::_WhenAnyImpl<
               typename std::iterator_traits<_Iterator>::value_type::result_type,
               _Iterator>::_Perform(_CancellationToken._GetImplValue(), _Begin, _End));
```

### <a name="parameters"></a>Parametry

*_Iterator*<br/>
Typ iteratora wejściowego.

*_Begin*<br/>
Pozycja pierwszego elementu w zakresie elementów, który ma zostać połączony z wynikiem zadania.

*_End*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które mają być połączone w zadanie w wyniku.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token anulowania, który kontroluje anulowanie zwracanego zadania. Jeśli nie podasz tokenu anulowania, zadanie wyniki otrzyma token anulowania zadania, które powoduje jego zakończenie.

### <a name="return-value"></a>Wartość zwrócona

Zadanie, które zakończyło się pomyślnie po pomyślnym zakończeniu jednego z zadań wejściowych. Jeśli zadania wejściowe są typu `T`, dane wyjściowe tej funkcji będą `task<std::pair<T, size_t>>>`, gdzie pierwszy element pary jest wynikiem ukończenia zadania, a drugi element jest indeksem zadania, które zostało zakończone. Jeśli zadania wejściowe są typu `void` dane wyjściowe to `task<size_t>`, gdzie wynik jest indeksem ukończenia zadania.

### <a name="remarks"></a>Uwagi

`when_any` jest funkcją nieblokującą, która generuje `task` jako wynik. W przeciwieństwie do [zadania:: czekaj](task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy UWP w wątku ASTA (Application sta).

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
