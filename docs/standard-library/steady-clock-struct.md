---
title: steady_clock — struktura | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- chrono/std::chrono::steady_clock
dev_langs:
- C++
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba4ebbe6db12fef05bfabd9970d354a7726fcd7d
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="steadyclock-struct"></a>steady_clock — struktura

Reprezentuje `steady` zegara.

## <a name="syntax"></a>Składnia

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Uwagi

W systemie Windows steady_clock opakowuje funkcji QueryPerformanceCounter.

Zegar jest *monotoniczna* Jeśli wartość, która jest zwracana przez pierwsze wywołanie w celu `now()` zawsze jest mniejsza niż wartość zwracaną przez kolejne wywołanie `now()`.

Zegar jest *stałej* przypadku *monotoniczna* i jeśli czas między zegarowych jest stałą.

High_resolution_clock jest typdef dla steady_clock.

## <a name="public-functions"></a>Funkcje publiczne

|Funkcja|Opis|
|--------------|-----------------|
|Teraz|Zwraca bieżącą godzinę jako wartość time_point —.|

## <a name="public-constants"></a>Publiczny — stałe

|Nazwa|Opis|
|----------|-----------------|
|`system_clock::is_steady`|Przechowuje `true`. A `steady_clock` jest *stałej*.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<chrono >

**Namespace:** std::chrono

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
[system_clock, struktura](../standard-library/system-clock-structure.md)<br/>
