---
title: future — Klasa
ms.date: 11/04/2016
f1_keywords:
- future/std::future
- future/std::future::future
- future/std::future::get
- future/std::future::share
- future/std::future::valid
- future/std::future::wait
- future/std::future::wait_for
- future/std::future::wait_until
ms.assetid: 495e82c3-5341-4e37-87dd-b40107fbdfb6
helpviewer_keywords:
- std::future [C++]
- std::future [C++], future
- std::future [C++], get
- std::future [C++], share
- std::future [C++], valid
- std::future [C++], wait
- std::future [C++], wait_for
- std::future [C++], wait_until
ms.openlocfilehash: 9ca18e62038d93a50b592868f71223962a22857d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159330"
---
# <a name="future-class"></a>future — Klasa

W tym artykule opisano *asynchronicznego zwrotu obiektu*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Uwagi

Poszczególnym *dostawcę asynchronicznego* zwraca obiekt, którego typem jest egzemplarzem z tego szablonu. Element `future` obiektu zapewnia tylko dostęp do asynchronicznego dostawcy, który jest skojarzony. Jeśli potrzebujesz wielu asynchronicznego zwrotu obiektów, które są skojarzone z tego samego dostawcę asynchronicznego, skopiuj `future` obiekt [shared_future](../standard-library/shared-future-class.md) obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[przyszłe](#future)|Konstruuje `future` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Pobiera wynik, który znajduje się w stanie stowarzyszonym asynchroniczne.|
|[Udostępnij](#share)|Konwertuje obiekt na potrzeby `shared_future`.|
|[Nieprawidłowa](#valid)|Określa, czy obiekt nie jest pusty.|
|[Czekaj](#wait)|Blokuje bieżący wątek, aż asynchronicznego stanu stowarzyszonego będzie gotowa.|
|[wait_for](#wait_for)|Bloki, aż do asynchronicznego stanu stowarzyszonego jest gotowy, lub do określonego czasu upłynął.|
|[wait_until](#wait_until)|Bloki, aż do asynchronicznego stanu stowarzyszonego jest gotowy, lub do momentu określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Future::operator =](#op_eq)|Przesyła asynchronicznego stanu stowarzyszonego z określonego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłych >

**Namespace:** standardowe

## <a name="future"></a>  Future::Future — Konstruktor

Konstruuje `future` obiektu.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Inne*<br/>
Element `future` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `future` asynchroniczny stan stowarzyszony obiektu, który nie ma.

Drugi Konstruktor konstruuje `future` obiekt i dokonuje transferu asynchronicznego stanu stowarzyszonego z *innych*. *Inne* nie posiada już stowarzyszonego stanu asynchronicznego.

## <a name="get"></a>  Future::Get —

Pobiera wynik, który znajduje się w stanie stowarzyszonym asynchroniczne.

```cpp
Ty get();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik jest wyjątek, metoda ponownie zgłasza go. W przeciwnym razie wynik jest zwracany.

### <a name="remarks"></a>Uwagi

Zanim pobiera wynik, ta metoda blokują bieżący wątek, aż asynchronicznego stanu stowarzyszonego będzie gotowa.

Przypadku częściowej specjalizacji `future<Ty&>`, wartość przechowywana jest skutecznym odniesieniem do obiektu, który został przekazany do dostawcę asynchronicznego jako wartość zwracaną.

Ponieważ przechowywana wartość nie istnieje w przypadku specjalizacji `future<void>`, metoda zwraca **void**.

W innym specjalizacje metody przenosi jego wartość zwrotną z wartości przechowywanej. Wywołaj tę metodę w związku z tym, tylko raz.

## <a name="op_eq"></a>  Future::operator =

Przesyła asynchronicznego stanu stowarzyszonego z określonego obiektu.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
Element `future` obiektu.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Po przesłaniu *po prawej stronie* nie posiada już stowarzyszonego stanu asynchronicznego.

## <a name="share"></a>  Future::share —

Konwertuje obiekt na potrzeby [shared_future](../standard-library/shared-future-class.md) obiektu.

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Wartość zwracana

`shared_future(move(*this))`

## <a name="valid"></a>  Future::valid —

Określa, czy obiekt posiada asynchronicznego stanu stowarzyszonego.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli obiekt ma asynchronicznego stanu stowarzyszonego; w przeciwnym razie **false**.

## <a name="wait"></a>  Future::wait —

Blokuje bieżący wątek, dopóki nie zostanie asynchronicznego stanu stowarzyszonego *gotowe*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Jest asynchronicznego stanu stowarzyszonego *gotowe* tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

## <a name="wait_for"></a>  Future::wait_for —

Blokuje bieżący wątek, dopóki nie zostanie asynchronicznego stanu stowarzyszonego *gotowe* lub dopóki nie upłynie określony przedział czasu.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*<br/>
A [chrono::duration](../standard-library/duration-class.md) obiekt, który określa przedział czasu maksymalna, która blokuje wątek.

### <a name="return-value"></a>Wartość zwracana

A [future_status —](../standard-library/future-enums.md#future_status) oznacza Przyczyna zwrotu.

### <a name="remarks"></a>Uwagi

Asynchronicznego stanu stowarzyszonego jest gotowy, tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

## <a name="wait_until"></a>  Future::wait_until —

Blokuje bieżący wątek, dopóki nie zostanie asynchronicznego stanu stowarzyszonego *gotowe* lub dopiero po określonym czasie punktu.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*<br/>
A [chrono::time_point](../standard-library/time-point-class.md) obiektu, który określa czas, po którym można odblokować wątku.

### <a name="return-value"></a>Wartość zwracana

A [future_status —](../standard-library/future-enums.md#future_status) oznacza Przyczyna zwrotu.

### <a name="remarks"></a>Uwagi

Jest asynchronicznego stanu stowarzyszonego *gotowe* tylko wtedy, gdy jego dostawcę asynchronicznego jest przechowywana wartość zwracaną lub przechowywane wyjątek.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<future>](../standard-library/future.md)<br/>
