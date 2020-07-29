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
ms.openlocfilehash: 4e530887e7c8cf26e8969a839702286913da9b67
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224581"
---
# <a name="system_clock-structure"></a>system_clock — Struktura

Reprezentuje *Typ zegara* , który jest oparty na zegarze w czasie rzeczywistym systemu.

## <a name="syntax"></a>Składnia

```cpp
struct system_clock;
```

## <a name="remarks"></a>Uwagi

*Typ zegara* służy do uzyskiwania bieżącego czasu jako czasu UTC. Typ zawiera Tworzenie wystąpienia [czasu trwania](../standard-library/duration-class.md) i szablonu klasy [time_point](../standard-library/time-point-class.md)i definiuje statyczną funkcję członkowską `now()` , która zwraca czas.

Zegar jest *monotoniczny* , jeśli wartość zwracana przez pierwsze wywołanie `now()` jest zawsze mniejsza lub równa wartości zwracanej przez kolejne wywołanie do `now()` .

Zegar jest *stabilny* , jeśli jest *monotoniczny* , a czas między taktami zegara jest stały.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`system_clock::duration`|Synonim dla `duration<rep, period>` .|
|`system_clock::period`|Synonim dla typu, który jest używany do reprezentowania okresu osi w zawartym utworzeniu wystąpienia `duration` .|
|`system_clock::rep`|Synonim dla typu, który jest używany do reprezentowania liczby taktów zegara w zawartym utworzeniu wystąpienia `duration` .|
|`system_clock::time_point`|Synonim dla `time_point<Clock, duration>` , gdzie `Clock` jest synonimem dla samego typu zegara lub innego typu zegara, który jest oparty na tej samej epoki i ma ten sam typ zagnieżdżony `duration` .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[from_time_t](#from_time_t)|Statyczny. Zwraca `time_point` , który jest najbardziej zbliżony do określonego czasu.|
|[Znajdź](#now)|Statyczny. Zwraca bieżącą godzinę.|
|[to_time_t](#to_time_t)|Statyczny. Zwraca `time_t` obiekt, który jest najbardziej zbliżony do określonego `time_point` .|

### <a name="public-constants"></a>Stałe publiczne

|Nazwa|Opis|
|----------|-----------------|
|[system_clock:: is_monotonic, stała](#is_monotonic_constant)|Określa, czy typ zegara to monotoniczny.|
|[system_clock:: is_steady, stała](#is_steady_constant)|Określa, czy typ zegara jest stały.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<chrono>

**Przestrzeń nazw:** std:: Chrono

## <a name="system_clockfrom_time_t"></a><a name="from_time_t"></a>system_clock:: from_time_t

Metoda statyczna zwracająca [time_point](../standard-library/time-point-class.md) , który jest najbardziej zbliżony do czasu reprezentowanego przez *TM*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parametry

*®*\
Obiekt [time_t](../c-runtime-library/standard-types.md) .

## <a name="system_clockis_monotonic-constant"></a><a name="is_monotonic_constant"></a>system_clock:: is_monotonic, stała

Wartość statyczna określająca, czy typ zegara to monotoniczny.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Wartość zwracana

W tej implementacji `system_clock::is_monotonic` zawsze zwraca **`false`** .

### <a name="remarks"></a>Uwagi

Zegar jest *monotoniczny* , jeśli wartość zwracana przez pierwsze wywołanie `now()` jest zawsze mniejsza lub równa wartości zwracanej przez kolejne wywołanie do `now()` .

## <a name="system_clockis_steady-constant"></a><a name="is_steady_constant"></a>system_clock:: is_steady, stała

Wartość statyczna określająca, czy typ zegara jest *stały*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Wartość zwracana

W tej implementacji `system_clock::is_steady` zawsze zwraca **`false`** .

### <a name="remarks"></a>Uwagi

Zegar jest *stabilny* , jeśli jest [monotoniczny](#is_monotonic_constant) , a czas między taktami zegara jest stały.

## <a name="system_clocknow"></a><a name="now"></a>system_clock:: teraz

Metoda statyczna zwracająca bieżącą godzinę.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt [time_point](../standard-library/time-point-class.md) , który reprezentuje bieżący czas.

## <a name="system_clockto_time_t"></a><a name="to_time_t"></a>system_clock:: to_time_t

Metoda statyczna zwracająca [time_t](../c-runtime-library/standard-types.md) , który jest najbardziej zbliżony do czasu reprezentowanego przez *czas*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parametry

*Pierwszym*\
Obiekt [time_point](../standard-library/time-point-class.md) .

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock — struktura](../standard-library/steady-clock-struct.md)
