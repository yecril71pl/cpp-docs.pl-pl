---
title: shared_future — Klasa
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 2280c17c4ce58fe06365c107ad26d646c7ae2d72
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412608"
---
# <a name="sharedfuture-class"></a>shared_future — Klasa

W tym artykule opisano *asynchronicznego zwrotu obiektu*. W przeciwieństwie [przyszłych](../standard-library/future-class.md) obiektu *dostawcę asynchronicznego* można skojarzyć z dowolną liczbą `shared_future` obiektów.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Uwagi

Nie wywołuj żadnych metod innych niż `valid`, `operator=`i destruktor na `shared_future` obiektu to *pusty*.

`shared_future` obiekty nie są zsynchronizowane. Wywoływanie metod na tym samym obiekcie z wielu wątków wprowadza dane sytuacji wyścigu, która ma nieprzewidywalne rezultaty.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future](#shared_future)|Konstruuje `shared_future` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Pobiera wynik, który jest przechowywany w *asynchroniczny stan stowarzyszony*.|
|[Nieprawidłowa](#valid)|Określa, czy obiekt nie jest pusty.|
|[Czekaj](#wait)|Blokuje bieżący wątek, aż asynchronicznego stanu stowarzyszonego będzie gotowa.|
|[wait_for](#wait_for)|Bloki, aż do asynchronicznego stanu stowarzyszonego jest gotowy, lub do określonego czasu upłynął.|
|[wait_until](#wait_until)|Bloki, aż do asynchronicznego stanu stowarzyszonego jest gotowy, lub do momentu określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future::operator =](#op_eq)|Przypisuje nowy asynchronicznego stanu stowarzyszonego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłych >

**Namespace:** standardowe

## <a name="get"></a>  shared_future::Get —

Pobiera wynik, który jest przechowywany w *asynchroniczny stan stowarzyszony*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Uwagi

Jeśli wynik jest wyjątek, metoda ponownie zgłasza go. W przeciwnym razie wynik jest zwracany.

Zanim pobiera wynik, ta metoda blokują bieżący wątek, aż asynchronicznego stanu stowarzyszonego będzie gotowa.

Przypadku częściowej specjalizacji `shared_future<Ty&>`, wartość przechowywana jest skutecznym odniesieniem do obiektu, który został przekazany do *dostawcę asynchronicznego* jako wartość zwracaną.

Ponieważ przechowywana wartość nie istnieje w przypadku specjalizacji `shared_future<void>`, metoda zwraca **void**.

## <a name="op_eq"></a>  shared_future::operator =

Transfery *asynchroniczny stan stowarzyszony* od określonego obiektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
Element `shared_future` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Pierwszy operator *po prawej stronie* nie posiada już stowarzyszonego stanu asynchronicznego po wykonaniu operacji.

W przypadku drugiej metody *po prawej stronie* zachowuje jego asynchronicznie powiązanym stanie.

## <a name="shared_future"></a>  shared_future::shared_future — Konstruktor

Konstruuje `shared_future` obiektu.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
A [przyszłych](../standard-library/future-class.md) lub `shared_future` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `shared_future` obiektu, który nie ma *asynchroniczny stan stowarzyszony*.

Drugie i trzecie konstruktory konstruowania `shared_future` obiektu i transferu asynchronicznego stanu stowarzyszonego z *po prawej stronie*. *Po prawej stronie* nie posiada już stowarzyszonego stanu asynchronicznego.

Czwarty Konstruktor konstruuje `shared_future` asynchronicznego stanu jako skojarzony obiekt, który ma taką samą *po prawej stronie*.

## <a name="valid"></a>  shared_future::valid —

Określa, czy obiekt ma *asynchroniczny stan stowarzyszony*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt ma asynchronicznego stanu stowarzyszonego; w przeciwnym razie **false**.

## <a name="wait"></a>  shared_future::wait —

Blokuje bieżący wątek, dopóki *asynchroniczny stan stowarzyszony* jest *gotowe*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Asynchronicznego stanu stowarzyszonego jest gotowy, tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

## <a name="wait_for"></a>  shared_future::wait_for —

Blokuje bieżący wątek, dopóki nie zostanie asynchronicznego stanu stowarzyszonego *gotowe* lub dopóki nie upłynie czas określony.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa przedział czasu maksymalna, która blokuje wątek.

### <a name="return-value"></a>Wartość zwracana

A [future_status —](../standard-library/future-enums.md#future_status) oznacza Przyczyna zwrotu.

### <a name="remarks"></a>Uwagi

Jest asynchronicznego stanu stowarzyszonego *gotowe* tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

## <a name="wait_until"></a>  shared_future::wait_until —

Blokuje bieżący wątek, dopóki nie zostanie asynchronicznego stanu stowarzyszonego *gotowe* lub dopiero po określonym czasie punktu.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
A [chrono::time_point](../standard-library/time-point-class.md) obiektu, który określa czas, po którym można odblokować wątku.

### <a name="return-value"></a>Wartość zwracana

A [future_status —](../standard-library/future-enums.md#future_status) oznacza Przyczyna zwrotu.

### <a name="remarks"></a>Uwagi

Asynchronicznego stanu stowarzyszonego jest gotowy, tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
