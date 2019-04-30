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
ms.openlocfilehash: 66710f94d96f069d6d388d6b49c76747c618a0d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412153"
---
# <a name="systemclock-structure"></a>system_clock — Struktura

Reprezentuje *typ zegara* jest oparty na zegarze w czasie rzeczywistym systemu.

## <a name="syntax"></a>Składnia

```cpp
struct system_clock;
```

## <a name="remarks"></a>Uwagi

A *typ zegara* służy do uzyskiwania bieżącego czasu jako czas UTC. Typ uosabia wystąpienie z [czas trwania](../standard-library/duration-class.md) i szablonem klasy [time_point](../standard-library/time-point-class.md)i definiuje funkcję członka statycznego `now()` który zwraca czas.

Zegar jest *monotoniczny* Jeśli wartość, która jest zwracana przez pierwsze wywołanie `now()` jest zawsze mniejsza niż wartość, która jest zwracana przez kolejne wywołanie `now()`.

Zegar jest *stały* , gdy jest *monotoniczny* i jeśli czas między taktami zegara jest stały.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`system_clock::duration`|Synonim dla `duration<rep, period>`.|
|`system_clock::period`|Synonim dla typu, który jest używany do reprezentowania okresu taktu w zamkniętym `duration`.|
|`system_clock::rep`|Synonim dla typu, który jest używany do reprezentowania liczby taktów zegara w zamkniętym `duration`.|
|`system_clock::time_point`|Synonim dla `time_point<Clock, duration>`, gdzie `Clock` jest synonimem samego typu zegara lub innego typu zegara, który opiera się na tej samej epoce i ma taki sam zagnieżdżony `duration` typu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Statyczne. Zwraca `time_point` , najbardziej zbliżony przez określony czas.|
|[teraz](#now)|Statyczne. Zwraca bieżącą godzinę.|
|[to_time_t](#to_time_t)|Statyczne. Zwraca `time_t` obiekt, który jest najbardziej zbliżony do określonego `time_point`.|

### <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|[system_clock::is_monotonic Constant](#is_monotonic_constant)|Określa, czy typ zegara jest monotoniczny.|
|[system_clock::is_steady — stała](#is_steady_constant)|Określa, czy typ zegara jest stały.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t —

Metoda statyczna zwraca [time_point](../standard-library/time-point-class.md) który możliwie najbardziej przybliża czas, który jest reprezentowany przez *Tm*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

*Tm*<br/>
A [time_t](../c-runtime-library/standard-types.md) obiektu.

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic — stała

Wartość statyczna, która określa, czy typ zegara jest monotoniczny.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Wartość zwracana

W tej implementacji `system_clock::is_monotonic` zawsze zwraca **false**.

### <a name="remarks"></a>Uwagi

Zegar jest *monotoniczny* Jeśli wartość, która jest zwracana przez pierwsze wywołanie `now()` jest zawsze mniejsza niż wartość, która jest zwracana przez kolejne wywołanie `now()`.

## <a name="is_steady_constant"></a>  system_clock::is_steady — stała

Wartość statyczna, która określa, czy typ zegara jest *stały*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Wartość zwracana

W tej implementacji `system_clock::is_steady` zawsze zwraca **false**.

### <a name="remarks"></a>Uwagi

Zegar jest *stały* , gdy jest [monotoniczny](#is_monotonic_constant) i jeśli czas między taktami zegara jest stały.

## <a name="now"></a>  system_clock::Now —

Metoda statyczna zwraca bieżącą godzinę.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

A [time_point](../standard-library/time-point-class.md) obiekt, który reprezentuje bieżący czas.

## <a name="to_time_t"></a>  system_clock::to_time_t —

Metoda statyczna zwraca [time_t](../c-runtime-library/standard-types.md) który możliwie najbardziej przybliża czas, który jest reprezentowany przez *czasu*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

*czas*<br/>
A [time_point](../standard-library/time-point-class.md) obiektu.

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[steady_clock, struktura](../standard-library/steady-clock-struct.md)<br/>
