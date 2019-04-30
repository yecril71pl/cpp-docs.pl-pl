---
title: '&lt;limity&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: c029095d5298048874a7eb6f1a41209d6a6f4779
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413245"
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
