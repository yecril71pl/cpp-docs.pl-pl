---
title: condition_variable, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- condition_variable/std::condition
- condition_variable/std::condition_variable::condition_variable
- condition_variable/std::condition_variable::native_handle
- condition_variable/std::condition_variable::notify_all
- condition_variable/std::condition_variable::notify_one
- condition_variable/std::condition_variable::wait
- condition_variable/std::condition_variable::wait_for
- condition_variable/std::condition_variable::wait_until
dev_langs:
- C++
ms.assetid: 80b1295c-b73d-4d46-b664-6e183f2eec1b
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::condition
- std::condition_variable::condition_variable
- std::condition_variable::native_handle
- std::condition_variable::notify_all
- std::condition_variable::notify_one
- std::condition_variable::wait
- std::condition_variable::wait_for
- std::condition_variable::wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: ca85765d6fed21938a61f52f25c1a377ec43c499
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965181"
---
# <a name="conditionvariable-class"></a>condition_variable — Klasa

Użyj `condition_variable` klasy oczekiwania na zdarzenie, kiedy masz `mutex` typu `unique_lock<mutex>`. Obiekty tego typu może mieć lepszą wydajność niż obiekty typu [condition_variable_any < unique_lock\<mutex >>](../standard-library/condition-variable-any-class.md).

## <a name="syntax"></a>Składnia

```cpp
class condition_variable;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[condition_variable](#condition_variable)|Konstruuje `condition_variable` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[native_handle —](#native_handle)|Zwraca typ implementacji reprezentujący dojście condition_variable.|
|[notify_all](#notify_all)|Odblokowuje wszystkie wątki, które oczekują na `condition_variable` obiektu.|
|[notify_one](#notify_one)|Odblokowuje jeden z wątków, które oczekują na `condition_variable` obiektu.|
|[Czekaj](#wait)|Blokuje wątek.|
|[wait_for](#wait_for)|Blokuje wątek i ustawia przedział czasu, po którym odblokowuje wątek.|
|[wait_until](#wait_until)|Blokuje wątek i ustawia maksymalny punkt w czasie, w którym odblokowuje wątek.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<condition_variable >

**Namespace:** standardowe

## <a name="condition_variable"></a>  condition_variable::condition_variable — Konstruktor

Konstruuje `condition_variable` obiektu.

```cpp
condition_variable();
```

### <a name="remarks"></a>Uwagi

Jeśli nie ma wystarczającej ilości pamięci jest dostępny, Konstruktor wyrzuca [system_error](../standard-library/system-error-class.md) obiekt, który ma `not_enough_memory` kod błędu. Jeśli nie można utworzyć obiektu, ponieważ niektóre inne zasoby nie są dostępne, Konstruktor wyrzuca `system_error` obiekt, który ma `resource_unavailable_try_again` kod błędu.

## <a name="native_handle"></a>  condition_variable::native_handle —

Zwraca typ implementacji reprezentujący dojście condition_variable.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Wartość zwracana

`native_handle_type` jest zdefiniowany jako wskaźnik do współbieżności środowiska wykonawczego wewnętrznych struktur danych.

## <a name="notify_all"></a>  condition_variable::notify_all —

Odblokowuje wszystkie wątki, które oczekują na `condition_variable` obiektu.

```cpp
void notify_all() noexcept;
```

## <a name="notify_one"></a>  condition_variable::notify_one —

Odblokowuje jeden z wątków, które oczekują na `condition_variable` obiektu.

```cpp
void notify_one() noexcept;
```

## <a name="wait"></a>  condition_variable::wait —

Blokuje wątek.

```cpp
void wait(unique_lock<mutex>& Lck);

template <class Predicate>
void wait(unique_lock<mutex>& Lck, Predicate Pred);
```

### <a name="parameters"></a>Parametry

*Lck* A [unique_lock\<mutex >](../standard-library/unique-lock-class.md) obiektu.

*P.* dowolne wyrażenie zwracające **true** lub **false**.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](#notify_one) lub [notify_all](#notify_all). Go może również obudzić błędnie.

W efekcie druga metoda wykonuje następujący kod.

```cpp
while(!Pred())
    wait(Lck);
```

## <a name="wait_for"></a>  condition_variable::wait_for —

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

*Lck* A [unique_lock\<mutex >](../standard-library/unique-lock-class.md) obiektu.

*Rel_time* A `chrono::duration` obiektu, który określa ilość czasu przed wątek zostanie wznowiona.

*P.* dowolne wyrażenie zwracające **true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Pierwsza metoda zwraca `cv_status::timeout` Jeśli skończy się czas oczekiwania, gdy *Rel_time* upłynął. W przeciwnym razie metoda zwraca `cv_status::no_timeout`.

Druga metoda zwraca wartość *p*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](#notify_one) lub [notify_all](#notify_all) lub do momentu aż interwał czasowy *Rel_time* upłynął. Go może również obudzić błędnie.

W efekcie druga metoda wykonuje następujący kod.

```cpp
while(!Pred())
    if(wait_for(Lck, Rel_time) == cv_status::timeout)
    return Pred();

return true;
```

## <a name="wait_until"></a>  condition_variable::wait_until —

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

*Lck* A [unique_lock\<mutex >](../standard-library/unique-lock-class.md) obiektu.

*Abs_time* A [chrono::time_point](../standard-library/time-point-class.md) obiektu.

*P.* dowolne wyrażenie zwracające **true** lub **false**.

### <a name="return-value"></a>Wartość zwracana

Metody, które zwracają `cv_status` wpisz powrotu `cv_status::timeout` Jeśli skończy się czas oczekiwania, gdy *Abs_time* upływa. W przeciwnym razie metody zwracają `cv_status::no_timeout`.

Metody, które zwracają **bool** zwracają wartość *p*.

### <a name="remarks"></a>Uwagi

Pierwsza metoda blokuje do `condition_variable` zasygnalizowania obiektu przez wywołanie [notify_one](#notify_one) lub [notify_all](#notify_all) lub do momentu `Abs_time`. Go może również obudzić błędnie.

W efekcie druga metoda wykonuje następujący kod

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
