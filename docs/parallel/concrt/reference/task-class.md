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
ms.openlocfilehash: 6a063f0bba9482824817e4efe21ae5b7bf3c0995
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219537"
---
# <a name="task-class-concurrency-runtime"></a>task — Klasa (współbieżność środowiska wykonawczego)

Klasa Parallel wzorców Library (PPL) `task` . `task`Obiekt reprezentuje zadanie, które może być wykonywane asynchronicznie i współbieżnie przy użyciu innych zadań i równoległych pracy wytwarzanych przez algorytmy równoległe w środowisko uruchomieniowe współbieżności. Generuje wynik typu `_ResultType` po pomyślnym zakończeniu. Zadania typu `task<void>` nie generują żadnego wyniku. Zadanie może być odczekane i anulowane niezależnie od innych zadań. Może być również tworzony z innymi zadaniami przy użyciu wzorców kontynuacji ( `then` ) i sprzężeń ( `when_all` ) i wyboru ( `when_any` ). Gdy obiekt zadania jest przypisany do nowej zmiennej, zachowanie jest takie `std::shared_ptr` jak; innymi słowy, oba obiekty reprezentują to samo zadanie bazowe.

## <a name="syntax"></a>Składnia

```cpp
template <>
class task<void>;

template<typename _ResultType>
class task;
```

### <a name="parameters"></a>Parametry

