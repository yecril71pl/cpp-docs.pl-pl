---
title: '&lt;ograniczeń&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: de8f815cd59b84a1e63c231e18e4882d0b5d6f09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447571"
---
# <a name="ltlimitsgt"></a>&lt;ograniczeń&gt;

Definiuje klasę `numeric_limits` szablonu i dwa wyliczenia dotyczące reprezentacji zmiennoprzecinkowych i zaokrąglania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<limity >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Jawne specjalizacje `numeric_limits` klasy opisują wiele właściwości typów podstawowych, takich jak znak, liczba całkowita i typy zmiennoprzecinkowe oraz **bool** , które są zdefiniowane przez implementację, a nie ustalone przez reguły C++język. Właściwości opisane w \<limitach > obejmują dokładność, minimalną i maksymalną reprezentację rozmiaru, zaokrąglenie i Sygnalizowanie błędów typu.

## <a name="members"></a>Elementy członkowskie

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Wyliczenie opisuje różne metody, które można wybrać do reprezentowania nieznormalizowanej wartości zmiennoprzecinkowej — jeden za mały, aby reprezentować jako znormalizowaną wartość:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Wyliczenie opisuje różne metody, które można wybrać, aby zaokrąglić wartość zmiennoprzecinkową do wartości całkowitej.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[numeric_limits, klasa](../standard-library/numeric-limits-class.md)|Klasa szablonu opisuje arytmetyczne właściwości wbudowanych typów liczbowych.|

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
