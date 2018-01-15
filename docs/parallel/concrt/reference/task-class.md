---
title: "Task — klasa (współbieżność środowiska wykonawczego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- task
- PPLTASKS/concurrency::task
- PPLTASKS/concurrency::task::task
- PPLTASKS/concurrency::task::get
- PPLTASKS/concurrency::task::is_apartment_aware
- PPLTASKS/concurrency::task::is_done
- PPLTASKS/concurrency::task::scheduler
- PPLTASKS/concurrency::task::then
- PPLTASKS/concurrency::task::wait
dev_langs: C++
helpviewer_keywords: task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4ea618ca6a5784b44666c70d79bb10b2e9f6e394
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="task-class-concurrency-runtime"></a>task — Klasa (współbieżność środowiska wykonawczego)
Biblioteka równoległych wzorców (PLL) `task` klasy. A `task` obiekt reprezentuje pracy, które mogą być wykonywane asynchronicznie, a równocześnie z innymi zadaniami i współbieżność środowiska wykonawczego pracy równoległej utworzonych przez algorytmy równoległe. Tworzy wynik typu `_ResultType` na pomyślne zakończenie. Zadania typu `task<void>` utworzyć żadnego wyniku. Zadania można czas potrzebny na i anulowane niezależnie od innych zadań. Mogą być składane również z innymi zadaniami za pomocą kontynuacje ( `then`), a sprzężenia ( `when_all`) i wyboru ( `when_any`) wzorce.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T>
class task;

template <>
class task<void>;

