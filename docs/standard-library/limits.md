---
title: '&lt;limits &gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 3ad740975cfff4f65f9e1c800a709cfaca3367db
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687820"
---
# <a name="ltlimitsgt"></a>&lt;limits &gt;

Definiuje szablon klasy `numeric_limits` i dwa wyliczenia dotyczące reprezentacji zmiennoprzecinkowych i zaokrąglania.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<limits >

**Przestrzeń nazw:** std

## <a name="remarks"></a>Uwagi

Jawne specjalizacje klasy `numeric_limits` opisują wiele właściwości typów podstawowych, takich jak znak, liczba całkowita i typy zmiennoprzecinkowe oraz **bool** , które są zdefiniowane przez implementację, a nie ustalone przez reguły C++ językowe. Właściwości opisane w \<limits > obejmują dokładność, minimalną i maksymalną reprezentację rozmiaru, zaokrąglenie i Sygnalizowanie błędów typu.

## <a name="members"></a>Elementy członkowskie

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Wyliczenie opisuje różne metody, które można wybrać do reprezentowania nieznormalizowanej wartości zmiennoprzecinkowej — jeden za mały, aby reprezentować jako znormalizowaną wartość:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Wyliczenie opisuje różne metody, które można wybrać, aby zaokrąglić wartość zmiennoprzecinkową do wartości całkowitej.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[numeric_limits, klasa](../standard-library/numeric-limits-class.md)|Szablon klasy opisuje arytmetyczne właściwości wbudowanych typów liczbowych.|

## <a name="see-also"></a>Zobacz także

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md) \
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
