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
ms.openlocfilehash: e1de674d4a13ba465100923bffe6cba76e61ab4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368029"
---
# <a name="time_point-class"></a>time_point — Klasa

A `time_point` opisuje typ, który reprezentuje punkt w czasie. Posiada obiekt typu [czas trwania,](../standard-library/duration-class.md) który przechowuje czas, który upłynął od epoki, która jest reprezentowana przez argument `Clock`szablonu .

## <a name="syntax"></a>Składnia

```cpp
template <class Clock,
    class Duration = typename Clock::duration>
class time_point;
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`time_point::clock`|Synonim parametru `Clock`szablonu .|
|`time_point::duration`|Synonim parametru `Duration`szablonu .|
|`time_point::period`|Synonim nazwy `duration::period`typu zagnieżdżonego .|
|`time_point::rep`|Synonim nazwy `duration::rep`typu zagnieżdżonego .|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[time_point](#time_point)|Konstruuje `time_point` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Max](#max)|Określa górną granicę dla `time_point::ref`.|
|[Min](#min)|Określa dolną granicę dla `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Zwraca wartość `duration` zapisaną.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Dodaje określoną wartość do przechowywanego czasu trwania.|
|[time_point::operator-=](#operator-_eq)|Odejmuje określoną wartość od przechowywanego czasu trwania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono>

**Przestrzeń nazw:** std::chrono

## <a name="time_pointmax"></a><a name="max"></a>time_point::maks.

Metoda statyczna, która zwraca górną `time_point::ref`granicę dla wartości typu .

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie `time_point(duration::max())`zwraca .

## <a name="time_pointmin"></a><a name="min"></a>time_point::min

Metoda statyczna, która zwraca dolną `time_point::ref`granicę dla wartości typu .

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie `time_point(duration::min())`zwraca .

## <a name="time_pointoperator"></a><a name="op_add_eq"></a>time_point::operator+=

Dodaje określoną wartość do wartości [przechowywanego czasu trwania.](../standard-library/duration-class.md)

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Obiekt `time_point` po dodaniu jest wykonywany.

## <a name="time_pointoperator-"></a><a name="operator-_eq"></a>time_point::operator-=

Odejmuje określoną wartość od zapisanej wartości [czasu trwania.](../standard-library/duration-class.md)

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Obiekt `duration`.

### <a name="return-value"></a>Wartość zwracana

Obiekt `time_point` po wykonaniu odejmowania.

## <a name="time_pointtime_point-constructor"></a><a name="time_point"></a>time_point::time_point Konstruktor

Konstruuje `time_point` obiekt.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

*Dur (Dur)*\
Obiekt [czasu trwania.](../standard-library/duration-class.md)

*Tp*\
Obiekt `time_point`.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor tworzy obiekt, `duration` którego przechowywana wartość jest równa [czas trwania::zero](../standard-library/duration-class.md#zero).

Drugi konstruktor tworzy obiekt, którego wartość przechowywanego czasu trwania jest równa *Dur*. O `is_convertible<Duration2, duration>` ile nie jest true, drugi konstruktor nie uczestniczy w rozpoznawania przeciążenia. Aby uzyskać więcej informacji, zobacz [<type_traits>](../standard-library/type-traits.md).

Trzeci konstruktor inicjuje `duration` `Tp.time_since_epoch()`jego wartość przy użyciu programu .

## <a name="time_pointtime_since_epoch"></a><a name="time_since_epoch"></a>time_point::time_since_epoch

Pobiera wartość przechowywanego [czasu trwania.](../standard-library/duration-class.md)

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>chrono](../standard-library/chrono.md)
