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
ms.openlocfilehash: c38c080b0a8dbd9d4b0b76496aa367fa55892f50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279061"
---
# <a name="conditionvariableany-class"></a>condition_variable_any — Klasa

Korzystanie z klasy `condition_variable_any` oczekiwania na zdarzenie, które ma jakiekolwiek `mutex` typu.

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
|[notify_one](#notify_one)|Odblokowuje jeden z wątków, które oczekują na `condition_variable_any` obiektu.|
|[Czekaj](#wait)|Blokuje wątek.|
|[wait_for](#wait_for)|Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.|
|[wait_until](#wait_until)|Blokuje wątek i ustawia maksymalny punkt w czasie, w którym odblokowuje wątek.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<condition_variable >

**Namespace:** standardowe

## <a name="condition_variable_any"></a>  condition_variable_any::condition_variable_any — Konstruktor

Konstruuje `condition_variable_any` obiektu.

```cpp
condition_variable_any();
```

### <a name="remarks"></a>Uwagi

Jeśli nie ma wystarczającej ilości pamięci jest dostępny, Konstruktor wyrzuca [system_error](../standard-library/system-error-class.md) obiekt, który ma `not_enough_memory` kod błędu. Jeśli nie można utworzyć obiektu, ponieważ niektóre inne zasoby nie są dostępne, Konstruktor wyrzuca `system_error` obiekt, który ma `resource_unavailable_try_again` kod błędu.

## <a name="notify_all"></a>  condition_variable_any::notify_all —

Odblokowuje wszystkie wątki, które oczekują na `condition_variable_any` obiektu.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable_any::notify_one —

Odblokowuje jeden z wątków, które oczekują na `condition_variable_any` obiektu.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable_any::wait —

Blokuje wątek.

```cpp
template <class Lock>
void wait(Lock& Lck);

template <class Lock, class Predicate>
void wait(Lock& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*Lck*<br/>
A `mutex` obiekt dowolnego typu.

*P.*<br/>
Dowolne wyrażenie zwracające **true** lub **false**.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable_any` zasygnalizowania obiektu przez wywołanie [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all). Go może również obudzić błędnie.

Druga metoda wykonuje obowiązuje następujący kod.

```cpp
while (!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable_any::wait_for —

Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.

```cpp
template <class Lock, class Rep, class Period>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time);

template <class Lock, class Rep, class Period, class Predicate>
bool wait_for(Lock& Lck, const chrono::duration<Rep, Period>& Rel_time, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*Lck*<br/>
A `mutex` obiekt dowolnego typu.

*Rel_time*<br/>
Element `chrono::duration` obiektu, który określa ilość czasu przed wątek zostanie wznowiona.

*P.*<br/>
Dowolne wyrażenie zwracające **true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `cv_status::timeout` Jeśli skończy się czas oczekiwania, gdy *Rel_time* upłynął. W przeciwnym razie metoda zwraca `cv_status::no_timeout`.

Druga metoda zwraca wartość *p*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable_any` zasygnalizowania obiektu przez wywołanie [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all), lub do momentu aż interwał czasowy *Rel_time* upłynął. Go może również obudzić błędnie.

Druga metoda wykonuje obowiązuje następujący kod.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable_any::wait_until —

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

*Lck*<br/>
Obiekt wzajemnego wykluczania mutex.

*Abs_time*<br/>
A [chrono::time_point](../standard-library/time-point-class.md) obiektu.

*P.*<br/>
Dowolne wyrażenie zwracające **true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Metody, które zwracają `cv_status` wpisz powrotu `cv_status::timeout` Jeśli skończy się czas oczekiwania, gdy *Abs_time* upływa. W przeciwnym razie metody zwracają `cv_status::no_timeout`.

Metody, które zwracają `bool` zwracają wartość *p*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](../standard-library/condition-variable-class.md#notify_one) lub [notify_all](../standard-library/condition-variable-class.md#notify_all), lub do momentu *Abs_time*. Go może również obudzić błędnie.

Druga metoda wykonuje obowiązuje następujący kod.

```cpp
while(!Pred())
    if(wait_until(Lck, Abs_time) == cv_status::timeout)
    return Pred();

return true;
```

Metody trzecia i czwarta za pomocą wskaźnika do obiektu typu `xtime` zastąpić `chrono::time_point` obiektu. `xtime` Obiektu określa maksymalną ilość czasu oczekiwania na sygnał.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[<condition_variable>](../standard-library/condition-variable.md)<br/>
