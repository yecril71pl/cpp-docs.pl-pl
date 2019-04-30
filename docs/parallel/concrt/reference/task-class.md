---
title: task — Klasa (współbieżność środowiska wykonawczego)
ms.date: 11/04/2016
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
helpviewer_keywords:
- task class
ms.assetid: cdc3a8c0-5cbe-45a0-b5d5-e9f81d94df1a
ms.openlocfilehash: 99676ac0fff9584cd8453562f8918f6cadd66666
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385209"
---
# <a name="task-class-concurrency-runtime"></a>task — Klasa (współbieżność środowiska wykonawczego)

Biblioteka równoległych wzorców (PPL) `task` klasy. A `task` obiekt reprezentuje prac, które mogą być wykonywane asynchronicznie, a równocześnie z innymi zadaniami i w środowisku uruchomieniowym współbieżności: pracy równoległej produkowane przez algorytmy równoległe. Daje wynik o typie `_ResultType` po pomyślnym ukończeniu. Zadania typu `task<void>` nie generują żadnego wyniku. Zadanie można wstrzymywać i anulować niezależnie od innych zadań. Może również składać z innymi zadaniami za pomocą kontynuacji ( `then`) i sprzężenia ( `when_all`) i wyboru ( `when_any`) wzorców.

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

*T*<br/>
Typ obiektu zadania.

