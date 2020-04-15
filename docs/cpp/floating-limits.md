---
title: Limity liczb zmiennoprzecinkowych
ms.date: 08/03/2018
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- float.h header file
- limits, floating-point constants
- floating-point numbers [C++]
- floating limits
ms.assetid: fc718652-1f4c-4ed8-af60-0e769637459c
ms.openlocfilehash: ccd395eef319e57cecffad8a5278b6df1397f4cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373368"
---
# <a name="floating-limits"></a>Limity liczb zmiennoprzecinkowych

**Specyficzne dla firmy Microsoft**

W poniższej tabeli wymieniono limity wartości stałych zmiennoprzecinkowych. Limity te są również zdefiniowane w standardowym pliku \<nagłówka float.h>.

## <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych

|Stały|Znaczenie|Wartość|
|--------------|-------------|-----------|
|`FLT_DIG`<br/>`DBL_DIG`<br/>`LDBL_DIG`|Liczba cyfr, q, taka, że liczba zmiennoprzecinkowa z cyframi dziesiętnymi q może być zaokrąglona w reprezentację zmiennoprzecinkowa i z powrotem bez utraty precyzji.|6<br/>15<br/>15|
|`FLT_EPSILON`<br/>`DBL_EPSILON`<br/>`LDBL_EPSILON`|Najmniejsza liczba dodatnia x, taka, że x + 1.0 nie jest równa 1.0.|1.192092896e-07F<br/>2.2204460492503131e-016<br/>2.2204460492503131e-016|
|`FLT_GUARD`||0|
|`FLT_MANT_DIG`<br/>`DBL_MANT_DIG`<br/>`LDBL_MANT_DIG`|Liczba cyfr w radix określony `FLT_RADIX` przez w significand zmiennoprzecinkowych. Radix jest 2; dlatego te wartości określają bity.|24<br/>53<br/>53|
|`FLT_MAX`<br/>`DBL_MAX`<br/>`LDBL_MAX`|Maksymalna liczba zmiennoprzecinowa do reprezentowania.|3.402823466e+38F<br/>1.7976931348623158e+308<br/>1.7976931348623158e+308|
|`FLT_MAX_10_EXP`<br/>`DBL_MAX_10_EXP`<br/>`LDBL_MAX_10_EXP`|Maksymalna liczba całkowita taka, że 10 podniesiona do tej liczby jest reprezentowaną liczbą zmiennoprzecinkową.|38<br/>308<br/>308|
|`FLT_MAX_EXP`<br/>`DBL_MAX_EXP`<br/>`LDBL_MAX_EXP`|Maksymalna liczba całkowita `FLT_RADIX` taka, która została podniesiona do tej liczby, jest reprezentacyjną liczbą zmiennoprzecinkową.|128<br/>1024<br/>1024|
|`FLT_MIN`<br/>`DBL_MIN`<br/>`LDBL_MIN`|Minimalna wartość dodatnia.|1.175494351e-38F<br/>2.2250738585072014e-308<br/>2.2250738585072014e-308|
|`FLT_MIN_10_EXP`<br/>`DBL_MIN_10_EXP`<br/>`LDBL_MIN_10_EXP`|Minimalna ujemna liczba całkowita taka, że 10 podniesiona do tej liczby jest reprezentacyjną liczbą zmiennoprzecinkową.|-37<br/>-307<br/>-307|
|`FLT_MIN_EXP`<br/>`DBL_MIN_EXP`<br/>`LDBL_MIN_EXP`|Minimalna ujemna liczba `FLT_RADIX` całkowita taka, która została podniesiona do tej liczby, jest liczbą zmiennoprzecinową.|-125<br/>-1021<br/>-1021|
|`FLT_NORMALIZE`||0|
|`FLT_RADIX`<br/>`_DBL_RADIX`<br/>`_LDBL_RADIX`|Radix wykładnik reprezentacji.|2<br/>2<br/>2|
|`FLT_ROUNDS`<br/>`_DBL_ROUNDS`<br/>`_LDBL_ROUNDS`|Tryb zaokrąglania dla dodatku zmiennoprzecinkowego.|1 (w pobliżu)<br/>1 (w pobliżu)<br/>1 (w pobliżu)|

> [!NOTE]
> Informacje zawarte w tabeli mogą różnić się w przyszłych wersjach produktu.

**ZAKOŃCZ Specyficzne dla firmy Microsoft**

## <a name="see-also"></a>Zobacz też

[Limity całkowite](../cpp/integer-limits.md)
