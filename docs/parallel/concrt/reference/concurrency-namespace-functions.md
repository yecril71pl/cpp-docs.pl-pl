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
ms.openlocfilehash: 15b265744640628425502706d69fd98a1c64bda2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374371"
---
# <a name="concurrency-namespace-functions"></a>Funkcje przestrzeni nazw współbieżności

||||
|-|-|-|
|[Alloc](#alloc)|[Menedżer createresource](#createresourcemanager)|[Wyłączanieśledzenie](#disabletracing)|
|[Włącz śledzenie](#enabletracing)|[Bezpłatna](#free)|[GetExecutionContextId](#getexecutioncontextid)|
|[Wersja GetOSVersion](#getosversion)|[Licznik GetProcessor](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|
|[GetSchedulerId (NiechedulerId)](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[Asend](#asend)|
|[cancel_current_task](#cancel_current_task)|[Wyczyść](#clear)|[create_async](#create_async)|
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|
|[parallel_buffered_sort](#parallel_buffered_sort)|[Parallel_for](#parallel_for)|[Parallel_for_each](#parallel_for_each)|
|[Parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|
|[Parallel_sort](#parallel_sort)|[Parallel_transform](#parallel_transform)|[Otrzymywać](#receive)|
|[run_with_cancellation_token](#run_with_cancellation_token)|[Wyślij](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|
|[set_task_execution_resources](#set_task_execution_resources)|[Wymiany](#swap)|[task_from_exception](#task_from_exception)|
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Czekać](#wait)|
|[When_all](#when_all)|[When_any](#when_any)|

## <a name="alloc"></a><a name="alloc"></a>Alloc

Przydziela blok pamięci o rozmiarze określonym w podlokatorze buforowania współbieżności.

```cpp
void* __cdecl Alloc(size_t _NumBytes);
```

### <a name="parameters"></a>Parametry

*_NumBytes*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do nowo przydzielonej pamięci.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o scenariuszach w aplikacji może korzystać z korzystania z caching suballocator, zobacz [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="asend"></a><a name="asend"></a>Asend

Operacja wysyłania asynchronicznego, która planuje zadanie propagacji danych do bloku docelowego.

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

*T*<br/>
Typ danych, które mają być wysyłane.

*_Trg*<br/>
Wskaźnik lub odwołanie do obiektu docelowego, do którego wysyłane są dane.

*_Data*<br/>
Odwołanie do danych, które mają być wysyłane.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wiadomość została zaakceptowana przed użyciem metody, **false** inaczej.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Funkcje przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).

## <a name="cancel_current_task"></a><a name="cancel_current_task"></a>cancel_current_task

Anuluje aktualnie wykonywane zadanie. Ta funkcja może być wywoływana z poziomu treści zadania, aby przerwać wykonanie `canceled` zadania i spowodować jego wejście w stan.

Nie jest obsługiwany scenariusz do wywołania tej funkcji, jeśli `task`nie znajdują się w treści . Spowoduje to niezdefiniowane zachowanie, takie jak awaria lub zawieszenie w aplikacji.

```cpp
inline __declspec(noreturn) void __cdecl cancel_current_task();
```

## <a name="clear"></a><a name="clear"></a>Wyczyść

Czyści równoczesnych kolejki, niszcząc wszystkie aktualnie w kolejce elementów. Ta metoda nie jest bezpieczna dla współbieżności.

```cpp
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```

### <a name="parameters"></a>Parametry

*T*<br/>

*_Ax*<br/>

## <a name="create_async"></a><a name="create_async"></a>create_async

Tworzy asynchronikę środowiska wykonawczego systemu Windows na podstawie obiektu lambda lub funkcji dostarczonego przez użytkownika. Typ zwracany `create_async` jest jednym `IAsyncAction^`z `IAsyncActionWithProgress<TProgress>^` `IAsyncOperation<TResult>^`, `IAsyncOperationWithProgress<TResult, TProgress>^` , lub na podstawie podpisu lambda przekazane do metody.

```cpp
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typu.

*_func*<br/>
Lambda lub obiekt funkcji, z którego można utworzyć asynchronikę środowiska wykonawczego systemu Windows.

### <a name="return-value"></a>Wartość zwracana

Konstrukcja asynchroniczna reprezentowana przez IAsyncAction^, IAsyncActionWithProgress\<TProgress>^, IAsyncOperation\<TResult>^, lub IAsyncOperationWithProgress\<TResult, TProgress>^. Interfejs zwrócony zależy od podpisu lambda przekazywane do funkcji.

### <a name="remarks"></a>Uwagi

Zwracany typ lambda określa, czy konstrukcja jest operacją, czy operacją.

Lambdas, które zwracają pustkę spowodować tworzenie działań. Lambdas, które zwracają `TResult` wynik typu spowodować utworzenie operacji TResult.

Lambda może również `task<TResult>` zwrócić, który hermetyzuje pracy aysnchroniczne w sobie lub jest kontynuacją łańcucha zadań, które reprezentują pracy asynchroniczne. W takim przypadku lambda sama jest wykonywana w linii, ponieważ zadania są te, które wykonują asynchronicznie, a typ zwracany lambda jest `create_async`rozpakowany do produkcji konstrukcji asynchronicznie zwrócone przez . Oznacza to, że lambda,\<który zwraca zadanie void> spowoduje utworzenie akcji i lambda, który zwraca zadanie\<TResult> spowoduje utworzenie operacji TResult.

Lambda może mieć zero, jeden lub dwa argumenty. Prawidłowe argumenty `progress_reporter<TProgress>` `cancellation_token`są i , w tej kolejności, jeśli oba są używane. Lambda bez argumentów powoduje utworzenie konstrukcji asynchronii bez możliwości raportowania postępu. Lambda, która ma progress_reporter\<TProgress> spowoduje `create_async` zwrócenie konstrukcji asynchroniczne, która raportuje postęp typu TProgress za każdym `report` razem, gdy wywoływana jest metoda obiektu progress_reporter. Lambda, który ma cancellation_token może używać tego tokenu, aby sprawdzić, czy anulowanie lub przekazać go do zadań, które tworzy tak, że anulowanie konstrukcji asynchroniczne powoduje anulowanie tych zadań.

Jeśli treść lambda lub obiekt funkcji zwraca wynik (a nie zadanie\<TResult>), lamdba będą wykonywane asynchronicznie w ramach mta procesu w kontekście zadania Runtime niejawnie tworzy dla niego. Metoda `IAsyncInfo::Cancel` spowoduje anulowanie zadania niejawnego.

Jeśli treść lambda zwraca zadanie, lamba wykonuje w linii wbudowanej i deklarując lambda `cancellation_token` do podjęcia argument typu można wyzwolić anulowanie wszelkich zadań utworzonych w lambda, przekazując ten token podczas ich tworzenia. Można również użyć `register_callback` metody na tokenie, aby spowodować Runtime wywołać `IAsyncInfo::Cancel` wywołanie zwrotne, gdy wywołasz operację asynchronii lub wyprodukowanej akcji..

Ta funkcja jest dostępna tylko dla aplikacji środowiska wykonawczego systemu Windows.

## <a name="createresourcemanager"></a><a name="createresourcemanager"></a>Menedżer createresource

Zwraca interfejs reprezentujący pojedyncze wystąpienie Menedżera zasobów środowiska wykonawczego współbieżności. Menedżer zasobów jest odpowiedzialny za przypisywanie zasobów do harmonogramów, które chcą ze sobą współpracować.

```cpp
IResourceManager* __cdecl CreateResourceManager();
```

### <a name="return-value"></a>Wartość zwracana

Interfejs. `IResourceManager`

### <a name="remarks"></a>Uwagi

Wiele kolejnych wywołań tej metody zwróci to samo wystąpienie Menedżera zasobów. Każde wywołanie metody zwiększa liczbę odwołań w Menedżerze zasobów i musi być dopasowane do wywołania [metody IResourceManager::Release,](iresourcemanager-structure.md) gdy harmonogram jest wykonywany w komunikacji z Menedżerem zasobów.

[unsupported_os](unsupported-os-class.md) jest zgłaszany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="create_task"></a><a name="create_task"></a>create_task

Tworzy obiekt [zadania](task-class.md) PPL. `create_task`może być używany w dowolnym miejscu, w dowolnym miejscu użyto konstruktora zadań. Jest on dostarczany głównie dla wygody, `auto` ponieważ umożliwia użycie słowa kluczowego podczas tworzenia zadań.

```cpp
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru, z którego ma zostać skonstruowane zadanie.

*_ReturnType*<br/>
Typu.

*_Param*<br/>
Parametr, z którego ma zostać skonstruowane zadanie. Może to być lambda lub `task_completion_event` obiekt funkcji, `task` obiekt, inny obiekt lub windows::Foundation::IAsyncInfo interfejsu, jeśli używasz zadań w aplikacji platformy uniwersalnej systemu Windows.

*_TaskOptions*<br/>
Opcje zadania.

*_Task*<br/>
Zadanie do utworzenia.

### <a name="return-value"></a>Wartość zwracana

Nowe zadanie typu `T`, które jest `_Param`wywnioskowane z .

### <a name="remarks"></a>Uwagi

Pierwsze przeciążenie zachowuje się jak konstruktor zadań, który przyjmuje pojedynczy parametr.

Drugi przeciążenie kojarzy token anulowania dostarczone z nowo utworzonym zadaniem. Jeśli używasz tego przeciążenia nie mogą przekazać `task` w innym obiekcie jako pierwszy parametr.

Typ zwróconego zadania jest wywnioskowany z pierwszego parametru do funkcji. Jeśli `_Param` jest `task_completion_event<T>`to `task<T>`, a lub functor, `T` `task<T>`który zwraca typ lub `task<T>`typ utworzonego zadania jest .

W aplikacji platformy uniwersalnej systemu `_Param` Windows, jeśli jest typu Windows::Foundation::IAsyncOperation\<T>^ lub Windows::Foundation::IAsyncOperationWithProgress\<T,P>^, lub functor, `task<T>`który zwraca którykolwiek z tych typów, utworzone zadanie będzie typu . Jeśli `_Param` jest typu Windows::Foundation::IAsyncAction^ lub Windows::Foundation::IAsyncActionWithProgress\<P>^, lub functor, który zwraca którykolwiek `task<void>`z tych typów, utworzone zadanie będzie miało typ .

## <a name="disabletracing"></a><a name="disabletracing"></a>Wyłączanieśledzenie

Wyłącza śledzenie w czasie wykonywania współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest domyślnie wyrejestrowane.

```cpp
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli śledzenie zostało poprawnie `S_OK` wyłączone, jest zwracany. Jeśli śledzenie nie zostało wcześniej `E_NOT_STARTED` zainicjowane, jest zwracane

## <a name="enabletracing"></a><a name="enabletracing"></a>Włącz śledzenie

Umożliwia śledzenie w czasie wykonywania współbieżności. Ta funkcja jest przestarzała, ponieważ śledzenie ETW jest teraz domyślnie włączone.

```cpp
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli śledzenie zostało poprawnie `S_OK` zainicjowane, jest zwracany; w `E_NOT_STARTED` przeciwnym razie jest zwracany.

## <a name="free"></a><a name="free"></a>Wolna

Zwalnia blok pamięci wcześniej przydzielone `Alloc` przez metodę do współdziałania buforowania suballocatora.

```cpp
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```

### <a name="parameters"></a>Parametry

*_PAllocation*<br/>
Wskaźnik do pamięci wcześniej przydzielone przez metodę, `Alloc` która ma zostać zwolniona. Jeśli parametr `_PAllocation` jest ustawiony `NULL`na wartość, ta metoda zignoruje go i natychmiast zwróci.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji o scenariuszach w aplikacji może korzystać z korzystania z caching suballocator, zobacz [Harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).

## <a name="get_ambient_scheduler"></a><a name="get_ambient_scheduler"></a>get_ambient_scheduler

```cpp
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```

### <a name="return-value"></a>Wartość zwracana

## <a name="getexecutioncontextid"></a><a name="getexecutioncontextid"></a>GetExecutionContextId

Zwraca unikatowy identyfikator, który można przypisać do kontekstu `IExecutionContext` wykonywania, który implementuje interfejs.

```cpp
unsigned int __cdecl GetExecutionContextId();
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator kontekstu wykonywania.

### <a name="remarks"></a>Uwagi

Ta metoda służy do uzyskania identyfikatora kontekstu `IExecutionContext` wykonywania przed przekazaniem interfejsu jako parametr do dowolnej z metod oferowanych przez Menedżera zasobów.

## <a name="getosversion"></a><a name="getosversion"></a>Wersja GetOSVersion

Zwraca wersję systemu operacyjnego.

```cpp
IResourceManager::OSVersion __cdecl GetOSVersion();
```

### <a name="return-value"></a>Wartość zwracana

Wyliczona wartość reprezentująca system operacyjny.

### <a name="remarks"></a>Uwagi

[unsupported_os](unsupported-os-class.md) jest zgłaszany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="getprocessorcount"></a><a name="getprocessorcount"></a>Licznik GetProcessor

Zwraca liczbę wątków sprzętowych w systemie źródłowym.

```cpp
unsigned int __cdecl GetProcessorCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba wątków sprzętowych.

### <a name="remarks"></a>Uwagi

[unsupported_os](unsupported-os-class.md) jest zgłaszany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="getprocessornodecount"></a><a name="getprocessornodecount"></a>GetProcessorNodeCount

Zwraca liczbę węzłów NUMA lub pakietów procesorów w systemie bazowym.

```cpp
unsigned int __cdecl GetProcessorNodeCount();
```

### <a name="return-value"></a>Wartość zwracana

Liczba węzłów NUMA lub pakietów procesorów.

### <a name="remarks"></a>Uwagi

Jeśli system zawiera więcej węzłów NUMA niż pakietów procesora, zwracana jest liczba węzłów NUMA, w przeciwnym razie zwracana jest liczba pakietów procesora.

[unsupported_os](unsupported-os-class.md) jest zgłaszany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.

## <a name="getschedulerid"></a><a name="getschedulerid"></a>GetSchedulerId (NiechedulerId)

Zwraca unikatowy identyfikator, który można przypisać do harmonogramu, który implementuje `IScheduler` interfejs.

```cpp
unsigned int __cdecl GetSchedulerId();
```

### <a name="return-value"></a>Wartość zwracana

Unikatowy identyfikator harmonogramu.

### <a name="remarks"></a>Uwagi

Ta metoda służy do uzyskania identyfikatora harmonogramu `IScheduler` przed przekazaniem interfejsu jako parametru do dowolnej z metod oferowanych przez Menedżera zasobów.

## <a name="internal_assign_iterators"></a><a name="internal_assign_iterators"></a>internal_assign_iterators

```cpp
template<typename T, class _Ax>
template<class _I>
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```

### <a name="parameters"></a>Parametry

*T*<br/>

*_Ax*<br/>

*_I*<br/>

*Pierwszym*<br/>

*Ostatnio*<br/>

## <a name="interruption_point"></a><a name="interruption_point"></a>interruption_point

Tworzy punkt przerwania do anulowania. Jeśli anulowanie jest w toku w kontekście, w którym ta funkcja jest wywoływana, spowoduje to zgłosić wyjątek wewnętrzny, który przerywa wykonywanie obecnie wykonywanej pracy równoległej. Jeśli anulowanie nie jest w toku, funkcja nie robi nic.

```cpp
inline void interruption_point();
```

### <a name="remarks"></a>Uwagi

Nie należy przechwytyć wyjątek `interruption_point()` anulowania wewnętrznego generowane przez funkcję. Wyjątek zostanie przechwycony i obsłużone przez środowisko wykonawcze i połowu może spowodować, że program zachowywać się nieprawidłowo.

## <a name="is_current_task_group_canceling"></a><a name="is_current_task_group_canceling"></a>is_current_task_group_canceling

Zwraca wskazanie, czy grupa zadań, która jest obecnie wykonywana w linii w bieżącym kontekście, znajduje się w środku aktywnego anulowania (lub będzie wkrótce). Należy zauważyć, że jeśli nie ma żadnej grupy zadań `false` obecnie wykonywanych w linii wbudowanej w bieżącym kontekście, zostaną zwrócone.

```cpp
bool __cdecl is_current_task_group_canceling();
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli grupa zadań, która jest obecnie wykonywana jest anulowanie, **false** inaczej.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Anulowanie](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).

## <a name="make_choice"></a><a name="make_choice"></a>make_choice

Tworzy blok `choice` obsługi wiadomości `Scheduler` z `ScheduleGroup` opcjonalnych lub i dwóch lub więcej źródeł wejściowych.

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

*T1*<br/>
Typ bloku wiadomości pierwszego źródła.

*T2*<br/>
Typ bloku wiadomości drugiego źródła.

*_PScheduler*<br/>
Obiekt, `Scheduler` w którym zaplanowane jest `choice` zadanie propagacji dla bloku obsługi wiadomości.

*_Item1*<br/>
Pierwsze źródło.

*_Item2*<br/>
Drugie źródło.

*_Items*<br/>
Dodatkowe źródła.

*_PScheduleGroup*<br/>
Obiekt, `ScheduleGroup` w którym zaplanowane jest `choice` zadanie propagacji dla bloku obsługi wiadomości. Używany `Scheduler` obiekt jest implikowany przez grupę harmonogramu.

### <a name="return-value"></a>Wartość zwracana

Blok `choice` komunikatów z co najmniej dwoma źródłami wejściowymi.

## <a name="make_greedy_join"></a><a name="make_greedy_join"></a>make_greedy_join

Tworzy blok `greedy multitype_join` obsługi wiadomości `Scheduler` z `ScheduleGroup` opcjonalnych lub i dwóch lub więcej źródeł wejściowych.

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

*T1*<br/>
Typ bloku wiadomości pierwszego źródła.

*T2*<br/>
Typ bloku wiadomości drugiego źródła.

*_PScheduler*<br/>
Obiekt, `Scheduler` w którym zaplanowane jest `multitype_join` zadanie propagacji dla bloku obsługi wiadomości.

*_Item1*<br/>
Pierwsze źródło.

*_Item2*<br/>
Drugie źródło.

*_Items*<br/>
Dodatkowe źródła.

*_PScheduleGroup*<br/>
Obiekt, `ScheduleGroup` w którym zaplanowane jest `multitype_join` zadanie propagacji dla bloku obsługi wiadomości. Używany `Scheduler` obiekt jest implikowany przez grupę harmonogramu.

### <a name="return-value"></a>Wartość zwracana

Blok `greedy multitype_join` komunikatów z co najmniej dwoma źródłami wejściowymi.

## <a name="make_join"></a><a name="make_join"></a>make_join

Tworzy blok `non_greedy multitype_join` obsługi wiadomości `Scheduler` z `ScheduleGroup` opcjonalnych lub i dwóch lub więcej źródeł wejściowych.

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

*T1*<br/>
Typ bloku wiadomości pierwszego źródła.

*T2*<br/>
Typ bloku wiadomości drugiego źródła.

*_PScheduler*<br/>
Obiekt, `Scheduler` w którym zaplanowane jest `multitype_join` zadanie propagacji dla bloku obsługi wiadomości.

*_Item1*<br/>
Pierwsze źródło.

*_Item2*<br/>
Drugie źródło.

*_Items*<br/>
Dodatkowe źródła.

*_PScheduleGroup*<br/>
Obiekt, `ScheduleGroup` w którym zaplanowane jest `multitype_join` zadanie propagacji dla bloku obsługi wiadomości. Używany `Scheduler` obiekt jest implikowany przez grupę harmonogramu.

### <a name="return-value"></a>Wartość zwracana

Blok `non_greedy multitype_join` komunikatów z co najmniej dwoma źródłami wejściowymi.

## <a name="make_task"></a><a name="make_task"></a>make_task

Metoda fabryczna do `task_handle` tworzenia obiektu.

```cpp
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany w celu wykonania `task_handle` pracy reprezentowanej przez obiekt.

*_func*<br/>
Funkcja, która zostanie wywołana w celu wykonania `task_handle` pracy reprezentowane przez obiekt. Może to być functor lambda, wskaźnik do funkcji lub dowolny obiekt, który obsługuje `void operator()()`wersję operatora wywołania funkcji z podpisem .

### <a name="return-value"></a>Wartość zwracana

Obiekt `task_handle`.

### <a name="remarks"></a>Uwagi

Ta funkcja jest przydatna, gdy `task_handle` trzeba utworzyć obiekt z wyrażeniem lambda, ponieważ pozwala na utworzenie obiektu bez znajomości prawdziwego typu functor lambda.

## <a name="parallel_buffered_sort"></a><a name="parallel_buffered_sort"></a>parallel_buffered_sort

Rozmieszcza elementy w określonym zakresie w kolejności nie malejącej lub zgodnie z kryterium zamawiania określonym przez predykat binarny, równolegle. Ta funkcja jest semantycznie podobna do `std::sort` tego, że jest to sortowanie `O(n)` oparte na porównaniu, niestabilne, w miejscu, z tą różnicą, że wymaga dodatkowego miejsca i wymaga domyślnego inicjowania dla sortowanych elementów.

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
Typ alokatora pamięci zgodnej z biblioteką standardową języka C++.

*_Function*<br/>
Typ komparatora binarnego.

*_Begin*<br/>
Iterator dostępu losowego adresowania położenie pierwszego elementu w zakresie do sortowania.

*_end*<br/>
Iterator dostępu losowego adresowania pozycji jeden przeszłości końcowy element w zakresie do sortowania.

*_Alloc*<br/>
Wystąpienie alokatora pamięci zgodnego z biblioteką standardową języka C++.

*_func*<br/>
Obiekt funkcji predykatu zdefiniowanej przez użytkownika, który definiuje kryterium porównania, które ma być spełnione przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true,** gdy spełnione i **false,** gdy nie są spełnione. Ta funkcja komparatora musi nałożyć ścisłe słabe kolejność na pary elementów z sekwencji.

*_Chunk_size*<br/>
Rozmiar mimimum fragmentu, który zostanie podzielony na dwa dla wykonywania równoległego.

### <a name="remarks"></a>Uwagi

Wszystkie przeciążenia `n * sizeof(T)` wymagają dodatkowego miejsca, gdzie `n` jest liczba `T` elementów do sortowania i jest typem elementu. W większości przypadków parallel_buffered_sort będzie wykazywać poprawę wydajności w stosunku [do parallel_sort](concurrency-namespace-functions.md)i należy go używać przez parallel_sort jeśli masz dostępną pamięć.

Jeśli nie podasz komparatora `std::less` binarnego jest używany jako wartość `operator<()`domyślna, która wymaga typu elementu, aby zapewnić operator .

Jeśli nie podasz typu alokatora lub wystąpienia, alokator `std::allocator<T>` pamięci biblioteki standardowej języka C++ jest używany do przydzielenia buforu.

Algorytm dzieli zakres danych wejściowych na dwa fragmenty i sukcesywnie dzieli każdy fragment na dwa podwamionki do wykonania równolegle. Opcjonalny `_Chunk_size` argument może służyć do wskazania algorytmu, że powinien obsługiwać fragmenty rozmiaru < `_Chunk_size` szeregowo.

## <a name="parallel_for"></a><a name="parallel_for"></a>Parallel_for

`parallel_for`iteruje w zakresie indeksów i wykonuje funkcję dostarczoną przez użytkownika przy każdej iteracji, równolegle.

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
Typ funkcji, która będzie wykonywana przy każdej iteracji.

*_Partitioner*<br/>
Typ partycjonowania, który jest używany do partycjonowania podanego zakresu.

*Pierwszym*<br/>
Pierwszy indeks, który ma zostać uwzględniony w iteracji.

*Ostatnio*<br/>
Indeks jeden przeszłości ostatni indeks, który ma zostać uwzględniony w iteracji.

*_Step*<br/>
Wartość, o którą należy przejść, `first` `last`gdy iteracja od do . Krok musi być pozytywny. [invalid_argument](../../../standard-library/invalid-argument-class.md) jest wyrzucany, jeśli krok jest mniejszy niż 1.

*_func*<br/>
Funkcja, która ma być wykonywana przy każdej iteracji. Może to być wyrażenie lambda, wskaźnik funkcji lub dowolny obiekt, który obsługuje `void operator()(_Index_type)`wersję operatora wywołania funkcji z podpisem .

*_Part*<br/>
Odwołanie do obiektu partycjonowania. Argument może być `const`jednym z [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&` `const` [, simple_partitioner](simple-partitioner-class.md) `&` lub [affinity_partitioner](affinity-partitioner-class.md) `&` Jeśli używany jest [obiekt affinity_partitioner,](affinity-partitioner-class.md) odwołanie musi być odwołaniem nie-const l-value, aby algorytm mógł przechowywać stan dla przyszłych pętli do ponownego użycia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_for_each"></a><a name="parallel_for_each"></a>Parallel_for_each

`parallel_for_each`stosuje określoną funkcję do każdego elementu w zakresie, równolegle. Jest semantycznie `for_each` równoważne funkcji `std` w obszarze nazw, z tą różnicą, że iteracja nad elementami jest wykonywana równolegle, a kolejność iteracji jest nieokreślony. Argument `_Func` musi obsługiwać operatora wywołania `operator()(T)` funkcji `T` formularza, w którym parametr jest typem elementu kontenera, który jest iterowany.

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
Typ iteratora używanego do iteracji nad kontenerem.

*_Function*<br/>
Typ funkcji, która zostanie zastosowana do każdego elementu w zakresie.

*_Partitioner*<br/>
*Pierwszym*<br/>
Iterator adresowania pozycji pierwszego elementu, które mają być uwzględnione w iteracji równoległej.

*Ostatnio*<br/>
Iterator adresowania pozycji jeden przeszłości końcowy element, który ma zostać uwzględniony w iteracji równoległej.

*_func*<br/>
Obiekt funkcji zdefiniowany przez użytkownika, który jest stosowany do każdego elementu w zakresie.

*_Part*<br/>
Odwołanie do obiektu partycjonowania. Argument może być `const`jednym z [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&` `const` [, simple_partitioner](simple-partitioner-class.md) `&` lub [affinity_partitioner](affinity-partitioner-class.md) `&` Jeśli używany jest [obiekt affinity_partitioner,](affinity-partitioner-class.md) odwołanie musi być odwołaniem nie-const l-value, aby algorytm mógł przechowywać stan dla przyszłych pętli do ponownego użycia.

### <a name="remarks"></a>Uwagi

[auto_partitioner](auto-partitioner-class.md) będzie używany do przeciążenia bez jawnego partycjonowania.

W przypadku iteratorów, które nie obsługują dostępu losowego, obsługiwane są tylko [auto_partitioner.](auto-partitioner-class.md)

Aby uzyskać więcej informacji, zobacz [Algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_invoke"></a><a name="parallel_invoke"></a>Parallel_invoke

Wykonuje obiekty funkcji dostarczane jako parametry równolegle i blokuje, dopóki nie zakończy się wykonywanie. Każdy obiekt funkcji może być wyrażeniem lambda, wskaźnikiem do działania lub dowolnym `void operator()()`obiektem, który obsługuje operatora wywołania funkcji z podpisem .

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
Obiekt piątej funkcji, który ma być wykonywany równolegle.

*_Func6*<br/>
Szósty obiekt funkcji, który ma być wykonywany równolegle.

*_Func7*<br/>
Siódmy obiekt funkcji, który ma być wykonywany równolegle.

*_Func8*<br/>
Ósmy obiekt funkcji, który ma być wykonywany równolegle.

*_Func9*<br/>
Dziewiąty obiekt funkcji, który ma być wykonywany równolegle.

*_Func10*<br/>
Dziesiąty obiekt funkcji, który ma być wykonywany równolegle.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że jeden lub więcej obiektów funkcji dostarczonych jako parametry mogą wykonywać wbudowane w kontekście wywołującym.

Jeśli jeden lub więcej obiektów funkcji przekazanych jako parametry do tej funkcji zgłasza wyjątek, środowisko wykonawcze wybierze jeden `parallel_invoke`taki wyjątek jego wyboru i propaguje go z wywołania do .

Aby uzyskać więcej informacji, zobacz [Algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="parallel_radixsort"></a><a name="parallel_radixsort"></a>parallel_radixsort

Rozmieszcza elementy w określonym zakresie w kolejności nie malejącej przy użyciu algorytmu sortowania radix. Jest to funkcja sortowania stabilnego, która wymaga funkcji projekcji, która może wyświetlać elementy do sortowania w niepodpisane klucze całkowite. Domyślna inicjalizacja jest wymagana dla elementów sortowanych.

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
Typ alokatora pamięci zgodnej z biblioteką standardową języka C++.

*_Function*<br/>
Typ funkcji projekcji.

*_Begin*<br/>
Iterator dostępu losowego adresowania położenie pierwszego elementu w zakresie do sortowania.

*_end*<br/>
Iterator dostępu losowego adresowania pozycji jeden przeszłości końcowy element w zakresie do sortowania.

*_Alloc*<br/>
Wystąpienie alokatora pamięci zgodnego z biblioteką standardową języka C++.

*_Proj_func*<br/>
Obiekt funkcji rzutowania zdefiniowanej przez użytkownika, który konwertuje element na wartość integralną.

*_Chunk_size*<br/>
Rozmiar mimimum fragmentu, który zostanie podzielony na dwa dla wykonywania równoległego.

### <a name="remarks"></a>Uwagi

Wszystkie przeciążenia `n * sizeof(T)` wymagają dodatkowego miejsca, gdzie `n` jest liczba `T` elementów do sortowania i jest typem elementu. Dwuary projekcji functor `I _Proj_func(T)` z podpisem jest wymagane do zwrócenia `T` klucza, gdy `I` dany element, gdzie jest typem elementu i jest niepodpisany typ liczby całkowitej, jak.

Jeśli funkcja rzutowania nie zostanie podajoną, domyślna funkcja rzutowania, która po prostu zwraca element, jest używana dla typów całkowitych. Funkcja nie powiedzie się skompilować, jeśli element nie jest typem integralnym w przypadku braku funkcji rzutowania.

Jeśli nie podasz typu alokatora lub wystąpienia, alokator `std::allocator<T>` pamięci biblioteki standardowej języka C++ jest używany do przydzielenia buforu.

Algorytm dzieli zakres danych wejściowych na dwa fragmenty i sukcesywnie dzieli każdy fragment na dwa podwamionki do wykonania równolegle. Opcjonalny `_Chunk_size` argument może służyć do wskazania algorytmu, że powinien obsługiwać fragmenty rozmiaru < `_Chunk_size` szeregowo.

## <a name="parallel_reduce"></a><a name="parallel_reduce"></a>parallel_reduce

Oblicza sumę wszystkich elementów w określonym zakresie, obliczając kolejne sumy częściowe lub oblicza wynik kolejnych wyników częściowych, podobnie uzyskanych z użycia określonej operacji binarnej innej niż suma, równolegle. `parallel_reduce`jest semantycznie `std::accumulate`podobny do , z tą różnicą, że wymaga operacji binarnej, aby być asocjacyjny i wymaga wartości tożsamości zamiast wartości początkowej.

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
Typ symetrycznej funkcji redukcji. Musi to być typ `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`funkcji z podpisem , gdzie _Reduce_type jest taka sama jak typ tożsamości i typ wyniku redukcji. W przypadku trzeciego przeciążenia powinno to być `_Range_reduce_fun`zgodne z typem wyjściowym .

*_Reduce_type*<br/>
Typ, do którego dane zostaną zredukować, który może się różnić od typu elementu wejściowego. Zwracana wartość i wartość tożsamości będzie miał tego typu.

*_Range_reduce_fun*<br/>
Typ funkcji redukcji zakresu. Musi to być typ `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`funkcji z podpisem, _Reduce_type jest taki sam jak typ tożsamości i typ wyniku redukcji.

*_Begin*<br/>
Iterator wejściowy adresowania pierwszy element w zakresie, który ma zostać zmniejszona.

*_end*<br/>
Iterator wejściowy adresowania elementu, który jest jedną pozycję poza końcowy element w zakresie, który ma zostać zmniejszona.

*_Identity*<br/>
Wartość `_Identity` tożsamości jest tego samego typu jako typ wyniku `value_type` redukcji, a także iteratora dla pierwszego i drugiego przeciążenia. Dla trzeciego przeciążenia wartość tożsamości musi mieć ten sam typ jako typ wyniku `value_type` redukcji, ale może się różnić od iteratora. Musi mieć odpowiednią wartość, tak aby `_Range_fun`operator redukcji zakresu , po zastosowaniu `value_type` do zakresu pojedynczego elementu typu i wartości `value_type` tożsamości, zachowywał się jak rzut typu wartości od typu do typu tożsamości.

*_Sym_fun*<br/>
Funkcja symetryczna, która będzie używana w drugim z redukcji. Więcej informacji można znaleźć w uwagach.

*_Range_fun*<br/>
Funkcja, która będzie używana w pierwszej fazie redukcji. Więcej informacji można znaleźć w uwagach.

### <a name="return-value"></a>Wartość zwracana

Wynik redukcji.

### <a name="remarks"></a>Uwagi

Aby wykonać redukcję równoległą, funkcja dzieli zakres na fragmenty na podstawie liczby pracowników dostępnych dla harmonogramu bazowego. Redukcja odbywa się w dwóch fazach, pierwsza faza wykonuje redukcję w ramach każdego fragmentu, a druga faza wykonuje redukcję między częściowymi wynikami z każdego fragmentu.

Pierwsze przeciążenie wymaga, aby iterator `value_type`, `T`być taki sam jak typ wartości tożsamości, a także typ wyniku redukcji. Element typu T musi `T T::operator + (T)` zapewnić operator, aby zmniejszyć elementy w każdym fragmencie. Ten sam operator jest również używany w drugiej fazie.

Drugie przeciążenie wymaga również, aby `value_type` iteratora być takie same jak typ wartości tożsamości, a także typ wyniku redukcji. Dostarczony operator `_Sym_fun` binarny jest używany w obu fazach redukcji, z wartością tożsamości jako wartością początkową dla pierwszej fazy.

Dla trzeciego przeciążenia typ wartości tożsamości musi być taki sam jak typ wyniku `value_type` redukcji, ale iteratora może się różnić od obu. Funkcja `_Range_fun` redukcji zakresu jest używana w pierwszej fazie z wartością tożsamości `_Sym_reduce_fun` jako wartością początkową, a funkcja binarna jest stosowana do wyników podrzędnych w drugiej fazie.

## <a name="parallel_sort"></a><a name="parallel_sort"></a>Parallel_sort

Rozmieszcza elementy w określonym zakresie w kolejności nie malejącej lub zgodnie z kryterium zamawiania określonym przez predykat binarny, równolegle. Ta funkcja jest semantycznie podobna do `std::sort` tego, że jest to sortowanie oparte na porównaniu, niestabilne w miejscu.

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
Typ binarnego functor porównania.

*_Begin*<br/>
Iterator dostępu losowego adresowania położenie pierwszego elementu w zakresie do sortowania.

*_end*<br/>
Iterator dostępu losowego adresowania pozycji jeden przeszłości końcowy element w zakresie do sortowania.

*_func*<br/>
Obiekt funkcji predykatu zdefiniowanej przez użytkownika, który definiuje kryterium porównania, które ma być spełnione przez kolejne elementy w kolejności. Predykat binarny przyjmuje dwa argumenty i zwraca **wartość true,** gdy spełnione i **false,** gdy nie są spełnione. Ta funkcja komparatora musi nałożyć ścisłe słabe kolejność na pary elementów z sekwencji.

*_Chunk_size*<br/>
Minimalny rozmiar fragmentu, który zostanie podzielony na dwa dla wykonywania równoległego.

### <a name="remarks"></a>Uwagi

Pierwsze przeciążenie używa komparatora `std::less`binarnego .

Drugi przeciążony używa dostarczonego komparatora binarnego, który powinien mieć podpis, `bool _Func(T, T)` gdzie `T` jest typem elementów w zakresie wejściowym.

Algorytm dzieli zakres danych wejściowych na dwa fragmenty i sukcesywnie dzieli każdy fragment na dwa podwamionki do wykonania równolegle. Opcjonalny `_Chunk_size` argument może służyć do wskazania algorytmu, że powinien obsługiwać fragmenty rozmiaru < `_Chunk_size` szeregowo.

## <a name="parallel_transform"></a><a name="parallel_transform"></a>Parallel_transform

Stosuje określony obiekt funkcji do każdego elementu w zakresie źródłowym lub do pary elementów z dwóch zakresów źródłowych i kopiuje wartości zwracane obiektu funkcji do zakresu docelowego, równolegle. Ta funkcja jest semantycznie równoważna `std::transform`.

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
Typ pierwszego lub jedynego iteratora wejściowego.

*_Output_iterator*<br/>
Typ iteratora wyjściowego.

*_Unary_operator*<br/>
Typ kojca bezemisowego, który ma być wykonywany dla każdego elementu w zakresie wejściowym.

*_Input_iterator2*<br/>
Typ drugiego iteratora wejściowego.

*_Binary_operator*<br/>
Typ binarnego functor wykonywane parowo na elementy z dwóch zakresów źródłowych.

*_Partitioner*<br/>
*po pierwsze1*<br/>
Iterator wejściowy adresowania pozycji pierwszego elementu w pierwszym lub jedynym zakresie źródła, który ma być obsługiwany na.

*ostatni1*<br/>
Iterator wejściowy adresowania pozycji jeden przeszłości końcowy element w pierwszym lub jedynym zakresie źródła, które mają być obsługiwane na.

*_Result*<br/>
Iterator wyjściowy adresowania pozycji pierwszego elementu w zakresie docelowym.

*_Unary_op*<br/>
Zdefiniowany przez użytkownika obiekt funkcji dwuarysowej, który jest stosowany do każdego elementu w zakresie źródłowym.

*_Part*<br/>
Odwołanie do obiektu partycjonowania. Argument może być `const`jednym z [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&` `const` [, simple_partitioner](simple-partitioner-class.md) `&` lub [affinity_partitioner](affinity-partitioner-class.md) `&` Jeśli używany jest [obiekt affinity_partitioner,](affinity-partitioner-class.md) odwołanie musi być odwołaniem nie-const l-value, aby algorytm mógł przechowywać stan dla przyszłych pętli do ponownego użycia.

*pierwszy2*<br/>
Iterator wejściowy adresowania pozycji pierwszego elementu w drugim zakresie źródła, który ma być obsługiwany na.

*_binary_op*<br/>
Zdefiniowany przez użytkownika obiekt funkcji binarnej, który jest stosowany parowo, w kolejności do przodu, do dwóch zakresów źródłowych.

### <a name="return-value"></a>Wartość zwracana

Iterator wyjściowy adresowania pozycji jeden przeszłości końcowy element w zakresie docelowym, który odbiera elementy wyjściowe przekształcone przez obiekt funkcji.

### <a name="remarks"></a>Uwagi

[auto_partitioner](auto-partitioner-class.md) będzie używany dla przeciążeń bez jawnego argumentu partycjonowania.

W przypadku iteratorów, które nie obsługują dostępu losowego, obsługiwane są tylko [auto_partitioner.](auto-partitioner-class.md)

Przeciążenia, które przyjmują argument `_Unary_op` przekształcić zakres wejściowy do zakresu danych wyjściowych, stosując tryb końcowy do każdego elementu w zakresie wejściowym. `_Unary_op`musi obsługiwać operatora wywołania funkcji z podpisem, `operator()(T)` gdzie `T` jest typ wartości zakresu jest iterowany ponad.

Przeciążenia, które przyjmują argument `_Binary_op` przekształcenia dwóch zakresów wejściowych do zakresu danych wyjściowych, stosując binarny functor do jednego elementu z pierwszego zakresu wejściowego i jeden element z drugiego zakresu wejściowego. `_Binary_op`musi obsługiwać operatora wywołania `T` `U` funkcji z podpisem, `operator()(T, U)` gdzie są typy wartości dwóch iteratorów wejściowych.

Aby uzyskać więcej informacji, zobacz [Algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).

## <a name="receive"></a><a name="receive"></a>Otrzymywać

Implementacja odbierania ogólne, dzięki czemu kontekst czekać na dane z dokładnie jednego źródła i filtrować wartości, które są akceptowane.

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

*T*<br/>
Typ ładunku.

*_Src*<br/>
Wskaźnik lub odwołanie do źródła, z którego oczekuje się danych.

*_Timeout*<br/>
Maksymalny czas, dla którego metoda powinna dla danych, w milisekundach.

*_Filter_proc*<br/>
Funkcja filtrowania, która określa, czy wiadomości powinny być akceptowane.

### <a name="return-value"></a>Wartość zwracana

Wartość ze źródła, typu ładunku.

### <a name="remarks"></a>Uwagi

Jeśli parametr `_Timeout` ma wartość inną `COOPERATIVE_TIMEOUT_INFINITE`niż stała , wyjątek [operation_timed_out](operation-timed-out-class.md) jest zgłaszany, jeśli określona ilość czasu wygasa przed odebraniem wiadomości. Jeśli chcesz zero length timeout, należy użyć funkcji [try_receive,](concurrency-namespace-functions.md) w `receive` przeciwieństwie do wywoływania z limitem czasu `0` (zero), ponieważ jest bardziej wydajne i nie zgłasza wyjątków na limity czasu.

Aby uzyskać więcej informacji, zobacz [Funkcje przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).

## <a name="run_with_cancellation_token"></a><a name="run_with_cancellation_token"></a>run_with_cancellation_token

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

*_func*<br/>
Obiekt funkcji, który zostanie wykonany. Ten obiekt musi obsługiwać operatora wywołania funkcji z podpisem void (void).

*_Ct*<br/>
Token anulowania, który będzie kontrolować niejawne anulowanie obiektu funkcji. Użyj, `cancellation_token::none()` jeśli chcesz, aby funkcja była wykonywana bez możliwości niejawnego anulowania z nadrzędnej grupy zadań, która została anulowana.

### <a name="remarks"></a>Uwagi

Wszystkie punkty przerwania w obiekcie funkcji `cancellation_token` zostaną wyzwolone po anulowaniu. Jawny `_Ct` token wyizoluje to `_Func` od anulowania nadrzędnego, jeśli element nadrzędny ma inny token lub nie ma tokenu.

## <a name="send"></a><a name="send"></a>Wyślij

Operacja synchroniczowego wysyłania, która czeka, aż obiekt docelowy zaakceptuje lub odrzuci wiadomość.

```cpp
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ ładunku.

*_Trg*<br/>
Wskaźnik lub odwołanie do obiektu docelowego, do którego wysyłane są dane.

*_Data*<br/>
Odwołanie do danych, które mają być wysyłane.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wiadomość została zaakceptowana, **false** inaczej.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Funkcje przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).

## <a name="set_ambient_scheduler"></a><a name="set_ambient_scheduler"></a>set_ambient_scheduler

```cpp
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```

### <a name="parameters"></a>Parametry

*_Scheduler*<br/>
Harmonogram otoczenia do skonfigurowania.

## <a name="set_task_execution_resources"></a><a name="set_task_execution_resources"></a>set_task_execution_resources

Ogranicza zasoby wykonywania używane przez współbieżne wątki wewnętrznego procesu roboczego do określonego zestawu koligacji.

Wywoływanie tej metody jest prawidłowe tylko przed utworzeniem Menedżera zasobów lub między dwoma okresami istnienia Menedżera zasobów. Można go wywołać wiele razy, o ile Menedżer zasobów nie istnieje w momencie wywołania. Po ustawieniu limitu koligacji pozostaje w mocy do następnego `set_task_execution_resources` prawidłowego wywołania metody.

Maska koligacji pod warunkiem, że nie musi być podzbiorem maski koligacji procesu. Koligacja procesu zostanie zaktualizowana, jeśli to konieczne.

```cpp
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```

### <a name="parameters"></a>Parametry

*_ProcessAffinityMask*<br/>
Maska koligacji, do których mają być ograniczone wątki procesu roboczego współbieżności. Tej metody należy używać w systemie z większą niż 64 wątkami sprzętowymi tylko wtedy, gdy chcesz ograniczyć środowisko uruchomieniowe współbieżności do podzbioru bieżącej grupy procesorów. Ogólnie rzecz biorąc należy użyć wersji metody, która akceptuje tablicę koligacji grupy jako parametr, aby ograniczyć koligację na komputerach z większą niż 64 wątkami sprzętowymi.

*Liczba*<br/>
Liczba wpisów `GROUP_AFFINITY` w tablicy określonej `_PGroupAffinity`przez parametr .

*_PGroupAffinity*<br/>
Tablica `GROUP_AFFINITY` wpisów.

### <a name="remarks"></a>Uwagi

Metoda zda [wyjątek invalid_operation,](invalid-operation-class.md) jeśli Menedżer zasobów jest obecny w czasie, gdy jest wywoływany, a [wyjątek invalid_argument,](../../../standard-library/invalid-argument-class.md) jeśli określony koligacja powoduje pusty zestaw zasobów.

Wersja metody, która przyjmuje tablicę koligacji grup jako parametru, powinna być używana tylko w systemach operacyjnych z wersją systemu Windows 7 lub nowszego. W przeciwnym razie zostanie zgłoszony wyjątek [invalid_operation.](invalid-operation-class.md)

Programowo modyfikowanie koligacji procesu po wywołaniu tej metody nie spowoduje Menedżera zasobów do ponownej oceny koligacji jest ograniczona do. W związku z tym wszystkie zmiany koligacji procesu należy wnieść przed wywołaniem tej metody.

## <a name="swap"></a><a name="swap"></a>Wymiany

Wymienia elementy dwóch `concurrent_vector` obiektów.

```cpp
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych elementów przechowywanych w równoczesnych wektorach.

*_Ax*<br/>
Typ alokatora równoczesnych wektorów.

*_A*<br/>
Wektor równoczesnych, których elementy mają być wymieniane z elementami `_B`równoczesnego wektora .

*_B*<br/>
Wektor równoczesnych zapewniających elementy, które mają być zamienione, lub wektor, którego elementy mają być `_A`wymieniane z elementami równoczesnych wektorów .

### <a name="remarks"></a>Uwagi

Funkcja szablonu jest algorytmem wyspecjalizowanym w `concurrent_vector` klasie `_A`kontenera w celu wykonania funkcji elementu członkowskiego . [concurrent_vector::swap](concurrent-vector-class.md#swap)( ). `_B` Są to wystąpienia częściowej kolejności szablonów funkcji przez kompilator. Gdy funkcje szablonu są przeciążone w taki sposób, że dopasowanie szablonu z wywołaniem funkcji nie jest unikatowe, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólna wersja funkcji szablonu, `template <class T> void swap(T&, T&)`w klasie algorytmu działa według przypisania i jest powolną operacją. Wyspecjalizowana wersja w każdym kontenerze jest znacznie szybsza, ponieważ może pracować z wewnętrzną reprezentacją klasy kontenera.

Ta metoda nie jest bezpieczna dla współbieżności. Należy upewnić się, że żadne inne wątki wykonują operacje na jednym z równoczesnych wektorów podczas wywoływania tej metody.

## <a name="task_from_exception"></a><a name="task_from_exception"></a>task_from_exception

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

### <a name="return-value"></a>Wartość zwracana

## <a name="task_from_result"></a><a name="task_from_result"></a>task_from_result

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

*T*<br/>

*_Param*<br/>

*_TaskOptions*<br/>

### <a name="return-value"></a>Wartość zwracana

## <a name="trace_agents_register_name"></a><a name="trace_agents_register_name"></a>Trace_agents_register_name

Kojarzy nadają nazwę z blokiem wiadomości lub agentem w śledzenia ETW.

```cpp
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu. Zazwyczaj jest to blok wiadomości lub agent.

*_PObject*<br/>
Wskaźnik do bloku wiadomości lub agenta, który jest nazwany w śledzenia.

*_Name*<br/>
Nazwa danego obiektu.

## <a name="try_receive"></a><a name="try_receive"></a>try_receive

Ogólna implementacja try-receive, umożliwiająca kontekstowi wyszukiwanie danych z dokładnie jednego źródła i filtrowanie wartości, które są akceptowane. Jeśli dane nie są gotowe, metoda zwróci **false**.

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

*T*<br/>
Typ ładunku

*_Src*<br/>
Wskaźnik lub odwołanie do źródła, z którego oczekuje się danych.

*_value*<br/>
Odwołanie do lokalizacji, w której zostanie umieszczony wynik.

*_Filter_proc*<br/>
Funkcja filtrowania, która określa, czy wiadomości powinny być akceptowane.

### <a name="return-value"></a>Wartość zwracana

Wartość `bool` wskazująca, czy ładunek został `_value`umieszczony w .

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Funkcje przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).

## <a name="wait"></a><a name="wait"></a>Czekać

Wstrzymuje bieżący kontekst przez określony czas.

```cpp
void __cdecl wait(unsigned int _Milliseconds);
```

### <a name="parameters"></a>Parametry

*_Milliseconds*<br/>
Liczba milisekund bieżącego kontekstu powinna zostać wstrzymana. Jeśli `_Milliseconds` parametr jest ustawiony `0`na wartość, bieżący kontekst powinien dać wykonanie do innych kontekstów runnable przed kontynuowaniem.

### <a name="remarks"></a>Uwagi

Jeśli ta metoda jest wywoływana w kontekście harmonogramu współbieżności, harmonogram znajdzie inny kontekst do uruchomienia na zasób podstawowy. Ponieważ harmonogram jest współpracy w naturze, ten kontekst nie można wznowić dokładnie po liczbie milisekund określony. Jeśli harmonogram jest zajęty wykonywaniem innych zadań, które nie przynoszą wspólnie harmonogramu, okres oczekiwania może być nieokreślony.

## <a name="when_all"></a><a name="when_all"></a>When_all

Tworzy zadanie, które zostanie pomyślnie ukończone, gdy wszystkie zadania dostarczone jako argumenty zostaną pomyślnie ukończone.

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
Położenie pierwszego elementu w zakresie elementów, które mają być połączone w wynikowe zadanie.

*_end*<br/>
Położenie pierwszego elementu poza zakresem elementów, które mają być połączone w wynikowe zadanie.

*_TaskOptions*<br/>
Obiekt `task_options`.

### <a name="return-value"></a>Wartość zwracana

Zadanie, które kończy się pomyślnie po pomyślnym zakończeniu wszystkich zadań wejściowych. Jeśli zadania wejściowe `T`są typu, dane wyjściowe `task<std::vector<T>>`tej funkcji będzie . Jeśli zadania wejściowe `void` są typu, zadaniem `task<void>`wyjściowym będzie również .

### <a name="remarks"></a>Uwagi

`when_all`jest funkcją nieblokujną, która daje `task` jako jej wynik. W przeciwieństwie do [zadania::wait](task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy uniwersalnej systemu uniwersalnego w wątku ASTA (Application STA).

Jeśli jedno z zadań zostanie anulowane lub zgłosić wyjątek, zwrócone zadanie zakończy się wcześniej, w stanie anulowanym, a wyjątek, jeśli wystąpi, zostanie zgłoszony, jeśli wywołasz [task::get](task-class.md#get) lub `task::wait` w tym zadaniu.

Aby uzyskać więcej informacji, zobacz [Równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="when_any"></a><a name="when_any"></a>When_any

Tworzy zadanie, które zostanie pomyślnie ukończone, gdy którekolwiek z zadań dostarczonych jako argumenty zakończy się pomyślnie.

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
Położenie pierwszego elementu w zakresie elementów, które mają być połączone w wynikowe zadanie.

*_end*<br/>
Położenie pierwszego elementu poza zakresem elementów, które mają być połączone w wynikowe zadanie.

*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token anulowania, który kontroluje anulowanie zwróconego zadania. Jeśli nie podasz tokenu anulowania, wynikowe zadanie otrzyma token anulowania zadania, które powoduje jego ukończenie.

### <a name="return-value"></a>Wartość zwracana

Zadanie, które kończy się pomyślnie po pomyślnym zakończeniu jednego z zadań wejściowych. Jeśli zadania wejściowe `T`są typu, dane wyjściowe `task<std::pair<T, size_t>>>`tej funkcji będzie , gdzie pierwszy element pary jest wynikiem wykonania zadania, a drugi element jest indeksem zadania, które zakończyły. Jeśli zadania wejściowe `void` są typu `task<size_t>`dane wyjściowe jest , gdzie wynikiem jest indeks zadania ukończenia.

### <a name="remarks"></a>Uwagi

`when_any`jest funkcją nieblokujną, która daje `task` jako jej wynik. W przeciwieństwie do [zadania::wait](task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy uniwersalnej systemu uniwersalnego w wątku ASTA (Application STA).

Aby uzyskać więcej informacji, zobacz [Równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
