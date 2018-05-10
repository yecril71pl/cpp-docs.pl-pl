---
title: shared_future — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
dev_langs:
- C++
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac125b068de5111a2b98800956c12a0c979737f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="sharedfuture-class"></a>shared_future — Klasa

W tym artykule opisano *asynchronicznego obiektu zwracanego*. Contrast z [przyszłych](../standard-library/future-class.md) obiektu *asynchroniczne dostawcy* można skojarzyć z dowolną liczbę `shared_future` obiektów.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Uwagi

Nie wymagają żadnych metod innych niż `valid`, `operator=`, a destruktor na `shared_future` obiektu to jest *pusty*.

`shared_future` obiekty nie są zsynchronizowane. Wywoływanie metody dla tego samego obiektu z wielu wątków wprowadza wyścigu danych, która ma nieprzewidywalne skutki.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future](#shared_future)|Konstruuje `shared_future` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Pobiera wynik, który jest przechowywany w *skojarzony stan asynchronicznego*.|
|[Nieprawidłowa](#valid)|Określa, czy obiekt nie jest pusty.|
|[oczekiwania](#wait)|Blokuje bieżącego wątku, dopóki skojarzony stan asynchroniczne jest gotowy.|
|[wait_for](#wait_for)|Bloki do skojarzony stan asynchroniczne jest gotowy lub przed upływem czasu określonego.|
|[wait_until](#wait_until)|Bloki do skojarzony stan asynchroniczne jest gotowe lub do określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future::operator =](#op_eq)|Przypisuje nowy skojarzony stan asynchronicznego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłych >

**Namespace:** Standard

## <a name="get"></a>  shared_future::Get

Pobiera wynik, który jest przechowywany w *skojarzony stan asynchronicznego*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Uwagi

Jeśli wynik wynosi wyjątek, metoda ponownie zgłasza wyjątek go. W przeciwnym razie wynik zostanie zwrócony.

Przed jego pobiera wynik, ta metoda blokuje bieżący wątek aż skojarzony stan asynchronicznego będzie gotowa.

Dla specjalizacji częściowej `shared_future<Ty&>`, przechowywana wartość jest odwołanie do obiektu, który został przekazany do *asynchroniczne dostawcy* jako wartości zwracane.

Ponieważ przechowywanych wartość nie istnieje dla specjalizacji `shared_future<void>`, metoda zwraca `void`.

## <a name="op_eq"></a>  shared_future::operator =

Transfery *skojarzony stan asynchronicznego* od określonego obiektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

`Right` A `shared_future` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Dla pierwszego operatora `Right` nie ma już skojarzony stan asynchronicznych po wykonaniu operacji.

W przypadku drugiego metody `Right` zachowuje jego skojarzony stan asynchronicznego.

## <a name="shared_future"></a>  shared_future::shared_future — Konstruktor

Konstruuje `shared_future` obiektu.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

`Right` A [przyszłych](../standard-library/future-class.md) lub `shared_future` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy konstrukcje konstruktora `shared_future` obiektu, którego nie zdefiniowano *skojarzony stan asynchronicznego*.

Utworzyć drugi i trzeci konstruktorów `shared_future` obiektu i transfer skojarzony stan asynchroniczne z `Right`. `Right` nie ma już skojarzony stan asynchronicznego.

Czwarty konstrukcje konstruktora `shared_future` obiektu, który ma taką samą skojarzony stan asynchronicznych jako `Right`.

## <a name="valid"></a>  shared_future::valid

Określa, czy obiekt ma *skojarzony stan asynchronicznego*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli obiekt ma skojarzony stan asynchronicznego; w przeciwnym razie `false`.

## <a name="wait"></a>  shared_future::wait

Blokuje bieżącego wątku do *skojarzony stan asynchronicznego* jest *gotowe*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest gotowy, tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.

## <a name="wait_for"></a>  shared_future::wait_for

Blokuje bieżącego wątku, dopóki nie zostanie skojarzony stan asynchronicznego *gotowe* lub przed upływem określonego czasu.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

`Rel_time` A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa maksymalny czas który bloki wątku.

### <a name="return-value"></a>Wartość zwracana

A [future_status —](../standard-library/future-enums.md#future_status) wskazujące przyczynę przekazujących.

### <a name="remarks"></a>Uwagi

Jest skojarzony stan asynchronicznego *gotowe* tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.

## <a name="wait_until"></a>  shared_future::wait_until

Blokuje bieżącego wątku, dopóki nie zostanie skojarzony stan asynchronicznego *gotowe* lub po określonym momencie.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

`Abs_time` A [chrono::time_point](../standard-library/time-point-class.md) obiektu, który określa czas, po którym można odblokować wątku.

### <a name="return-value"></a>Wartość zwracana

A [future_status —](../standard-library/future-enums.md#future_status) wskazujące przyczynę przekazujących.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest gotowy, tylko wtedy, gdy jego dostawcą asynchroniczne przechowywanego wartości zwracanej albo przechowywane Wystąpił wyjątek.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