*_ResultType*<br/>
Typ wyniku, który generuje zadanie.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`result_type`|Typ wyniku, który tworzy obiekt tej klasy.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[zadaniem](#ctor)|Przeciążone. Konstruuje `task` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Pobierz](#get)|Przeciążone. Zwraca wynik tworzony przez to zadanie. Jeśli zadanie nie jest w stanie terminalu, wywołanie w celu `get` poczeka na zakończenie zadania. Ta metoda nie zwraca wartości, gdy jest wywoływana dla zadania z `result_type` **`void`** .|
|[is_apartment_aware](#is_apartment_aware)|Określa, czy zadanie odpakuje interfejs środowisko wykonawcze systemu Windows `IAsyncInfo` , czy też jest wynikiem tego zadania.|
|[is_done](#is_done)|Określa, czy zadanie zostało ukończone.|
|[pracę](#scheduler)|Zwraca harmonogram dla tego zadania|
|[następnie](#then)|Przeciążone. Dodaje zadanie kontynuacji do tego zadania.|
|[trwa](#wait)|Czeka, aż to zadanie osiągnie stan końcowy. Można `wait` wykonać zadanie wbudowane, jeśli wszystkie zależności zadań są spełnione i nie zostały jeszcze pobrane do wykonania przez proces roboczy w tle.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator! =](#operator_neq)|Przeciążone. Określa, czy dwa `task` obiekty reprezentują różne zadania wewnętrzne.|
|[operator =](#operator_eq)|Przeciążone. Zamienia zawartość jednego `task` obiektu na inny.|
|[operator = =](#operator_eq_eq)|Przeciążone. Określa, czy dwa `task` obiekty reprezentują to samo zadanie wewnętrzne.|

## <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`task`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ppltasks. h

**Przestrzeń nazw:** współbieżność

## <a name="get"></a><a name="get"></a>Pobierz

Zwraca wynik tworzony przez to zadanie. Jeśli zadanie nie jest w stanie terminalu, wywołanie w celu `get` poczeka na zakończenie zadania. Ta metoda nie zwraca wartości, gdy jest wywoływana dla zadania z `result_type` **`void`** .

```cpp
_ResultType get() const;

void get() const;
```

### <a name="return-value"></a>Wartość zwracana

Wynik zadania.

### <a name="remarks"></a>Uwagi

Jeśli zadanie zostało anulowane, wywołanie `get` zostanie zgłosić wyjątek [task_canceled](task-canceled-class.md) . Jeśli zadanie napotkało inny wyjątek lub został on rozpropagowany do niego z zadania poprzedzającego, wywołanie `get` spowoduje zgłoszenie tego wyjątku.

> [!IMPORTANT]
> W aplikacji platforma uniwersalna systemu Windows (platformy UWP) Nie wywołuj [concurrency:: Task:: wait](#wait) lub `get` ( `wait` Calls `get` ) w kodzie, który jest uruchamiany w wątku interfejsu użytkownika. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność:: invalid_operation](invalid-operation-class.md) , ponieważ te metody blokują bieżący wątek i mogą spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać `get` metodę, aby otrzymać wynik zadania poprzedzającego w kontynuacji opartej na zadaniach, ponieważ wynik jest natychmiast dostępny.

## <a name="is_apartment_aware"></a><a name="is_apartment_aware"></a>is_apartment_aware

Określa, czy zadanie odpakuje interfejs środowisko wykonawcze systemu Windows `IAsyncInfo` , czy też jest wynikiem tego zadania.

```cpp
bool is_apartment_aware() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli zadanie odpakuje `IAsyncInfo` interfejs lub jest ono wynikiem tego zadania, **`false`** w przeciwnym razie.

## <a name="taskis_done-method-concurrency-runtime"></a><a name="is_done"></a>Task:: is_done, Metoda (środowisko uruchomieniowe współbieżności)

Określa, czy zadanie zostało ukończone.

```cpp
bool is_done() const;
```

### <a name="return-value"></a>Wartość zwracana

Ma wartość true, jeśli zadanie zostało ukończone, w przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Funkcja zwraca wartość true, jeśli zadanie zostało ukończone lub anulowane (z wyjątkiem użytkownika lub bez niego).

## <a name="operator"></a><a name="operator_neq"></a>operator! =

Określa, czy dwa `task` obiekty reprezentują różne zadania wewnętrzne.

```cpp
bool operator!= (const task<_ResultType>& _Rhs) const;

bool operator!= (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zadanie, które ma zostać porównane.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty odnoszą się do różnych zadań podstawowych i **`false`** w inny sposób.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Zamienia zawartość jednego `task` obiektu na inny.

```cpp
task& operator= (const task& _Other);

task& operator= (task&& _Other);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt źródłowy `task` .

### <a name="return-value"></a>Wartość zwracana

### <a name="remarks"></a>Uwagi

Podobnie jak w przypadku `task` inteligentnego wskaźnika, po przypisaniu kopii te `task` obiekty reprezentują to samo rzeczywiste zadanie, co `_Other` .

## <a name="operator"></a><a name="operator_eq_eq"></a>operator = =

Określa, czy dwa `task` obiekty reprezentują to samo zadanie wewnętrzne.

```cpp
bool operator== (const task<_ResultType>& _Rhs) const;

bool operator== (const task<void>& _Rhs) const;
```

### <a name="parameters"></a>Parametry

*_Rhs*<br/>
Zadanie, które ma zostać porównane.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekty odnoszą się do tego samego zadania bazowego i **`false`** w inny sposób.

## <a name="taskscheduler-method-concurrency-runtime"></a><a name="scheduler"></a>Task:: Scheduler — Metoda (środowisko uruchomieniowe współbieżności)

Zwraca harmonogram dla tego zadania

```cpp
scheduler_ptr scheduler() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do harmonogramu

## <a name="task"></a><a name="ctor"></a>zadaniem

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
Typ parametru, z którego ma zostać wykonane zadanie.

*_Param*<br/>
Parametr, z którego ma zostać wykonane zadanie. Może to być wyrażenie lambda, obiekt funkcji, `task_completion_event<result_type>` obiekt lub Windows:: Foundation:: IAsyncInfo, jeśli używasz zadań w aplikacji środowisko wykonawcze systemu Windows. Obiekt lambda lub Function powinien być odpowiednikiem typu `std::function<X(void)>` , gdzie X może być zmienną typu `result_type` , `task<result_type>` lub Windows:: Foundation:: IAsyncInfo w aplikacjach środowisko wykonawcze systemu Windows.

*_TaskOptions*<br/>
Opcje zadania obejmują token anulowania, harmonogram itd.

*_Other*<br/>
Obiekt źródłowy `task` .

### <a name="remarks"></a>Uwagi

Konstruktor domyślny dla elementu `task` jest obecny tylko w celu zezwalania na używanie zadań w kontenerach. Nie można użyć domyślnego zadania konstruowanego, dopóki nie przypiszesz do niego prawidłowego zadania. Metody takie jak `get` `wait` lub będą zgłaszać `then` wyjątek [invalid_argument](../../../standard-library/invalid-argument-class.md) , gdy zostanie wywołane w przytworzonym domyślnym zadaniu.

Zadanie, które jest tworzone na podstawie zakończy `task_completion_event` pracę (i ma zaplanowaną kontynuację) po ustawieniu zdarzenia ukończenia zadania.

Wersja konstruktora, który pobiera token anulowania, tworzy zadanie, które można anulować przy użyciu `cancellation_token_source` tokenu uzyskanego z. Zadania utworzone bez tokenu anulowania nie są anulowane.

Zadania utworzone na podstawie `Windows::Foundation::IAsyncInfo` interfejsu lub wyrażenia lambda, które zwracają `IAsyncInfo` interfejs docierają do stanu terminalu, gdy zawarta środowisko wykonawcze systemu Windows operacja asynchroniczna lub akcja zostanie ukończona. Podobnie zadania utworzone na podstawie wyrażenia lambda, które zwraca `task<result_type>` osiągnięcie stanu terminalu, gdy zadanie wewnętrzne osiągnie swój stan końcowy, a nie gdy zwraca lambda.

`task`zachowuje się jak inteligentny wskaźnik i jest bezpiecznie przekazywania między wartościami. Dostęp do niego można uzyskać przez wiele wątków bez potrzeby blokad.

Przeciążenia konstruktora, które mają interfejs Windows:: Foundation:: IAsyncInfo lub lambda zwracające taki interfejs, są dostępne tylko dla aplikacji środowisko wykonawcze systemu Windows.

Aby uzyskać więcej informacji, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="then"></a><a name="then"></a>następnie

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
Typ obiektu funkcji, który zostanie wywołany przez to zadanie.

*_Func*<br/>
Funkcja kontynuacji do wykonania, gdy to zadanie zostanie ukończone. Ta funkcja kontynuacji musi przyjąć jako wartość wejściową zmienną `result_type` lub `task<result_type>` , gdzie `result_type` jest typem wyniku tego zadania.

*_TaskOptions*<br/>
Opcje zadania obejmują token anulowania, harmonogram i kontekst kontynuacji. Domyślnie trzy pierwsze opcje są dziedziczone z zadania poprzedzającego

*_CancellationToken*<br/>
Token anulowania do skojarzenia z zadaniem kontynuacji. Zadanie kontynuacji tworzone bez tokenu anulowania odziedziczy token zadania poprzedzającego.

*_ContinuationContext*<br/>
Zmienna, która określa, gdzie kontynuacja powinna zostać wykonana. Ta zmienna jest przydatna tylko w przypadku użycia w aplikacji platformy UWP. Aby uzyskać więcej informacji, zobacz [task_continuation_context](task-continuation-context-class.md)

### <a name="return-value"></a>Wartość zwracana

Nowo utworzone zadanie kontynuacji. Typ wyniku zwracanego zadania jest określany na podstawie `_Func` zwracanych danych.

### <a name="remarks"></a>Uwagi

Przeciążenia mające `then` wartość lambda lub Funktor, które zwracają interfejs Windows:: Foundation:: IAsyncInfo, są dostępne tylko dla środowisko wykonawcze systemu Windows aplikacji.

Aby uzyskać więcej informacji na temat sposobu używania kontynuacji zadań do redagowania pracy asynchronicznej, zobacz [równoległość zadań](../../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="wait"></a><a name="wait"></a>trwa

Czeka, aż to zadanie osiągnie stan końcowy. Można `wait` wykonać zadanie wbudowane, jeśli wszystkie zależności zadań są spełnione i nie zostały jeszcze pobrane do wykonania przez proces roboczy w tle.

```cpp
task_status wait() const;
```

### <a name="return-value"></a>Wartość zwracana

`task_status`Wartość, która może być albo `completed` `canceled` . Jeśli zadanie napotkało wyjątek podczas wykonywania lub został on rozpropagowany do niego z zadania poprzedzającego, `wait` spowoduje zgłoszenie tego wyjątku.

### <a name="remarks"></a>Uwagi

> [!IMPORTANT]
> W aplikacji platforma uniwersalna systemu Windows (platformy UWP) Nie wywołuj `wait` kodu, który jest uruchamiany w wątku interfejsu użytkownika. W przeciwnym razie środowisko uruchomieniowe zgłasza [współbieżność:: invalid_operation](invalid-operation-class.md) , ponieważ ta metoda blokuje bieżący wątek i może spowodować, że aplikacja przestanie odpowiadać. Można jednak wywołać metodę [concurrency:: Task:: Get](#get) , aby otrzymać wynik zadania poprzedzającego w kontynuacji opartej na zadaniach.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności](concurrency-namespace.md)
