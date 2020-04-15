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
ms.openlocfilehash: 65ea01a9ced1ca69cd1b1526e7594c4b54387553
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336779"
---
# <a name="shared_future-class"></a>shared_future — Klasa

Opisuje *asynchroniiowy obiekt zwracany*. W przeciwieństwie do [przyszłego](../standard-library/future-class.md) obiektu *dostawcy asynchroniiowego* może `shared_future` być skojarzony z dowolną liczbą obiektów.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Uwagi

Nie należy wywoływać `valid`żadnych `operator=`metod innych niż , `shared_future` i destruktora na obiekcie, który jest *pusty*.

`shared_future`obiekty nie są synchronizowane. Wywoływanie metod na tym samym obiekcie z wielu wątków wprowadza wyścig danych, który ma nieprzewidywalne wyniki.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Shared_future](#shared_future)|Konstruuje `shared_future` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Pobiera wynik, który jest przechowywany w *skojarzonym stanie asynchroniza.*|
|[Prawidłowe](#valid)|Określa, czy obiekt nie jest pusty.|
|[Czekać](#wait)|Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne nie będzie gotowy.|
|[wait_for](#wait_for)|Blokuje, dopóki skojarzony stan asynchroniczne nie będzie gotowy lub do upływu określonego czasu.|
|[wait_until](#wait_until)|Blokuje, dopóki skojarzony stan asynchroniczne jest gotowy lub do określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|Przypisuje nowy skojarzony stan asynchroniczne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłe>

**Przestrzeń nazw:** std

## <a name="shared_futureget"></a><a name="get"></a>shared_future::get

Pobiera wynik, który jest przechowywany w *skojarzonym stanie asynchroniza.*

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Uwagi

Jeśli wynik jest wyjątkiem, metoda ponownie go wydwoje. W przeciwnym razie wynik jest zwracany.

Przed pobraniem wyniku, ta metoda blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne jest gotowy.

Dla częściowej `shared_future<Ty&>`specjalizacji wartość przechowywana jest skutecznie odwołanie do obiektu, który został przekazany do *dostawcy asynchronicznie* jako wartość zwracaną.

Ponieważ dla specjalizacji `shared_future<void>`nie istnieje żadna wartość przechowywana, metoda zwraca **void**.

## <a name="shared_futureoperator"></a><a name="op_eq"></a>shared_future::operator=

Przenosi *skojarzony stan asynchroniczne* z określonego obiektu.

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt `shared_future`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Dla pierwszego operatora *Right* nie ma już skojarzonego stanu asynchroniza po operacji.

Dla drugiej metody *Right* zachowuje skojarzony stan asynchroniczne.

## <a name="shared_futureshared_future-constructor"></a><a name="shared_future"></a>shared_future::shared_future konstruktor

Konstruuje `shared_future` obiekt.

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
[Przyszłość](../standard-library/future-class.md) lub `shared_future` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy `shared_future` obiekt, który nie ma *skojarzonego stanu asynchroniowego.*

Drugi i trzeci konstruktorzy konstruować `shared_future` obiekt i przenieść skojarzony stan asynchroniczne z *Right*. *Right* nie ma już skojarzonego stanu asynchroniowego.

Czwarty konstruktor tworzy `shared_future` obiekt, który ma ten sam skojarzony stan asynchroniczne jako *Right*.

## <a name="shared_futurevalid"></a><a name="valid"></a>shared_future::prawidłowy

Określa, czy obiekt ma *skojarzony stan asynchroniczne*.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekt ma skojarzony stan asynchroniczne; w przeciwnym razie **false**.

## <a name="shared_futurewait"></a><a name="wait"></a>shared_future::czekaj

Blokuje bieżący wątek, dopóki *skojarzony stan asynchroniczne nie* będzie *gotowy.*

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest gotowy tylko wtedy, gdy jego dostawca asynchroniczne ma przechowywane wartości zwracanej lub przechowywane wyjątek.

## <a name="shared_futurewait_for"></a><a name="wait_for"></a>shared_future::wait_for

Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne nie będzie *gotowy* lub do upływu określonego czasu.

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
A [chrono::duration](../standard-library/duration-class.md) obiektu, który określa maksymalny przedział czasu, który blokuje wątku.

### <a name="return-value"></a>Wartość zwracana

[Future_status,](../standard-library/future-enums.md#future_status) który wskazuje przyczynę powrotu.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczne ma przechowywane wartości zwracanej lub przechowywane wyjątek.

## <a name="shared_futurewait_until"></a><a name="wait_until"></a>shared_future::wait_until

Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne jest *gotowy* lub do momentu po określonym punkcie czasowym.

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
A [chrono::time_point](../standard-library/time-point-class.md) obiekt, który określa czas, po którym wątek może odblokować.

### <a name="return-value"></a>Wartość zwracana

[Future_status,](../standard-library/future-enums.md#future_status) który wskazuje przyczynę powrotu.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest gotowy tylko wtedy, gdy jego dostawca asynchroniczne ma przechowywane wartości zwracanej lub przechowywane wyjątek.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<przyszłych>](../standard-library/future.md)
