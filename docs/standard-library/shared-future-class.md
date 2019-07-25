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
ms.openlocfilehash: 3b08a1341ed450dd5d5cee93cdfcbab57f8d6760
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450491"
---
# <a name="sharedfuture-class"></a>shared_future — Klasa

Opisuje *asynchroniczny obiekt Return*. W przeciwieństwie do [przyszłego](../standard-library/future-class.md) obiektu *dostawca asynchroniczny* może być skojarzony z `shared_future` dowolną liczbą obiektów.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Uwagi

Nie wywołuj żadnych metod innych `valid`niż, `operator=`i destruktora na `shared_future` obiekcie, który jest *pusty*.

`shared_future`obiekty nie są zsynchronizowane. Wywoływanie metod na tym samym obiekcie z wielu wątków wprowadza rasę danych, który ma nieprzewidywalne wyniki.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future](#shared_future)|Konstruuje `shared_future` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Pobiera wynik, który jest przechowywany w *skojarzonym stanie asynchronicznym*.|
|[prawidłowa](#valid)|Określa, czy obiekt nie jest pusty.|
|[trwa](#wait)|Blokuje bieżący wątek do momentu, gdy skojarzony stan asynchroniczny jest gotowy.|
|[wait_for](#wait_for)|Bloki do momentu, aż skojarzony stan asynchroniczny jest gotowy lub dopóki nie upłynie określony czas.|
|[wait_until](#wait_until)|Bloki do momentu, aż skojarzony stan asynchroniczny jest gotowy lub do określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future:: operator =](#op_eq)|Przypisuje nowy, skojarzony stan asynchroniczny.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłe >

**Przestrzeń nazw:** std

## <a name="get"></a>shared_future:: Get

Pobiera wynik, który jest przechowywany w *skojarzonym stanie asynchronicznym*.

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Uwagi

Jeśli wynikiem jest wyjątek, Metoda ponownie zgłosi ją. W przeciwnym razie zwracany jest wynik.

Przed pobraniem wyniku ta metoda blokuje bieżący wątek do momentu, gdy skojarzony stan asynchroniczny będzie gotowy.

W przypadku częściowej specjalizacji `shared_future<Ty&>`przechowywana wartość jest efektywnie odwołaniem do obiektu, który został przekazano do *dostawcy asynchronicznego* jako wartość zwracana.

Ponieważ nie istnieje wartość składowana dla specjalizacji `shared_future<void>`, metoda zwraca wartość **void**.

## <a name="op_eq"></a>shared_future:: operator =

Przenosi *skojarzony stan asynchroniczny* z określonego obiektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
`shared_future` Obiekt.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

W przypadku pierwszego operatora *prawo* nie ma już skojarzonego stanu asynchronicznego po operacji.

W przypadku drugiej metody, *prawo* zachowuje swój skojarzony stan asynchroniczny.

## <a name="shared_future"></a>shared_future:: shared_future — Konstruktor

Konstruuje `shared_future` obiekt.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
[Przyszłość](../standard-library/future-class.md) lub `shared_future` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje `shared_future` obiekt, który nie ma *skojarzonego stanu asynchronicznego*.

Drugi i trzeci konstruktory konstruują `shared_future` obiekt i przesyłają skojarzony stan asynchroniczny z *prawej strony*. *Prawo* nie ma już skojarzonego stanu asynchronicznego.

Czwarty Konstruktor konstruuje `shared_future` obiekt, który ma ten sam skojarzony stan asynchroniczny jako *prawo*.

## <a name="valid"></a>shared_future:: prawidłowe

Określa, czy obiekt ma *skojarzony stan asynchroniczny*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

ma **wartość true** , jeśli obiekt ma skojarzony stan asynchroniczny; w przeciwnym razie **false**.

## <a name="wait"></a>shared_future:: wait

Blokuje bieżący wątek do momentu, gdy *skojarzony stan asynchroniczny* jest *gotowy*.

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczny jest gotowy tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

## <a name="wait_for"></a>shared_future::wait_for

Blokuje bieżący wątek do momentu, aż skojarzony stan asynchroniczny jest *gotowy* lub dopóki nie upłynie określony czas.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
Obiekt [chrono::d wersja](../standard-library/duration-class.md) , który określa maksymalny przedział czasu, który jest blokowany przez wątek.

### <a name="return-value"></a>Wartość zwracana

Element [future_status](../standard-library/future-enums.md#future_status) , który wskazuje przyczynę zwrócenia.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczny jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

## <a name="wait_until"></a>shared_future::wait_until

Blokuje bieżący wątek do momentu, aż skojarzony stan asynchroniczny jest *gotowy* lub do momentu po określonym punkcie czasu.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
Obiekt [chrono:: time_point](../standard-library/time-point-class.md) , który określa czas, po którym wątek może zostać odblokowany.

### <a name="return-value"></a>Wartość zwracana

Element [future_status](../standard-library/future-enums.md#future_status) , który wskazuje przyczynę zwrócenia.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczny jest gotowy tylko wtedy, gdy jego dostawca asynchroniczny przechowuje wartość zwracaną lub zgłosił wyjątek.

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
