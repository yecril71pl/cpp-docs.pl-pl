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
ms.openlocfilehash: ac52429919f83a90a87141399952e248e18e0862
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220941"
---
# <a name="future-class"></a>future — Klasa

Opisuje *asynchroniczny obiekt Return*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Uwagi

Każdy standardowy *dostawca asynchroniczny* zwraca obiekt, którego typ jest wystąpieniem tego szablonu. `future`Obiekt zapewnia jedyny dostęp do dostawcy asynchronicznego, z którym jest skojarzony. Jeśli potrzebujesz wielu obiektów zwrotów asynchronicznych, które są skojarzone z tym samym dostawcą asynchronicznym, skopiuj `future` obiekt do [shared_future](../standard-library/shared-future-class.md) obiektu.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[kontrakt](#future)|Konstruuje `future` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Pobierz](#get)|Pobiera wynik, który jest przechowywany w skojarzonym stanie asynchronicznym.|
|[udostępnij](#share)|Konwertuje obiekt na `shared_future` .|
|[prawidłowa](#valid)|Określa, czy obiekt nie jest pusty.|
|[trwa](#wait)|Blokuje bieżący wątek do momentu, gdy skojarzony stan asynchroniczny jest gotowy.|
|[wait_for](#wait_for)|Bloki do momentu, aż skojarzony stan asynchroniczny jest gotowy lub dopóki nie upłynie określony czas.|
|[wait_until](#wait_until)|Bloki do momentu, aż skojarzony stan asynchroniczny jest gotowy lub do określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Future:: operator =](#op_eq)|Przenosi skojarzony stan asynchroniczny z określonego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<future>

**Przestrzeń nazw:** std

## <a name="futurefuture-constructor"></a><a name="future"></a>Future:: Future — Konstruktor

Konstruuje `future` obiekt.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Różnych*\
Obiekt `future`.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `future` obiekt, który nie ma skojarzonego stanu asynchronicznego.

Drugi Konstruktor konstruuje `future` obiekt i transferuje związany z nim stan asynchroniczny. *Other* *Inne* nie mają już skojarzonego stanu asynchronicznego.

## <a name="futureget"></a><a name="get"></a>przyszłość:: Get

Pobiera wynik, który jest przechowywany w skojarzonym stanie asynchronicznym.

```cpp
Ty get();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wynikiem jest wyjątek, Metoda ponownie zgłosi ją. W przeciwnym razie zwracany jest wynik.

### <a name="remarks"></a>Uwagi

Przed pobraniem wyniku ta metoda blokuje bieżący wątek do momentu, gdy skojarzony stan asynchroniczny będzie gotowy.

W przypadku częściowej specjalizacji `future<Ty&>` przechowywana wartość jest efektywnie odwołaniem do obiektu, który został przekazano do dostawcy asynchronicznego jako wartość zwracana.

Ponieważ nie istnieje przechowywana wartość dla specjalizacji `future<void>` , metoda zwraca **`void`** .

W innych specjalizacjach Metoda przenosi wartość zwracaną z wartości przechowywanej. W związku z tym należy wywołać tę metodę tylko raz.

## <a name="futureoperator"></a><a name="op_eq"></a>Future:: operator =

Przenosi skojarzony stan asynchroniczny z określonego obiektu.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt `future`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Po przeniesieniu *nie ma* już skojarzonego stanu asynchronicznego.

## <a name="futureshare"></a><a name="share"></a>przyszłość:: udostępnianie

Konwertuje obiekt na obiekt [shared_future](../standard-library/shared-future-class.md) .

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Wartość zwracana

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>przyszłość:: prawidłowe

Określa, czy obiekt ma skojarzony stan asynchroniczny.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli obiekt ma skojarzony stan asynchroniczny; w przeciwnym razie **`false`** .

## <a name="futurewait"></a><a name="wait"></a>przyszłość:: czekaj

Blokuje bieżący wątek do momentu, gdy skojarzony stan asynchroniczny jest *gotowy*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczny jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

## <a name="futurewait_for"></a><a name="wait_for"></a>przyszłość:: wait_for

Blokuje bieżący wątek do momentu, aż skojarzony stan asynchroniczny jest *gotowy* lub dopóki nie upłynie określony przedział czasu.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalny przedział czasu, który jest blokowany przez wątek.

### <a name="return-value"></a>Wartość zwracana

[Future_status](../standard-library/future-enums.md#future_status) , który wskazuje przyczynę zwrócenia.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczny jest gotowy tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

## <a name="futurewait_until"></a><a name="wait_until"></a>przyszłość:: wait_until

Blokuje bieżący wątek do momentu, aż skojarzony stan asynchroniczny jest *gotowy* lub do momentu po określonym punkcie czasu.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Obiekt [chrono:: time_point](../standard-library/time-point-class.md) , który określa czas, po którym wątek może zostać odblokowany.

### <a name="return-value"></a>Wartość zwracana

[Future_status](../standard-library/future-enums.md#future_status) , który wskazuje przyczynę zwrócenia.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczny jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
