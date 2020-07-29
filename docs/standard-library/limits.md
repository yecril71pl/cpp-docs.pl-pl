---
title: '&lt;ograniczeń&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 2d0f4f96d25c91ac20fe5a1883fc61fc47d15d5e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217691"
---
# <a name="ltlimitsgt"></a>&lt;ograniczeń&gt;

Definiuje szablon klasy `numeric_limits` i dwa wyliczenia dotyczące reprezentacji zmiennoprzecinkowych i zaokrąglania.

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<limits>

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Jawne specjalizacje `numeric_limits` klasy opisują wiele właściwości typów podstawowych, takich jak znaki, liczby całkowite i typy zmiennoprzecinkowe, **`bool`** które są zdefiniowane, a nie stałe przez reguły języka C++. Właściwości opisane w \<limits> obejmują dokładność, minimalną i maksymalną reprezentację rozmiaru, zaokrąglenie i Sygnalizowanie błędów typu.

## <a name="members"></a>Elementy członkowskie

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Wyliczenie opisuje różne metody, które można wybrać do reprezentowania nieznormalizowanej wartości zmiennoprzecinkowej — jeden za mały, aby reprezentować jako znormalizowaną wartość:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Wyliczenie opisuje różne metody, które można wybrać, aby zaokrąglić wartość zmiennoprzecinkową do wartości całkowitej.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[Klasa numeric_limits](../standard-library/numeric-limits-class.md)|Szablon klasy opisuje arytmetyczne właściwości wbudowanych typów liczbowych.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