template<typename _ReturnType>
class task;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 `T`  
 `_ReturnType`  
 Typ wyniku tego zadania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`result_type`|Typ wyniku tworzy obiekt tej klasy.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[zadanie](#ctor)|Przeciążone. Konstruuje `task` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[get](#get)|Przeciążone. Zwraca wynik tego zadania utworzone. Jeśli zadanie nie jest w terminalu, stan, wywołanie `get` będzie czekać na zakończenie zadania. Ta metoda nie zwraca wartości, gdy jest wywoływana dla zadania z `result_type` z `void`.|  
|[is_apartment_aware](#is_apartment_aware)|Określa, czy zadanie dekoduje Windows Runtime `IAsyncInfo` interfejsu lub podrzędne takich zadań.|  
|[is_done](#is_done)|Określa, czy zadanie zostało ukończone.|  
|[Harmonogram](#scheduler)|Zwraca harmonogramu dla tego zadania|  
|[następnie](#then)|Przeciążone. Dodaje zadania kontynuacji do tego zadania.|  
|[oczekiwania](#wait)|Czeka na to zadanie do przejścia terminala. Istnieje możliwość `wait` do wykonania zadania w tekście, jeśli spełnione są wszystkie zależności zadania i jego ma nie już pobrane do wykonania w tle proces roboczy.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Przeciążone. Określa, czy dwa `task` reprezentować różnych zadań wewnętrznych.|  
|[operator =](#operator_eq)|Przeciążone. Zastępuje zawartość jednej `task` obiekt z inną.|  
|[operator ==](#operator_eq_eq)|Przeciążone. Określa, czy dwa `task` obiekty reprezentują tego samego zadania wewnętrznego.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `task`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ppltasks.h  
  
 **Namespace:** współbieżności  
  
##  <a name="get"></a>Pobierz 

 Zwraca wynik tego zadania utworzone. Jeśli zadanie nie jest w terminalu, stan, wywołanie `get` będzie czekać na zakończenie zadania. Ta metoda nie zwraca wartości, gdy jest wywoływana dla zadania z `result_type` z `void`.  
  
```
_ReturnType get() const;

void get() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynik zadania.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli zadanie zostało anulowane, wywołanie `get` zgłosi [task_canceled —](task-canceled-class.md) wyjątku. Jeśli zadanie napotkał wyjątek różnych lub wyjątek pochodzi z antecedent do niego task, wywołanie `get` zgłosi ten wyjątek.  
  
> [!IMPORTANT]
>  W [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] aplikacji, nie należy wywoływać [concurrency::task::wait](#wait) lub `get` ( `wait` wywołania `get`) w kodzie, który jest uruchamiany na pozostaje tryb komórek jednowątkowych W przeciwnym razie zwraca środowiska uruchomieniowego [concurrency::invalid_operation](invalid-operation-class.md) ponieważ metody te zablokować bieżącego wątku i może spowodować, że aplikacja przestanie odpowiadać. Jednak możesz wywołać `get` metodę, aby odbierać wynik zadania poprzedzających kontynuację opartego na zadaniach, ponieważ wynik jest natychmiast dostępna.  
  
##  <a name="is_apartment_aware"></a>is_apartment_aware 

 Określa, czy zadanie dekoduje Windows Runtime `IAsyncInfo` interfejsu lub podrzędne takich zadań.  
  
```
bool is_apartment_aware() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli zadanie odkodowuje `IAsyncInfo` interfejsu lub podrzędne takich zadań `false` inaczej.  
  
##  <a name="is_done"></a>Task::is_done — metoda (współbieżność środowiska wykonawczego)  
 Określa, czy zadanie zostało ukończone.  
  
```
bool is_done() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość true, jeśli zadanie zostało ukończone, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwraca wartość true, jeśli zadanie zostało zakończone lub anulowane (z lub bez wyjątku użytkownika).  
  
##  <a name="operator_neq"></a>operator! = 

 Określa, czy dwa `task` reprezentować różnych zadań wewnętrznych.  
  
```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekty odwołują się do różnych zadań podstawowej, a `false` inaczej.  
  
##  <a name="operator_eq"></a>operator = 

 Zastępuje zawartość jednej `task` obiekt z inną.  
  
```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 Źródło `task` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
  
### <a name="remarks"></a>Uwagi  
 Jako `task` zachowuje się jak wskaźnika inteligentnego, po przypisaniu kopiowania to `task` obiektów reprezentuje to samo zadanie rzeczywiste `_Other` jest.  
  
##  <a name="operator_eq_eq"></a>operator == 

 Określa, czy dwa `task` obiekty reprezentują tego samego zadania wewnętrznego.  
  
```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```  
  
### <a name="parameters"></a>Parametry  
 `_Rhs`  
  
### <a name="return-value"></a>Wartość zwracana  
 `true`Jeśli obiekty odwołują się do tego samego zadania podstawowej i `false` inaczej.  
  
##  <a name="scheduler"></a>Task::Scheduler — metoda (współbieżność środowiska wykonawczego)  
 Zwraca harmonogramu dla tego zadania  
  
```
scheduler_ptr scheduler() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do harmonogramu  
  
##  <a name="ctor"></a>zadanie 

 Konstruuje `task` obiektu.  
  
```
task();

template<typename T>
__declspec(
    noinline) explicit task(T _Param);

template<typename T>
__declspec(
    noinline) explicit task(T _Param, const task_options& _TaskOptions);

task(
    const task& _Other);

task(
    task&& _Other);
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ parametru, z którego ma zostać wykonane zadanie.  
  
 `_Param`  
 Parametr, z którego ma zostać wykonane zadanie. Może to być wyrażenie lambda obiektem funkcji `task_completion_event<result_type>` obiektu lub Windows::Foundation::IAsyncInfo, korzystając z zadania w aplikacji ze Sklepu Windows. Obiekt lambda lub funkcja powinien być typem odpowiednikiem `std::function<X(void)>`, gdzie X może być zmienną typu `result_type`, `task<result_type>`, lub Windows::Foundation::IAsyncInfo w aplikacjach w Sklepie Windows.  
  
 `_TaskOptions`  
 Dostępne są następujące opcje zadania harmonogramu tokenem anulowania itp.  
  
 `_Other`  
 Źródło `task` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Domyślny konstruktor `task` występuje tylko w celu umożliwienia zadań do użycia w kontenerach. Nie można użyć zadania wykonane domyślne, dopóki nie zostanie przypisana do niego prawidłowe zadanie. Metody, takie jak `get`, `wait` lub `then` zgłosi [invalid_argument —](../../../standard-library/invalid-argument-class.md) wyjątku, gdy wywołać dla zadania domyślne skonstruowany.  
  
 Zadanie, które jest tworzona na podstawie `task_completion_event` ukończy (i jego kontynuacje zaplanowane), gdy zdarzenie ukończenia zadań jest ustawiona.  
  
 Wersja Konstruktor, który pobiera token anulowania tworzy zadanie, które mogą zostać anulowane przy użyciu `cancellation_token_source` token został uzyskany. Nie są można anulować zadania utworzone bez token anulowania.  
  
 Zadania utworzone na podstawie `Windows::Foundation::IAsyncInfo` interfejsu lub wyrażenie lambda, która zwraca `IAsyncInfo` interfejsu przejścia ich terminali po zakończeniu objętego operację asynchroniczną środowiska wykonawczego systemu Windows lub akcji. Podobnie, zadania utworzone na podstawie lambda, która zwraca `task<result_type>` przejścia ich terminali wewnętrzny zadań osiągnie stanu terminali, a nie zwraca lambda.  
  
 `task`zachowuje się jak wskaźnika inteligentnego i bezpiecznie przekazać wokół przez wartość. Są dostępne przez wiele wątków bez konieczności blokad.  
  
 Przeciążeń konstruktora, które przyjmują interfejsu Windows::Foundation::IAsyncInfo lub wyrażenia lambda zwracanie interfejsu, są dostępne tylko do aplikacji ze Sklepu Windows.  
  
 Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="then"></a>następnie 

 Dodaje zadania kontynuacji do tego zadania.  
  
```
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ReturnType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions = task_options()) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    void>::_TaskOfType;
```   
  
### <a name="parameters"></a>Parametry  
 `_Function`  
 Typ obiektu funkcja, która zostanie wywołana przez to zadanie.  
  
 `_Func`  
 Funkcja kontynuacji do wykonania po zakończeniu zadania. Ta funkcja kontynuacji musi przyjmować jako danych wejściowych zmiennej albo `result_type` lub `task<result_type>`, gdzie `result_type` jest typ wyniku to zadanie tworzy.  
  
 `_TaskOptions`  
 Opcje zadania obejmują token, harmonogram i kontynuacji kontekst anulowania. Domyślnie wcześniejsze 3 opcje są dziedziczone z poprzedzających zadań  
  
 `_CancellationToken`  
 Token anulowania do skojarzenia z zadania kontynuacji. Utworzony bez token anulowania zadania kontynuacji będzie dziedziczyć token poprzedzających zadania.  
  
 `_ContinuationContext`  
 Zmienna, która określa, gdzie powinien zostać wykonany kontynuacji. Ta zmienna jest przydatna w stylu aplikacji ze Sklepu Windows. Aby uzyskać więcej informacji, zobacz [task_continuation_context —](task-continuation-context-class.md)  
  
### <a name="return-value"></a>Wartość zwracana  
 Zadania kontynuacji nowo utworzony. Typ wyniku zwrócone zadania jest określany przez co `_Func` zwraca.  
  
### <a name="remarks"></a>Uwagi  
 Przeciążeń `then` który lambda lub obiekt, który zwraca interfejs Windows::Foundation::IAsyncInfo, są dostępne tylko dla aplikacji ze Sklepu Windows.  
  
 Aby uzyskać więcej informacji na temat korzystania z zadań kontynuacje utworzenie asynchroniczne, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).  
  
##  <a name="wait"></a>oczekiwania 

 Czeka na to zadanie do przejścia terminala. Istnieje możliwość `wait` do wykonania zadania w tekście, jeśli spełnione są wszystkie zależności zadania i jego ma nie już pobrane do wykonania w tle proces roboczy.  
  
```
task_status wait() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `task_status` wartość, która może być albo `completed` lub `canceled`. Zadania wystąpił wyjątek podczas wykonywania, czy wyjątek pochodzi z poprzedzających zadania do niego `wait` zgłosi ten wyjątek.  
  
### <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  W [!INCLUDE[win8_appname_long](../../../build/includes/win8_appname_long_md.md)] aplikacji, nie należy wywoływać `wait` w kodzie, który jest uruchamiany na pozostaje tryb komórek jednowątkowych W przeciwnym razie zwraca środowiska uruchomieniowego [concurrency::invalid_operation](invalid-operation-class.md) , ponieważ ta metoda umożliwia blokowanie bieżącego wątku i może spowodować, że aplikacja przestanie odpowiadać. Jednak możesz wywołać [concurrency::task::get](#get) metodę, aby odbierać wynik zadania poprzedzających kontynuację opartego na zadaniach.  
  
## <a name="see-also"></a>Zobacz też  
 [Przestrzeń nazw współbieżności](concurrency-namespace.md)
