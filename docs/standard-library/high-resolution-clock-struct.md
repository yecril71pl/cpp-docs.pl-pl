---
title: Struktura poprawiono elementy high_resolution_clock | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/22/2018
ms.technology: cpp-standard-libraries
ms.topic: reference
f1_keywords:
- chrono/std::chrono::high_resolution_clock
dev_langs:
- C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b00b20e7cea4fa24b37ad33d5536eb9844e6953
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268091"
---
# <a name="steadyclock-struct"></a>steady_clock — struktura

Reprezentuje *high_resolution* zegara.

## <a name="syntax"></a>Składnia

```cpp
class high_resolution_clock
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`duration`|Synonim dla `nanoseconds`zdefiniowaną w \<chrono >.|
|`period`|Synonim dla `nano`zdefiniowaną w \<współczynnik >.|
|`rep`|Synonim dla **długie** **długie**, typ, który jest używany do reprezentowania liczby taktów zegara w zamkniętym `duration`.|
|`time_point`|Synonim dla `chrono::time_point<high_resolution_clock>`.|

## <a name="functions"></a>Funkcje

|||
|-|-|
|`now`|Zwraca bieżącą godzinę jako `time_point` wartość.|

## <a name="constants"></a>Stałe

|Nazwa|Opis|
|----------|-----------------|
|`is_steady`|Przechowuje **true**. A `high_resolution_clock` jest *stały*.|
