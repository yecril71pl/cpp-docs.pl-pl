---
title: '&lt;limity&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66f9401bed0a6c9d0b1ffa09a10f98afa258069d
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964759"
---
# <a name="ltlimitsgt"></a>&lt;limity&gt;

Definiuje klasę szablonu `numeric_limits` i dwa wyliczenia dotyczącymi reprezentacji zmiennoprzecinkowe i zaokrąglania.

## <a name="syntax"></a>Składnia

```cpp
#include <limits>

```

## <a name="remarks"></a>Uwagi

Jawne specjalizacje `numeric_limits` klasy opisują wiele właściwości typów podstawowych, w tym znak, liczba całkowita i typów zmiennoprzecinkowych i **bool** , które są implementacji zdefiniowane, a nie przez reguły języka C++. Właściwości opisane w \<limity > obejmują dokładności, minimalnej i maksymalnej wielkości oświadczenia, zaokrąglania oraz trybu sygnalizowania błędów typu.

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Wyliczenia w tym artykule opisano różne metody, które można wybrać implementacji reprezentujący wartość zmiennoprzecinkowa nieznormalizowany — jeden zbyt mała, aby przedstawić jako wartość znormalizowaną:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Wyliczenia w tym artykule opisano różne metody wdrażania można wybrać podczas zaokrąglania wartość zmiennoprzecinkowa wartość będącą liczbą całkowitą.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[numeric_limits, klasa](../standard-library/numeric-limits-class.md)|Klasa szablonu opisuje arytmetyczne właściwości wbudowanych typów liczbowych.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
