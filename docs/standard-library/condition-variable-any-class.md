---
title: condition_variable_any — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- condition_variable/std::condition_variable_any
- condition_variable/std::condition_variable_any::condition_variable_any
- condition_variable/std::condition_variable_any::notify_all
- condition_variable/std::condition_variable_any::notify_one
- condition_variable/std::condition_variable_any::wait
- condition_variable/std::condition_variable_any::wait_for
- condition_variable/std::condition_variable_any::wait_until
dev_langs:
- C++
ms.assetid: d8afe5db-1561-4ec2-8e85-21ea03ee4321
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::condition_variable_any
- std::condition_variable_any::condition_variable_any
- std::condition_variable_any::notify_all
- std::condition_variable_any::notify_one
- std::condition_variable_any::wait
- std::condition_variable_any::wait_for
- std::condition_variable_any::wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: f0fe38031dc215f537d82fe6e06f68acf6db8e0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="conditionvariableany-class"></a>condition_variable_any — Klasa

Klasa `condition_variable_any` oczekiwania na zdarzenie, które ma jakiekolwiek `mutex` typu.

## <a name="syntax"></a>Składnia

```cpp
class condition_variable_any;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[condition_variable_any](#condition_variable_any)|Konstruuje `condition_variable_any` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[notify_all](#notify_all)|Odblokowuje wszystkie wątki, które oczekują na `condition_variable_any` obiektu.|
|[notify_one](#notify_one)|Jeden z wątków, które oczekują na odblokowuje `condition_variable_any` obiektu.|
|[oczekiwania](#wait)|Blokuje wątku.|
|[wait_for](#wait_for)|Blokuje wątku i ustawia przedział czasu, po którym odblokowuje wątku.|
|[wait_until](#wait_until)|Blokuje wątku i ustawia maksymalną punktu w czasie, w którym odblokowuje wątku.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<condition_variable — >

**Namespace:** Standard

## <a name="condition_variable_any"></a>  condition_variable_any::condition_variable_any — Konstruktor

Konstruuje `condition_variable_any` obiektu.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>Uwagi

Jeśli nie ma wystarczającej ilości pamięci jest dostępny, zgłasza konstruktora [system_error —](../standard-library/system-error-class.md) obiektu, który ma `not_enough_memory` kod błędu. Jeśli nie można utworzyć obiektu, ponieważ innego zasobu nie jest dostępna, zgłasza konstruktora `system_error` obiektu, który ma `resource_unavailable_try_again` kod błędu.

## <a name="notify_all"></a>  condition_variable_any::notify_all

Odblokowuje wszystkie wątki, które oczekują na `condition_variable_any` obiektu.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable_any::notify_one

Jeden z wątków, które oczekują na odblokowuje `condition_variable_any` obiektu.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable_any::wait

Blokuje wątku.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

`Lck` A `mutex` obiekt dowolnego typu.

`Pred` Dowolne wyrażenie zwracające `true` lub `false`.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable_any` obiektu zostanie zasygnalizowane przez wywołanie do [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all). On również wybudzania spuriously.

Druga metoda wykonuje skutkuje poniższy kod.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable_any::wait_for

Blokuje wątku i ustawia przedział czasu, po którym odblokowuje wątku.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>Parametry

`Lck` A `mutex` obiekt dowolnego typu.

`Rel_time` A `chrono::duration` obiekt, który określa ilość czasu przed wątku zostanie wznowiona.

`Pred` Dowolne wyrażenie zwracające `true` lub `false`.

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `cv_status::timeout` jeśli kończy czas oczekiwania, kiedy `Rel_time` upłynął. W przeciwnym razie metoda zwraca `cv_status::no_timeout`.

Druga metoda zwraca wartość `Pred`.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable_any` obiektu zostanie zasygnalizowane przez wywołanie do [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all), lub do czasu przedział czasu `Rel_time` upłynął. On również wybudzania spuriously.

Druga metoda wykonuje skutkuje poniższy kod.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable_any::wait_until

Blokuje wątku i ustawia maksymalną punktu w czasie, w którym odblokowuje wątku.

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

`Lck` Obiektu mutex.

`Abs_time` A [chrono::time_point](../standard-library/time-point-class.md) obiektu.

`Pred` Dowolne wyrażenie zwracające `true` lub `false`.

### <a name="return-value"></a>Wartość zwracana

Metody zwracające `cv_status` typ zwracany `cv_status::timeout` jeśli kończy czas oczekiwania, kiedy `Abs_time` upływa. W przeciwnym razie zwracany metody `cv_status::no_timeout`.

Metody zwracające `bool` zwrócić wartość `Pred`.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable` obiektu zostanie zasygnalizowane przez wywołanie do [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all), lub do czasu `Abs_time`. On również wybudzania spuriously.

Druga metoda wykonuje skutkuje poniższy kod.

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Metody trzeci i czwarty używać wskaźnika do obiektu typu `xtime` zastąpić `chrono::time_point` obiektu. `xtime` Obiektu określa maksymalną ilość czasu oczekiwania na sygnał.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[<condition_variable>](../standard-library/condition-variable.md)<br/>
