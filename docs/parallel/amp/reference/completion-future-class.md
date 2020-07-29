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
ms.openlocfilehash: 1863f0908753fb05abb01cf1bd2e34dc6649e0a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228495"
---
# <a name="completion_future-class"></a>completion_future — Klasa

Reprezentuje przyszłość odpowiadającą C++ AMP operacji asynchronicznej.

## <a name="syntax"></a>Składnia

```cpp
class completion_future;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Konstruktor completion_future](#ctor)|Inicjuje nowe wystąpienie klasy `completion_future`.|
|[~ completion_future destruktor](#dtor)|Niszczy `completion_future` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Pobierz](#get)|Czeka, aż zostanie zakończona skojarzona operacja asynchroniczna.|
|[następnie](#then)|Łańcuchuje obiekt funkcji wywołania zwrotnego do `completion_future` obiektu, który ma zostać wykonany po zakończeniu wykonywania skojarzonej operacji asynchronicznej.|
|[to_task](#to_task)|Zwraca `task` obiekt odpowiadający skojarzonej operacji asynchronicznej.|
|[prawidłowa](#valid)|Pobiera wartość logiczną wskazującą, czy obiekt jest skojarzony z operacją asynchroniczną.|
|[trwa](#wait)|Bloki do momentu zakończenia skojarzonej operacji asynchronicznej.|
|[wait_for](#wait_for)|Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub upłynie czas określony przez `_Rel_time` .|
|[wait_until](#wait_until)|Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub dopóki bieżąca godzina przekroczy wartość określoną przez `_Abs_time` .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[operator std:: shared_future\<void>](#operator_shared_future)|Niejawnie konwertuje `completion_future` obiekt na `std::shared_future` obiekt.|
|[operator =](#operator_eq)|Kopiuje zawartość określonego `completion_future` obiektu do tego elementu.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`completion_future`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** współbieżność

## <a name="completion_future"></a><a name="ctor"></a>completion_future

Inicjuje nowe wystąpienie klasy `completion_future`.

### <a name="syntax"></a>Składnia

```cpp
completion_future();

completion_future(
    const completion_future& _Other );

completion_future(
    completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
`completion_future`Obiekt do skopiowania lub przeniesienia.

### <a name="overloads-list"></a>Lista przeciążeń

|Nazwa|Opis|
|----------|-----------------|
|`completion_future();`|Inicjuje nowe wystąpienie `completion_future` klasy|
|`completion_future(const completion_future& _Other);`|Inicjuje nowe wystąpienie `completion_future` klasy przez skopiowanie konstruktora.|
|`completion_future(completion_future&& _Other);`|Inicjuje nowe wystąpienie `completion_future` klasy przez przeniesienie konstruktora.|

## <a name="get"></a><a name="get"></a>Pobierz

Czeka, aż zostanie zakończona skojarzona operacja asynchroniczna. Zgłasza zapisany wyjątek, jeśli został napotkany podczas operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
void get() const;
```

## <a name="operator-stdshared_futurevoid"></a><a name="operator_shared_future"></a>operator std:: shared_future\<void>

Niejawnie konwertuje `completion_future` obiekt na `std::shared_future` obiekt.

### <a name="syntax"></a>Składnia

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt `std::shared_future`.

## <a name="operator"></a><a name="operator_eq"></a>operator =

Kopiuje zawartość określonego `completion_future` obiektu do tego elementu.

### <a name="syntax"></a>Składnia

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt, z którego mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do tego `completion_future` obiektu.

## <a name="overloads-list"></a>Lista przeciążeń

|Nazwa|Opis|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Kopiuje zawartość określonego `completion_future` obiektu do tego, za pomocą kopii głębokiej.|
|`completion_future& operator=(completion_future&& _Other);`|Kopiuje zawartość określonego `completion_future` obiektu do tego elementu przy użyciu przypisania przenoszenia.|

## <a name="then"></a><a name="then"></a>następnie

Łańcuchuje obiekt funkcji wywołania zwrotnego do `completion_future` obiektu, który ma zostać wykonany po zakończeniu wykonywania skojarzonej operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
template <typename _Functor>
void then(const _Functor & _Func ) const;
```

### <a name="parameters"></a>Parametry

*_Functor*<br/>
Wywołanie zwrotne Funktor.

*_Func*<br/>
Obiekt funkcji wywołania zwrotnego.

## <a name="to_task"></a><a name="to_task"></a>to_task

Zwraca `task` obiekt odpowiadający skojarzonej operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Wartość zwracana

`task`Obiekt odpowiadający skojarzonej operacji asynchronicznej.

## <a name="valid"></a><a name="valid"></a>prawidłowa

Pobiera wartość logiczną wskazującą, czy obiekt jest skojarzony z operacją asynchroniczną.

### <a name="syntax"></a>Składnia

```cpp
bool valid() const;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt jest skojarzony z operacją asynchroniczną; w przeciwnym razie **`false`** .

## <a name="wait"></a><a name="wait"></a>trwa

Bloki do momentu zakończenia skojarzonej operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
void wait() const;
```

## <a name="wait_for"></a><a name="wait_for"></a>wait_for

Bloki do momentu zakończenia skojarzonej operacji asynchronicznej lub czasu określonego przez, który `_Rel_time` upłynął.

### <a name="syntax"></a>Składnia

```cpp
template <
    class _Rep,
    class _Period
>
std::future_status::future_status wait_for(
    const std::chrono::duration< _Rep, _Period>& _Rel_time ) const;
```

### <a name="parameters"></a>Parametry

*_Rep*<br/>
Typ arytmetyczny, który reprezentuje liczbę taktów.

*_Period*<br/>
Współczynnik std::, który reprezentuje liczbę sekund, które upłynęły do osi.

*_Rel_time*<br/>
Maksymalna ilość czasu oczekiwania na zakończenie operacji.

### <a name="return-value"></a>Wartość zwracana

Zwraca:

- `std::future_status::deferred`Jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.

- `std::future_status::ready`Jeśli skojarzona operacja asynchroniczna została zakończona.

- `std::future_status::timeout`w przypadku upływu określonego czasu.

## <a name="wait_until"></a><a name="wait_until"></a>wait_until

Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub dopóki bieżąca godzina przekroczy wartość określoną przez `_Abs_time` .

### <a name="syntax"></a>Składnia

```cpp
template <
    class _Clock,
    class _Duration
>
std::future_status::future_status wait_until(
    const std::chrono::time_point< _Clock, _Duration>& _Abs_time ) const;
```

### <a name="parameters"></a>Parametry

*_Clock*<br/>
Zegar, od którego jest mierzony ten punkt czasu.

*_Duration*<br/>
Przedział czasu od momentu rozpoczęcia `_Clock` epoki, po którym funkcja przekroczy limit czasu.

*_Abs_time*<br/>
Punkt w czasie, po którym funkcja przekroczy limit czasu.

### <a name="return-value"></a>Wartość zwracana

Zwraca:

1. `std::future_status::deferred`Jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.

1. `std::future_status::ready`Jeśli skojarzona operacja asynchroniczna została zakończona.

1. `std::future_status::timeout`w przypadku upływu określonego czasu.

## <a name="completion_future"></a><a name="dtor"></a>~ completion_future

Niszczy `completion_future` obiekt.

### <a name="syntax"></a>Składnia

```cpp
~completion_future();
```

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
