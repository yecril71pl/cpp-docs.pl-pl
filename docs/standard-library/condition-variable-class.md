---
title: condition_variable — Klasa
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.openlocfilehash: 999e236433ec4f3f2f52abb06855004a89169fa6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449456"
---
# <a name="conditionvariable-class"></a>condition_variable — Klasa

Użyj klasy `condition_variable` , aby zaczekać na zdarzenie, gdy `mutex` masz typ `unique_lock<mutex>`. Obiekty tego typu mogą mieć lepszą wydajność niż obiekty typu [condition_variable_any < unique_lock\<muteks > >](../standard-library/condition-variable-any-class.md).

## <a name="syntax"></a>Składnia

```cpp
class condition_variable;
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[condition_variable](#condition_variable)|Konstruuje `condition_variable` obiekt.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[native_handle](#native_handle)|Zwraca typ specyficzny dla implementacji reprezentujący uchwyt condition_variable.|
|[notify_all](#notify_all)|Odblokowuje wszystkie wątki, które oczekują na `condition_variable` obiekt.|
|[notify_one](#notify_one)|Odblokowuje jeden z wątków, które oczekują `condition_variable` na obiekt.|
|[trwa](#wait)|Blokuje wątek.|
|[wait_for](#wait_for)|Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.|
|[wait_until](#wait_until)|Blokuje wątek i ustawia maksymalny punkt w czasie, w którym odblokowuje wątek.|

## <a name="condition_variable"></a>condition_variable

Konstruuje `condition_variable` obiekt.

```cpp
condition_variable();
```

### <a name="remarks"></a>Uwagi

Jeśli nie jest dostępna wystarczająca ilość pamięci, Konstruktor zgłasza obiekt [system_error](../standard-library/system-error-class.md) , który ma `not_enough_memory` kod błędu. Jeśli nie można utworzyć obiektu, ponieważ jakiś inny zasób nie jest dostępny, Konstruktor zgłasza `system_error` obiekt, który `resource_unavailable_try_again` ma kod błędu.

## <a name="native_handle"></a>native_handle

Zwraca typ specyficzny dla implementacji, który reprezentuje uchwyt condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type`jest definiowana jako wskaźnik do środowisko uruchomieniowe współbieżności wewnętrznych struktur danych.

## <a name="notify_all"></a>notify_all

Odblokowuje wszystkie wątki, które oczekują na `condition_variable` obiekt.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>notify_one

Odblokowuje jeden z wątków, które oczekują na `condition_variable` obiekt.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>trwa

Blokuje wątek.

```cpp
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*\
Obiekt [>\<mutex unique_lock](../standard-library/unique-lock-class.md) .

*Pred*\
Dowolne wyrażenie zwracające **wartość true** lub **false**.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do momentu `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](#notify_one) lub [notify_all](#notify_all). Może również wzbudzać obudzić.

W efekcie druga metoda wykonuje następujący kod.

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>wait_for

Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.

```cpp
template <class Rep, class Period>
cv_status wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time);

template <class Rep, class Period, class Predicate>
bool wait_for(
    unique_lock<mutex>& Lck,
    const chrono::duration<Rep, Period>& Rel_time,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*\
Obiekt [>\<mutex unique_lock](../standard-library/unique-lock-class.md) .

*Rel_time*\
`chrono::duration` Obiekt, który określa czas, po którym wątek zostanie wznowiony.

*Pred*\
Dowolne wyrażenie zwracające **wartość true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `cv_status::timeout` , jeśli czas oczekiwania zakończy się, gdy *Rel_time* . W przeciwnym razie metoda zwraca `cv_status::no_timeout`.

Druga metoda zwraca wartość *p*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do momentu `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](#notify_one) lub [notify_all](#notify_all) lub do czasu, aż upłynie czas *Rel_time* . Może również wzbudzać obudzić.

W efekcie druga metoda wykonuje następujący kod.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>wait_until

Blokuje wątek i ustawia maksymalny punkt w czasie, w którym odblokowuje wątek.

```cpp
template <class Clock, class Duration>
cv_status wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time);

template <class Clock, class Duration, class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

cv_status wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time);

template <class Predicate>
bool wait_until(
    unique_lock<mutex>& Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*\
Obiekt [>\<mutex unique_lock](../standard-library/unique-lock-class.md) .

*Abs_time*\
Obiekt [chrono:: time_point](../standard-library/time-point-class.md) .

*Pred*\
Dowolne wyrażenie zwracające **wartość true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Metody, które zwracają `cv_status` typ Return `cv_status::timeout` , jeśli oczekiwania zakończy się po upłynięciu *Abs_time* . W przeciwnym razie metody zwracają `cv_status::no_timeout`.

Metody, które zwracają **bool** zwracają wartość *p*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do momentu `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](#notify_one) lub [notify_all](#notify_all) lub do `Abs_time`. Może również wzbudzać obudzić.

W efekcie druga metoda wykonuje następujący kod

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Trzecia i czwarta Metoda używa wskaźnika do obiektu typu `xtime` , aby `chrono::time_point` zastąpić obiekt. `xtime` Obiekt Określa maksymalną ilość czasu oczekiwania na sygnał.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[<condition_variable>](../standard-library/condition-variable.md)
