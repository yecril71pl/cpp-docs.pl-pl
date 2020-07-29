---
title: Struktura high_resolution_clock | Microsoft Docs
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
ms.openlocfilehash: 850d5e3a5434aa44e23a7f74aeb9c306ab6c0a8e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203211"
---
# <a name="steady_clock-struct"></a>steady_clock — struktura

Przedstawia zegar *high_resolution* .

## <a name="syntax"></a>Składnia

```cpp
class high_resolution_clock
```

## <a name="members"></a>Elementy członkowskie

### <a name="typedefs"></a>Typedefs

|Nazwa|Opis|
|----------|-----------------|
|`duration`|Synonim dla `nanoseconds` , zdefiniowany w \<chrono> .|
|`period`|Synonim dla `nano` , zdefiniowany w \<ratio> .|
|`rep`|Synonim dla **`long long`** typu, który jest używany do reprezentowania liczby taktów zegara w zawartym utworzeniu wystąpienia `duration` .|
|`time_point`|Synonim dla `chrono::time_point<high_resolution_clock>` .|

## <a name="functions"></a>Funkcje

|||
|-|-|
|`now`|Zwraca bieżący czas jako `time_point` wartość.|

## <a name="constants"></a>Stałe

|Nazwa|Opis|
|----------|-----------------|
|`is_steady`|Zawiera **`true`** . `high_resolution_clock`Jest *stała*.|
