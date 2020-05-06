---
title: Limity dla stałych zmiennoprzecinkowych
ms.date: 11/04/2016
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
ms.openlocfilehash: df39ee719a4474f6dfd55d31a2848169a1168390
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325588"
---
# <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych

**Specyficzne dla firmy Microsoft**

W poniższej tabeli podano limity wartości stałych zmiennoprzecinkowych. Plik nagłówka ZMIENNOPRZECINKOWego. H zawiera te informacje.

### <a name="limits-on-floating-point-constants"></a>Limity dla stałych zmiennoprzecinkowych

|Stały|Znaczenie|Wartość|
|--------------|-------------|-----------|
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|Liczba cyfr, *q*, takich jak liczba zmiennoprzecinkowa z cyframi dziesiętnymi *q* , może być zaokrąglana do reprezentacji zmiennoprzecinkowej i z powrotem bez utraty dokładności.|6<br />15<br />15|
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|Najmniejsza liczba dodatnia *x*, tak że *x* + 1,0 nie jest równa 1,0|1.192092896 e-07F<br />2.2204460492503131 e-016<br />2.2204460492503131 e-016|
|**FLT_GUARD**||0|
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|Liczba cyfr w podstawy określonym przez **FLT_RADIX** w mantysę zmiennoprzecinkowej. Podstawy to 2; w związku z tym te wartości określają bity.|24<br />53<br />53|
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|Maksymalna reprezentacja liczby zmiennoprzecinkowej.|3.402823466 e + 38F<br />1.7976931348623158 e + 308<br />1.7976931348623158 e + 308|
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|Maksymalna liczba całkowita, taka jak 10 podniesiona do tej liczby, to reprezentacja liczby zmiennoprzecinkowej.|38<br />308<br />308|
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|Maksymalna liczba całkowita, taka jak **FLT_RADIX** podniesioną do tej liczby, to reprezentacja liczby zmiennoprzecinkowej.|128<br />1024<br />1024|
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|Minimalna wartość dodatnia.|1.175494351 e-38F<br />2.2250738585072014 e-308<br />2.2250738585072014 e-308|
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|Minimalna ujemna liczba całkowita, taka jak 10 podniesiono do tej liczby, jest reprezentacją liczby zmiennoprzecinkowej.|-37<br />-307<br />-307|
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|Minimalna ujemna liczba całkowita, która **FLT_RADIX** podniesiona do tej liczby to liczba zmiennoprzecinkowa, którą można reprezentować.|-125<br />-1021<br />-1021|
|**FLT_NORMALIZE**||0|
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|Podstawy reprezentacji wykładnika.|2<br />2<br />2|
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|Tryb zaokrąglania dla dodawania zmiennoprzecinkowego.|1 (blisko)<br />1 (blisko)<br />1 (blisko)|

Należy zauważyć, że informacje w powyższej tabeli mogą się różnić w przyszłych implementacjach.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz też

[Stałe zmiennoprzecinkowe języka C](../c-language/c-floating-point-constants.md)
