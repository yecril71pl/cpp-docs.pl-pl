---
title: steady_clock, struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/22/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f4deb0bfe9439011f75cd22d0d52b74dae9c1f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959728"
---
# <a name="steadyclock-struct"></a>steady_clock — struktura

Reprezentuje *stały* zegara.

## <a name="syntax"></a>Składnia

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Uwagi

W Windows `steady_clock` opakowuje `QueryPerformanceCounter` funkcji.

Zegar jest *monotoniczny* Jeśli wartość, która jest zwracana przez pierwsze wywołanie `now` jest zawsze mniejsza niż wartość, która jest zwracana przez kolejne wywołanie `now`. Zegar jest *stały* , gdy jest *monotoniczny* i jeśli czas między taktami zegara jest stały.

`high_resolution_clock` element typedef dla jest `steady_clock`.

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`steady_clock::duration`|Synonim dla `nanoseconds`zdefiniowaną w \<chrono >.|
|`steady_clock::period`|Synonim dla `nano`zdefiniowaną w \<współczynnik >.|
|`steady_clock::rep`|Synonim dla **długie** **długie**, typ, który jest używany do reprezentowania liczby taktów zegara w zamkniętym `duration`.|
|`steady_clock::time_point`|Synonim dla `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Funkcji publicznych

|Funkcja|Opis|
|--------------|-----------------|
|`now`|Zwraca bieżącą godzinę jako `time_point` wartość.|

## <a name="public-constants"></a>Publiczne stałe

|Nazwa|Opis|
|----------|-----------------|
|`steady_clock::is_steady`|Przechowuje **true**. A `steady_clock` jest *stały*.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Zobacz także

- [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock, struktura](../standard-library/system-clock-structure.md)
