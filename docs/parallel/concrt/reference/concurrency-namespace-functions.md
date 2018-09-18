---
title: Funkcje przestrzeni nazw współbieżności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: 520a6dff-9324-4df2-990d-302e3050af6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e71804a2b9b9420e4e7839bf33054fb1ed0a7797
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021203"
---
# <a name="concurrency-namespace-functions"></a>Funkcje przestrzeni nazw współbieżności
||||  
|-|-|-|  
|[Alokacji](#alloc)|[CreateResourceManager](#createresourcemanager)|[Disabletracing —](#disabletracing)|  
|[Enabletracing —](#enabletracing)|[Bezpłatne](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
|[GetOSVersion](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|  
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend —](#asend)|  
|[cancel_current_task](#cancel_current_task)|[Usuń zaznaczenie](#clear)|[create_async](#create_async)|  
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|  
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice —](#make_choice)|  
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|  
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|  
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce](#parallel_reduce)|  
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[Odbieranie](#receive)|  
|[run_with_cancellation_token](#run_with_cancellation_token)|[Wyślij](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|  
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception](#task_from_exception)|  
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[Czekaj](#wait)|  
|[when_all](#when_all)|[when_any](#when_any)|  
  
##  <a name="alloc"></a>  Alokacji  
 Przydziela blok pamięci w procentach rozmiaru określonego z Suballocator buforowania w czasie wykonywania współbieżności.  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>Parametry  
*_NumBytes*<br/>
Liczba bajtów pamięci do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo przydzielonego pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o tym, które scenariusze w aplikacji mogą odnieść korzyści z używania Sublokatora wyłapywania, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="asend"></a>  asend —  
 Operacja asynchronicznego wysyłania, która planuje zadania propagowanie danych do bloku docelowego.  
  
```
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
Typ danych do wysłania.  
  
*_Trg*<br/>
Wskaźnik lub odwołanie do obiektu docelowego, do którego dane są wysyłane.  
  
*_Dane*<br/>
Odwołanie do danych do wysłania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został zaakceptowany, zanim metoda zwróciła, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="cancel_current_task"></a>  cancel_current_task —  
 Anuluje aktualnie przeprowadzane zadanie. Ta funkcja może zostać wywołana z treści zadania, aby przerwać jego wykonywanie i spowodować wprowadzenie `canceled` stanu.  
  
 Nie jest to obsługiwany scenariusz, aby wywołać tę funkcję, jeśli nie jesteś w treści `task`. To spowoduje nieokreślone zachowanie przykład awarię lub zawieszenie aplikacji.  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear"></a>  Usuń zaznaczenie  
 Czyści kolejka współbieżna, niszczenie dowolnego aktualnie elementów umieszczonych w kolejce. Ta metoda nie jest bezpieczna pod kątem współbieżności.  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>Parametry  
*T*<br/>

*_Ax*<br/>
  
##  <a name="create_async"></a>  create_async —  
 Tworzy konstrukcję asynchroniczną środowiska wykonawczego Windows na podstawie podanych przez użytkownika obiektu lambda lub funkcji. Zwracany typ `create_async` jest `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, lub `IAsyncOperationWithProgress<TResult, TProgress>^` zależnie od podpisu wyrażenia lambda przekazanego do metody.  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ.

*_Func*<br/>
Obiekt wyrażenia lambda lub funkcji służący do utworzenia konstrukcji asynchronicznej środowiska wykonawczego Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Konstrukt asynchroniczny, reprezentowany przez IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, lub IAsyncOperationWithProgress\<TResult, TProgress > ^. Zawracany interfejs zależy od podpisu wyrażenia lambda przekazanego do funkcji.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany typ wyrażenia lambda Określa, czy konstrukcja jest akcją lub operacją.  
  
 Wyrażenia lambda, które zwracają void, powodują tworzenie akcji. Wyrażenia lambda, które zwracają wynik o typie `TResult` powodują powstawanie operacji TResult.  
  
 Wyrażenie lambda może również zwracać `task<TResult>` który hermetyzuje pracę asynchroniczną w sobie lub jest kontynuacją łańcucha zadań reprezentującego pracę asynchroniczną. W tym przypadku lambda jest sam wykonywany w tekście, ponieważ zadania są tymi, które działają asynchronicznie, a zwracany typ lambda jest nieopakowanych, aby produkować asynchroniczne konstrukcje zwracane przez `create_async`. Oznacza to, że wyrażenie lambda, zwraca klasę task,\<void > spowoduje tworzenie działań i Wyrażenie lambda, która zwraca klasę task,\<TResult > spowoduje utworzenie operacji TResult.  
  
 Wyrażenie lambda może potrwać albo zero, jeden lub dwa argumenty. Prawidłowe argumenty to `progress_reporter<TProgress>` i `cancellation_token`, w tej kolejności, jeśli oba są używane. Lambda bez argumentów powoduje utworzenie asynchronicznego konstruktu bez możliwości raportowania postępu. Wyrażenie lambda, która pobiera progress_reporter\<TProgress > spowoduje, że `create_async` do zwrócenia asynchronicznego konstruktu, które raporty postęp typu TProgress, zawsze `report` wywoływana jest metoda obiektu progress_reporter. Wyrażenie lambda, która pobiera cancellation_token może stosować ten token do sprawdzania występowania unieważnienia lub przekazywania go do zadań, które tworzy tak, że anulowanie asynchronicznego konstruktu powoduje unieważnienie tych zadań.  
  
 Jeśli treść obiektu lambda lub funkcja zwraca wynik (a nie task\<TResult >), wielowątkowego przedziału lambda będzie wykonywany asynchronicznie w ramach procesu w kontekście zadania, środowisko uruchomieniowe niejawnie tworzy dla niego. `IAsyncInfo::Cancel` Metoda spowoduje anulowanie zadania niejawnego.  
  
 Jeśli treść obiektu lambda zwraca zadanie, lambda jest wykonywany wewnątrz, a deklarując lambda ma przyjmować argument typu `cancellation_token` można inicjować anulowanie wszystkich zadań tworzonych w ramach lambda przez przekazanie tego tokenu podczas ich tworzenia. Można także użyć `register_callback` metody w tokenie aby spowodować, że środowisko uruchomieniowe wykona wywołanie zwrotne, gdy wywołujesz `IAsyncInfo::Cancel` na asynchronicznej operacji lub utworzonym działaniu...  
  
 Ta funkcja jest dostępna tylko dla aplikacji środowiska wykonawczego Windows.  
  
##  <a name="createresourcemanager"></a>  Createresourcemanager —  
 Zwraca interfejs, który reprezentuje wystąpienie singleton Menedżera zasobów Runtime współbieżności. Menedżer zasobów jest odpowiedzialny za przydzielanie zasobów, do których chcesz współpracować ze sobą.  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IResourceManager` Interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Wiele kolejnych wywołań tej metody zwróci to samo wystąpienie Menedżera zasobów. Każde wywołanie metody zwiększa odwołanie zliczane w Menedżerze zasobów i musi być dopasowane z wywołaniem [IResourceManager::Release](iresourcemanager-structure.md) metoda po zakończeniu harmonogramu podczas komunikowania się z usługą Resource Manager.  
  
 [unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.  
  
##  <a name="create_task"></a>  create_task —  
 Tworzy PPL [zadań](task-class.md) obiektu. `create_task` może służyć wszędzie użyto konstruktora zadania. Jest ona udostępniana przede wszystkim dla wygody, ponieważ zezwala ona na korzystanie z `auto` — słowo kluczowe podczas tworzenia zadań.  
  
```
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
Typ.

*_Param*<br/>
Parametr, z którego ma zostać skonstruowane zadanie. Może to być obiekt wyrażenia lambda lub funkcji `task_completion_event` obiektu, inny `task` obiektu lub interfejs Windows::Foundation:: iasyncinfo, jeśli używasz zadań w aplikacji platformy uniwersalnej systemu Windows.  
  
*_TaskOptions*<br/>
Opcje zadania.

*_Task*<br/>
Zadanie tworzenia.

### <a name="return-value"></a>Wartość zwracana  
 Nowe zadanie typu `T`, która jest wnioskowany z `_Param`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze przeciążenie zachowuje się jak konstruktora zadania, który przyjmuje jeden parametr.  
  
 Drugie przeciążenie kojarzy token anulowania dostarczany z nowo utworzonym zadaniem. Jeśli używasz tego przeciążenia nie możesz przekazać innego `task` obiektu jako pierwszego parametru.  
  
 Typ zwracanego zadania jest wnioskowany z pierwszego parametru do funkcji. Jeśli `_Param` jest `task_completion_event<T>`, `task<T>`, lub funktor, który zwraca albo typ `T` lub `task<T>`, typem utworzonego zadania jest `task<T>`.  
  
 W aplikacji platformy uniwersalnej systemu Windows Jeśli `_Param` jest typu Windows::Foundation:: iasyncoperation\<T > ^ lub Windows::Foundation:: iasyncoperationwithprogress\<T, P > ^, lub funktorem, który zwraca jeden z tych typów, utworzone zadanie będzie mieć Typ `task<T>`. Jeśli `_Param` jest typu Windows::Foundation:: iasyncaction ^ lub Windows::Foundation:: iasyncactionwithprogress\<P > ^, lub funktorem, który zwraca jeden z tych typów, utworzone zadanie będzie mieć typ `task<void>`.  
  
##  <a name="disabletracing"></a>  Disabletracing —  
 Wyłącza śledzenie w środowisku uruchomieniowym współbieżności. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest niezarejestrowana domyślnie.  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wyłączenie śledzenia został poprawnie `S_OK` jest zwracana. Jeśli śledzenie nie zostały wcześniej zainicjowane, `E_NOT_STARTED` zwróceniem  
  
##  <a name="enabletracing"></a>  Enabletracing —  
 Umożliwia śledzenie w środowisku uruchomieniowym współbieżności. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest teraz domyślnie włączona.  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli Śledzenie zostało poprawnie zainicjowane, `S_OK` jest zwracana; w przeciwnym razie `E_NOT_STARTED` jest zwracana.  
  
##  <a name="free"></a>  Bezpłatne  
 Zwalnia blok pamięci uprzednio przydzielonej przez `Alloc` metodę Suballocator buforowania w czasie wykonywania współbieżności.  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>Parametry  
*_PAllocation*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez `Alloc` metodę, która ma zostać uwolniona. Jeśli parametr `_PAllocation` jest ustawiona na wartość `NULL`, ta metoda zignoruje go i natychmiast zwróci.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o tym, które scenariusze w aplikacji mogą odnieść korzyści z używania Sublokatora wyłapywania, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler —  
  
```
inline std::shared_ptr<::Concurrency::scheduler_interface> get_ambient_scheduler();
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="getexecutioncontextid"></a>  GetExecutionContextId  
 Zwraca unikatowy identyfikator, który można przypisać do kontekstu wykonywania, który implementuje `IExecutionContext` interfejsu.  
  
```
unsigned int __cdecl GetExecutionContextId();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Unikatowy identyfikator dla kontekstu wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Użyj tej metody, aby uzyskać identyfikator kontekstu wykonywania, zanim przekażesz `IExecutionContext` interfejsu jako parametr do dowolnej z metod oferowane przez Menedżera zasobów.  
  
##  <a name="getosversion"></a>  Getosversion —  
 Zwraca wersję systemu operacyjnego.  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wyliczana reprezentująca systemu operacyjnego.  
  
### <a name="remarks"></a>Uwagi  
 [unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.  
  
##  <a name="getprocessorcount"></a>  Getprocessorcount —  
 Zwraca liczbę wątków sprzętu w systemie podstawowym.  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wątków sprzętu.  
  
### <a name="remarks"></a>Uwagi  
 [unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.  
  
##  <a name="getprocessornodecount"></a>  Getprocessornodecount —  
 Zwraca liczbę węzłów NUMA lub opakowań procesora w systemie podstawowym.  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba węzłów NUMA lub opakowań procesora.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli system zawiera więcej węzłów NUMA niż pakiety procesora, zwracana jest liczba węzłów NUMA, w przeciwnym razie jest zwracana liczba pakietów procesora.  
  
 [unsupported_os](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez środowisko uruchomieniowe współbieżności.  
  
##  <a name="getschedulerid"></a>  Getschedulerid —  
 Zwraca unikatowy identyfikator, który można przypisać do harmonogramu, który implementuje `IScheduler` interfejsu.  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Unikatowy identyfikator dla harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do uzyskania identyfikatora dla harmonogramu, zanim przekażesz `IScheduler` interfejsu jako parametr do dowolnej z metod oferowane przez Menedżera zasobów.  
  
##  <a name="internal_assign_iterators"></a>  internal_assign_iterators —  
  
```
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

*pierwszy*<br/>

*ostatni*<br/>
  
##  <a name="interruption_point"></a>  interruption_point —  
 Tworzy punkt przerwania do anulowania. W przypadku anulowania w toku w kontekście, w których ta funkcja jest wywoływana, zgłosi wyjątek wewnętrzny, który przerywa wykonywanie aktualnie wykonywanej pracy równoległej. Jeśli anulowania nie jest w toku, funkcja nie działa.  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie należy przechwytywać anulowania wewnętrzny wyjątek zgłoszony przez `interruption_point()` funkcji. Wyjątek zostanie wychwycony i obsługiwane przez środowisko uruchomieniowe i przechwytywania go może spowodować, że program będzie działać nieprawidłowo.  
  
##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling —  
 Zwraca wskazanie, czy zadanie grupy, która jest aktualnie wykonywana i wbudowana w bieżącym kontekście jest w środku aktywnego anulowania (lub będzie wkrótce). Należy pamiętać, że jeśli żadna grupa zadań aktualnie wykonywana i wbudowana w bieżącym kontekście `false` zostaną zwrócone.  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli anuluje grupy zadań, która jest aktualnie wykonywana `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="make_choice"></a>  make_choice —  
 Konstruuje `choice` Blok obsługi wiadomości z opcjonalnego `Scheduler` lub `ScheduleGroup` i co najmniej dwóch źródeł danych wejściowych.  
  
```
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
Typ bloku komunikatu pierwszego źródła.  
  
*T2*<br/>
Typ bloku komunikatu drugiego źródła.  
  
*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `choice` zaplanowano Blok obsługi wiadomości.  
  
*_Item1*<br/>
Pierwsze źródło.  
  
*_Item2*<br/>
Drugie źródło.  
  
*_Elementy*<br/>
Dodatkowe zasoby.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `choice` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `choice` blok komunikatów przy użyciu dwóch lub więcej źródeł danych wejściowych.  
  
##  <a name="make_greedy_join"></a>  make_greedy_join —  
 Konstruuje `greedy multitype_join` Blok obsługi wiadomości z opcjonalnego `Scheduler` lub `ScheduleGroup` i co najmniej dwóch źródeł danych wejściowych.  
  
```
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
Typ bloku komunikatu pierwszego źródła.  
  
*T2*<br/>
Typ bloku komunikatu drugiego źródła.  
  
*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `multitype_join` zaplanowano Blok obsługi wiadomości.  
  
*_Item1*<br/>
Pierwsze źródło.  
  
*_Item2*<br/>
Drugie źródło.  
  
*_Elementy*<br/>
Dodatkowe zasoby.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `multitype_join` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `greedy multitype_join` blok komunikatów przy użyciu dwóch lub więcej źródeł danych wejściowych.  
  
##  <a name="make_join"></a>  make_join —  
 Konstruuje `non_greedy multitype_join` Blok obsługi wiadomości z opcjonalnego `Scheduler` lub `ScheduleGroup` i co najmniej dwóch źródeł danych wejściowych.  
  
```
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
Typ bloku komunikatu pierwszego źródła.  
  
*T2*<br/>
Typ bloku komunikatu drugiego źródła.  
  
*_PScheduler*<br/>
`Scheduler` Obiekt, w którym zadanie propagacji dla `multitype_join` zaplanowano Blok obsługi wiadomości.  
  
*_Item1*<br/>
Pierwsze źródło.  
  
*_Item2*<br/>
Drugie źródło.  
  
*_Elementy*<br/>
Dodatkowe zasoby.  
  
*_PScheduleGroup*<br/>
`ScheduleGroup` Obiekt, w którym zadanie propagacji dla `multitype_join` zaplanowano Blok obsługi wiadomości. `Scheduler` Obiekt używany jest implikowany przez grupę harmonogramów.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `non_greedy multitype_join` blok komunikatów przy użyciu dwóch lub więcej źródeł danych wejściowych.  
  
##  <a name="make_task"></a>  make_task —  
 Metoda fabryki, do tworzenia `task_handle` obiektu.  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ obiektu funkcji, który zostanie wywołany do wykonywania pracy, reprezentowane przez `task_handle` obiektu.  
  
*_Func*<br/>
Funkcja, która zostanie wywołany do wykonywania pracy, reprezentowane przez `task_handle` obiektu. Może to być funktorem lambda, wskaźnika do funkcji, lub dowolnego obiektu, która obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Element `task_handle` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja ta jest przydatna, gdy trzeba utworzyć `task_handle` obiektu za pomocą wyrażenia lambda, ponieważ pozwala na utworzenie obiektu, nie wiedząc o tym prawidłowego typu funkcję lambda.  
  
##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort —  
 Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat, jednocześnie. Ta funkcja jest semantycznie podobne do `std::sort` naciśnięcia sortowania na podstawie porównania, niestabilne, w miejscu, z tą różnicą, że potrzebuje `O(n)` dodatkowe miejsce i wymaga domyślna Inicjalizacja elementów posortowana.  
  
```
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
Typ iteratora danych wejściowych zakresu.  
  
*_Allocator*<br/>
Typ alokatora pamięci zgodne standardowej biblioteki języka C++.  
  
*_Function*<br/>
Typ porównania binarne.  
  
*_Rozpocznij*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie ma zostać posortowana.  
  
*_Zakończ*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszej po elemencie końcowym w zakresie ma zostać posortowana.  
  
*_Alloc*<br/>
Wystąpienie alokatora pamięci zgodne standardowej biblioteki języka C++.  
  
*_Func*<br/>
Obiekt funkcji predykatu zdefiniowanej przez użytkownika, który definiuje kryterium porównania, które muszą być spełnione przez kolejne elementy w kolejności. Predykat dwuelementowy przyjmuje dwa argumenty i zwraca `true` po spełnieniu oraz `false` Jeśli nie jest spełniony. Ta funkcja komparator musi powodować ścisłe słabe porządkowanie w pary elementów z sekwencji.  
  
*_Chunk_size*<br/>
Rozmiar minimalny fragment, zostanie ona podzielona na dwie dla przetwarzania równoległego.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie przeciążenia wymagają `n * sizeof(T)` dodatkowe miejsce, gdzie `n` jest to liczba elementów, które mają być sortowane i `T` jest typ elementu. W większości przypadków parallel_buffered_sort — pokaże poprawę wydajności za pośrednictwem [parallel_sort —](concurrency-namespace-functions.md), i użyj go za pośrednictwem parallel_sort — Jeśli masz dostępnej pamięci.  
  
 Jeśli nie podasz binarne komparator `std::less` jest używana jako domyślna, która wymaga typu elementu zapewnić operator `operator<()`.  
  
 Jeśli nie zostanie podany typ programu przydzielania lub wystąpienia, alokatora pamięci standardowej biblioteki języka C++ `std::allocator<T>` służy do przydzielania buforu.  
  
 Algorytm zakresu wejściowego jest podzielony na dwie części i kolejno każdego fragmentu są podzielone na dwie części podrzędnych do wykonania w sposób równoległy. Opcjonalny argument `_Chunk_size` może służyć do wskazywania algorytm powinien obsługi fragmenty o rozmiarze < `_Chunk_size` szeregowo.  
  
##  <a name="parallel_for"></a>  parallel_for  
 `parallel_for` wykonuje iterację na szeroką gamę indeksów i wykonuje funkcję dostarczone przez użytkownika w każdej iteracji równolegle.  
  
```
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
Typ indeksu używany dla iteracji.  
  
*_Function*<br/>
Typ funkcji, która zostanie wykonana w każdej iteracji.  
  
*_Partitioner*<br/>
Typ partycjonera, który jest używany do partycjonowania wprowadzony zakres.  
  
*pierwszy*<br/>
Pierwszy indeks, które mają zostać uwzględnione w iteracji.  
  
*ostatni*<br/>
Indeks jednej ostatnie ostatni indeks, które mają zostać uwzględnione w iteracji.  
  
*_Step*<br/>
Wartość w kroku podczas iteracji z `first` do `last`. Ten krok musi być dodatnia. [invalid_argument](../../../standard-library/invalid-argument-class.md) jest generowany, jeśli ten krok jest mniejszy niż 1.  
  
*_Func*<br/>
Funkcja, które mają być wykonane w każdej iteracji. Może to być wyrażenie lambda, wskaźnika funkcji lub dowolnego obiektu, która obsługuje wersję operator wywołania funkcji z podpisem `void operator()(_Index_type)`.  
  
*_Part —*<br/>
Odwołanie do obiektu partycjonera. Argument może być jednym z `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ partycjonera](simple-partitioner-class.md) `&` lub [affinity_partitioner](affinity-partitioner-class.md) `&` Jeśli [affinity_partitioner](affinity-partitioner-class.md) obiekt jest używany, odwołanie musi być wartością l niż stała odwołanie, tak aby algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_for_each"></a>  parallel_for_each  
 `parallel_for_each` stosuje określoną funkcję do każdego elementu w zakresie, w sposób równoległy. Jest to semantycznie równoważne `for_each` działa w programach `std` przestrzeni nazw, z wyjątkiem tej iteracji nad elementami jest wykonywane równolegle i kolejność iteracji jest nieokreślona. Argument `_Func` musi obsługiwać operator wywołania funkcji w postaci `operator()(T)` gdzie parametr `T` jest typem elementu kontenera jest powtarzana.  
  
```
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
Typ iteratora, używany do wykonywania iteracji w kontenerze.  
  
*_Function*<br/>
Typ funkcji, które zostaną zastosowane do każdego elementu w zakresie.  
  
*_Partitioner*<br/>
*pierwszy*<br/>
Iterator adresowania adresuje pozycję pierwszego elementu mają zostać uwzględnione w iteracjami równoległymi.  
  
*ostatni*<br/>
Iterator odnoszący się do pozycji pierwszej po elemencie końcowym mają zostać uwzględnione w iteracjami równoległymi.  
  
*_Func*<br/>
Obiekt funkcji zdefiniowanej przez użytkownika, która jest stosowana do każdego elementu w zakresie.  
  
*_Part —*<br/>
Odwołanie do obiektu partycjonera. Argument może być jednym z `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ partycjonera](simple-partitioner-class.md) `&` lub [affinity_partitioner](affinity-partitioner-class.md) `&` Jeśli [affinity_partitioner](affinity-partitioner-class.md) obiekt jest używany, odwołanie musi być wartością l niż stała odwołanie, tak aby algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia.  
  
### <a name="remarks"></a>Uwagi  
 [auto_partitioner](auto-partitioner-class.md) stosowanych w odniesieniu do przeciążenia bez jawnego partycjonera.  
  
 Iteratory, które nie obsługują losowe dostępem do tylko [auto_partitioner](auto-partitioner-class.md) jest obsługiwana.  
  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_invoke"></a>  parallel_invoke  
 Wykonuje obiektów funkcyjnych, podana jako parametry w równoległych i bloków, dopóki nie została zakończona, wykonywanie. Każdy obiekt funkcji, może być wyrażenie lambda, wskaźnika do funkcji, lub dowolny obiekt obsługujący operator wywołania funkcji z podpisem `void operator()()`.  
  
```
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
Typ pierwszy obiekt funkcji, aby być wykonywane równolegle.  
  
*_Function2*<br/>
Typ drugiego obiektu funkcji wykonywanej równolegle.  
  
*_Function3*<br/>
Typ trzeciego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function4*<br/>
Typ czwartego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function5*<br/>
Typ piątego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function6*<br/>
Typ szóstego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function7*<br/>
Typ siódmego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function8*<br/>
Typ ósmego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function9*<br/>
Typ dziewiątego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Function10*<br/>
Typ obiektu funkcji oraz być wykonywane równolegle.  
  
*_Func1*<br/>
Pierwszy obiekt funkcji, aby być wykonywane równolegle.  
  
*_Func2*<br/>
Drugi obiekt funkcji wykonywanej równolegle.  
  
*_Func3*<br/>
Trzeci obiekt funkcji wykonywanej równolegle.  
  
*_Func4*<br/>
Czwarty obiekt funkcji, który ma być wykonana równolegle.  
  
*_Func5*<br/>
Piąty obiekt funkcji, który ma być wykonana równolegle.  
  
*_Func6*<br/>
Szósty obiekt funkcji, który ma być wykonana równolegle.  
  
*_Func7*<br/>
Siódmego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Func8*<br/>
Ósmego obiekt funkcji, który ma być wykonana równolegle.  
  
*_Func9*<br/>
Dziewiąty obiekt funkcji, który ma być wykonana równolegle.  
  
*_Func10*<br/>
Obiekt funkcji oraz być wykonywane równolegle.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że co najmniej jeden z obiektów funkcyjnych dostarczone jako parametry wbudowane może być wykonywany na kontekst wywołania.  
  
 Jeśli jeden lub więcej obiektów funkcyjnych przekazywane jako parametry do tej funkcji zgłasza wyjątek, środowisko uruchomieniowe zaznaczy jeden taki wyjątek, jego zalety i propagowanie go poza wywołanie `parallel_invoke`.  
  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_radixsort"></a>  parallel_radixsort —  
 Rozmieszcza elementy w określonym zakresie, w innych malejąco według, za pomocą podstawy, algorytm sortowania. To jest funkcja stabilne sortowanie, które wymaga funkcji projekcji, które można poddawać projekcji elementy, które mają być sortowane w niepodpisane klucze podobne do liczby całkowitej. Domyślna Inicjalizacja jest wymagany dla elementów posortowana.  
  
```
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
Typ iteratora danych wejściowych zakresu.  
  
*_Allocator*<br/>
Typ alokatora pamięci zgodne standardowej biblioteki języka C++.  
  
*_Function*<br/>
Typ funkcji projekcji.  
  
*_Rozpocznij*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie ma zostać posortowana.  
  
*_Zakończ*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszej po elemencie końcowym w zakresie ma zostać posortowana.  
  
*_Alloc*<br/>
Wystąpienie alokatora pamięci zgodne standardowej biblioteki języka C++.  
  
*_Proj_func*<br/>
Obiekt funkcji projekcji zdefiniowanych przez użytkownika, który konwertuje element na wartość całkowitą.  
  
*_Chunk_size*<br/>
Rozmiar minimalny fragment, zostanie ona podzielona na dwie dla przetwarzania równoległego.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie przeciążenia wymagają `n * sizeof(T)` dodatkowe miejsce, gdzie `n` jest to liczba elementów, które mają być sortowane i `T` jest typ elementu. Jednoargumentowy funktor projekcji o podpisie `I _Proj_func(T)` jest wymagane, aby przywrócić klucz, gdy element, gdzie `T` jest typ elementu i `I` jest typ notacji liczba całkowita bez znaku.  
  
 Jeśli funkcja projekcji nie jest podana, funkcja projekcji domyślna, która po prostu zwraca element jest używany w przypadku typów całkowitych. Funkcja zakończy się niepowodzeniem skompilować, jeśli element nie jest typem całkowitym w przypadku braku funkcja projekcji.  
  
 Jeśli nie zostanie podany typ programu przydzielania lub wystąpienia, alokatora pamięci standardowej biblioteki języka C++ `std::allocator<T>` służy do przydzielania buforu.  
  
 Algorytm zakresu wejściowego jest podzielony na dwie części i kolejno każdego fragmentu są podzielone na dwie części podrzędnych do wykonania w sposób równoległy. Opcjonalny argument `_Chunk_size` może służyć do wskazywania algorytm powinien obsługi fragmenty o rozmiarze < `_Chunk_size` szeregowo.  
  
##  <a name="parallel_reduce"></a>  parallel_reduce  
 Oblicza sumę wszystkich elementów w określonym zakresie przez obliczanie kolejnych sum częściowych, lub oblicza kolejne wyniki częściowe podobnie uzyskanej przy użyciu określonej operacji binarnej sumą, równolegle. `parallel_reduce` przypomina semantycznie `std::accumulate`, z tą różnicą, że wymaga operacja binarna być asocjacyjna i wymaga wartości tożsamości zamiast wartości początkowej.  
  
```
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
Typ iteratora danych wejściowych zakresu.  
  
*_Sym_reduce_fun*<br/>
Typ funkcji redukcji symetryczne. Musi to być typ funkcji za pomocą podpisu `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, gdzie _Reduce_type jest taki sam jak typ tożsamości i typ wyniku redukcji. Trzecie przeciążenie to powinien być zgodny z typem danych wyjściowych `_Range_reduce_fun`.  
  
*_Reduce_type*<br/>
Typ który zmniejszy danych wejściowych, który może być inny niż typ elementu wejściowego. Zwracana wartość i wartość tożsamości zostanie ma tego typu.  
  
*_Range_reduce_fun*<br/>
Typ funkcji zmniejszenie zakresu. Musi to być typ funkcji za pomocą podpisu `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type jest taki sam jak typ tożsamości i typ wyniku redukcji.  
  
*_Rozpocznij*<br/>
Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie obniżenie.  
  
*_Zakończ*<br/>
Iterator danych wejściowych, odnoszący się do elementu, który jest o jedną pozycję poza ostatnim elementem w zakresie obniżenie.  
  
*_Identity*<br/>
Wartość tożsamości `_Identity` jest taki sam typ co typ wyniku ograniczenia, a także `value_type` iteratora dla pierwszego i drugiego przeciążenia. W przypadku trzecie przeciążenie wartość tożsamości musi mieć taki sam typ co typ wyniku redukcji jednak może być inny niż `value_type` iteratora. Musi mieć odpowiednie wartości tak, aby operator zmniejszenie zakresu `_Range_fun`, po zastosowaniu różnych pojedynczy element typu `value_type` i wartość tożsamości, który zachowuje się jak rzutowanie typu wartości z typu `value_type` typ tożsamości.  
  
*_Sym_fun*<br/>
Funkcja symetryczne, używanym w drugim redukcji. Aby uzyskać więcej informacji, zobacz uwagi.  
  
*_Range_fun*<br/>
Funkcja, która będzie używana w pierwszej fazie redukcji. Aby uzyskać więcej informacji, zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik redukcji.  
  
### <a name="remarks"></a>Uwagi  
 Do wykonywania równoległych redukcji, funkcja dzieli zakres na fragmenty na podstawie liczby procesów roboczych dostępnych do bazowego harmonogramu. Zmniejszenie odbywa się w dwóch fazach, pierwsza faza wykonuje redukcji w ramach każdego fragmentu i drugą fazę wykonuje redukcji między częściowe wyniki z każdego fragmentu.  
  
 Pierwsze przeciążenie wymaga, aby iteratora `value_type`, `T`, być taka sama jak typ wartości tożsamości, a także typ wyniku redukcji. Element typu T należy podać operator `T T::operator + (T)` zmniejszyć elementy w każdym fragmencie. Tym samym operator jest używany w drugim etapie także.  
  
 Drugie przeciążenie wymaga również, aby iteratora `value_type` być taka sama jak typ wartości tożsamości, a także typ wyniku redukcji. Dostarczony operator binarny `_Sym_fun` jest używany w obu fazach zmniejszenie o wartości tożsamości jako wartość początkową dla pierwszej fazy.  
  
 Dla trzecie przeciążenie typu wartości tożsamości musi być taka sama jak redukcja typu wyniku, ale iteratora `value_type` może się różnić od obu. Funkcja redukcji zakresu `_Range_fun` jest używany w pierwszej fazie przy użyciu wartości tożsamości jako wartość początkową, a funkcja binarne `_Sym_reduce_fun` jest stosowany do podrzędnych wyniki w drugim etapie.  
  
##  <a name="parallel_sort"></a>  parallel_sort —  
 Rozmieszcza elementy w określonym zakresie w niemalejącej kolejności lub według kryteriów sortowania określonych przez binarny predykat, jednocześnie. Ta funkcja przypomina semantycznie `std::sort` , jest sortowania na podstawie porównania, niestabilne, w miejscu.  
  
```
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
Typ iteratora danych wejściowych zakresu.  
  
*_Function*<br/>
Typ funktor porównanie binarne.  
  
*_Rozpocznij*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszego elementu w zakresie ma zostać posortowana.  
  
*_Zakończ*<br/>
Iterator dostępu swobodnego odnoszący się do pozycji pierwszej po elemencie końcowym w zakresie ma zostać posortowana.  
  
*_Func*<br/>
Obiekt funkcji predykatu zdefiniowanej przez użytkownika, który definiuje kryterium porównania, które muszą być spełnione przez kolejne elementy w kolejności. Predykat dwuelementowy przyjmuje dwa argumenty i zwraca `true` po spełnieniu oraz `false` Jeśli nie jest spełniony. Ta funkcja komparator musi powodować ścisłe słabe porządkowanie w pary elementów z sekwencji.  
  
*_Chunk_size*<br/>
Rozmiar minimalny fragment, zostanie ona podzielona na dwie dla przetwarzania równoległego.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsze przeciążenie używa porównania binarne `std::less`.  
  
 Drugi przeciążone używa podane komparator binarne, którą powinien posiadać podpis `bool _Func(T, T)` gdzie `T` jest typ elementów w zakresie wejściowym.  
  
 Algorytm zakresu wejściowego jest podzielony na dwie części i kolejno każdego fragmentu są podzielone na dwie części podrzędnych do wykonania w sposób równoległy. Opcjonalny argument `_Chunk_size` może służyć do wskazywania algorytm powinien obsługi fragmenty o rozmiarze < `_Chunk_size` szeregowo.  
  
##  <a name="parallel_transform"></a>  Funkcja parallel_transform  
 Stosuje określony obiekt funkcji do każdego elementu w zakresie źródłowym lub pary elementów z dwóch zakresów sortowania i kopiuje zwracane wartości obiektu funkcji do zakresu docelowego, równolegle. Tym funkcjonalności są semantycznie równoważne `std::transform`.  
  
```
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
Typ pierwszego lub tylko iterator danych wejściowych.  
  
*_Output_iterator*<br/>
Typ iteratora wyjściowego.  
  
*_Unary_operator*<br/>
Typ Jednoelementowy funkcję do wykonania dla każdego elementu w zakresie wejściowym.  
  
*_Input_iterator2*<br/>
Typ drugiego iteratora danych wejściowych.  
  
*_Binary_operator*<br/>
Typ binarny funkcję parowania wykonywane elementów z dwóch zakresów.  
  
*_Partitioner*<br/>
*first1*<br/>
Iterator danych wejściowych, odnoszący się do pozycji pierwszego elementu w pierwszym lub tylko zakres źródłowy na.  
  
*Nazwisko1*<br/>
Iterator danych wejściowych, odnoszący się do pozycji pierwszej po ostatnim elementem w pierwszej lub tylko zakresu źródłowego na.  
  
*_Result*<br/>
Iterator danych wyjściowych odnoszący się do pozycji pierwszego elementu w zakresie docelowym.  
  
*_Unary_op*<br/>
Jednoargumentowy zdefiniowanych przez użytkownika obiekt funkcji, która jest stosowana do każdego elementu w zakresie źródłowym.  
  
*_Part —*<br/>
Odwołanie do obiektu partycjonera. Argument może być jednym z `const` [auto_partitioner](auto-partitioner-class.md)`&`, `const` [static_partitioner](static-partitioner-class.md)`&`, `const` [simple_ partycjonera](simple-partitioner-class.md) `&` lub [affinity_partitioner](affinity-partitioner-class.md) `&` Jeśli [affinity_partitioner](affinity-partitioner-class.md) obiekt jest używany, odwołanie musi być wartością l niż stała odwołanie, tak aby algorytm może przechowywać stan dla przyszłych pętli do ponownego użycia.  
  
*first2*<br/>
Iterator danych wejściowych, odnoszący się do pozycji pierwszego elementu w zakresie źródłowym drugi na.  
  
*_Binary_op*<br/>
Obiekt binarny funkcji zdefiniowanej przez użytkownika, który jest stosowany parowania, w kolejności do przodu, do dwóch zakresów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator danych wyjściowych odnoszący się do pozycji pierwszej po elemencie końcowym w zakresie docelowym, który otrzymuje elementy danych wyjściowych przekształcenia przez obiekt funkcji.  
  
### <a name="remarks"></a>Uwagi  
 [auto_partitioner](auto-partitioner-class.md) stosowanych w odniesieniu do przeciążenia bez jawnego partycjonera argumentu.  
  
 Iteratory, które nie obsługują losowe dostępem do tylko [auto_partitioner](auto-partitioner-class.md) jest obsługiwana.  
  
 Przeciążenia, które przyjmują argument `_Unary_op` Przekształcanie zakres wyjściowy zakresu wejściowego, stosując funkcję jednoargumentowe do każdego elementu w zakresie wejściowym. `_Unary_op` musi obsługiwać operator wywołania funkcji za pomocą podpisu `operator()(T)` gdzie `T` jest typem wartości zakresu jest powtarzana.  
  
 Przeciążenia, które przyjmują argument `_Binary_op` Przekształcanie dwa zakresy danych wejściowych zakres wyjściowy, stosując funktor binarne do jednego elementu z pierwszym zakresu wejściowego i jednego elementu z drugiego zakresu wejściowego. `_Binary_op` musi obsługiwać operator wywołania funkcji za pomocą podpisu `operator()(T, U)` gdzie `T`, `U` są typami wartości danych wejściowych do dwóch iteratorów.  
  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="receive"></a>  Odbieranie  
 Ogólny otrzymują implementacji, umożliwiając kontekstu, aby czekać na dane z dokładnie jednego źródła i filtrować wartości, które są akceptowane.  
  
```
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
  
*_Limit czasu*<br/>
Maksymalny czas dla którego należy metoda dla danych, w milisekundach.  
  
*_Filter_proc*<br/>
Funkcja filtrowania, który określa, czy powinna być akceptowana wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość z zakresu od źródła typ ładunku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany, jeżeli określony przedział czasu upłynie, zanim wiadomość zostaje odebrana. Jeśli ma zerową długość przekroczenie limitu czasu, należy użyć [try_receive —](concurrency-namespace-functions.md) funkcji, w przeciwieństwie do wywoływania `receive` z limitem czasu równym `0` (zero), ponieważ jest bardziej wydajne i nie generuje wyjątków przekroczenia limitu czasu.  
  
 Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token —  
 Wykonuje obiektu funkcyjnego natychmiast w kontekście token danego odwołania.  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>Parametry  
*_Function*<br/>
Typ obiektu funkcji, która zostanie wywołana.  
  
*_Func*<br/>
Obiekt funkcji, która zostanie wykonana. Ten obiekt musi obsługiwać za pomocą podpisu void(void) operatora wywołania funkcji.  
  
*_Ct*<br/>
Token anulowania, który będzie kontrolować anulowanie niejawne obiektu funkcji. Użyj `cancellation_token::none()` Jeśli chcesz, aby funkcja wykonywania bez możliwości anulowanie niejawne z nadrzędnej grupy zadań, zostanie ono anulowane.  
  
### <a name="remarks"></a>Uwagi  
 Żadnych punktów przerwania w obiekt funkcji, który zostanie wywołany, gdy `cancellation_token` zostało anulowane. Jawne token `_Ct` izoluje to `_Func` z nadrzędnego anulowania, jeśli element nadrzędny ma inny token lub brak tokenu.  
  
##  <a name="send"></a>  Wyślij  
 Operacja synchroniczna wysyłania, która czeka, aż element docelowy zaakceptuje lub odrzuci to wiadomość.  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Typ ładunku.  
  
*_Trg*<br/>
Wskaźnik lub odwołanie do obiektu docelowego, do którego dane są wysyłane.  
  
*_Dane*<br/>
Odwołanie do danych do wysłania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został zaakceptowany, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler —  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>Parametry  
*_Scheduler*<br/>
Harmonogram otoczenia, który można ustawić.
  
##  <a name="set_task_execution_resources"></a>  set_task_execution_resources —  
 Ogranicza zasoby wykonywania używane przez środowisko uruchomieniowe współbieżności wewnętrznego wątków na koligacji określony zestaw.  
  
 Jest on prawidłowy, aby wywołać tę metodę, tylko, zanim Menedżer zasobów została utworzona lub między dwoma okresy istnienia usługi Resource Manager. Może być wywoływany wielokrotnie tak długo, jak usługi Resource Manager nie istnieje w momencie wywołania. Po ustawieniu limitu koligacji on obowiązuje do następnego wywołania prawidłowy do `set_task_execution_resources` metody.  
  
 Maska koligacji nie muszą być podzbiorem Maska koligacji procesu. Koligacja procesu zostanie zaktualizowany, jeśli to konieczne.  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>Parametry  
*_ProcessAffinityMask*<br/>
Maska koligacji, która wątków roboczych współbieżność środowiska wykonawczego jest ograniczona do. Użyj tej metody w systemie o rozmiarze większym niż 64 wątków sprzętu, tylko wtedy, gdy chcesz ograniczyć środowiska uruchomieniowego współbieżności z podzbiorem bieżącą grupę procesorów. Ogólnie rzecz biorąc należy użyć wersji metody, która przyjmuje tablicę grupy koligacji jako parametru, aby ograniczyć koligacji na komputerach o rozmiarze większym niż 64 wątków sprzętu.  
  
*Liczba*<br/>
Liczba `GROUP_AFFINITY` pozycje w tablicy, określony przez parametr `_PGroupAffinity`.  
  
*_PGroupAffinity*<br/>
Tablica `GROUP_AFFINITY` wpisów.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłosi [invalid_operation](invalid-operation-class.md) wyjątek, jeśli usługi Resource Manager znajduje się w czasie jest wywoływana, i [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli określona koligacja jest wyników w pustym zestawem zasoby.  
  
 Wersja metody, która przyjmuje tablicę grupy koligacji, jako parametr powinien składać się wyłącznie używanych w systemach operacyjnych z wersji Windows 7 lub nowszej. W przeciwnym razie [invalid_operation](invalid-operation-class.md) wyjątku.  
  
 Programowo modyfikowanie koligacji procesu po wywołaniu tej metody nie spowoduje ponownej oceny koligacji, który jest ograniczony do Menedżera zasobów. W związku z tym wszystkie zmiany do przetworzenia koligacji należy przed wywołaniem tej metody.  
  
##  <a name="swap"></a>  swap  
 Zamienia elementy z dwóch `concurrent_vector` obiektów.  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Typ danych elementów zapisanych w wektorów współbieżnych.  
  
*_Ax*<br/>
Typ programu przydzielania wektorów współbieżnych.  
  
*_A*<br/>
Współbieżnego wektora, której elementy są wymieniane z tymi współbieżnego wektora `_B`.  
  
*_B*<br/>
Współbieżnego wektora zawierająca elementy, które mają być zamienione lub wektora, której elementy są wymieniane z tymi współbieżnego wektora `_A`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm wyspecjalizowane klasy kontenera `concurrent_vector` na wykonanie funkcji elementu członkowskiego `_A`. [concurrent_vector::swap —](concurrent-vector-class.md#swap)( `_B`). Są to wystąpień częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonu przeciążone są w sposób dopasowania szablonu za pomocą wywołania funkcji nie jest unikatowa, kompilator wybierze najbardziej wyspecjalizowaną wersję funkcji szablonu. Ogólne wersję funkcji szablonu `template <class T> void swap(T&, T&)`, w algorytmie klasy działa przez przypisanie a wolne działanie. Specjalizowanej wersji w każdym kontenerze jest znacznie szybsza, ponieważ może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
 Ta metoda nie jest bezpieczna pod kątem współbieżności. Należy się upewnić, że nie ma innych wątków są wykonywanie operacji na albo wektorów współbieżnych po wywołaniu tej metody.  
  
##  <a name="task_from_exception"></a>  task_from_exception —  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>Parametry  
*_TaskType*<br/>

*_ExType*<br/>

*_Exception —*<br/>

*_TaskOptions*<br/>
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="task_from_result"></a>  task_from_result —  
  
```
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
  
##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name —  
 Kojarzy imię blok komunikatów lub agenta śledzenia zdarzeń systemu Windows.  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>Parametry  
*T*<br/>
Typ obiektu. Zazwyczaj jest to blok komunikatów lub agenta.  
  
*_PObject*<br/>
Wskaźnik do bloku komunikatów lub agenta o nazwie w śladzie.  
  
*_Nazwa*<br/>
Nazwa dla danego obiektu.  
  
##  <a name="try_receive"></a>  try_receive —  
 Ogólny spróbuj i odbierania implementacji, umożliwiając kontekstu, aby wyszukiwać dane z dokładnie jednego źródła i filtrować wartości, które są akceptowane. Jeśli dane nie są gotowe, metoda zwróci wartość false.  
  
``` 
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
  
*_wartość*<br/>
Odwołanie do lokalizacji, w którym zostaną umieszczone wyniki.  
  
*_Filter_proc*<br/>
Funkcja filtrowania, który określa, czy powinna być akceptowana wiadomości.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `bool` wartość wskazującą, czy ładunek został umieszczony w `_value`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [funkcje przekazywania komunikatów](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="wait"></a>  Czekaj  
 Wstrzymuje działanie bieżącego kontekstu na określoną ilość czasu.  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>Parametry  
*_Milliseconds*<br/>
Liczba milisekund, które bieżący kontekst powinien wstrzymane dla zasad. Jeśli `_Milliseconds` parametr jest ustawiony na wartość `0`, bieżącego kontekstu powinien uzyskanie wykonywania innych kontekstach możliwy do uruchomienia przed kontynuowaniem.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ta metoda jest wywoływana w środowisku uruchomieniowym współbieżności: Kontekst harmonogramu, harmonogram znajdzie inny kontekst do uruchamiania na bazowego zasobu. Ponieważ Harmonogram jest współpraca z natury, tym kontekście nie można wznowić dokładnie po wyrażony w milisekundach czas określony. Jeśli harmonogram jest zajęty, wykonywanie innych zadań, które nie wspólnie dają wyniku do harmonogramu, okres oczekiwania może być nieokreślony.  
  
##  <a name="when_all"></a>  when_all —  
 Tworzy zadanie, które zostanie ukończone pomyślnie, gdy wszystkie zadania dostarczone jako argumenty zakończą się pomyślnie.  
  
```
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
  
*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które można połączyć w zadanie wynikowe.  
  
*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które można połączyć w zadanie wynikowe.  
  
*_TaskOptions*<br/>
`task_options` Obiektu.
  
### <a name="return-value"></a>Wartość zwracana  
 Zadanie, które zostaje wykonane pomyślnie, gdy wszystkie zadania wejściowe zostały ukończone pomyślnie. Jeśli zadania wejściowe są typu `T`, danymi wyjściowymi tej funkcji będą `task<std::vector<T>>`. Jeśli zadania wejściowe są typu `void` zadaniem wyjściowym też będzie `task<void>`.  
  
### <a name="remarks"></a>Uwagi  
 `when_all` jest funkcją bez blokowania tworzącego `task` jako wynik. W odróżnieniu od [Task::wait —](task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA (aplikacja STA).  
  
 Jeśli jedno z zadań zostanie anulowane lub zgłasza wyjątek, zwrócone zadanie zostanie ukończone przedwcześnie ze stanem anulowane, a wyjątek, jeśli wystąpi, zostanie zgłoszony, jeśli wywołujesz [Task::GET —](task-class.md#get) lub `task::wait` dla tego zadania.  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="when_any"></a>  when_any —  
 Tworzy zadanie, które zostanie ukończone pomyślnie po dowolne zadania dostarczone jako argumenty zakończą się pomyślnie.  
  
```
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
  
*_Rozpocznij*<br/>
Pozycja pierwszego elementu w zakresie elementów, które można połączyć w zadanie wynikowe.  
  
*_Zakończ*<br/>
Pozycja pierwszego elementu poza zakresem elementów, które można połączyć w zadanie wynikowe.  
  
*_TaskOptions*<br/>
*_CancellationToken*<br/>
Token anulowania, który steruje anulowaniem zadania zwróconego. Jeśli nie podasz token anulowania, wynikowe zadanie otrzyma token anulowania zadania, które powoduje jego ukończenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zadanie, które zostaje wykonane pomyślnie, gdy jeden z zadania wejściowe została ukończona pomyślnie. Jeśli zadania wejściowe są typu `T`, danymi wyjściowymi tej funkcji będą `task<std::pair<T, size_t>>>`, gdzie pierwszy element pary jest wynikiem ukończenia zadania, a drugi element jest indeks zadanie, które zostało zakończone. Jeśli zadania wejściowe są typu `void` dane wyjściowe są `task<size_t>`, gdzie wynik jest indeksem kończonego zadania.  
  
### <a name="remarks"></a>Uwagi  
 `when_any` jest funkcją bez blokowania tworzącego `task` jako wynik. W odróżnieniu od [Task::wait —](task-class.md#wait), można bezpiecznie wywołać tę funkcję w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA (aplikacja STA).  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
