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
ms.openlocfilehash: e71c750ddeb198faa3ae9c5960b2668c376241ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370701"
---
# <a name="future-class"></a>future — Klasa

Opisuje *asynchroniiowy obiekt zwracany*.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
class future;
```

## <a name="remarks"></a>Uwagi

Każdy *standardowy dostawca asynchroniczny* zwraca obiekt, którego typem jest wystąpienie tego szablonu. Obiekt `future` zapewnia jedyny dostęp do asynchronii dostawcy, z którymi jest skojarzony. Jeśli potrzebujesz wielu asynchronicznych zwracanych obiektów, które są skojarzone z `future` tym samym dostawcą asynchronii, skopiuj obiekt do [obiektu shared_future.](../standard-library/shared-future-class.md)

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Przyszłości](#future)|Konstruuje `future` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[get](#get)|Pobiera wynik, który jest przechowywany w skojarzonym stanie asynchroniza.|
|[udostępnij](#share)|Konwertuje obiekt `shared_future`na plik .|
|[Prawidłowe](#valid)|Określa, czy obiekt nie jest pusty.|
|[Czekać](#wait)|Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne nie będzie gotowy.|
|[wait_for](#wait_for)|Blokuje, dopóki skojarzony stan asynchroniczne nie będzie gotowy lub do upływu określonego czasu.|
|[wait_until](#wait_until)|Blokuje, dopóki skojarzony stan asynchroniczne jest gotowy lub do określonego punktu w czasie.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[przyszłość::operator=](#op_eq)|Przenosi skojarzony stan asynchroniczne z określonego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<przyszłe>

**Przestrzeń nazw:** std

## <a name="futurefuture-constructor"></a><a name="future"></a>przyszłość::przyszły konstruktor

Konstruuje `future` obiekt.

```cpp
future() noexcept;
future(future&& Other) noexcept;
```

### <a name="parameters"></a>Parametry

*Innych*\
Obiekt `future`.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy `future` obiekt, który nie ma skojarzonego stanu asynchroniowego.

Drugi konstruktor tworzy `future` obiekt i przenosi skojarzony stan asynchroniczne z *Other*. *Inne* nie ma już skojarzonego stanu asynchroniowego.

## <a name="futureget"></a><a name="get"></a>przyszłość::get

Pobiera wynik, który jest przechowywany w skojarzonym stanie asynchroniza.

```cpp
Ty get();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli wynik jest wyjątkiem, metoda ponownie go wydwoje. W przeciwnym razie wynik jest zwracany.

### <a name="remarks"></a>Uwagi

Przed pobraniem wyniku, ta metoda blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne jest gotowy.

Dla częściowej `future<Ty&>`specjalizacji wartość przechowywana jest skutecznie odwołanie do obiektu, który został przekazany do dostawcy asynchronicznie jako wartość zwracaną.

Ponieważ dla specjalizacji `future<void>`nie istnieje żadna wartość przechowywana, metoda zwraca **void**.

W innych specjalizacjach metoda przenosi jego wartość zwracaną z wartości przechowywanej. W związku z tym wywołać tę metodę tylko raz.

## <a name="futureoperator"></a><a name="op_eq"></a>przyszłość::operator=

Przenosi skojarzony stan asynchroniczne z określonego obiektu.

```cpp
future& operator=(future&& Right) noexcept;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Obiekt `future`.

### <a name="return-value"></a>Wartość zwracana

`*this`

### <a name="remarks"></a>Uwagi

Po przeniesieniu *Right* nie ma już skojarzonego stanu asynchronisty.

## <a name="futureshare"></a><a name="share"></a>przyszłość::share

Konwertuje obiekt na [obiekt shared_future.](../standard-library/shared-future-class.md)

```cpp
shared_future<Ty> share();
```

### <a name="return-value"></a>Wartość zwracana

`shared_future(move(*this))`

## <a name="futurevalid"></a><a name="valid"></a>przyszłość::valid

Określa, czy obiekt ma skojarzony stan asynchroniczne.

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli obiekt ma skojarzony stan asynchroniczne; w przeciwnym razie **false**.

## <a name="futurewait"></a><a name="wait"></a>przyszłość::czekać

Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne nie będzie *gotowy.*

```cpp
void wait() const;
```

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczne ma przechowywane wartości zwracanej lub przechowywane wyjątek.

## <a name="futurewait_for"></a><a name="wait_for"></a>przyszłość::wait_for

Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne nie będzie *gotowy* lub do czasu upływu określonego przedziału czasu.

```cpp
template <class Rep, class Period>
future_status wait_for(const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>Parametry

*Rel_time*\
A [chrono::duration](../standard-library/duration-class.md) obiektu, który określa maksymalny przedział czasu, który blokuje wątku.

### <a name="return-value"></a>Wartość zwracana

[Future_status,](../standard-library/future-enums.md#future_status) który wskazuje przyczynę powrotu.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest gotowy tylko wtedy, gdy jego dostawca asynchroniczne ma przechowywane wartości zwracanej lub przechowywane wyjątek.

## <a name="futurewait_until"></a><a name="wait_until"></a>przyszłość::wait_until

Blokuje bieżący wątek, dopóki skojarzony stan asynchroniczne jest *gotowy* lub do momentu po określonym punkcie czasowym.

```cpp
template <class Clock, class Duration>
future_status wait_until(const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>Parametry

*Abs_time*\
A [chrono::time_point](../standard-library/time-point-class.md) obiekt, który określa czas, po którym wątek może odblokować.

### <a name="return-value"></a>Wartość zwracana

[Future_status,](../standard-library/future-enums.md#future_status) który wskazuje przyczynę powrotu.

### <a name="remarks"></a>Uwagi

Skojarzony stan asynchroniczne jest *gotowy* tylko wtedy, gdy jego dostawca asynchroniczne ma przechowywane wartości zwracanej lub przechowywane wyjątek.

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<przyszłych>](../standard-library/future.md)
