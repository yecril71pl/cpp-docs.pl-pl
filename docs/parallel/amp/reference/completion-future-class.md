---
title: completion_future — Klasa
ms.date: 11/04/2016
f1_keywords:
- completion_future
- AMPRT/completion_future
- AMPRT/Concurrency::completion_future::completion_future
- AMPRT/Concurrency::completion_future::get
- AMPRT/Concurrency::completion_future::then
- AMPRT/Concurrency::completion_future::to_task
- AMPRT/Concurrency::completion_future::valid
- AMPRT/Concurrency::completion_future::wait
- AMPRT/Concurrency::completion_future::wait_for
- AMPRT/Concurrency::completion_future::wait_until
ms.assetid: 1303c62e-546d-4b02-a578-251ed3fc0b6b
ms.openlocfilehash: d121477cf63236ee40df826a63dd7c7c9880d142
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535297"
---
# <a name="completionfuture-class"></a>completion_future — Klasa

Reprezentuje przyszłą operacji asynchronicznych C++ AMP.

### <a name="syntax"></a>Składnia

```
class completion_future;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[completion_future konstruktora](#ctor)|Inicjuje nowe wystąpienie klasy `completion_future` klasy.|
|[~ completion_future — destruktor](#dtor)|Niszczy `completion_future` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Czeka, aż skojarzona operacja asynchroniczna.|
|[Następnie](#then)|Tworzy powiązanie obiekt funkcji wywołania zwrotnego `completion_future` obiektu do wykonania, gdy skojarzona operacja asynchroniczna kończy działanie.|
|[to_task](#to_task)|Zwraca `task` obiektu odpowiadającego skojarzona operacja asynchroniczna.|
|[Nieprawidłowa](#valid)|Pobiera wartość logiczną, wskazującą, czy obiekt jest skojarzony z operacją asynchroniczną.|
|[Czekaj](#wait)|Blokuje, dopóki nie zakończy się skojarzona operacja asynchroniczna.|
|[wait_for](#wait_for)|Blokuje, dopóki nie zakończy się skojarzona operacja asynchroniczna lub w czasie określonym przez `_Rel_time` upłynął.|
|[wait_until](#wait_until)|Blokuje, dopóki skojarzona operacja asynchroniczna lub dopóki bieżący czas przekracza wartość określoną przez `_Abs_time`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Operator std::shared_future\<void >](#operator_shared_future)|Niejawnie konwertuje `completion_future` obiekt `std::shared_future` obiektu.|
|[operator=](#operator_eq)|Kopiuje zawartość określonego `completion_future` obiektu do wskazanego.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`completion_future`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt.h

**Namespace:** współbieżności

## <a name="ctor"></a> completion_future

Inicjuje nowe wystąpienie klasy `completion_future` klasy.

### <a name="syntax"></a>Składnia

```
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
`completion_future` Obiektu, aby skopiować lub przenieść.

### <a name="overloads-list"></a>Lista przeciążeń

|Nazwa|Opis|
|----------|-----------------|
|`completion_future();`|Inicjuje nowe wystąpienie klasy `completion_future` klasy|
|`completion_future(const completion_future& _Other);`|Inicjuje nowe wystąpienie klasy `completion_future` klasy przez kopiowanie konstruktora.|
|`completion_future(completion_future&& _Other);`|Inicjuje nowe wystąpienie klasy `completion_future` klasy, przenosząc konstruktora.|

## <a name="get"></a> Pobierz

Czeka, aż skojarzona operacja asynchroniczna. Zgłasza wyjątek przechowywane, jeśli jeden napotkano podczas operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```
void get() const;
```

## <a name="operator_shared_future"></a> std::shared_future — operator<void>

Niejawnie konwertuje `completion_future` obiekt `std::shared_future` obiektu.

### <a name="syntax"></a>Składnia

```
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Wartość zwracana

`std::shared_future` Obiektu.

## <a name="operator_eq"></a> operator =

Kopiuje zawartość określonego `completion_future` obiektu do wskazanego.

### <a name="syntax"></a>Składnia

```
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Inne*<br/>
Obiekt do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do `completion_future` obiektu.

## <a name="overloads-list"></a>Lista przeciążeń

|Nazwa|Opis|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Kopiuje zawartość określonego `completion_future` obiektu do tego, używając głębokiego kopiowania.|
|`completion_future& operator=(completion_future&& _Other);`|Kopiuje zawartość określonego `completion_future` obiektu do wskazanego przy użyciu przeniesienia przypisania.|

## <a name="then"></a> Następnie

Tworzy powiązanie obiekt funkcji wywołania zwrotnego `completion_future` obiektu do wykonania, gdy skojarzona operacja asynchroniczna kończy działanie.

### <a name="syntax"></a>Składnia

```
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Parametry

*_Functor*<br/>
Funkcję wywołania zwrotnego.

*_Func*<br/>
Obiekt funkcyjny wywołania zwrotnego.

## <a name="to_task"></a> to_task

Zwraca `task` obiektu odpowiadającego skojarzona operacja asynchroniczna.

### <a name="syntax"></a>Składnia

```
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Wartość zwracana

Element `task` obiektu odpowiadającego skojarzona operacja asynchroniczna.

## <a name="valid"></a> Nieprawidłowa

Pobiera wartość logiczną, wskazującą, czy obiekt jest skojarzony z operacją asynchroniczną.

### <a name="syntax"></a>Składnia

```
bool valid() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt jest skojarzony z operacją asynchroniczną; w przeciwnym razie **false**.

## <a name="wait"></a> Czekaj

Blokuje, dopóki nie zakończy się skojarzona operacja asynchroniczna.

### <a name="syntax"></a>Składnia

```
void wait() const;
```

## <a name="wait_for"></a> wait_for

Blokuje, dopóki nie zakończy się skojarzona operacja asynchroniczna lub czas, który jest określony przez `_Rel_time` upłynął.

### <a name="syntax"></a>Składnia

```
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Parametry

*_Rep*<br/>
Typ arytmetyczny, który reprezentuje liczbę znaczników.

*_Period*<br/>
Std::ratio wskazuje liczbę sekund, które upłynęły na jednostkę skali.

*_Rel_time*<br/>
Maksymalna ilość czasu oczekiwania na ukończenie tej operacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca:

- `std::future_status::deferred` Jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.

- `std::future_status::ready` Jeśli skojarzona operacja asynchroniczna została zakończona.

- `std::future_status::timeout` Jeśli określony czas upłynął.

## <a name="wait_until"></a> wait_until

Blokuje, dopóki skojarzona operacja asynchroniczna lub dopóki bieżący czas przekracza wartość określoną przez `_Abs_time`.

### <a name="syntax"></a>Składnia

```
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Parametry

*_Clock*<br/>
Zegar, na którym mierzony jest punkt czasu.

*_Duration*<br/>
Interwał czasu od chwili uruchomienia `_Clock`firmy epoki, po upływie którego funkcja przekroczy limit czasu.

*_Abs_time*<br/>
Punkt w czasie, po upływie którego funkcja przekroczy limit czasu.

### <a name="return-value"></a>Wartość zwracana

Zwraca:

1. `std::future_status::deferred` Jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.

1. `std::future_status::ready` Jeśli skojarzona operacja asynchroniczna została zakończona.

1. `std::future_status::timeout` Jeśli określony czas upłynął.

## <a name="dtor"></a> ~ completion_future

Niszczy `completion_future` obiektu.

### <a name="syntax"></a>Składnia

```
~completion_future();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