*_ReturnType*<br/>
Typ wyniku tego zadania.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`result_type`|Typ wyniku tworzy obiekt tej klasy.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Zadanie](#ctor)|Przeciążone. Konstruuje `task` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Przeciążone. Zwraca wynik tego zadania. Jeśli zadanie nie jest w terminalu, stan, wywołanie `get` będzie czekać na zakończenie zadania. Ta metoda nie zwraca wartości, gdy jest wywoływana w zadaniu o `result_type` z `void`.|
|[is_apartment_aware](#is_apartment_aware)|Określa, czy zadanie dekoduje środowiska uruchomieniowego Windows `IAsyncInfo` interfejsu, lub czy wywodzi się z takiego zadania.|
|[is_done](#is_done)|Określa, jeśli zadanie zostało ukończone.|
|[scheduler](#scheduler)|Zwraca harmonogram tego zadania|
|[Następnie](#then)|Przeciążone. Dodaje zadanie kontynuacji do wykonania takiego zadania.|
|[Czekaj](#wait)|Czeka, aż zadanie osiągnie stan końcowy. Możliwe jest `wait` do wykonywania zadań w tekście, jeśli spełnione są wszystkie współzależności zadań i jej nie już zostało odebrane do wykonania przez pracownika tła.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Przeciążone. Określa, czy dwa `task` obiekty reprezentują różne zadania wewnętrzne.|
|[operator=](#operator_eq)|Przeciążone. Zastępuje zawartość jednego `task` obiektu na inny.|
|[operator==](#operator_eq_eq)|Przeciążone. Określa, czy dwa `task` obiekty reprezentują te same zadania wewnętrzne.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks.h

**Namespace:** współbieżności

##  <a name="get"></a> Pobierz

Zwraca wynik tego zadania. Jeśli zadanie nie jest w terminalu, stan, wywołanie `get` będzie czekać na zakończenie zadania. Ta metoda nie zwraca wartości, gdy jest wywoływana w zadaniu o `result_type` z `void`.

```
_ReturnType get() const;

void get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wynik zadania.

### <a name="remarks"></a>Uwagi

Jeśli zadanie zostanie anulowane, wywołanie `get` zgłosi [task_canceled](task-canceled-class.md) wyjątku. Jeśli zadanie napotkało inny wyjątek lub wyjątek został rozpropagowany do niego z poprzedzającego zadania, wywołanie `get` spowoduje zgłoszenie tego wyjątku.

> [!IMPORTANT]
>  W aplikacji platformy uniwersalnej Windows (UWP), nie należy wywoływać metody [CONCURRENCY::Task](#wait) lub `get` ( `wait` wywołania `get`) w kodzie, który jest uruchamiany na wątku interfejsu użytkownika. W przeciwnym wypadku środowisko wykonawcze zgłasza [concurrency::invalid_operation](invalid-operation-class.md) ponieważ te metody blokują bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Jednak można wywoływać `get` metodę do uzyskania wyniku zadania poprzedzającego w kontynuacji opartej na zadaniach, ponieważ wynik jest natychmiast dostępna.

##  <a name="is_apartment_aware"></a> is_apartment_aware —

Określa, czy zadanie dekoduje środowiska uruchomieniowego Windows `IAsyncInfo` interfejsu, lub czy wywodzi się z takiego zadania.

```
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli zadanie dekoduje `IAsyncInfo` interfejsu, lub czy wywodzi się z takiego zadania **false** inaczej.

##  <a name="is_done"></a>  Task::is_done — metoda (współbieżność środowiska wykonawczego)

Określa, jeśli zadanie zostało ukończone.

```
bool is_done() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli zadanie zostało ukończone, wartość false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Funkcja zwraca wartość true, jeśli zadanie jest ukończone lub anulowane (z wyjątkiem użytkownika lub bez).

##  <a name="operator_neq"></a> operator! =

Określa, czy dwa `task` obiekty reprezentują różne zadania wewnętrzne.

```
bool operator!= (const task<_ReturnType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zadanie do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty odnoszą się do różnych zadań podstawowych, a **false** inaczej.

##  <a name="operator_eq"></a> operator =

Zastępuje zawartość jednego `task` obiektu na inny.

```
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
Źródło `task` obiektu.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Jako `task` zachowuje się jak wskaźnik inteligentny, po przydzieleniu kopii to `task` obiektów reprezentuje to samo zadanie rzeczywiste `_Other` jest.

##  <a name="operator_eq_eq"></a> operator ==

Określa, czy dwa `task` obiekty reprezentują te same zadania wewnętrzne.

```
bool operator== (const task<_ReturnType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zadanie do porównania.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekty odnoszą się do tego samego zadania podstawowego, a **false** inaczej.

##  <a name="scheduler"></a>  Task::Scheduler — metoda (współbieżność środowiska wykonawczego)

Zwraca harmonogram tego zadania

```
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do harmonogramu

##  <a name="ctor"></a> Zadanie

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

*T*<br/>
Typ parametru, z którego ma zostać skonstruowane zadanie.

*_Param*<br/>
Parametr, z którego ma zostać skonstruowane zadanie. Może to być wyrażenie lambda, obiektów funkcyjnych `task_completion_event<result_type>` obiektu lub interfejs Windows::Foundation:: iasyncinfo, jeśli używasz zadań w aplikacji środowiska wykonawczego Windows. Obiekt wyrażenia lambda lub funkcji powinien być typem równoważnym z `std::function<X(void)>`, gdzie X może być zmienną typu `result_type`, `task<result_type>`, lub interfejs Windows::Foundation:: iasyncinfo w aplikacjach Windows Runtime.

*_TaskOptions*<br/>
Opcje zadania obejmują token anulowania, harmonogram itp.

*_Inne*<br/>
Źródło `task` obiektu.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor dla `task` tylko znajduje się w celu umożliwienia zadań, które jest używane w kontenerach. Nie można użyć zadanie domyślne, dopóki nie zostanie przypisana do niego prawidłowego zadania. Metody takie jak `get`, `wait` lub `then` zgłosi [invalid_argument](../../../standard-library/invalid-argument-class.md) wyjątek przy wywołaniu nad zadaniem domyślne.

Zadanie, które jest tworzona na podstawie `task_completion_event` zostanie ukończone (i mają jego kontynuacje zostaną zaplanowane) po ustawieniu zdarzenia zakończenia zadania.

Wersja Konstruktor, który pobiera token anulowania, tworzy zadanie, które można anulować przy użyciu `cancellation_token_source` otrzymanego tokenu. Zadań utworzonych bez tokenu anulowania nie są można anulować.

Zadania utworzone z `Windows::Foundation::IAsyncInfo` interfejsu lub wyrażenia lambda, która zwraca `IAsyncInfo` interfejsu osiągają swój stan końcowy, po ukończeniu operacji asynchronicznej środowiska wykonawczego Windows zamknięte lub akcji. Podobnie, zadania utworzone z wyrażenia lambda, która zwraca `task<result_type>` osiągają swój stan końcowy, gdy zadanie wewnętrzne osiągnie swój stan końcowy, a nie w przypadku, gdy wyrażenie lambda zwraca.

`task` zachowuje się jak inteligentny wskaźnik i można bezpiecznie przekazywać go przez wartość. Może zostać oceniony przez wiele wątków, bez potrzeby blokad.

Przeciążenia konstruktora, które przyjmują interfejs Windows::Foundation:: iasyncinfo lub wyrażenia lambda zwraca ten interfejs, są dostępne tylko dla aplikacji środowiska wykonawczego Windows.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="then"></a> Następnie

Dodaje zadanie kontynuacji do wykonania takiego zadania.

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

*_Function*<br/>
Typ obiektu funkcji, która zostanie wywołany przez to zadanie.

*_Func*<br/>
Funkcja kontynuacji do wykonania po zakończeniu tego zadania. Ta funkcja kontynuacji musi przyjmować jako dane wejściowe zmienną `result_type` lub `task<result_type>`, gdzie `result_type` jest typ wyniku tego zadania.

*_TaskOptions*<br/>
Opcje zadania obejmują anulowania tokenu, harmonogram i kontekst kontynuacji. Domyślnie poprzednie 3 opcje są dziedziczone od zadania poprzedzającego

*_CancellationToken*<br/>
Token anulowania do skojarzenia z zadaniem kontynuacji. Zadanie kontynuacji, który jest tworzony bez tokena odwołania, będzie dziedziczyć token zadania poprzedzającego.

*_ContinuationContext*<br/>
Zmienna, która określa, gdzie należy realizować kontynuację. Ta zmienna jest przydatna, gdy są używane w aplikacji platformy uniwersalnej systemu Windows. Aby uzyskać więcej informacji, zobacz [task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Wartość zwracana

Nowo utworzone zadanie kontynuacji. Typ wyniku zwracanego zadania jest określana przez wartość, jaką `_Func` zwraca.

### <a name="remarks"></a>Uwagi

Przeciążenia `then` , wyrażenia lambda lub funktora zwracającego interfejs Windows::Foundation:: iasyncinfo, są dostępne tylko dla aplikacji środowiska wykonawczego Windows.

Aby uzyskać więcej informacji na temat sposobu używania kontynuacji zadań do redagowania prac asynchronicznych, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

##  <a name="wait"></a> Czekaj

Czeka, aż zadanie osiągnie stan końcowy. Możliwe jest `wait` do wykonywania zadań w tekście, jeśli spełnione są wszystkie współzależności zadań i jej nie już zostało odebrane do wykonania przez pracownika tła.

```
task_status wait() const;
```

### <a name="return-value"></a>Wartość zwracana

A `task_status` wartość, która może być `completed` lub `canceled`. Jeśli zadanie napotkało wyjątek podczas wykonywania lub wyjątek został rozpropagowany do niego z poprzedzającego zadania, `wait` spowoduje zgłoszenie tego wyjątku.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
>  W aplikacji platformy uniwersalnej Windows (UWP), nie należy wywoływać metody `wait` w kodzie, który jest uruchamiany na wątku interfejsu użytkownika. W przeciwnym wypadku środowisko wykonawcze zgłasza [concurrency::invalid_operation](invalid-operation-class.md) , ponieważ ta metoda blokują bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Jednak można wywoływać [CONCURRENCY::Task:: GET](#get) metodę do uzyskania wyniku zadania poprzedzającego w kontynuacji opartej na zadaniach.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
