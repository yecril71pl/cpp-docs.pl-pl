---
title: steady_clock — struktura | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5445379597c4fefcd657303a05c33b6509d54d2e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34569901"
---
# <a name="steadyclock-struct"></a>steady_clock — struktura

Reprezentuje *stałej* zegara.

## <a name="syntax"></a>Składnia

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Uwagi

W systemie Windows `steady_clock` opakowuje `QueryPerformanceCounter` funkcji.

Zegar jest *monotoniczna* Jeśli wartość, która jest zwracana przez pierwsze wywołanie w celu `now` zawsze jest mniejsza niż wartość zwracaną przez kolejne wywołanie `now`. Zegar jest *stałej* przypadku *monotoniczna* i jeśli czas między zegarowych jest stałą.

`high_resolution_clock` jest elementem typedef dla `steady_clock`.

### <a name="public-typedefs"></a>Definicje typów publicznych

|Nazwa|Opis|
|----------|-----------------|
|`steady_clock::duration`|Jest to synonim `nanoseconds`zdefiniowanej w \<chrono >.|
|`steady_clock::period`|Jest to synonim `nano`zdefiniowanej w \<stosunek >.|
|`steady_clock::rep`|Synonimem **długi** **długi**, typu, który jest używany do reprezentowania liczbę taktów zegara w zawartych w niej tworzenia wystąpienia elementu `duration`.|
|`steady_clock::time_point`|Jest to synonim `chrono::time_point<steady_clock>`.|

## <a name="public-functions"></a>Funkcje publiczne

|Funkcja|Opis|
|--------------|-----------------|
|`now`|Zwraca bieżącą godzinę jako `time_point` wartość.|

## <a name="public-constants"></a>Publiczny — stałe

|Nazwa|Opis|
|----------|-----------------|
|`steady_clock::is_steady`|Przechowuje `true`. A `steady_clock` jest *stałej*.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Zobacz także

- [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock, struktura](../standard-library/system-clock-structure.md)
