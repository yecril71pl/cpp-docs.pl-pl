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
ms.openlocfilehash: 69aacad02df5290f161e9d8d311be347668be9f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127023"
---
# <a name="completion_future-class"></a>completion_future — Klasa

Reprezentuje przyszłość odpowiadającą operacji asynchronicznej C++ amp.

## <a name="syntax"></a>Składnia

```cpp
class completion_future;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[Konstruktor completion_future](#ctor)|Inicjuje nowe wystąpienie klasy `completion_future`.|
|[~ completion_future destruktor](#dtor)|Niszczy obiekt `completion_future`.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[get](#get)|Czeka, aż zostanie zakończona skojarzona operacja asynchroniczna.|
|[następnie](#then)|Łańcuchuje obiekt funkcji wywołania zwrotnego do obiektu `completion_future`, który ma zostać wykonany po zakończeniu wykonywania skojarzonej operacji asynchronicznej.|
|[to_task](#to_task)|Zwraca obiekt `task` odpowiadający skojarzonej operacji asynchronicznej.|
|[prawidłowa](#valid)|Pobiera wartość logiczną wskazującą, czy obiekt jest skojarzony z operacją asynchroniczną.|
|[trwa](#wait)|Bloki do momentu zakończenia skojarzonej operacji asynchronicznej.|
|[wait_for](#wait_for)|Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub upłynie czas określony przez `_Rel_time`.|
|[wait_until](#wait_until)|Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub dopóki bieżąca godzina przekroczy wartość określoną przez `_Abs_time`.|

### <a name="public-operators"></a>Operatory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[operator std:: shared_future\<void >](#operator_shared_future)|Niejawnie konwertuje obiekt `completion_future` na obiekt `std::shared_future`.|
|[operator =](#operator_eq)|Kopiuje zawartość określonego obiektu `completion_future` do tego.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`completion_future`

## <a name="requirements"></a>Wymagania

**Nagłówek:** amprt. h

**Przestrzeń nazw:** współbieżność

## <a name="ctor"></a>completion_future

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
Obiekt `completion_future`, który ma zostać skopiowany lub przeniesiony.

### <a name="overloads-list"></a>Lista przeciążeń

|Name (Nazwa)|Opis|
|----------|-----------------|
|`completion_future();`|Inicjuje nowe wystąpienie klasy `completion_future`|
|`completion_future(const completion_future& _Other);`|Inicjuje nowe wystąpienie klasy `completion_future` przez skopiowanie konstruktora.|
|`completion_future(completion_future&& _Other);`|Inicjuje nowe wystąpienie klasy `completion_future` przez przeniesienie konstruktora.|

## <a name="get"></a>Pobierz

Czeka, aż zostanie zakończona skojarzona operacja asynchroniczna. Zgłasza zapisany wyjątek, jeśli został napotkany podczas operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
void get() const;
```

## <a name="operator_shared_future"></a>operator std:: shared_future\<void >

Niejawnie konwertuje obiekt `completion_future` na obiekt `std::shared_future`.

### <a name="syntax"></a>Składnia

```cpp
operator std::shared_future<void>() const;
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `std::shared_future`.

## <a name="operator_eq"></a>operator =

Kopiuje zawartość określonego obiektu `completion_future` do tego.

### <a name="syntax"></a>Składnia

```cpp
completion_future&  operator= (const completion_future& _Other );
completion_future&  operator= (completion_future&& _Other );
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Obiekt, z którego mają zostać skopiowane.

### <a name="return-value"></a>Wartość zwrócona

Odwołanie do tego obiektu `completion_future`.

## <a name="overloads-list"></a>Lista przeciążeń

|Name (Nazwa)|Opis|
|----------|-----------------|
|`completion_future& operator=(const completion_future& _Other);`|Kopiuje zawartość określonego obiektu `completion_future` do tego, za pomocą kopii głębokiej.|
|`completion_future& operator=(completion_future&& _Other);`|Kopiuje zawartość określonego obiektu `completion_future` do tego, przy użyciu przypisania przenoszenia.|

## <a name="then"></a>następnie

Łańcuchuje obiekt funkcji wywołania zwrotnego do obiektu `completion_future`, który ma zostać wykonany po zakończeniu wykonywania skojarzonej operacji asynchronicznej.

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

## <a name="to_task"></a>to_task

Zwraca obiekt `task` odpowiadający skojarzonej operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
concurrency::task<void> to_task() const;
```

### <a name="return-value"></a>Wartość zwrócona

Obiekt `task` odpowiadający skojarzonej operacji asynchronicznej.

## <a name="valid"></a>prawidłowa

Pobiera wartość logiczną wskazującą, czy obiekt jest skojarzony z operacją asynchroniczną.

### <a name="syntax"></a>Składnia

```cpp
bool valid() const;
```

### <a name="return-value"></a>Wartość zwrócona

**ma wartość true** , jeśli obiekt jest skojarzony z operacją asynchroniczną; w przeciwnym razie **false**.

## <a name="wait"></a>trwa

Bloki do momentu zakończenia skojarzonej operacji asynchronicznej.

### <a name="syntax"></a>Składnia

```cpp
void wait() const;
```

## <a name="wait_for"></a>wait_for

Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub upłynie czas określony przez `_Rel_time`.

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

### <a name="return-value"></a>Wartość zwrócona

Typu

- `std::future_status::deferred`, jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.

- `std::future_status::ready`, jeśli skojarzona operacja asynchroniczna została zakończona.

- `std::future_status::timeout` w przypadku upływu określonego okresu.

## <a name="wait_until"></a>wait_until

Bloki dopóki nie zostanie zakończona skojarzona operacja asynchroniczna lub dopóki bieżąca godzina przekroczy wartość określoną przez `_Abs_time`.

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
Interwał czasu od momentu rozpoczęcia epoki `_Clock`, po upływie którego funkcja przekroczy limit czasu.

*_Abs_time*<br/>
Punkt w czasie, po którym funkcja przekroczy limit czasu.

### <a name="return-value"></a>Wartość zwrócona

Typu

1. `std::future_status::deferred`, jeśli skojarzona operacja asynchroniczna nie jest uruchomiona.

1. `std::future_status::ready`, jeśli skojarzona operacja asynchroniczna została zakończona.

1. `std::future_status::timeout`, jeśli upłynie określony czas.

## <a name="dtor"></a>~ completion_future

Niszczy obiekt `completion_future`.

### <a name="syntax"></a>Składnia

```cpp
~completion_future();
```

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności (C++ AMP)](concurrency-namespace-cpp-amp.md)
