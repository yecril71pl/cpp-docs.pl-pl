---
title: "Funkcje przestrzeń nazw współbieżności | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db8dd57c912c62dab895d613c5d7bbe0d5c3cd9a
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="concurrency-namespace-functions"></a>Funkcje przestrzeń nazw współbieżności
||||  
|-|-|-|  
|[Alokacji](#alloc)|[CreateResourceManager](#createresourcemanager)|[Disabletracing —](#disabletracing)|  
|[Enabletracing —](#enabletracing)|[W warstwie bezpłatna](#free)|[GetExecutionContextId](#getexecutioncontextid)|  
|[Getosversion —](#getosversion)|[GetProcessorCount](#getprocessorcount)|[GetProcessorNodeCount](#getprocessornodecount)|  
|[GetSchedulerId](#getschedulerid)|[Trace_agents_register_name](#trace_agents_register_name)|[asend —](#asend)|  
|[cancel_current_task](#cancel_current_task)|[Wyczyść](#clear)|[create_async](#create_async)|  
|[create_task](#create_task)|[get_ambient_scheduler](#get_ambient_scheduler)|[internal_assign_iterators](#internal_assign_iterators)|  
|[interruption_point](#interruption_point)|[is_current_task_group_canceling](#is_current_task_group_canceling)|[make_choice](#make_choice)|  
|[make_greedy_join](#make_greedy_join)|[make_join](#make_join)|[make_task](#make_task)|  
|[parallel_buffered_sort](#parallel_buffered_sort)|[parallel_for](#parallel_for)|[parallel_for_each](#parallel_for_each)|  
|[parallel_invoke](#parallel_invoke)|[parallel_radixsort](#parallel_radixsort)|[parallel_reduce —](#parallel_reduce)|  
|[parallel_sort](#parallel_sort)|[parallel_transform](#parallel_transform)|[receive](#receive)|  
|[run_with_cancellation_token](#run_with_cancellation_token)|[Wyślij](#send)|[set_ambient_scheduler](#set_ambient_scheduler)|  
|[set_task_execution_resources](#set_task_execution_resources)|[swap](#swap)|[task_from_exception —](#task_from_exception)|  
|[task_from_result](#task_from_result)|[try_receive](#try_receive)|[oczekiwania](#wait)|  
|[when_all —](#when_all)|[when_any —](#when_any)|  
  
##  <a name="alloc">Alokacji</a>  
 Przydziela bloku pamięci o wielkości określone z Suballocator buforowanie współbieżności środowiska wykonawczego.  
  
```
void* __cdecl Alloc(size_t _NumBytes);
```  
  
### <a name="parameters"></a>Parametry  
 `_NumBytes`  
 Liczba bajtów pamięci do przydzielenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o tym, które scenariuszy w aplikacji można korzystać z Suballocator buforowania, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="asend">asend —</a>  
 Operacja asynchronicznego wysyłania, która planuje zadania propagację danych blok docelowy.  
  
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
 `T`  
 Typ danych do wysłania.  
  
 `_Trg`  
 Wskaźnik lub odwołanie do obiektu docelowego, do którego dane są wysyłane.  
  
 `_Data`  
 Odwołanie do danych do wysłania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został zaakceptowany, zanim metoda zwróciła, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [funkcji przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="cancel_current_task"></a>  cancel_current_task —  
 Umożliwia anulowanie aktualnie wykonywanego zadania. Ta funkcja może zostać wywołana z w treści zadania do przerwania wykonywania zadań i spowodować, że wprowadzić `canceled` stanu.  
  
 Nie jest obsługiwany scenariusz do wywołania tej funkcji, jeśli nie znajdujesz się w treści `task`. W ten sposób spowoduje niezdefiniowane zachowanie, takich jak awarię lub zawieszenie aplikacji.  
  
```
inline __declspec(noreturn) void __cdecl cancel_current_task();
```  
  
##  <a name="clear">Wyczyść</a>  
 Czyści równoczesnych kolejki niszczenie żadnego obecnie elementów umieszczonych w kolejce. Ta metoda nie jest bezpieczne współbieżności.  
  
```
template<typename T, class _Ax>
void concurrent_queue<T, _Ax>::clear();
```   
  
### <a name="parameters"></a>Parametry  
 `T`  
 `_Ax`  
  
##  <a name="create_async"></a>  create_async —  
 Tworzy konstrukcję asynchroniczne środowiska wykonawczego systemu Windows oparte na obiekt lambda lub funkcja podana przez użytkownika. Zwracany typ `create_async` jest jednym z dwóch `IAsyncAction^`, `IAsyncActionWithProgress<TProgress>^`, `IAsyncOperation<TResult>^`, lub `IAsyncOperationWithProgress<TResult, TProgress>^` oparte na podpis lambda przekazywany do metody.  
  
```
template<typename _Function>
__declspec(noinline) auto create_async(const _Function& _Func)
    -> decltype(ref new details::_AsyncTaskGeneratorThunk<_Function>(_Func));
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 `_Func`  
 Obiekt lambda lub funkcji z którym ma zostać utworzony konstrukcję asynchroniczne środowiska wykonawczego systemu Windows.  
  
### <a name="return-value"></a>Wartość zwracana  
 Konstrukcja asynchroniczne reprezentowany przez IAsyncAction ^, IAsyncActionWithProgress\<TProgress > ^, IAsyncOperation\<TResult > ^, lub IAsyncOperationWithProgress\<TResult, TProgress > ^. Interfejs zwrócił zależy od podpis lambda przekazany do funkcji.  
  
### <a name="remarks"></a>Uwagi  
 Zwracany typ lambda Określa, czy konstrukcja jest operacji lub akcji.  
  
 Wyrażenia lambda, które zwracać typ void powodują tworzenie akcji. Wyrażenia lambda, które zwracają wynik typu `TResult` spowodować utworzenie operacji TResult.  
  
 Wyrażenie lambda może też zwracać `task<TResult>` która hermetyzuje pracy asynchroniczne w siebie lub jest to kontynuacja łańcuch zadań, które reprezentują asynchroniczne. W takim przypadku lambda, sam jest wykonywane w tekście, ponieważ zadania są tymi, które są wykonywane asynchronicznie, a zwracany typ Wyrażenie lambda jest nie opakowanych wygenerowało asynchroniczne konstrukcja zwrócony przez `create_async`. Oznacza to, że wyrażenie lambda zwracającego zadania\<void > spowoduje utworzenie działań i lambda, która zwraca klasę task,\<TResult > spowoduje utworzenie operacji TResult.  
  
 Wyrażenie lambda, może potrwać albo zero, co najmniej dwóch argumentów. Prawidłowe argumenty to `progress_reporter<TProgress>` i `cancellation_token`, w tej kolejności, jeśli obie są używane. Wyrażenie lambda bez argumentów powoduje utworzenie asynchroniczne konstrukcji bez możliwości raportowania postępu. Wyrażenie lambda, która przyjmuje progress_reporter —\<TProgress > spowoduje, że `create_async` do zwrócenia konstrukcję asynchroniczne, które raporty o typie TProgress zawsze `report` jest wywoływana metoda obiektu progress_reporter —. Lambda, która przyjmuje cancellation_token — może użyć tokenu, aby wyszukać anulowania lub przekaż go do zadań, które tworzy tak, aby anulowanie asynchroniczne konstrukcja powoduje, że anulowania zadań.  
  
 Jeśli jednostka obiektu lambda lub funkcja zwraca wynik (i nie jest to zadanie\<TResult >), lamdba zostanie wykonany asynchronicznie, w ramach procesu MTA w kontekście zadania środowiska uruchomieniowego niejawnie tworzy dla niego. `IAsyncInfo::Cancel` Metoda spowoduje anulowanie zadań niejawne.  
  
 Jeśli treść zwraca lambda zadanie, lamba wykonuje wbudowanego i przez zadeklarowanie lambda podjęcie argumentu typu `cancellation_token` możesz wyzwolić anulowania zadań lambda tworzony przez przekazanie tokenu WE po ich utworzeniu. Można także użyć `register_callback` metody w tokenie, aby spowodować środowiska uruchomieniowego do wywołania wywołania zwrotnego w przypadku wywołania `IAsyncInfo::Cancel` na async wyprodukowane operacji lub akcji.  
  
 Ta funkcja jest dostępna tylko do aplikacji środowiska wykonawczego systemu Windows.  
  
##  <a name="createresourcemanager"></a>  Createresourcemanager —  
 Zwraca interfejs, który reprezentuje pojedyncze wystąpienie Menedżera zasobów współbieżność środowiska wykonawczego. Menedżer zasobów jest odpowiedzialny za przydzielanie zasobów do transfery danych, które chcesz współpracować ze sobą.  
  
```
IResourceManager* __cdecl CreateResourceManager();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `IResourceManager` Interfejsu.  
  
### <a name="remarks"></a>Uwagi  
 Wiele kolejnych wywołań ta metoda zwróci tego samego wystąpienia usługi Resource Manager. Każde wywołanie metody zwiększa odwołanie liczba w usłudze Resource Manager i muszą być zgodne z wywołaniem do [IResourceManager::Release](http://msdn.microsoft.com/en-us/5d1356ec-fbd3-4284-a361-1e9e20bbb522) metody po zakończeniu Twojej harmonogramu komunikowania się z Menedżerem zasobów.  
  
 [unsupported_os —](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez współbieżności środowiska wykonawczego.  
  
##  <a name="create_task"></a>  create_task —  
 Tworzy PPL [zadań](http://msdn.microsoft.com/en-us/5389e8a5-5038-40b6-844a-55e9b58ad35f) obiektu. `create_task` mogą być używane wszędzie możesz korzystać z konstruktora zadań. Jest udostępniana głównie udogodnienie, ponieważ umożliwia używanie `auto` — słowo kluczowe podczas tworzenia zadania.  
  
```
template<typename T>
__declspec(noinline) auto create_task(T _Param, const task_options& _TaskOptions = task_options())
    -> task<typename details::_TaskTypeFromParam<T>::T>;

template<typename _ReturnType>
__declspec( noinline) task<_ReturnType> create_task(const task<_ReturnType>& _Task);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru, z którego ma zostać wykonane zadanie.  
  
 `_ReturnType`  
 `_Param`  
 Parametr, z którego ma zostać wykonane zadanie. Może to być obiekt lambda lub funkcja `task_completion_event` obiektu, inną `task` obiektu lub interfejs Windows::Foundation::IAsyncInfo, jeśli używasz zadania w aplikacji platformy uniwersalnej systemu Windows.  
  
 `_TaskOptions`  
 `_Task`  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe zadanie typu `T`, która jest wywnioskowany na podstawie `_Param`.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy przeciążenia zachowuje się jak zadanie konstruktora, który przyjmuje jeden parametr.  
  
 Drugi przeciążenia kojarzy token anulowania dostarczane z nowo utworzone zadanie. Jeśli używasz tego przeciążenia nie możesz przekazać w innej `task` obiektu jako pierwszym parametrem.  
  
 Typ zadania zwracane jest wywnioskowany na podstawie pierwszy parametr funkcji. Jeśli `_Param` jest `task_completion_event<T>`, `task<T>`, lub obiekt, który zwraca typ albo `T` lub `task<T>`, typ utworzonego zadania jest `task<T>`.  
  
 W aplikacji platformy uniwersalnej systemu Windows Jeśli `_Param` jest typu Windows::Foundation::IAsyncOperation\<T > ^ lub Windows::Foundation::IAsyncOperationWithProgress\<T, P > ^, lub obiekt, który zwraca jedną z tych typów, z zostaną utworzone zadanie Typ `task<T>`. Jeśli `_Param` jest typu Windows::Foundation::IAsyncAction ^ lub Windows::Foundation::IAsyncActionWithProgress\<P > ^, lub obiekt, który zwraca jedną z tych typów, będzie mieć typ utworzonego zadania `task<void>`.  
  
##  <a name="disabletracing">Disabletracing —</a>  
 Wyłącza śledzenie współbieżność środowiska wykonawczego. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest niezarejestrowany domyślnie.  
  
```
__declspec(deprecated("Concurrency::DisableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl DisableTracing();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wyłączenie śledzenia został poprawnie `S_OK` jest zwracany. Jeśli śledzenie nie zostały wcześniej zainicjowane, `E_NOT_STARTED` jest zwracana  
  
##  <a name="enabletracing">Enabletracing —</a>  
 Umożliwia śledzenie współbieżność środowiska wykonawczego. Ta funkcja jest przestarzały, ponieważ śledzenie zdarzeń systemu Windows jest teraz włączona domyślnie.  
  
```
__declspec(deprecated("Concurrency::EnableTracing is a deprecated function.")) _CRTIMP HRESULT __cdecl EnableTracing();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli Śledzenie zostało poprawnie zainicjowane, `S_OK` zwrócony, a w przeciwnym razie `E_NOT_STARTED` jest zwracany.  
  
##  <a name="free">W warstwie bezpłatna</a>  
 Zwalnia blok pamięci przydzielony wcześniej przez `Alloc` metodę Suballocator buforowanie współbieżności środowiska wykonawczego.  
  
```
void __cdecl Free(_Pre_maybenull_ _Post_invalid_ void* _PAllocation);
```  
  
### <a name="parameters"></a>Parametry  
 `_PAllocation`  
 Wskaźnik do pamięci przydzielonej wcześniej przez `Alloc` metodę, która ma zostać zwolniony. Jeśli parametr `_PAllocation` jest ustawiona na wartość `NULL`, ta metoda będzie ją zignorować i zwracać natychmiast.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji o tym, które scenariuszy w aplikacji można korzystać z Suballocator buforowania, zobacz [harmonogram zadań](../../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
##  <a name="get_ambient_scheduler"></a>  get_ambient_scheduler  
  
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
 Unikatowy identyfikator kontekstu wykonywania.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do uzyskania identyfikatora kontekstu wykonywania przed przekazujesz `IExecutionContext` interfejsu jako parametr do dowolnej z metod oferowane przez Menedżera zasobów.  
  
##  <a name="getosversion">Getosversion —</a>  
 Zwraca informacje o wersji systemu operacyjnego.  
  
```
IResourceManager::OSVersion __cdecl GetOSVersion();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość wyliczenia reprezentujący system operacyjny.  
  
### <a name="remarks"></a>Uwagi  
 [unsupported_os —](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez współbieżności środowiska wykonawczego.  
  
##  <a name="getprocessorcount"></a>  Getprocessorcount —  
 Zwraca liczbę wątków sprzętu na podstawowym systemie.  
  
```
unsigned int __cdecl GetProcessorCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba wątków sprzętu.  
  
### <a name="remarks"></a>Uwagi  
 [unsupported_os —](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez współbieżności środowiska wykonawczego.  
  
##  <a name="getprocessornodecount"></a>  Getprocessornodecount —  
 Zwraca liczbę węzłów NUMA lub pakietów procesora na podstawowym systemie.  
  
```
unsigned int __cdecl GetProcessorNodeCount();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba węzłów NUMA lub pakietów procesora.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli system zawiera więcej węzłów NUMA niż pakiety procesora, liczbę węzłów NUMA jest zwracany, w przeciwnym razie zwracany jest maksymalna liczba pakietów procesora.  
  
 [unsupported_os —](unsupported-os-class.md) jest generowany, jeśli system operacyjny nie jest obsługiwany przez współbieżności środowiska wykonawczego.  
  
##  <a name="getschedulerid"></a>  GetSchedulerId  
 Zwraca unikatowy identyfikator, który można przypisać do harmonogramu, który implementuje `IScheduler` interfejsu.  
  
```
unsigned int __cdecl GetSchedulerId();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Unikatowy identyfikator dla harmonogramu.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda służy do uzyskania identyfikatora użytkownika harmonogramu przed przekazujesz `IScheduler` interfejsu jako parametr do dowolnej z metod oferowane przez Menedżera zasobów.  
  
##  <a name="internal_assign_iterators"></a>  internal_assign_iterators —  
  
```
template<typename T, class _Ax>
template<class _I> 
void concurrent_vector<T, _Ax>::internal_assign_iterators(
   _I first,
   _I last);
```   
  
### <a name="parameters"></a>Parametry  
 `T`  
 `_Ax`  
 `_I`  
 `first`  
 `last`  
  
##  <a name="interruption_point"></a>  interruption_point —  
 Tworzy punkt przerwania do anulowania. Jeśli trwa anulowanie w tym kontekście, w którym ta funkcja jest wywoływana, zgłosi wyjątek wewnętrzny, który przerywa wykonywanie aktualnie wykonywane równolegle pracy. Jeśli anulowania nie jest w toku, funkcja nie działa.  
  
```
inline void interruption_point();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie należy przechwytywać anulowania wewnętrzny wyjątek przez `interruption_point()` funkcji. Wyjątek zostanie przechwycony i obsługiwane przez środowisko wykonawcze i przechwytywanie go może spowodować program będzie działać nieprawidłowo.  
  
##  <a name="is_current_task_group_canceling"></a>  is_current_task_group_canceling  
 Zwraca wskazaniem, czy zadanie grupy, które jest aktualnie wykonywany wbudowany w bieżącym kontekście jest pośrodku active anulowania (lub zostanie wkrótce). Należy pamiętać, że jeśli grupa zadań wykonywanych aktualnie wbudowany w bieżącym kontekście `false` zostaną zwrócone.  
  
```
bool __cdecl is_current_task_group_canceling();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli grupy zadań, które jest aktualnie wykonywany jest anulowanie, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [anulowania](../../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md#cancellation).  
  
##  <a name="make_choice"></a>  make_choice —  
 Konstruuje `choice` bloku komunikatów z opcjonalną `Scheduler` lub `ScheduleGroup` i dwa lub więcej źródeł danych wejściowych.  
  
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
 `T1`  
 Typ bloku komunikatów pierwszego źródła.  
  
 `T2`  
 Typ bloku komunikatów drugie źródło.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `choice` zaplanowano bloku obsługi wiadomości.  
  
 `_Item1`  
 Pierwsze źródło.  
  
 `_Item2`  
 Drugie źródło.  
  
 `_Items`  
 Dodatkowe źródła.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `choice` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `choice` bloku komunikatów z dwóch lub więcej źródeł danych wejściowych.  
  
##  <a name="make_greedy_join"></a>  make_greedy_join —  
 Konstruuje `greedy multitype_join` bloku komunikatów z opcjonalną `Scheduler` lub `ScheduleGroup` i dwa lub więcej źródeł danych wejściowych.  
  
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
 `T1`  
 Typ bloku komunikatów pierwszego źródła.  
  
 `T2`  
 Typ bloku komunikatów drugie źródło.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `multitype_join` zaplanowano bloku obsługi wiadomości.  
  
 `_Item1`  
 Pierwsze źródło.  
  
 `_Item2`  
 Drugie źródło.  
  
 `_Items`  
 Dodatkowe źródła.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `multitype_join` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `greedy multitype_join` bloku komunikatów z dwóch lub więcej źródeł danych wejściowych.  
  
##  <a name="make_join"></a>  make_join —  
 Konstruuje `non_greedy multitype_join` bloku komunikatów z opcjonalną `Scheduler` lub `ScheduleGroup` i dwa lub więcej źródeł danych wejściowych.  
  
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
 `T1`  
 Typ bloku komunikatów pierwszego źródła.  
  
 `T2`  
 Typ bloku komunikatów drugie źródło.  
  
 `_PScheduler`  
 `Scheduler` Obiektu, w którym zadanie propagacji `multitype_join` zaplanowano bloku obsługi wiadomości.  
  
 `_Item1`  
 Pierwsze źródło.  
  
 `_Item2`  
 Drugie źródło.  
  
 `_Items`  
 Dodatkowe źródła.  
  
 `_PScheduleGroup`  
 `ScheduleGroup` Obiektu, w którym zadanie propagacji `multitype_join` zaplanowano bloku obsługi wiadomości. `Scheduler` Technicznego obiekt używany przez grupę harmonogramu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `non_greedy multitype_join` bloku komunikatów z dwóch lub więcej źródeł danych wejściowych.  
  
##  <a name="make_task"></a>  make_task —  
 Fabryka metodę tworzenia `task_handle` obiektu.  
  
```
template <class _Function>
task_handle<_Function> make_task(const _Function& _Func);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcja, która będzie wywołana na wykonanie pracy reprezentowany przez `task_handle` obiektu.  
  
 `_Func`  
 Funkcji, które będą wywoływane w celu wykonywania pracy reprezentowany przez `task_handle` obiektu. Może to być obiekt lambda, wskaźnika do funkcji, lub dowolnego obiektu, która obsługuje wersję operator wywołania funkcji z podpisem `void operator()()`.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `task_handle` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest przydatna, gdy trzeba utworzyć `task_handle` obiektu za pomocą wyrażenia lambda, ponieważ pozwala na tworzenie obiektu bez wiedzy o typu wartość true, obiekt lambda.  
  
##  <a name="parallel_buffered_sort"></a>  parallel_buffered_sort —  
 Rozmieszcza elementy w określonym zakresie w kolejności nondescending lub zgodnie z kryterium porządkowania określony przez predykat binarnego, równolegle. Ta funkcja przypomina semantycznie `std::sort` w tym z tą różnicą, że konieczne jest sortowania na podstawie porównania, niestabilny, w miejscu `O(n)` dodatkowe miejsce i wymaga inicjowanie domyślnych elementów sortowane.  
  
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
 `_Random_iterator`  
 Typ iteratora zakresu wejściowego.  
  
 `_Allocator`  
 Typ zgodny alokatora standardowa biblioteka C++.  
  
 `_Function`  
 Typ porównania binarnego.  
  
 `_Begin`  
 Dostęp losowy iteratora adresowania położenie pierwszego elementu w zakresie ma zostać posortowana.  
  
 `_End`  
 Dostęp losowy iteratora adresowania poza ostatniego elementu w zakresie pozycji, co ma zostać posortowana.  
  
 `_Alloc`  
 Wystąpienie alokatora zgodne standardowa biblioteka C++.  
  
 `_Func`  
 Obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca `true` po spełnieniu i `false` gdy nie są spełnione. Ta funkcja komparatora musi nakładają strict słabe porządkowanie dla pary elementów z sekwencji.  
  
 `_Chunk_size`  
 Rozmiar co najmniej fragment, do którego zostanie podzielony na dwa do wykonywania równoległego.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie przeciążenia wymagają `n * sizeof(T)` dodatkowe miejsce, gdy `n` jest liczba elementów, które mają być sortowane i `T` jest typ elementu. W większości przypadków parallel_buffered_sort — wyświetli poprawy wydajności za pośrednictwem [parallel_sort —](concurrency-namespace-functions.md), i należy z niej korzystać za pośrednictwem parallel_sort — Jeśli masz dostępnej pamięci.  
  
 Jeśli nie podasz binarne komparatora `std::less` jest używany jako domyślny, który wymaga typu elementu zapewnienie operator `operator<()`.  
  
 Jeśli nie podasz alokatora typ lub wystąpienie, alokatora standardowa biblioteka C++ `std::allocator<T>` służy do alokacji buforu.  
  
 Algorytm zakres wejściowy jest podzielony na dwie fragmentów i kolejno dzieli dwie fragmentów podrzędne wykonywanie równoległe każdego fragmentu. Opcjonalny argument `_Chunk_size` może służyć do wskazywania algorytm powinien obsługi fragmenty rozmiaru < `_Chunk_size` pojedynczo.  
  
##  <a name="parallel_for"></a>  parallel_for  
 `parallel_for` wykonuje iterację na zakres indeksy i wykonuje funkcję dostarczone przez użytkownika w każdej iteracji równolegle.  
  
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
 `_Index_type`  
 Typ indeksu używany na potrzeby iteracji.  
  
 `_Function`  
 Typ funkcji, która zostanie wykonana w każdej iteracji.  
  
 `_Partitioner`  
 Typ partycjonerem, który jest używany do partycjonowania podany zakres.  
  
 `first`  
 Indeks pierwszego do uwzględnienia w iteracji.  
  
 `last`  
 Indeks jednej poza ostatniego indeksu do uwzględnienia w iteracji.  
  
 `_Step`  
 Wartość w kroku podczas iteracji z `first` do `last`. Krok musi być dodatnia. [invalid_argument —](../../../standard-library/invalid-argument-class.md) jest generowany, jeśli kroku jest mniejszy niż 1.  
  
 `_Func`  
 Funkcja mają być wykonane w każdej iteracji. Może to być wyrażenie lambda, wskaźnik funkcji, lub dowolnego obiektu, która obsługuje wersję operator wywołania funkcji z podpisem `void operator()(_Index_type)`.  
  
 `_Part`  
 Odwołanie do obiektu partycjonera. Argument może być jedną z `const` [auto_partitioner —](auto-partitioner-class.md)`&`, `const` [static_partitioner —](static-partitioner-class.md)`&`, `const` [simple_ partycjoner](simple-partitioner-class.md) `&` lub [affinity_partitioner —](affinity-partitioner-class.md) `&` Jeśli [affinity_partitioner —](affinity-partitioner-class.md) obiekt jest używany, odwołania musi być wartością l-const odwołania, tak aby algorytm może przechowywać stanu dla przyszłych pętli do ponownego użycia.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_for_each"></a>  parallel_for_each  
 `parallel_for_each` stosuje funkcję do każdego elementu w zakresie, równolegle. Jest to równoważne semantycznie `for_each` działać w `std` przestrzeni nazw, z wyjątkiem tego iteracji w elementów jest wykonywane równolegle i kolejność iteracji jest nieokreślony. Argument `_Func` musi obsługiwać operator wywołania funkcji w formę `operator()(T)` gdzie parametr `T` jest typem elementu kontenera jest iterowane za pośrednictwem.  
  
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
 `_Iterator`  
 Typ iteratora używany do wykonywania iteracji kontenera.  
  
 `_Function`  
 Typ funkcji, które zostaną zastosowane do każdego elementu w ramach zakresu.  
  
 `_Partitioner`  
 `first`  
 Iteratora adresowania położenie pierwszego elementu do uwzględnienia w iteracji równoległych.  
  
 `last`  
 Iteratora adresowania pozycji w jeden element końcowego do uwzględnienia w iteracji równoległych.  
  
 `_Func`  
 Obiekt funkcji zdefiniowanej przez użytkownika, który jest stosowany do każdego elementu w zakresie.  
  
 `_Part`  
 Odwołanie do obiektu partycjonera. Argument może być jedną z `const` [auto_partitioner —](auto-partitioner-class.md)`&`, `const` [static_partitioner —](static-partitioner-class.md)`&`, `const` [simple_ partycjoner](simple-partitioner-class.md) `&` lub [affinity_partitioner —](affinity-partitioner-class.md) `&` Jeśli [affinity_partitioner —](affinity-partitioner-class.md) obiekt jest używany, odwołania musi być wartością l-const odwołania, tak aby algorytm może przechowywać stanu dla przyszłych pętli do ponownego użycia.  
  
### <a name="remarks"></a>Uwagi  
 [auto_partitioner —](auto-partitioner-class.md) będzie służyć do przeciążenia bez jawnego partycjonera.  
  
 Iteratory, które nie obsługują losowe dostępem tylko do [auto_partitioner —](auto-partitioner-class.md) jest obsługiwana.  
  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_invoke"></a>  parallel_invoke —  
 Wykonuje obiekty funkcji podana jako parametry w równolegle i bloków, dopóki nie zostało ukończone, wykonywania. Każdy obiekt funkcja może być wyrażenie lambda wskaźnika do funkcji, lub dowolnego obiektu spełniającego operator wywołania funkcji z podpisem `void operator()()`.  
  
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
 `_Function1`  
 Typ pierwszego obiektu funkcji ma być wykonywana równolegle.  
  
 `_Function2`  
 Typ drugi obiekt funkcji ma być wykonywana równolegle.  
  
 `_Function3`  
 Typ trzeciego obiekt funkcji ma być wykonywana równolegle.  
  
 `_Function4`  
 Typ czwartego obiekt funkcji ma być wykonywana równolegle.  
  
 `_Function5`  
 Typ piątego obiekt funkcji ma być wykonywana równolegle.  
  
 `_Function6`  
 Typ szóstego obiekt funkcji ma być wykonywana równolegle.  
  
 `_Function7`  
 Typ siódmego obiekt funkcji ma być wykonywana równolegle.  
  
 `_Function8`  
 Typ obiektu ósmego funkcji ma być wykonywana równolegle.  
  
 `_Function9`  
 Typ obiektu dziewiąty funkcji ma być wykonywana równolegle.  
  
 `_Function10`  
 Typ obiektu dziesiątego funkcji ma być wykonywana równolegle.  
  
 `_Func1`  
 Pierwszy obiekt funkcji ma być wykonywana równolegle.  
  
 `_Func2`  
 Drugi obiekt funkcji ma być wykonywana równolegle.  
  
 `_Func3`  
 Trzeci obiekt funkcji ma być wykonywana równolegle.  
  
 `_Func4`  
 Czwarty obiekt funkcji ma być wykonywana równolegle.  
  
 `_Func5`  
 Obiekt funkcji piątej ma być wykonywana równolegle.  
  
 `_Func6`  
 Obiekt funkcji szóstego ma być wykonywana równolegle.  
  
 `_Func7`  
 Obiekt funkcji siódmego ma być wykonywana równolegle.  
  
 `_Func8`  
 Obiekt funkcji ósmego ma być wykonywana równolegle.  
  
 `_Func9`  
 Obiekt funkcji dziewiąty ma być wykonywana równolegle.  
  
 `_Func10`  
 Obiekt funkcji dziesiątego ma być wykonywana równolegle.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że co najmniej jeden z obiektów funkcji dostarczone parametry mogą wykonać wbudowanego na kontekst wywołania.  
  
 Jeśli co najmniej jeden z obiektów funkcji przekazane jako parametry do tej funkcji zgłasza wyjątek, środowisko uruchomieniowe będzie wybierz jeden taki wyjątek jego wybieranie i Propaguj go poza wywołanie `parallel_invoke`.  
  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="parallel_radixsort"></a>  parallel_radixsort —  
 Rozmieszcza elementy w określonym zakresie z systemem innym niż malejącej przy użyciu podstawa, algorytm sortowania. Jest to funkcja stabilna sortowania, które wymaga funkcji projekcji, które można wyświetlać elementy, które można sortować według kluczy typu Liczba całkowita bez znaku. Inicjowanie domyślnych jest wymagana dla elementów sortowane.  
  
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
 `_Random_iterator`  
 Typ iteratora zakresu wejściowego.  
  
 `_Allocator`  
 Typ zgodny alokatora standardowa biblioteka C++.  
  
 `_Function`  
 Typ funkcji projekcji.  
  
 `_Begin`  
 Dostęp losowy iteratora adresowania położenie pierwszego elementu w zakresie ma zostać posortowana.  
  
 `_End`  
 Dostęp losowy iteratora adresowania poza ostatniego elementu w zakresie pozycji, co ma zostać posortowana.  
  
 `_Alloc`  
 Wystąpienie alokatora zgodne standardowa biblioteka C++.  
  
 `_Proj_func`  
 Obiekt funkcji projekcji zdefiniowanych przez użytkownika, który konwertuje element na wartość będącą liczbą całkowitą.  
  
 `_Chunk_size`  
 Rozmiar co najmniej fragment, do którego zostanie podzielony na dwa do wykonywania równoległego.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie przeciążenia wymagają `n * sizeof(T)` dodatkowe miejsce, gdy `n` jest liczba elementów, które mają być sortowane i `T` jest typ elementu. Obiekt projekcji jednoargumentowe z podpisem `I _Proj_func(T)` jest wymagany do zwracania klucza, gdy element, gdzie `T` jest typ elementu i `I` jest typem typu Liczba całkowita bez znaku.  
  
 Jeśli funkcja projekcji nie zostanie podana, funkcja projekcji domyślna, która po prostu zwraca element jest używany dla typów całkowitych. Funkcja nie będzie można skompilować, jeśli element nie jest typem wartości całkowitych w przypadku braku funkcji projekcji.  
  
 Jeśli nie podasz alokatora typ lub wystąpienie, alokatora standardowa biblioteka C++ `std::allocator<T>` służy do alokacji buforu.  
  
 Algorytm zakres wejściowy jest podzielony na dwie fragmentów i kolejno dzieli dwie fragmentów podrzędne wykonywanie równoległe każdego fragmentu. Opcjonalny argument `_Chunk_size` może służyć do wskazywania algorytm powinien obsługi fragmenty rozmiaru < `_Chunk_size` pojedynczo.  
  
##  <a name="parallel_reduce">parallel_reduce —</a>  
 Oblicza sumę wszystkich elementów w określonym zakresie przez obliczanie sum częściowych kolejnych lub oblicza wynik kolejne wyniki częściowe podobnie uzyskany przy użyciu określonej operacji binarnych sumą, równolegle. `parallel_reduce` przypomina semantycznie `std::accumulate`, ale wymaga operację binarną być asocjacyjnej i wymaga wartości tożsamości, zamiast wartości początkowej.  
  
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
 `_Forward_iterator`  
 Typ iteratora zakresu wejściowego.  
  
 `_Sym_reduce_fun`  
 Typ funkcji redukcji symetrycznego. Musi to być typ funkcji podpisem `_Reduce_type _Sym_fun(_Reduce_type, _Reduce_type)`, gdzie _Reduce_type jest taki sam jak typ tożsamości i typie wyniku zmniejszenia. Dla trzeciego przeciążenie to powinny być zgodne z typem danych wyjściowych `_Range_reduce_fun`.  
  
 `_Reduce_type`  
 Typ danych wejściowych zmniejszenia, który może być inny niż typ elementu wejściowego. Zwracana wartość i wartość tożsamości będzie ma tego typu.  
  
 `_Range_reduce_fun`  
 Typ funkcji zmniejszenie zakresu. Musi to być typ funkcji podpisem `_Reduce_type _Range_fun(_Forward_iterator, _Forward_iterator, _Reduce_type)`, _Reduce_type jest taki sam jak typ tożsamości i typie wyniku zmniejszenia.  
  
 `_Begin`  
 Iteratora wejściowych adresowania pierwszym elementem w zakresie należy zmniejszyć.  
  
 `_End`  
 Adresowanie element o jedną pozycję poza ostatniego elementu w zakresie zmniejszana iteratora wejściowych.  
  
 `_Identity`  
 Wartość tożsamości `_Identity` jest ten sam typ co typ wyniku zmniejszenia, a także `value_type` z iteratora dla pierwszego i drugiego przeciążeń. Dla trzeciego przeciążenia, muszą mieć ten sam typ co typ wyniku zmniejszenia wartości tożsamości, ale może różnić się od `value_type` z iteratora. Musi mieć odpowiednią wartość tak, aby operator zmniejszenie zakresu `_Range_fun`, gdy jest stosowany do zakresu określonego typu elementu `value_type` i wartość tożsamości zachowuje się jak rzutowanie typu wartości z typu `value_type` do typu tożsamości.  
  
 `_Sym_fun`  
 Funkcja symetrycznego używanego w ciągu sekundy ograniczenia. Aby uzyskać więcej informacji, zobacz uwagi.  
  
 `_Range_fun`  
 Funkcja, która będzie używana w pierwszej fazie ograniczenia. Aby uzyskać więcej informacji, zobacz uwagi.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik ograniczenia.  
  
### <a name="remarks"></a>Uwagi  
 Do wykonywania równoległego zmniejszenie, funkcja dzieli zakres fragmentów, w oparciu o liczbę procesów roboczych dostępne dla podstawowego harmonogramu. Zmniejszenie odbywa się w dwóch fazach, pierwszą fazę wykonuje zmniejszenia w ramach każdego fragmentu, a na drugim etapie wykonuje odstępu między częściowe wyniki każdego fragmentu.  
  
 Pierwszy przeciążenia wymaga, aby iteratora `value_type`, `T`, jest taka sama jak typ wartości tożsamości, a także do typu wyniku odstępu. Typ elementu T musi udostępniać operator `T T::operator + (T)` zmniejszenie elementów w każdego fragmentu. Ten sam podmiot jest używany na drugim etapie.  
  
 Drugi przeciążenia wymaga również, aby iteratora `value_type` taka sama jak typ wartości tożsamości, a także do typu wyniku odstępu. Dostarczony operator binarny `_Sym_fun` jest używany w obu fazach zmniejszenie wartości tożsamości jako początkowa wartość dla pierwszej fazy.  
  
 Dla trzeciego przeciążenia typ wartości tożsamości muszą być takie same jak typ wyniku redukcji, ale iteratora `value_type` mogą różnić się od obu. Funkcja zmniejszenie zakresu `_Range_fun` jest używany w pierwszej fazie o wartości tożsamości jako wartości początkowej, a funkcja binarnej `_Sym_reduce_fun` jest stosowany do sub wyników w drugim etapie.  
  
##  <a name="parallel_sort"></a>  parallel_sort —  
 Rozmieszcza elementy w określonym zakresie w kolejności nondescending lub zgodnie z kryterium porządkowania określony przez predykat binarnego, równolegle. Ta funkcja przypomina semantycznie `std::sort` w tym jest sortowania na podstawie porównania, niestabilny, w miejscu.  
  
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
 `_Random_iterator`  
 Typ iteratora zakresu wejściowego.  
  
 `_Function`  
 Typ obiekt porównanie binarne.  
  
 `_Begin`  
 Dostęp losowy iteratora adresowania położenie pierwszego elementu w zakresie ma zostać posortowana.  
  
 `_End`  
 Dostęp losowy iteratora adresowania poza ostatniego elementu w zakresie pozycji, co ma zostać posortowana.  
  
 `_Func`  
 Obiekt zdefiniowane przez użytkownika funkcja predykatu, który definiuje kryterium porównania muszą być spełnione przez kolejnych elementów w kolejności. Predykat binarne przyjmuje dwa argumenty i zwraca `true` po spełnieniu i `false` gdy nie są spełnione. Ta funkcja komparatora musi nakładają strict słabe porządkowanie dla pary elementów z sekwencji.  
  
 `_Chunk_size`  
 Rozmiar co najmniej fragment, do którego zostanie podzielony na dwa do wykonywania równoległego.  
  
### <a name="remarks"></a>Uwagi  
 Używa pierwszego przeciążenia binarne komparatora `std::less`.  
  
 Drugi przeciążony używa dostarczony komparatora binarny, który ma podpis `bool _Func(T, T)` gdzie `T` jest typ elementów w zakresie wejściowym.  
  
 Algorytm zakres wejściowy jest podzielony na dwie fragmentów i kolejno dzieli dwie fragmentów podrzędne wykonywanie równoległe każdego fragmentu. Opcjonalny argument `_Chunk_size` może służyć do wskazywania algorytm powinien obsługi fragmenty rozmiaru < `_Chunk_size` pojedynczo.  
  
##  <a name="parallel_transform"></a>  parallel_transform —  
 Dotyczy obiektu o określonej funkcji, do każdego elementu w zakresie źródła lub dwa elementy z dwóch zakresów i kopiuje zwracanych wartości obiektu funkcji do zakresu docelowego równolegle. Tym funkcjonalności jest semantycznie równoważne `std::transform`.  
  
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
 `_Input_iterator1`  
 Typ pierwszego lub tylko wejściowego iteratora.  
  
 `_Output_iterator`  
 Typ iteratora danych wyjściowych.  
  
 `_Unary_operator`  
 Typ obiekt jednoargumentowy wykonywanej na każdym elemencie zakresu wejściowego.  
  
 `_Input_iterator2`  
 Typ iteratora wejściowe drugiego.  
  
 `_Binary_operator`  
 Typ binarny obiekt parowania wykonane w przypadku elementów z dwóch zakresów.  
  
 `_Partitioner`  
 `first1`  
 Adresowanie położenie pierwszego elementu w pierwszy lub tylko zakres źródłowy działały na iteratora wejściowego.  
  
 `last1`  
 Adresowanie pozycji w jednym ostatniego elementu w pierwszy lub tylko zakres źródłowy działały na iteratora wejściowych.  
  
 `_Result`  
 Dane wyjściowe iteratora adresowania położenie pierwszego elementu w zakresie docelowym.  
  
 `_Unary_op`  
 Obiekt funkcja jednoargumentowy zdefiniowane przez użytkownika, który jest stosowane do każdego elementu w zakresie źródłowym.  
  
 `_Part`  
 Odwołanie do obiektu partycjonera. Argument może być jedną z `const` [auto_partitioner —](auto-partitioner-class.md)`&`, `const` [static_partitioner —](static-partitioner-class.md)`&`, `const` [simple_ partycjoner](simple-partitioner-class.md) `&` lub [affinity_partitioner —](affinity-partitioner-class.md) `&` Jeśli [affinity_partitioner —](affinity-partitioner-class.md) obiekt jest używany, odwołania musi być wartością l-const odwołania, tak aby algorytm może przechowywać stanu dla przyszłych pętli do ponownego użycia.  
  
 `first2`  
 Adresowanie położenie pierwszego elementu w zakresie drugiego źródła działały na iteratora wejściowego.  
  
 `_Binary_op`  
 Obiekt zdefiniowane przez użytkownika funkcja binarnej parowania, stosowany w kolejności do przodu, do dwóch zakresów.  
  
### <a name="return-value"></a>Wartość zwracana  
 Dane wyjściowe iteratora adresowania jedną pozycję poza ostatniego elementu w zakresie docelowym, który otrzymuje przekształcenia przez obiekt funkcji elementy danych wyjściowych.  
  
### <a name="remarks"></a>Uwagi  
 [auto_partitioner —](auto-partitioner-class.md) będzie służyć do przeciążenia bez argumentu partycjonera jawnego.  
  
 Iteratory, które nie obsługują losowe dostępem tylko do [auto_partitioner —](auto-partitioner-class.md) jest obsługiwana.  
  
 Przeciążeń, które przyjmują argument `_Unary_op` przekształcania, stosując obiekt jednoargumentowy do każdego elementu wejściowego zakresu zakres danych wyjściowych zakresu wejściowego. `_Unary_op` musi obsługiwać operator wywołania funkcji podpisem `operator()(T)` gdzie `T` jest typ wartości jest iterowane za pośrednictwem zakresu.  
  
 Przeciążeń, które przyjmują argument `_Binary_op` przekształcania dwa zakresy wejściowych zakresu danych wyjściowych przez zastosowanie binarny obiekt do jednego elementu z pierwszego zakresu wejściowego i jednego elementu z drugiego zakresu wejściowego. `_Binary_op` musi obsługiwać operator wywołania funkcji podpisem `operator()(T, U)` gdzie `T`, `U` typów wartości dwa Iteratory wejściowego.  
  
 Aby uzyskać więcej informacji, zobacz [algorytmy równoległe](../../../parallel/concrt/parallel-algorithms.md).  
  
##  <a name="receive"></a>  Odbieranie  
 Ogólny odbierać implementacji, umożliwiając kontekstu, poczekaj na danych z dokładnie jednego źródła i filtrowanie ich wartości, które są akceptowane.  
  
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
 `T`  
 Typ ładunku.  
  
 `_Src`  
 Wskaźnik lub odwołanie do źródła, z którego są oczekiwane dane.  
  
 `_Timeout`  
 Maksymalny czas dla którego metoda powinna danych, w milisekundach.  
  
 `_Filter_proc`  
 Funkcja filtr, który określa, czy wiadomości powinna być akceptowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość ze źródła, typ ładunku.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli parametr `_Timeout` ma wartość inną niż stała `COOPERATIVE_TIMEOUT_INFINITE`, wyjątek [operation_timed_out —](operation-timed-out-class.md) jest generowany po przekroczeniu określoną ilość czasu, zanim wiadomość zostanie odebrana. Jeśli chcesz zerowej długości przekroczenie limitu czasu, należy użyć [try_receive —](concurrency-namespace-functions.md) funkcji, w przeciwieństwie do wywoływania `receive` z limitem czasu równym `0` (zero), ponieważ jest bardziej wydajny i nie zgłasza wyjątków przekroczenia limitu czasu.  
  
 Aby uzyskać więcej informacji, zobacz [funkcji przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="run_with_cancellation_token"></a>  run_with_cancellation_token —  
 Wykonuje obiektem funkcji natychmiast w kontekście token danego anulowania.  
  
```
template<typename _Function>
void run_with_cancellation_token(
    const _Function& _Func,
    cancellation_token _Ct);
```  
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcja, która będzie wywołana.  
  
 `_Func`  
 Obiekt funkcja, która zostanie wykonana. Ten obiekt musi obsługiwać operator wywołania funkcji za pomocą podpisu void(void).  
  
 `_Ct`  
 Token anulowania, którego będzie kontrolował niejawne anulowania obiektu funkcji. Użyj `cancellation_token::none()` Jeśli funkcja wykonania bez możliwości niejawne odwołania w grupie zadań nadrzędnej anulowane.  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie punkty przerwania w obiekcie funkcja będzie wyzwalane, gdy `cancellation_token` została anulowana. Jawne token `_Ct` będzie izolować to `_Func` z anulowania nadrzędnego, jeśli element nadrzędny ma inny token lub nie tokenu.  
  
##  <a name="send">Wyślij</a>  
 Operacja synchroniczna wysyłania, która czeka, aż docelowy albo zaakceptuje lub odrzuci komunikat.  
  
```
template <class T>
bool send(_Inout_ ITarget<T>* _Trg, const T& _Data);

template <class T>
bool send(ITarget<T>& _Trg, const T& _Data);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ ładunku.  
  
 `_Trg`  
 Wskaźnik lub odwołanie do obiektu docelowego, do którego dane są wysyłane.  
  
 `_Data`  
 Odwołanie do danych do wysłania.  
  
### <a name="return-value"></a>Wartość zwracana  
 `true` Jeśli komunikat został zaakceptowany, `false` inaczej.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [funkcji przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="set_ambient_scheduler"></a>  set_ambient_scheduler —  
  
```
inline void set_ambient_scheduler(std::shared_ptr<::Concurrency::scheduler_interface> _Scheduler);
```  
  
### <a name="parameters"></a>Parametry  
 `_Scheduler`  
  
##  <a name="set_task_execution_resources"></a>  set_task_execution_resources —  
 Ogranicza wykonywania zasoby używane przez współbieżność środowiska wykonawczego wewnętrzny wątków na koligacji określony zestaw.  
  
 Jest on prawidłowy aby wywołać tę metodę, tylko przed utworzeniem Resource Manager lub między dwa okresy Menedżera zasobów. Go może być wywoływany wielokrotnie tak długo, jak Menedżer zasobów nie istnieje w tym czasie wywołania. Po ustawieniu limitu koligacji on obowiązuje aż do następnego wywołania prawidłowe `set_task_execution_resources` metody.  
  
 Podana maska koligacji nie musi być podzbiorem Maska koligacji procesu. Koligacja procesu zostanie zaktualizowany w razie potrzeby.  
  
```
void __cdecl set_task_execution_resources(
    DWORD_PTR _ProcessAffinityMask);

void __cdecl set_task_execution_resources(
    unsigned short count,
    PGROUP_AFFINITY _PGroupAffinity);
```  
  
### <a name="parameters"></a>Parametry  
 `_ProcessAffinityMask`  
 Maska koligacji, które mają być ograniczone do wątków roboczych współbieżność środowiska wykonawczego. Użyj tej metody w systemie z więcej niż 64 wątki sprzętu tylko wtedy, gdy chce się ograniczyć do podzbioru bieżącej grupy procesora współbieżności środowiska wykonawczego. Ogólnie rzecz biorąc należy używać wersji metody, która przyjmuje jako parametr, aby ograniczyć koligacji na maszynach z więcej niż 64 wątki sprzętu tablicę grupy koligacji.  
  
 `count`  
 Liczba `GROUP_AFFINITY` wpisów w tablicy określona przez parametr `_PGroupAffinity`.  
  
 `_PGroupAffinity`  
 Tablica `GROUP_AFFINITY` wpisów.  
  
### <a name="remarks"></a>Uwagi  
 Metoda zgłosi [invalid_operation —](invalid-operation-class.md) wyjątek, jeśli występuje w momencie jej wywoływanie, Menedżer zasobów i [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątek, jeśli określona koligacja wyników w pustym zestawem zasoby.  
  
 Wersja metody, która pobiera tablicę grupy koligacji, jako parametr tylko powinien być używany w systemach operacyjnych z wersji Windows 7 lub nowszej. W przeciwnym razie [invalid_operation —](invalid-operation-class.md) wyjątku.  
  
 Programowo modyfikowania koligacji procesu po ta metoda została wywołana nie spowoduje ponownej oceny koligacji, który jest ograniczona do Menedżera zasobów. W związku z tym wszystkie zmiany do przetworzenia koligacji należy przed wywołaniem tej metody.  
  
##  <a name="swap"></a>  Swap  
 Zamienia elementy dwóch `concurrent_vector` obiektów.  
  
```
template<typename T, class _Ax>
inline void swap(
    concurrent_vector<T, _Ax>& _A,
    concurrent_vector<T, _Ax>& _B);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych elementy przechowywane w równoczesnych wektory.  
  
 `_Ax`  
 Typ alokatora wektorów współbieżnych.  
  
 `_A`  
 Wektor równoczesnych, której elementy są wymienianych z tymi równoczesnych wektora `_B`.  
  
 `_B`  
 Równoczesnych wektora, zapewniając elementy zamianę lub wektora, której elementy są wymienianych z tymi równoczesnych wektora `_A`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja szablonu jest algorytm specjalizowany w klasie kontenera `concurrent_vector` można wykonać funkcji członkowskiej `_A`. [concurrent_vector::swap](concurrent-vector-class.md#swap)( `_B`). Te są wystąpieniami klasy częściowe porządkowanie szablonów funkcji przez kompilator. Gdy funkcje szablonów są przeciążone w taki sposób, dopasowania szablonu z wywołaniem funkcji nie jest unikatowa, kompilator wybierze najbardziej specjalna wersja funkcji szablonu. Ogólne wersja funkcji szablonu `template <class T> void swap(T&, T&)`, w algorytmie klasa działa przez przypisanie i jest wolne działanie. Specjalna wersja w poszczególnych kontenerach jest znacznie szybsze może współpracować z reprezentacji wewnętrznej klasy kontenera.  
  
 Ta metoda nie jest bezpieczne współbieżności. Należy się upewnić, że nie ma innych wątków są wykonywanie operacji na albo wektorów równoczesnych podczas wywoływania tej metody.  
  
##  <a name="task_from_exception">task_from_exception —</a>  
  
```
template<typename _TaskType, typename _ExType>
task<_TaskType> task_from_exception(
    _ExType _Exception,
    const task_options& _TaskOptions = task_options());
```  
  
### <a name="parameters"></a>Parametry  
 `_TaskType`  
 `_ExType`  
 `_Exception`  
 `_TaskOptions`  
  
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
 `T`  
 `_Param`  
 `_TaskOptions`  
  
### <a name="return-value"></a>Wartość zwracana  
  
##  <a name="trace_agents_register_name"></a>  Trace_agents_register_name  
 Kojarzy imię bloku komunikatów lub agenta w śledzenia zdarzeń systemu Windows.  
  
```
template <class T>
void Trace_agents_register_name(
    _Inout_ T* _PObject,
    _In_z_ const wchar_t* _Name);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ obiektu. Jest to zazwyczaj bloku komunikatów lub agenta.  
  
 `_PObject`  
 Wskaźnik do bloku komunikatów lub agenta o nazwie w śledzeniu.  
  
 `_Name`  
 Nazwa dla danego obiektu.  
  
##  <a name="try_receive"></a>  try_receive —  
 Ogólny spróbuj odbierania implementacji, umożliwiając kontekstu wyszukiwać dane z dokładnie jednego źródła i filtrowanie ich wartości, które są akceptowane. W przypadku danych nie jest gotowy, metoda zwraca wartość false.  
  
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
 `T`  
 Typ ładunku  
  
 `_Src`  
 Wskaźnik lub odwołanie do źródła, z którego są oczekiwane dane.  
  
 `_value`  
 Odwołanie do lokalizacji, w którym zostaną umieszczone wynik.  
  
 `_Filter_proc`  
 Funkcja filtr, który określa, czy wiadomości powinna być akceptowana.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `bool` wartość wskazującą, czy ładunku została umieszczona w `_value`.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [funkcji przekazywania wiadomości](../../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="wait"></a>  oczekiwania  
 Wstrzymuje bieżącego kontekstu dla określonego przedziału czasu.  
  
```
void __cdecl wait(unsigned int _Milliseconds);
```  
  
### <a name="parameters"></a>Parametry  
 `_Milliseconds`  
 Wyrażony w milisekundach czas, który bieżącego kontekstu powinny być wstrzymane dla. Jeśli `_Milliseconds` parametr ma ustawioną wartość `0`, bieżącego kontekstu należy użyć instrukcji yield wykonywania innych kontekstach do uruchomienia przed kontynuowaniem.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana w kontekście harmonogramu współbieżność środowiska wykonawczego, harmonogram zostanie znalezione inny kontekst do uruchomienia na podstawowych zasobów. Ponieważ planista współpracy charakter, tym kontekście nie można wznowić dokładnie po wyrażony w milisekundach czas określony. Jeśli harmonogram jest zajęty wykonywaniem innych zadań, które nie zwracają wspólnie do harmonogramu, może być nieograniczonego okresu oczekiwania.  
  
##  <a name="when_all"></a>  when_all —  
 Tworzy zadanie, które zostanie zakończony pomyślnie, gdy wszystkie zadania podana jako argumenty pomyślnie ukończona.  
  
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
 `_Iterator`  
 Typ iteratora wejściowego.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów do połączenia w zadaniu wynikowym.  
  
 `_End`  
 Pozycja pierwszego elementu poza zakres elementów do połączenia w zadaniu wynikowym.  
  
 `_TaskOptions`  
  
### <a name="return-value"></a>Wartość zwracana  
 Zadanie kończące pomyślnie, gdy wszystkie wejściowych zadania zostały ukończone pomyślnie. W przypadku wprowadzania zadania typu `T`, dane wyjściowe z tej funkcji będą `task<std::vector<T>>`. W przypadku wprowadzania zadania typu `void` dane wyjściowe zadania zostanie również `task<void>`.  
  
### <a name="remarks"></a>Uwagi  
 `when_all` to nieblokujące funkcja, która tworzy `task` wyniku. W odróżnieniu od [task::wait](task-class.md#wait), można bezpiecznie wywołanie tej funkcji w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA (STA aplikacji).  
  
 Jeśli jedno z zadań została anulowana lub zgłasza wyjątek, zadanie zwrócone ukończy wcześnie w stanie anulowane i, jeśli jest encoutered, zostanie wygenerowany wyjątek, jeśli wywołujesz [task::get](task-class.md#get) lub `task::wait` dla tego zadania.  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="when_any"></a>  when_any —  
 Tworzy zadanie, które zostanie zakończony pomyślnie, gdy zadań dostarczony jako argumenty zakończy się pomyślnie.  
  
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
 `_Iterator`  
 Typ iteratora wejściowego.  
  
 `_Begin`  
 Pozycja pierwszego elementu w zakresie elementów do połączenia w zadaniu wynikowym.  
  
 `_End`  
 Pozycja pierwszego elementu poza zakres elementów do połączenia w zadaniu wynikowym.  
  
 `_TaskOptions`  
 `_CancellationToken`  
 Token anulowania, który kontroluje anulowania zwrócone zadania. Jeśli nie podasz token anulowania, wynikowy zadania zostanie wyświetlony token anulowania zadania, które powoduje jej zakończenie.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zadanie, które zostanie wykonane pomyślnie, jeśli dowolny wejściowych zadania zostało ukończone pomyślnie. W przypadku wprowadzania zadania typu `T`, dane wyjściowe z tej funkcji będą `task<std::pair<T, size_t>>>`, gdzie pierwszy element pary jest wynik Kończenie zadań, a drugi element jest indeks zadania, które zostało zakończone. W przypadku wprowadzania zadania typu `void` dane wyjściowe `task<size_t>`, której wynikiem jest indeks Kończenie zadań.  
  
### <a name="remarks"></a>Uwagi  
 `when_any` to nieblokujące funkcja, która tworzy `task` wyniku. W odróżnieniu od [task::wait](task-class.md#wait), można bezpiecznie wywołanie tej funkcji w aplikacji platformy uniwersalnej systemu Windows w wątku ASTA (STA aplikacji).  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
