---
title: system_clock — Struktura
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: ca516551bb1b41d96b99aaf7b842666c9341ee7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376513"
---
# <a name="system_clock-structure"></a>system_clock — Struktura

Reprezentuje *typ zegara,* który jest oparty na zegarze czasu rzeczywistego systemu.

## <a name="syntax"></a>Składnia

```cpp
struct system_clock;
```

## <a name="remarks"></a>Uwagi

*Typ zegara* służy do uzyskania bieżącego czasu jako UTC. Typ uosabia wystąpienie czasu [trwania](../standard-library/duration-class.md) i szablon klasy [time_point](../standard-library/time-point-class.md)i definiuje statyczną funkcję `now()` elementu członkowskiego, która zwraca czas.

Zegar jest *monotoniczny,* jeśli wartość zwracana przez `now()` pierwsze wywołanie jest zawsze mniejsza lub równa wartości `now()`zwracana przez kolejne wywołanie .

Zegar jest *stały,* jeśli jest *monotoniczny* i jeśli czas między znacznikami zegara jest stały.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`system_clock::duration`|Synonimem . `duration<rep, period>`|
|`system_clock::period`|Synonim typu, który jest używany do reprezentowania okresu znacznika w `duration`zawartym wystąpieniu .|
|`system_clock::rep`|Synonim typu, który jest używany do reprezentowania liczby znaczników zegara w `duration`zawartym wystąpieniu .|
|`system_clock::time_point`|Synonim dla `time_point<Clock, duration>`programu `Clock` , gdzie jest synonimem dla samego typu zegara lub innego typu zegara, który `duration` jest oparty na tej samej epoce i ma ten sam typ zagnieżdżony.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Statyczny. `time_point` Zwraca, że najbardziej przybliża określony czas.|
|[Nwo](#now)|Statyczny. Zwraca bieżącą godzinę.|
|[to_time_t](#to_time_t)|Statyczny. Zwraca `time_t` obiekt, który najbardziej przybliża `time_point`określony plik .|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[system_clock::is_monotonic stała](#is_monotonic_constant)|Określa, czy typ zegara jest monotoniczny.|
|[system_clock::is_steady stała](#is_steady_constant)|Określa, czy typ zegara jest stały.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono>

**Przestrzeń nazw:** std::chrono

## <a name="system_clockfrom_time_t"></a><a name="from_time_t"></a>system_clock::from_time_t

Metoda statyczna, która zwraca [time_point,](../standard-library/time-point-class.md) która najbardziej przybliża czas reprezentowany przez *Tm*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

*Tm*\
Obiekt [time_t.](../c-runtime-library/standard-types.md)

## <a name="system_clockis_monotonic-constant"></a><a name="is_monotonic_constant"></a>system_clock::is_monotonic stała

Wartość statyczna określająca, czy typ zegara jest monotoniczny.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Wartość zwracana

W tej `system_clock::is_monotonic` implementacji zawsze zwraca **false**.

### <a name="remarks"></a>Uwagi

Zegar jest *monotoniczny,* jeśli wartość zwracana przez `now()` pierwsze wywołanie jest zawsze mniejsza lub równa wartości `now()`zwracana przez kolejne wywołanie .

## <a name="system_clockis_steady-constant"></a><a name="is_steady_constant"></a>system_clock::is_steady stała

Wartość statyczna określająca, czy typ zegara jest *stały*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Wartość zwracana

W tej `system_clock::is_steady` implementacji zawsze zwraca **false**.

### <a name="remarks"></a>Uwagi

Zegar jest *stały,* jeśli jest [monotoniczny](#is_monotonic_constant) i jeśli czas między znacznikami zegara jest stały.

## <a name="system_clocknow"></a><a name="now"></a>system_clock::now

Metoda statyczna, która zwraca bieżący czas.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [time_point](../standard-library/time-point-class.md) reprezentujący bieżący czas.

## <a name="system_clockto_time_t"></a><a name="to_time_t"></a>system_clock::to_time_t

Metoda statyczna, która zwraca [time_t,](../c-runtime-library/standard-types.md) która najbardziej przybliża czas, który jest reprezentowany przez *Czas*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

*Czas*\
Obiekt [time_point.](../standard-library/time-point-class.md)

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<>chrono](../standard-library/chrono.md)\
[steady_clock — struktura](../standard-library/steady-clock-struct.md)
