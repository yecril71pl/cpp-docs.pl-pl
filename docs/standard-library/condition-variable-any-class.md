---
title: condition_variable_any — Klasa
ms.date: 11/04/2016
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.openlocfilehash: 9dc73de515aa8e321dbb28ca4a859b256613fbfe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831480"
---
# <a name="condition_variable_any-class"></a>condition_variable_any — Klasa

Użyj klasy, `condition_variable_any` aby zaczekać na zdarzenie o dowolnym `mutex` typie.

## <a name="syntax"></a>Składnia

```cpp
class condition_variable_any;
```

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktory

|Nazwa|Opis|
|-|-|
|[condition_variable_any](#condition_variable_any)|Konstruuje `condition_variable_any` obiekt.|

### <a name="functions"></a>Functions

|Nazwa|Opis|
|-|-|
|[notify_all](#notify_all)|Odblokowuje wszystkie wątki, które oczekują na `condition_variable_any` obiekt.|
|[notify_one](#notify_one)|Odblokowuje jeden z wątków, które oczekują na `condition_variable_any` obiekt.|
|[trwa](#wait)|Blokuje wątek.|
|[wait_for](#wait_for)|Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.|
|[wait_until](#wait_until)|Blokuje wątek i ustawia maksymalny punkt w czasie, w którym odblokowuje wątek.|

## <a name="condition_variable_any"></a><a name="condition_variable_any"></a> condition_variable_any

Konstruuje `condition_variable_any` obiekt.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>Uwagi

Jeśli nie jest dostępna wystarczająca ilość pamięci, Konstruktor zgłasza obiekt [system_error](../standard-library/system-error-class.md) , który ma `not_enough_memory` Kod błędu. Jeśli nie można utworzyć obiektu, ponieważ jakiś inny zasób nie jest dostępny, Konstruktor zgłasza `system_error` obiekt, który ma `resource_unavailable_try_again` Kod błędu.

## <a name="notify_all"></a><a name="notify_all"></a> notify_all

Odblokowuje wszystkie wątki, które oczekują na `condition_variable_any` obiekt.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a><a name="notify_one"></a> notify_one

Odblokowuje jeden z wątków, które oczekują na `condition_variable_any` obiekt.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a><a name="wait"></a> trwa

Blokuje wątek.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*\
`mutex`Obiekt dowolnego typu.

*Pred*\
Dowolne wyrażenie zwracające **`true`** lub **`false`** .

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do momentu `condition_variable_any` zasygnalizowania obiektu przez wywołanie do [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all). Może również wzbudzać obudzić.

Druga metoda w efekcie wykonuje Poniższy kod.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a><a name="wait_for"></a> wait_for

Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*\
`mutex`Obiekt dowolnego typu.

*Rel_time*\
`chrono::duration`Obiekt, który określa czas, po którym wątek zostanie wznowiony.

*Pred*\
Dowolne wyrażenie zwracające **`true`** lub **`false`** .

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca, `cv_status::timeout` Jeśli oczekiwanie zakończy się po upłynięciu *Rel_time* . W przeciwnym razie metoda zwraca `cv_status::no_timeout` .

Druga metoda zwraca wartość *pred*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do momentu `condition_variable_any` zasygnalizowania obiektu przez wywołanie do [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all)lub do czasu, aż upłynie *Rel_time* przedział czasu. Może również wzbudzać obudzić.

Druga metoda w efekcie wykonuje Poniższy kod.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a><a name="wait_until"></a> wait_until

Blokuje wątek i ustawia maksymalny punkt w czasie, w którym odblokowuje wątek.

```cpp
template <class Lock, class Clock, class Duration>
void wait_until(Lock& Lck, const chrono::time_point<Clock, Duration>& Abs_time);

template <class Lock, class Clock, class Duration, class Predicate>
void wait_until(
    Lock& Lck,
    const chrono::time_point<Clock, Duration>& Abs_time,
    Predicate Pred);

template <class Lock>
void wait_until(Lock Lck, const xtime* Abs_time);

template <class Lock, class Predicate>
void wait_until(
    Lock Lck,
    const xtime* Abs_time,
    Predicate Pred);
```

### <a name="parameters"></a>Parametry

*LCK*\
Obiekt mutex.

*Abs_time*\
Obiekt [chrono:: time_point](../standard-library/time-point-class.md) .

*Pred*\
Dowolne wyrażenie zwracające **`true`** lub **`false`** .

### <a name="return-value"></a>Wartość zwracana

Metody, które zwracają `cv_status` Typ Return, `cv_status::timeout` Jeśli oczekiwania zakończy się po upłynięciu *Abs_time* . W przeciwnym razie metody zwracają `cv_status::no_timeout` .

Metody zwracające **`bool`** zwraca wartość *pred*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do momentu `condition_variable` zasygnalizowania obiektu przez wywołanie do [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all)lub do momentu *Abs_time*. Może również wzbudzać obudzić.

Druga metoda w efekcie wykonuje Poniższy kod.

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Trzecia i czwarta Metoda używa wskaźnika do obiektu typu `xtime` , aby zastąpić `chrono::time_point` obiekt. `xtime`Obiekt Określa maksymalną ilość czasu oczekiwania na sygnał.
