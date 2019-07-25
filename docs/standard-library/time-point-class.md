---
title: time_point — Klasa
ms.date: 03/27/2019
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
helpviewer_keywords:
- std::chrono [C++], time_point
ms.openlocfilehash: 4511c7b2d8629f1a052137c7997daf5913c976ab
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459985"
---
# <a name="timepoint-class"></a>time_point — Klasa

`time_point` Opisuje typ, który reprezentuje punkt w czasie. Przechowuje obiekt typu Duration, który przechowuje czas, który upłynął od czasu [trwania](../standard-library/duration-class.md) epoki reprezentowanej przez argument `Clock`szablonu.

## <a name="syntax"></a>Składnia

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`time_point::clock`|Synonim dla parametru `Clock`szablonu.|
|`time_point::duration`|Synonim dla parametru `Duration`szablonu.|
|`time_point::period`|Synonim nazwy `duration::period`typu zagnieżdżonego.|
|`time_point::rep`|Synonim nazwy `duration::rep`typu zagnieżdżonego.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[time_point](#time_point)|Konstruuje `time_point` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[max](#max)|Określa górną granicę `time_point::ref`dla.|
|[min](#min)|Określa dolny limit dla `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Zwraca przechowywaną `duration` wartość.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Dodaje określoną wartość do przechowywanego czasu trwania.|
|[time_point::operator-=](#operator-_eq)|Odejmuje określoną wartość od przechowywanego czasu trwania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<Chrono >

**Przestrzeń nazw:** std:: Chrono

## <a name="max"></a>time_point:: max

Metoda statyczna zwracająca górną granicę dla wartości `time_point::ref`typu.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca wartość `time_point(duration::max())`.

## <a name="min"></a>time_point:: min

Metoda statyczna zwracająca dolną granicę dla wartości `time_point::ref`typu.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca wartość `time_point(duration::min())`.

## <a name="op_add_eq"></a>time_point:: operator + =

Dodaje określoną wartość do przechowywanej wartości [czasu trwania](../standard-library/duration-class.md) .

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`time_point` Obiekt po dodaniu jest wykonywany.

## <a name="operator-_eq"></a>time_point:: operator-=

Odejmuje określoną wartość z przechowywanej wartości [czasu trwania](../standard-library/duration-class.md) .

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`time_point` Obiekt po wykonaniu odejmowania.

## <a name="time_point"></a>time_point:: time_point — Konstruktor

Konstruuje `time_point` obiekt.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

*Trwania*\
Obiekt [czasu trwania](../standard-library/duration-class.md) .

*TP*\
Element `time_point` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, którego przechowywana `duration` wartość jest równa wartości [Duration:: zero](../standard-library/duration-class.md#zero).

Drugi Konstruktor konstruuje obiekt, którego przechowywana wartość czasu trwania jest równa czasowi *trwania*. O `is_convertible<Duration2, duration>` ile nie ma wartości true, drugi Konstruktor nie uczestniczy w rozpoznawaniu przeciążenia. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

Trzeci Konstruktor inicjuje swoją `duration` wartość przy użyciu. `Tp.time_since_epoch()`

## <a name="time_since_epoch"></a>time_point::time_since_epoch

Pobiera wartość przechowywanego [czasu trwania](../standard-library/duration-class.md) .

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
