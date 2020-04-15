---
title: task — Klasa (współbieżność środowiska wykonawczego)
ms.date: 07/30/2019
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
ms.openlocfilehash: d42c7fbd3e065fc295027b7c56e207b2a49221bb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358736"
---
# <a name="task-class-concurrency-runtime"></a>task — Klasa (współbieżność środowiska wykonawczego)

Klasa Biblioteka wzorców równoległych `task` (PPL). Obiekt `task` reprezentuje pracę, która może być wykonywana asynchronicznie i jednocześnie z innymi zadaniami i pracy równoległej produkowane przez algorytmy równoległe w współbieżności środowiska wykonawczego. Daje wynik typu `_ResultType` po pomyślnym zakończeniu. Zadania typu `task<void>` nie dają żadnych rezultatów. Zadanie można czekać i anulować niezależnie od innych zadań. Może być również składa się z `then`innych zadań `when_all`za pomocą `when_any`kontynuacji( ), i połączyć( ) i wybór( ) wzory. Gdy obiekt zadania jest przypisany do nowej zmiennej, zachowanie jest zachowanie ; `std::shared_ptr` innymi słowy, oba obiekty reprezentują to samo zadanie podstawowe.

## <a name="syntax"></a>Składnia

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ wyniku, który tworzy zadanie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`result_type`|Typ wyniku obiekt tej klasy produkuje.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[task](#ctor)|Przeciążone. Konstruuje `task` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Przeciążone. Zwraca wynik tego zadania produkowane. Jeśli zadanie nie jest w stanie terminalu, wywołanie `get` będzie czekać na zakończenie zadania. Ta metoda nie zwraca wartości, gdy wywoływane na zadanie `result_type` z . `void`|
|[is_apartment_aware](#is_apartment_aware)|Określa, czy zadanie odkręca interfejs `IAsyncInfo` środowiska wykonawczego systemu Windows, czy pochodzi z takiego zadania.|
|[is_done](#is_done)|Określa, czy zadanie zostało ukończone.|
|[Harmonogram](#scheduler)|Zwraca harmonogram dla tego zadania|
|[Następnie](#then)|Przeciążone. Dodaje zadanie kontynuacji do tego zadania.|
|[Czekać](#wait)|Czeka na to zadanie, aby osiągnąć stan terminalu. Jest możliwe `wait` do wykonania zadania wbudowanego, jeśli wszystkie zależności zadań są spełnione i nie został już pobrany do wykonania przez pracownika w tle.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator!=](#operator_neq)|Przeciążone. Określa, czy `task` dwa obiekty reprezentują różne zadania wewnętrzne.|
|[operator=](#operator_eq)|Przeciążone. Zastępuje zawartość jednego `task` obiektu innym.|
|[operator==](#operator_eq_eq)|Przeciążone. Określa, czy `task` dwa obiekty reprezentują to samo zadanie wewnętrzne.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks.h

**Przestrzeń nazw:** współbieżność

## <a name="get"></a><a name="get"></a>Pobierz

Zwraca wynik tego zadania produkowane. Jeśli zadanie nie jest w stanie terminalu, wywołanie `get` będzie czekać na zakończenie zadania. Ta metoda nie zwraca wartości, gdy wywoływane na zadanie `result_type` z . `void`

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wynik zadania.

### <a name="remarks"></a>Uwagi

Jeśli zadanie zostanie anulowane, `get` wywołanie zda wyjątek [task_canceled.](task-canceled-class.md) Jeśli zadanie napotkał inny wyjątek lub wyjątek został propagowany do niego z `get` zadania poprzedzago, wywołanie zgłosić ten wyjątek.

> [!IMPORTANT]
> W aplikacji platformy uniwersalnej systemu Windows (UWP) nie należy wywoływać `get` [współbieżności::task::wait](#wait) lub ( `wait` wywołania `get`) w kodzie uruchamianym w wątku interfejsu użytkownika. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność::invalid_operation](invalid-operation-class.md) ponieważ te metody blokują bieżący wątek i mogą spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać `get` metodę, aby otrzymać wynik zadania poprzedzago w kontynuacji opartej na zadaniach, ponieważ wynik jest natychmiast dostępny.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

Określa, czy zadanie odkręca interfejs `IAsyncInfo` środowiska wykonawczego systemu Windows, czy pochodzi z takiego zadania.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli zadanie odwija `IAsyncInfo` interfejs lub pochodzi z takiego zadania, **false** inaczej.

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>zadanie::metoda is_done (środowisko uruchomieniowe współbieżności)

Określa, czy zadanie zostało ukończone.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość true, jeśli zadanie zostało ukończone, false inaczej.

### <a name="remarks"></a>Uwagi

Funkcja zwraca wartość true, jeśli zadanie zostało ukończone lub anulowane (z wyjątkiem użytkownika lub bez niego).

## <a name="operator"></a><a name="operator_neq"></a>operator!=

Określa, czy `task` dwa obiekty reprezentują różne zadania wewnętrzne.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zadanie do porównania.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekty odnoszą się do różnych podstawowych zadań i **false** w przeciwnym razie.

## <a name="operator"></a><a name="operator_eq"></a>operator=

Zastępuje zawartość jednego `task` obiektu innym.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt `task` źródłowy.

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Jak `task` zachowuje się jak inteligentny wskaźnik, po `task` przypisaniu kopii, `_Other` ten obiekt reprezentuje to samo zadanie rzeczywiste, jak nie.

## <a name="operator"></a><a name="operator_eq_eq"></a>operator==

Określa, czy `task` dwa obiekty reprezentują to samo zadanie wewnętrzne.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zadanie do porównania.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekty odnoszą się do tego samego zadania źródłowego i **false** w przeciwnym razie.

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>zadanie::metoda harmonogramu (środowisko uruchomieniowe współbieżności)

Zwraca harmonogram dla tego zadania

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do harmonogramu

## <a name="task"></a><a name="ctor"></a>Zadanie

Konstruuje `task` obiekt.

```cpp
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
Parametr, z którego ma zostać skonstruowane zadanie. Może to być lambda, obiekt `task_completion_event<result_type>` funkcji, obiekt lub windows::Foundation::IAsyncInfo, jeśli używasz zadań w aplikacji środowiska wykonawczego systemu Windows. Obiekt lambda lub funkcji powinien być `std::function<X(void)>`typem równoważnym , `result_type`gdzie `task<result_type>`X może być zmienną typu, lub Windows::Foundation::IAsyncInfo w aplikacjach środowiska wykonawczego systemu Windows.

*_TaskOptions*<br/>
Opcje zadania obejmują token anulowania, harmonogram itp.

*_Other*<br/>
Obiekt `task` źródłowy.

### <a name="remarks"></a>Uwagi

Domyślny konstruktor `task` dla a jest obecny tylko w celu umożliwienia wykonywania zadań w kontenerach. Domyślne zadanie skonstruowane nie może być używane, dopóki nie zostanie mu przypisane prawidłowe zadanie. Metody, `get`takie `wait` `then` jak , lub zrzucą [wyjątek invalid_argument,](../../../standard-library/invalid-argument-class.md) gdy jest wywoływana w domyślnym zadaniu skonstruowanym.

Zadanie, które jest `task_completion_event` tworzone z will zakończyć (i jego kontynuacje zaplanowane) po ustawieniu zdarzenia ukończenia zadania.

Wersja konstruktora, który przyjmuje token anulowania tworzy zadanie, `cancellation_token_source` które można anulować przy użyciu tokenu został uzyskany z. Zadania utworzone bez tokenu anulowania nie można anulować.

Zadania utworzone `Windows::Foundation::IAsyncInfo` za podstawie interfejsu lub lambda, który zwraca `IAsyncInfo` interfejs osiągnąć stan terminalu po zakończeniu zamkniętej operacji asynchroniczneją systemu Windows lub akcji. Podobnie zadania utworzone z lambda, `task<result_type>` który zwraca osiągnąć ich stan terminalu, gdy zadanie wewnętrzne osiągnie stan terminalu, a nie, gdy lambda zwraca.

`task`zachowuje się jak inteligentny wskaźnik i jest bezpieczny do przejścia przez wartość. Dostęp do niej jest dostępny przez wiele wątków bez konieczności stosowania blokad.

Przeciążenia konstruktora, które zajmują interfejs Windows::Foundation::IAsyncInfo lub lambda zwracający taki interfejs, są dostępne tylko dla aplikacji środowiska wykonawczego systemu Windows.

Aby uzyskać więcej informacji, zobacz [Równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="then"></a><a name="then"></a>Następnie

Dodaje zadanie kontynuacji do tego zadania.

```cpp
template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    const task_options& _TaskOptions) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

template<typename _Function>
__declspec(
    noinline) auto then(const _Function& _Func,
    cancellation_token _CancellationToken,
    task_continuation_context _ContinuationContext) const -> typename details::_ContinuationTypeTraits<_Function,
    _ResultType>::_TaskOfType;

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
Typ obiektu funkcji, który będzie wywoływany przez to zadanie.

*_func*<br/>
Funkcja kontynuacji do wykonania po zakończeniu tego zadania. Ta funkcja kontynuacji musi przyjmować `result_type` jako `task<result_type>`dane `result_type` wejściowe zmienną jednej lub , gdzie jest typ wyniku, który to zadanie tworzy.

*_TaskOptions*<br/>
Opcje zadania obejmują token anulowania, harmonogram i kontekst kontynuacji. Domyślnie poprzednie opcje 3 są dziedziczone z zadania poprzedzago

*_CancellationToken*<br/>
Token anulowania do skojarzenia z zadaniem kontynuacji. Zadanie kontynuacji, które jest tworzone bez tokenu anulowania odziedziczy token jego zadania poprzedzago.

*_ContinuationContext*<br/>
Zmienna określająca, gdzie kontynuacja powinna zostać wykonana. Ta zmienna jest przydatna tylko wtedy, gdy jest używana w aplikacji platformy uniwersalnej systemu uniwersalnego. Aby uzyskać więcej informacji, zobacz [task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Wartość zwracana

Nowo utworzone zadanie kontynuacji. Typ wyniku zwróconego zadania zależy `_Func` od tego, co zwraca.

### <a name="remarks"></a>Uwagi

Przeciążenia, `then` które zajmują lambda lub functor, który zwraca interfejs Windows::Foundation::IAsyncInfo, są dostępne tylko dla aplikacji środowiska wykonawczego systemu Windows.

Aby uzyskać więcej informacji na temat używania kontynuacji zadań do komponowania pracy asynchronicznego, zobacz [Równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="wait"></a><a name="wait"></a>Czekać

Czeka na to zadanie, aby osiągnąć stan terminalu. Jest możliwe `wait` do wykonania zadania wbudowanego, jeśli wszystkie zależności zadań są spełnione i nie został już pobrany do wykonania przez pracownika w tle.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Wartość zwracana

Wartość, `task_status` która może `completed` być `canceled`albo lub . Jeśli zadanie napotkał wyjątek podczas wykonywania lub wyjątek został propagowany do niego `wait` z zadania poprzedzago, zgłoś ten wyjątek.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
> W aplikacji platformy uniwersalnej systemu Windows (UWP) nie należy wywoływać `wait` kodu, który działa w wątku interfejsu użytkownika. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność::invalid_operation](invalid-operation-class.md) ponieważ ta metoda blokuje bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać [metodę współbieżności::task::get,](#get) aby otrzymać wynik zadania poprzedzanego w kontynuacji opartej na zadaniu.

## <a name="see-also"></a>Zobacz też

[współbieżność Obszar nazw](concurrency-namespace.md)
