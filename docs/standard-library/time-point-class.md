---
title: time_point, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::time_point
- chrono/std::chrono::time_point::time_point
- chrono/std::chrono::time_point::max
- chrono/std::chrono::time_point::min
- chrono/std::chrono::time_point::time_since_epoch
dev_langs:
- C++
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::chrono [C++], time_point
ms.workload:
- cplusplus
ms.openlocfilehash: eb5390ad8fec7e355181c9711de1bb14d3b17820
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705981"
---
# <a name="timepoint-class"></a>time_point — Klasa

A `time_point` opisuje typ, który reprezentuje punkt w czasie. Przechowuje obiekt typu [czas trwania](../standard-library/duration-class.md) który przechowuje czas, jaki upłynął od początku epoki reprezentowanej przez argument szablonu `Clock`.

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
|`time_point::clock`|Synonim dla parametru szablonu `Clock`.|
|`time_point::duration`|Synonim dla parametru szablonu `Duration`.|
|`time_point::period`|Synonim dla nazwy typu zagnieżdżonego `duration::period`.|
|`time_point::rep`|Synonim dla nazwy typu zagnieżdżonego `duration::rep`.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[time_point](#time_point)|Konstruuje `time_point` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[max](#max)|Określa górną granicę dla `time_point::ref`.|
|[min](#min)|Określa dolną granicę dla `time_point::ref`.|
|[time_since_epoch](#time_since_epoch)|Zwraca przechowywaną `duration` wartość.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[time_point::operator+=](#op_add_eq)|Dodaje określoną wartość do przechowywanego czasu trwania.|
|[time_point::operator-=](#operator-_eq)|Odejmuje określoną wartość z przechowywanego czasu trwania.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="max"></a>  time_point::Max —

Metoda statyczna zwraca górną granicę wartości typu `time_point::ref`.

```cpp
static constexpr time_point max();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `time_point(duration::max())`.

## <a name="min"></a>  time_point::min —

Metoda statyczna zwraca dolną granicę wartości typu `time_point::ref`.

```cpp
static constexpr time_point min();
```

### <a name="return-value"></a>Wartość zwracana

W efekcie zwraca `time_point(duration::min())`.

## <a name="op_add_eq"></a>  time_point::operator +=

Dodaje określoną wartość do przechowywanej [czas trwania](../standard-library/duration-class.md) wartość.

```cpp
time_point& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`time_point` Obiektu po wykonaniu dodawania.

## <a name="time_point__operator-_eq"></a>  time_point::operator-=

Odejmuje określoną wartość z przechowywanej [czas trwania](../standard-library/duration-class.md) wartość.

```cpp
time_point& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
Element `duration` obiektu.

### <a name="return-value"></a>Wartość zwracana

`time_point` Obiektu po wykonaniu odejmowania.

## <a name="time_point"></a>  time_point::time_point — Konstruktor

Konstruuje `time_point` obiektu.

```cpp
constexpr time_point();

constexpr explicit time_point(const duration& Dur);

template <class Duration2>
constexpr time_point(const time_point<clock, Duration2>& Tp);
```

### <a name="parameters"></a>Parametry

*Czas trwania*<br/>
A [czas trwania](../standard-library/duration-class.md) obiektu.

*Jednostka TP*<br/>
Element `time_point` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor konstruuje obiekt, którego przechowywane `duration` wartość jest równa [duration::zero](../standard-library/duration-class.md#zero).

Drugi Konstruktor konstruuje obiekt, którego przechowywana wartość jest równa *czas trwania*. Chyba że `is_convertible<Duration2, duration>` przechowuje wartości true, drugi Konstruktor nie uczestniczy w przeciążeniu rozdzielczości. Aby uzyskać więcej informacji, zobacz [< type_traits >](../standard-library/type-traits.md).

Trzeci Konstruktor inicjuje jego `duration` wartości za pomocą `Tp.time_since_epoch()`.

## <a name="time_since_epoch"></a>  time_point::time_since_epoch —

Pobiera przechowywaną [czas trwania](../standard-library/duration-class.md) wartość.

```cpp
constexpr duration time_since_epoch() const;
```

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
